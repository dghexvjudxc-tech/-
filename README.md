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
            --bg: #020202; --bg2: #0a0a0a; --gold: #D4AF37; --gold2: #FFD700;
            --white: #fff; --gray: #999; --red: #e74c3c; --green: #2ecc71;
            --orange: #f39c12; --blue: #3498db;
        }
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body {
            background: var(--bg); color: var(--white);
            font-family: 'Segoe UI', Tahoma, sans-serif; min-height: 100vh;
        }

        /* ========== AUTH PAGE - FIRST THING ========== */
        #authPage {
            display: flex;
            min-height: 100vh;
            align-items: center;
            justify-content: center;
            padding: 20px;
            background: radial-gradient(ellipse at center, rgba(212,175,55,0.05) 0%, transparent 70%);
        }
        .auth-box {
            background: #111;
            border: 1px solid rgba(212,175,55,0.3);
            border-radius: 20px;
            padding: 35px 30px;
            width: 100%;
            max-width: 420px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.5);
        }
        .auth-box h1 {
            text-align: center;
            color: var(--gold);
            font-size: 36px;
            font-weight: 900;
            letter-spacing: 5px;
            margin-bottom: 5px;
        }
        .auth-box .subtitle {
            text-align: center;
            color: var(--gray);
            font-size: 14px;
            margin-bottom: 25px;
        }

        /* Tabs */
        .tabs {
            display: flex;
            gap: 5px;
            margin-bottom: 20px;
            background: rgba(255,255,255,0.03);
            border-radius: 12px;
            padding: 4px;
        }
        .tab {
            flex: 1;
            padding: 10px;
            text-align: center;
            background: transparent;
            border: none;
            color: var(--gray);
            border-radius: 10px;
            cursor: pointer;
            font-size: 13px;
            font-weight: 600;
            transition: 0.3s;
        }
        .tab.active {
            background: linear-gradient(135deg, #8B7500, var(--gold));
            color: #000;
            font-weight: 700;
        }

        /* Inputs */
        .inp {
            width: 100%;
            padding: 14px 16px;
            margin-bottom: 12px;
            background: #1a1a1a;
            border: 1.5px solid #333;
            border-radius: 12px;
            color: #fff;
            font-size: 15px;
            transition: 0.3s;
        }
        .inp:focus {
            outline: none;
            border-color: var(--gold);
            box-shadow: 0 0 0 3px rgba(212,175,55,0.1);
        }
        .inp.error { border-color: var(--red); }
        .inp::placeholder { color: #555; }

        /* Buttons */
        .btn {
            width: 100%;
            padding: 14px;
            border: none;
            border-radius: 12px;
            font-size: 16px;
            font-weight: 700;
            cursor: pointer;
            margin-bottom: 8px;
            transition: 0.3s;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
        }
        .btn-gold {
            background: linear-gradient(135deg, #7A6500, var(--gold));
            color: #000;
        }
        .btn-gold:hover { transform: translateY(-2px); box-shadow: 0 8px 25px rgba(212,175,55,0.4); }
        .btn-outline {
            background: transparent;
            border: 2px solid rgba(212,175,55,0.3);
            color: var(--gold);
        }
        .btn-outline:hover { border-color: var(--gold); background: rgba(212,175,55,0.05); }
        .btn-google {
            background: #fff;
            color: #333;
            font-weight: 600;
        }
        .btn-google:hover { background: #f0f0f0; }

        .divider {
            text-align: center;
            margin: 15px 0;
            color: #666;
            font-size: 12px;
            position: relative;
        }
        .divider::before, .divider::after {
            content: '';
            position: absolute;
            top: 50%;
            width: 35%;
            height: 1px;
            background: rgba(255,255,255,0.1);
        }
        .divider::before { left: 0; }
        .divider::after { right: 0; }

        .link {
            color: var(--gold);
            cursor: pointer;
            font-weight: 600;
        }
        .link:hover { text-decoration: underline; }

        /* OTP */
        .otp-section { display: none; }
        .otp-section.show { display: block; }
        .otp-inputs {
            display: flex;
            gap: 8px;
            justify-content: center;
            margin: 15px 0;
        }
        .otp-inputs input {
            width: 48px;
            height: 52px;
            text-align: center;
            font-size: 22px;
            font-weight: 700;
            background: #1a1a1a;
            border: 2px solid #333;
            border-radius: 10px;
            color: var(--gold);
        }
        .otp-inputs input:focus { border-color: var(--gold); outline: none; }
        .timer {
            text-align: center;
            color: var(--gold);
            font-weight: 700;
            margin: 10px 0;
        }
        .timer.expired { color: var(--red); }

        /* ========== MAIN APP ========== */
        #mainApp { display: none; }
        #mainApp.show { display: block; }

        .navbar {
            background: rgba(5,5,5,0.9);
            backdrop-filter: blur(20px);
            border-bottom: 1px solid rgba(212,175,55,0.15);
            padding: 12px 20px;
            position: sticky;
            top: 0;
            z-index: 100;
            display: flex;
            align-items: center;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 10px;
        }
        .brand {
            color: var(--gold);
            font-size: 24px;
            font-weight: 900;
            text-decoration: none;
            letter-spacing: 3px;
        }
        .nav-links {
            display: flex;
            gap: 5px;
            flex-wrap: wrap;
            align-items: center;
        }
        .nav-links a {
            color: #fff;
            text-decoration: none;
            padding: 7px 12px;
            border-radius: 8px;
            font-size: 13px;
            cursor: pointer;
            transition: 0.3s;
        }
        .nav-links a:hover, .nav-links a.active {
            color: var(--gold);
            background: rgba(212,175,55,0.08);
        }

        .hero {
            min-height: 85vh;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            background: linear-gradient(rgba(0,0,0,0.8), rgba(0,0,0,0.9)), url('https://images.unsplash.com/photo-1470337458703-46ad1756a187?w=1920');
            background-size: cover;
            background-position: center;
        }
        .hero h1 {
            font-size: clamp(45px, 8vw, 90px);
            color: var(--gold);
            font-weight: 900;
            letter-spacing: 8px;
        }
        .hero p {
            font-size: 18px;
            color: #ccc;
            margin: 15px 0 25px;
        }

        .section { padding: 60px 20px; }
        .section-title {
            text-align: center;
            font-size: 30px;
            margin-bottom: 35px;
        }
        .gold-text { color: var(--gold); }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
            gap: 18px;
            max-width: 1200px;
            margin: 0 auto;
        }
        .product-card {
            background: #111;
            border: 1px solid #222;
            border-radius: 15px;
            overflow: hidden;
            transition: 0.3s;
        }
        .product-card:hover {
            border-color: var(--gold);
            transform: translateY(-5px);
            box-shadow: 0 15px 40px rgba(0,0,0,0.4);
        }
        .product-img {
            height: 190px;
            overflow: hidden;
            position: relative;
        }
        .product-img img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: 0.5s;
        }
        .product-card:hover .product-img img { transform: scale(1.08); }
        .badge-discount {
            position: absolute;
            top: 10px;
            left: 10px;
            background: var(--red);
            color: #fff;
            padding: 3px 10px;
            border-radius: 20px;
            font-size: 11px;
            font-weight: 700;
        }
        .product-body { padding: 15px; }
        .product-body h5 { margin-bottom: 3px; font-size: 16px; }
        .product-body .desc { color: #888; font-size: 12px; margin-bottom: 8px; }
        .price {
            color: var(--gold);
            font-size: 20px;
            font-weight: 900;
        }
        .price-old {
            text-decoration: line-through;
            color: #666;
            font-size: 13px;
            margin-left: 8px;
        }
        .stars { color: var(--gold); font-size: 12px; margin: 5px 0 10px; }
        .btn-add {
            width: 100%;
            padding: 10px;
            background: linear-gradient(135deg, #7A6500, var(--gold));
            color: #000;
            border: none;
            border-radius: 10px;
            font-weight: 700;
            cursor: pointer;
            font-size: 14px;
            transition: 0.3s;
        }
        .btn-add:hover { box-shadow: 0 5px 20px rgba(212,175,55,0.3); }

        /* Cart */
        .cart-overlay {
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: rgba(0,0,0,0.7);
            z-index: 200;
            display: none;
        }
        .cart-overlay.open { display: block; }
        .cart-sidebar {
            position: fixed;
            top: 0; right: -400px;
            width: 380px; height: 100%;
            background: #0d0d0d;
            z-index: 201;
            transition: right 0.3s;
            padding: 20px;
            overflow-y: auto;
            border-left: 1px solid rgba(212,175,55,0.3);
        }
        .cart-sidebar.open { right: 0; }

        /* Modal */
        .modal-overlay {
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: rgba(0,0,0,0.9);
            z-index: 300;
            display: none;
            align-items: center;
            justify-content: center;
        }
        .modal-overlay.open { display: flex; }
        .modal-box {
            background: #111;
            border: 2px solid rgba(212,175,55,0.4);
            border-radius: 20px;
            padding: 25px;
            width: 90%;
            max-width: 500px;
            max-height: 85vh;
            overflow-y: auto;
        }

        /* Dashboard */
        .stat-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
            gap: 15px;
            margin-bottom: 25px;
        }
        .stat-box {
            background: #111;
            border: 1px solid #222;
            border-radius: 15px;
            padding: 20px;
            text-align: center;
        }
        .stat-box h3 { font-size: 34px; color: var(--gold); }

        table {
            width: 100%;
            border-collapse: collapse;
            font-size: 13px;
        }
        th {
            background: #1a1a1a;
            color: var(--gold);
            padding: 12px;
            text-align: right;
        }
        td {
            padding: 10px 12px;
            border-bottom: 1px solid #222;
        }

        .status-review { background: var(--blue); color: #fff; padding: 3px 10px; border-radius: 20px; font-size: 11px; font-weight: 700; }
        .status-done { background: var(--green); color: #fff; padding: 3px 10px; border-radius: 20px; font-size: 11px; font-weight: 700; }
        .status-no { background: var(--red); color: #fff; padding: 3px 10px; border-radius: 20px; font-size: 11px; font-weight: 700; }

        .toast {
            position: fixed;
            bottom: 20px;
            right: 20px;
            z-index: 999;
            background: #1a1a1a;
            border: 1px solid rgba(212,175,55,0.3);
            padding: 15px 20px;
            border-radius: 12px;
            color: #fff;
            font-weight: 600;
            transform: translateX(120%);
            transition: 0.3s;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
        }
        .toast.show { transform: translateX(0); }
        .toast.ok { border-right: 4px solid var(--green); }
        .toast.err { border-right: 4px solid var(--red); }

        footer {
            background: #050505;
            border-top: 1px solid rgba(212,175,55,0.1);
            padding: 30px;
            text-align: center;
            color: #888;
            margin-top: 40px;
        }

        @media (max-width: 768px) {
            .hero h1 { font-size: 36px; }
            .cart-sidebar { width: 100%; right: -100%; }
            .products-grid { grid-template-columns: repeat(auto-fill, minmax(155px, 1fr)); gap: 12px; }
        }
    </style>
</head>
<body>

    <!-- Toast -->
    <div class="toast" id="toast"></div>

    <!-- ==================== AUTH PAGE (FIRST THING) ==================== -->
    <div id="authPage">
        <div class="auth-box">
            <h1>🔥 EVIL BAR</h1>
            <p class="subtitle">أفخم كافيه وبار في المدينة</p>

            <div class="tabs">
                <button class="tab active" onclick="switchAuthTab('login')">🔑 دخول</button>
                <button class="tab" onclick="switchAuthTab('register')">📝 حساب جديد</button>
            </div>

            <!-- Login -->
            <div id="loginForm">
                <input type="text" class="inp" id="loginId" placeholder="📧 البريد أو 📱 الهاتف" dir="ltr">
                <input type="password" class="inp" id="loginPass" placeholder="🔒 كلمة المرور">
                <button class="btn btn-gold" onclick="login()">🚀 تسجيل الدخول</button>
                <button class="btn btn-google" onclick="googleLogin()"><i class="fab fa-google"></i> Google</button>
                <p style="text-align:center;margin-top:10px;font-size:11px;color:#666;">
                    المدير: 01026966717 | 308191
                </p>
            </div>

            <!-- Register -->
            <div id="registerForm" style="display:none;">
                <input type="text" class="inp" id="regName" placeholder="👤 الاسم الكامل">
                <input type="email" class="inp" id="regEmail" placeholder="📧 البريد الإلكتروني" dir="ltr">
                <input type="tel" class="inp" id="regPhone" placeholder="📱 الهاتف (اختياري)" dir="ltr">
                <input type="password" class="inp" id="regPass" placeholder="🔒 كلمة المرور">
                <button class="btn btn-gold" onclick="register()">✅ إنشاء حساب</button>
                <button class="btn btn-outline" onclick="switchAuthTab('login')">⬅ العودة للدخول</button>
            </div>

            <!-- Phone OTP -->
            <div class="otp-section" id="otpSection">
                <p style="text-align:center;color:#888;font-size:13px;">📱 أدخل رمز التحقق المرسل إلى هاتفك</p>
                <div class="otp-inputs">
                    <input type="text" maxlength="1" oninput="nextOtp(this)" id="o1">
                    <input type="text" maxlength="1" oninput="nextOtp(this)" id="o2">
                    <input type="text" maxlength="1" oninput="nextOtp(this)" id="o3">
                    <input type="text" maxlength="1" oninput="nextOtp(this)" id="o4">
                    <input type="text" maxlength="1" oninput="nextOtp(this)" id="o5">
                    <input type="text" maxlength="1" oninput="nextOtp(this)" id="o6">
                </div>
                <div class="timer" id="otpTimer">02:00</div>
                <button class="btn btn-gold" onclick="verifyOTP()">✅ تأكيد</button>
                <button class="btn btn-outline" id="btnResendOtp" onclick="sendOTP()" disabled>🔄 إعادة الإرسال</button>
            </div>
        </div>
    </div>

    <!-- ==================== MAIN APP ==================== -->
    <div id="mainApp">
        <nav class="navbar">
            <a class="brand" href="#" onclick="goPage('home')">🔥 EVIL BAR</a>
            <div class="nav-links">
                <a href="#" onclick="goPage('home')" class="active">🏠 الرئيسية</a>
                <a href="#" onclick="goPage('menu')">📋 المنيو</a>
                <a href="#" onclick="goPage('drinks')">🥤 مشروبات</a>
                <a href="#" onclick="goPage('alcohol')">🍺 خمور</a>
                <a href="#" onclick="goPage('food')">🍰 حلويات</a>
                <a href="#" onclick="goPage('reserve')">📅 حجز</a>
                <a href="#" id="dashLink" style="display:none;" onclick="goPage('dashboard')">📊 لوحة التحكم</a>
                <button class="btn btn-gold" style="width:auto;padding:8px 14px;font-size:12px;" onclick="toggleCart()">🛒 <span id="cartBadge">0</span></button>
                <span style="color:var(--gold);cursor:pointer;font-weight:600;" onclick="goPage('profile')">👤 <span id="navUser"></span></span>
                <button class="btn" style="width:auto;padding:8px 14px;font-size:12px;background:var(--red);color:#fff;" onclick="doLogout()">🚪</button>
            </div>
        </nav>

        <div id="pageContent"></div>

        <footer>
            <h4 style="color:var(--gold);">EVIL BAR</h4>
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
        <hr style="border-color:#333;margin:15px 0;">
        <h4>الإجمالي: <span style="color:var(--gold);" id="cartTotal">0</span> ج.م</h4>
        <button class="btn btn-gold" onclick="openPayment()" style="margin-top:10px;">💳 ادفع الآن</button>
        <button class="btn" style="background:var(--red);color:#fff;margin-top:5px;" onclick="clearCart()">🗑 تفريغ</button>
    </div>

    <!-- Payment Modal -->
    <div class="modal-overlay" id="payModal">
        <div class="modal-box">
            <div style="display:flex;justify-content:space-between;margin-bottom:15px;">
                <h4 style="color:var(--gold);">💳 الدفع</h4>
                <button onclick="closePayment()" style="background:none;border:none;color:#fff;font-size:20px;cursor:pointer;">✕</button>
            </div>
            <div class="tabs" style="margin-bottom:15px;">
                <button class="tab active" onclick="switchPay('visa')">💳 فيزا</button>
                <button class="tab" onclick="switchPay('vodafone')">📱 فودافون كاش</button>
            </div>
            <div id="payVisa">
                <div style="background:linear-gradient(135deg,#1a1f71,#2a3f91);border-radius:15px;padding:20px;color:#fff;margin-bottom:15px;">
                    <div style="font-size:26px;font-weight:900;">VISA</div>
                    <div style="font-size:16px;letter-spacing:3px;margin:8px 0;">•••• •••• •••• ••••</div>
                </div>
                <input class="inp" id="cardName" placeholder="👤 الاسم على البطاقة">
                <input class="inp" id="cardNum" placeholder="💳 رقم البطاقة" maxlength="19" oninput="formatCard(this)" dir="ltr">
                <div style="display:flex;gap:10px;">
                    <input class="inp" id="cardExp" placeholder="📅 MM/YY" maxlength="5" style="flex:1;" dir="ltr">
                    <input class="inp" id="cardCVV" placeholder="🔒 CVV" maxlength="4" style="flex:1;" dir="ltr" type="password">
                </div>
                <div id="visaErrors" style="display:none;background:rgba(231,76,60,0.1);border:1px solid var(--red);border-radius:10px;padding:12px;margin-bottom:12px;color:var(--red);font-size:13px;"></div>
                <p style="color:#888;">💰 المبلغ: <span style="color:var(--gold);font-weight:700;" id="visaAmt"></span></p>
                <button class="btn btn-gold" onclick="validateVisa()">🔍 فحص ودفع</button>
            </div>
            <div id="payVodafone" style="display:none;">
                <div style="background:#e60000;border-radius:15px;padding:20px;text-align:center;color:#fff;margin-bottom:15px;">
                    <h5>📱 فودافون كاش</h5>
                    <div style="font-size:22px;font-weight:900;background:rgba(255,255,255,0.2);padding:12px;border-radius:10px;margin:10px 0;">
                        01026966717
                        <button onclick="copyVodafone()" style="background:#fff;color:#000;border:none;padding:5px 10px;border-radius:5px;cursor:pointer;margin-right:8px;">📋 نسخ</button>
                    </div>
                    <p style="font-size:12px;">الاسم: Evil Bar</p>
                </div>
                <input class="inp" id="senderPhone" placeholder="📱 رقم هاتفك المحول منه (إجباري)" dir="ltr">
                <input class="inp" id="senderName" placeholder="👤 اسمك في فودافون كاش">
                <div style="border:2px dashed rgba(212,175,55,0.4);border-radius:12px;padding:20px;text-align:center;cursor:pointer;margin-bottom:15px;" onclick="document.getElementById('scrFile').click()">
                    📸 اضغط لرفع سكرين شوت
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
            { id:1, name:'إسبرسو', cat:'hot', price:35, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1510707577719-ae7c14805e3a?w=400', desc:'إسبرسو إيطالي أصيل' },
            { id:2, name:'كابتشينو', cat:'hot', price:45, disc:38, rating:4.9, img:'https://images.unsplash.com/photo-1534778101976-62847782c213?w=400', desc:'كابتشينو برغوة' },
            { id:3, name:'لاتيه', cat:'hot', price:45, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1461023058943-07fcbe16d735?w=400', desc:'لاتيه كريمي' },
            { id:4, name:'موكا', cat:'hot', price:50, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1572442388796-11668a67e53d?w=400', desc:'موكا شوكولاتة' },
            { id:5, name:'أمريكانو', cat:'hot', price:40, disc:35, rating:4.6, img:'https://images.unsplash.com/photo-1551030173-122aabc4489c?w=400', desc:'أمريكانو كلاسيك' },
            { id:6, name:'قهوة تركي', cat:'hot', price:30, disc:null, rating:4.9, img:'https://images.unsplash.com/photo-1509042239860-f550ce710b93?w=400', desc:'قهوة تركية' },
            { id:7, name:'آيس لاتيه', cat:'cold', price:50, disc:null, rating:4.6, img:'https://images.unsplash.com/photo-1517701604599-bb29b565090c?w=400', desc:'آيس لاتيه' },
            { id:8, name:'ليمون نعناع', cat:'cold', price:35, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1621263764928-df1444c5e859?w=400', desc:'ليمونادة' },
            { id:9, name:'عصير برتقال', cat:'cold', price:30, disc:null, rating:4.5, img:'https://images.unsplash.com/photo-1621506289937-a8e4df240d0b?w=400', desc:'عصير طبيعي' },
            { id:10, name:'مانجو', cat:'cold', price:40, disc:null, rating:4.9, img:'https://images.unsplash.com/photo-1546173159-315724a31696?w=400', desc:'عصير مانجو' },
            { id:11, name:'تشيز كيك', cat:'food', price:60, disc:50, rating:4.9, img:'https://images.unsplash.com/photo-1533134242443-d4fd215305ad?w=400', desc:'تشيز كيك' },
            { id:12, name:'براوني', cat:'food', price:45, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1606313564200-e75d5e30476c?w=400', desc:'براوني' },
            { id:13, name:'كرواسون', cat:'food', price:35, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1555507036-ab1f4038024a?w=400', desc:'كرواسون' },
            { id:14, name:'كيك شوكولاتة', cat:'food', price:70, disc:60, rating:4.9, img:'https://images.unsplash.com/photo-1578985545062-69928b1d9587?w=400', desc:'كيك شوكولاتة' },
            { id:15, name:'هاينكن', cat:'alcohol', price:70, disc:null, rating:4.6, img:'https://images.unsplash.com/photo-1618885472179-5e474019f2a9?w=400', desc:'بيرة هاينكن' },
            { id:16, name:'ويسكي', cat:'alcohol', price:120, disc:100, rating:4.8, img:'https://images.unsplash.com/photo-1527281400683-1aae777175f0?w=400', desc:'ويسكي 12 سنة' },
            { id:17, name:'فودكا', cat:'alcohol', price:80, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1569529465841-dfecdab7503b?w=400', desc:'فودكا نقية' },
            { id:18, name:'موهيتو', cat:'alcohol', price:75, disc:null, rating:4.9, img:'https://images.unsplash.com/photo-1551538827-9c037cb4f32a?w=400', desc:'موهيتو منعش' },
            { id:19, name:'مارتيني', cat:'alcohol', price:85, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1575023782549-62ca0d244b39?w=400', desc:'مارتيني جاف' },
            { id:20, name:'شامبانيا', cat:'alcohol', price:200, disc:180, rating:4.9, img:'https://images.unsplash.com/photo-1510812431401-41d2bd2722f3?w=400', desc:'شامبانيا فرنسية' },
        ];

        // ==================== STATE ====================
        let cart = JSON.parse(localStorage.getItem('evilCart') || '[]');
        let currentUser = JSON.parse(localStorage.getItem('evilUser') || 'null');
        let otpCode = '';
        let otpTimer = null;
        let otpSeconds = 120;
        let scrFile = null;

        // ==================== INIT ====================
        window.addEventListener('DOMContentLoaded', () => {
            // Ensure admin exists
            let users = JSON.parse(localStorage.getItem('evilUsers') || '[]');
            if (!users.find(u => u.phone === ADMIN.phone)) {
                users.push(ADMIN);
                localStorage.setItem('evilUsers', JSON.stringify(users));
            }

            // ALWAYS SHOW AUTH PAGE FIRST
            document.getElementById('authPage').style.display = 'flex';
            document.getElementById('mainApp').style.display = 'none';

            AOS.init({ duration: 600 });
        });

        // ==================== AUTH ====================
        function switchAuthTab(tab) {
            document.querySelectorAll('.tabs .tab').forEach(t => t.classList.remove('active'));
            if (tab === 'login') {
                document.querySelector('.tabs .tab:first-child').classList.add('active');
                document.getElementById('loginForm').style.display = 'block';
                document.getElementById('registerForm').style.display = 'none';
            } else {
                document.querySelector('.tabs .tab:last-child').classList.add('active');
                document.getElementById('loginForm').style.display = 'none';
                document.getElementById('registerForm').style.display = 'block';
            }
        }

        function login() {
            const id = document.getElementById('loginId').value.trim();
            const pass = document.getElementById('loginPass').value.trim();
            if (!id || !pass) return toastMsg('املأ جميع الحقول', 'err');

            const users = JSON.parse(localStorage.getItem('evilUsers') || '[]');
            const found = users.find(u => (u.phone === id || u.email === id) && u.password === pass);

            if (found) {
                currentUser = found;
                localStorage.setItem('evilUser', JSON.stringify(currentUser));
                showApp();
                toastMsg('👋 مرحباً ' + currentUser.name);
            } else {
                toastMsg('❌ بيانات خاطئة', 'err');
            }
        }

        function register() {
            const name = document.getElementById('regName').value.trim();
            const email = document.getElementById('regEmail').value.trim();
            const phone = document.getElementById('regPhone').value.trim();
            const pass = document.getElementById('regPass').value.trim();

            if (!name || !email || !pass) return toastMsg('املأ الحقول المطلوبة', 'err');
            if (pass.length < 8) return toastMsg('كلمة المرور 8 أحرف على الأقل', 'err');

            let users = JSON.parse(localStorage.getItem('evilUsers') || '[]');
            if (users.find(u => u.email === email)) return toastMsg('البريد مستخدم', 'err');
            if (phone && users.find(u => u.phone === phone)) return toastMsg('الهاتف مستخدم', 'err');

            const user = { name, email, phone, password: pass, role: 'user' };
            users.push(user);
            localStorage.setItem('evilUsers', JSON.stringify(users));
            currentUser = user;
            localStorage.setItem('evilUser', JSON.stringify(user));
            showApp();
            toastMsg('✅ تم إنشاء الحساب');
        }

        function googleLogin() {
            const email = prompt('أدخل بريد Google:');
            if (email) {
                let users = JSON.parse(localStorage.getItem('evilUsers') || '[]');
                let u = users.find(x => x.email === email);
                if (!u) { u = { name: email.split('@')[0], email, phone: '', password: '', role: 'user', google: true }; users.push(u); localStorage.setItem('evilUsers', JSON.stringify(users)); }
                currentUser = u;
                localStorage.setItem('evilUser', JSON.stringify(currentUser));
                showApp();
                toastMsg('👋 ' + u.name);
            }
        }

        function sendOTP() {
            const phone = document.getElementById('loginId').value.trim();
            if (!phone) return toastMsg('أدخل رقم الهاتف', 'err');
            otpCode = String(Math.floor(100000 + Math.random() * 900000));
            localStorage.setItem('evilOTP', otpCode);
            document.getElementById('otpSection').classList.add('show');
            document.getElementById('loginForm').style.display = 'none';
            document.getElementById('registerForm').style.display = 'none';
            document.querySelector('.tabs').style.display = 'none';
            document.getElementById('o1').focus();
            otpSeconds = 120;
            updateTimer();
            if (otpTimer) clearInterval(otpTimer);
            otpTimer = setInterval(() => { otpSeconds--; updateTimer(); if (otpSeconds <= 0) { clearInterval(otpTimer); document.getElementById('btnResendOtp').disabled = false; document.getElementById('otpTimer').classList.add('expired'); document.getElementById('otpTimer').textContent = 'انتهت'; } }, 1000);
            document.getElementById('btnResendOtp').disabled = true;
            console.log('OTP:', otpCode);
            toastMsg('📱 رمز التحقق: ' + otpCode);
        }

        function updateTimer() {
            document.getElementById('otpTimer').textContent = String(Math.floor(otpSeconds / 60)).padStart(2, '0') + ':' + String(otpSeconds % 60).padStart(2, '0');
        }

        function nextOtp(input) { if (input.value.length === 1) { const n = input.nextElementSibling; if (n) n.focus(); } }

        function verifyOTP() {
            const code = ['o1', 'o2', 'o3', 'o4', 'o5', 'o6'].map(id => document.getElementById(id).value).join('');
            if (code === localStorage.getItem('evilOTP')) {
                clearInterval(otpTimer);
                const phone = document.getElementById('loginId').value.trim();
                let users = JSON.parse(localStorage.getItem('evilUsers') || '[]');
                let u = users.find(x => x.phone === phone);
                if (!u) { u = { name: 'مستخدم', email: '', phone, password: '', role: 'user' }; users.push(u); localStorage.setItem('evilUsers', JSON.stringify(users)); }
                currentUser = u;
                localStorage.setItem('evilUser', JSON.stringify(currentUser));
                showApp();
                toastMsg('✅ تم التحقق');
            } else { toastMsg('❌ رمز خاطئ', 'err'); }
        }

        function doLogout() {
            currentUser = null;
            localStorage.removeItem('evilUser');
            document.getElementById('mainApp').classList.remove('show');
            document.getElementById('mainApp').style.display = 'none';
            document.getElementById('authPage').style.display = 'flex';
            document.getElementById('loginForm').style.display = 'block';
            document.getElementById('registerForm').style.display = 'none';
            document.getElementById('otpSection').classList.remove('show');
            document.querySelector('.tabs').style.display = 'flex';
            toastMsg('👋 تم الخروج');
        }

        // ==================== SHOW APP ====================
        function showApp() {
            document.getElementById('authPage').style.display = 'none';
            document.getElementById('mainApp').classList.add('show');
            document.getElementById('mainApp').style.display = 'block';
            document.getElementById('navUser').textContent = currentUser.name;
            if (currentUser.role === 'super_admin') document.getElementById('dashLink').style.display = 'inline';
            updateCart();
            goPage('home');
        }

        // ==================== PAGES ====================
        function goPage(page) {
            const c = document.getElementById('pageContent');
            switch (page) {
                case 'home': c.innerHTML = homePage(); break;
                case 'menu': c.innerHTML = productsPage(PRODUCTS, '📋 المنيو'); break;
                case 'drinks': c.innerHTML = productsPage(PRODUCTS.filter(p => ['hot', 'cold'].includes(p.cat)), '🥤 مشروبات'); break;
                case 'alcohol': c.innerHTML = productsPage(PRODUCTS.filter(p => p.cat === 'alcohol'), '🍺 خمور'); break;
                case 'food': c.innerHTML = productsPage(PRODUCTS.filter(p => p.cat === 'food'), '🍰 حلويات'); break;
                case 'reserve': c.innerHTML = reservePage(); break;
                case 'profile': c.innerHTML = profilePage(); break;
                case 'dashboard': c.innerHTML = currentUser.role === 'super_admin' ? dashboardPage() : '<p style="text-align:center;padding:80px;">⛔ غير مصرح</p>'; break;
            }
            document.querySelectorAll('.nav-links a').forEach(l => l.classList.remove('active'));
            window.scrollTo(0, 0);
            AOS.refresh();
        }

        function homePage() {
            const f = PRODUCTS.filter(p => [1,3,7,9,11,14,16,18,20].includes(p.id));
            return `
                <div class="hero"><div><h1>EVIL BAR</h1><p>✦ أفخم كافيه وبار ✦</p>
                <button class="btn btn-gold" style="width:auto;display:inline-flex;padding:14px 28px;font-size:16px;" onclick="goPage('menu')">📋 المنيو</button>
                <button class="btn btn-outline" style="width:auto;display:inline-flex;padding:14px 28px;font-size:16px;margin-right:10px;" onclick="goPage('reserve')">📅 حجز</button></div></div>
                <div class="section"><h2 class="section-title"><span class="gold-text">منتجات</span> مميزة</h2>
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
                    <div class="product-body"><h5>${p.name}</h5><p class="desc">${p.desc}</p><div>${p.disc?`<span class="price-old">${p.price}ج.م</span>`:''}<span class="price">${pr} ج.م</span></div>
                    <div class="stars">${'★'.repeat(Math.floor(p.rating))} ${p.rating}</div>
                    <button class="btn-add" onclick="addToCart(${p.id})">🛒 أضف للسلة</button></div>
                </div>`;
        }

        function reservePage() {
            return `<div class="section"><div style="max-width:500px;margin:0 auto;background:#111;border:1px solid rgba(212,175,55,0.3);border-radius:20px;padding:30px;">
                <h3 style="color:var(--gold);text-align:center;">📅 حجز</h3><input class="inp" placeholder="الأشخاص"><input class="inp" type="date"><input class="inp" type="time">
                <button class="btn btn-gold" onclick="toastMsg('✅ تم')">تأكيد</button></div></div>`;
        }

        function profilePage() {
            return `<div class="section"><div style="max-width:500px;margin:0 auto;background:#111;border:1px solid rgba(212,175,55,0.3);border-radius:20px;padding:30px;">
                <h3 style="color:var(--gold);">👤 ${currentUser.name}</h3><p>📧 ${currentUser.email||'-'}</p><p>📱 ${currentUser.phone||'-'}</p></div></div>`;
        }

        function dashboardPage() {
            const users = JSON.parse(localStorage.getItem('evilUsers') || '[]');
            const payments = JSON.parse(localStorage.getItem('evilPayments') || '[]');
            const pending = payments.filter(p => p.status === 'قيد المراجعة');
            const rev = payments.filter(p => p.status === 'مكتمل').reduce((s,p) => s+p.amount, 0);
            return `<div class="section"><h2 class="section-title">📊 <span class="gold-text">لوحة التحكم</span></h2>
                <p style="text-align:center;color:var(--gold);">👑 ${currentUser.name}</p>
                <div class="stat-grid" style="max-width:1000px;margin:0 auto 20px;">
                    <div class="stat-box"><h3>${users.length}</h3><p>👥 مستخدمين</p></div>
                    <div class="stat-box"><h3>${payments.length}</h3><p>💳 مدفوعات</p></div>
                    <div class="stat-box"><h3>${rev} ج.م</h3><p>💰 إيرادات</p></div>
                    <div class="stat-box" style="border-color:var(--orange);"><h3 style="color:var(--orange);">${pending.length}</h3><p>⏳ مراجعة</p></div>
                </div>
                <div style="max-width:1000px;margin:0 auto;">
                    <button class="btn btn-gold" style="width:auto;display:inline-flex;margin:3px;" onclick="addProd()">➕ منتج</button>
                    <button class="btn btn-outline" style="width:auto;display:inline-flex;margin:3px;" onclick="editProd()">✏️ تعديل</button>
                    <button class="btn" style="width:auto;display:inline-flex;margin:3px;background:var(--red);color:#fff;" onclick="delProd()">🗑 حذف</button>
                </div>
                ${pending.length>0?`<div style="max-width:1000px;margin:20px auto;background:rgba(243,156,18,0.1);border:1px solid var(--orange);border-radius:15px;padding:20px;">
                    <h4 style="color:var(--orange);">⏳ طلبات للمراجعة</h4>
                    ${pending.map(p=>`<div style="background:#111;padding:12px;border-radius:10px;margin:8px 0;display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:8px;">
                        <div><strong>${p.userName}</strong> | ${p.amount}ج.م<br><small>من: ${p.senderPhone||'?'} | ${p.date}</small></div>
                        <div><button class="btn" style="width:auto;padding:6px 12px;font-size:11px;background:var(--green);color:#fff;margin:2px;" onclick="approvePay(${p.id})">✅ قبول</button>
                        <button class="btn" style="width:auto;padding:6px 12px;font-size:11px;background:var(--red);color:#fff;margin:2px;" onclick="rejectPay(${p.id})">❌ رفض</button></div>
                    </div>`).join('')}</div>`:''}
                <h4 style="color:var(--gold);margin:20px 0;">💳 المدفوعات</h4>
                <div style="overflow-x:auto;max-width:1000px;margin:0 auto;"><table><tr><th>#</th><th>عميل</th><th>طريقة</th><th>مبلغ</th><th>حالة</th><th>تاريخ</th></tr>
                ${payments.length===0?'<tr><td colspan="6">لا يوجد</td></tr>':payments.reverse().slice(0,15).map(p=>`<tr><td>${p.id}</td><td>${p.userName}</td><td>${p.method}</td><td style="color:var(--gold);">${p.amount}ج.م</td><td><span class="status-${p.status==='مكتمل'?'done':p.status==='مرفوض'?'no':'review'}">${p.status}</span></td><td>${p.date}</td></tr>`).join('')}</table></div></div>`;
        }

        function approvePay(id) { let p=JSON.parse(localStorage.getItem('evilPayments')||'[]'); const i=p.findIndex(x=>x.id===id); if(i>-1){p[i].status='مكتمل';localStorage.setItem('evilPayments',JSON.stringify(p));goPage('dashboard');toastMsg('✅ تم القبول');} }
        function rejectPay(id) { let p=JSON.parse(localStorage.getItem('evilPayments')||'[]'); const i=p.findIndex(x=>x.id===id); if(i>-1){p[i].status='مرفوض';localStorage.setItem('evilPayments',JSON.stringify(p));goPage('dashboard');toastMsg('❌ تم الرفض');} }
        function addProd() { const n=prompt('اسم المنتج:'); if(!n)return; const c=prompt('فئة (hot/cold/food/alcohol):','hot'); const pr=parseInt(prompt('سعر:','50')); PRODUCTS.push({id:Date.now(),name:n,cat:c,price:pr,disc:null,rating:5,img:'https://via.placeholder.com/400x200/111/d4af37?text='+n,desc:'جديد'}); goPage('dashboard'); toastMsg('✅ تم'); }
        function editProd() { const list=PRODUCTS.map((p,i)=>`${i+1}. ${p.name}`).join('\n'); const idx=parseInt(prompt('رقم:\n'+list)); if(!idx||idx<1||idx>PRODUCTS.length)return; const p=PRODUCTS[idx-1]; p.name=prompt('اسم:',p.name)||p.name; p.price=parseInt(prompt('سعر:',p.price))||p.price; goPage('dashboard'); toastMsg('✅ تم'); }
        function delProd() { const list=PRODUCTS.map((p,i)=>`${i+1}. ${p.name}`).join('\n'); const idx=parseInt(prompt('رقم:\n'+list)); if(!idx||idx<1||idx>PRODUCTS.length)return; PRODUCTS.splice(idx-1,1); goPage('dashboard'); toastMsg('🗑 تم'); }

        // ==================== CART ====================
        function addToCart(id) { const p=PRODUCTS.find(x=>x.id===id); if(!p)return; const ex=cart.find(i=>i.productId===id); if(ex)ex.qty++; else cart.push({productId:id,qty:1,price:p.disc||p.price,name:p.name,img:p.img}); saveCart(); toastMsg('✅ '+p.name); }
        function removeCart(i){cart.splice(i,1);saveCart();}
        function qtyCart(i,d){cart[i].qty+=d;if(cart[i].qty<=0)cart.splice(i,1);saveCart();}
        function clearCart(){cart=[];saveCart();toastMsg('🗑 تم');}
        function saveCart(){localStorage.setItem('evilCart',JSON.stringify(cart));updateCart();}
        function updateCart(){
            const cnt=cart.reduce((s,i)=>s+i.qty,0),tot=cart.reduce((s,i)=>s+(i.price*i.qty),0);
            document.getElementById('cartBadge').textContent=cnt;
            document.getElementById('cartTotal').textContent=tot+' ج.م';
            document.getElementById('visaAmt').textContent=tot+' ج.م';
            document.getElementById('vodAmt').textContent=tot+' ج.م';
            const l=document.getElementById('cartItemsList');
            if(cart.length===0)l.innerHTML='<p style="color:#888;">فارغة</p>';
            else l.innerHTML=cart.map((item,i)=>`<div style="display:flex;align-items:center;gap:8px;padding:8px;background:#1a1a1a;border-radius:8px;margin-bottom:6px;"><img src="${item.img}" width="35" style="border-radius:5px;"><div style="flex:1;"><strong>${item.name}</strong><br><small style="color:var(--gold);">${item.price}ج.م × ${item.qty}</small></div><button onclick="qtyCart(${i},-1)" style="background:rgba(255,255,255,0.1);color:#fff;border:none;padding:3px 7px;border-radius:4px;cursor:pointer;">-</button><span>${item.qty}</span><button onclick="qtyCart(${i},1)" style="background:rgba(255,255,255,0.1);color:#fff;border:none;padding:3px 7px;border-radius:4px;cursor:pointer;">+</button><button onclick="removeCart(${i})" style="background:var(--red);color:#fff;border:none;padding:3px 7px;border-radius:4px;cursor:pointer;">🗑</button></div>`).join('');
        }
        function toggleCart(){document.getElementById('cartSidebar').classList.toggle('open');document.getElementById('cartOverlay').classList.toggle('open');}

        // ==================== PAYMENT ====================
        function openPayment(){if(cart.length===0)return toastMsg('سلة فارغة','err');const t=cart.reduce((s,i)=>s+(i.price*i.qty),0);document.getElementById('visaAmt').textContent=t+' ج.م';document.getElementById('vodAmt').textContent=t+' ج.م';document.getElementById('payModal').classList.add('open');}
        function closePayment(){document.getElementById('payModal').classList.remove('open');scrFile=null;document.getElementById('scrPreview').style.display='none';document.getElementById('scrFile').value='';document.getElementById('visaErrors').style.display='none';}
        function switchPay(t){document.querySelectorAll('#payModal .tab').forEach(x=>x.classList.remove('active'));document.getElementById('payVisa').style.display=t==='visa'?'block':'none';document.getElementById('payVodafone').style.display=t==='vodafone'?'block':'none';if(t==='visa')document.querySelector('#payModal .tab:first-child').classList.add('active');else document.querySelector('#payModal .tab:last-child').classList.add('active');}
        function formatCard(i){let v=i.value.replace(/\D/g,'').substring(0,16);i.value=v.replace(/(\d{4})(?=\d)/g,'$1 ');}

        function luhnCheck(num){let s=0,alt=false;for(let i=num.length-1;i>=0;i--){let d=parseInt(num[i]);if(alt){d*=2;if(d>9)d-=9;}s+=d;alt=!alt;}return s%10===0;}
        function isBadBIN(bin){return['411111','424242','400000','555555','601100','123456','000000','999999','111111'].some(b=>bin.startsWith(b));}
        function isFake(num){if(/^(\d)\1+$/.test(num))return true;if('0123456789'.includes(num.substring(0,6)))return true;return['4111111111111111','4242424242424242','5555555555554444'].includes(num);}

        function validateVisa(){
            const n=document.getElementById('cardName').value.trim();
            const num=document.getElementById('cardNum').value.replace(/\s/g,'');
            const exp=document.getElementById('cardExp').value.trim();
            const cvv=document.getElementById('cardCVV').value.trim();
            const errDiv=document.getElementById('visaErrors');
            let errs=[];
            document.querySelectorAll('#payVisa .inp').forEach(i=>i.classList.remove('error'));
            if(!n||n.length<3){errs.push('❌ اسم حامل البطاقة غير صالح');document.getElementById('cardName').classList.add('error');}
            if(!luhnCheck(num)){errs.push('❌ فشل اختبار Luhn - بطاقة غير صالحة');document.getElementById('cardNum').classList.add('error');}
            if(isBadBIN(num.substring(0,6))){errs.push('⚠️ BIN في القائمة السوداء');document.getElementById('cardNum').classList.add('error');}
            if(isFake(num)){errs.push('🚫 بطاقة وهمية مكتشفة');document.getElementById('cardNum').classList.add('error');}
            if(num.length<13||num.length>19){errs.push('❌ طول رقم البطاقة غير صحيح');document.getElementById('cardNum').classList.add('error');}
            if(!exp||!exp.match(/^\d{2}\/\d{2}$/)){errs.push('❌ تاريخ انتهاء غير صالح');document.getElementById('cardExp').classList.add('error');}
            else{const[mm,yy]=exp.split('/');if(new Date(2000+parseInt(yy),parseInt(mm))<new Date()){errs.push('❌ البطاقة منتهية');document.getElementById('cardExp').classList.add('error');}}
            if(!cvv||cvv.length<3){errs.push('❌ CVV غير صالح');document.getElementById('cardCVV').classList.add('error');}
            if(errs.length>0){errDiv.innerHTML=errs.join('<br>');errDiv.style.display='block';return;}
            completePay('💳 فيزا');
        }

        function submitVodafone(){
            const ph=document.getElementById('senderPhone').value.trim();
            const nm=document.getElementById('senderName').value.trim();
            if(!ph){toastMsg('⚠️ أدخل رقم هاتفك','err');return;}
            if(!nm){toastMsg('⚠️ أدخل اسمك','err');return;}
            if(!scrFile){toastMsg('⚠️ ارفع سكرين شوت','err');return;}
            if(ph==='01026966717'){toastMsg('⚠️ لا تستخدم نفس الرقم','err');return;}
            const t=cart.reduce((s,i)=>s+(i.price*i.qty),0);
            const pay={id:Date.now(),userName:currentUser?.name||'زائر',userPhone:currentUser?.phone||'',senderPhone:ph,senderName:nm,method:'
