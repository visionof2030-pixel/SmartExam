<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <!-- إعدادات Meta محسنة للتوافق مع جميع الأجهزة -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=5.0, user-scalable=yes">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <meta name="theme-color" content="#0c2d41">
    <meta name="mobile-web-app-capable" content="yes">
    <meta name="format-detection" content="telephone=no">
    <title>نُبـل - أداة التعلم الذكية</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@300;400;500;700;800;900&display=swap" rel="stylesheet">
    
    <style>
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
            --border-radius: 20px;
            --border-radius-sm: 12px;
            --transition: all 0.3s ease;
            --gold: #ffd166;
            --gold-light: #ffe8a3;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent; /* إزالة اللون الأزرق عند النقر على iOS */
            -webkit-touch-callout: none; /* منع القائمة السياقية على iOS */
        }
        
        html {
            -webkit-text-size-adjust: 100%; /* منع تغيير حجم النص على iOS */
            -webkit-font-smoothing: antialiased;
        }
        
        body {
            font-family: 'Tajawal', sans-serif;
            background: linear-gradient(135deg, var(--primary-dark) 0%, var(--primary) 50%, var(--primary-light) 100%);
            color: var(--light);
            min-height: 100vh;
            padding: 0;
            line-height: 1.6;
            overflow-x: hidden;
            /* تحسينات لأجهزة iOS */
            -webkit-overflow-scrolling: touch; /* تمرير سلس على iOS */
            overscroll-behavior-y: none; /* منع تأثير الارتداد الزائد */
        }
        
        /* تحسينات للأجهزة المحمولة */
        @supports (-webkit-touch-callout: none) {
            body {
                min-height: -webkit-fill-available;
            }
        }
        
        /* تغيير اتجاه النص للغة الإنجليزية */
        body.english-mode {
            direction: ltr;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
        }
        
        body.english-mode .header p,
        body.english-mode .question-text,
        body.english-mode .option-text,
        body.english-mode .flashcard-front,
        body.english-mode .flashcard-back,
        body.english-mode .summary-point-text,
        body.english-mode .instant-feedback-content,
        body.english-mode .wrong-feedback-content {
            text-align: left;
        }
        
        body.english-mode .summary-section-title {
            border-right: none;
            border-left: 5px solid var(--accent);
            padding-right: 0;
            padding-left: 20px;
        }
        
        body.english-mode .summary-point {
            border-right: none;
            border-left: 5px solid;
        }
        
        body.english-mode .instant-feedback,
        body.english-mode .wrong-feedback-area {
            border-right: none;
            border-left: 5px solid;
        }
        
        body.english-mode .wrong-feedback-item {
            border-right: none;
            border-left: 4px solid var(--danger);
        }
        
        body.english-mode .question-number,
        body.english-mode .summary-point,
        body.english-mode .option {
            text-align: left;
        }
        
        body.english-mode .summary-points {
            padding-right: 0;
            padding-left: 25px;
        }
        
        body.english-mode .option::before {
            right: auto;
            left: 0;
        }
        
        /* تحسينات للأزرار على iOS */
        button, select, textarea, input {
            font-size: 16px !important; /* منع التكبير على iOS */
            -webkit-appearance: none; /* إزالة المظهر الافتراضي على iOS */
            border-radius: 0; /* إعادة تعيين الحدود */
        }
        
        /* البار العلوي */
        .top-bar {
            background: rgba(12, 45, 65, 0.95);
            backdrop-filter: blur(15px);
            padding: 14px 20px;
            text-align: center;
            border-bottom: 1px solid rgba(255, 255, 255, 0.12);
            font-size: 0.95rem;
            color: var(--accent-light);
            box-shadow: var(--shadow-light);
            font-weight: 500;
            letter-spacing: 0.3px;
            /* تحسينات للموبايل */
            padding-top: max(14px, env(safe-area-inset-top));
            padding-bottom: max(14px, env(safe-area-inset-bottom));
        }
        
        /* الهيدر الرئيسي */
        .header {
            padding: 35px 20px 25px;
            text-align: center;
            background: linear-gradient(135deg, rgba(12, 45, 65, 0.9) 0%, rgba(26, 72, 101, 0.9) 100%);
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            position: relative;
            overflow: hidden;
            /* تحسينات للموبايل */
            padding-top: max(35px, calc(env(safe-area-inset-top) + 20px));
        }
        
        .header::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 100%;
            background: radial-gradient(circle at 30% 50%, rgba(74, 144, 226, 0.15) 0%, transparent 70%);
            pointer-events: none;
        }
        
        .logo-container {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 20px;
            margin-bottom: 15px;
        }
        
        .logo-icon {
            width: 70px;
            height: 70px;
            background: linear-gradient(135deg, var(--accent) 0%, var(--accent-light) 100%);
            border-radius: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2.5rem;
            color: white;
            box-shadow: 0 10px 25px rgba(42, 157, 143, 0.4);
            transform: rotate(-5deg);
            border: 3px solid rgba(255, 255, 255, 0.2);
        }
        
        .logo-text {
            font-size: 3.2rem;
            font-weight: 900;
            margin-bottom: 0;
            color: #4ecdc4;
            text-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
            letter-spacing: -1px;
            position: relative;
        }
        
        /* إضافة ضمة على حرف اللام */
        .logo-text::after {
            content: "ُ";
            position: absolute;
            font-size: 2rem;
            color: #ffd166;
            right: -5px;
            top: -15px;
            text-shadow: 0 2px 5px rgba(0, 0, 0, 0.3);
        }
        
        body.english-mode .logo-text::after {
            right: auto;
            left: -5px;
        }
        
        .header p {
            font-size: 1.25rem;
            color: var(--gray-light);
            max-width: 800px;
            margin: 0 auto;
            opacity: 0.95;
            font-weight: 300;
            line-height: 1.8;
        }
        
        .header p span {
            font-weight: 600;
        }
        
        /* الحاوية الرئيسية */
        .container {
            max-width: 1000px;
            margin: 0 auto;
            padding: 30px 20px 50px;
            /* تحسينات للموبايل */
            padding-bottom: max(50px, env(safe-area-inset-bottom));
        }
        
        /* بطاقة التحكم */
        .control-card {
            background: rgba(255, 255, 255, 0.07);
            backdrop-filter: blur(15px);
            border-radius: var(--border-radius);
            padding: 30px;
            margin-bottom: 35px;
            border: 1px solid rgba(255, 255, 255, 0.12);
            box-shadow: var(--shadow);
            position: relative;
            overflow: hidden;
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
        
        body.english-mode .control-card::before {
            right: auto;
            left: 0;
            background: linear-gradient(to right, var(--accent), var(--accent-light));
        }
        
        /* أزرار التبويب */
        .mode-tabs {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            margin-bottom: 30px;
        }
        
        .mode-tab {
            flex: 1;
            min-width: 170px;
            background: rgba(255, 255, 255, 0.05);
            border: 2px solid rgba(255, 255, 255, 0.1);
            border-radius: var(--border-radius-sm);
            padding: 22px 15px;
            text-align: center;
            cursor: pointer;
            transition: var(--transition);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
            /* تحسينات للموبايل */
            touch-action: manipulation; /* تحسين الاستجابة للمس */
        }
        
        .mode-tab::after {
            content: '';
            position: absolute;
            bottom: 0;
            right: 0;
            width: 100%;
            height: 3px;
            background: linear-gradient(to left, var(--accent), transparent);
            transform: translateX(100%);
            transition: var(--transition);
        }
        
        body.english-mode .mode-tab::after {
            right: auto;
            left: 0;
            background: linear-gradient(to right, var(--accent), transparent);
            transform: translateX(-100%);
        }
        
        .mode-tab:hover {
            background: rgba(255, 255, 255, 0.1);
            transform: translateY(-5px);
            border-color: rgba(255, 255, 255, 0.2);
        }
        
        .mode-tab:hover::after {
            transform: translateX(0);
        }
        
        body.english-mode .mode-tab:hover::after {
            transform: translateX(0);
        }
        
        .mode-tab.active {
            background: rgba(42, 157, 143, 0.2);
            border-color: var(--accent);
            box-shadow: 0 8px 25px rgba(42, 157, 143, 0.25);
        }
        
        .mode-tab.active::after {
            transform: translateX(0);
            background: linear-gradient(to left, var(--accent), var(--accent-light));
        }
        
        body.english-mode .mode-tab.active::after {
            background: linear-gradient(to right, var(--accent), var(--accent-light));
        }
        
        .mode-tab i {
            font-size: 2.3rem;
            margin-bottom: 15px;
            color: var(--accent-light);
            transition: var(--transition);
        }
        
        .mode-tab.active i {
            color: var(--accent);
            transform: scale(1.1);
        }
        
        .mode-tab span {
            font-weight: 700;
            font-size: 1.15rem;
            color: var(--light);
        }
        
        /* إعدادات التحكم */
        .control-group {
            margin-bottom: 30px;
        }
        
        .control-group label {
            display: block;
            margin-bottom: 12px;
            font-weight: 700;
            color: var(--accent-light);
            font-size: 1.15rem;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        select, textarea, input[type="file"] {
            width: 100%;
            padding: 18px 22px;
            background: rgba(255, 255, 255, 0.06);
            border: 2px solid rgba(255, 255, 255, 0.12);
            border-radius: var(--border-radius-sm);
            color: var(--light);
            font-family: 'Tajawal', sans-serif;
            font-size: 1.05rem;
            transition: var(--transition);
            /* تحسينات للموبايل */
            -webkit-appearance: none;
            appearance: none;
        }
        
        body.english-mode select,
        body.english-mode textarea,
        body.english-mode input[type="file"] {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
        }
        
        select:focus, textarea:focus, input[type="file"]:focus {
            outline: none;
            border-color: var(--accent);
            box-shadow: 0 0 0 4px rgba(42, 157, 143, 0.25);
            background: rgba(255, 255, 255, 0.1);
        }
        
        select option {
            background: var(--primary-dark);
            color: var(--light);
            padding: 12px;
        }
        
        textarea {
            min-height: 150px;
            resize: vertical;
            line-height: 1.7;
            /* تحسينات للموبايل */
            touch-action: manipulation;
        }
        
        /* زر التنفيذ */
        .execute-btn {
            width: 100%;
            padding: 22px;
            background: linear-gradient(135deg, var(--accent) 0%, var(--accent-dark) 100%);
            color: white;
            border: none;
            border-radius: var(--border-radius-sm);
            font-family: 'Tajawal', sans-serif;
            font-size: 1.3rem;
            font-weight: 800;
            cursor: pointer;
            transition: var(--transition);
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 15px;
            box-shadow: 0 8px 25px rgba(42, 157, 143, 0.4);
            position: relative;
            overflow: hidden;
            letter-spacing: 0.5px;
            /* تحسينات للموبايل */
            touch-action: manipulation;
            -webkit-appearance: none;
        }
        
        body.english-mode .execute-btn {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
        }
        
        .execute-btn::before {
            content: '';
            position: absolute;
            top: 0;
            right: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
            transform: translateX(-100%);
            transition: transform 0.6s;
        }
        
        .execute-btn:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 35px rgba(42, 157, 143, 0.5);
        }
        
        .execute-btn:hover::before {
            transform: translateX(100%);
        }
        
        .execute-btn:active {
            transform: translateY(-2px);
        }
        
        /* منطقة الإخراج */
        #out {
            margin-top: 35px;
        }
        
        /* تصميم الأسئلة */
        .question {
            background: rgba(255, 255, 255, 0.07);
            backdrop-filter: blur(15px);
            border-radius: var(--border-radius);
            padding: 30px;
            margin-bottom: 30px;
            border: 1px solid rgba(255, 255, 255, 0.12);
            box-shadow: var(--shadow);
            transition: var(--transition);
            position: relative;
        }
        
        .question::before {
            content: '';
            position: absolute;
            top: 0;
            right: 0;
            width: 100%;
            height: 4px;
            background: linear-gradient(to left, var(--primary-light), transparent);
            border-radius: var(--border-radius) var(--border-radius) 0 0;
        }
        
        body.english-mode .question::before {
            right: auto;
            left: 0;
            background: linear-gradient(to right, var(--primary-light), transparent);
        }
        
        .question-header {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            margin-bottom: 25px;
        }
        
        body.english-mode .question-header {
            flex-direction: row-reverse;
        }
        
        .question-text {
            font-size: 1.4rem;
            font-weight: 800;
            color: var(--light);
            line-height: 1.6;
            flex: 1;
        }
        
        .question-number {
            background: linear-gradient(135deg, var(--accent) 0%, var(--accent-light) 100%);
            color: white;
            width: 50px;
            height: 50px;
            border-radius: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 900;
            flex-shrink: 0;
            margin-left: 20px;
            font-size: 1.4rem;
            box-shadow: 0 5px 15px rgba(42, 157, 143, 0.4);
            border: 2px solid rgba(255, 255, 255, 0.2);
        }
        
        body.english-mode .question-number {
            margin-left: 0;
            margin-right: 20px;
        }
        
        /* خيارات الأسئلة */
        .options {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
            gap: 18px;
            margin-bottom: 25px;
        }
        
        @media (max-width: 768px) {
            .options {
                grid-template-columns: 1fr;
            }
        }
        
        .option {
            background: rgba(255, 255, 255, 0.05);
            border: 2px solid rgba(255, 255, 255, 0.12);
            border-radius: var(--border-radius-sm);
            padding: 22px;
            cursor: pointer;
            transition: var(--transition);
            display: flex;
            align-items: center;
            gap: 18px;
            position: relative;
            overflow: hidden;
            /* تحسينات للموبايل */
            touch-action: manipulation;
        }
        
        .option::before {
            content: '';
            position: absolute;
            top: 0;
            right: 0;
            width: 5px;
            height: 100%;
            background: rgba(255, 255, 255, 0.1);
            transition: var(--transition);
        }
        
        body.english-mode .option::before {
            right: auto;
            left: 0;
        }
        
        .option:hover {
            background: rgba(255, 255, 255, 0.09);
            transform: translateY(-5px);
            border-color: rgba(255, 255, 255, 0.2);
        }
        
        .option:hover::before {
            background: var(--accent-light);
        }
        
        .option.disabled {
            pointer-events: none;
            opacity: 0.9;
        }
        
        .option.correct {
            background: var(--success-bg);
            border-color: var(--accent);
            box-shadow: 0 6px 20px rgba(42, 157, 143, 0.25);
        }
        
        .option.correct::before {
            background: var(--accent);
        }
        
        .option.wrong {
            background: var(--error-bg);
            border-color: var(--danger);
            box-shadow: 0 6px 20px rgba(231, 111, 81, 0.25);
        }
        
        .option.wrong::before {
            background: var(--danger);
        }
        
        .option-letter {
            background: rgba(255, 255, 255, 0.1);
            color: var(--light);
            width: 42px;
            height: 42px;
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 800;
            flex-shrink: 0;
            font-size: 1.2rem;
            transition: var(--transition);
        }
        
        .option.correct .option-letter {
            background: var(--accent);
            color: white;
            box-shadow: 0 4px 12px rgba(42, 157, 143, 0.4);
        }
        
        .option.wrong .option-letter {
            background: var(--danger);
            color: white;
            box-shadow: 0 4px 12px rgba(231, 111, 81, 0.4);
        }
        
        .option-text {
            font-size: 1.15rem;
            font-weight: 600;
            flex: 1;
        }
        
        /* التغذية الراجعة الفورية للإجابة الصحيحة */
        .instant-feedback {
            margin-top: 25px;
            padding: 25px;
            background: rgba(42, 157, 143, 0.1);
            border-radius: var(--border-radius-sm);
            border-right: 5px solid var(--accent);
            display: none;
            animation: fadeIn 0.5s ease;
        }
        
        .instant-feedback.show {
            display: block;
        }
        
        .instant-feedback-header {
            display: flex;
            align-items: center;
            gap: 12px;
            margin-bottom: 15px;
            color: var(--accent);
        }
        
        .instant-feedback-header i {
            font-size: 1.5rem;
        }
        
        .instant-feedback-header h3 {
            font-size: 1.3rem;
            font-weight: 800;
            margin: 0;
        }
        
        .instant-feedback-content {
            font-size: 1.1rem;
            line-height: 1.7;
            color: var(--light);
            padding-right: 10px;
        }
        
        body.english-mode .instant-feedback-content {
            padding-right: 0;
            padding-left: 10px;
        }
        
        /* زر التغذية الراجعة للخيارات الخاطئة */
        .wrong-feedback-btn {
            background: rgba(231, 111, 81, 0.1);
            border: 2px solid rgba(231, 111, 81, 0.3);
            border-radius: var(--border-radius-sm);
            color: var(--danger-light);
            padding: 18px 28px;
            font-family: 'Tajawal', sans-serif;
            font-size: 1.15rem;
            font-weight: 700;
            cursor: pointer;
            transition: var(--transition);
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 12px;
            width: 100%;
            margin-top: 20px;
            /* تحسينات للموبايل */
            touch-action: manipulation;
            -webkit-appearance: none;
        }
        
        body.english-mode .wrong-feedback-btn {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
        }
        
        .wrong-feedback-btn:hover {
            background: rgba(231, 111, 81, 0.2);
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(231, 111, 81, 0.2);
        }
        
        /* منطقة التغذية الراجعة للخيارات الخاطئة */
        .wrong-feedback-area {
            margin-top: 25px;
            padding: 25px;
            background: rgba(12, 45, 65, 0.8);
            border-radius: var(--border-radius-sm);
            border-right: 5px solid var(--danger);
            display: none;
        }
        
        .wrong-feedback-area.show {
            display: block;
            animation: fadeIn 0.5s ease;
        }
        
        .wrong-feedback-title {
            font-size: 1.3rem;
            font-weight: 800;
            margin-bottom: 20px;
            color: var(--danger-light);
            display: flex;
            align-items: center;
            gap: 12px;
        }
        
        .wrong-feedback-item {
            margin-bottom: 20px;
            padding: 20px;
            background: rgba(231, 111, 81, 0.08);
            border-radius: var(--border-radius-sm);
            border-right: 4px solid var(--danger);
        }
        
        .wrong-feedback-header {
            font-weight: 700;
            margin-bottom: 10px;
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 1.1rem;
            color: var(--danger-light);
        }
        
        .wrong-feedback-content {
            font-size: 1.05rem;
            line-height: 1.7;
            color: #f0f0f0;
        }
        
        /* تصميم البطاقات التعليمية */
        .flashcard {
            background: rgba(255, 255, 255, 0.07);
            backdrop-filter: blur(15px);
            border-radius: var(--border-radius);
            padding: 50px 40px;
            margin-bottom: 35px;
            border: 1px solid rgba(255, 255, 255, 0.12);
            box-shadow: var(--shadow);
            min-height: 400px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            transition: var(--transition);
            text-align: center;
            position: relative;
            /* تحسينات للموبايل */
            touch-action: manipulation;
        }
        
        .flashcard::before {
            content: '';
            position: absolute;
            top: 0;
            right: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle at 20% 80%, rgba(74, 144, 226, 0.1) 0%, transparent 70%);
            pointer-events: none;
            border-radius: var(--border-radius);
        }
        
        .flashcard:hover {
            transform: translateY(-8px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.25);
        }
        
        .flashcard-front, .flashcard-back {
            font-size: 2rem;
            font-weight: 800;
            color: var(--light);
            line-height: 1.7;
            max-width: 800px;
        }
        
        .flashcard-back {
            color: var(--accent-light);
        }
        
        .flashcard-counter {
            margin-top: 30px;
            font-size: 1.2rem;
            color: var(--gray-light);
            font-weight: 600;
            background: rgba(255, 255, 255, 0.05);
            padding: 10px 25px;
            border-radius: 30px;
        }
        
        .flashcard-nav {
            display: flex;
            justify-content: center;
            gap: 25px;
            margin-top: 30px;
        }
        
        .flashcard-btn {
            background: rgba(255, 255, 255, 0.07);
            border: 2px solid rgba(255, 255, 255, 0.12);
            border-radius: var(--border-radius-sm);
            color: var(--light);
            padding: 18px 35px;
            font-family: 'Tajawal', sans-serif;
            font-size: 1.15rem;
            font-weight: 700;
            cursor: pointer;
            transition: var(--transition);
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 12px;
            /* تحسينات للموبايل */
            touch-action: manipulation;
            -webkit-appearance: none;
        }
        
        body.english-mode .flashcard-btn {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
        }
        
        .flashcard-btn:hover {
            background: rgba(255, 255, 255, 0.12);
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.15);
        }
        
        /* تصميم التلخيص */
        .summary {
            background: rgba(255, 255, 255, 0.07);
            backdrop-filter: blur(15px);
            border-radius: var(--border-radius);
            padding: 40px;
            margin-bottom: 35px;
            border: 1px solid rgba(255, 255, 255, 0.12);
            box-shadow: var(--shadow);
            position: relative;
        }
        
        .summary::before {
            content: '';
            position: absolute;
            top: 0;
            right: 0;
            width: 100%;
            height: 4px;
            background: linear-gradient(to left, var(--gold), var(--accent-light));
            border-radius: var(--border-radius) var(--border-radius) 0 0;
        }
        
        body.english-mode .summary::before {
            right: auto;
            left: 0;
            background: linear-gradient(to right, var(--gold), var(--accent-light));
        }
        
        .summary-title {
            font-size: 2rem;
            font-weight: 900;
            margin-bottom: 35px;
            color: var(--gold);
            text-align: center;
            border-bottom: 2px solid rgba(255, 255, 255, 0.1);
            padding-bottom: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 15px;
        }
        
        .summary-section {
            margin-bottom: 40px;
        }
        
        .summary-section-title {
            font-size: 1.6rem;
            font-weight: 800;
            margin-bottom: 25px;
            color: var(--light);
            display: flex;
            align-items: center;
            gap: 15px;
            padding-right: 20px;
            border-right: 5px solid var(--accent);
        }
        
        .summary-points {
            list-style-type: none;
            padding-right: 25px;
        }
        
        .summary-point {
            margin-bottom: 22px;
            padding: 22px;
            background: rgba(255, 255, 255, 0.04);
            border-radius: var(--border-radius-sm);
            border-right: 5px solid;
            transition: var(--transition);
            position: relative;
            overflow: hidden;
        }
        
        .summary-point::before {
            content: '';
            position: absolute;
            top: 0;
            right: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.03), transparent);
            transform: translateX(-100%);
            transition: transform 0.6s;
        }
        
        body.english-mode .summary-point::before {
            transform: translateX(100%);
        }
        
        .summary-point:hover {
            background: rgba(255, 255, 255, 0.07);
            transform: translateX(-10px);
        }
        
        body.english-mode .summary-point:hover {
            transform: translateX(10px);
        }
        
        .summary-point:hover::before {
            transform: translateX(100%);
        }
        
        body.english-mode .summary-point:hover::before {
            transform: translateX(-100%);
        }
        
        .point-1 { border-color: #2a9d8f; }
        .point-2 { border-color: #4ecdc4; }
        .point-3 { border-color: #ffd166; }
        .point-4 { border-color: #f4a261; }
        .point-5 { border-color: #e76f51; }
        .point-6 { border-color: #6a8eae; }
        .point-7 { border-color: #9d4edd; }
        
        .summary-point i {
            margin-left: 12px;
            color: inherit;
            font-size: 1.2rem;
        }
        
        body.english-mode .summary-point i {
            margin-left: 0;
            margin-right: 12px;
        }
        
        .summary-point-text {
            font-size: 1.15rem;
            line-height: 1.7;
            font-weight: 500;
        }
        
        /* تخصيص خيارات تحميل الملف */
        .file-upload-area {
            width: 100%;
            padding: 18px 22px;
            background: rgba(255, 255, 255, 0.06);
            border: 2px solid rgba(255, 255, 255, 0.12);
            border-radius: var(--border-radius-sm);
            color: var(--light);
            transition: var(--transition);
            text-align: center;
            cursor: pointer;
            margin-bottom: 15px;
            /* تحسينات للموبايل */
            touch-action: manipulation;
        }
        
        .file-upload-area:hover {
            background: rgba(255, 255, 255, 0.1);
            border-color: var(--accent-light);
        }
        
        .file-upload-area input[type="file"] {
            display: none;
        }
        
        .file-upload-label {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 15px;
            cursor: pointer;
        }
        
        .file-upload-label i {
            font-size: 3rem;
            color: var(--accent-light);
        }
        
        .upload-options {
            display: flex;
            gap: 15px;
            margin-top: 10px;
            flex-wrap: wrap;
            justify-content: center;
        }
        
        .upload-option-btn {
            background: rgba(42, 157, 143, 0.2);
            border: 1px solid rgba(42, 157, 143, 0.4);
            border-radius: var(--border-radius-sm);
            padding: 12px 20px;
            color: var(--accent-light);
            cursor: pointer;
            transition: var(--transition);
            display: flex;
            align-items: center;
            gap: 8px;
            font-weight: 600;
            /* تحسينات للموبايل */
            touch-action: manipulation;
        }
        
        .upload-option-btn:hover {
            background: rgba(42, 157, 143, 0.3);
            transform: translateY(-3px);
        }
        
        .upload-option-btn.active {
            background: rgba(42, 157, 143, 0.4);
            border-color: var(--accent);
            box-shadow: 0 5px 15px rgba(42, 157, 143, 0.2);
        }
        
        .image-preview {
            margin-top: 20px;
            max-width: 100%;
            border-radius: var(--border-radius-sm);
            display: none;
        }
        
        .image-preview img {
            max-width: 100%;
            max-height: 300px;
            border-radius: var(--border-radius-sm);
            object-fit: contain;
        }
        
        .camera-container {
            width: 100%;
            height: 300px;
            background: rgba(0, 0, 0, 0.2);
            border-radius: var(--border-radius-sm);
            display: flex;
            justify-content: center;
            align-items: center;
            position: relative;
            overflow: hidden;
            margin-top: 20px;
            display: none;
        }
        
        #camera-feed {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transform: scaleX(-1); /* عكس الصورة للكاميرا الأمامية */
        }
        
        .camera-controls {
            position: absolute;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            gap: 15px;
            z-index: 10;
        }
        
        .camera-btn {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background: rgba(231, 111, 81, 0.8);
            border: 3px solid white;
            color: white;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            transition: var(--transition);
            font-size: 1.5rem;
            /* تحسينات للموبايل */
            touch-action: manipulation;
        }
        
        .camera-btn:hover {
            background: rgba(231, 111, 81, 1);
            transform: scale(1.1);
        }
        
        .camera-btn.capture {
            background: rgba(42, 157, 143, 0.8);
        }
        
        .camera-btn.capture:hover {
            background: rgba(42, 157, 143, 1);
        }
        
        /* التحميل */
        .loading {
            text-align: center;
            padding: 60px;
        }
        
        .spinner {
            width: 70px;
            height: 70px;
            border: 6px solid rgba(255, 255, 255, 0.1);
            border-top: 6px solid var(--accent);
            border-radius: 50%;
            animation: spin 1s linear infinite;
            margin: 0 auto 30px;
        }
        
        .loading-text {
            font-size: 1.4rem;
            font-weight: 700;
            color: var(--accent-light);
        }
        
        /* الرسائل */
        .message {
            padding: 30px;
            border-radius: var(--border-radius-sm);
            margin-bottom: 30px;
            text-align: center;
            font-weight: 700;
            font-size: 1.3rem;
            border-right: 5px solid;
            backdrop-filter: blur(10px);
        }
        
        body.english-mode .message {
            border-right: none;
            border-left: 5px solid;
        }
        
        .message.success {
            background: rgba(42, 157, 143, 0.15);
            color: var(--accent-light);
            border-right-color: var(--accent);
        }
        
        body.english-mode .message.success {
            border-left-color: var(--accent);
        }
        
        .message.error {
            background: rgba(231, 111, 81, 0.15);
            color: var(--danger-light);
            border-right-color: var(--danger);
        }
        
        body.english-mode .message.error {
            border-left-color: var(--danger);
        }
        
        /* الأنيميشن */
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(15px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        /* تحسينات مخصصة لأجهزة iOS */
        @supports (-webkit-touch-callout: none) {
            /* تحسينات للتمرير على iOS */
            .control-card, .question, .flashcard, .summary {
                -webkit-overflow-scrolling: touch;
            }
            
            /* تحسينات للإدخال على iOS */
            input, textarea, select {
                font-size: 16px !important; /* منع التكبير التلقائي */
            }
            
            /* تحسينات للأزرار على iOS */
            button {
                cursor: pointer;
                -webkit-user-select: none;
                user-select: none;
            }
        }
        
        /* تحسينات مخصصة لأجهزة Android */
        @supports not (-webkit-touch-callout: none) {
            /* تحسينات للخطوط على Android */
            body {
                text-rendering: optimizeLegibility;
                -webkit-font-smoothing: antialiased;
                -moz-osx-font-smoothing: grayscale;
            }
        }
        
        /* تحسينات للأجهزة المحمولة */
        @media (max-width: 768px) {
            .header {
                padding: 25px 15px 20px;
                padding-top: max(25px, calc(env(safe-area-inset-top) + 15px));
            }
            
            .logo-container {
                flex-direction: column;
                gap: 15px;
            }
            
            .logo-icon {
                width: 60px;
                height: 60px;
                font-size: 2rem;
            }
            
            .logo-text {
                font-size: 2.5rem;
            }
            
            .logo-text::after {
                font-size: 1.5rem;
                right: -4px;
                top: -10px;
            }
            
            body.english-mode .logo-text::after {
                left: -4px;
            }
            
            .header p {
                font-size: 1.1rem;
            }
            
            .mode-tabs {
                flex-direction: column;
            }
            
            .mode-tab {
                min-width: 100%;
            }
            
            .container {
                padding: 20px 15px 40px;
                padding-bottom: max(40px, calc(env(safe-area-inset-bottom) + 20px));
            }
            
            .control-card {
                padding: 25px 20px;
            }
            
            .question {
                padding: 25px 20px;
            }
            
            .question-text {
                font-size: 1.25rem;
            }
            
            .question-number {
                width: 45px;
                height: 45px;
                font-size: 1.2rem;
                margin-left: 15px;
            }
            
            body.english-mode .question-number {
                margin-left: 0;
                margin-right: 15px;
            }
            
            .flashcard {
                padding: 35px 25px;
                min-height: 350px;
            }
            
            .flashcard-front, .flashcard-back {
                font-size: 1.7rem;
            }
            
            .flashcard-nav {
                flex-direction: column;
                gap: 15px;
            }
            
            .flashcard-btn {
                width: 100%;
            }
            
            .summary {
                padding: 25px;
            }
            
            .summary-title {
                font-size: 1.7rem;
            }
            
            .summary-point {
                padding: 18px;
            }
            
            .upload-options {
                flex-direction: column;
            }
            
            .camera-container {
                height: 250px;
            }
            
            /* زيادة مساحة النقر على الهواتف */
            button, .option, .mode-tab, .upload-option-btn {
                min-height: 44px; /* الحد الأدنى لمساحة النقر على iOS */
            }
            
            .option {
                padding: 18px;
            }
        }
        
        /* تحسينات للأجهزة اللوحية */
        @media (min-width: 769px) and (max-width: 1024px) {
            .container {
                max-width: 95%;
            }
        }
        
        /* تحسينات للشاشات الكبيرة */
        @media (min-width: 1025px) {
            .container {
                max-width: 1000px;
            }
        }
        
        /* إخفاء العناصر */
        .hidden {
            display: none !important;
        }
        
        /* تحسينات للوضع الأفقي على الموبايل */
        @media (max-height: 600px) and (orientation: landscape) {
            .header {
                padding: 15px 20px 10px;
                padding-top: max(15px, env(safe-area-inset-top));
            }
            
            .logo-container {
                flex-direction: row;
                gap: 15px;
                margin-bottom: 10px;
            }
            
            .logo-icon {
                width: 50px;
                height: 50px;
                font-size: 1.8rem;
            }
            
            .logo-text {
                font-size: 2rem;
            }
            
            .header p {
                font-size: 1rem;
                line-height: 1.5;
            }
            
            .control-card {
                padding: 20px;
                margin-bottom: 20px;
            }
            
            .mode-tab {
                padding: 15px 10px;
            }
            
            .mode-tab i {
                font-size: 1.8rem;
                margin-bottom: 10px;
            }
            
            .mode-tab span {
                font-size: 1rem;
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
        // كائن للتحقق من نوع الجهاز
        const deviceInfo = {
            isIOS: /iPad|iPhone|iPod/.test(navigator.userAgent) && !window.MSStream,
            isAndroid: /Android/.test(navigator.userAgent),
            isMobile: /Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(navigator.userAgent),
            isTablet: /iPad|Android(?!.*Mobile)/i.test(navigator.userAgent)
        };
        
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
            
            // إعدادات الكاميرا حسب الجهاز
            const constraints = {
                video: {
                    facingMode: 'environment',
                    width: { ideal: 1280 },
                    height: { ideal: 720 }
                },
                audio: false
            };
            
            // تحسينات لأجهزة iOS
            if (deviceInfo.isIOS) {
                constraints.video = {
                    facingMode: 'environment',
                    width: { min: 640, ideal: 1280, max: 1920 },
                    height: { min: 480, ideal: 720, max: 1080 }
                };
            }
            
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
            // إضافة تأثير للعناصر عند التحميل
            document.querySelectorAll('.control-card, .header').forEach(el => {
                el.style.opacity = '0';
                el.style.transform = 'translateY(20px)';
                
                setTimeout(() => {
                    el.style.transition = 'opacity 0.5s ease, transform 0.5s ease';
                    el.style.opacity = '1';
                    el.style.transform = 'translateY(0)';
                }, 100);
            });
            
            // إضافة حدث للنقر على منطقة التحميل
            document.querySelector('.file-upload-area').addEventListener('click', function(e) {
                if (e.target.closest('.upload-option-btn')) {
                    return; // لا تفعل شيئاً إذا تم النقر على زر الخيار
                }
                
                if (currentUploadType === 'image') {
                    imageInput.click();
                } else {
                    fileInput.click();
                }
            });
            
            // تحديث التعليمات الافتراضية
            const fileMessage = document.getElementById('file-message');
            if (fileMessage) {
                fileMessage.innerHTML = '<i class="fas fa-file"></i> يمكنك رفع ملفات نصية أو PDF أو Word أو صور';
                fileMessage.classList.add('success');
                fileMessage.style.display = 'block';
            }
            
            // تحسين تجربة المستخدم على الهواتف
            if (deviceInfo.isMobile) {
                document.body.classList.add('mobile-device');
                
                // منع التكبير عند النقر على المدخلات (خاصة iOS)
                if (deviceInfo.isIOS) {
                    const inputs = document.querySelectorAll('input, textarea, select');
                    inputs.forEach(input => {
                        input.addEventListener('focus', () => {
                            setTimeout(() => {
                                document.body.style.transform = 'scale(1)';
                                window.scrollTo(0, 0);
                            }, 100);
                        });
                    });
                }
                
                // تحسينات للتمرير السلس
                document.querySelectorAll('.container, .control-card, .question, .flashcard, .summary').forEach(el => {
                    el.style.webkitOverflowScrolling = 'touch';
                });
            }
            
            // تحسينات لأجهزة iOS
            if (deviceInfo.isIOS) {
                // إضافة خاصية touch-action للعناصر القابلة للنقر
                document.querySelectorAll('button, .option, .mode-tab, .flashcard').forEach(el => {
                    el.style.cursor = 'pointer';
                });
                
                // تحسينات للكاميرا على iOS
                document.addEventListener('click', function(e) {
                    if (e.target.matches('button, input, textarea, select')) {
                        e.target.style.fontSize = '16px';
                    }
                }, true);
            }
            
            // تحسينات لأجهزة Android
            if (deviceInfo.isAndroid) {
                // تحسينات للخطوط على Android
                document.body.style.textRendering = 'optimizeLegibility';
                document.body.style.webkitFontSmoothing = 'antialiased';
            }
            
            // توقف عن تشغيل الكاميرا عند إغلاق الصفحة
            window.addEventListener('beforeunload', function() {
                if (stream) {
                    stream.getTracks().forEach(track => {
                        track.stop();
                    });
                }
            });
            
            // تحسينات لشاشات Notch (iPhone X وما بعده)
            const style = document.createElement('style');
            style.textContent = `
                @supports (padding: max(0px)) {
                    .top-bar, .header, .container {
                        padding-left: max(20px, env(safe-area-inset-left));
                        padding-right: max(20px, env(safe-area-inset-right));
                    }
                }
            `;
            document.head.appendChild(style);
            
            // إصلاح مشكلة الـ 100vh على iOS
            function setVhProperty() {
                const vh = window.innerHeight * 0.01;
                document.documentElement.style.setProperty('--vh', `${vh}px`);
            }
            
            setVhProperty();
            window.addEventListener('resize', setVhProperty);
            window.addEventListener('orientationchange', setVhProperty);
        });
    </script>
</body>
</html>