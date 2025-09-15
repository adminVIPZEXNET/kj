<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>میکس پلی - دنیایی از برنامه ها</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary-blue: #1E88E5;
            --secondary-green: #43A047;
            --dark-blue: #0D47A1;
            --light-blue: #29B6F6;
            --text-light: #FFFFFF;
            --text-dark: #37474F;
            --bg-light: #E3F2FD;
            --card-bg: #FFFFFF;
            --border-color: #BBDEFB;
            --success: #4CAF50;
            --warning: #FF9800;
            --error: #F44336;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--bg-light);
            color: var(--text-dark);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            overflow-x: hidden;
        }

        /* صفحه اسپلش با انیمیشن تایپ */
        .splash-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, var(--dark-blue) 0%, var(--primary-blue) 100%);
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            z-index: 1000;
            transition: opacity 0.5s ease-out;
        }

        .splash-screen.hidden {
            opacity: 0;
            pointer-events: none;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 15px;
            margin-bottom: 2rem;
        }

        .logo i {
            font-size: 4rem;
            color: var(--text-light);
        }

        .logo h1 {
            font-size: 3.5rem;
            font-weight: 700;
            color: var(--text-light);
        }

        .typing-animation {
            font-size: 2rem;
            color: var(--text-light);
            height: 2.5rem;
            overflow: hidden;
            border-right: 2px solid var(--text-light);
            white-space: nowrap;
            margin: 0 auto;
            animation: blink-caret 0.75s step-end infinite;
        }

        @keyframes blink-caret {
            from, to { border-color: transparent; }
            50% { border-color: var(--text-light); }
        }

        /* استایل‌های اصلی برنامه */
        header {
            background: linear-gradient(135deg, var(--dark-blue) 0%, var(--primary-blue) 100%);
            color: var(--text-light);
            padding: 1rem;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
        }

        .header-content {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .app-logo {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .app-logo h1 {
            font-size: 1.8rem;
            font-weight: 700;
        }

        .app-logo i {
            font-size: 2rem;
        }

        nav ul {
            display: flex;
            list-style: none;
            gap: 1.5rem;
        }

        nav a {
            color: var(--text-light);
            text-decoration: none;
            font-weight: 500;
            padding: 0.5rem;
            border-radius: 4px;
            transition: background-color 0.3s;
        }

        nav a:hover {
            background-color: rgba(255, 255, 255, 0.1);
        }

        .user-actions {
            display: flex;
            gap: 1rem;
            align-items: center;
        }

        .btn {
            padding: 0.6rem 1.2rem;
            border-radius: 4px;
            border: none;
            cursor: pointer;
            font-weight: 500;
            transition: all 0.3s;
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
        }

        .btn-primary {
            background-color: var(--primary-blue);
            color: white;
        }

        .btn-primary:hover {
            background-color: var(--dark-blue);
        }

        .btn-secondary {
            background-color: var(--secondary-green);
            color: white;
        }

        .btn-secondary:hover {
            background-color: #2E7D32;
        }

        .btn-outline {
            background-color: transparent;
            border: 1px solid var(--text-light);
            color: var(--text-light);
        }

        .btn-outline:hover {
            background-color: rgba(255, 255, 255, 0.1);
        }

        .btn-admin {
            background-color: var(--warning);
            color: white;
        }

        .btn-admin:hover {
            background-color: #EF6C00;
        }

        main {
            flex: 1;
            padding: 2rem 1rem;
            max-width: 1200px;
            margin: 0 auto;
            width: 100%;
        }

        .section-title {
            font-size: 1.8rem;
            color: var(--dark-blue);
            margin-bottom: 1.5rem;
            padding-bottom: 0.5rem;
            border-bottom: 2px solid var(--primary-blue);
        }

        .apps-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 1.5rem;
            margin-bottom: 2rem;
        }

        .app-card {
            background-color: var(--card-bg);
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s;
        }

        .app-card:hover {
            transform: translateY(-5px);
        }

        .app-image {
            height: 160px;
            overflow: hidden;
        }

        .app-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .app-info {
            padding: 1rem;
        }

        .app-name {
            font-size: 1.2rem;
            font-weight: 600;
            color: var(--dark-blue);
            margin-bottom: 0.5rem;
        }

        .app-version {
            color: var(--primary-blue);
            font-size: 0.9rem;
            margin-bottom: 0.5rem;
        }

        .app-desc {
            color: var(--text-dark);
            font-size: 0.9rem;
            margin-bottom: 1rem;
            height: 40px;
            overflow: hidden;
        }

        .app-actions {
            display: flex;
            justify-content: space-between;
        }

        .form-container {
            background-color: var(--card-bg);
            border-radius: 8px;
            padding: 2rem;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            max-width: 600px;
            margin: 0 auto;
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 500;
            color: var(--dark-blue);
        }

        .form-control {
            width: 100%;
            padding: 0.8rem;
            border: 1px solid var(--border-color);
            border-radius: 4px;
            font-size: 1rem;
        }

        textarea.form-control {
            min-height: 100px;
            resize: vertical;
        }

        .file-upload {
            border: 2px dashed var(--border-color);
            padding: 1.5rem;
            text-align: center;
            border-radius: 4px;
            cursor: pointer;
            transition: border-color 0.3s;
            position: relative;
        }

        .file-upload:hover {
            border-color: var(--primary-blue);
        }

        .file-upload i {
            font-size: 2rem;
            color: var(--primary-blue);
            margin-bottom: 0.5rem;
        }

        .file-upload input {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            opacity: 0;
            cursor: pointer;
        }

        .file-preview {
            margin-top: 1rem;
            text-align: center;
        }

        .file-preview img {
            max-width: 100%;
            max-height: 200px;
            border-radius: 4px;
            margin-top: 0.5rem;
        }

        .file-name {
            margin-top: 0.5rem;
            font-size: 0.9rem;
            color: var(--primary-blue);
        }

        .admin-panel {
            background-color: var(--card-bg);
            border-radius: 8px;
            padding: 2rem;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }

        .admin-apps {
            display: grid;
            gap: 1rem;
        }

        .admin-app {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem;
            border: 1px solid var(--border-color);
            border-radius: 4px;
        }

        .admin-app-info {
            flex: 1;
        }

        .admin-app-actions {
            display: flex;
            gap: 0.5rem;
        }

        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            justify-content: center;
            align-items: center;
            z-index: 1000;
        }

        .modal-content {
            background-color: var(--card-bg);
            border-radius: 8px;
            padding: 2rem;
            width: 90%;
            max-width: 500px;
            max-height: 90vh;
            overflow-y: auto;
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.5rem;
        }

        .close-modal {
            background: none;
            border: none;
            font-size: 1.5rem;
            cursor: pointer;
            color: var(--text-dark);
        }

        footer {
            background: linear-gradient(135deg, var(--dark-blue) 0%, var(--primary-blue) 100%);
            color: var(--text-light);
            padding: 2rem 1rem;
            text-align: center;
            margin-top: auto;
        }

        .footer-content {
            max-width: 1200px;
            margin: 0 auto;
        }

        .user-welcome {
            color: var(--text-light);
            margin-right: 1rem;
        }

        .admin-login-form {
            max-width: 400px;
            margin: 0 auto;
        }

        .empty-state {
            text-align: center;
            padding: 2rem;
            color: var(--text-dark);
        }

        .empty-state i {
            font-size: 3rem;
            color: var(--primary-blue);
            margin-bottom: 1rem;
        }

        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                gap: 1rem;
            }
            
            nav ul {
                gap: 0.8rem;
                flex-wrap: wrap;
                justify-content: center;
            }
            
            .user-actions {
                flex-wrap: wrap;
                justify-content: center;
            }
            
            .apps-grid {
                grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            }

            .logo h1 {
                font-size: 2.5rem;
            }

            .typing-animation {
                font-size: 1.5rem;
            }

            .admin-app {
                flex-direction: column;
                align-items: flex-start;
                gap: 1rem;
            }

            .admin-app-actions {
                align-self: flex-end;
            }
        }
    </style>
