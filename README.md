<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Evil Bar - إيفل بار | Luxury Cafe</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.rtl.min.css" rel="stylesheet">
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" rel="stylesheet">
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">
    <style>
        :root {
            --bg: #020202; --bg2: #0a0a0a; --bg3: #111;
            --gold: #D4AF37; --gold2: #FFD700; --gold3: #F4D03F;
            --white: #fff; --gray: #999; --gray2: #666;
            --red: #e74c3c; --green: #2ecc71; --orange: #f39c12; --blue: #3498db;
            --glass: rgba(15,15,15,0.8); --border-gold: rgba(212,175,55,0.25);
            --shadow-gold: 0 0 20px rgba(212,175,55,0.2);
            --shadow-gold2: 0 0 40px rgba(212,175,55,0.4);
            --radius: 16px; --transition: all 0.35s cubic-bezier(0.4,0,0.2,1);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }
        body {
            background: var(--bg); color: var(--white);
            font-family: 'Segoe UI', Tahoma, sans-serif; min-height: 100vh;
            overflow-x: hidden;
        }

        /* ============ PARTICLES ============ */
        #particlesCanvas { position: fixed; top: 0; left: 0; width: 100%; height: 100%; z-index: 0; pointer-events: none; }

        /* ============ PRELOADER ============ */
        #preloader {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: #000; z-index: 99999; display: flex;
            align-items: center; justify-content: center; flex-direction: column;
            transition: opacity 0.5s, visibility 0.5s;
        }
        #preloader.hidden { opacity: 0; visibility: hidden; }
        .preloader-logo {
            font-size: 50px; font-weight: 900; color: var(--gold);
            animation: preloaderPulse 1.5s infinite; letter-spacing: 8px;
            text-shadow: 0 0 30px rgba(212,175,55,0.6);
        }
        @keyframes preloaderPulse {
            0%,100% { opacity: 1; transform: scale(1); }
            50% { opacity: 0.6; transform: scale(1.08); }
        }
        .preloader-spinner {
            width: 60px; height: 60px; border: 3px solid #333;
            border-top-color: var(--gold); border-radius: 50%;
            animation: spin 1s linear infinite; margin-top: 20px;
        }
        @keyframes spin { to { transform: rotate(360deg); } }

        /* ============ AUTH PAGE ============ */
        #authPage {
            display: flex; min-height: 100vh; align-items: center;
            justify-content: center; padding: 20px; position: relative; z-index: 1;
        }
        .auth-container {
            width: 100%; max-width: 460px;
            animation: authSlideIn 0.7s cubic-bezier(0.22,0.61,0.36,1);
        }
        @keyframes authSlideIn {
            from { opacity: 0; transform: translateY(30px) scale(0.95); }
            to { opacity: 1; transform: translateY(0) scale(1); }
        }
        .auth-card {
            background: rgba(15,15,15,0.9); backdrop-filter: blur(25px);
            border: 1px solid var(--border-gold); border-radius: 24px;
            padding: 35px 30px; box-shadow: var(--shadow-gold2);
        }
        .auth-logo {
            text-align: center; margin-bottom: 25px;
        }
        .auth-logo h1 {
            font-size: 42px; font-weight: 900;
            background: linear-gradient(135deg, #8B7500, var(--gold), var(--gold3), var(--gold));
            background-size: 300% 300%; -webkit-background-clip: text;
            -webkit-text-fill-color: transparent; animation: goldShimmer 4s infinite;
            letter-spacing: 6px;
        }
        @keyframes goldShimmer {
            0%,100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }
        .auth-logo .subtitle {
            color: var(--gray); font-size: 14px; margin-top: 5px; letter-spacing: 2px;
        }

        .auth-tabs {
            display: flex; gap: 6px; background: rgba(255,255,255,0.03);
            border-radius: 14px; padding: 5px; margin-bottom: 22px;
        }
        .auth-tab {
            flex: 1; padding: 11px; text-align: center; border: none;
            background: transparent; color: var(--gray); border-radius: 11px;
            cursor: pointer; font-size: 13px; font-weight: 600; transition: var(--transition);
        }
        .auth-tab.active {
            background: linear-gradient(135deg, var(--gold-dark, #8B7500), var(--gold));
            color: #000; font-weight: 700; box-shadow: var(--shadow-gold);
        }

        .form-group { margin-bottom: 15px; }
        .form-group label {
            display: block; margin-bottom: 5px; color: var(--gray2);
            font-size: 12px; font-weight: 600;
        }
        .form-input {
            width: 100%; padding: 14px 16px; background: rgba(255,255,255,0.03);
            border: 1.5px solid rgba(255,255,255,0.1); border-radius: 12px;
            color: var(--white); font-size: 15px; transition: var(--transition);
        }
        .form-input:focus {
            outline: none; border-color: var(--gold);
            box-shadow: 0 0 0 3px rgba(212,175,55,0.08);
        }
        .form-input::placeholder { color: rgba(255,255,255,0.2); }

        .btn {
            width: 100%; padding: 14px; border: none; border-radius: 12px;
            font-size: 15px; font-weight: 700; cursor: pointer; transition: var(--transition);
            display: flex; align-items: center; justify-content: center; gap: 8px;
        }
        .btn-gold {
            background: linear-gradient(135deg, #7A6500, var(--gold), var(--gold3));
            color: #000; position: relative; overflow: hidden;
        }
        .btn-gold::after {
            content: ''; position: absolute; top: -50%; left: -50%;
            width: 200%; height: 200%;
            background: linear-gradient(45deg, transparent 40%, rgba(255,255,255,0.3) 50%, transparent 60%);
            animation: btnShine 3s infinite;
        }
        @keyframes btnShine { 0% { transform: translateX(-100%) rotate(45deg); } 100% { transform: translateX(100%) rotate(45deg); } }
        .btn-gold:hover { transform: translateY(-3px); box-shadow: 0 10px 30px rgba(212,175,55,0.5); }
        .btn-outline { background: transparent; border: 2px solid var(--border-gold); color: var(--gold); }
        .btn-outline:hover { background: rgba(212,175,55,0.08); border-color: var(--gold); }
        .btn-google { background: #fff; color: #333; font-weight: 600; }
        .btn-google:hover { background: #f0f0f0; }
        .btn-red { background: var(--red); color: #fff; }
        .btn-green { background: var(--green); color: #fff; }
        .btn-sm { width: auto; padding: 8px 16px; font-size: 13px; }

        .divider {
            display: flex; align-items: center; gap: 15px; margin: 18px 0;
            color: var(--gray2); font-size: 12px;
        }
        .divider::before, .divider::after {
            content: ''; flex: 1; height: 1px; background: rgba(255,255,255,0.1);
        }
        .auth-link { color: var(--gold); cursor: pointer; font-weight: 600; }
        .auth-link:hover { text-decoration: underline; }

        /* ============ MAIN APP ============ */
        #mainApp { display: none; position: relative; z-index: 1; }
        #mainApp.show { display: block; animation: fadeIn 0.5s ease; }
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }

        /* Top Bar with 3 dots */
        .top-bar {
            background: #050505; border-bottom: 1px solid rgba(212,175,55,0.15);
            padding: 8px 20px; display: flex; align-items: center; justify-content: space-between;
            font-size: 13px; color: var(--gray);
        }
        .top-bar .dot-menu {
            display: flex; gap: 6px; align-items: center;
        }
        .top-bar .dot {
            width: 8px; height: 8px; border-radius: 50%; cursor: pointer;
            transition: var(--transition);
        }
        .top-bar .dot.red { background: var(--red); }
        .top-bar .dot.orange { background: var(--orange); }
        .top-bar .dot.green { background: var(--green); }
        .top-bar .dot:hover { transform: scale(1.5); }

        /* Navbar */
        .navbar-evil {
            background: rgba(5,5,5,0.9); backdrop-filter: blur(25px);
            border-bottom: 1px solid rgba(212,175,55,0.1);
            padding: 12px 20px; position: sticky; top: 0; z-index: 100;
            display: flex; align-items: center; justify-content: space-between;
            flex-wrap: wrap; gap: 10px; transition: var(--transition);
        }
        .navbar-evil.scrolled { box-shadow: 0 5px 30px rgba(0,0,0,0.6); }
        .brand {
            display: flex; align-items: center; gap: 10px;
            color: var(--gold); font-size: 24px; font-weight: 900;
            text-decoration: none; letter-spacing: 3px; cursor: pointer;
        }
        .brand img { width: 40px; height: 40px; border-radius: 10px; }
        .nav-links { display: flex; gap: 4px; flex-wrap: wrap; align-items: center; }
        .nav-link-item {
            color: #ccc; text-decoration: none; padding: 7px 13px;
            border-radius: 8px; font-size: 13px; cursor: pointer; transition: var(--transition);
            font-weight: 500; border: none; background: none; font-family: inherit;
        }
        .nav-link-item:hover, .nav-link-item.active {
            color: var(--gold); background: rgba(212,175,55,0.08);
        }
        .nav-cart-btn {
            background: transparent; border: 1.5px solid rgba(255,255,255,0.2);
            color: #fff; padding: 7px 14px; border-radius: 50px; cursor: pointer;
            font-weight: 600; font-size: 13px; transition: var(--transition); position: relative;
        }
        .nav-cart-btn:hover { border-color: var(--gold); color: var(--gold); }
        .cart-badge {
            position: absolute; top: -7px; right: -7px; background: var(--gold);
            color: #000; border-radius: 50%; width: 20px; height: 20px;
            font-size: 11px; display: flex; align-items: center; justify-content: center;
            font-weight: 900; animation: badgePop 0.3s ease;
        }
        @keyframes badgePop { 0%{transform:scale(0)} 50%{transform:scale(1.3)} 100%{transform:scale(1)} }

        /* Hero */
        .hero {
            min-height: 85vh; display: flex; align-items: center; justify-content: center;
            text-align: center; position: relative;
            background: radial-gradient(ellipse at center, rgba(212,175,55,0.05) 0%, transparent 70%);
        }
        .hero h1 {
            font-size: clamp(50px, 10vw, 100px); font-weight: 900;
            background: linear-gradient(135deg, #6B5B00, var(--gold), var(--gold3), var(--gold));
            background-size: 300% 300%; -webkit-background-clip: text;
            -webkit-text-fill-color: transparent; animation: goldShimmer 5s infinite;
            letter-spacing: 10px;
        }
        .hero p { font-size: 18px; color: var(--gray); margin: 15px 0 25px; }
        .hero-btns { display: flex; gap: 15px; justify-content: center; flex-wrap: wrap; }
        .hero-btn {
            padding: 15px 35px; border-radius: 50px; font-size: 16px; font-weight: 700;
            cursor: pointer; transition: var(--transition); text-decoration: none;
            display: inline-flex; align-items: center; gap: 8px;
        }
        .hero-btn-primary {
            background: linear-gradient(135deg, #7A6500, var(--gold)); color: #000; border: none;
        }
        .hero-btn-primary:hover { transform: translateY(-5px); box-shadow: 0 15px 40px rgba(212,175,55,0.5); }
        .hero-btn-outline {
            background: transparent; border: 2px solid var(--gold); color: var(--gold);
        }
        .hero-btn-outline:hover { background: var(--gold); color: #000; transform: translateY(-5px); }

        /* Sections */
        .section { padding: 70px 20px; }
        .section-dark { background: var(--bg2); }
        .section-title {
            text-align: center; font-size: 32px; font-weight: 900; margin-bottom: 40px;
        }
        .gold-text { color: var(--gold); }
        .section-title::after {
            content: ''; display: block; width: 60px; height: 3px;
            background: linear-gradient(90deg, transparent, var(--gold), transparent);
            margin: 12px auto 0;
        }

        /* Products */
        .products-grid {
            display: grid; grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 20px; max-width: 1200px; margin: 0 auto;
        }
        .product-card {
            background: rgba(18,18,18,0.9); border: 1px solid rgba(255,255,255,0.06);
            border-radius: 18px; overflow: hidden; transition: var(--transition);
        }
        .product-card:hover {
            transform: translateY(-8px); border-color: var(--border-gold);
            box-shadow: 0 20px 50px rgba(0,0,0,0.5), var(--shadow-gold);
        }
        .product-img { height: 200px; overflow: hidden; position: relative; }
        .product-img img { width: 100%; height: 100%; object-fit: cover; transition: 0.6s; }
        .product-card:hover .product-img img { transform: scale(1.1); }
        .badge-discount {
            position: absolute; top: 10px; left: 10px; background: var(--red);
            color: #fff; padding: 3px 10px; border-radius: 20px; font-size: 11px; font-weight: 700;
        }
        .product-body { padding: 16px; }
        .product-body h5 { font-size: 16px; margin-bottom: 4px; }
        .product-body .desc { color: #888; font-size: 12px; margin-bottom: 8px; }
        .price-row { display: flex; align-items: center; gap: 8px; margin-bottom: 6px; }
        .price-old { text-decoration: line-through; color: #666; font-size: 13px; }
        .price-current { color: var(--gold); font-size: 20px; font-weight: 900; }
        .stars { color: var(--gold); font-size: 12px; margin-bottom: 10px; }
        .btn-add-cart {
            width: 100%; padding: 10px; background: linear-gradient(135deg, #7A6500, var(--gold));
            color: #000; border: none; border-radius: 10px; font-weight: 700; cursor: pointer;
            font-size: 14px; transition: var(--transition);
        }
        .btn-add-cart:hover { box-shadow: var(--shadow-gold2); }

        /* Cart Sidebar */
        .cart-overlay { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.8); z-index: 2000; display: none; backdrop-filter: blur(5px); }
        .cart-overlay.open { display: block; }
        .cart-sidebar { position: fixed; top: 0; right: -420px; width: 400px; height: 100%; background: #0d0d0d; z-index: 2001; transition: right 0.4s; border-left: 1px solid var(--border-gold); padding: 22px; overflow-y: auto; }
        .cart-sidebar.open { right: 0; }

        /* Modal */
        .modal-overlay { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.9); z-index: 3000; display: none; align-items: center; justify-content: center; backdrop-filter: blur(8px); }
        .modal-overlay.open { display: flex; }
        .modal-dialog { background: #111; border: 2px solid var(--border-gold); border-radius: 24px; padding: 28px; width: 90%; max-width: 520px; max-height: 85vh; overflow-y: auto; animation: modalIn 0.4s; }
        @keyframes modalIn { from{opacity:0;transform:scale(0.9)translateY(20px);} to{opacity:1;transform:scale(1)translateY(0);} }

        /* Dashboard */
        .dash-stats { display: grid; grid-template-columns: repeat(auto-fill, minmax(200px, 1fr)); gap: 15px; margin-bottom: 25px; }
        .dash-stat { background: rgba(18,18,18,0.9); border: 1px solid rgba(255,255,255,0.06); border-radius: 16px; padding: 22px; text-align: center; transition: var(--transition); }
        .dash-stat:hover { border-color: var(--border-gold); transform: translateY(-3px); }
        .dash-stat h2 { font-size: 36px; font-weight: 900; color: var(--gold); }
        .dash-stat p { color: var(--gray); font-size: 13px; margin-top: 4px; }

        .table-dark { width: 100%; border-collapse: collapse; font-size: 13px; }
        .table-dark th { background: rgba(212,175,55,0.08); color: var(--gold); padding: 12px; text-align: right; font-weight: 700; border-bottom: 2px solid var(--border-gold); }
        .table-dark td { padding: 10px 12px; border-bottom: 1px solid rgba(255,255,255,0.04); }
        .table-dark tr:hover td { background: rgba(255,255,255,0.02); }

        .status-pending { background: var(--orange); color: #000; padding: 3px 10px; border-radius: 20px; font-size: 11px; font-weight: 700; }
        .status-approved { background: var(--green); color: #fff; padding: 3px 10px; border-radius: 20px; font-size: 11px; font-weight: 700; }
        .status-rejected { background: var(--red); color: #fff; padding: 3px 10px; border-radius: 20px; font-size: 11px; font-weight: 700; }

        /* Toast */
        .toast-container { position: fixed; bottom: 25px; right: 25px; z-index: 9999; display: flex; flex-direction: column; gap: 10px; }
        .toast-msg { background: #1a1a1a; border: 1px solid var(--border-gold); padding: 15px 20px; border-radius: 14px; color: #fff; font-weight: 600; font-size: 14px; animation: toastIn 0.4s; box-shadow: 0 10px 30px rgba(0,0,0,0.5); display: flex; align-items: center; gap: 10px; min-width: 280px; }
        .toast-msg.success { border-right: 4px solid var(--green); }
        .toast-msg.error { border-right: 4px solid var(--red); }
        @keyframes toastIn { from{opacity:0;transform:translateX(80px);} to{opacity:1;transform:translateX(0);} }

        footer { background: #020202; border-top: 1px solid rgba(212,175,55,0.1); padding: 30px; text-align: center; color: #888; }

        @media (max-width: 768px) {
            .hero h1 { font-size: 38px; }
            .cart-sidebar { width: 100%; right: -100%; }
            .products-grid { grid-template-columns: repeat(auto-fill, minmax(155px, 1fr)); gap: 12px; }
        }
    </style>
</head>
<body>

    <canvas id="particlesCanvas"></canvas>

    <div id="preloader">
        <div class="preloader-logo">EVIL BAR</div>
        <div class="preloader-spinner"></div>
    </div>

    <div class="toast-container" id="toastContainer"></div>

    <!-- ==================== AUTH PAGE ==================== -->
    <div id="authPage">
        <div class="auth-container">
            <div class="auth-card">
                <div class="auth-logo">
                    <h1>EVIL BAR</h1>
                    <p class="subtitle">✦ أفخم كافيه وبار في المدينة ✦</p>
                </div>

                <div class="auth-tabs">
                    <button class="auth-tab active" onclick="switchTab('login')">🔑 دخول</button>
                    <button class="auth-tab" onclick="switchTab('register')">📝 حساب جديد</button>
                </div>

                <div id="loginForm">
                    <div class="form-group"><label>البريد أو الهاتف</label><input type="text" class="form-input" id="loginId" placeholder="example@email.com" dir="ltr"></div>
                    <div class="form-group"><label>كلمة المرور</label><input type="password" class="form-input" id="loginPass" placeholder="••••••••"></div>
                    <button class="btn btn-gold" onclick="doLogin()"><i class="fas fa-sign-in-alt"></i> تسجيل الدخول</button>
                    <button class="btn btn-google" onclick="googleLogin()"><i class="fab fa-google"></i> Google</button>
                    <p style="text-align:center;margin-top:10px;font-size:11px;color:#666;">المدير: 01026966717 | 308191</p>
                </div>

                <div id="registerForm" style="display:none;">
                    <div class="form-group"><label>الاسم</label><input type="text" class="form-input" id="regName"></div>
                    <div class="form-group"><label>البريد</label><input type="email" class="form-input" id="regEmail" dir="ltr"></div>
                    <div class="form-group"><label>الهاتف</label><input type="tel" class="form-input" id="regPhone" dir="ltr"></div>
                    <div class="form-group"><label>كلمة المرور</label><input type="password" class="form-input" id="regPass"></div>
                    <button class="btn btn-gold" onclick="doRegister()">إنشاء حساب</button>
                    <button class="btn btn-outline" onclick="switchTab('login')">⬅ العودة</button>
                </div>
            </div>
        </div>
    </div>

    <!-- ==================== MAIN APP ==================== -->
    <div id="mainApp">
        <!-- Top Bar with 3 dots -->
        <div class="top-bar">
            <div class="dot-menu">
                <span class="dot red" onclick="soundEffect('close')" title="إغلاق"></span>
                <span class="dot orange" onclick="soundEffect('minimize')" title="تصغير"></span>
                <span class="dot green" onclick="soundEffect('maximize')" title="تكبير"></span>
            </div>
            <span>🕐 <span id="liveClock"></span></span>
            <span>📅 <span id="liveDate"></span></span>
        </div>

        <!-- Navbar -->
        <nav class="navbar-evil" id="navbar">
            <a class="brand" onclick="goPage('home')">
                <span style="font-size:30px;">🔥</span> EVIL BAR
            </a>
            <div class="nav-links">
                <button class="nav-link-item active" onclick="goPage('home')">🏠 الرئيسية</button>
                <button class="nav-link-item" onclick="goPage('menu')">📋 المنيو</button>
                <button class="nav-link-item" onclick="goPage('drinks')">🥤 مشروبات</button>
                <button class="nav-link-item" onclick="goPage('alcohol')">🍺 خمور</button>
                <button class="nav-link-item" onclick="goPage('food')">🍰 حلويات</button>
                <button class="nav-link-item" onclick="goPage('reserve')">📅 حجز</button>
                <button class="nav-link-item" id="dashNavBtn" style="display:none;" onclick="goPage('dashboard')">📊 لوحة التحكم</button>
                <button class="nav-cart-btn" onclick="toggleCart()">🛒 <span class="cart-badge" id="cartBadge">0</span></button>
                <button class="nav-link-item" onclick="goPage('profile')">👤 <span id="navUser"></span></button>
                <button class="btn btn-red btn-sm" onclick="doLogout()">🚪</button>
            </div>
        </nav>

        <div id="pageContent"></div>

        <footer>
            <h4 style="color:var(--gold);">🔥 EVIL BAR</h4>
            <p>أفخم كافيه وبار | 2024</p>
        </footer>
    </div>

    <!-- Cart Sidebar -->
    <div class="cart-overlay" id="cartOverlay" onclick="toggleCart()"></div>
    <div class="cart-sidebar" id="cartSidebar">
        <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:15px;">
            <h4 style="color:var(--gold);">🛒 السلة</h4>
            <button onclick="toggleCart()" style="background:none;border:none;color:#fff;font-size:20px;cursor:pointer;">✕</button>
        </div>
        <div id="cartItemsList"></div>
        <hr style="border-color:rgba(255,255,255,0.08);margin:15px 0;">
        <h4>الإجمالي: <span style="color:var(--gold);" id="cartTotal">0</span> ج.م</h4>
        <button class="btn btn-gold" onclick="openPayment()">💳 ادفع الآن</button>
        <button class="btn btn-red" onclick="clearCart()" style="margin-top:5px;">🗑 تفريغ</button>
    </div>

    <!-- Payment Modal -->
    <div class="modal-overlay" id="payModal">
        <div class="modal-dialog">
            <div style="display:flex;justify-content:space-between;margin-bottom:15px;">
                <h4 style="color:var(--gold);">💳 الدفع</h4>
                <button onclick="closePayment()" style="background:none;border:none;color:#fff;font-size:20px;cursor:pointer;">✕</button>
            </div>
            <div class="auth-tabs" style="margin-bottom:15px;">
                <button class="auth-tab active" onclick="switchPay('visa')">💳 فيزا</button>
                <button class="auth-tab" onclick="switchPay('vodafone')">📱 فودافون كاش</button>
            </div>
            <div id="payVisa">
                <div style="background:linear-gradient(135deg,#1a1f71,#2a3f91);border-radius:14px;padding:20px;color:#fff;margin-bottom:15px;">
                    <div style="font-size:28px;font-weight:900;">VISA</div>
                    <div style="font-size:16px;letter-spacing:3px;margin:8px 0;">•••• •••• •••• ••••</div>
                </div>
                <input class="form-input" id="cardName" placeholder="👤 الاسم على البطاقة" style="margin-bottom:10px;">
                <input class="form-input" id="cardNum" placeholder="💳 رقم البطاقة" maxlength="19" oninput="formatCard(this)" dir="ltr" style="margin-bottom:10px;">
                <div style="display:flex;gap:10px;margin-bottom:10px;">
                    <input class="form-input" id="cardExp" placeholder="📅 MM/YY" maxlength="5" dir="ltr" style="flex:1;">
                    <input class="form-input" id="cardCVV" placeholder="🔒 CVV" maxlength="4" dir="ltr" type="password" style="flex:1;">
                </div>
                <div id="visaErrors" style="display:none;background:rgba(231,76,60,0.1);border:1px solid var(--red);border-radius:10px;padding:12px;margin-bottom:12px;color:var(--red);font-size:13px;"></div>
                <p style="color:#888;">💰 المبلغ: <span style="color:var(--gold);font-weight:700;" id="visaAmt"></span></p>
                <button class="btn btn-gold" onclick="validateVisa()">🔍 فحص ودفع</button>
            </div>
            <div id="payVodafone" style="display:none;">
                <div style="background:#e60000;border-radius:14px;padding:20px;text-align:center;color:#fff;margin-bottom:15px;">
                    <h5>📱 فودافون كاش</h5>
                    <div style="font-size:22px;font-weight:900;background:rgba(255,255,255,0.2);padding:12px;border-radius:10px;margin:10px 0;">
                        01026966717
                        <button onclick="copyVodafone()" style="background:#fff;color:#000;border:none;padding:6px 12px;border-radius:6px;cursor:pointer;margin-right:8px;">📋 نسخ</button>
                    </div>
                </div>
                <input class="form-input" id="senderPhone" placeholder="📱 رقم هاتفك (إجباري)" dir="ltr" style="margin-bottom:10px;">
                <input class="form-input" id="senderName" placeholder="👤 اسمك في فودافون كاش" style="margin-bottom:10px;">
                <div style="border:2px dashed rgba(212,175,55,0.4);border-radius:12px;padding:20px;text-align:center;cursor:pointer;margin-bottom:15px;" onclick="document.getElementById('scrFile').click()">
                    📸 سكرين شوت
                    <input type="file" id="scrFile" accept="image/*" style="display:none;" onchange="prevScr(event)">
                    <img id="scrPreview" style="max-width:100%;max-height:150px;display:none;margin-top:10px;border-radius:8px;">
                </div>
                <p style="color:#888;">💰 المبلغ: <span style="color:var(--gold);font-weight:700;" id="vodAmt"></span></p>
                <button class="btn btn-gold" onclick="submitVodafone()">📤 إرسال للمراجعة</button>
            </div>
        </div>
    </div>

    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
    <script>
        // ==================== DATA ====================
        const ADMIN = { name: 'المدير', phone: '01026966717', password: '308191', role: 'super_admin' };

        const PRODUCTS = [
            { id:1, name:'إسبرسو', cat:'hot', price:35, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1510707577719-ae7c14805e3a?w=400&q=80', desc:'إسبرسو إيطالي أصيل غني وقوي' },
            { id:2, name:'كابتشينو', cat:'hot', price:45, disc:38, rating:4.9, img:'https://images.unsplash.com/photo-1534778101976-62847782c213?w=400&q=80', desc:'كابتشينو برغوة حليب كثيفة' },
            { id:3, name:'لاتيه', cat:'hot', price:45, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1461023058943-07fcbe16d735?w=400&q=80', desc:'لاتيه كريمي ناعم' },
            { id:4, name:'موكا', cat:'hot', price:50, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1572442388796-11668a67e53d?w=400&q=80', desc:'موكا غنية بالشوكولاتة' },
            { id:5, name:'قهوة تركي', cat:'hot', price:30, disc:null, rating:4.9, img:'https://images.unsplash.com/photo-1509042239860-f550ce710b93?w=400&q=80', desc:'قهوة تركية تقليدية' },
            { id:6, name:'فلات وايت', cat:'hot', price:45, disc:null, rating:4.5, img:'https://images.unsplash.com/photo-1495474472287-4d71bcdd2085?w=400&q=80', desc:'فلات وايت أسترالي' },
            { id:7, name:'آيس لاتيه', cat:'cold', price:50, disc:null, rating:4.6, img:'https://images.unsplash.com/photo-1517701604599-bb29b565090c?w=400&q=80', desc:'آيس لاتيه منعش' },
            { id:8, name:'آيس موكا', cat:'cold', price:55, disc:48, rating:4.7, img:'https://images.unsplash.com/photo-1461023058943-07fcbe16d735?w=400&q=80', desc:'آيس موكا' },
            { id:9, name:'ليمون نعناع', cat:'cold', price:35, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1621263764928-df1444c5e859?w=400&q=80', desc:'ليمونادة طازجة' },
            { id:10, name:'عصير برتقال', cat:'cold', price:30, disc:null, rating:4.5, img:'https://images.unsplash.com/photo-1621506289937-a8e4df240d0b?w=400&q=80', desc:'عصير طبيعي 100%' },
            { id:11, name:'مانجو', cat:'cold', price:40, disc:null, rating:4.9, img:'https://images.unsplash.com/photo-1546173159-315724a31696?w=400&q=80', desc:'عصير مانجو طازج' },
            { id:12, name:'تشيز كيك', cat:'food', price:60, disc:50, rating:4.9, img:'https://images.unsplash.com/photo-1533134242443-d4fd215305ad?w=400&q=80', desc:'تشيز كيك نيويورك' },
            { id:13, name:'براوني', cat:'food', price:45, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1606313564200-e75d5e30476c?w=400&q=80', desc:'براوني شوكولاتة' },
            { id:14, name:'تيراميسو', cat:'food', price:65, disc:null, rating:4.9, img:'https://images.unsplash.com/photo-1571877227200-a0d98ea607e9?w=400&q=80', desc:'تيراميسو إيطالي' },
            { id:15, name:'كرواسون', cat:'food', price:35, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1555507036-ab1f4038024a?w=400&q=80', desc:'كرواسون فرنسي' },
            { id:16, name:'كيك شوكولاتة', cat:'food', price:70, disc:60, rating:4.9, img:'https://images.unsplash.com/photo-1578985545062-69928b1d9587?w=400&q=80', desc:'كيك شوكولاتة ثلاثي' },
            { id:17, name:'هاينكن', cat:'alcohol', price:70, disc:null, rating:4.6, img:'https://images.unsplash.com/photo-1618885472179-5e474019f2a9?w=400&q=80', desc:'بيرة هاينكن' },
            { id:18, name:'كورونا', cat:'alcohol', price:65, disc:null, rating:4.4, img:'https://images.unsplash.com/photo-1559526324-593bc073d938?w=400&q=80', desc:'بيرة كورونا' },
            { id:19, name:'ويسكي', cat:'alcohol', price:120, disc:100, rating:4.8, img:'https://images.unsplash.com/photo-1527281400683-1aae777175f0?w=400&q=80', desc:'ويسكي 12 سنة' },
            { id:20, name:'فودكا', cat:'alcohol', price:80, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1569529465841-dfecdab7503b?w=400&q=80', desc:'فودكا نقية' },
            { id:21, name:'موهيتو', cat:'alcohol', price:75, disc:null, rating:4.9, img:'https://images.unsplash.com/photo-1551538827-9c037cb4f32a?w=400&q=80', desc:'موهيتو منعش' },
            { id:22, name:'مارتيني', cat:'alcohol', price:85, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1575023782549-62ca0d244b39?w=400&q=80', desc:'مارتيني جاف' },
            { id:23, name:'شامبانيا', cat:'alcohol', price:200, disc:180, rating:4.9, img:'https://images.unsplash.com/photo-1510812431401-41d2bd2722f3?w=400&q=80', desc:'شامبانيا فرنسية' },
            { id:24, name:'مارغريتا', cat:'alcohol', price:80, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1556855810-ac404d3c2eba?w=400&q=80', desc:'مارغريتا كلاسيك' },
        ];

        // BIN Database for card validation
        const BIN_DB = {
            '4': { bank: 'Visa', country: 'عالمي', type: 'ائتمان' },
            '51': { bank: 'Mastercard', country: 'عالمي', type: 'ائتمان' },
            '52': { bank: 'Mastercard', country: 'عالمي', type: 'ائتمان' },
            '53': { bank: 'Mastercard', country: 'عالمي', type: 'ائتمان' },
            '54': { bank: 'Mastercard', country: 'عالمي', type: 'ائتمان' },
            '55': { bank: 'Mastercard', country: 'عالمي', type: 'ائتمان' },
            '34': { bank: 'Amex', country: 'أمريكي', type: 'ائتمان' },
            '37': { bank: 'Amex', country: 'أمريكي', type: 'ائتمان' },
            '6011': { bank: 'Discover', country: 'أمريكي', type: 'ائتمان' },
            '65': { bank: 'Discover', country: 'أمريكي', type: 'ائتمان' },
            '45': { bank: 'البنك الأهلي', country: 'مصر', type: 'خصم مباشر' },
            '49': { bank: 'بنك مصر', country: 'مصر', type: 'ائتمان' },
            '42': { bank: 'CIB', country: 'مصر', type: 'ائتمان' },
            '40': { bank: 'QNB', country: 'مصر', type: 'ائتمان' },
            '47': { bank: 'HSBC', country: 'مصر', type: 'ائتمان' },
        };

        // ==================== STATE ====================
        let cart = JSON.parse(localStorage.getItem('evilCart') || '[]');
        let currentUser = JSON.parse(localStorage.getItem('evilUser') || 'null');
        let scrFile = null;

        // ==================== SOUND EFFECTS ====================
        function soundEffect(type) {
            const AudioContext = window.AudioContext || window.webkitAudioContext;
            if (!AudioContext) return;
            const ctx = new AudioContext();
            const osc = ctx.createOscillator();
            const gain = ctx.createGain();
            osc.connect(gain); gain.connect(ctx.destination);
            
            switch(type) {
                case 'click': osc.frequency.value = 800; gain.gain.value = 0.1; osc.start(); osc.stop(ctx.currentTime + 0.05); break;
                case 'success': osc.frequency.value = 1200; gain.gain.value = 0.1; osc.start(); osc.stop(ctx.currentTime + 0.1); setTimeout(() => { const o2 = ctx.createOscillator(); o2.connect(gain); o2.frequency.value = 1600; o2.start(); o2.stop(ctx.currentTime + 0.1); }, 100); break;
                case 'error': osc.frequency.value = 200; gain.gain.value = 0.15; osc.start(); osc.stop(ctx.currentTime + 0.3); break;
                case 'add': osc.frequency.value = 600; gain.gain.value = 0.08; osc.start(); osc.stop(ctx.currentTime + 0.08); break;
                case 'close': osc.frequency.value = 300; gain.gain.value = 0.1; osc.start(); osc.stop(ctx.currentTime + 0.15); break;
                case 'minimize': osc.frequency.value = 500; gain.gain.value = 0.05; osc.start(); osc.stop(ctx.currentTime + 0.05); break;
                case 'maximize': osc.frequency.value = 1000; gain.gain.value = 0.08; osc.start(); osc.stop(ctx.currentTime + 0.1); break;
            }
        }

        // ==================== PARTICLES ====================
        function initParticles() {
            const canvas = document.getElementById('particlesCanvas');
            const ctx = canvas.getContext('2d');
            canvas.width = window.innerWidth; canvas.height = window.innerHeight;
            const particles = [];
            for (let i = 0; i < 50; i++) {
                particles.push({
                    x: Math.random() * canvas.width, y: Math.random() * canvas.height,
                    size: Math.random() * 2 + 0.5, sx: (Math.random() - 0.5) * 0.4,
                    sy: (Math.random() - 0.5) * 0.4, o: Math.random() * 0.4 + 0.1
                });
            }
            function animate() {
                ctx.clearRect(0, 0, canvas.width, canvas.height);
                particles.forEach(p => {
                    p.x += p.sx; p.y += p.sy;
                    if (p.x < 0) p.x = canvas.width; if (p.x > canvas.width) p.x = 0;
                    if (p.y < 0) p.y = canvas.height; if (p.y > canvas.height) p.y = 0;
                    ctx.beginPath(); ctx.arc(p.x, p.y, p.size, 0, Math.PI * 2);
                    ctx.fillStyle = `rgba(212,175,55,${p.o})`; ctx.fill();
                });
                requestAnimationFrame(animate);
            }
            animate();
        }

        // ==================== LIVE CLOCK ====================
        function updateClock() {
            const now = new Date();
            document.getElementById('liveClock').textContent = now.toLocaleTimeString('ar-EG');
            document.getElementById('liveDate').textContent = now.toLocaleDateString('ar-EG', { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' });
        }

        // ==================== INIT ====================
        window.onload = function() {
            let users = JSON.parse(localStorage.getItem('evilUsers') || '[]');
            if (!users.find(u => u.phone === ADMIN.phone)) {
                users.push(ADMIN);
                localStorage.setItem('evilUsers', JSON.stringify(users));
            }

            initParticles();
            updateClock();
            setInterval(updateClock, 1000);

            setTimeout(() => {
                document.getElementById('preloader').classList.add('hidden');
            }, 1800);

            document.getElementById('authPage').style.display = 'flex';
            document.getElementById('mainApp').style.display = 'none';
            AOS.init({ duration: 700, once: false });
        };

        // ==================== AUTH ====================
        function switchTab(tab) {
            document.querySelectorAll('.auth-tab').forEach(t => t.classList.remove('active'));
            if (tab === 'login') {
                document.querySelector('.auth-tab:first-child').classList.add('active');
                document.getElementById('loginForm').style.display = 'block';
                document.getElementById('registerForm').style.display = 'none';
            } else {
                document.querySelector('.auth-tab:last-child').classList.add('active');
                document.getElementById('loginForm').style.display = 'none';
                document.getElementById('registerForm').style.display = 'block';
            }
            soundEffect('click');
        }

        function doLogin() {
            const id = document.getElementById('loginId').value.trim();
            const pass = document.getElementById('loginPass').value.trim();
            if (!id || !pass) { soundEffect('error'); return toastMsg('املأ الحقول', 'error'); }

            const users = JSON.parse(localStorage.getItem('evilUsers') || '[]');
            const found = users.find(u => (u.phone === id || u.email === id) && u.password === pass);
            if (found) { loginSuccess(found); soundEffect('success'); }
            else { toastMsg('بيانات خاطئة', 'error'); soundEffect('error'); }
        }

        function doRegister() {
            const name = document.getElementById('regName').value.trim();
            const email = document.getElementById('regEmail').value.trim();
            const phone = document.getElementById('regPhone').value.trim();
            const pass = document.getElementById('regPass').value.trim();
            if (!name || !email || !pass) { soundEffect('error'); return toastMsg('املأ الحقول', 'error'); }
            if (pass.length < 8) { soundEffect('error'); return toastMsg('كلمة مرور 8 أحرف', 'error'); }

            let users = JSON.parse(localStorage.getItem('evilUsers') || '[]');
            if (users.find(u => u.email === email)) return toastMsg('البريد مستخدم', 'error');
            const user = { name, email, phone, password: pass, role: 'user' };
            users.push(user); localStorage.setItem('evilUsers', JSON.stringify(users));
            loginSuccess(user); soundEffect('success');
        }

        function googleLogin() {
            const email = prompt('أدخل بريد Google:');
            if (email && email.includes('@')) {
                let users = JSON.parse(localStorage.getItem('evilUsers') || '[]');
                let u = users.find(x => x.email === email);
                if (!u) { u = { name: email.split('@')[0], email, phone: '', password: '', role: 'user', google: true }; users.push(u); localStorage.setItem('evilUsers', JSON.stringify(users)); }
                loginSuccess(u); soundEffect('success');
            }
        }

        function loginSuccess(user) {
            currentUser = user; localStorage.setItem('evilUser', JSON.stringify(user));
            document.getElementById('authPage').style.display = 'none';
            document.getElementById('mainApp').classList.add('show');
            document.getElementById('mainApp').style.display = 'block';
            document.getElementById('navUser').textContent = user.name;
            if (user.role === 'super_admin') document.getElementById('dashNavBtn').style.display = 'inline';
            updateCartUI(); goPage('home');
            toastMsg('👋 ' + user.name);
        }

        function doLogout() {
            currentUser = null; localStorage.removeItem('evilUser');
            document.getElementById('mainApp').classList.remove('show');
            document.getElementById('mainApp').style.display = 'none';
            document.getElementById('authPage').style.display = 'flex';
            switchTab('login'); soundEffect('close'); toastMsg('تم الخروج');
        }

        // ==================== PAGES ====================
        function goPage(page) {
            soundEffect('click');
            const c = document.getElementById('pageContent');
            switch (page) {
                case 'home': c.innerHTML = homePage(); break;
                case 'menu': c.innerHTML = productsPage(PRODUCTS, '📋 المنيو الكامل'); break;
                case 'drinks': c.innerHTML = productsPage(PRODUCTS.filter(p => ['hot','cold'].includes(p.cat)), '🥤 المشروبات'); break;
                case 'alcohol': c.innerHTML = productsPage(PRODUCTS.filter(p => p.cat === 'alcohol'), '🍺 المشروبات الكحولية'); break;
                case 'food': c.innerHTML = productsPage(PRODUCTS.filter(p => p.cat === 'food'), '🍰 الحلويات والمخبوزات'); break;
                case 'reserve': c.innerHTML = reservePage(); break;
                case 'profile': c.innerHTML = profilePage(); break;
                case 'dashboard': c.innerHTML = (currentUser && currentUser.role === 'super_admin') ? dashboardPage() : '<p style="text-align:center;padding:100px;">⛔ غير مصرح</p>'; break;
            }
            document.querySelectorAll('.nav-link-item').forEach(l => l.classList.remove('active'));
            window.scrollTo(0, 0); AOS.refresh();
        }

        function homePage() {
            const f = PRODUCTS.filter(p => [1,3,7,9,12,14,17,19,21,23].includes(p.id));
            return `
                <div class="hero"><div><h1>EVIL BAR</h1><p>✦ أفخم تجربة قهوة وبار في المدينة ✦</p>
                <div class="hero-btns"><button class="hero-btn hero-btn-primary" onclick="goPage('menu')">📋 تصفح المنيو</button>
                <button class="hero-btn hero-btn-outline" onclick="goPage('reserve')">📅 احجز طاولة</button></div></div></div>
                <div class="section"><h2 class="section-title"><span class="gold-text">منتجاتنا</span> المميزة</h2>
                <div class="products-grid">${f.map(p => productCard(p)).join('')}</div></div>
            `;
        }

        function productsPage(items, title) {
            return `<div class="section"><h2 class="section-title"><span class="gold-text">${title}</span></h2><div class="products-grid">${items.map(p => productCard(p)).join('')}</div></div>`;
        }

        function productCard(p) {
            const pr = p.disc || p.price;
            return `
                <div class="product-card" data-aos="fade-up">
                    <div class="product-img"><img src="${p.img}" alt="${p.name}" onerror="this.src='https://via.placeholder.com/400x200/111/d4af37?text=${p.name}'">${p.disc?`<span class="badge-discount">-${Math.round((1-p.disc/p.price)*100)}%</span>`:''}</div>
                    <div class="product-body"><h5>${p.name}</h5><p class="desc">${p.desc}</p>
                    <div class="price-row">${p.disc?`<span class="price-old">${p.price}ج.م</span>`:''}<span class="price-current">${pr} ج.م</span></div>
                    <div class="stars">${'★'.repeat(Math.floor(p.rating))} ${p.rating}</div>
                    <button class="btn-add-cart" onclick="addToCart(${p.id});soundEffect('add')">🛒 أضف للسلة</button></div></div>`;
        }

        function reservePage() {
            return `<div class="section"><div style="max-width:500px;margin:0 auto;background:rgba(18,18,18,0.9);border:1px solid var(--border-gold);border-radius:20px;padding:30px;">
                <h3 style="color:var(--gold);text-align:center;">🍽 حجز طاولة</h3>
                <div class="form-group"><label>عدد الأشخاص</label><select class="form-input">${[1,2,3,4,5,6,7,8].map(n=>`<option>${n}</option>`).join('')}</select></div>
                <div class="form-group"><label>التاريخ</label><input type="date" class="form-input"></div>
                <div class="form-group"><label>الوقت</label><input type="time" class="form-input"></div>
                <button class="btn btn-gold" onclick="soundEffect('success');toastMsg('✅ تم الحجز')">تأكيد</button></div></div>`;
        }

        function profilePage() {
            return `<div class="section"><div style="max-width:500px;margin:0 auto;background:rgba(18,18,18,0.9);border:1px solid var(--border-gold);border-radius:20px;padding:30px;">
                <h3 style="color:var(--gold);">👤 ${currentUser.name}</h3><p>📧 ${currentUser.email||'-'}</p><p>📱 ${currentUser.phone||'-'}</p></div></div>`;
        }

        function dashboardPage() {
            const users = JSON.parse(localStorage.getItem('evilUsers') || '[]');
            const payments = JSON.parse(localStorage.getItem('evilPayments') || '[]');
            const pending = payments.filter(p => p.status === 'قيد المراجعة');
            const rev = payments.filter(p => p.status === 'مكتمل').reduce((s,p) => s+p.amount, 0);
            return `<div class="section"><h2 class="section-title">📊 <span class="gold-text">لوحة التحكم</span></h2>
                <p style="text-align:center;color:var(--gold);">👑 ${currentUser.name} - المدير الرئيسي</p>
                <div class="dash-stats" style="max-width:1000px;margin:0 auto 20px;">
                    <div class="dash-stat"><h2>${users.length}</h2><p>👥 مستخدمين</p></div>
                    <div class="dash-stat"><h2>${payments.length}</h2><p>💳 مدفوعات</p></div>
                    <div class="dash-stat"><h2>${rev} ج.م</h2><p>💰 إيرادات</p></div>
                    <div class="dash-stat" style="border-color:var(--orange);"><h2 style="color:var(--orange);">${pending.length}</h2><p>⏳ مراجعة</p></div>
                </div>
                ${pending.length>0?`<div style="max-width:1000px;margin:20px auto;background:rgba(243,156,18,0.1);border:1px solid var(--orange);border-radius:15px;padding:20px;">
                    <h4 style="color:var(--orange);">⏳ طلبات للمراجعة</h4>
                    ${pending.map(p=>`<div style="background:#111;padding:12px;border-radius:10px;margin:8px 0;display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:8px;">
                        <div><strong>${p.userName}</strong> | ${p.amount}ج.م<br><small>من: ${p.senderPhone||'?'} | ${p.cardInfo||''} | ${p.date}</small></div>
                        <div><button class="btn btn-green btn-sm" onclick="approvePay(${p.id})">✅ قبول</button>
                        <button class="btn btn-red btn-sm" onclick="rejectPay(${p.id})">❌ رفض</button></div></div>`).join('')}</div>`:''}
                <h4 style="color:var(--gold);margin:20px 0;">💳 سجل المدفوعات</h4>
                <div style="overflow-x:auto;max-width:1000px;margin:0 auto;"><table class="table-dark"><tr><th>#</th><th>عميل</th><th>طريقة</th><th>مبلغ</th><th>معلومات</th><th>حالة</th><th>تاريخ</th></tr>
                ${payments.length===0?'<tr><td colspan="7">لا يوجد</td></tr>':payments.reverse().slice(0,20).map(p=>`<tr><td>${p.id}</td><td>${p.userName}</td><td>${p.method}</td><td style="color:var(--gold);">${p.amount}ج.م</td><td>${p.cardInfo||p.senderPhone||'-'}</td><td><span class="status-${p.status==='مكتمل'?'approved':p.status==='مرفوض'?'rejected':'pending'}">${p.status}</span></td><td>${p.date}</td></tr>`).join('')}</table></div></div>`;
        }

        function approvePay(id) { let p=JSON.parse(localStorage.getItem('evilPayments')||'[]'); const i=p.findIndex(x=>x.id===id); if(i>-1){p[i].status='مكتمل';localStorage.setItem('evilPayments',JSON.stringify(p));goPage('dashboard');soundEffect('success');toastMsg('✅ تم القبول');} }
        function rejectPay(id) { let p=JSON.parse(localStorage.getItem('evilPayments')||'[]'); const i=p.findIndex(x=>x.id===id); if(i>-1){p[i].status='مرفوض';localStorage.setItem('evilPayments',JSON.stringify(p));goPage('dashboard');soundEffect('error');toastMsg('❌ تم الرفض');} }

        // ==================== CART ====================
        function addToCart(id) { const p=PRODUCTS.find(x=>x.id===id); if(!p)return; const ex=cart.find(i=>i.productId===id); if(ex)ex.qty++; else cart.push({productId:id,qty:1,price:p.disc||p.price,name:p.name,img:p.img}); saveCart(); toastMsg('✅ '+p.name); }
        function removeCart(i){cart.splice(i,1);saveCart();}
        function qtyCart(i,d){cart[i].qty+=d;if(cart[i].qty<=0)cart.splice(i,1);saveCart();}
        function clearCart(){cart=[];saveCart();toastMsg('🗑 تم');}
