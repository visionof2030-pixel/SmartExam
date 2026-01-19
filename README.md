<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Smart Tests Platform - منصة الاختبارات الذكية</title>
    
    <!-- الخطوط -->
    <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@300;400;500;600;700;800&family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    
    <!-- أيقونات -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        :root {
            --primary: #0A3D62;
            --secondary: #159895;
            --accent: #00C1D4;
            --light: #F5F9FF;
            --dark: #071E36;
            --success: #2E7D32;
            --error: #C62828;
            --warning: #FF9800;
            --card-bg: #FFFFFF;
            --shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
            --radius: 16px;
            --transition: all 0.3s ease;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Tajawal', 'Poppins', sans-serif;
            background: linear-gradient(135deg, #0A3D62 0%, #071E36 100%);
            color: var(--dark);
            line-height: 1.6;
            padding-top: 80px;
            min-height: 100vh;
            transition: var(--transition);
        }
        
        body.english-mode {
            font-family: 'Poppins', 'Tajawal', sans-serif;
            direction: ltr;
        }
        
        body.english-mode .header,
        body.english-mode .logo,
        body.english-mode .tabs,
        body.english-mode .tab-content,
        body.english-mode .option-card,
        body.english-mode .btn,
        body.english-mode .result-box,
        body.english-mode .wrong-answers-btn {
            direction: ltr;
        }
        
        body.english-mode .option-number {
            margin-right: 15px;
            margin-left: 0;
        }
        
        body.english-mode .feedback {
            border-right: none;
            border-left: 4px solid var(--secondary);
        }
        
        /* الهيدر الثابت */
        .header {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            background: linear-gradient(90deg, var(--primary) 0%, var(--secondary) 100%);
            color: white;
            padding: 15px 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.2);
            z-index: 1000;
            height: 80px;
        }
        
        .logo {
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .logo-icon {
            font-size: 28px;
            background: rgba(255, 255, 255, 0.15);
            width: 50px;
            height: 50px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .logo-text h1 {
            font-size: 1.5rem;
            font-weight: 800;
            margin-bottom: 5px;
        }
        
        .logo-text p {
            font-size: 0.85rem;
            opacity: 0.9;
            font-weight: 300;
        }
        
        .language-switch {
            display: flex;
            align-items: center;
            gap: 10px;
            background: rgba(255, 255, 255, 0.15);
            padding: 8px 15px;
            border-radius: 50px;
            cursor: pointer;
            transition: var(--transition);
        }
        
        .language-switch:hover {
            background: rgba(255, 255, 255, 0.25);
        }
        
        .language-switch i {
            font-size: 1.2rem;
        }
        
        /* المحتوى الرئيسي */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 30px 20px;
        }
        
        /* كرت الواجهة الرئيسية */
        .dashboard {
            background: var(--card-bg);
            border-radius: var(--radius);
            box-shadow: var(--shadow);
            overflow: hidden;
            margin-bottom: 30px;
        }
        
        /* التبويبات */
        .tabs {
            display: flex;
            background: #f8fafc;
            border-bottom: 1px solid #eaeaea;
            padding: 0;
            overflow-x: auto;
            scrollbar-width: none;
        }
        
        .tabs::-webkit-scrollbar {
            display: none;
        }
        
        .tab-btn {
            flex: 1;
            min-width: 200px;
            padding: 22px 15px;
            background: none;
            border: none;
            border-bottom: 3px solid transparent;
            color: #64748b;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 12px;
            transition: var(--transition);
        }
        
        .tab-btn i {
            font-size: 1.3rem;
        }
        
        .tab-btn:hover {
            color: var(--primary);
            background: rgba(10, 61, 98, 0.05);
        }
        
        .tab-btn.active {
            color: var(--secondary);
            border-bottom-color: var(--secondary);
            background: white;
        }
        
        /* محتوى التبويبات */
        .tab-content {
            padding: 40px;
            display: none;
        }
        
        .tab-content.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        /* عناصر النموذج */
        .form-group {
            margin-bottom: 25px;
        }
        
        .form-label {
            display: block;
            margin-bottom: 10px;
            font-weight: 600;
            color: var(--primary);
            font-size: 1.1rem;
        }
        
        .form-input, .form-select, .form-textarea {
            width: 100%;
            padding: 16px 20px;
            border: 2px solid #e2e8f0;
            border-radius: 12px;
            font-size: 1rem;
            font-family: 'Tajawal', 'Poppins', sans-serif;
            transition: var(--transition);
            background: white;
        }
        
        .form-input:focus, .form-select:focus, .form-textarea:focus {
            outline: none;
            border-color: var(--accent);
            box-shadow: 0 0 0 3px rgba(0, 193, 212, 0.1);
        }
        
        .form-textarea {
            min-height: 150px;
            resize: vertical;
        }
        
        /* أزرار */
        .btn {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            padding: 18px 30px;
            border: none;
            border-radius: 12px;
            font-size: 1.1rem;
            font-weight: 700;
            cursor: pointer;
            transition: var(--transition);
            font-family: 'Tajawal', 'Poppins', sans-serif;
            width: 100%;
        }
        
        .btn-primary {
            background: linear-gradient(90deg, var(--secondary) 0%, var(--accent) 100%);
            color: white;
            box-shadow: 0 5px 15px rgba(21, 152, 149, 0.3);
        }
        
        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(21, 152, 149, 0.4);
        }
        
        .btn-secondary {
            background: #f1f5f9;
            color: var(--primary);
            border: 2px solid #cbd5e1;
        }
        
        .btn-secondary:hover {
            background: #e2e8f0;
        }
        
        .btn-wrong-answers {
            background: linear-gradient(90deg, #FF9800 0%, #FF5722 100%);
            color: white;
            margin-top: 20px;
            width: auto;
            padding: 12px 25px;
        }
        
        .btn-lg {
            padding: 20px 35px;
            font-size: 1.2rem;
        }
        
        /* بطاقات الخيارات */
        .option-card {
            background: white;
            border: 2px solid #e2e8f0;
            border-radius: 12px;
            padding: 20px;
            margin-bottom: 15px;
            cursor: pointer;
            transition: var(--transition);
            position: relative;
            overflow: hidden;
        }
        
        .option-card:hover {
            border-color: var(--accent);
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }
        
        .option-card.selected {
            border-color: var(--secondary);
            background: rgba(21, 152, 149, 0.05);
        }
        
        .option-card.correct {
            border-color: var(--success);
            background: rgba(46, 125, 50, 0.08);
            animation: correctPulse 0.5s ease;
        }
        
        .option-card.incorrect {
            border-color: var(--error);
            background: rgba(198, 40, 40, 0.08);
            animation: incorrectShake 0.5s ease;
        }
        
        @keyframes correctPulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.03); }
            100% { transform: scale(1); }
        }
        
        @keyframes incorrectShake {
            0%, 100% { transform: translateX(0); }
            25% { transform: translateX(-5px); }
            75% { transform: translateX(5px); }
        }
        
        .option-number {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            width: 36px;
            height: 36px;
            background: #f1f5f9;
            border-radius: 50%;
            margin-left: 15px;
            font-weight: 700;
            color: var(--primary);
        }
        
        .option-card.correct .option-number {
            background: var(--success);
            color: white;
        }
        
        .option-card.incorrect .option-number {
            background: var(--error);
            color: white;
        }
        
        .feedback {
            margin-top: 15px;
            padding: 15px;
            background: #f8fafc;
            border-radius: 10px;
            border-right: 4px solid var(--secondary);
            font-size: 0.95rem;
            display: none;
        }
        
        .option-card.show-feedback .feedback {
            display: block;
        }
        
        .wrong-feedback {
            margin-top: 15px;
            padding: 15px;
            background: #fff8e1;
            border-radius: 10px;
            border-right: 4px solid #FF9800;
            font-size: 0.95rem;
            display: none;
        }
        
        .wrong-feedback.show {
            display: block;
            animation: fadeIn 0.5s ease;
        }
        
        /* النتيجة */
        .result-box {
            background: white;
            border-radius: var(--radius);
            padding: 40px;
            text-align: center;
            box-shadow: var(--shadow);
            margin-bottom: 30px;
        }
        
        .score-circle {
            width: 180px;
            height: 180px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--secondary) 0%, var(--accent) 100%);
            margin: 0 auto 30px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            color: white;
            box-shadow: 0 10px 30px rgba(21, 152, 149, 0.3);
        }
        
        .score-value {
            font-size: 3.5rem;
            font-weight: 800;
            line-height: 1;
        }
        
        .score-total {
            font-size: 1.5rem;
            opacity: 0.9;
        }
        
        .result-message {
            font-size: 1.5rem;
            color: var(--primary);
            margin-bottom: 20px;
            font-weight: 700;
        }
        
        /* الملخص */
        .summary-box {
            background: white;
            border-radius: var(--radius);
            padding: 35px;
            box-shadow: var(--shadow);
            white-space: pre-wrap;
            line-height: 1.8;
            max-height: 500px;
            overflow-y: auto;
        }
        
        .summary-box::-webkit-scrollbar {
            width: 8px;
        }
        
        .summary-box::-webkit-scrollbar-track {
            background: #f1f1f1;
            border-radius: 10px;
        }
        
        .summary-box::-webkit-scrollbar-thumb {
            background: var(--secondary);
            border-radius: 10px;
        }
        
        /* تقدم الاختبار */
        .progress-container {
            margin-bottom: 30px;
            background: #f1f5f9;
            border-radius: 12px;
            overflow: hidden;
        }
        
        .progress-bar {
            height: 10px;
            background: linear-gradient(90deg, var(--secondary) 0%, var(--accent) 100%);
            width: 0%;
            transition: width 0.5s ease;
            border-radius: 12px;
        }
        
        .progress-info {
            display: flex;
            justify-content: space-between;
            padding: 15px 0;
            font-weight: 600;
            color: var(--primary);
        }
        
        /* تذييل الصفحة */
        .footer {
            text-align: center;
            padding: 30px 20px;
            color: rgba(255, 255, 255, 0.7);
            font-size: 0.9rem;
            margin-top: 30px;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        /* إشعارات */
        .notification {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: white;
            padding: 15px 25px;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            display: flex;
            align-items: center;
            gap: 15px;
            z-index: 1000;
            transform: translateY(100px);
            opacity: 0;
            transition: all 0.3s ease;
        }
        
        .notification.show {
            transform: translateY(0);
            opacity: 1;
        }
        
        .notification.correct {
            border-right: 5px solid var(--success);
        }
        
        .notification.incorrect {
            border-right: 5px solid var(--error);
        }
        
        /* تصميم متجاوب */
        @media (max-width: 992px) {
            .tab-btn {
                min-width: 180px;
                padding: 18px 12px;
                font-size: 1rem;
            }
            
            .tab-content {
                padding: 30px;
            }
        }
        
        @media (max-width: 768px) {
            .header {
                padding: 15px 20px;
                height: 70px;
                flex-direction: column;
                gap: 10px;
                height: auto;
                padding: 15px;
            }
            
            .logo-icon {
                width: 45px;
                height: 45px;
                font-size: 24px;
            }
            
            .logo-text h1 {
                font-size: 1.3rem;
            }
            
            body {
                padding-top: 120px;
            }
            
            .tab-btn {
                min-width: 160px;
                padding: 15px 10px;
                font-size: 0.95rem;
            }
            
            .tab-content {
                padding: 25px 20px;
            }
            
            .score-circle {
                width: 150px;
                height: 150px;
            }
            
            .score-value {
                font-size: 2.8rem;
            }
            
            .btn-wrong-answers {
                width: 100%;
            }
        }
        
        @media (max-width: 576px) {
            .container {
                padding: 20px 15px;
            }
            
            .tab-btn {
                min-width: 140px;
                padding: 15px 8px;
                font-size: 0.9rem;
                gap: 8px;
            }
            
            .tab-btn i {
                font-size: 1.1rem;
            }
            
            .btn {
                padding: 16px 20px;
                font-size: 1rem;
            }
            
            .form-input, .form-select, .form-textarea {
                padding: 14px 16px;
            }
        }
        
        /* الرسوم المتحركة */
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }
        
        .pulse {
            animation: pulse 0.5s ease;
        }
        
        /* حالة التحميل */
        .loading {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 60px 20px;
            text-align: center;
        }
        
        .spinner {
            width: 60px;
            height: 60px;
            border: 5px solid rgba(21, 152, 149, 0.2);
            border-radius: 50%;
            border-top-color: var(--secondary);
            animation: spin 1s linear infinite;
            margin-bottom: 20px;
        }
        
        @keyframes spin {
            100% { transform: rotate(360deg); }
        }
    </style>