</head>
<body>
    <!-- صفحه اسپلش با انیمیشن تایپ -->
    <div class="splash-screen" id="splashScreen">
        <div class="logo">
            <i class="fas fa-mobile-alt"></i>
            <h1>میکس پلی</h1>
        </div>
        <div class="typing-animation" id="typingAnimation"></div>
    </div>

    <!-- محتوای اصلی برنامه -->
    <div id="appContent" style="display: none;">
        <header>
            <div class="header-content">
                <div class="app-logo">
                    <i class="fas fa-mobile-alt"></i>
                    <h1>میکس پلی</h1>
                </div>
                
                <nav>
                    <ul>
                        <li><a href="#" class="nav-link" data-section="homeSection">خانه</a></li>
                        <li><a href="#" class="nav-link" data-section="homeSection">برنامه‌ها</a></li>
                        <li><a href="#" class="nav-link" data-section="homeSection">درباره ما</a></li>
                        <li><a href="#" class="nav-link" data-section="homeSection">تماس با ما</a></li>
                    </ul>
                </nav>
                
                <div class="user-actions" id="userActions">
                    <button class="btn btn-outline" id="loginBtn">
                        <i class="fas fa-sign-in-alt"></i> ورود
                    </button>
                    <button class="btn btn-primary" id="registerBtn">
                        <i class="fas fa-user-plus"></i> ثبت‌نام
                    </button>
                    <button class="btn btn-secondary" id="submitAppBtn">
                        <i class="fas fa-plus"></i> ارسال برنامه
                    </button>
                    <button class="btn btn-admin" id="adminBtn">
                        <i class="fas fa-cog"></i> پنل ادمین
                    </button>
                </div>
            </div>
        </header>
        
        <main>
            <section id="homeSection">
                <h2 class="section-title">برنامه‌های منتخب</h2>
                
                <div class="apps-grid" id="appsGrid">
                    <!-- برنامه‌ها توسط JavaScript اضافه خواهند شد -->
                </div>
            </section>
            
            <section id="loginSection" style="display: none;">
                <h2 class="section-title">ورود به حساب کاربری</h2>
                
                <div class="form-container">
                    <div class="form-group">
                        <label for="loginEmail">ایمیل</label>
                        <input type="email" id="loginEmail" class="form-control" placeholder="ایمیل خود را وارد کنید">
                    </div>
                    
                    <div class="form-group">
                        <label for="loginPassword">رمز عبور</label>
                        <input type="password" id="loginPassword" class="form-control" placeholder="رمز عبور خود را وارد کنید">
                    </div>
                    
                    <button class="btn btn-primary" style="width: 100%;" id="doLogin">
                        <i class="fas fa-sign-in-alt"></i> ورود
                    </button>
                    
                    <p style="text-align: center; margin-top: 1rem;">
                        حساب کاربری ندارید؟ <a href="#" id="goToRegister" style="color: var(--primary-blue);">ثبت‌نام کنید</a>
                    </p>
                </div>
            </section>
            
            <section id="registerSection" style="display: none;">
                <h2 class="section-title">ایجاد حساب کاربری</h2>
                
                <div class="form-container">
                    <div class="form-group">
                        <label for="registerEmail">ایمیل</label>
                        <input type="email" id="registerEmail" class="form-control" placeholder="ایمیل خود را وارد کنید">
                    </div>
                    
                    <div class="form-group">
                        <label for="registerPassword">رمز عبور</label>
                        <input type="password" id="registerPassword" class="form-control" placeholder="یک رمز عبور انتخاب کنید">
                    </div>
                    
                    <div class="form-group">
                        <label for="registerFirstName">نام</label>
                        <input type="text" id="registerFirstName" class="form-control" placeholder="نام خود را وارد کنید">
                    </div>
                    
                    <div class="form-group">
                        <label for="registerLastName">نام خانوادگی</label>
                        <input type="text" id="registerLastName" class="form-control" placeholder="نام خانوادگی خود را وارد کنید">
                    </div>
                    
                    <button class="btn btn-primary" style="width: 100%;" id="doRegister">
                        <i class="fas fa-user-plus"></i> ثبت‌نام
                    </button>
                    
                    <p style="text-align: center; margin-top: 1rem;">
                        قبلاً حساب کاربری دارید؟ <a href="#" id="goToLogin" style="color: var(--primary-blue);">وارد شوید</a>
                    </p>
                </div>
            </section>
            
            <section id="submitAppSection" style="display: none;">
                <h2 class="section-title">ارسال برنامه جدید</h2>
                
                <div class="form-container">
                    <div class="form-group">
                        <label for="appName">نام برنامه</label>
                        <input type="text" id="appName" class="form-control" placeholder="نام برنامه را وارد کنید">
                    </div>
                    
                    <div class="form-group">
                        <label for="appDescription">توضیحات برنامه</label>
                        <textarea id="appDescription" class="form-control" placeholder="توضیحات کامل درباره برنامه"></textarea>
                    </div>
                    
                    <div class="form-group">
                        <label for="appVersion">ورژن برنامه</label>
                        <input type="text" id="appVersion" class="form-control" placeholder="مثال: ۱.۰.۰" value="1.0.0">
                    </div>
                    
                    <div class="form-group">
                        <label>عکس برنامه</label>
                        <div class="file-upload" id="imageUpload">
                            <i class="fas fa-cloud-upload-alt"></i>
                            <p>برای آپلود عکس برنامه کلیک کنید</p>
                            <input type="file" id="appImage" accept="image/*">
                        </div>
                        <div class="file-preview" id="imagePreview"></div>
                    </div>
                    
                    <div class="form-group">
                        <label>فایل برنامه</label>
                        <div class="file-upload" id="fileUpload">
                            <i class="fas fa-file-upload"></i>
                            <p>برای آپلود فایل برنامه کلیک کنید</p>
                            <input type="file" id="appFile" accept=".apk,.ipa">
                        </div>
                        <div class="file-preview" id="filePreview"></div>
                    </div>
                    
                    <button class="btn btn-primary" style="width: 100%;" id="submitApp">
                        <i class="fas fa-paper-plane"></i> ارسال برای بررسی
                    </button>
                </div>
            </section>
            
            <section id="adminLoginSection" style="display: none;">
                <h2 class="section-title">ورود به پنل مدیریت</h2>
                
                <div class="form-container admin-login-form">
                    <div class="form-group">
                        <label for="adminUsername">نام کاربری ادمین</label>
                        <input type="text" id="adminUsername" class="form-control" placeholder="نام کاربری ادمین">
                    </div>
                    
                    <div class="form-group">
                        <label for="adminPassword">رمز عبور ادمین</label>
                        <input type="password" id="adminPassword" class="form-control" placeholder="رمز عبور ادمین">
                    </div>
                    
                    <button class="btn btn-admin" style="width: 100%;" id="doAdminLogin">
                        <i class="fas fa-sign-in-alt"></i> ورود به پنل مدیریت
                    </button>
                    
                    <p style="text-align: center; margin-top: 1rem;">
                        <a href="#" class="nav-link" data-section="homeSection" style="color: var(--primary-blue);">بازگشت به صفحه اصلی</a>
                    </p>
                </div>
            </section>
            
            <section id="adminSection" style="display: none;">
                <h2 class="section-title">پنل مدیریت</h2>
                
                <div class="admin-panel">
                    <h3 style="margin-bottom: 1rem; color: var(--dark-blue);">برنامه‌های در انتظار تایید</h3>
                    
                    <div class="admin-apps" id="pendingApps">
                        <!-- برنامه‌های در انتظار تایید توسط JavaScript اضافه خواهند شد -->
                    </div>
                    
                    <div style="margin-top: 2rem;">
                        <h3 style="margin-bottom: 1rem; color: var(--dark-blue);">برنامه‌های تایید شده</h3>
                        
                        <div class="admin-apps" id="approvedApps">
                            <!-- برنامه‌های تایید شده توسط JavaScript اضافه خواهند شد -->
                        </div>
                    </div>
                    
                    <div style="margin-top: 2rem; text-align: center;">
                        <button class="btn btn-outline" id="adminLogoutBtn">
                            <i class="fas fa-sign-out-alt"></i> خروج از پنل مدیریت
                        </button>
                    </div>
                </div>
            </section>
        </main>
        
        <footer>
            <div class="footer-content">
                <p>© ۲۰۲۳ میکس پلی - تمام حقوق محفوظ است</p>
                <p>پلتفرم انتشار برنامه‌های موبایل</p>
            </div>
        </footer>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // انیمیشن تایپ متن
            const text = "میکس پلی  دنیایی از برنامه ها";
            let index = 0;
            const typingElement = document.getElementById('typingAnimation');
            const splashScreen = document.getElementById('splashScreen');
            const appContent = document.getElementById('appContent');
            
            function typeText() {
                if (index < text.length) {
                    typingElement.textContent += text.charAt(index);
                    index++;
                    setTimeout(typeText, 100);
                } else {
                    // پس از اتمام تایپ، صفحه اسپلش را مخفی کرده و برنامه را نمایش دهید
                    setTimeout(() => {
                        splashScreen.classList.add('hidden');
                        appContent.style.display = 'block';
                        loadApps(); // بارگذاری برنامه‌ها
                    }, 1500);
                }
            }
            
            // شروع انیمیشن تایپ
            typeText();
            
            // اطلاعات ادمین
            const ADMIN_USERNAME = "admin";
            const ADMIN_PASSWORD = "admin123";
            
            // عناصر صفحه
            const homeSection = document.getElementById('homeSection');
            const loginSection = document.getElementById('loginSection');
            const registerSection = document.getElementById('registerSection');
            const submitAppSection = document.getElementById('submitAppSection');
            const adminLoginSection = document.getElementById('adminLoginSection');
            const adminSection = document.getElementById('adminSection');
            const userActions = document.getElementById('userActions');
            const appsGrid = document.getElementById('appsGrid');
            const pendingApps = document.getElementById('pendingApps');
            const approvedApps = document.getElementById('approvedApps');
            
            // دکمه‌های ناوبری
            const loginBtn = document.getElementById('loginBtn');
            const registerBtn = document.getElementById('registerBtn');
            const submitAppBtn = document.getElementById('submitAppBtn');
            const adminBtn = document.getElementById('adminBtn');
            const goToLogin = document.getElementById('goToLogin');
            const goToRegister = document.getElementById('goToRegister');
            const doLogin = document.getElementById('doLogin');
            const doRegister = document.getElementById('doRegister');
            const doAdminLogin = document.getElementById('doAdminLogin');
            const adminLogoutBtn = document.getElementById('adminLogoutBtn');
            const submitApp = document.getElementById('submitApp');
            
            // مدیریت آپلود فایل
            const appImage = document.getElementById('appImage');
            const appFile = document.getElementById('appFile');
            const imagePreview = document.getElementById('imagePreview');
            const filePreview = document.getElementById('filePreview');
            
            // نمایش بخش‌های مختلف
            function showSection(section) {
                // مخفی کردن تمام بخش‌ها
                homeSection.style.display = 'none';
                loginSection.style.display = 'none';
                registerSection.style.display = 'none';
                submitAppSection.style.display = 'none';
                adminLoginSection.style.display = 'none';
                adminSection.style.display = 'none';
                
                // نمایش بخش مورد نظر
                document.getElementById(section).style.display = 'block';
            }
            
            // رویدادهای کلیک
            loginBtn.addEventListener('click', () => showSection('loginSection'));
            registerBtn.addEventListener('click', () => showSection('registerSection'));
            submitAppBtn.addEventListener('click', () => {
                if (isLoggedIn()) {
                    showSection('submitAppSection');
                } else {
                    showSection('loginSection');
                    alert('لطفاً ابتدا وارد حساب کاربری خود شوید');
                }
            });
            
            adminBtn.addEventListener('click', () => {
                showSection('adminLoginSection');
            });
            
            goToLogin.addEventListener('click', (e) => {
                e.preventDefault();
                showSection('loginSection');
            });
            
            goToRegister.addEventListener('click', (e) => {
                e.preventDefault();
                showSection('registerSection');
            });
            
            // لینک‌های ناوبری
            document.querySelectorAll('.nav-link').forEach(link => {
                link.addEventListener('click', (e) => {
                    e.preventDefault();
                    showSection(link.dataset.section);
                });
            });
            
            // بررسی وضعیت ورود کاربر
            function isLoggedIn() {
                return localStorage.getItem('userEmail') !== null;
            }
            
            // بارگذاری برنامه‌ها از localStorage
            function loadApps() {
                const savedApps = JSON.parse(localStorage.getItem('approvedApps') || '[]');
                appsGrid.innerHTML = '';
                
                if (savedApps.length === 0) {
                    appsGrid.innerHTML = `
                        <div class="empty-state">
                            <i class="fas fa-mobile-alt"></i>
                            <h3>هنوز برنامه‌ای اضافه نشده است</h3>
                            <p>اولین نفری باشید که برنامه خود را اضافه می‌کند</p>
                        </div>
                    `;
                    return;
                }
                
                savedApps.forEach(app => {
                    const appCard = document.createElement('div');
                    appCard.className = 'app-card';
                    appCard.innerHTML = `
                        <div class="app-image">
                            <img src="${app.image}" alt="${app.name}">
                        </div>
                        <div class="app-info">
                            <h3 class="app-name">${app.name}</h3>
                            <div class="app-version">ورژن: ${app.version}</div>
                            <p class="app-desc">${app.description}</p>
                            <div class="app-actions">
                                <button class="btn btn-primary">
                                    <i class="fas fa-info-circle"></i> جزئیات
                                </button>
                                <button class="btn btn-secondary">
                                    <i class="fas fa-download"></i> دانلود
                                </button>
                            </div>
                        </div>
                    `;
                    appsGrid.appendChild(appCard);
                });
            }
            
            // بارگذاری برنامه‌های در انتظار تایید برای ادمین
            function loadPendingApps() {
                const pending = JSON.parse(localStorage.getItem('pendingApps') || '[]');
                pendingApps.innerHTML = '';
                
                if (pending.length === 0) {
                    pendingApps.innerHTML = `
                        <div class="empty-state">
                            <i class="fas fa-check-circle"></i>
                            <p>هیچ برنامه‌ای در انتظار تایید نیست</p>
                        </div>
                    `;
                    return;
                }
                
                pending.forEach(app => {
                    const appElement = document.createElement('div');
                    appElement.className = 'admin-app';
                    appElement.innerHTML = `
                        <div class="admin-app-info">
                            <h4>${app.name}</h4>
                            <p>ارسال شده توسط: ${app.submittedBy}</p>
                            <p>${app.description}</p>
                        </div>
                        <div class="admin-app-actions">
                            <button class="btn btn-secondary approve-btn" data-app-id="${app.id}">
                                <i class="fas fa-check"></i> تایید
                            </button>
                            <button class="btn btn-outline reject-btn" data-app-id="${app.id}" style="color: var(--error);">
                                <i class="fas fa-times"></i> رد
                            </button>
                        </div>
                    `;
                    pendingApps.appendChild(appElement);
                });
                
                // اضافه کردن رویداد به دکمه‌های تایید و رد
                document.querySelectorAll('.approve-btn').forEach(btn => {
                    btn.addEventListener('click', () => {
                        approveApp(btn.dataset.appId);
                    });
                });
                
                document.querySelectorAll('.reject-btn').forEach(btn => {
                    btn.addEventListener('click', () => {
                        rejectApp(btn.dataset.appId);
                    });
                });
            }
            
            // بارگذاری برنامه‌های تایید شده برای ادمین
            function loadApprovedApps() {
                const approved = JSON.parse(localStorage.getItem('approvedApps') || '[]');
                approvedApps.innerHTML = '';
                
                if (approved.length === 0) {
                    approvedApps.innerHTML = `
                        <div class="empty-state">
                            <i class="fas fa-box-open"></i>
                            <p>هیچ برنامه‌ای تایید نشده است</p>
                        </div>
                    `;
                    return;
                }
                
                approved.forEach(app => {
                    const appElement = document.createElement('div');
                    appElement.className = 'admin-app';
                    appElement.innerHTML = `
                        <div class="admin-app-info">
                            <h4>${app.name}</h4>
                            <p>ارسال شده توسط: ${app.submittedBy}</p>
                            <p>${app.description}</p>
                        </div>
                        <div class="admin-app-actions">
                            <button class="btn btn-outline delete-btn" data-app-id="${app.id}" style="color: var(--error);">
                                <i class="fas fa-trash"></i> حذف
                            </button>
                        </div>
                    `;
                    approvedApps.appendChild(appElement);
                });
                
                // اضافه کردن رویداد به دکمه‌های حذف
                document.querySelectorAll('.delete-btn').forEach(btn => {
                    btn.addEventListener('click', () => {
                        deleteApp(btn.dataset.appId);
                    });
                });
            }
            
            // تایید برنامه توسط ادمین
            function approveApp(appId) {
                const pending = JSON.parse(localStorage.getItem('pendingApps') || '[]');
                const approved = JSON.parse(localStorage.getItem('approvedApps') || '[]');
                
                const appIndex = pending.findIndex(app => app.id === appId);
                if (appIndex === -1) return;
                
                const app = pending[appIndex];
                pending.splice(appIndex, 1);
                
                approved.push(app);
                
                localStorage.setItem('pendingApps', JSON.stringify(pending));
                localStorage.setItem('approvedApps', JSON.stringify(approved));
                
                loadPendingApps();
                loadApprovedApps();
                loadApps();
                
                alert('برنامه با موفقیت تایید شد');
            }
            
            // رد برنامه توسط ادمین
            function rejectApp(appId) {
                const pending = JSON.parse(localStorage.getItem('pendingApps') || '[]');
                
                const appIndex = pending.findIndex(app => app.id === appId);
                if (appIndex === -1) return;
                
                pending.splice(appIndex, 1);
                
                localStorage.setItem('pendingApps', JSON.stringify(pending));
                
                loadPendingApps();
                
                alert('برنامه با موفقیت رد شد');
            }
            
            // حذف برنامه توسط ادمین
            function deleteApp(appId) {
                const approved = JSON.parse(localStorage.getItem('approvedApps') || '[]');
                
                const appIndex = approved.findIndex(app => app.id === appId);
                if (appIndex === -1) return;
                
                approved.splice(appIndex, 1);
                
                localStorage.setItem('approvedApps', JSON.stringify(approved));
                
                loadApprovedApps();
                loadApps();
                
                alert('برنامه با موفقیت حذف شد');
            }
            
            // نمایش وضعیت کاربر در نوار بالایی
            function updateUserStatus() {
                const userEmail = localStorage.getItem('userEmail');
                const userName = localStorage.getItem('userName');
                
                if (userEmail) {
                    userActions.innerHTML = `
                        <span class="user-welcome">خوش آمدید ${userName}</span>
                        <button class="btn btn-outline" id="logoutBtn">
                            <i class="fas fa-sign-out-alt"></i> خروج
                        </button>
                        <button class="btn btn-secondary" id="submitAppBtn">
                            <i class="fas fa-plus"></i> ارسال برنامه
                        </button>
                        <button class="btn btn-admin" id="adminBtn">
                            <i class="fas fa-cog"></i> پنل ادمین
                        </button>
                    `;
                    
                    document.getElementById('logoutBtn').addEventListener('click', logout);
                    document.getElementById('submitAppBtn').addEventListener('click', () => showSection('submitAppSection'));
                    document.getElementById('adminBtn').addEventListener('click', () => showSection('adminLoginSection'));
                }
            }
            
            // پیش‌نمایش عکس آپلود شده
            appImage.addEventListener('change', function() {
                const file = this.files[0];
                if (file) {
                    const reader = new FileReader();
                    reader.onload = function(e) {
                        imagePreview.innerHTML = `
                            <img src="${e.target.result}" alt="Preview">
                            <div class="file-name">${file.name}</div>
                        `;
                    };
                    reader.readAsDataURL(file);
                }
            });
            
            // پیش‌نمایش فایل آپلود شده
            appFile.addEventListener('change', function() {
                const file = this.files[0];
                if (file) {
                    filePreview.innerHTML = `
                        <i class="fas fa-file" style="font-size: 3rem; color: var(--primary-blue);"></i>
                        <div class="file-name">${file.name}</div>
                    `;
                }
            });
            
            // ارسال برنامه جدید
            submitApp.addEventListener('click', function() {
                const name = document.getElementById('appName').value;
                const description = document.getElementById('appDescription').value;
                const version = document.getElementById('appVersion').value;
                const imageFile = appImage.files[0];
                const appFile = document.getElementById('appFile').files[0];
                
                if (!name || !description || !version || !imageFile || !appFile) {
                    alert('لطفاً تمام فیلدهای ضروری را پر کنید');
                    return;
                }
                
                // خواندن عکس به صورت Data URL
                const reader = new FileReader();
                reader.onload = function(e) {
                    const appData = {
                        id: Date.now().toString(),
                        name,
                        description,
                        version,
                        image: e.target.result,
                        fileName: appFile.name,
                        submittedBy: localStorage.getItem('userName') || 'کاربر ناشناس',
                        date: new Date().toLocaleDateString('fa-IR')
                    };
                    
                    // ذخیره برنامه در لیست انتظار
                    const pendingApps = JSON.parse(localStorage.getItem('pendingApps') || '[]');
                    pendingApps.push(appData);
                    localStorage.setItem('pendingApps', JSON.stringify(pendingApps));
                    
                    // ریست فرم
                    document.getElementById('appName').value = '';
                    document.getElementById('appDescription').value = '';
                    document.getElementById('appVersion').value = '1.0.0';
                    appImage.value = '';
                    document.getElementById('appFile').value = '';
                    imagePreview.innerHTML = '';
                    filePreview.innerHTML = '';
                    
                    // نمایش پیام موفقیت
                    alert('برنامه با موفقیت ارسال شد و در انتظار تایید ادمین است');
                    showSection('homeSection');
                };
                reader.readAsDataURL(imageFile);
            });
            
            // عملیات ورود
            doLogin.addEventListener('click', function() {
                const email = document.getElementById('loginEmail').value;
                const password = document.getElementById('loginPassword').value;
                
                if (!email || !password) {
                    alert('لطفاً ایمیل و رمز عبور خود را وارد کنید');
                    return;
                }
                
                // ذخیره اطلاعات کاربر در localStorage
                localStorage.setItem('userEmail', email);
                localStorage.setItem('userName', 'کاربر میکس پلی');
                
                // به روزرسانی وضعیت کاربر
                updateUserStatus();
                
                // نمایش صفحه اصلی
                showSection('homeSection');
                
                alert('ورود با موفقیت انجام شد');
            });
            
            // عملیات ثبت‌نام
            doRegister.addEventListener('click', function() {
                const email = document.getElementById('registerEmail').value;
                const password = document.getElementById('registerPassword').value;
                const firstName = document.getElementById('registerFirstName').value;
                const lastName = document.getElementById('registerLastName').value;
                
                if (!email || !password || !firstName || !lastName) {
                    alert('لطفاً تمام فیلدهای ضروری را پر کنید');
                    return;
                }
                
                // ذخیره اطلاعات کاربر در localStorage
                localStorage.setItem('userEmail', email);
                localStorage.setItem('userName', `${firstName} ${lastName}`);
                
                // به روزرسانی وضعیت کاربر
                updateUserStatus();
                
                // نمایش صفحه اصلی
                showSection('homeSection');
                
                alert('ثبت‌نام با موفقیت انجام شد');
            });
            
            // ورود ادمین
            doAdminLogin.addEventListener('click', function() {
                const username = document.getElementById('adminUsername').value;
                const password = document.getElementById('adminPassword').value;
                
                if (username === ADMIN_USERNAME && password === ADMIN_PASSWORD) {
                    // نمایش پنل ادمین
                    showSection('adminSection');
                    loadPendingApps();
                    loadApprovedApps();
                } else {
                    alert('نام کاربری یا رمز عبور ادمین اشتباه است');
                }
            });
            
            // خروج از پنل ادمین
            adminLogoutBtn.addEventListener('click', function() {
                showSection('homeSection');
            });
            
            // عملیات خروج
            function logout() {
                localStorage.removeItem('userEmail');
                localStorage.removeItem('userName');
                
                userActions.innerHTML = `
                    <button class="btn btn-outline" id="loginBtn">
                        <i class="fas fa-sign-in-alt"></i> ورود
                    </button>
                    <button class="btn btn-primary" id="registerBtn">
                        <i class="fas fa-user-plus"></i> ثبت‌نام
                    </button>
                    <button class="btn btn-secondary" id="submitAppBtn">
                        <i class="fas fa-plus"></i> ارسال برنامه
                    </button>
                    <button class="btn btn-admin" id="adminBtn">
                        <i class="fas fa-cog"></i> پنل ادمین
                    </button>
                `;
                
                // اضافه کردن مجدد رویدادها به دکمه‌ها
                document.getElementById('loginBtn').addEventListener('click', () => showSection('loginSection'));
                document.getElementById('registerBtn').addEventListener('click', () => showSection('registerSection'));
                document.getElementById('submitAppBtn').addEventListener('click', () => {
                    showSection('loginSection');
                    alert('لطفاً ابتدا وارد حساب کاربری خود شوید');
                });
                document.getElementById('adminBtn').addEventListener('click', () => showSection('adminLoginSection'));
                
                // نمایش صفحه اصلی
                showSection('homeSection');
                
                alert('خروج با موفقیت انجام شد');
            }
            
            // بررسی وضعیت کاربر هنگام بارگذاری صفحه
            updateUserStatus();
        });
    </script>
</body>
</html>
