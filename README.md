<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Evil Bar - إيفل بار</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.rtl.min.css" rel="stylesheet">
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" rel="stylesheet">
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">
    <style>
        :root {
            --bg: #04000d; --bg2: #0a001a; --bg3: #120026;
            --purple: #8B5CF6; --purple2: #A78BFA; --purple3: #C4B5FD;
            --purple-dark: #6D28D9; --white: #fff; --gray: #999; --gray2: #666;
            --red: #ef4444; --green: #10b981; --orange: #f59e0b;
            --glass: rgba(18,10,40,0.85); --border-purple: rgba(139,92,246,0.25);
            --shadow-purple: 0 0 30px rgba(139,92,246,0.3);
            --shadow-purple2: 0 0 60px rgba(139,92,246,0.5);
            --radius: 16px; --transition: all 0.3s cubic-bezier(0.4,0,0.2,1);
        }
        * { margin:0; padding:0; box-sizing:border-box; }
        body { background:var(--bg); color:var(--white); font-family:'Segoe UI',Tahoma,sans-serif; min-height:100vh; overflow-x:hidden; }
        ::-webkit-scrollbar { width:6px; } ::-webkit-scrollbar-track { background:var(--bg); } ::-webkit-scrollbar-thumb { background:var(--purple); border-radius:10px; }

        /* Particles */
        #particlesCanvas { position:fixed; top:0; left:0; width:100%; height:100%; z-index:0; pointer-events:none; }

        /* Preloader - fast */
        #preloader { position:fixed; top:0; left:0; width:100%; height:100%; background:#030010; z-index:99999; display:flex; align-items:center; justify-content:center; flex-direction:column; transition:opacity 0.3s,visibility 0.3s; }
        #preloader.hidden { opacity:0; visibility:hidden; }
        .preloader-ring { width:60px; height:60px; border:3px solid transparent; border-top-color:var(--purple); border-radius:50%; animation:spin 0.8s linear infinite; }
        @keyframes spin { to{transform:rotate(360deg)} }
        .preloader-text { color:var(--purple2); font-size:24px; font-weight:900; margin-top:12px; letter-spacing:5px; }

        /* Auth */
        #authPage { display:flex; min-height:100vh; align-items:center; justify-content:center; padding:20px; position:relative; z-index:1; }
        .auth-card { background:var(--glass); backdrop-filter:blur(30px); border:1px solid var(--border-purple); border-radius:24px; padding:30px 24px; width:100%; max-width:420px; box-shadow:var(--shadow-purple2); animation:slideUp 0.5s ease; }
        @keyframes slideUp { from{opacity:0;transform:translateY(25px)scale(0.96)} to{opacity:1;transform:translateY(0)scale(1)} }
        .auth-logo { text-align:center; margin-bottom:20px; }
        .auth-logo .icon { font-size:45px; animation:float 3s ease-in-out infinite; }
        @keyframes float { 0%,100%{transform:translateY(0)} 50%{transform:translateY(-8px)} }
        .auth-logo h1 { font-size:34px; font-weight:900; background:linear-gradient(135deg,var(--purple-dark),var(--purple2),var(--purple3)); background-size:300% 300%; -webkit-background-clip:text; -webkit-text-fill-color:transparent; animation:shimmer 3s infinite; letter-spacing:4px; }
        @keyframes shimmer { 0%,100%{background-position:0% 50%} 50%{background-position:100% 50%} }

        .auth-tabs { display:flex; gap:5px; background:rgba(255,255,255,0.02); border-radius:12px; padding:4px; margin-bottom:18px; }
        .auth-tab { flex:1; padding:10px; text-align:center; border:none; background:transparent; color:var(--gray); border-radius:10px; cursor:pointer; font-size:13px; font-weight:600; transition:var(--transition); }
        .auth-tab.active { background:linear-gradient(135deg,var(--purple-dark),var(--purple)); color:#fff; font-weight:700; box-shadow:var(--shadow-purple); }

        .inp { width:100%; padding:13px 15px; margin-bottom:10px; background:rgba(255,255,255,0.03); border:1.5px solid rgba(255,255,255,0.08); border-radius:12px; color:var(--white); font-size:15px; transition:var(--transition); }
        .inp:focus { outline:none; border-color:var(--purple); box-shadow:0 0 0 3px rgba(139,92,246,0.1); }
        .inp::placeholder { color:rgba(255,255,255,0.2); }
        .inp.error { border-color:var(--red); animation:shake 0.5s; }
        @keyframes shake { 0%,100%{transform:translateX(0)} 25%{transform:translateX(-5px)} 75%{transform:translateX(5px)} }

        .btn { width:100%; padding:13px; border:none; border-radius:12px; font-size:15px; font-weight:700; cursor:pointer; transition:var(--transition); display:flex; align-items:center; justify-content:center; gap:8px; margin-bottom:7px; }
        .btn-purple { background:linear-gradient(135deg,var(--purple-dark),var(--purple),var(--purple2)); color:#fff; position:relative; overflow:hidden; }
        .btn-purple::after { content:''; position:absolute; top:-50%; left:-50%; width:200%; height:200%; background:linear-gradient(45deg,transparent 40%,rgba(255,255,255,0.2) 50%,transparent 60%); animation:btnShine 3s infinite; }
        @keyframes btnShine { 0%{transform:translateX(-100%)rotate(45deg)} 100%{transform:translateX(100%)rotate(45deg)} }
        .btn-purple:hover { transform:translateY(-2px); box-shadow:0 8px 25px rgba(139,92,246,0.5); }
        .btn-outline { background:transparent; border:2px solid var(--border-purple); color:var(--purple2); }
        .btn-red { background:var(--red); color:#fff; }
        .btn-green { background:var(--green); color:#fff; }
        .btn-sm { width:auto; padding:7px 14px; font-size:12px; }

        .divider { display:flex; align-items:center; gap:12px; margin:15px 0; color:var(--gray2); font-size:11px; }
        .divider::before,.divider::after { content:''; flex:1; height:1px; background:rgba(255,255,255,0.08); }
        .link { color:var(--purple2); cursor:pointer; font-weight:600; }

        /* OTP */
        .otp-box { display:none; animation:fadeIn 0.3s; }
        .otp-box.show { display:block; }
        @keyframes fadeIn { from{opacity:0;transform:translateY(-10px)} to{opacity:1;transform:translateY(0)} }
        .otp-inputs { display:flex; gap:7px; justify-content:center; margin:15px 0; }
        .otp-inputs input { width:45px; height:50px; text-align:center; font-size:20px; font-weight:700; background:rgba(255,255,255,0.03); border:2px solid rgba(255,255,255,0.1); border-radius:10px; color:var(--purple2); transition:var(--transition); }
        .otp-inputs input:focus { outline:none; border-color:var(--purple); box-shadow:0 0 10px rgba(139,92,246,0.2); }
        .timer { text-align:center; color:var(--purple2); font-weight:700; margin:8px 0; font-size:15px; }
        .timer.expired { color:var(--red); }

        /* Main App */
        #mainApp { display:none; position:relative; z-index:1; }
        #mainApp.show { display:block; }

        /* Top Bar with 3 dots */
        .top-bar { background:#030010; border-bottom:1px solid rgba(139,92,246,0.1); padding:6px 15px; display:flex; align-items:center; justify-content:space-between; font-size:12px; color:var(--gray); }
        .dots { display:flex; gap:5px; }
        .dot { width:7px; height:7px; border-radius:50%; cursor:pointer; transition:0.2s; }
        .dot:hover { transform:scale(1.4); }
        .dot.red { background:var(--red); }
        .dot.orange { background:var(--orange); }
        .dot.green { background:var(--green); }

        /* 3 Dots Menu */
        .three-dots-menu { position:relative; display:inline-block; }
        .three-dots-btn { background:none; border:none; color:var(--purple2); font-size:20px; cursor:pointer; padding:5px 10px; border-radius:8px; transition:var(--transition); }
        .three-dots-btn:hover { background:rgba(139,92,246,0.1); }
        .dropdown-menu-custom { display:none; position:absolute; top:40px; right:0; background:rgba(18,10,40,0.98); border:1px solid var(--border-purple); border-radius:14px; padding:8px; z-index:200; min-width:200px; box-shadow:var(--shadow-purple2); backdrop-filter:blur(20px); }
        .dropdown-menu-custom.show { display:block; animation:fadeIn 0.2s; }
        .dropdown-menu-custom a { display:block; padding:10px 15px; color:var(--white); text-decoration:none; border-radius:8px; font-size:13px; cursor:pointer; transition:var(--transition); }
        .dropdown-menu-custom a:hover { background:rgba(139,92,246,0.15); color:var(--purple2); }

        /* Navbar */
        .navbar-ev { background:rgba(4,0,13,0.9); backdrop-filter:blur(25px); border-bottom:1px solid rgba(139,92,246,0.1); padding:10px 15px; position:sticky; top:0; z-index:100; display:flex; align-items:center; justify-content:space-between; flex-wrap:wrap; gap:8px; }
        .brand { display:flex; align-items:center; gap:8px; color:var(--purple2); font-size:22px; font-weight:900; text-decoration:none; letter-spacing:2px; cursor:pointer; }
        .brand-icon { font-size:28px; animation:float 3s ease-in-out infinite; }
        .nav-actions { display:flex; align-items:center; gap:6px; }
        .cart-btn { position:relative; background:rgba(139,92,246,0.1); border:1px solid var(--border-purple); color:var(--purple2); padding:7px 13px; border-radius:50px; cursor:pointer; font-weight:600; font-size:13px; transition:var(--transition); }
        .cart-btn:hover { background:var(--purple); color:#fff; }
        .cart-badge { position:absolute; top:-6px; right:-6px; background:var(--purple); color:#fff; border-radius:50%; width:18px; height:18px; font-size:10px; display:flex; align-items:center; justify-content:center; font-weight:900; }

        /* Hero */
        .hero { min-height:80vh; display:flex; align-items:center; justify-content:center; text-align:center; position:relative; }
        .hero h1 { font-size:clamp(40px,8vw,80px); font-weight:900; background:linear-gradient(135deg,var(--purple-dark),var(--purple2),var(--purple3)); background-size:300% 300%; -webkit-background-clip:text; -webkit-text-fill-color:transparent; animation:shimmer 4s infinite; letter-spacing:8px; }
        .hero p { font-size:16px; color:var(--gray); margin:12px 0 20px; }
        .hero-btns { display:flex; gap:10px; justify-content:center; flex-wrap:wrap; }
        .hero-btn { padding:14px 30px; border-radius:50px; font-size:15px; font-weight:700; cursor:pointer; transition:var(--transition); text-decoration:none; display:inline-flex; align-items:center; gap:7px; }
        .hero-btn-primary { background:linear-gradient(135deg,var(--purple-dark),var(--purple)); color:#fff; border:none; }
        .hero-btn-primary:hover { transform:translateY(-4px); box-shadow:0 12px 30px rgba(139,92,246,0.5); }
        .hero-btn-outline { background:transparent; border:2px solid var(--purple); color:var(--purple2); }
        .hero-btn-outline:hover { background:var(--purple); color:#fff; transform:translateY(-4px); }

        /* Sections */
        .section { padding:50px 15px; }
        .section-title { text-align:center; font-size:28px; font-weight:900; margin-bottom:30px; }
        .section-title .hl { color:var(--purple2); }
        .section-title::after { content:''; display:block; width:50px; height:3px; background:linear-gradient(90deg,transparent,var(--purple),transparent); margin:10px auto 0; }

        /* Products - loaded instantly */
        .products-grid { display:grid; grid-template-columns:repeat(auto-fill,minmax(220px,1fr)); gap:16px; max-width:1100px; margin:0 auto; }
        .product-card { background:rgba(15,8,35,0.9); border:1px solid rgba(255,255,255,0.05); border-radius:16px; overflow:hidden; transition:var(--transition); }
        .product-card:hover { transform:translateY(-6px); border-color:var(--border-purple); box-shadow:0 15px 35px rgba(0,0,0,0.4),var(--shadow-purple); }
        .product-img { height:180px; overflow:hidden; position:relative; }
        .product-img img { width:100%; height:100%; object-fit:cover; transition:0.5s; }
        .product-card:hover .product-img img { transform:scale(1.08); }
        .badge-disc { position:absolute; top:8px; left:8px; background:var(--red); color:#fff; padding:2px 8px; border-radius:15px; font-size:10px; font-weight:700; }
        .product-body { padding:14px; }
        .product-body h5 { font-size:15px; margin-bottom:3px; }
        .product-body .desc { color:var(--gray); font-size:11px; margin-bottom:6px; }
        .price-row { display:flex; align-items:center; gap:6px; margin-bottom:5px; }
        .price-old { text-decoration:line-through; color:var(--gray2); font-size:12px; }
        .price-current { color:var(--purple2); font-size:18px; font-weight:900; }
        .stars { color:var(--orange); font-size:11px; margin-bottom:8px; }
        .btn-add { width:100%; padding:9px; background:linear-gradient(135deg,var(--purple-dark),var(--purple)); color:#fff; border:none; border-radius:10px; font-weight:700; cursor:pointer; font-size:13px; transition:var(--transition); }
        .btn-add:hover { box-shadow:0 5px 15px rgba(139,92,246,0.4); }

        /* Cart */
        .cart-overlay { position:fixed; top:0; left:0; width:100%; height:100%; background:rgba(0,0,0,0.8); z-index:2000; display:none; backdrop-filter:blur(5px); }
        .cart-overlay.open { display:block; }
        .cart-sidebar { position:fixed; top:0; right:-400px; width:380px; height:100%; background:var(--bg3); z-index:2001; transition:right 0.35s; border-left:1px solid var(--border-purple); padding:20px; overflow-y:auto; }
        .cart-sidebar.open { right:0; }

        /* Modal */
        .modal-overlay { position:fixed; top:0; left:0; width:100%; height:100%; background:rgba(0,0,0,0.9); z-index:3000; display:none; align-items:center; justify-content:center; backdrop-filter:blur(8px); }
        .modal-overlay.open { display:flex; }
        .modal-dialog { background:var(--bg3); border:2px solid var(--border-purple); border-radius:20px; padding:24px; width:90%; max-width:480px; max-height:85vh; overflow-y:auto; animation:modalIn 0.35s; }
        @keyframes modalIn { from{opacity:0;transform:scale(0.92)translateY(15px)} to{opacity:1;transform:scale(1)translateY(0)} }

        /* Dashboard */
        .stat-grid { display:grid; grid-template-columns:repeat(auto-fill,minmax(180px,1fr)); gap:12px; margin-bottom:20px; }
        .stat-box { background:rgba(15,8,35,0.9); border:1px solid rgba(255,255,255,0.05); border-radius:14px; padding:18px; text-align:center; transition:var(--transition); }
        .stat-box:hover { border-color:var(--border-purple); transform:translateY(-3px); }
        .stat-box h2 { font-size:30px; font-weight:900; color:var(--purple2); }

        table { width:100%; border-collapse:collapse; font-size:12px; }
        th { background:rgba(139,92,246,0.1); color:var(--purple2); padding:10px; text-align:right; font-weight:700; }
        td { padding:8px 10px; border-bottom:1px solid rgba(255,255,255,0.03); }
        .status-p { background:var(--orange); color:#000; padding:2px 8px; border-radius:15px; font-size:10px; font-weight:700; }
        .status-a { background:var(--green); color:#fff; padding:2px 8px; border-radius:15px; font-size:10px; font-weight:700; }
        .status-r { background:var(--red); color:#fff; padding:2px 8px; border-radius:15px; font-size:10px; font-weight:700; }

        /* Toast */
        .toast-ct { position:fixed; bottom:20px; right:20px; z-index:9999; display:flex; flex-direction:column; gap:8px; }
        .toast-item { background:var(--bg3); border:1px solid var(--border-purple); padding:14px 18px; border-radius:12px; color:#fff; font-weight:600; font-size:13px; animation:toastIn 0.35s; box-shadow:0 8px 25px rgba(0,0,0,0.5); display:flex; align-items:center; gap:8px; min-width:250px; }
        .toast-item.ok { border-right:3px solid var(--green); }
        .toast-item.err { border-right:3px solid var(--red); }
        @keyframes toastIn { from{opacity:0;transform:translateX(70px)} to{opacity:1;transform:translateX(0)} }

        footer { background:var(--bg2); border-top:1px solid rgba(139,92,246,0.08); padding:25px; text-align:center; color:var(--gray); font-size:13px; }

        @media(max-width:768px) {
            .hero h1 { font-size:34px; }
            .cart-sidebar { width:100%; right:-100%; }
            .products-grid { grid-template-columns:repeat(auto-fill,minmax(150px,1fr)); gap:10px; }
            .product-img { height:140px; }
        }
    </style>
</head>
<body>

    <canvas id="particlesCanvas"></canvas>
    <div id="preloader"><div class="preloader-ring"></div><div class="preloader-text">EVIL BAR</div></div>
    <div class="toast-ct" id="toastContainer"></div>

    <!-- AUTH PAGE -->
    <div id="authPage">
        <div class="auth-card">
            <div class="auth-logo"><div class="icon">🔥</div><h1>EVIL BAR</h1><p class="auth-subtitle">أفخم كافيه وبار</p></div>
            <div class="auth-tabs">
                <button class="auth-tab active" onclick="switchTab('login')">🔑 دخول</button>
                <button class="auth-tab" onclick="switchTab('register')">📱 برقم الهاتف</button>
            </div>
            <div id="loginForm">
                <input type="text" class="inp" id="loginId" placeholder="📱 الهاتف أو 📧 البريد" dir="ltr">
                <input type="password" class="inp" id="loginPass" placeholder="🔒 كلمة المرور">
                <button class="btn btn-purple" onclick="doLogin()">🚀 دخول</button>
                <button class="btn btn-outline" onclick="googleLogin()"><i class="fab fa-google"></i> Google</button>
                <p style="text-align:center;font-size:10px;color:var(--gray2);margin-top:8px;">المدير: 01026966717 | 308191</p>
            </div>
            <div id="registerForm" style="display:none;">
                <input type="text" class="inp" id="regName" placeholder="👤 الاسم">
                <input type="tel" class="inp" id="regPhone" placeholder="📱 رقم الهاتف" dir="ltr">
                <small style="color:var(--gray);font-size:10px;">سيصلك رمز تحقق عبر الواتساب</small>
                <input type="password" class="inp" id="regPass" placeholder="🔒 كلمة المرور" style="margin-top:8px;">
                <button class="btn btn-purple" onclick="sendWhatsAppOTP()">📲 إرسال رمز التحقق</button>
                <div class="otp-box" id="otpBox">
                    <p style="text-align:center;color:var(--gray);font-size:12px;margin-top:10px;">أدخل الرمز المكون من 6 أرقام</p>
                    <div class="otp-inputs">
                        <input type="text" maxlength="1" oninput="nextOtp(this)" id="o1">
                        <input type="text" maxlength="1" oninput="nextOtp(this)" id="o2">
                        <input type="text" maxlength="1" oninput="nextOtp(this)" id="o3">
                        <input type="text" maxlength="1" oninput="nextOtp(this)" id="o4">
                        <input type="text" maxlength="1" oninput="nextOtp(this)" id="o5">
                        <input type="text" maxlength="1" oninput="nextOtp(this)" id="o6">
                    </div>
                    <div class="timer" id="otpTimer">02:00</div>
                    <button class="btn btn-purple" onclick="verifyOTPAndRegister()">✅ تأكيد</button>
                    <button class="btn btn-outline" id="btnResendOtp" onclick="sendWhatsAppOTP()" disabled>🔄 إعادة</button>
                </div>
                <button class="btn btn-outline" style="margin-top:5px;" onclick="switchTab('login')">⬅ العودة</button>
            </div>
        </div>
    </div>

    <!-- MAIN APP -->
    <div id="mainApp">
        <!-- Top Bar -->
        <div class="top-bar">
            <div class="dots"><span class="dot red" onclick="sfx('close')"></span><span class="dot orange" onclick="sfx('min')"></span><span class="dot green" onclick="sfx('max')"></span></div>
            <span>🕐 <span id="liveTime"></span></span>
            <!-- 3 Dots Menu -->
            <div class="three-dots-menu">
                <button class="three-dots-btn" onclick="toggleDotsMenu()">⋮</button>
                <div class="dropdown-menu-custom" id="dotsDropdown">
                    <a onclick="goPage('home');toggleDotsMenu()">🏠 الرئيسية</a>
                    <a onclick="goPage('menu');toggleDotsMenu()">📋 المنيو</a>
                    <a onclick="goPage('drinks');toggleDotsMenu()">🥤 مشروبات</a>
                    <a onclick="goPage('alcohol');toggleDotsMenu()">🍺 خمور</a>
                    <a onclick="goPage('food');toggleDotsMenu()">🍰 حلويات</a>
                    <a onclick="goPage('reserve');toggleDotsMenu()">📅 حجز</a>
                    <a onclick="goPage('dashboard');toggleDotsMenu()" id="dashLink" style="display:none;">📊 لوحة التحكم</a>
                    <a onclick="goPage('profile');toggleDotsMenu()">👤 حسابي</a>
                    <a onclick="doLogout();toggleDotsMenu()" style="color:var(--red);">🚪 خروج</a>
                </div>
            </div>
        </div>

        <!-- Navbar -->
        <nav class="navbar-ev">
            <a class="brand" onclick="goPage('home')"><span class="brand-icon">🔥</span>EVIL BAR</a>
            <div class="nav-actions">
                <button class="cart-btn" onclick="toggleCart()">🛒 <span class="cart-badge" id="cartBadge">0</span></button>
                <span style="color:var(--purple2);font-weight:600;font-size:13px;">👤 <span id="navUser"></span></span>
            </div>
        </nav>

        <div id="pageContent"></div>
        <footer><h4 style="color:var(--purple2);">🔥 EVIL BAR</h4><p>أفخم كافيه وبار | 2024</p></footer>
    </div>

    <!-- Cart -->
    <div class="cart-overlay" id="cartOverlay" onclick="toggleCart()"></div>
    <div class="cart-sidebar" id="cartSidebar">
        <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:12px;"><h4 style="color:var(--purple2);">🛒 السلة</h4><button onclick="toggleCart()" style="background:none;border:none;color:#fff;font-size:18px;cursor:pointer;">✕</button></div>
        <div id="cartItemsList"></div><hr style="border-color:rgba(255,255,255,0.06);margin:12px 0;">
        <h4>الإجمالي: <span style="color:var(--purple2);" id="cartTotal">0</span> ج.م</h4>
        <button class="btn btn-purple" onclick="openPayment()">💳 ادفع الآن</button>
        <button class="btn btn-red" onclick="clearCart()" style="margin-top:6px;">🗑 تفريغ</button>
    </div>

    <!-- Payment Modal -->
    <div class="modal-overlay" id="payModal">
        <div class="modal-dialog">
            <div style="display:flex;justify-content:space-between;margin-bottom:12px;"><h4 style="color:var(--purple2);">💳 الدفع</h4><button onclick="closePayment()" style="background:none;border:none;color:#fff;font-size:18px;cursor:pointer;">✕</button></div>
            <div class="auth-tabs" style="margin-bottom:12px;"><button class="auth-tab active" onclick="switchPay('visa')">💳 فيزا</button><button class="auth-tab" onclick="switchPay('vodafone')">📱 فودافون كاش</button></div>
            <div id="payVisa">
                <div style="background:linear-gradient(135deg,#1a1f71,#2a3f91);border-radius:12px;padding:16px;color:#fff;margin-bottom:12px;"><div style="font-size:24px;font-weight:900;">VISA</div></div>
                <input class="inp" id="cardName" placeholder="👤 الاسم على البطاقة"><input class="inp" id="cardNum" placeholder="💳 رقم البطاقة" maxlength="19" oninput="formatCard(this)" dir="ltr">
                <div style="display:flex;gap:8px;"><input class="inp" id="cardExp" placeholder="📅 MM/YY" maxlength="5" dir="ltr" style="flex:1;"><input class="inp" id="cardCVV" placeholder="🔒 CVV" maxlength="4" dir="ltr" type="password" style="flex:1;"></div>
                <div id="visaErrors" style="display:none;background:rgba(239,68,68,0.1);border:1px solid var(--red);border-radius:8px;padding:10px;margin:8px 0;color:var(--red);font-size:12px;"></div>
                <p style="color:var(--gray);font-size:12px;">💰 <span style="color:var(--purple2);font-weight:700;" id="visaAmt"></span></p>
                <button class="btn btn-purple" onclick="validateVisa()">🔍 فحص ودفع</button>
            </div>
            <div id="payVodafone" style="display:none;">
                <div style="background:#e60000;border-radius:12px;padding:16px;text-align:center;color:#fff;margin-bottom:12px;"><h5>📱 فودافون كاش</h5><div style="font-size:20px;font-weight:900;background:rgba(255,255,255,0.2);padding:10px;border-radius:8px;margin:8px 0;">01026966717<button onclick="copyVodafone()" style="background:#fff;color:#000;border:none;padding:4px 8px;border-radius:5px;cursor:pointer;margin-right:6px;">📋</button></div></div>
                <input class="inp" id="senderPhone" placeholder="📱 رقم هاتفك (إجباري)" dir="ltr"><input class="inp" id="senderName" placeholder="👤 اسمك">
                <div style="border:2px dashed rgba(139,92,246,0.3);border-radius:10px;padding:15px;text-align:center;cursor:pointer;margin-bottom:10px;" onclick="document.getElementById('scrFile').click()">📸 سكرين شوت<input type="file" id="scrFile" accept="image/*" style="display:none;" onchange="prevScr(event)"><img id="scrPreview" style="max-width:100%;max-height:120px;display:none;margin-top:8px;border-radius:6px;"></div>
                <p style="color:var(--gray);font-size:12px;">💰 <span style="color:var(--purple2);font-weight:700;" id="vodAmt"></span></p>
                <button class="btn btn-purple" onclick="submitVodafone()">📤 إرسال للمراجعة</button>
            </div>
        </div>
    </div>

    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
    <script>
        // ==================== DATA ====================
        const ADMIN = { name: 'المدير', phone: '01026966717', password: '308191', role: 'super_admin' };
        const PRODUCTS = [
            { id:1, name:'إسبرسو', cat:'hot', price:35, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1510707577719-ae7c14805e3a?w=400&q=80', desc:'إسبرسو إيطالي أصيل' },
            { id:2, name:'كابتشينو', cat:'hot', price:45, disc:38, rating:4.9, img:'https://images.unsplash.com/photo-1534778101976-62847782c213?w=400&q=80', desc:'كابتشينو برغوة' },
            { id:3, name:'لاتيه', cat:'hot', price:45, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1461023058943-07fcbe16d735?w=400&q=80', desc:'لاتيه كريمي' },
            { id:4, name:'موكا', cat:'hot', price:50, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1572442388796-11668a67e53d?w=400&q=80', desc:'موكا شوكولاتة' },
            { id:5, name:'قهوة تركي', cat:'hot', price:30, disc:null, rating:4.9, img:'https://images.unsplash.com/photo-1509042239860-f550ce710b93?w=400&q=80', desc:'قهوة تركية' },
            { id:6, name:'آيس لاتيه', cat:'cold', price:50, disc:null, rating:4.6, img:'https://images.unsplash.com/photo-1517701604599-bb29b565090c?w=400&q=80', desc:'آيس لاتيه' },
            { id:7, name:'ليمون نعناع', cat:'cold', price:35, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1621263764928-df1444c5e859?w=400&q=80', desc:'ليمونادة' },
            { id:8, name:'مانجو', cat:'cold', price:40, disc:null, rating:4.9, img:'https://images.unsplash.com/photo-1546173159-315724a31696?w=400&q=80', desc:'عصير مانجو' },
            { id:9, name:'تشيز كيك', cat:'food', price:60, disc:50, rating:4.9, img:'https://images.unsplash.com/photo-1533134242443-d4fd215305ad?w=400&q=80', desc:'تشيز كيك' },
            { id:10, name:'براوني', cat:'food', price:45, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1606313564200-e75d5e30476c?w=400&q=80', desc:'براوني' },
            { id:11, name:'كرواسون', cat:'food', price:35, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1555507036-ab1f4038024a?w=400&q=80', desc:'كرواسون' },
            { id:12, name:'هاينكن', cat:'alcohol', price:70, disc:null, rating:4.6, img:'https://images.unsplash.com/photo-1618885472179-5e474019f2a9?w=400&q=80', desc:'بيرة هاينكن' },
            { id:13, name:'ويسكي', cat:'alcohol', price:120, disc:100, rating:4.8, img:'https://images.unsplash.com/photo-1527281400683-1aae777175f0?w=400&q=80', desc:'ويسكي 12 سنة' },
            { id:14, name:'فودكا', cat:'alcohol', price:80, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1569529465841-dfecdab7503b?w=400&q=80', desc:'فودكا نقية' },
            { id:15, name:'موهيتو', cat:'alcohol', price:75, disc:null, rating:4.9, img:'https://images.unsplash.com/photo-1551538827-9c037cb4f32a?w=400&q=80', desc:'موهيتو منعش' },
            { id:16, name:'مارتيني', cat:'alcohol', price:85, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1575023782549-62ca0d244b39?w=400&q=80', desc:'مارتيني جاف' },
            { id:17, name:'شامبانيا', cat:'alcohol', price:200, disc:180, rating:4.9, img:'https://images.unsplash.com/photo-1510812431401-41d2bd2722f3?w=400&q=80', desc:'شامبانيا' },
            { id:18, name:'مارغريتا', cat:'alcohol', price:80, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1556855810-ac404d3c2eba?w=400&q=80', desc:'مارغريتا' },
        ];

        const BIN_DB = { '4':{bank:'Visa',country:'عالمي'}, '51':{bank:'Mastercard',country:'عالمي'}, '52':{bank:'Mastercard',country:'عالمي'}, '53':{bank:'Mastercard',country:'عالمي'}, '54':{bank:'Mastercard',country:'عالمي'}, '55':{bank:'Mastercard',country:'عالمي'}, '34':{bank:'Amex',country:'أمريكي'}, '37':{bank:'Amex',country:'أمريكي'}, '45':{bank:'البنك الأهلي',country:'مصر'}, '49':{bank:'بنك مصر',country:'مصر'}, '42':{bank:'CIB',country:'مصر'}, '40':{bank:'QNB',country:'مصر'} };

        let cart = JSON.parse(localStorage.getItem('evilCart')||'[]');
        let currentUser = JSON.parse(localStorage.getItem('evilUser')||'null');
        let scrFile = null, otpCode = '', otpTimer = null, otpSec = 120;
        let regData = {};

        // ==================== SOUND FX ====================
        function sfx(t) {
            try {
                const a = new (window.AudioContext||window.webkitAudioContext)();
                const o = a.createOscillator(); const g = a.createGain();
                o.connect(g); g.connect(a.destination);
                switch(t){ case'click':o.frequency.value=800;g.gain.value=0.08;o.start();o.stop(a.currentTime+0.04);break; case'ok':o.frequency.value=1200;g.gain.value=0.1;o.start();o.stop(a.currentTime+0.08);break; case'err':o.frequency.value=200;g.gain.value=0.12;o.start();o.stop(a.currentTime+0.25);break; case'add':o.frequency.value=600;g.gain.value=0.06;o.start();o.stop(a.currentTime+0.06);break; case'close':o.frequency.value=300;g.gain.value=0.1;o.start();o.stop(a.currentTime+0.12);break; case'min':o.frequency.value=500;g.gain.value=0.04;o.start();o.stop(a.currentTime+0.04);break; case'max':o.frequency.value=1000;g.gain.value=0.06;o.start();o.stop(a.currentTime+0.08);break; }
            } catch(e) {}
        }

        // ==================== PARTICLES ====================
        function initParticles() {
            const c = document.getElementById('particlesCanvas'), ctx = c.getContext('2d');
            c.width = innerWidth; c.height = innerHeight;
            const ps = Array.from({length:50}, () => ({ x:Math.random()*c.width, y:Math.random()*c.height, s:Math.random()*2+0.5, sx:(Math.random()-0.5)*0.4, sy:(Math.random()-0.5)*0.4, o:Math.random()*0.4+0.1 }));
            (function anim() {
                ctx.clearRect(0,0,c.width,c.height);
                ps.forEach(p => { p.x+=p.sx; p.y+=p.sy; if(p.x<0)p.x=c.width; if(p.x>c.width)p.x=0; if(p.y<0)p.y=c.height; if(p.y>c.height)p.y=0; ctx.beginPath(); ctx.arc(p.x,p.y,p.s,0,Math.PI*2); ctx.fillStyle=`rgba(139,92,246,${p.o})`; ctx.fill(); });
                requestAnimationFrame(anim);
            })();
        }

        // ==================== CLOCK ====================
        function updateClock() { const n = new Date(); document.getElementById('liveTime').textContent = n.toLocaleTimeString('ar-EG'); }
        setInterval(updateClock, 1000); updateClock();

        // ==================== 3 DOTS MENU ====================
        function toggleDotsMenu() { document.getElementById('dotsDropdown').classList.toggle('show'); sfx('click'); }
        document.addEventListener('click', (e) => { if (!e.target.closest('.three-dots-menu')) document.getElementById('dotsDropdown').classList.remove('show'); });

        // ==================== INIT ====================
        window.onload = function() {
            let users = JSON.parse(localStorage.getItem('evilUsers')||'[]');
            if (!users.find(u => u.phone === ADMIN.phone)) { users.push(ADMIN); localStorage.setItem('evilUsers', JSON.stringify(users)); }
            initParticles();
            // Fast preloader
            setTimeout(() => document.getElementById('preloader').classList.add('hidden'), 800);
            document.getElementById('authPage').style.display = 'flex';
            document.getElementById('mainApp').style.display = 'none';
            AOS.init({ duration: 500, once: true });
        };

        // ==================== AUTH ====================
        function switchTab(t) {
            document.querySelectorAll('.auth-tab').forEach(x => x.classList.remove('active'));
            if (t === 'login') { document.querySelector('.auth-tab:first-child').classList.add('active'); document.getElementById('loginForm').style.display='block'; document.getElementById('registerForm').style.display='none'; }
            else { document.querySelector('.auth-tab:last-child').classList.add('active'); document.getElementById('loginForm').style.display='none'; document.getElementById('registerForm').style.display='block'; }
            sfx('click');
        }

        function doLogin() {
            const id = document.getElementById('loginId').value.trim(), pass = document.getElementById('loginPass').value.trim();
            if (!id || !pass) { sfx('err'); return toast('املأ الحقول','err'); }
            const users = JSON.parse(localStorage.getItem('evilUsers')||'[]');
            const found = users.find(u => (u.phone===id||u.email===id) && u.password===pass);
            if (found) { loginSuccess(found); sfx('ok'); } else { toast('بيانات خاطئة','err'); sfx('err'); }
        }

        function sendWhatsAppOTP() {
            const phone = document.getElementById('regPhone').value.trim();
            const name = document.getElementById('regName').value.trim();
            const pass = document.getElementById('regPass').value.trim();
            if (!phone || !name || !pass) { sfx('err'); return toast('املأ جميع الحقول','err'); }
            if (pass.length < 8) { sfx('err'); return toast('كلمة المرور 8 أحرف على الأقل','err'); }
            let users = JSON.parse(localStorage.getItem('evilUsers')||'[]');
            if (users.find(u => u.phone === phone)) { sfx('err'); return toast('الهاتف مستخدم','err'); }
            
            regData = { name, phone, password: pass, role: 'user' };
            otpCode = String(Math.floor(100000 + Math.random() * 900000));
            localStorage.setItem('evilOTP', otpCode);
            
            // WhatsApp link
            const waMsg = encodeURIComponent(`رمز التحقق الخاص بـ Evil Bar: ${otpCode}\nلا تشاركه مع أحد`);
            const waLink = `https://wa.me/${phone.replace(/^\+/,'')}?text=${waMsg}`;
            
            document.getElementById('otpBox').classList.add('show');
            document.getElementById('o1').focus();
            otpSec = 120; updateOTPTimer();
            if (otpTimer) clearInterval(otpTimer);
            otpTimer = setInterval(() => { otpSec--; updateOTPTimer(); if (otpSec <= 0) { clearInterval(otpTimer); document.getElementById('btnResendOtp').disabled = false; document.getElementById('otpTimer').classList.add('expired'); document.getElementById('otpTimer').textContent = 'انتهت'; } }, 1000);
            document.getElementById('btnResendOtp').disabled = true;
            
            console.log('📱 OTP:', otpCode);
            // Open WhatsApp
            window.open(waLink, '_blank');
            toast('📲 تم فتح الواتساب. الرمز: ' + otpCode);
            sfx('ok');
        }

        function updateOTPTimer() { document.getElementById('otpTimer').textContent = `${String(Math.floor(otpSec/60)).padStart(2,'0')}:${String(otpSec%60).padStart(2,'0')}`; }
        function nextOtp(i) { if (i.value.length === 1) { const n = i.nextElementSibling; if (n) n.focus(); } }

        function verifyOTPAndRegister() {
            const code = ['o1','o2','o3','o4','o5','o6'].map(id => document.getElementById(id).value).join('');
            if (code === localStorage.getItem('evilOTP')) {
                clearInterval(otpTimer);
                let users = JSON.parse(localStorage.getItem('evilUsers')||'[]');
                users.push(regData);
                localStorage.setItem('evilUsers', JSON.stringify(users));
                loginSuccess(regData);
                sfx('ok'); toast('✅ تم التسجيل');
            } else { sfx('err'); toast('❌ رمز خاطئ','err'); }
        }

        function googleLogin() {
            const email = prompt('بريد Google:');
            if (email && email.includes('@')) {
                let users = JSON.parse(localStorage.getItem('evilUsers')||'[]');
                let u = users.find(x => x.email === email);
                if (!u) { u = { name: email.split('@')[0], email, phone: '', password: '', role: 'user', google: true }; users.push(u); localStorage.setItem('evilUsers', JSON.stringify(users)); }
                loginSuccess(u); sfx('ok');
            }
        }

        function loginSuccess(u) {
            currentUser = u; localStorage.setItem('evilUser', JSON.stringify(u));
            document.getElementById('authPage').style.display = 'none';
            document.getElementById('mainApp').classList.add('show');
            document.getElementById('mainApp').style.display = 'block';
            document.getElementById('navUser').textContent = u.name;
            if (u.role === 'super_admin') document.getElementById('dashLink').style.display = 'block';
            updateCartUI(); goPage('home'); toast('👋 ' + u.name);
        }

        function doLogout() {
            currentUser = null; localStorage.removeItem('evilUser');
            document.getElementById('mainApp').classList.remove('show');
            document.getElementById('mainApp').style.display = 'none';
            document.getElementById('authPage').style.display = 'flex';
            switchTab('login'); sfx('close'); toast('👋 تم الخروج');
        }

        // ==================== PAGES ====================
        function goPage(p) {
            sfx('click');
            const c = document.getElementById('pageContent');
            switch(p) {
                case 'home': c.innerHTML = homePage(); break;
                case 'menu': c.innerHTML = prodPage(PRODUCTS, '📋 المنيو'); break;
                case 'drinks': c.innerHTML = prodPage(PRODUCTS.filter(x => ['hot','cold'].includes(x.cat)), '🥤 مشروبات'); break;
                case 'alcohol': c.innerHTML = prodPage(PRODUCTS.filter(x => x.cat === 'alcohol'), '🍺 خمور'); break;
                case 'food': c.innerHTML = prodPage(PRODUCTS.filter(x => x.cat === 'food'), '🍰 حلويات'); break;
                case 'reserve': c.innerHTML = reservePage(); break;
                case 'profile': c.innerHTML = profilePage(); break;
                case 'dashboard': c.innerHTML = (currentUser && currentUser.role === 'super_admin') ? dashPage() : '<p style="text-align:center;padding:80px;">⛔ غير مصرح</p>'; break;
            }
            window.scrollTo(0,0); AOS.refresh();
        }

        function homePage() {
            const f = PRODUCTS.filter(p => [1,3,6,8,9,12,14,16].includes(p.id));
            return `<div class="hero"><div><h1>EVIL BAR</h1><p>✦ أفخم كافيه وبار ✦</p><div class="hero-btns"><button class="hero-btn hero-btn-primary" onclick="goPage('menu')">📋 المنيو</button><button class="hero-btn hero-btn-outline" onclick="goPage('reserve')">📅 حجز</button></div></div></div><div class="section"><h2 class="section-title"><span class="hl">منتجات</span> مميزة</h2><div class="products-grid">${f.map(p => productCard(p)).join('')}</div></div>`;
        }

        function prodPage(items, t) { return `<div class="section"><h2 class="section-title"><span class="hl">${t}</span></h2><div class="products-grid">${items.map(p => productCard(p)).join('')}</div></div>`; }

        function productCard(p) {
            const pr = p.disc || p.price;
            return `<div class="product-card" data-aos="fade-up"><div class="product-img"><img src="${p.img}" alt="${p.name}" loading="lazy" onerror="this.src='https://via.placeholder.com/400x180/120026/8B5CF6?text=${p.name}'">${p.disc?`<span class="badge-disc">-${Math.round((1-p.disc/p.price)*100)}%</span>`:''}</div><div class="product-body"><h5>${p.name}</h5><p class="desc">${p.desc}</p><div class="price-row">${p.disc?`<span class="price-old">${p.price}ج.م</span>`:''}<span class="price-current">${pr} ج.م</span></div><div class="stars">${'★'.repeat(Math.floor(p.rating))} ${p.rating}</div><button class="btn-add" onclick="addToCart(${p.id});sfx('add')">🛒 أضف</button></div></div>`;
        }

        function reservePage() {
            return `<div class="section"><div style="max-width:450px;margin:0 auto;background:var(--glass);border:1px solid var(--border-purple);border-radius:18px;padding:25px;"><h3 style="color:var(--purple2);text-align:center;">📅 حجز</h3><input class="inp" placeholder="الأشخاص"><input class="inp" type="date"><input class="inp" type="time"><button class="btn btn-purple" onclick="sfx('ok');toast('✅ تم')">تأكيد</button></div></div>`;
        }

        function profilePage() {
            return `<div class="section"><div style="max-width:450px;margin:0 auto;background:var(--glass);border:1px solid var(--border-purple);border-radius:18px;padding:25px;"><h3 style="color:var(--purple2);">👤 ${currentUser.name}</h3><p>📧 ${currentUser.email||'-'}</p><p>📱 ${currentUser.phone||'-'}</p></div></div>`;
        }

        function dashPage() {
            const users = JSON.parse(localStorage.getItem('evilUsers')||'[]');
            const payments = JSON.parse(localStorage.getItem('evilPayments')||'[]');
            const pending = payments.filter(p => p.status === 'قيد المراجعة');
            const rev = payments.filter(p => p.status === 'مكتمل').reduce((s,p) => s+p.amount, 0);
            return `<div class="section"><h2 class="section-title">📊 <span class="hl">لوحة التحكم</span></h2><p style="text-align:center;color:var(--purple2);">👑 ${currentUser.name}</p><div class="stat-grid" style="max-width:900px;margin:0 auto 15px;"><div class="stat-box"><h2>${users.length}</h2><p>👥 مستخدمين</p></div><div class="stat-box"><h2>${payments.length}</h2><p>💳 مدفوعات</p></div><div class="stat-box"><h2>${rev} ج.م</h2><p>💰 إيرادات</p></div><div class="stat-box"><h2>${pending.length}</h2><p>⏳ مراجعة</p></div></div>${pending.length>0?`<div style="max-width:900px;margin:15px auto;background:rgba(245,158,11,0.08);border:1px solid var(--orange);border-radius:12px;padding:15px;"><h4 style="color:var(--orange);">⏳ مراجعة</h4>${pending.map(p=>`<div style="background:var(--bg3);padding:10px;border-radius:8px;margin:6px 0;display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:6px;"><div><strong>${p.userName}</strong> | ${p.amount}ج.م<br><small>${p.cardInfo||p.senderPhone||''} | ${p.date}</small></div><div><button class="btn btn-green btn-sm" onclick="approve(${p.id})">✅</button><button class="btn btn-red btn-sm" onclick="reject(${p.id})">❌</button></div></div>`).join('')}</div>`:''}<h4 style="color:var(--purple2);margin:15px 0;">💳 المدفوعات</h4><div style="overflow-x:auto;max-width:900px;margin:0 auto;"><table><tr><th>#</th><th>عميل</th><th>طريقة</th><th>مبلغ</th><th>معلومات</th><th>حالة</th><th>تاريخ</th></tr>${payments.length===0?'<tr><td colspan="7">لا يوجد</td></tr>':payments.reverse().slice(0,20).map(p=>`<tr><td>${p.id}</td><td>${p.userName}</td><td>${p.method}</td><td style="color:var(--purple2);">${p.amount}ج.م</td><td>${p.cardInfo||p.senderPhone||'-'}</td><td><span class="status-${p.status==='مكتمل'?'a':p.status==='مرفوض'?'r':'p'}">${p.status}</span></td><td>${p.date}</td></tr>`).join('')}</table></div></div>`;
        }

        function approve(id) { let p=JSON.parse(localStorage.getItem('evilPayments')||'[]'); const i=p.findIndex(x=>x.id===id); if(i>-1){p[i].status='مكتمل';localStorage.setItem('evilPayments',JSON.stringify(p));goPage('dashboard');sfx('ok');toast('✅ تم');} }
        function reject(id) { let p=JSON.parse(localStorage.getItem('evilPayments')||'[]'); const i=p.findIndex(x=>x.id===id); if(i>-1){p[i].status='مرفوض';localStorage.setItem('evilPayments',JSON.stringify(p));goPage('dashboard');sfx('err');toast('❌ تم');} }

        // ==================== CART ====================
        function addToCart(id) { const p=PRODUCTS.find(x=>x.id===id); if(!p)return; const ex=cart.find(i=>i.productId===id); if(ex)ex.qty++; else cart.push({productId:id,qty:1,price:p.disc||p.price,name:p.name,img:p.img}); saveCart(); toast('✅ '+p.name); }
        function removeCart(i){cart.splice(i,1);saveCart();} function qtyCart(i,d){cart[i].qty+=d;if(cart[i].qty<=0)cart.splice(i,1);saveCart();}
        function clearCart(){cart=[];saveCart();toast('🗑 تم');} function saveCart(){localStorage.setItem('evilCart',JSON.stringify(cart));updateCartUI();}
        function updateCartUI(){
            const cnt=cart.reduce((s,i)=>s+i.qty,0),tot=cart.reduce((s,i)=>s+(i.price*i.qty),0);
            document.getElementById('cartBadge').textContent=cnt; document.getElementById('cartTotal').textContent=tot+' ج.م';
            document.getElementById('visaAmt').textContent=tot+' ج.م'; document.getElementById('vodAmt').textContent=tot+' ج.م';
            const l=document.getElementById('cartItemsList');
            if(cart.length===0)l.innerHTML='<p style="color:var(--gray);">فارغة</p>';
            else l.innerHTML=cart.map((item,i)=>`<div style="display:flex;align-items:center;gap:7px;padding:7px;background:rgba(255,255,255,0.02);border-radius:7px;margin-bottom:5px;"><img src="${item.img}" width="32" style="border-radius:4px;"><div style="flex:1;"><strong>${item.name}</strong><br><small style="color:var(--purple2);">${item.price}ج.م × ${item.qty}</small></div><button onclick="qtyCart(${i},-1)" style="background:rgba(255,255,255,0.08);color:#fff;border:none;padding:2px 6px;border-radius:4px;cursor:pointer;">-</button><span>${item.qty}</span><button onclick="qtyCart(${i},1)" style="background:rgba(255,255,255,0.08);color:#fff;border:none;padding:2px 6px;border-radius:4px;cursor:pointer;">+</button><button onclick="removeCart(${i})" style="background:var(--red);color:#fff;border:none;padding:2px 6px;border-radius:4px;cursor:pointer;">🗑</button></div>`).join('');
        }
        function toggleCart(){document.getElementById('cartSidebar').classList.toggle('open');document.getElementById('cartOverlay').classList.toggle('open');}

        // ==================== PAYMENT ====================
        function openPayment(){if(cart.length===0)return toast('سلة فارغة','err');const t=cart.reduce((s,i)=>s+(i.price*i.qty),0);document.getElementById('visaAmt').textContent=t+' ج.م';document.getElementById('vodAmt').textContent=t+' ج.م';document.getElementById('payModal').classList.add('open');}
        function closePayment(){document.getElementById('payModal').classList.remove('open');scrFile=null;document.getElementById('scrPreview').style.display='none';document.getElementById('scrFile').value='';document.getElementById('visaErrors').style.display='none';}
        function switchPay(t){document.querySelectorAll('#payModal .auth-tab').forEach(x=>x.classList.remove('active'));document.getElementById('payVisa').style.display=t==='visa'?'block':'none';document.getElementById('payVodafone').style.display=t==='vodafone'?'block':'none';if(t==='visa')document.querySelector('#payModal .auth-tab:first-child').classList.add('active');else document.querySelector('#payModal .auth-tab:last-child').classList.add('active');}
        function formatCard(i){let v=i.value.replace(/\D/g,'').substring(0,16);i.value=v.replace(/(\d{4})(?=\d)/g,'$1 ');}
        function luhnCheck(num){let s=0,alt=false;for(let i=num.length-1;i>=0;i--){let d=parseInt(num[i]);if(alt){d*=2;if(d>9)d-=9;}s+=d;alt=!alt;}return s%10===0;}
        function getBank(bin){for(let k in BIN_DB){if(bin.startsWith(k))return BIN_DB[k];}return null;}

        function validateVisa(){
            const n=document.getElementById('cardName').value.trim(),num=document.getElementById('cardNum').value.replace(/\s/g,''),exp=document.getElementById('cardExp').value.trim(),cvv=document.getElementById('cardCVV').value.trim();
            const err=document.getElementById('visaErrors'); let errs=[];
            if(!n||n.length<3)errs.push('❌ اسم حامل البطاقة');
            if(!luhnCheck(num))errs.push('❌ فشل Luhn');
            if(num.length<13)errs.push('❌ رقم قصير');
            if(!exp||!exp.match(/^\d{2}\/\d{2}$/))errs.push('❌ تاريخ غير صالح');
            if(!cvv||cvv.length<3)errs.push('❌ CVV');
            if(/^(\d)\1+$/.test(num))errs.push('🚫 وهمية');
            const bank = getBank(num.substring(0,6));
            if(!bank)errs.push('⚠️ بنك غير معروف');
            if(errs.length>0){err.innerHTML=errs.join('<br>');err.style.display='block';sfx('err');return;}
            const info = bank ? `${bank.bank} - ${bank.country} | ${n} | ****${num.slice(-4)}` : `غير معروف | ${n}`;
            completePay('💳 فيزا', info); sfx('ok');
        }

        function submitVodafone(){
            const ph=document.getElementById('senderPhone').value.trim(),nm=document.getElementById('senderName').value.trim();
            if(!ph)return toast('رقم الهاتف','err'); if(!nm)return toast('الاسم','err'); if(!scrFile)return t