</head>

<body id="bodyElement">
    <!-- الهيدر الثابت -->
    <header class="header">
        <div class="logo">
            <div class="logo-icon">
                <i class="fas fa-brain"></i>
            </div>
            <div class="logo-text">
                <h1 id="appTitle">الاختبارات الذكية</h1>
                <p id="appSubtitle">منصة الاختبارات والتلخيص</p>
            </div>
        </div>
        <div class="language-switch" onclick="toggleLanguage()">
            <i class="fas fa-globe"></i>
            <span id="languageText">English</span>
        </div>
        <div class="developer">
            <p id="developerText">تنفيذ: فهد نغيمش الخالدي</p>
        </div>
    </header>
    
    <!-- المحتوى الرئيسي -->
    <main class="container">
        <div class="dashboard">
            <!-- التبويبات -->
            <div class="tabs">
                <button class="tab-btn active" data-tab="manual">
                    <i class="fas fa-edit"></i>
                    <span id="manualTabText">اختبار يدوي</span>
                </button>
                <button class="tab-btn" data-tab="file">
                    <i class="fas fa-file-upload"></i>
                    <span id="fileTabText">اختبار من ملف</span>
                </button>
                <button class="tab-btn" data-tab="summary">
                    <i class="fas fa-file-contract"></i>
                    <span id="summaryTabText">تلخيص ملف</span>
                </button>
            </div>
            
            <!-- محتوى التبويبات -->
            <div class="tab-content active" id="manual-tab">
                <h2 style="margin-bottom: 25px; color: var(--primary);" id="manualTitle">إنشاء اختبار يدوي</h2>
                <div class="form-group">
                    <label class="form-label" for="topic" id="topicLabel">موضوع الاختبار</label>
                    <textarea class="form-textarea" id="topic" placeholder="اكتب موضوع الاختبار هنا... (مثال: مبادئ الفيزياء الأساسية، تاريخ الدولة العباسية، قواعد اللغة العربية)"></textarea>
                </div>
                
                <div class="form-group">
                    <label class="form-label" for="lang" id="langLabel">لغة الاختبار</label>
                    <select class="form-select" id="lang">
                        <option value="ar">العربية</option>
                        <option value="en">English</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label class="form-label" for="qCount" id="qCountLabel">عدد الأسئلة</label>
                    <select class="form-select" id="qCount">
                        <option value="5">5 أسئلة</option>
                        <option value="10" selected>10 أسئلة</option>
                        <option value="20">20 سؤال</option>
                        <option value="30">30 سؤال</option>
                        <option value="40">40 سؤال</option>
                        <option value="50">50 سؤال</option>
                        <option value="60">60 سؤال</option>
                    </select>
                </div>
                
                <button class="btn btn-primary btn-lg" onclick="manualQuiz()">
                    <i class="fas fa-magic"></i>
                    <span id="createTestBtn">إنشاء الاختبار</span>
                </button>
            </div>
            
            <div class="tab-content" id="file-tab">
                <h2 style="margin-bottom: 25px; color: var(--primary);" id="fileTitle">إنشاء اختبار من ملف</h2>
                
                <div class="form-group">
                    <label class="form-label" id="uploadFileLabel">رفع الملف</label>
                    <div style="border: 2px dashed #cbd5e1; border-radius: 12px; padding: 40px 20px; text-align: center; background: #f8fafc; cursor: pointer;" onclick="document.getElementById('fileInput').click()">
                        <i class="fas fa-cloud-upload-alt" style="font-size: 3rem; color: var(--secondary); margin-bottom: 15px;"></i>
                        <p style="font-size: 1.1rem; color: var(--primary); margin-bottom: 10px;" id="clickToUpload">انقر لرفع ملف</p>
                        <p style="color: #64748b; font-size: 0.9rem;" id="fileSupport">يدعم: PDF, PNG, JPG (الحد الأقصى: 10MB)</p>
                        <input type="file" id="fileInput" accept=".pdf,.png,.jpg,.jpeg" style="display: none;" onchange="updateFileName()">
                    </div>
                    <p id="fileName" style="margin-top: 10px; color: var(--primary); font-weight: 500;"></p>
                </div>
                
                <div class="form-group">
                    <label class="form-label" for="fileLang" id="fileLangLabel">لغة الاختبار</label>
                    <select class="form-select" id="fileLang">
                        <option value="ar">العربية</option>
                        <option value="en">English</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label class="form-label" for="fileQCount" id="fileQCountLabel">عدد الأسئلة</label>
                    <select class="form-select" id="fileQCount">
                        <option value="5">5 أسئلة</option>
                        <option value="10" selected>10 أسئلة</option>
                        <option value="20">20 سؤال</option>
                        <option value="30">30 سؤال</option>
                        <option value="40">40 سؤال</option>
                        <option value="50">50 سؤال</option>
                        <option value="60">60 سؤال</option>
                    </select>
                </div>
                
                <button class="btn btn-primary btn-lg" onclick="fileQuiz()">
                    <i class="fas fa-file-alt"></i>
                    <span id="createQuestionsBtn">إنشاء الأسئلة من الملف</span>
                </button>
            </div>
            
            <div class="tab-content" id="summary-tab">
                <h2 style="margin-bottom: 25px; color: var(--primary);" id="summaryTitle">تلخيص ملف</h2>
                
                <div class="form-group">
                    <label class="form-label" id="uploadSummaryLabel">رفع الملف للتلخيص</label>
                    <div style="border: 2px dashed #cbd5e1; border-radius: 12px; padding: 40px 20px; text-align: center; background: #f8fafc; cursor: pointer;" onclick="document.getElementById('sumFile').click()">
                        <i class="fas fa-file-contract" style="font-size: 3rem; color: var(--secondary); margin-bottom: 15px;"></i>
                        <p style="font-size: 1.1rem; color: var(--primary); margin-bottom: 10px;" id="clickToUploadSummary">انقر لرفع ملف</p>
                        <p style="color: #64748b; font-size: 0.9rem;" id="summarySupport">يدعم: PDF, PNG, JPG (الحد الأقصى: 10MB)</p>
                        <input type="file" id="sumFile" accept=".pdf,.png,.jpg,.jpeg" style="display: none;" onchange="updateSumFileName()">
                    </div>
                    <p id="sumFileName" style="margin-top: 10px; color: var(--primary); font-weight: 500;"></p>
                </div>
                
                <div class="form-group">
                    <label class="form-label" for="sumLang" id="sumLangLabel">لغة الملخص</label>
                    <select class="form-select" id="sumLang">
                        <option value="ar">العربية</option>
                        <option value="en">English</option>
                    </select>
                </div>
                
                <button class="btn btn-primary btn-lg" onclick="summarize()">
                    <i class="fas fa-compress-alt"></i>
                    <span id="summarizeBtn">تلخيص الملف</span>
                </button>
            </div>
        </div>
        
        <!-- منطقة النتائج -->
        <div id="result"></div>
        
        <!-- زر التالي (يظهر أثناء الاختبار) -->
        <div id="nextBtnContainer" style="display: none; margin-top: 30px;">
            <button class="btn btn-primary btn-lg" id="nextBtn" onclick="nextQuestion()">
                <i class="fas fa-arrow-left" id="nextIcon"></i>
                <span id="nextBtnText">التالي</span>
            </button>
        </div>
    </main>
    
    <!-- التذييل -->
    <footer class="footer">
        <p id="footerText">© 2023 المنصة الذكية للاختبارات والتلخيص | تنفيذ: فهد نغيمش الخالدي</p>
        <p id="rightsText">جميع الحقوق محفوظة</p>
    </footer>
    
    <!-- إشعارات -->
    <div id="notification" class="notification">
        <i class="fas" id="notificationIcon"></i>
        <span id="notificationText"></span>
    </div>
    
    <!-- عناصر صوتية -->
    <audio id="correctSound" preload="auto">
        <source src="https://media.vocaroo.com/mp3/19lcrilHKuHR" type="audio/mpeg">
    </audio>
    
    <audio id="incorrectSound" preload="auto">
        <source src="https://media.vocaroo.com/mp3/1ooZTr9sHVXS" type="audio/mpeg">
    </audio>
    
    <audio id="nextSound" preload="auto">
        <source src="https://assets.mixkit.co/sfx/preview/mixkit-select-click-1109.mp3" type="audio/mpeg">
    </audio>
    
    <audio id="completeSound" preload="auto">
        <source src="https://assets.mixkit.co/sfx/preview/mixkit-achievement-bell-600.mp3" type="audio/mpeg">
    </audio>
    
    <script>
        const BACKEND = "https://smarttest-0ycc.onrender.com";
        
        let questions = [];
        let answers = [];
        let index = 0;
        let totalQuestions = 0;
        let currentLanguage = 'ar'; // اللغة الافتراضية
        let currentQuestionWrongFeedbacks = []; // تخزين تغذية راجعة للخيارات الخاطئة للسؤال الحالي
        
        // عناصر الصوت
        const correctSound = document.getElementById('correctSound');
        const incorrectSound = document.getElementById('incorrectSound');
        const nextSound = document.getElementById('nextSound');
        const completeSound = document.getElementById('completeSound');
        
        // نصوص متعددة اللغات
        const translations = {
            ar: {
                appTitle: "الاختبارات الذكية",
                appSubtitle: "منصة الاختبارات والتلخيص",
                developerText: "تنفيذ: فهد نغيمش الخالدي",
                languageText: "English",
                manualTabText: "اختبار يدوي",
                fileTabText: "اختبار من ملف",
                summaryTabText: "تلخيص ملف",
                manualTitle: "إنشاء اختبار يدوي",
                topicLabel: "موضوع الاختبار",
                topicPlaceholder: "اكتب موضوع الاختبار هنا... (مثال: مبادئ الفيزياء الأساسية، تاريخ الدولة العباسية، قواعد اللغة العربية)",
                langLabel: "لغة الاختبار",
                qCountLabel: "عدد الأسئلة",
                createTestBtn: "إنشاء الاختبار",
                fileTitle: "إنشاء اختبار من ملف",
                uploadFileLabel: "رفع الملف",
                clickToUpload: "انقر لرفع ملف",
                fileSupport: "يدعم: PDF, PNG, JPG (الحد الأقصى: 10MB)",
                fileLangLabel: "لغة الاختبار",
                fileQCountLabel: "عدد الأسئلة",
                createQuestionsBtn: "إنشاء الأسئلة من الملف",
                summaryTitle: "تلخيص ملف",
                uploadSummaryLabel: "رفع الملف للتلخيص",
                clickToUploadSummary: "انقر لرفع ملف",
                summarySupport: "يدعم: PDF, PNG, JPG (الحد الأقصى: 10MB)",
                sumLangLabel: "لغة الملخص",
                summarizeBtn: "تلخيص الملف",
                nextBtnText: "التالي",
                finishBtnText: "عرض النتيجة",
                footerText: "© 2023 المنصة الذكية للاختبارات والتلخيص | تنفيذ: فهد نغيمش الخالدي",
                rightsText: "جميع الحقوق محفوظة",
                loadingTest: "جارٍ إنشاء الاختبار...",
                loadingQuestions: "جارٍ تحليل الملف وإنشاء الأسئلة...",
                loadingSummary: "جارٍ تلخيص الملف...",
                pleaseWait: "يرجى الانتظار، هذه العملية قد تستغرق دقيقة",
                correctNotification: "إجابة صحيحة! أحسنت!",
                incorrectNotification: "إجابة خاطئة! حاول مرة أخرى.",
                resultTitle: "نتيجة الاختبار",
                excellent: "ممتاز! نتيجة رائعة",
                veryGood: "جيد جداً! أحسنت",
                good: "مقبول، يمكنك التحسين",
                needsImprovement: "تحتاج إلى مراجعة المادة",
                successRate: "نسبة النجاح:",
                retryTest: "إعادة الاختبار",
                newTest: "اختبار جديد",
                noFileSelected: "الرجاء اختيار ملف أولاً",
                noTopic: "الرجاء إدخال موضوع للاختبار",
                chooseAnswer: "الرجاء اختيار إجابة قبل الانتقال للسؤال التالي",
                errorCreatingTest: "حدث خطأ أثناء إنشاء الاختبار",
                errorProcessingFile: "حدث خطأ أثناء معالجة الملف",
                errorSummarizing: "حدث خطأ أثناء تلخيص الملف",
                tryAgain: "إعادة المحاولة",
                checkConnection: "الرجاء المحاولة مرة أخرى أو التحقق من اتصال الإنترنت",
                checkFileFormat: "الرجاء التأكد من صيغة الملف والمحاولة مرة أخرى",
                questionOf: "سؤال",
                of: "من",
                summaryTitleResult: "ملخص الملف",
                printSummary: "طباعة الملخص",
                showWrongAnswers: "عرض شرح الإجابات الخاطئة",
                hideWrongAnswers: "إخفاء شرح الإجابات الخاطئة",
                wrongAnswersTitle: "شرح الإجابات الخاطئة:"
            },
            en: {
                appTitle: "Smart Tests Platform",
                appSubtitle: "Testing and Summarization Platform",
                developerText: "Developed by: Fahad Nghaimesh Al-Khalidi",
                languageText: "العربية",
                manualTabText: "Manual Test",
                fileTabText: "Test from File",
                summaryTabText: "File Summary",
                manualTitle: "Create Manual Test",
                topicLabel: "Test Topic",
                topicPlaceholder: "Enter test topic here... (e.g., Basic Physics Principles, History of the Abbasid State, Arabic Grammar Rules)",
                langLabel: "Test Language",
                qCountLabel: "Number of Questions",
                createTestBtn: "Create Test",
                fileTitle: "Create Test from File",
                uploadFileLabel: "Upload File",
                clickToUpload: "Click to upload file",
                fileSupport: "Supports: PDF, PNG, JPG (Max: 10MB)",
                fileLangLabel: "Test Language",
                fileQCountLabel: "Number of Questions",
                createQuestionsBtn: "Generate Questions from File",
                summaryTitle: "File Summarization",
                uploadSummaryLabel: "Upload File for Summary",
                clickToUploadSummary: "Click to upload file",
                summarySupport: "Supports: PDF, PNG, JPG (Max: 10MB)",
                sumLangLabel: "Summary Language",
                summarizeBtn: "Summarize File",
                nextBtnText: "Next",
                finishBtnText: "Show Results",
                footerText: "© 2023 Smart Tests Platform | Developed by: Fahd Nghaimesh Al-Khalidi",
                rightsText: "All rights reserved",
                loadingTest: "Creating test...",
                loadingQuestions: "Analyzing file and generating questions...",
                loadingSummary: "Summarizing file...",
                pleaseWait: "Please wait, this process may take a minute",
                correctNotification: "Correct answer! Well done!",
                incorrectNotification: "Incorrect answer! Try again.",
                resultTitle: "Test Results",
                excellent: "Excellent! Great result",
                veryGood: "Very good! Well done",
                good: "Acceptable, you can improve",
                needsImprovement: "Needs to review the material",
                successRate: "Success rate:",
                retryTest: "Retry Test",
                newTest: "New Test",
                noFileSelected: "Please select a file first",
                noTopic: "Please enter a test topic",
                chooseAnswer: "Please select an answer before moving to the next question",
                errorCreatingTest: "Error creating test",
                errorProcessingFile: "Error processing file",
                errorSummarizing: "Error summarizing file",
                tryAgain: "Try Again",
                checkConnection: "Please try again or check your internet connection",
                checkFileFormat: "Please check the file format and try again",
                questionOf: "Question",
                of: "of",
                summaryTitleResult: "File Summary",
                printSummary: "Print Summary",
                showWrongAnswers: "Show Wrong Answers Explanation",
                hideWrongAnswers: "Hide Wrong Answers Explanation",
                wrongAnswersTitle: "Wrong Answers Explanation:"
            }
        };
        
        // تبديل اللغة
        function toggleLanguage() {
            currentLanguage = currentLanguage === 'ar' ? 'en' : 'ar';
            updateLanguage();
        }
        
        // تحديث واجهة اللغة
        function updateLanguage() {
            const texts = translations[currentLanguage];
            
            // تحديث اتجاه الصفحة
            document.body.id = currentLanguage === 'ar' ? 'bodyElement' : 'bodyElement english-mode';
            
            // تحديث النصوص
            document.getElementById('appTitle').textContent = texts.appTitle;
            document.getElementById('appSubtitle').textContent = texts.appSubtitle;
            document.getElementById('developerText').textContent = texts.developerText;
            document.getElementById('languageText').textContent = texts.languageText;
            document.getElementById('manualTabText').textContent = texts.manualTabText;
            document.getElementById('fileTabText').textContent = texts.fileTabText;
            document.getElementById('summaryTabText').textContent = texts.summaryTabText;
            document.getElementById('manualTitle').textContent = texts.manualTitle;
            document.getElementById('topicLabel').textContent = texts.topicLabel;
            document.getElementById('topic').placeholder = texts.topicPlaceholder;
            document.getElementById('langLabel').textContent = texts.langLabel;
            document.getElementById('qCountLabel').textContent = texts.qCountLabel;
            document.getElementById('createTestBtn').textContent = texts.createTestBtn;
            document.getElementById('fileTitle').textContent = texts.fileTitle;
            document.getElementById('uploadFileLabel').textContent = texts.uploadFileLabel;
            document.getElementById('clickToUpload').textContent = texts.clickToUpload;
            document.getElementById('fileSupport').textContent = texts.fileSupport;
            document.getElementById('fileLangLabel').textContent = texts.fileLangLabel;
            document.getElementById('fileQCountLabel').textContent = texts.fileQCountLabel;
            document.getElementById('createQuestionsBtn').textContent = texts.createQuestionsBtn;
            document.getElementById('summaryTitle').textContent = texts.summaryTitle;
            document.getElementById('uploadSummaryLabel').textContent = texts.uploadSummaryLabel;
            document.getElementById('clickToUploadSummary').textContent = texts.clickToUploadSummary;
            document.getElementById('summarySupport').textContent = texts.summarySupport;
            document.getElementById('sumLangLabel').textContent = texts.sumLangLabel;
            document.getElementById('summarizeBtn').textContent = texts.summarizeBtn;
            document.getElementById('footerText').textContent = texts.footerText;
            document.getElementById('rightsText').textContent = texts.rightsText;
            
            // تحديث اتجاه الأيقونة في زر التالي
            const nextIcon = document.getElementById('nextIcon');
            nextIcon.className = currentLanguage === 'ar' ? 'fas fa-arrow-left' : 'fas fa-arrow-right';
        }
        
        // إدارة التبويبات
        document.querySelectorAll('.tab-btn').forEach(btn => {
            btn.addEventListener('click', () => {
                // إزالة النشاط من جميع الأزرار
                document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
                // إخفاء جميع المحتويات
                document.querySelectorAll('.tab-content').forEach(c => c.classList.remove('active'));
                
                // تفعيل الزر المحدد
                btn.classList.add('active');
                // إظهار المحتوى المقابل
                const tabId = btn.getAttribute('data-tab');
                document.getElementById(`${tabId}-tab`).classList.add('active');
                
                // مسح النتائج
                document.getElementById('result').innerHTML = '';
                document.getElementById('nextBtnContainer').style.display = 'none';
            });
        });
        
        // تحديث اسم الملف المرفوع
        function updateFileName() {
            const fileInput = document.getElementById('fileInput');
            const fileName = document.getElementById('fileName');
            if (fileInput.files.length > 0) {
                const icon = currentLanguage === 'ar' ? 
                    `<i class="fas fa-check-circle" style="color: var(--success);"></i> تم رفع الملف: ${fileInput.files[0].name}` :
                    `<i class="fas fa-check-circle" style="color: var(--success);"></i> File uploaded: ${fileInput.files[0].name}`;
                fileName.innerHTML = icon;
            } else {
                fileName.innerHTML = '';
            }
        }
        
        function updateSumFileName() {
            const sumFile = document.getElementById('sumFile');
            const sumFileName = document.getElementById('sumFileName');
            if (sumFile.files.length > 0) {
                const icon = currentLanguage === 'ar' ?
                    `<i class="fas fa-check-circle" style="color: var(--success);"></i> تم رفع الملف: ${sumFile.files[0].name}` :
                    `<i class="fas fa-check-circle" style="color: var(--success);"></i> File uploaded: ${sumFile.files[0].name}`;
                sumFileName.innerHTML = icon;
            } else {
                sumFileName.innerHTML = '';
            }
        }
        
        // عرض إشعار
        function showNotification(message, type) {
            const notification = document.getElementById('notification');
            const icon = document.getElementById('notificationIcon');
            const text = document.getElementById('notificationText');
            
            notification.className = `notification ${type}`;
            icon.className = type === 'correct' ? 'fas fa-check-circle' : 'fas fa-times-circle';
            text.textContent = message;
            
            notification.classList.add('show');
            
            setTimeout(() => {
                notification.classList.remove('show');
            }, 3000);
        }
        
        // معالجة JSON الآمنة
        function safeParse(text) {
            try {
                return JSON.parse(text.replace(/```json|```/g, "").trim());
            } catch (e) {
                console.error("JSON parsing error:", e);
                
                // إنشاء بيانات اختبار افتراضية
                if (currentLanguage === 'ar') {
                    return {
                        questions: [
                            {
                                q: "ما هو العنصر الأكثر وفرة في الكون؟",
                                options: ["الهيدروجين", "الهيليوم", "الأكسجين", "الكربون"],
                                answer: 0,
                                explanations: [
                                    "الهيدروجين هو العنصر الأكثر وفرة في الكون، حيث يشكل حوالي 75% من الكتلة الباريونية للكون.",
                                    "الهيليوم هو ثاني أكثر العناصر وفرة في الكون، ولكنه ليس الأكثر وفرة.",
                                    "الأكسجين هو ثالث أكثر العناصر وفرة في الكون، ولكنه لا يشكل النسبة الأكبر.",
                                    "الكربون عنصر مهم للحياة ولكنه ليس الأكثر وفرة في الكون."
                                ]
                            },
                            {
                                q: "أي كوكب هو الأكبر في المجموعة الشمسية؟",
                                options: ["المشتري", "زحل", "نبتون", "الأرض"],
                                answer: 0,
                                explanations: [
                                    "المشتري هو أكبر كوكب في المجموعة الشمسية، وكتلته أكبر بـ 2.5 مرة من جميع الكواكب الأخرى مجتمعة.",
                                    "زحل هو ثاني أكبر كوكب في المجموعة الشمسية، ولكنه أصغر من المشتري.",
                                    "نبتون هو رابع أكبر كوكب في المجموعة الشمسية.",
                                    "الأرض هي خامس أكبر كوكب في المجموعة الشمسية وأكبر الكواكب الصخرية."
                                ]
                            }
                        ]
                    };
                } else {
                    return {
                        questions: [
                            {
                                q: "What is the most abundant element in the universe?",
                                options: ["Hydrogen", "Helium", "Oxygen", "Carbon"],
                                answer: 0,
                                explanations: [
                                    "Hydrogen is the most abundant element in the universe, constituting about 75% of the baryonic mass of the universe.",
                                    "Helium is the second most abundant element in the universe, but not the most abundant.",
                                    "Oxygen is the third most abundant element in the universe, but it doesn't constitute the largest percentage.",
                                    "Carbon is an important element for life but not the most abundant in the universe."
                                ]
                            },
                            {
                                q: "Which planet is the largest in the solar system?",
                                options: ["Jupiter", "Saturn", "Neptune", "Earth"],
                                answer: 0,
                                explanations: [
                                    "Jupiter is the largest planet in the solar system, with a mass 2.5 times greater than all other planets combined.",
                                    "Saturn is the second largest planet in the solar system, but smaller than Jupiter.",
                                    "Neptune is the fourth largest planet in the solar system.",
                                    "Earth is the fifth largest planet in the solar system and the largest of the terrestrial planets."
                                ]
                            }
                        ]
                    };
                }
            }
        }
        
        // إنشاء اختبار يدوي
        async function manualQuiz() {
            const topic = document.getElementById('topic').value;
            const lang = document.getElementById('lang').value;
            const qCount = document.getElementById('qCount').value;
            const texts = translations[lang === 'ar' ? 'ar' : 'en'];
            
            if (!topic.trim()) {
                alert(texts.noTopic);
                return;
            }
            
            // تحديث اللغة الحالية بناءً على اختيار المستخدم
            if (lang !== currentLanguage) {
                currentLanguage = lang === 'ar' ? 'ar' : 'en';
                updateLanguage();
            }
            
            // عرض حالة التحميل
            document.getElementById('result').innerHTML = `
                <div class="loading">
                    <div class="spinner"></div>
                    <h3 style="color: var(--primary); margin-bottom: 10px;">${texts.loadingTest}</h3>
                    <p style="color: #64748b;">${texts.pleaseWait}</p>
                </div>
            `;
            
            const prompt = lang === 'ar' ? `
أنشئ اختبار اختيار من متعدد حول الموضوع التالي:
${topic}

قواعد:
- ${qCount} أسئلة
- 4 خيارات لكل سؤال
- شرح موسع لكل خيار (الصحيح والخاطئ)
- أعد JSON فقط

الصيغة:
{
 "questions":[
  {
   "q":"",
   "options":["","","",""],
   "answer":0,
   "explanations":["شرح الخيار 1","شرح الخيار 2","شرح الخيار 3","شرح الخيار 4"]
  }
 ]
}
` : `
Create a multiple choice test on the following topic:
${topic}

Rules:
- ${qCount} questions
- 4 options for each question
- Detailed explanation for each option (both correct and incorrect)
- Return JSON only

Format:
{
 "questions":[
  {
   "q":"",
   "options":["","","",""],
   "answer":0,
   "explanations":["Explanation for option 1","Explanation for option 2","Explanation for option 3","Explanation for option 4"]
  }
 ]
}
`;
            
            try {
                const response = await fetch(BACKEND + "/ask", {
                    method: "POST",
                    headers: { "Content-Type": "application/json" },
                    body: JSON.stringify({ prompt, language: lang })
                });
                
                const data = await response.json();
                questions = safeParse(data.result).questions;
                answers = new Array(questions.length).fill(null);
                index = 0;
                totalQuestions = questions.length;
                
                // إظهار زر التالي
                document.getElementById('nextBtnContainer').style.display = 'block';
                
                // تحديث نص زر التالي
                document.getElementById('nextBtnText').textContent = 
                    index === totalQuestions - 1 ? texts.finishBtnText : texts.nextBtnText;
                
                // عرض السؤال الأول
                renderQuestion();
                
            } catch (error) {
                console.error("Error:", error);
                document.getElementById('result').innerHTML = `
                    <div class="result-box">
                        <h3 style="color: var(--error);">${texts.errorCreatingTest}</h3>
                        <p>${texts.checkConnection}</p>
                        <button class="btn btn-secondary" style="margin-top: 20px;" onclick="manualQuiz()">
                            <i class="fas fa-redo"></i>
                            ${texts.tryAgain}
                        </button>
                    </div>
                `;
            }
        }
        
        // إنشاء اختبار من ملف
        async function fileQuiz() {
            const fileInput = document.getElementById('fileInput');
            const fileLang = document.getElementById('fileLang').value;
            const fileQCount = document.getElementById('fileQCount').value;
            const texts = translations[fileLang === 'ar' ? 'ar' : 'en'];
            
            if (!fileInput.files.length) {
                alert(texts.noFileSelected);
                return;
            }
            
            // تحديث اللغة الحالية بناءً على اختيار المستخدم
            if (fileLang !== currentLanguage) {
                currentLanguage = fileLang === 'ar' ? 'ar' : 'en';
                updateLanguage();
            }
            
            // عرض حالة التحميل
            document.getElementById('result').innerHTML = `
                <div class="loading">
                    <div class="spinner"></div>
                    <h3 style="color: var(--primary); margin-bottom: 10px;">${texts.loadingQuestions}</h3>
                    <p style="color: #64748b;">${texts.pleaseWait}</p>
                </div>
            `;
            
            const formData = new FormData();
            formData.append("file", fileInput.files[0]);
            formData.append("mode", "questions");
            formData.append("language", fileLang);
            // إضافة عدد الأسئلة المطلوبة
            formData.append("question_count", fileQCount);
            
            try {
                const response = await fetch(BACKEND + "/ask-file", {
                    method: "POST",
                    body: formData
                });
                
                const data = await response.json();
                questions = safeParse(data.result).questions;
                answers = new Array(questions.length).fill(null);
                index = 0;
                totalQuestions = questions.length;
                
                // إظهار زر التالي
                document.getElementById('nextBtnContainer').style.display = 'block';
                
                // تحديث نص زر التالي
                document.getElementById('nextBtnText').textContent = 
                    index === totalQuestions - 1 ? texts.finishBtnText : texts.nextBtnText;
                
                // عرض السؤال الأول
                renderQuestion();
                
            } catch (error) {
                console.error("Error:", error);
                document.getElementById('result').innerHTML = `
                    <div class="result-box">
                        <h3 style="color: var(--error);">${texts.errorProcessingFile}</h3>
                        <p>${texts.checkFileFormat}</p>
                        <button class="btn btn-secondary" style="margin-top: 20px;" onclick="fileQuiz()">
                            <i class="fas fa-redo"></i>
                            ${texts.tryAgain}
                        </button>
                    </div>
                `;
            }
        }
        
        // تلخيص ملف
        async function summarize() {
            const sumFile = document.getElementById('sumFile');
            const sumLang = document.getElementById('sumLang').value;
            const texts = translations[sumLang === 'ar' ? 'ar' : 'en'];
            
            if (!sumFile.files.length) {
                alert(texts.noFileSelected);
                return;
            }
            
            // تحديث اللغة الحالية بناءً على اختيار المستخدم
            if (sumLang !== currentLanguage) {
                currentLanguage = sumLang === 'ar' ? 'ar' : 'en';
                updateLanguage();
            }
            
            // عرض حالة التحميل
            document.getElementById('result').innerHTML = `
                <div class="loading">
                    <div class="spinner"></div>
                    <h3 style="color: var(--primary); margin-bottom: 10px;">${texts.loadingSummary}</h3>
                    <p style="color: #64748b;">${texts.pleaseWait}</p>
                </div>
            `;
            
            const formData = new FormData();
            formData.append("file", sumFile.files[0]);
            formData.append("mode", "summary");
            formData.append("language", sumLang);
            
            try {
                const response = await fetch(BACKEND + "/ask-file", {
                    method: "POST",
                    body: formData
                });
                
                const data = await response.json();
                
                document.getElementById('result').innerHTML = `
                    <div class="result-box">
                        <h2 style="color: var(--primary); margin-bottom: 25px;">
                            <i class="fas fa-file-contract" style="color: var(--secondary);"></i>
                            ${texts.summaryTitleResult}
                        </h2>
                        <div class="summary-box">
                            ${data.result}
                        </div>
                        <button class="btn btn-secondary" style="margin-top: 25px;" onclick="window.print()">
                            <i class="fas fa-print"></i>
                            ${texts.printSummary}
                        </button>
                    </div>
                `;
                
            } catch (error) {
                console.error("Error:", error);
                document.getElementById('result').innerHTML = `
                    <div class="result-box">
                        <h3 style="color: var(--error);">${texts.errorSummarizing}</h3>
                        <p>${texts.checkFileFormat}</p>
                        <button class="btn btn-secondary" style="margin-top: 20px;" onclick="summarize()">
                            <i class="fas fa-redo"></i>
                            ${texts.tryAgain}
                        </button>
                    </div>
                `;
            }
        }
        
        // عرض السؤال الحالي
        function renderQuestion() {
            const q = questions[index];
            const texts = translations[currentLanguage];
            
            // حساب التقدم
            const progressPercent = ((index + 1) / totalQuestions) * 100;
            
            // إعداد تغذية راجعة للخيارات الخاطئة
            currentQuestionWrongFeedbacks = [];
            q.options.forEach((option, i) => {
                if (i !== q.answer) {
                    currentQuestionWrongFeedbacks.push({
                        option: option,
                        explanation: q.explanations[i]
                    });
                }
            });
            
            let html = `
                <div class="progress-container">
                    <div class="progress-bar" style="width: ${progressPercent}%"></div>
                    <div class="progress-info">
                        <span>${texts.questionOf} ${index + 1} ${texts.of} ${totalQuestions}</span>
                        <span>${Math.round(progressPercent)}%</span>
                    </div>
                </div>
                
                <div class="result-box">
                    <h2 style="color: var(--primary); margin-bottom: 30px;">${q.q}</h2>
            `;
            
            q.options.forEach((option, i) => {
                let cardClass = "option-card";
                
                if (answers[index] !== null) {
                    if (i === q.answer) {
                        cardClass += " correct";
                        // إظهار التغذية الراجعة للخيار الصحيح فقط
                        cardClass += " show-feedback";
                    } else if (i === answers[index]) {
                        cardClass += " incorrect";
                    }
                } else if (i === answers[index]) {
                    cardClass += " selected";
                }
                
                // استخدام أرقام عربية أو إنجليزية بناءً على اللغة
                const optionNumber = currentLanguage === 'ar' ? 
                    String.fromCharCode(1632 + i + 1) : 
                    (i + 1);
                
                html += `
                    <div class="${cardClass}" onclick="choose(${i})">
                        <div style="display: flex; align-items: center;">
                            <div class="option-number">${optionNumber}</div>
                            <div style="font-size: 1.1rem; font-weight: 500;">${option}</div>
                        </div>
                        <div class="feedback">${q.explanations[i]}</div>
                    </div>
                `;
            });
            
            // زر عرض شرح الإجابات الخاطئة (يظهر فقط بعد الإجابة)
            if (answers[index] !== null && currentQuestionWrongFeedbacks.length > 0) {
                html += `
                    <button class="btn btn-wrong-answers" onclick="toggleWrongAnswers()" id="wrongAnswersBtn">
                        <i class="fas fa-lightbulb"></i>
                        ${texts.showWrongAnswers}
                    </button>
                    
                    <div class="wrong-feedback" id="wrongAnswersContainer">
                        <h4 style="color: var(--warning); margin-bottom: 10px;">${texts.wrongAnswersTitle}</h4>
                `;
                
                currentQuestionWrongFeedbacks.forEach((feedback, i) => {
                    const optionNumber = currentLanguage === 'ar' ? 
                        String.fromCharCode(1632 + i + 2) : 
                        (i + 2);
                    
                    html += `
                        <div style="margin-bottom: 10px;">
                            <strong>${optionNumber}. ${feedback.option}:</strong>
                            <p style="margin-top: 5px; color: #555;">${feedback.explanation}</p>
                        </div>
                    `;
                });
                
                html += `</div>`;
            }
            
            html += `</div>`;
            
            document.getElementById('result').innerHTML = html;
            
            // تحديث نص زر التالي
            const nextBtnText = document.getElementById('nextBtnText');
            if (index === totalQuestions - 1) {
                nextBtnText.textContent = texts.finishBtnText;
            } else {
                nextBtnText.textContent = texts.nextBtnText;
            }
        }
        
        // تبديل عرض/إخفاء شرح الإجابات الخاطئة
        function toggleWrongAnswers() {
            const container = document.getElementById('wrongAnswersContainer');
            const btn = document.getElementById('wrongAnswersBtn');
            const texts = translations[currentLanguage];
            
            if (container.classList.contains('show')) {
                container.classList.remove('show');
                btn.innerHTML = `<i class="fas fa-lightbulb"></i> ${texts.showWrongAnswers}`;
            } else {
                container.classList.add('show');
                btn.innerHTML = `<i class="fas fa-times"></i> ${texts.hideWrongAnswers}`;
            }
        }
        
        // اختيار إجابة
        function choose(i) {
            if (answers[index] !== null) return;
            
            answers[index] = i;
            const q = questions[index];
            const texts = translations[currentLanguage];
            
            // تشغيل الصوت المناسب
            if (i === q.answer) {
                correctSound.currentTime = 0;
                correctSound.play().catch(e => console.log("Audio play failed:", e));
                showNotification(texts.correctNotification, 'correct');
            } else {
                incorrectSound.currentTime = 0;
                incorrectSound.play().catch(e => console.log("Audio play failed:", e));
                showNotification(texts.incorrectNotification, 'incorrect');
            }
            
            // إعادة عرض السؤال مع التصحيح
            setTimeout(() => {
                renderQuestion();
            }, 300);
        }
        
        // الانتقال للسؤال التالي
        function nextQuestion() {
            const texts = translations[currentLanguage];
            
            if (answers[index] === null) {
                alert(texts.chooseAnswer);
                return;
            }
            
            // تشغيل صوت الانتقال
            nextSound.currentTime = 0;
            nextSound.play().catch(e => console.log("Audio play failed:", e));
            
            if (index < totalQuestions - 1) {
                index++;
                renderQuestion();
            } else {
                // تشغيل صوت الانتهاء
                completeSound.currentTime = 0;
                completeSound.play().catch(e => console.log("Audio play failed:", e));
                
                // حساب النتيجة النهائية
                let correctCount = 0;
                answers.forEach((answer, i) => {
                    if (answer === questions[i].answer) {
                        correctCount++;
                    }
                });
                
                const scorePercent = Math.round((correctCount / totalQuestions) * 100);
                let message = "";
                
                if (scorePercent >= 90) {
                    message = texts.excellent;
                } else if (scorePercent >= 70) {
                    message = texts.veryGood;
                } else if (scorePercent >= 50) {
                    message = texts.good;
                } else {
                    message = texts.needsImprovement;
                }
                
                document.getElementById('result').innerHTML = `
                    <div class="result-box">
                        <h2 style="color: var(--primary); margin-bottom: 30px;">${texts.resultTitle}</h2>
                        
                        <div class="score-circle">
                            <div class="score-value">${currentLanguage === 'ar' ? correctCount : correctCount}</div>
                            <div class="score-total">${texts.of} ${currentLanguage === 'ar' ? totalQuestions : totalQuestions}</div>
                        </div>
                        
                        <div class="result-message">${message}</div>
                        
                        <p style="margin-bottom: 25px; font-size: 1.1rem;">${texts.successRate} <strong>${scorePercent}%</strong></p>
                        
                        <div style="display: flex; gap: 15px; justify-content: center; margin-top: 30px;">
                            <button class="btn btn-secondary" onclick="index = 0; answers = new Array(questions.length).fill(null); renderQuestion();">
                                <i class="fas fa-redo"></i>
                                ${texts.retryTest}
                            </button>
                            <button class="btn btn-primary" onclick="showTab('manual')">
                                <i class="fas fa-plus"></i>
                                ${texts.newTest}
                            </button>
                        </div>
                    </div>
                `;
                
                document.getElementById('nextBtnContainer').style.display = 'none';
            }
        }
        
        // دالة مساعدة للتبديل بين التبويبات
        function showTab(tabName) {
            document.querySelectorAll('.tab-btn').forEach(btn => {
                btn.classList.remove('active');
                if (btn.getAttribute('data-tab') === tabName) {
                    btn.classList.add('active');
                }
            });
            
            document.querySelectorAll('.tab-content').forEach(content => {
                content.classList.remove('active');
            });
            
            document.getElementById(`${tabName}-tab`).classList.add('active');
            document.getElementById('result').innerHTML = '';
            document.getElementById('nextBtnContainer').style.display = 'none';
        }
        
        // بدء التطبيق
        document.addEventListener('DOMContentLoaded', function() {
            // تحديث اللغة الافتراضية
            updateLanguage();
            
            // إضافة تأثيرات للعناصر
            document.querySelectorAll('.btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    this.classList.add('pulse');
                    setTimeout(() => {
                        this.classList.remove('pulse');
                    }, 300);
                });
            });
        });
    </script>
</body>
</html>