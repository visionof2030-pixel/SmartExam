<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <!-- إعدادات Meta محسنة للتوافق مع جميع الأجهزة -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=5.0">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="default">
    <meta name="theme-color" content="#0c2d41">
    <meta name="mobile-web-app-capable" content="yes">
    <meta name="format-detection" content="telephone=no">
    <title>نُبـل - أداة التعلم الذكية</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@300;400;500;700;800;900&display=swap" rel="stylesheet">
    
    <style>
        /* CSS Reset أولاً */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
        }
        
        html, body {
            width: 100%;
            height: 100%;
            overflow-x: hidden;
            -webkit-text-size-adjust: 100%;
        }
        
        :root {
            --primary-dark: #0c2d41;
            --primary: #1a4865;
            --primary-light: #2a6a8f;
            --accent: #2a9d8f;
            --accent-light: #4ecdc4;
            --accent-dark: #21867a;
            --accent-transparent: rgba(42, 157, 143, 0.15);
            --danger: #e76f51;
            --danger-light: #f4a261;
            --warning: #e9c46a;
            --light: #f8f9fa;
            --dark: #212529;
            --gray: #6c757d;
            --gray-light: #e9ecef;
            --success-bg: rgba(42, 157, 143, 0.15);
            --error-bg: rgba(231, 111, 81, 0.15);
            --shadow: 0 8px 30px rgba(0, 0, 0, 0.15);
            --shadow-light: 0 4px 15px rgba(0, 0, 0, 0.08);
            --border-radius: 16px;
            --border-radius-sm: 10px;
            --transition: all 0.3s ease;
            --gold: #ffd166;
            --gold-light: #ffe8a3;
            --safe-top: env(safe-area-inset-top);
            --safe-bottom: env(safe-area-inset-bottom);
            --safe-left: env(safe-area-inset-left);
            --safe-right: env(safe-area-inset-right);
        }
        
        body {
            font-family: 'Tajawal', -apple-system, BlinkMacSystemFont, sans-serif;
            background: linear-gradient(135deg, var(--primary-dark) 0%, var(--primary) 50%, var(--primary-light) 100%);
            color: var(--light);
            min-height: 100vh;
            min-height: -webkit-fill-available;
            line-height: 1.5;
            padding: 0;
            margin: 0;
        }
        
        /* تصحيح لـ iOS Safari */
        @supports (-webkit-touch-callout: none) {
            body {
                min-height: -webkit-fill-available;
            }
        }
        
        /* البار العلوي - مصحح للجوال */
        .top-bar {
            background: rgba(12, 45, 65, 0.95);
            padding: 12px 16px;
            text-align: center;
            font-size: 14px;
            color: var(--accent-light);
            font-weight: 500;
            position: relative;
            width: 100%;
        }
        
        /* الهيدر الرئيسي - مصحح للجوال */
        .header {
            padding: 20px 16px;
            text-align: center;
            background: linear-gradient(135deg, rgba(12, 45, 65, 0.9) 0%, rgba(26, 72, 101, 0.9) 100%);
            position: relative;
            overflow: hidden;
            width: 100%;
        }
        
        .logo-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 12px;
            margin-bottom: 15px;
        }
        
        .logo-icon {
            width: 60px;
            height: 60px;
            background: linear-gradient(135deg, var(--accent) 0%, var(--accent-light) 100%);
            border-radius: 16px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2rem;
            color: white;
            box-shadow: 0 6px 20px rgba(42, 157, 143, 0.4);
            transform: rotate(-5deg);
        }
        
        .logo-text {
            font-size: 2.5rem;
            font-weight: 900;
            color: #4ecdc4;
            text-shadow: 0 3px 10px rgba(0, 0, 0, 0.2);
            position: relative;
        }
        
        .logo-text::after {
            content: "ُ";
            position: absolute;
            font-size: 1.5rem;
            color: #ffd166;
            right: -4px;
            top: -10px;
        }
        
        .header p {
            font-size: 1.1rem;
            color: var(--gray-light);
            max-width: 100%;
            margin: 0 auto;
            opacity: 0.95;
            font-weight: 300;
            line-height: 1.6;
            padding: 0 10px;
        }
        
        /* الحاوية الرئيسية - مصححة للجوال */
        .container {
            width: 100%;
            max-width: 100%;
            padding: 20px 16px;
            margin: 0 auto;
            box-sizing: border-box;
        }
        
        /* بطاقة التحكم - مصححة للجوال */
        .control-card {
            background: rgba(255, 255, 255, 0.07);
            border-radius: var(--border-radius);
            padding: 20px;
            margin-bottom: 20px;
            border: 1px solid rgba(255, 255, 255, 0.12);
            box-shadow: var(--shadow-light);
            position: relative;
            width: 100%;
            box-sizing: border-box;
        }
        
        .control-card::before {
            content: '';
            position: absolute;
            top: 0;
            right: 0;
            width: 100%;
            height: 4px;
            background: linear-gradient(to left, var(--accent), var(--accent-light));
            border-radius: var(--border-radius) var(--border-radius) 0 0;
        }
        
        /* أزرار التبويب - مصححة للجوال */
        .mode-tabs {
            display: flex;
            flex-direction: column;
            gap: 12px;
            margin-bottom: 20px;
            width: 100%;
        }
        
        .mode-tab {
            background: rgba(255, 255, 255, 0.05);
            border: 2px solid rgba(255, 255, 255, 0.1);
            border-radius: var(--border-radius-sm);
            padding: 16px 12px;
            text-align: center;
            cursor: pointer;
            transition: var(--transition);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            position: relative;
            width: 100%;
            min-height: 60px;
        }
        
        .mode-tab.active {
            background: rgba(42, 157, 143, 0.2);
            border-color: var(--accent);
            box-shadow: 0 4px 15px rgba(42, 157, 143, 0.2);
        }
        
        .mode-tab i {
            font-size: 1.8rem;
            margin-bottom: 8px;
            color: var(--accent-light);
        }
        
        .mode-tab span {
            font-weight: 700;
            font-size: 1rem;
            color: var(--light);
        }
        
        /* إعدادات التحكم - مصححة للجوال */
        .control-group {
            margin-bottom: 20px;
            width: 100%;
        }
        
        .control-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 700;
            color: var(--accent-light);
            font-size: 1rem;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        select, textarea, input[type="file"] {
            width: 100%;
            padding: 14px 16px;
            background: rgba(255, 255, 255, 0.06);
            border: 2px solid rgba(255, 255, 255, 0.12);
            border-radius: var(--border-radius-sm);
            color: var(--light);
            font-family: 'Tajawal', sans-serif;
            font-size: 16px; /* مهم لمنع التكبير على iOS */
            transition: var(--transition);
            box-sizing: border-box;
            -webkit-appearance: none;
            appearance: none;
        }
        
        textarea {
            min-height: 120px;
            resize: vertical;
            line-height: 1.6;
        }
        
        /* زر التنفيذ - مصحح للجوال */
        .execute-btn {
            width: 100%;
            padding: 18px;
            background: linear-gradient(135deg, var(--accent) 0%, var(--accent-dark) 100%);
            color: white;
            border: none;
            border-radius: var(--border-radius-sm);
            font-family: 'Tajawal', sans-serif;
            font-size: 1.1rem;
            font-weight: 800;
            cursor: pointer;
            transition: var(--transition);
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 12px;
            box-shadow: 0 6px 20px rgba(42, 157, 143, 0.3);
            position: relative;
            margin-top: 10px;
            min-height: 50px;
        }
        
        /* منطقة الإخراج */
        #out {
            margin-top: 20px;
            width: 100%;
        }
        
        /* تصميم الأسئلة - مصحح للجوال */
        .question {
            background: rgba(255, 255, 255, 0.07);
            border-radius: var(--border-radius);
            padding: 20px 16px;
            margin-bottom: 20px;
            border: 1px solid rgba(255, 255, 255, 0.12);
            box-shadow: var(--shadow-light);
            position: relative;
            width: 100%;
            box-sizing: border-box;
        }
        
        .question-header {
            display: flex;
            flex-direction: column-reverse;
            gap: 15px;
            margin-bottom: 20px;
        }
        
        .question-text {
            font-size: 1.2rem;
            font-weight: 700;
            color: var(--light);
            line-height: 1.5;
            width: 100%;
        }
        
        .question-number {
            background: linear-gradient(135deg, var(--accent) 0%, var(--accent-light) 100%);
            color: white;
            width: 40px;
            height: 40px;
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 800;
            font-size: 1.2rem;
            box-shadow: 0 4px 12px rgba(42, 157, 143, 0.3);
            align-self: flex-start;
        }
        
        /* خيارات الأسئلة - مصححة للجوال */
        .options {
            display: flex;
            flex-direction: column;
            gap: 12px;
            margin-bottom: 20px;
            width: 100%;
        }
        
        .option {
            background: rgba(255, 255, 255, 0.05);
            border: 2px solid rgba(255, 255, 255, 0.12);
            border-radius: var(--border-radius-sm);
            padding: 16px;
            cursor: pointer;
            transition: var(--transition);
            display: flex;
            align-items: center;
            gap: 12px;
            position: relative;
            width: 100%;
            min-height: 60px;
        }
        
        .option-letter {
            background: rgba(255, 255, 255, 0.1);
            color: var(--light);
            width: 36px;
            height: 36px;
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 800;
            flex-shrink: 0;
            font-size: 1rem;
        }
        
        .option-text {
            font-size: 1rem;
            font-weight: 600;
            flex: 1;
        }
        
        /* تصميم البطاقات التعليمية - مصحح للجوال */
        .flashcard {
            background: rgba(255, 255, 255, 0.07);
            border-radius: var(--border-radius);
            padding: 30px 20px;
            margin-bottom: 20px;
            border: 1px solid rgba(255, 255, 255, 0.12);
            box-shadow: var(--shadow-light);
            min-height: 300px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            transition: var(--transition);
            text-align: center;
            width: 100%;
        }
        
        .flashcard-front, .flashcard-back {
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--light);
            line-height: 1.6;
            max-width: 100%;
            padding: 0 10px;
        }
        
        .flashcard-back {
            color: var(--accent-light);
        }
        
        .flashcard-counter {
            margin-top: 20px;
            font-size: 1rem;
            color: var(--gray-light);
            font-weight: 600;
            background: rgba(255, 255, 255, 0.05);
            padding: 8px 20px;
            border-radius: 20px;
        }
        
        .flashcard-nav {
            display: flex;
            justify-content: center;
            gap: 12px;
            margin-top: 20px;
            width: 100%;
            flex-wrap: wrap;
        }
        
        .flashcard-btn {
            background: rgba(255, 255, 255, 0.07);
            border: 2px solid rgba(255, 255, 255, 0.12);
            border-radius: var(--border-radius-sm);
            color: var(--light);
            padding: 14px 20px;
            font-family: 'Tajawal', sans-serif;
            font-size: 1rem;
            font-weight: 700;
            cursor: pointer;
            transition: var(--transition);
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 8px;
            flex: 1;
            min-width: 120px;
            min-height: 50px;
        }
        
        /* تصميم التلخيص - مصحح للجوال */
        .summary {
            background: rgba(255, 255, 255, 0.07);
            border-radius: var(--border-radius);
            padding: 25px 20px;
            margin-bottom: 20px;
            border: 1px solid rgba(255, 255, 255, 0.12);
            box-shadow: var(--shadow-light);
            position: relative;
            width: 100%;
        }
        
        .summary-title {
            font-size: 1.8rem;
            font-weight: 900;
            margin-bottom: 25px;
            color: var(--gold);
            text-align: center;
            border-bottom: 2px solid rgba(255, 255, 255, 0.1);
            padding-bottom: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 12px;
            flex-wrap: wrap;
        }
        
        .summary-point {
            margin-bottom: 16px;
            padding: 16px;
            background: rgba(255, 255, 255, 0.04);
            border-radius: var(--border-radius-sm);
            border-right: 4px solid;
            transition: var(--transition);
            position: relative;
            width: 100%;
        }
        
        .summary-point-text {
            font-size: 1rem;
            line-height: 1.6;
            font-weight: 500;
        }
        
        /* تخصيص خيارات تحميل الملف - مصحح للجوال */
        .file-upload-area {
            width: 100%;
            padding: 16px;
            background: rgba(255, 255, 255, 0.06);
            border: 2px solid rgba(255, 255, 255, 0.12);
            border-radius: var(--border-radius-sm);
            color: var(--light);
            transition: var(--transition);
            text-align: center;
            cursor: pointer;
            margin-bottom: 15px;
            box-sizing: border-box;
        }
        
        .file-upload-label {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 12px;
            cursor: pointer;
        }
        
        .file-upload-label i {
            font-size: 2.5rem;
            color: var(--accent-light);
        }
        
        .upload-options {
            display: flex;
            flex-direction: column;
            gap: 10px;
            margin-top: 10px;
            width: 100%;
        }
        
        .upload-option-btn {
            background: rgba(42, 157, 143, 0.2);
            border: 1px solid rgba(42, 157, 143, 0.4);
            border-radius: var(--border-radius-sm);
            padding: 14px;
            color: var(--accent-light);
            cursor: pointer;
            transition: var(--transition);
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            font-weight: 600;
            width: 100%;
            min-height: 50px;
        }
        
        .image-preview {
            margin-top: 15px;
            max-width: 100%;
            border-radius: var(--border-radius-sm);
            display: none;
        }
        
        .image-preview img {
            max-width: 100%;
            max-height: 250px;
            border-radius: var(--border-radius-sm);
            object-fit: contain;
        }
        
        .camera-container {
            width: 100%;
            height: 250px;
            background: rgba(0, 0, 0, 0.2);
            border-radius: var(--border-radius-sm);
            display: flex;
            justify-content: center;
            align-items: center;
            position: relative;
            overflow: hidden;
            margin-top: 15px;
            display: none;
        }
        
        #camera-feed {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        .camera-controls {
            position: absolute;
            bottom: 15px;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            gap: 15px;
            z-index: 10;
        }
        
        .camera-btn {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: rgba(231, 111, 81, 0.8);
            border: 2px solid white;
            color: white;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            transition: var(--transition);
            font-size: 1.2rem;
        }
        
        /* التحميل */
        .loading {
            text-align: center;
            padding: 40px 20px;
        }
        
        .spinner {
            width: 50px;
            height: 50px;
            border: 4px solid rgba(255, 255, 255, 0.1);
            border-top: 4px solid var(--accent);
            border-radius: 50%;
            animation: spin 1s linear infinite;
            margin: 0 auto 20px;
        }
        
        .loading-text {
            font-size: 1.2rem;
            font-weight: 700;
            color: var(--accent-light);
        }
        
        /* الرسائل */
        .message {
            padding: 20px;
            border-radius: var(--border-radius-sm);
            margin-bottom: 20px;
            text-align: center;
            font-weight: 700;
            font-size: 1.1rem;
            border-right: 4px solid;
            width: 100%;
            box-sizing: border-box;
        }
        
        /* الأنيميشن */
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        /* إخفاء العناصر */
        .hidden {
            display: none !important;
        }
        
        /* استعلامات الوسائط للشاشات المتوسطة والكبيرة */
        @media (min-width: 768px) {
            .container {
                max-width: 90%;
                padding: 30px 20px;
            }
            
            .mode-tabs {
                flex-direction: row;
                flex-wrap: wrap;
            }
            
            .mode-tab {
                flex: 1;
                min-width: 150px;
            }
            
            .question-header {
                flex-direction: row;
                justify-content: space-between;
                align-items: flex-start;
            }
            
            .options {
                display: grid;
                grid-template-columns: repeat(2, 1fr);
                gap: 15px;
            }
            
            .upload-options {
                flex-direction: row;
                flex-wrap: wrap;
            }
            
            .upload-option-btn {
                flex: 1;
                min-width: 140px;
            }
            
            .flashcard-nav {
                flex-wrap: nowrap;
            }
        }
        
        @media (min-width: 1024px) {
            .container {
                max-width: 1000px;
                padding: 40px 20px;
            }
            
            .options {
                grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            }
            
            .flashcard {
                min-height: 400px;
                padding: 50px 40px;
            }
            
            .flashcard-front, .flashcard-back {
                font-size: 2rem;
            }
        }
        
        /* تصحيحات خاصة لأجهزة iOS */
        @supports (-webkit-touch-callout: none) {
            select, textarea, input[type="file"], button, .execute-btn {
                font-size: 16px !important;
            }
            
            body {
                -webkit-user-select: none;
                user-select: none;
            }
        }
        
        /* تصحيحات خاصة للوضع الأفقي */
        @media (orientation: landscape) and (max-height: 500px) {
            .header {
                padding: 15px;
            }
            
            .logo-container {
                flex-direction: row;
                justify-content: center;
                gap: 20px;
            }
            
            .logo-icon {
                width: 50px;
                height: 50px;
                font-size: 1.5rem;
            }
            
            .logo-text {
                font-size: 2rem;
            }
            
            .header p {
                font-size: 1rem;
            }
            
            .control-card {
                padding: 15px;
            }
            
            .mode-tab {
                padding: 12px 8px;
                min-height: 50px;
            }
            
            .mode-tab i {
                font-size: 1.5rem;
                margin-bottom: 5px;
            }
            
            .mode-tab span {
                font-size: 0.9rem;
            }
        }
    </style>
</head>

<body>
    <!-- البار العلوي -->
    <div class="top-bar">
        <i class="fas fa-code"></i> تطوير: فهد الخالدي | نُبـل - أداة التعلم الذكية
    </div>
    
    <!-- الهيدر -->
    <div class="header">
        <div class="logo-container">
            <div class="logo-icon">
                <i class="fas fa-book-open"></i>
            </div>
            <h1 class="logo-text">نُبـل</h1>
        </div>
        <p>تعلمٌ أذكى… تحصيلٌ أرقى</p>
    </div>
    
    <!-- الحاوية الرئيسية -->
    <div class="container">
        <!-- بطاقة التحكم -->
        <div class="control-card">
            <!-- أزرار التبويب -->
            <div class="mode-tabs">
                <div class="mode-tab active" data-mode="manual">
                    <i class="fas fa-edit"></i>
                    <span>اختبار يدوي</span>
                </div>
                <div class="mode-tab" data-mode="file">
                    <i class="fas fa-file-alt"></i>
                    <span>اختبار من ملف</span>
                </div>
                <div class="mode-tab" data-mode="flashcards">
                    <i class="fas fa-layer-group"></i>
                    <span>فلاش كاردز</span>
                </div>
                <div class="mode-tab" data-mode="summary">
                    <i class="fas fa-scroll"></i>
                    <span>تلخيص</span>
                </div>
            </div>
            
            <!-- إعدادات التحكم -->
            <div class="control-group">
                <label for="language"><i class="fas fa-language"></i> لغة المحتوى</label>
                <select id="language">
                    <option value="ar">عربي</option>
                    <option value="en">English</option>
                </select>
            </div>
            
            <div class="control-group">
                <label for="num"><i class="fas fa-list-ol"></i> عدد الأسئلة/البطاقات</label>
                <select id="num">
                    <option value="5">5</option>
                    <option value="10" selected>10</option>
                    <option value="20">20</option>
                    <option value="30">30</option>
                    <option value="40">40</option>
                    <option value="50">50</option>
                    <option value="60">60</option>
                </select>
            </div>
            
            <!-- منطقة الإدخال اليدوي -->
            <div class="control-group" id="topic-group">
                <label for="topic"><i class="fas fa-book-open"></i> اكتب الموضوع هنا</label>
                <textarea id="topic" rows="4" placeholder="اكتب الموضوع أو النص الذي تريد إنشاء أسئلة أو تلخيص منه..."></textarea>
            </div>
            
            <!-- منطقة تحميل الملف -->
            <div class="control-group hidden" id="file-group">
                <label for="file"><i class="fas fa-upload"></i> اختر مصدر المحتوى</label>
                
                <!-- خيارات تحميل الملف -->
                <div class="file-upload-area">
                    <label class="file-upload-label">
                        <i class="fas fa-cloud-upload-alt"></i>
                        <span id="upload-instruction">انقر لاختيار ملف أو استخدم الخيارات أدناه</span>
                        
                        <div class="upload-options">
                            <div class="upload-option-btn active" data-upload-type="file">
                                <i class="fas fa-file"></i> ملف نصي
                            </div>
                            <div class="upload-option-btn" data-upload-type="image">
                                <i class="fas fa-image"></i> صورة
                            </div>
                            <div class="upload-option-btn" data-upload-type="camera">
                                <i class="fas fa-camera"></i> الكاميرا
                            </div>
                        </div>
                        
                        <!-- حقل اختيار الملف المخفي -->
                        <input type="file" id="file-input" accept=".txt,.pdf,.doc,.docx,.jpg,.jpeg,.png,.gif">
                        
                        <!-- حقل اختيار الصورة -->
                        <input type="file" id="image-input" accept="image/*" class="hidden">
                        
                        <!-- معاينة الصورة -->
                        <div class="image-preview" id="image-preview">
                            <img id="preview-image" src="" alt="معاينة الصورة">
                        </div>
                        
                        <!-- حاوية الكاميرا -->
                        <div class="camera-container" id="camera-container">
                            <video id="camera-feed" autoplay playsinline></video>
                            <div class="camera-controls">
                                <div class="camera-btn capture" id="capture-btn">
                                    <i class="fas fa-camera"></i>
                                </div>
                                <div class="camera-btn" id="cancel-camera-btn">
                                    <i class="fas fa-times"></i>
                                </div>
                            </div>
                        </div>
                    </label>
                </div>
                
                <div class="message" id="file-message" style="display: none;">
                    <i class="fas fa-file"></i> يمكنك رفع ملفات نصية أو PDF أو Word أو صور
                </div>
            </div>
            
            <!-- زر التنفيذ -->
            <button class="execute-btn" onclick="start()">
                <i class="fas fa-play-circle"></i> بدء التنفيذ
            </button>
        </div>
        
        <!-- منطقة الإخراج -->
        <div id="out"></div>
    </div>
    
    <!-- الأصوات -->
    <audio id="correct-sound" preload="auto">
        <source src="https://assets.mixkit.co/sfx/preview/mixkit-correct-answer-tone-2870.mp3" type="audio/mpeg">
    </audio>
    
    <audio id="wrong-sound" preload="auto">
        <source src="https://assets.mixkit.co/sfx/preview/mixkit-wrong-answer-fail-notification-946.mp3" type="audio/mpeg">
    </audio>

    <script>
        // كشف نوع الجهاز
        const isMobile = /Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(navigator.userAgent);
        const isIOS = /iPad|iPhone|iPod/.test(navigator.userAgent) && !window.MSStream;
        
        const API = "https://smarttest-0ycc.onrender.com";
        
        // العناصر الأساسية
        const modeTabs = document.querySelectorAll('.mode-tab');
        const topicGroup = document.getElementById('topic-group');
        const fileGroup = document.getElementById('file-group');
        const topic = document.getElementById('topic');
        const out = document.getElementById('out');
        const language = document.getElementById('language');
        const num = document.getElementById('num');
        const correctSound = document.getElementById('correct-sound');
        const wrongSound = document.getElementById('wrong-sound');
        
        // عناصر تحميل الملفات الجديدة
        const fileInput = document.getElementById('file-input');
        const imageInput = document.getElementById('image-input');
        const uploadOptions = document.querySelectorAll('.upload-option-btn');
        const uploadInstruction = document.getElementById('upload-instruction');
        const imagePreview = document.getElementById('image-preview');
        const previewImage = document.getElementById('preview-image');
        const cameraContainer = document.getElementById('camera-container');
        const cameraFeed = document.getElementById('camera-feed');
        const captureBtn = document.getElementById('capture-btn');
        const cancelCameraBtn = document.getElementById('cancel-camera-btn');
        
        // متغيرات التحكم
        let currentUploadType = 'file';
        let currentFile = null;
        let stream = null;
        
        // تهيئة وضع التبويب
        modeTabs.forEach(tab => {
            tab.addEventListener('click', () => {
                // إزالة النشط من جميع الألسنة
                modeTabs.forEach(t => t.classList.remove('active'));
                // إضافة النشط للسان المحدد
                tab.classList.add('active');
                
                // تحديث الواجهة بناءً على الوضع المحدد
                const mode = tab.dataset.mode;
                
                if (mode === 'manual') {
                    topicGroup.classList.remove('hidden');
                    fileGroup.classList.add('hidden');
                } else {
                    topicGroup.classList.add('hidden');
                    fileGroup.classList.remove('hidden');
                    
                    // عرض رسالة إرشادية للملف
                    const fileMessage = document.getElementById('file-message');
                    if (fileMessage) {
                        fileMessage.style.display = 'block';
                        fileMessage.classList.remove('success', 'error');
                        fileMessage.classList.add('success');
                        fileMessage.innerHTML = '<i class="fas fa-file"></i> يمكنك رفع ملفات نصية أو PDF أو Word أو صور';
                    }
                }
            });
        });
        
        // تغيير لغة المحتوى
        language.addEventListener('change', function() {
            const isEnglish = this.value === 'en';
            document.body.classList.toggle('english-mode', isEnglish);
            
            // تحديث النصوص حسب اللغة
            if (isEnglish) {
                document.querySelector('.top-bar').innerHTML = '<i class="fas fa-code"></i> Development: Fahad Al-Khalidi | Nubl - Smart Learning Tool';
                document.querySelector('.header p').textContent = 'Smarter Learning... Better Achievement';
                document.querySelector('.execute-btn').innerHTML = '<i class="fas fa-play-circle"></i> Start Processing';
                document.querySelectorAll('.mode-tab span')[0].textContent = 'Manual Test';
                document.querySelectorAll('.mode-tab span')[1].textContent = 'Test from File';
                document.querySelectorAll('.mode-tab span')[2].textContent = 'Flash Cards';
                document.querySelectorAll('.mode-tab span')[3].textContent = 'Summary';
                document.querySelector('label[for="language"]').innerHTML = '<i class="fas fa-language"></i> Content Language';
                document.querySelector('label[for="num"]').innerHTML = '<i class="fas fa-list-ol"></i> Number of Questions/Cards';
                document.querySelector('label[for="topic"]').innerHTML = '<i class="fas fa-book-open"></i> Write the topic here';
                document.querySelector('#topic').placeholder = 'Write the topic or text you want to create questions or summarize from...';
                document.querySelector('label[for="file"]').innerHTML = '<i class="fas fa-upload"></i> Choose content source';
                uploadInstruction.textContent = 'Click to choose a file or use the options below';
                document.querySelectorAll('.upload-option-btn')[0].innerHTML = '<i class="fas fa-file"></i> Text File';
                document.querySelectorAll('.upload-option-btn')[1].innerHTML = '<i class="fas fa-image"></i> Image';
                document.querySelectorAll('.upload-option-btn')[2].innerHTML = '<i class="fas fa-camera"></i> Camera';
                
                // تحديث رسالة الملف
                const fileMessage = document.getElementById('file-message');
                if (fileMessage) {
                    fileMessage.innerHTML = '<i class="fas fa-file"></i> You can upload text files, PDF, Word, or images';
                }
            } else {
                document.querySelector('.top-bar').innerHTML = '<i class="fas fa-code"></i> تطوير: فهد الخالدي | نُبـل - أداة التعلم الذكية';
                document.querySelector('.header p').textContent = 'تعلمٌ أذكى… تحصيلٌ أرقى';
                document.querySelector('.execute-btn').innerHTML = '<i class="fas fa-play-circle"></i> بدء التنفيذ';
                document.querySelectorAll('.mode-tab span')[0].textContent = 'اختبار يدوي';
                document.querySelectorAll('.mode-tab span')[1].textContent = 'اختبار من ملف';
                document.querySelectorAll('.mode-tab span')[2].textContent = 'فلاش كاردز';
                document.querySelectorAll('.mode-tab span')[3].textContent = 'تلخيص';
                document.querySelector('label[for="language"]').innerHTML = '<i class="fas fa-language"></i> لغة المحتوى';
                document.querySelector('label[for="num"]').innerHTML = '<i class="fas fa-list-ol"></i> عدد الأسئلة/البطاقات';
                document.querySelector('label[for="topic"]').innerHTML = '<i class="fas fa-book-open"></i> اكتب الموضوع هنا';
                document.querySelector('#topic').placeholder = 'اكتب الموضوع أو النص الذي تريد إنشاء أسئلة أو تلخيص منه...';
                document.querySelector('label[for="file"]').innerHTML = '<i class="fas fa-upload"></i> اختر مصدر المحتوى';
                uploadInstruction.textContent = 'انقر لاختيار ملف أو استخدم الخيارات أدناه';
                document.querySelectorAll('.upload-option-btn')[0].innerHTML = '<i class="fas fa-file"></i> ملف نصي';
                document.querySelectorAll('.upload-option-btn')[1].innerHTML = '<i class="fas fa-image"></i> صورة';
                document.querySelectorAll('.upload-option-btn')[2].innerHTML = '<i class="fas fa-camera"></i> الكاميرا';
                
                // تحديث رسالة الملف
                const fileMessage = document.getElementById('file-message');
                if (fileMessage) {
                    fileMessage.innerHTML = '<i class="fas fa-file"></i> يمكنك رفع ملفات نصية أو PDF أو Word أو صور';
                }
            }
        });
        
        // إدارة خيارات التحميل
        uploadOptions.forEach(option => {
            option.addEventListener('click', function() {
                // إزالة النشط من جميع الخيارات
                uploadOptions.forEach(opt => opt.classList.remove('active'));
                // إضافة النشط للخيار المحدد
                this.classList.add('active');
                
                // تحديث نوع التحميل الحالي
                currentUploadType = this.dataset.uploadType;
                
                // تحديث التعليمات
                const isEnglish = language.value === 'en';
                
                if (currentUploadType === 'file') {
                    uploadInstruction.textContent = isEnglish ? 
                        'Click to choose a text file (TXT, PDF, DOC, DOCX)' : 
                        'انقر لاختيار ملف نصي (TXT, PDF, DOC, DOCX)';
                    imagePreview.style.display = 'none';
                    stopCamera();
                } else if (currentUploadType === 'image') {
                    uploadInstruction.textContent = isEnglish ? 
                        'Click to choose an image (JPG, PNG, GIF)' : 
                        'انقر لاختيار صورة (JPG, PNG, GIF)';
                    imagePreview.style.display = 'none';
                    stopCamera();
                } else if (currentUploadType === 'camera') {
                    uploadInstruction.textContent = isEnglish ? 
                        'Click to start the camera' : 
                        'انقر لبدء الكاميرا';
                    imagePreview.style.display = 'none';
                    startCamera();
                }
                
                // إعادة تعيين الملف الحالي
                currentFile = null;
            });
        });
        
        // إدارة اختيار الملف
        fileInput.addEventListener('change', function() {
            if (this.files && this.files[0]) {
                handleFileSelect(this.files[0]);
            }
        });
        
        // إدارة اختيار الصورة
        imageInput.addEventListener('change', function() {
            if (this.files && this.files[0]) {
                handleFileSelect(this.files[0], true);
            }
        });
        
        // دالة معالجة اختيار الملف
        function handleFileSelect(file, isImage = false) {
            currentFile = file;
            
            const isEnglish = language.value === 'en';
            const fileMessage = document.getElementById('file-message');
            
            if (isImage) {
                // عرض معاينة الصورة
                const reader = new FileReader();
                reader.onload = function(e) {
                    previewImage.src = e.target.result;
                    imagePreview.style.display = 'block';
                    
                    if (fileMessage) {
                        fileMessage.innerHTML = isEnglish ? 
                            `<i class="fas fa-image"></i> Selected image: ${file.name}` : 
                            `<i class="fas fa-image"></i> الصورة المحددة: ${file.name}`;
                        fileMessage.classList.remove('success', 'error');
                        fileMessage.classList.add('success');
                        fileMessage.style.display = 'block';
                    }
                };
                reader.readAsDataURL(file);
            } else {
                // ملف نصي
                if (fileMessage) {
                    fileMessage.innerHTML = isEnglish ? 
                        `<i class="fas fa-file"></i> Selected file: ${file.name}` : 
                        `<i class="fas fa-file"></i> الملف المحدد: ${file.name}`;
                    fileMessage.classList.remove('success', 'error');
                    fileMessage.classList.add('success');
                    fileMessage.style.display = 'block';
                }
            }
        }
        
        // بدء تشغيل الكاميرا
        function startCamera() {
            cameraContainer.style.display = 'flex';
            
            // إعدادات الكاميرا المبسطة للجوال
            const constraints = {
                video: {
                    facingMode: 'environment',
                    width: { ideal: 1280 },
                    height: { ideal: 720 }
                },
                audio: false
            };
            
            navigator.mediaDevices.getUserMedia(constraints)
            .then(function(mediaStream) {
                stream = mediaStream;
                cameraFeed.srcObject = stream;
                
                // تفعيل زر التقاط الصورة
                captureBtn.disabled = false;
            })
            .catch(function(err) {
                console.error("Error accessing camera: ", err);
                const isEnglish = language.value === 'en';
                showMessage(isEnglish ? 
                    "Unable to access camera. Please check permissions." : 
                    "تعذر الوصول إلى الكاميرا. الرجاء التحقق من الأذونات.", 
                'error');
                captureBtn.disabled = true;
                
                // العودة إلى خيار الصورة
                uploadOptions.forEach(opt => {
                    if (opt.dataset.uploadType === 'image') {
                        opt.click();
                    }
                });
            });
        }
        
        // إيقاف تشغيل الكاميرا
        function stopCamera() {
            cameraContainer.style.display = 'none';
            
            if (stream) {
                stream.getTracks().forEach(track => {
                    track.stop();
                });
                stream = null;
            }
        }
        
        // التقاط صورة من الكاميرا
        captureBtn.addEventListener('click', function() {
            if (!stream || this.disabled) return;
            
            const canvas = document.createElement('canvas');
            const video = cameraFeed;
            
            // تحديد أبعاد القماش بناءً على أبعاد الفيديو
            canvas.width = video.videoWidth;
            canvas.height = video.videoHeight;
            
            const context = canvas.getContext('2d');
            
            // عكس الصورة للكاميرا الأمامية
            if (stream.getVideoTracks()[0].getSettings().facingMode === 'user') {
                context.translate(canvas.width, 0);
                context.scale(-1, 1);
            }
            
            context.drawImage(video, 0, 0, canvas.width, canvas.height);
            
            canvas.toBlob(function(blob) {
                const file = new File([blob], 'camera-capture.jpg', { type: 'image/jpeg' });
                handleFileSelect(file, true);
                stopCamera();
                
                // العودة إلى خيار الصورة
                uploadOptions.forEach(opt => {
                    if (opt.dataset.uploadType === 'image') {
                        opt.click();
                    }
                });
            }, 'image/jpeg', 0.95);
        });
        
        // إلغاء الكاميرا
        cancelCameraBtn.addEventListener('click', function() {
            stopCamera();
            
            // العودة إلى خيار الملف
            uploadOptions.forEach(opt => {
                if (opt.dataset.uploadType === 'file') {
                    opt.click();
                }
            });
        });
        
        // دالة البدء
        async function start() {
            const activeTab = document.querySelector('.mode-tab.active');
            const mode = activeTab.dataset.mode;
            
            // التحقق من صحة الإدخال
            if (mode === 'manual' && !topic.value.trim()) {
                const isEnglish = language.value === 'en';
                showMessage(isEnglish ? 
                    "Please enter a topic to create questions" : 
                    "الرجاء إدخال موضوع لإنشاء الأسئلة", 
                'error');
                return;
            }
            
            if (mode !== 'manual') {
                if (!currentFile && currentUploadType !== 'camera') {
                    const isEnglish = language.value === 'en';
                    showMessage(isEnglish ? 
                        "Please choose a file or take a picture" : 
                        "الرجاء اختيار ملف أو التقاط صورة", 
                    'error');
                    return;
                }
                
                if (currentUploadType === 'camera' && !previewImage.src) {
                    const isEnglish = language.value === 'en';
                    showMessage(isEnglish ? 
                        "Please take a picture first" : 
                        "الرجاء التقاط صورة أولاً", 
                    'error');
                    return;
                }
            }
            
            // عرض مؤشر التحميل
            showLoading();
            
            try {
                if (mode === 'manual') {
                    await runManual();
                } else {
                    await runFile(mode);
                }
            } catch (error) {
                console.error('Error:', error);
                const isEnglish = language.value === 'en';
                showMessage(isEnglish ? 
                    "An error occurred during processing. Please try again." : 
                    "حدث خطأ أثناء المعالجة. الرجاء المحاولة مرة أخرى.", 
                'error');
            }
        }
        
        // دالة الاختبار اليدوي
        async function runManual() {
            const response = await fetch(API + "/ask", {
                method: "POST",
                headers: { "Content-Type": "application/json" },
                body: JSON.stringify({
                    prompt: topic.value,
                    language: language.value,
                    total_questions: +num.value
                })
            });
            
            const data = await response.json();
            renderQuiz(JSON.parse(extractJSON(data.result)));
        }
        
        // دالة معالجة الملف
        async function runFile(mode) {
            const formData = new FormData();
            
            // إضافة الملف المناسب
            if (currentUploadType === 'image' && currentFile) {
                formData.append("file", currentFile, "image.jpg");
            } else if (currentFile) {
                formData.append("file", currentFile);
            } else if (previewImage.src) {
                // تحويل base64 إلى blob
                const base64Response = await fetch(previewImage.src);
                const blob = await base64Response.blob();
                formData.append("file", blob, "image.jpg");
            }
            
            formData.append("language", language.value);
            formData.append("num_questions", num.value);
            formData.append("mode", mode === 'file' ? "questions" : mode);
            
            const response = await fetch(API + "/ask-file", {
                method: "POST",
                body: formData
            });
            
            if (!response.ok) {
                throw new Error(`HTTP error! status: ${response.status}`);
            }
            
            const data = await response.json();
            
            if (mode === 'summary') {
                renderSummary(data.result);
            } else if (mode === 'flashcards') {
                renderCards(JSON.parse(extractJSON(data.result)));
            } else {
                renderQuiz(JSON.parse(extractJSON(data.result)));
            }
        }
        
        // دالة عرض الأسئلة
        function renderQuiz(data) {
            if (!data || !data.questions || !Array.isArray(data.questions)) {
                const isEnglish = language.value === 'en';
                showMessage(isEnglish ? 
                    "No questions found in received data" : 
                    "لم يتم العثور على أسئلة في البيانات المستلمة", 
                'error');
                return;
            }
            
            const isEnglish = language.value === 'en';
            const letters = isEnglish ? ['A', 'B', 'C', 'D', 'E', 'F'] : ['أ', 'ب', 'ج', 'د', 'هـ', 'و'];
            
            const questionsHTML = data.questions.map((q, qi) => {
                // التحقق من وجود explanations
                const hasExplanations = q.explanations && Array.isArray(q.explanations) && q.explanations.length > 0;
                const correctExplanation = hasExplanations && q.answer !== undefined ? q.explanations[q.answer] : 
                    (isEnglish ? 'No explanation available for the correct answer' : 'لا يوجد شرح متاح للإجابة الصحيحة');
                
                return `
                    <div class="question" data-q="${qi}">
                        <div class="question-header">
                            <div class="question-number">${qi + 1}</div>
                            <div class="question-text">${q.q}</div>
                        </div>
                        
                        <div class="options">
                            ${q.options.map((o, oi) => `
                                <div class="option" data-o="${oi}" data-q="${qi}">
                                    <div class="option-letter">${letters[oi]}</div>
                                    <div class="option-text">${o}</div>
                                </div>
                            `).join('')}
                        </div>
                        
                        <!-- التغذية الراجعة الفورية للإجابة الصحيحة -->
                        <div class="instant-feedback" id="instant-feedback-${qi}">
                            <div class="instant-feedback-header">
                                <i class="fas fa-check-circle"></i>
                                <h3>${isEnglish ? 'Correct Answer Explanation' : 'شرح الإجابة الصحيحة'}</h3>
                            </div>
                            <div class="instant-feedback-content">${correctExplanation}</div>
                        </div>
                        
                        <!-- زر التغذية الراجعة للخيارات الخاطئة -->
                        <button class="wrong-feedback-btn" onclick="toggleWrongFeedback(${qi})" id="wrong-feedback-btn-${qi}" style="display: none;">
                            <i class="fas fa-comment-alt"></i> ${isEnglish ? 'Show Wrong Answers Explanation' : 'عرض تفسير الإجابات الخاطئة'}
                        </button>
                        
                        <!-- منطقة التغذية الراجعة للخيارات الخاطئة -->
                        <div class="wrong-feedback-area" id="wrong-feedback-${qi}">
                            <div class="wrong-feedback-title">
                                <i class="fas fa-times-circle"></i> ${isEnglish ? 'Wrong Answers Explanation' : 'تفسير الإجابات الخاطئة'}
                            </div>
                            ${hasExplanations ? q.explanations.map((exp, expIdx) => {
                                if (expIdx === q.answer) return ''; // تخطي الإجابة الصحيحة
                                return `
                                    <div class="wrong-feedback-item">
                                        <div class="wrong-feedback-header">
                                            <i class="fas fa-times-circle"></i>
                                            ${isEnglish ? 'Wrong option: ' : 'خيار خاطئ: '} ${letters[expIdx]}
                                        </div>
                                        <div class="wrong-feedback-content">${exp}</div>
                                    </div>
                                `;
                            }).join('') : `<div class="wrong-feedback-item">${isEnglish ? 'No explanations for wrong options' : 'لا توجد تفسيرات للخيارات الخاطئة'}</div>`}
                        </div>
                    </div>
                `;
            }).join('');
            
            out.innerHTML = questionsHTML;
            bindQuizEvents(data);
        }
        
        // دالة ربط أحداث الأسئلة
        function bindQuizEvents(data) {
            document.querySelectorAll('.option').forEach(option => {
                option.addEventListener('click', function() {
                    const questionIndex = parseInt(this.dataset.q);
                    const optionIndex = parseInt(this.dataset.o);
                    const questionData = data.questions[questionIndex];
                    const correctIndex = questionData.answer;
                    
                    // تعطيل جميع الخيارات في هذا السؤال
                    const allOptions = document.querySelectorAll(`.question[data-q="${questionIndex}"] .option`);
                    allOptions.forEach(opt => opt.classList.add('disabled'));
                    
                    // تحديد الخيار الصحيح والخاطئ
                    allOptions.forEach((opt, idx) => {
                        if (idx === correctIndex) {
                            opt.classList.add('correct');
                            
                            // تشغيل صوت الإجابة الصحيحة
                            if (idx === optionIndex) {
                                playSound('correct');
                            }
                        } else if (idx === optionIndex) {
                            opt.classList.add('wrong');
                            
                            // تشغيل صوت الإجابة الخاطئة
                            playSound('wrong');
                        }
                    });
                    
                    // إظهار التغذية الراجعة الفورية للإجابة الصحيحة
                    const instantFeedback = document.getElementById(`instant-feedback-${questionIndex}`);
                    instantFeedback.classList.add('show');
                    
                    // إظهار زر التغذية الراجعة للخيارات الخاطئة
                    const wrongFeedbackBtn = document.getElementById(`wrong-feedback-btn-${questionIndex}`);
                    wrongFeedbackBtn.style.display = 'flex';
                    
                    // إذا كانت الإجابة خاطئة، إظهار منطقة التغذية الراجعة للخيارات الخاطئة تلقائياً
                    if (optionIndex !== correctIndex) {
                        setTimeout(() => {
                            const wrongFeedbackArea = document.getElementById(`wrong-feedback-${questionIndex}`);
                            wrongFeedbackArea.classList.add('show');
                            const isEnglish = language.value === 'en';
                            wrongFeedbackBtn.innerHTML = `<i class="fas fa-chevron-up"></i> ${isEnglish ? 'Hide Wrong Answers Explanation' : 'إخفاء تفسير الإجابات الخاطئة'}`;
                        }, 500);
                    }
                });
            });
        }
        
        // دالة تبديل عرض التغذية الراجعة للخيارات الخاطئة
        function toggleWrongFeedback(questionIndex) {
            const wrongFeedbackArea = document.getElementById(`wrong-feedback-${questionIndex}`);
            const wrongFeedbackBtn = document.getElementById(`wrong-feedback-btn-${questionIndex}`);
            const isEnglish = language.value === 'en';
            
            wrongFeedbackArea.classList.toggle('show');
            
            // تحديث نص الزر
            if (wrongFeedbackArea.classList.contains('show')) {
                wrongFeedbackBtn.innerHTML = `<i class="fas fa-chevron-up"></i> ${isEnglish ? 'Hide Wrong Answers Explanation' : 'إخفاء تفسير الإجابات الخاطئة'}`;
            } else {
                wrongFeedbackBtn.innerHTML = `<i class="fas fa-comment-alt"></i> ${isEnglish ? 'Show Wrong Answers Explanation' : 'عرض تفسير الإجابات الخاطئة'}`;
            }
        }
        
        // دالة عرض البطاقات التعليمية
        function renderCards(data) {
            if (!data || !data.cards || !Array.isArray(data.cards)) {
                const isEnglish = language.value === 'en';
                showMessage(isEnglish ? 
                    "No cards found in received data" : 
                    "لم يتم العثور على بطاقات في البيانات المستلمة", 
                'error');
                return;
            }
            
            const isEnglish = language.value === 'en';
            
            window.cards = data.cards;
            window.cardIndex = 0;
            
            out.innerHTML = `
                <div class="flashcard" onclick="flipCard()">
                    <div class="flashcard-front">${data.cards[0].front}</div>
                    <div class="flashcard-back hidden">${data.cards[0].back}</div>
                    <div class="flashcard-counter">${cardIndex + 1} / ${data.cards.length}</div>
                </div>
                
                <div class="flashcard-nav">
                    <button class="flashcard-btn" onclick="prevCard()">
                        <i class="fas fa-arrow-right"></i> ${isEnglish ? 'Previous' : 'السابق'}
                    </button>
                    <button class="flashcard-btn" onclick="flipCard()">
                        <i class="fas fa-sync-alt"></i> ${isEnglish ? 'Flip Card' : 'قلب البطاقة'}
                    </button>
                    <button class="flashcard-btn" onclick="nextCard()">
                        <i class="fas fa-arrow-left"></i> ${isEnglish ? 'Next' : 'التالي'}
                    </button>
                </div>
            `;
        }
        
        // دالة قلب البطاقة
        function flipCard() {
            const card = document.querySelector('.flashcard');
            const front = card.querySelector('.flashcard-front');
            const back = card.querySelector('.flashcard-back');
            
            front.classList.toggle('hidden');
            back.classList.toggle('hidden');
            
            // إضافة تأثير التحريك
            card.style.transform = 'scale(0.95)';
            setTimeout(() => {
                card.style.transform = 'scale(1)';
            }, 150);
        }
        
        // دالة البطاقة التالية
        function nextCard() {
            cardIndex = (cardIndex + 1) % cards.length;
            updateCard();
        }
        
        // دالة البطاقة السابقة
        function prevCard() {
            cardIndex = (cardIndex - 1 + cards.length) % cards.length;
            updateCard();
        }
        
        // دالة تحديث البطاقة
        function updateCard() {
            const card = document.querySelector('.flashcard');
            const front = card.querySelector('.flashcard-front');
            const back = card.querySelector('.flashcard-back');
            const counter = card.querySelector('.flashcard-counter');
            
            front.textContent = cards[cardIndex].front;
            back.textContent = cards[cardIndex].back;
            counter.textContent = `${cardIndex + 1} / ${cards.length}`;
            
            // التأكد من إظهار الوجه الأمامي
            back.classList.add('hidden');
            front.classList.remove('hidden');
            
            // إضافة تأثير التحريك
            card.style.transform = 'scale(0.95)';
            setTimeout(() => {
                card.style.transform = 'scale(1)';
            }, 150);
        }
        
        // دالة عرض التلخيص
        function renderSummary(text) {
            // تحويل النص إلى نقاط منسقة
            const paragraphs = text.split('\n').filter(p => p.trim().length > 0);
            let summaryHTML = '<div class="summary">';
            
            const isEnglish = language.value === 'en';
            summaryHTML += `<div class="summary-title"><i class="fas fa-scroll"></i> ${isEnglish ? 'Summary' : 'التلخيص'}</div>`;
            
            paragraphs.forEach((paragraph, idx) => {
                const pointClass = `point-${(idx % 7) + 1}`;
                const iconClass = getIconForSummaryPoint(idx);
                
                summaryHTML += `
                    <div class="summary-point ${pointClass}">
                        <i class="${iconClass}"></i>
                        <div class="summary-point-text">${paragraph}</div>
                    </div>
                `;
            });
            
            summaryHTML += '</div>';
            out.innerHTML = summaryHTML;
        }
        
        // دالة للحصول على الأيقونة المناسبة لنقطة التلخيص
        function getIconForSummaryPoint(index) {
            const icons = [
                'fas fa-lightbulb',
                'fas fa-chart-line',
                'fas fa-check-circle',
                'fas fa-exclamation-circle',
                'fas fa-question-circle',
                'fas fa-star',
                'fas fa-flag'
            ];
            return icons[index % icons.length];
        }
        
        // دالة لعرض رسالة
        function showMessage(text, type = 'info') {
            out.innerHTML = `
                <div class="message ${type}">
                    <i class="fas fa-${type === 'error' ? 'exclamation-triangle' : 'info-circle'}"></i>
                    ${text}
                </div>
            `;
        }
        
        // دالة لعرض مؤشر التحميل
        function showLoading() {
            const isEnglish = language.value === 'en';
            out.innerHTML = `
                <div class="loading">
                    <div class="spinner"></div>
                    <div class="loading-text">${isEnglish ? 'Processing...' : 'جارٍ المعالجة...'}</div>
                </div>
            `;
        }
        
        // دالة لاستخراج JSON من النص
        function extractJSON(text) {
            try {
                // محاولة تحليل النص مباشرة كـ JSON
                return JSON.stringify(JSON.parse(text));
            } catch (e) {
                // البحث عن JSON في النص
                const match = text.match(/\{[\s\S]*\}/);
                return match ? match[0] : '{"questions":[]}';
            }
        }
        
        // دالة لتشغيل الصوت
        function playSound(type) {
            try {
                if (type === 'correct') {
                    correctSound.currentTime = 0;
                    correctSound.play().catch(e => {
                        console.log('تعذر تشغيل الصوت:', e);
                    });
                } else if (type === 'wrong') {
                    wrongSound.currentTime = 0;
                    wrongSound.play().catch(e => {
                        console.log('تعذر تشغيل الصوت:', e);
                    });
                }
            } catch (e) {
                console.log('تعذر تشغيل الصوت:', e);
            }
        }
        
        // تهيئة أولية
        document.addEventListener('DOMContentLoaded', function() {
            // تحسينات خاصة للجوال
            if (isMobile) {
                // إضافة حدث للنقر على منطقة التحميل
                document.querySelector('.file-upload-area').addEventListener('click', function(e) {
                    if (e.target.closest('.upload-option-btn')) {
                        return;
                    }
                    
                    if (currentUploadType === 'image') {
                        imageInput.click();
                    } else {
                        fileInput.click();
                    }
                });
                
                // تحسينات للشاشات الصغيرة
                if (window.innerWidth < 768) {
                    // ضبط حجم الخط للحقول على iOS
                    if (isIOS) {
                        document.querySelectorAll('input, textarea, select').forEach(el => {
                            el.style.fontSize = '16px';
                        });
                    }
                }
            }
            
            // تحديث التعليمات الافتراضية
            const fileMessage = document.getElementById('file-message');
            if (fileMessage) {
                fileMessage.innerHTML = '<i class="fas fa-file"></i> يمكنك رفع ملفات نصية أو PDF أو Word أو صور';
                fileMessage.classList.add('success');
                fileMessage.style.display = 'block';
            }
            
            // إصلاح مشكلة الـ 100vh على iOS
            function setVh() {
                let vh = window.innerHeight * 0.01;
                document.documentElement.style.setProperty('--vh', `${vh}px`);
            }
            
            setVh();
            window.addEventListener('resize', setVh);
            window.addEventListener('orientationchange', setVh);
            
            // توقف عن تشغيل الكاميرا عند إغلاق الصفحة
            window.addEventListener('beforeunload', function() {
                if (stream) {
                    stream.getTracks().forEach(track => {
                        track.stop();
                    });
                }
            });
        });
    </script>
</body>
</html>