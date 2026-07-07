<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Evil Bar - إيفل بار | Luxury Cafe & Bar</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.rtl.min.css" rel="stylesheet">
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" rel="stylesheet">
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">
    <style>
        :root {
            --bg: #04000d; --bg2: #0a001a; --bg3: #120026;
            --purple: #8B5CF6; --purple2: #A78BFA; --purple3: #C4B5FD;
            --purple-dark: #6D28D9; --purple-deep: #4C1D95;
            --white: #fff; --gray: #999; --gray2: #666;
            --red: #ef4444; --green: #10b981; --orange: #f59e0b;
            --glass: rgba(15,10,35,0.85); --border-purple: rgba(139,92,246,0.3);
            --shadow-purple: 0 0 40px rgba(139,92,246,0.4);
            --shadow-purple2: 0 0 80px rgba(139,92,246,0.6);
            --shadow-purple3: 0 0 120px rgba(139,92,246,0.8);
            --glow-purple: 0 0 20px rgba(139,92,246,0.8), 0 0 40px rgba(139,92,246,0.6), 0 0 80px rgba(139,92,246,0.4);
            --glow-text: 0 0 10px rgba(167,139,250,0.8), 0 0 30px rgba(167,139,250,0.6), 0 0 60px rgba(167,139,250,0.4);
            --radius: 18px;
            --transition: all 0.35s cubic-bezier(0.4,0,0.2,1);
        }
        * { margin:0; padding:0; box-sizing:border-box; }
        body {
            background: var(--bg); color: var(--white);
            font-family: 'Segoe UI', Tahoma, sans-serif; min-height: 100vh;
            overflow-x: hidden;
        }

        /* ============ NEON GLOW PARTICLES ============ */
        #particlesCanvas { position:fixed; top:0; left:0; width:100%; height:100%; z-index:0; pointer-events:none; }

        /* ============ AUTH PAGE ============ */
        #authPage {
            display: flex; min-height: 100vh; align-items: center;
            justify-content: center; padding: 20px; position: relative; z-index: 1;
        }
        .auth-card {
            background: var(--glass); backdrop-filter: blur(40px);
            -webkit-backdrop-filter: blur(40px);
            border: 2px solid var(--border-purple); border-radius: var(--radius);
            padding: 40px 30px; width: 100%; max-width: 440px;
            box-shadow: var(--shadow-purple3), inset 0 0 60px rgba(139,92,246,0.05);
            animation: cardGlow 3s ease-in-out infinite, slideIn 0.6s ease;
        }
        @keyframes cardGlow {
            0%,100% { box-shadow: var(--shadow-purple2), inset 0 0 60px rgba(139,92,246,0.05); }
            50% { box-shadow: var(--shadow-purple3), inset 0 0 100px rgba(139,92,246,0.1); }
        }
        @keyframes slideIn {
            from { opacity:0; transform:translateY(40px) scale(0.9); }
            to { opacity:1; transform:translateY(0) scale(1); }
        }

        .auth-logo {
            text-align: center; margin-bottom: 30px;
        }
        .auth-icon {
            font-size: 60px; animation: floatIcon 3s ease-in-out infinite;
            filter: drop-shadow(0 0 20px rgba(139,92,246,0.8));
        }
        @keyframes floatIcon {
            0%,100% { transform:translateY(0); }
            50% { transform:translateY(-12px); }
        }
        .auth-title {
            font-size: 40px; font-weight: 900;
            background: linear-gradient(135deg, #6D28D9, #8B5CF6, #A78BFA, #C4B5FD, #A78BFA, #8B5CF6);
            background-size: 400% 400%;
            -webkit-background-clip: text; -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: shimmer 3s ease infinite;
            letter-spacing: 6px;
            text-shadow: none;
            filter: drop-shadow(0 0 15px rgba(139,92,246,0.6));
        }
        @keyframes shimmer {
            0%,100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }
        .auth-subtitle {
            color: var(--purple3); font-size: 14px; margin-top: 8px;
            letter-spacing: 3px; text-shadow: var(--glow-text);
        }

        /* Form */
        .form-group { margin-bottom: 18px; }
        .form-label {
            display: block; margin-bottom: 6px; color: var(--purple3);
            font-size: 13px; font-weight: 600; letter-spacing: 1px;
        }
        .form-input {
            width: 100%; padding: 15px 18px;
            background: rgba(139,92,246,0.05);
            border: 2px solid rgba(139,92,246,0.2);
            border-radius: 14px; color: var(--white); font-size: 16px;
            transition: var(--transition); font-family: 'Segoe UI', Tahoma, sans-serif;
        }
        .form-input:focus {
            outline: none; border-color: var(--purple2);
            box-shadow: 0 0 25px rgba(139,92,246,0.3), inset 0 0 15px rgba(139,92,246,0.05);
            background: rgba(139,92,246,0.08);
        }
        .form-input::placeholder { color: rgba(167,139,250,0.3); }

        /* Buttons */
        .btn {
            width: 100%; padding: 15px; border: none; border-radius: 14px;
            font-size: 16px; font-weight: 700; cursor: pointer; transition: var(--transition);
            display: flex; align-items: center; justify-content: center; gap: 10px;
            margin-bottom: 10px; font-family: 'Segoe UI', Tahoma, sans-serif;
            letter-spacing: 1px; position: relative; overflow: hidden;
        }
        .btn-purple {
            background: linear-gradient(135deg, #4C1D95, #6D28D9, #8B5CF6, #A78BFA);
            background-size: 300% 300%;
            color: #fff; animation: btnGlow 3s ease infinite;
            box-shadow: 0 0 30px rgba(139,92,246,0.4);
        }
        @keyframes btnGlow {
            0%,100% { background-position: 0% 50%; box-shadow: 0 0 30px rgba(139,92,246,0.4); }
            50% { background-position: 100% 50%; box-shadow: 0 0 60px rgba(139,92,246,0.8); }
        }
        .btn-purple::after {
            content: ''; position: absolute; top: -50%; left: -50%;
            width: 200%; height: 200%;
            background: linear-gradient(45deg, transparent 30%, rgba(255,255,255,0.3) 50%, transparent 70%);
            animation: btnShine 2.5s infinite;
        }
        @keyframes btnShine {
            0% { transform: translateX(-100%) rotate(45deg); }
            100% { transform: translateX(100%) rotate(45deg); }
        }
        .btn-purple:hover {
            transform: translateY(-4px);
            box-shadow: 0 0 60px rgba(139,92,246,0.9), 0 10px 30px rgba(0,0,0,0.5);
        }
        .btn-outline {
            background: transparent; border: 2px solid var(--border-purple);
            color: var(--purple2);
        }
        .btn-outline:hover {
            background: rgba(139,92,246,0.1);
            border-color: var(--purple2);
            box-shadow: 0 0 30px rgba(139,92,246,0.3);
        }
        .btn-red { background: linear-gradient(135deg, #dc2626, #ef4444); color: #fff; }
        .btn-green { background: linear-gradient(135deg, #059669, #10b981); color: #fff; }
        .btn-sm { width: auto; padding: 8px 18px; font-size: 13px; }

        /* OTP */
        .otp-section { display: none; animation: fadeIn 0.4s ease; }
        .otp-section.show { display: block; }
        @keyframes fadeIn { from{opacity:0;transform:translateY(-15px)} to{opacity:1;transform:translateY(0)} }
        .otp-inputs { display: flex; gap: 10px; justify-content: center; margin: 20px 0; }
        .otp-inputs input {
            width: 50px; height: 55px; text-align: center; font-size: 24px; font-weight: 700;
            background: rgba(139,92,246,0.05); border: 2px solid rgba(139,92,246,0.2);
            border-radius: 12px; color: var(--purple2); transition: var(--transition);
        }
        .otp-inputs input:focus {
            outline: none; border-color: var(--purple2);
            box-shadow: 0 0 20px rgba(139,92,246,0.4);
        }
        .timer-text {
            text-align: center; color: var(--purple2); font-weight: 700;
            font-size: 18px; margin: 12px 0; text-shadow: var(--glow-text);
        }
        .timer-text.expired { color: var(--red); }

        /* Main App */
        #mainApp { display: none; position: relative; z-index: 1; }
        #mainApp.show { display: block; animation: fadeIn 0.5s ease; }

        /* Top Bar */
        .top-bar {
            background: rgba(4,0,13,0.95); border-bottom: 1px solid rgba(139,92,246,0.15);
            padding: 10px 20px; display: flex; align-items: center;
            justify-content: space-between; font-size: 12px; color: var(--purple3);
        }
        .dots { display: flex; gap: 7px; }
        .dot { width: 9px; height: 9px; border-radius: 50%; cursor: pointer; transition: 0.2s; }
        .dot:hover { transform: scale(1.5); box-shadow: 0 0 15px currentColor; }
        .dot.r { background: var(--red); box-shadow: 0 0 10px var(--red); }
        .dot.o { background: var(--orange); box-shadow: 0 0 10px var(--orange); }
        .dot.g { background: var(--green); box-shadow: 0 0 10px var(--green); }

        /* Menu Dropdown */
        .menu-drop { position: relative; }
        .menu-btn {
            background: rgba(139,92,246,0.1); border: 1px solid var(--border-purple);
            color: var(--purple2); font-size: 22px; cursor: pointer;
            padding: 8px 14px; border-radius: 10px; transition: var(--transition);
        }
        .menu-btn:hover { background: rgba(139,92,246,0.2); box-shadow: 0 0 20px rgba(139,92,246,0.3); }
        .menu-content {
            display: none; position: absolute; top: 45px; right: 0;
            background: rgba(15,10,35,0.98); border: 1px solid var(--border-purple);
            border-radius: 14px; padding: 8px; z-index: 200; min-width: 200px;
            box-shadow: var(--shadow-purple2); backdrop-filter: blur(30px);
        }
        .menu-content.show { display: block; animation: fadeIn 0.2s ease; }
        .menu-content a {
            display: block; padding: 11px 16px; color: var(--white);
            text-decoration: none; border-radius: 10px; font-size: 14px;
            cursor: pointer; transition: var(--transition);
        }
        .menu-content a:hover {
            background: rgba(139,92,246,0.2); color: var(--purple2);
            text-shadow: var(--glow-text);
        }

        /* Navbar */
        .navbar-ev {
            background: rgba(4,0,13,0.9); backdrop-filter: blur(30px);
            border-bottom: 1px solid rgba(139,92,246,0.1);
            padding: 14px 20px; position: sticky; top: 0; z-index: 100;
            display: flex; align-items: center; justify-content: space-between;
            flex-wrap: wrap; gap: 12px;
        }
        .brand {
            display: flex; align-items: center; gap: 10px;
            color: var(--purple2); font-size: 24px; font-weight: 900;
            text-decoration: none; letter-spacing: 4px; cursor: pointer;
            text-shadow: var(--glow-text); transition: var(--transition);
        }
        .brand:hover { color: var(--purple3); text-shadow: 0 0 30px rgba(167,139,250,1); }
        .brand-icon {
            font-size: 32px; animation: floatIcon 3s ease-in-out infinite;
            filter: drop-shadow(0 0 15px rgba(139,92,246,0.8));
        }
        .nav-actions { display: flex; align-items: center; gap: 10px; }
        .cart-btn {
            position: relative; background: rgba(139,92,246,0.15);
            border: 1px solid var(--border-purple); color: var(--purple2);
            padding: 10px 18px; border-radius: 50px; cursor: pointer;
            font-weight: 600; font-size: 14px; transition: var(--transition);
        }
        .cart-btn:hover {
            background: var(--purple); color: #fff;
            box-shadow: 0 0 30px rgba(139,92,246,0.5);
        }
        .cart-badge {
            position: absolute; top: -7px; right: -7px;
            background: var(--purple2); color: #000; border-radius: 50%;
            width: 22px; height: 22px; font-size: 11px;
            display: flex; align-items: center; justify-content: center;
            font-weight: 900; animation: badgePop 0.3s ease;
        }
        @keyframes badgePop {
            0% { transform: scale(0); }
            50% { transform: scale(1.4); }
            100% { transform: scale(1); }
        }

        /* Hero */
        .hero {
            min-height: 85vh; display: flex; align-items: center; justify-content: center;
            text-align: center; position: relative;
            background: radial-gradient(ellipse at center, rgba(139,92,246,0.08) 0%, transparent 70%);
        }
        .hero::before {
            content: ''; position: absolute; top: 50%; left: 50%;
            transform: translate(-50%, -50%);
            width: 500px; height: 500px;
            background: radial-gradient(circle, rgba(139,92,246,0.15) 0%, transparent 70%);
            animation: heroGlow 4s ease-in-out infinite;
        }
        @keyframes heroGlow {
            0%,100% { transform: translate(-50%, -50%) scale(1); opacity: 0.5; }
            50% { transform: translate(-50%, -50%) scale(1.3); opacity: 1; }
        }
        .hero h1 {
            font-size: clamp(50px, 10vw, 100px); font-weight: 900;
            background: linear-gradient(135deg, #4C1D95, #8B5CF6, #A78BFA, #C4B5FD, #A78BFA);
            background-size: 400% 400%;
            -webkit-background-clip: text; -webkit-text-fill-color: transparent;
            background-clip: text; animation: shimmer 4s ease infinite;
            letter-spacing: 10px; position: relative; z-index: 1;
            filter: drop-shadow(0 0 30px rgba(139,92,246,0.6));
        }
        .hero p {
            font-size: 20px; color: var(--purple3); margin: 20px 0 30px;
            position: relative; z-index: 1; letter-spacing: 3px;
        }
        .hero-btns {
            display: flex; gap: 15px; justify-content: center;
            flex-wrap: wrap; position: relative; z-index: 1;
        }
        .hero-btn {
            padding: 16px 36px; border-radius: 50px; font-size: 16px;
            font-weight: 700; cursor: pointer; transition: var(--transition);
            text-decoration: none; display: inline-flex; align-items: center;
            gap: 10px; letter-spacing: 1px;
        }
        .hero-btn-primary {
            background: linear-gradient(135deg, #4C1D95, #8B5CF6, #A78BFA);
            background-size: 300% 300%;
            color: #fff; border: none; animation: btnGlow 3s ease infinite;
        }
        .hero-btn-primary:hover {
            transform: translateY(-5px);
            box-shadow: 0 0 60px rgba(139,92,246,0.8), 0 15px 40px rgba(0,0,0,0.5);
        }
        .hero-btn-outline {
            background: transparent; border: 2px solid var(--purple2);
            color: var(--purple2); box-shadow: 0 0 20px rgba(139,92,246,0.3);
        }
        .hero-btn-outline:hover {
            background: var(--purple2); color: #000;
            transform: translateY(-5px); box-shadow: 0 0 60px rgba(139,92,246,0.8);
        }

        /* Sections */
        .section { padding: 70px 20px; position: relative; }
        .section-title {
            text-align: center; font-size: 34px; font-weight: 900;
            margin-bottom: 40px; letter-spacing: 2px;
        }
        .section-title .hl {
            color: var(--purple2); text-shadow: var(--glow-text);
        }
        .section-title::after {
            content: ''; display: block; width: 70px; height: 4px;
            background: linear-gradient(90deg, transparent, var(--purple2), transparent);
            margin: 15px auto 0; border-radius: 2px;
        }

        /* Products */
        .products-grid {
            display: grid; grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 20px; max-width: 1100px; margin: 0 auto;
        }
        .product-card {
            background: rgba(15,10,35,0.9); border: 1px solid rgba(139,92,246,0.1);
            border-radius: 18px; overflow: hidden; transition: var(--transition);
            position: relative;
        }
        .product-card::before {
            content: ''; position: absolute; top: 0; left: 0; right: 0; bottom: 0;
            background: linear-gradient(135deg, rgba(139,92,246,0.05), transparent);
            opacity: 0; transition: var(--transition); border-radius: 18px;
        }
        .product-card:hover::before { opacity: 1; }
        .product-card:hover {
            transform: translateY(-8px);
            border-color: var(--purple2);
            box-shadow: 0 20px 50px rgba(0,0,0,0.5), 0 0 40px rgba(139,92,246,0.3);
        }
        .product-img { height: 210px; overflow: hidden; position: relative; }
        .product-img img {
            width: 100%; height: 100%; object-fit: cover;
            transition: transform 0.6s ease;
        }
        .product-card:hover .product-img img { transform: scale(1.12); }
        .badge-disc {
            position: absolute; top: 10px; left: 10px;
            background: var(--red); color: #fff; padding: 4px 12px;
            border-radius: 20px; font-size: 11px; font-weight: 700;
            box-shadow: 0 0 15px rgba(239,68,68,0.5);
        }
        .product-body { padding: 18px; }
        .product-body h5 { font-size: 17px; font-weight: 700; margin-bottom: 5px; }
        .product-body .desc { color: var(--gray); font-size: 12px; margin-bottom: 10px; }
        .price-row { display: flex; align-items: center; gap: 10px; margin-bottom: 8px; }
        .price-old { text-decoration: line-through; color: var(--gray2); font-size: 13px; }
        .price-current {
            color: var(--purple2); font-size: 22px; font-weight: 900;
            text-shadow: 0 0 10px rgba(139,92,246,0.4);
        }
        .stars { color: var(--orange); font-size: 13px; margin-bottom: 12px; }
        .btn-add {
            width: 100%; padding: 11px;
            background: linear-gradient(135deg, #6D28D9, #8B5CF6);
            color: #fff; border: none; border-radius: 12px;
            font-weight: 700; cursor: pointer; font-size: 14px;
            transition: var(--transition);
        }
        .btn-add:hover {
            box-shadow: 0 0 25px rgba(139,92,246,0.5);
            letter-spacing: 0.5px;
        }

        /* Cart */
        .cart-overlay {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.85); z-index: 2000; display: none;
            backdrop-filter: blur(5px);
        }
        .cart-overlay.open { display: block; }
        .cart-sidebar {
            position: fixed; top: 0; right: -420px; width: 400px; height: 100%;
            background: rgba(10,5,30,0.98); z-index: 2001;
            transition: right 0.35s cubic-bezier(0.4,0,0.2,1);
            border-left: 2px solid var(--border-purple); padding: 22px; overflow-y: auto;
            box-shadow: -10px 0 50px rgba(0,0,0,0.5);
        }
        .cart-sidebar.open { right: 0; }

        /* Modal */
        .modal-overlay {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.9); z-index: 3000; display: none;
            align-items: center; justify-content: center; backdrop-filter: blur(8px);
        }
        .modal-overlay.open { display: flex; }
        .modal-dialog {
            background: rgba(15,10,35,0.98); border: 2px solid var(--border-purple);
            border-radius: 22px; padding: 28px; width: 90%; max-width: 500px;
            max-height: 85vh; overflow-y: auto;
            box-shadow: var(--shadow-purple3);
            animation: modalIn 0.4s cubic-bezier(0.22,0.61,0.36,1);
        }
        @keyframes modalIn {
            from { opacity:0; transform:scale(0.9) translateY(30px); }
            to { opacity:1; transform:scale(1) translateY(0); }
        }

        /* Dashboard */
        .stat-grid {
            display: grid; grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 16px; margin-bottom: 25px;
        }
        .stat-box {
            background: rgba(15,10,35,0.9); border: 1px solid rgba(139,92,246,0.1);
            border-radius: 16px; padding: 24px; text-align: center;
            transition: var(--transition);
        }
        .stat-box:hover {
            border-color: var(--purple2);
            box-shadow: 0 0 30px rgba(139,92,246,0.3);
            transform: translateY(-3px);
        }
        .stat-box h2 { font-size: 36px; font-weight: 900; color: var(--purple2); text-shadow: var(--glow-text); }
        .stat-box p { color: var(--gray); margin-top: 5px; font-size: 14px; }

        table { width: 100%; border-collapse: collapse; font-size: 13px; }
        th {
            background: rgba(139,92,246,0.1); color: var(--purple2);
            padding: 12px; text-align: right; font-weight: 700;
            border-bottom: 2px solid var(--border-purple);
        }
        td { padding: 10px 12px; border-bottom: 1px solid rgba(255,255,255,0.04); }
        tr:hover td { background: rgba(139,92,246,0.05); }

        .status-p { background: var(--orange); color: #000; padding: 3px 10px; border-radius: 15px; font-size: 11px; font-weight: 700; }
        .status-a { background: var(--green); color: #fff; padding: 3px 10px; border-radius: 15px; font-size: 11px; font-weight: 700; }
        .status-r { background: var(--red); color: #fff; padding: 3px 10px; border-radius: 15px; font-size: 11px; font-weight: 700; }

        /* Toast */
        .toast-container {
            position: fixed; bottom: 25px; right: 25px; z-index: 9999;
            display: flex; flex-direction: column; gap: 10px;
        }
        .toast-item {
            background: rgba(15,10,35,0.98); border: 1px solid var(--border-purple);
            padding: 16px 22px; border-radius: 14px; color: #fff; font-weight: 600;
            font-size: 14px; animation: toastIn 0.4s ease;
            box-shadow: 0 10px 40px rgba(0,0,0,0.6), var(--shadow-purple);
            display: flex; align-items: center; gap: 10px; min-width: 280px;
        }
        .toast-item.success { border-right: 4px solid var(--green); }
        .toast-item.error { border-right: 4px solid var(--red); }
        @keyframes toastIn {
            from { opacity:0; transform: translateX(100px); }
            to { opacity:1; transform: translateX(0); }
        }

        footer {
            background: rgba(4,0,13,0.95); border-top: 1px solid rgba(139,92,246,0.1);
            padding: 35px 20px; text-align: center; color: var(--gray); font-size: 13px;
        }

        @media (max-width: 768px) {
            .hero h1 { font-size: 38px; letter-spacing: 5px; }
            .cart-sidebar { width: 100%; right: -100%; }
            .products-grid { grid-template-columns: repeat(auto-fill, minmax(155px, 1fr)); gap: 12px; }
            .product-img { height: 150px; }
        }
    </style>
</head>
<body>

    <canvas id="particlesCanvas"></canvas>
    <div class="toast-container" id="toastContainer"></div>

    <!-- ==================== AUTH PAGE ==================== -->
    <div id="authPage">
        <div class="auth-card">
            <div class="auth-logo">
                <div class="auth-icon">🔥</div>
                <h1 class="auth-title">EVIL BAR</h1>
                <p class="auth-subtitle">✦ أفخم كافيه وبار في المدينة ✦</p>
            </div>

            <div id="loginForm">
                <div class="form-group">
                    <label class="form-label">👤 اسم المستخدم</label>
                    <input type="text" class="form-input" id="loginUser" placeholder="أدخل اسم المستخدم" dir="ltr">
                </div>
                <div class="form-group">
                    <label class="form-label">🔒 كلمة المرور</label>
                    <input type="password" class="form-input" id="loginPass" placeholder="••••••••" dir="ltr">
                </div>
                <button class="btn btn-purple" onclick="doLogin()">
                    <i class="fas fa-sign-in-alt"></i> تسجيل الدخول
                </button>
                <p style="text-align:center;margin-top:10px;font-size:11px;color:var(--purple3);">
                    المدير: mostafaelsarnoby | 308191
                </p>
            </div>

            <div id="registerForm" style="display:none;">
                <div class="form-group">
                    <label class="form-label">👤 اسم المستخدم</label>
                    <input type="text" class="form-input" id="regUser" placeholder="اختر اسم مستخدم">
                </div>
                <div class="form-group">
                    <label class="form-label">👤 الاسم الكامل</label>
                    <input type="text" class="form-input" id="regName" placeholder="الاسم الكامل">
                </div>
                <div class="form-group">
                    <label class="form-label">📱 رقم الهاتف</label>
                    <input type="tel" class="form-input" id="regPhone" placeholder="01xxxxxxxxx" dir="ltr">
                    <small style="color:var(--purple3);font-size:10px;">سيصلك رمز تحقق واتساب</small>
                </div>
                <div class="form-group">
                    <label class="form-label">🔒 كلمة المرور</label>
                    <input type="password" class="form-input" id="regPass" placeholder="8 أحرف على الأقل">
                </div>
                <button class="btn btn-purple" onclick="sendOTP()">
                    <i class="fab fa-whatsapp"></i> إرسال رمز التحقق
                </button>

                <div class="otp-section" id="otpBox">
                    <p style="text-align:center;color:var(--purple3);font-size:13px;margin-top:12px;">أدخل رمز 6 أرقام</p>
                    <div class="otp-inputs">
                        <input type="text" maxlength="1" oninput="nextOtp(this)" id="o1">
                        <input type="text" maxlength="1" oninput="nextOtp(this)" id="o2">
                        <input type="text" maxlength="1" oninput="nextOtp(this)" id="o3">
                        <input type="text" maxlength="1" oninput="nextOtp(this)" id="o4">
                        <input type="text" maxlength="1" oninput="nextOtp(this)" id="o5">
                        <input type="text" maxlength="1" oninput="nextOtp(this)" id="o6">
                    </div>
                    <div class="timer-text" id="otpTimer">02:00</div>
                    <button class="btn btn-purple" onclick="verifyOTP()">✅ تأكيد الرمز</button>
                    <button class="btn btn-outline" id="btnReOTP" onclick="sendOTP()" disabled>🔄 إعادة</button>
                </div>

                <button class="btn btn-outline" style="margin-top:8px;" onclick="switchTab('login')">⬅ العودة للدخول</button>
            </div>

            <div style="text-align:center;margin-top:12px;">
                <span class="auth-link" onclick="switchTab('register')" id="showRegister" style="color:var(--purple2);cursor:pointer;font-weight:600;">📝 إنشاء حساب جديد</span>
                <span class="auth-link" onclick="switchTab('login')" id="showLogin" style="color:var(--purple2);cursor:pointer;font-weight:600;display:none;">🔑 تسجيل الدخول</span>
            </div>
        </div>
    </div>

    <!-- ==================== MAIN APP ==================== -->
    <div id="mainApp">
        <div class="top-bar">
            <div class="dots">
                <span class="dot r" onclick="playSound('close')"></span>
                <span class="dot o" onclick="playSound('min')"></span>
                <span class="dot g" onclick="playSound('max')"></span>
            </div>
            <span>🕐 <span id="liveTime"></span></span>
            <div class="menu-drop">
                <button class="menu-btn" onclick="toggleMenu()">⋮</button>
                <div class="menu-content" id="menuContent">
                    <a onclick="goPage('home');toggleMenu()">🏠 الرئيسية</a>
                    <a onclick="goPage('menu');toggleMenu()">📋 المنيو</a>
                    <a onclick="goPage('drinks');toggleMenu()">🥤 مشروبات</a>
                    <a onclick="goPage('alcohol');toggleMenu()">🍺 خمور</a>
                    <a onclick="goPage('food');toggleMenu()">🍰 حلويات</a>
                    <a onclick="goPage('reserve');toggleMenu()">📅 حجز طاولة</a>
                    <a onclick="goPage('dashboard');toggleMenu()" id="dashLink" style="display:none;">📊 لوحة التحكم</a>
                    <a onclick="goPage('profile');toggleMenu()">👤 حسابي</a>
                    <hr style="border-color:rgba(255,255,255,0.06);margin:4px 0;">
                    <a onclick="doLogout();toggleMenu()" style="color:var(--red);">🚪 خروج</a>
                </div>
            </div>
        </div>

        <nav class="navbar-ev">
            <a class="brand" onclick="goPage('home')">
                <span class="brand-icon">🔥</span>EVIL BAR
            </a>
            <div class="nav-actions">
                <button class="cart-btn" onclick="toggleCart()">
                    🛒 <span class="cart-badge" id="cartBadge">0</span>
                </button>
                <span style="color:var(--purple2);font-weight:600;font-size:14px;">
                    👤 <span id="navUser"></span>
                </span>
            </div>
        </nav>

        <div id="pageContent"></div>

        <footer>
            <h4 style="color:var(--purple2);text-shadow:var(--glow-text);">🔥 EVIL BAR</h4>
            <p>أفخم كافيه وبار في المدينة | منذ 2020</p>
            <p style="font-size:11px;margin-top:8px;">© 2024 Evil Bar. All rights reserved.</p>
        </footer>
    </div>

    <!-- Cart Sidebar -->
    <div class="cart-overlay" id="cartOverlay" onclick="toggleCart()"></div>
    <div class="cart-sidebar" id="cartSidebar">
        <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:15px;">
            <h4 style="color:var(--purple2);">🛒 السلة</h4>
            <button onclick="toggleCart()" style="background:none;border:none;color:#fff;font-size:18px;cursor:pointer;">✕</button>
        </div>
        <div id="cartItems"></div>
        <hr style="border-color:rgba(255,255,255,0.06);margin:15px 0;">
        <h4>الإجمالي: <span style="color:var(--purple2);" id="cartTotal">0 ج.م</span></h4>
        <button class="btn btn-purple" onclick="openPayment()">💳 ادفع الآن</button>
        <button class="btn btn-red" onclick="clearCart()" style="margin-top:6px;">🗑 تفريغ</button>
    </div>

    <!-- Payment Modal -->
    <div class="modal-overlay" id="payModal">
        <div class="modal-dialog">
            <div style="display:flex;justify-content:space-between;margin-bottom:15px;">
                <h4 style="color:var(--purple2);">💳 الدفع</h4>
                <button onclick="closePayment()" style="background:none;border:none;color:#fff;font-size:18px;cursor:pointer;">✕</button>
            </div>
            <div style="display:flex;gap:6px;margin-bottom:15px;">
                <button class="btn btn-purple btn-sm active" onclick="switchPay('visa')" style="flex:1;">💳 فيزا</button>
                <button class="btn btn-outline btn-sm" onclick="switchPay('vodafone')" style="flex:1;">📱 فودافون كاش</button>
            </div>
            <div id="payVisa">
                <div style="background:linear-gradient(135deg,#1a1f71,#2a3f91);border-radius:12px;padding:16px;color:#fff;margin-bottom:12px;"><div style="font-size:24px;font-weight:900;">VISA</div></div>
                <input class="form-input" id="cardName" placeholder="👤 الاسم على البطاقة" style="margin-bottom:8px;">
                <input class="form-input" id="cardNum" placeholder="💳 رقم البطاقة" maxlength="19" oninput="formatCard(this)" dir="ltr" style="margin-bottom:8px;">
                <div style="display:flex;gap:8px;margin-bottom:8px;">
                    <input class="form-input" id="cardExp" placeholder="📅 MM/YY" maxlength="5" dir="ltr" style="flex:1;">
                    <input class="form-input" id="cardCVV" placeholder="🔒 CVV" maxlength="4" dir="ltr" type="password" style="flex:1;">
                </div>
                <div id="visaErrors" style="display:none;background:rgba(239,68,68,0.1);border:1px solid var(--red);border-radius:10px;padding:12px;margin:8px 0;color:var(--red);font-size:12px;"></div>
                <p style="color:var(--gray);">💰 <span style="color:var(--purple2);font-weight:700;" id="visaAmt"></span></p>
                <button class="btn btn-purple" onclick="validateVisa()">🔍 فحص ودفع</button>
            </div>
            <div id="payVodafone" style="display:none;">
                <div style="background:#e60000;border-radius:12px;padding:16px;text-align:center;color:#fff;margin-bottom:12px;"><h5>📱 فودافون كاش</h5><div style="font-size:20px;font-weight:900;background:rgba(255,255,255,0.2);padding:10px;border-radius:8px;margin:8px 0;">01026966717<button onclick="copyVodafone()" style="background:#fff;color:#000;border:none;padding:4px 8px;border-radius:5px;cursor:pointer;margin-right:6px;">📋</button></div></div>
                <input class="form-input" id="senderPhone" placeholder="📱 رقم هاتفك" dir="ltr" style="margin-bottom:8px;">
                <input class="form-input" id="senderName" placeholder="👤 اسمك" style="margin-bottom:8px;">
                <div style="border:2px dashed rgba(139,92,246,0.3);border-radius:10px;padding:15px;text-align:center;cursor:pointer;margin-bottom:10px;" onclick="document.getElementById('scrFile').click()">📸 سكرين شوت<input type="file" id="scrFile" accept="image/*" style="display:none;" onchange="prevScr(event)"><img id="scrPreview" style="max-width:100%;max-height:120px;display:none;margin-top:8px;border-radius:6px;"></div>
                <p style="color:var(--gray);">💰 <span style="color:var(--purple2);font-weight:700;" id="vodAmt"></span></p>
                <button class="btn btn-purple" onclick="submitVodafone()">📤 إرسال للمراجعة</button>
            </div>
        </div>
    </div>

    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
    <script>
        // ==================== ADMIN ====================
        const ADMIN = {
            username: 'mostafaelsarnoby',
            password: '308191',
            name: 'مصطفى الصرنوبي',
            role: 'super_admin'
        };

        // ==================== PRODUCTS ====================
        const PRODUCTS = [
            { id:1, name:'إسبرسو', cat:'hot', price:35, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1510707577719-ae7c14805e3a?w=500&q=80', desc:'إسبرسو إيطالي أصيل غني وقوي' },
            { id:2, name:'كابتشينو', cat:'hot', price:45, disc:38, rating:4.9, img:'https://images.unsplash.com/photo-1534778101976-62847782c213?w=500&q=80', desc:'كابتشينو برغوة حليب كثيفة' },
            { id:3, name:'لاتيه', cat:'hot', price:45, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1461023058943-07fcbe16d735?w=500&q=80', desc:'لاتيه كريمي ناعم' },
            { id:4, name:'موكا', cat:'hot', price:50, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1572442388796-11668a67e53d?w=500&q=80', desc:'موكا غنية بالشوكولاتة' },
            { id:5, name:'قهوة تركي', cat:'hot', price:30, disc:null, rating:4.9, img:'https://images.unsplash.com/photo-1509042239860-f550ce710b93?w=500&q=80', desc:'قهوة تركية تقليدية' },
            { id:6, name:'آيس لاتيه', cat:'cold', price:50, disc:null, rating:4.6, img:'https://images.unsplash.com/photo-1517701604599-bb29b565090c?w=500&q=80', desc:'آيس لاتيه منعش' },
            { id:7, name:'ليمون نعناع', cat:'cold', price:35, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1621263764928-df1444c5e859?w=500&q=80', desc:'ليمونادة طازجة' },
            { id:8, name:'مانجو', cat:'cold', price:40, disc:null, rating:4.9, img:'https://images.unsplash.com/photo-1546173159-315724a31696?w=500&q=80', desc:'عصير مانجو' },
            { id:9, name:'تشيز كيك', cat:'food', price:60, disc:50, rating:4.9, img:'https://images.unsplash.com/photo-1533134242443-d4fd215305ad?w=500&q=80', desc:'تشيز كيك نيويورك' },
            { id:10, name:'براوني', cat:'food', price:45, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1606313564200-e75d5e30476c?w=500&q=80', desc:'براوني شوكولاتة' },
            { id:11, name:'كرواسون', cat:'food', price:35, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1555507036-ab1f4038024a?w=500&q=80', desc:'كرواسون فرنسي' },
            { id:12, name:'هاينكن', cat:'alcohol', price:70, disc:null, rating:4.6, img:'https://images.unsplash.com/photo-1618885472179-5e474019f2a9?w=500&q=80', desc:'بيرة هاينكن' },
            { id:13, name:'ويسكي', cat:'alcohol', price:120, disc:100, rating:4.8, img:'https://images.unsplash.com/photo-1527281400683-1aae777175f0?w=500&q=80', desc:'ويسكي 12 سنة' },
            { id:14, name:'فودكا', cat:'alcohol', price:80, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1569529465841-dfecdab7503b?w=500&q=80', desc:'فودكا نقية' },
            { id:15, name:'موهيتو', cat:'alcohol', price:75, disc:null, rating:4.9, img:'https://images.unsplash.com/photo-1551538827-9c037cb4f32a?w=500&q=80', desc:'موهيتو منعش' },
            { id:16, name:'مارتيني', cat:'alcohol', price:85, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1575023782549-62ca0d244b39?w=500&q=80', desc:'مارتيني جاف' },
        ];

        const BIN_DB = { '4':{bank:'Visa',country:'عالمي'}, '51':{bank:'Mastercard',country:'عالمي'}, '45':{bank:'البنك الأهلي',country:'مصر'}, '49':{bank:'بنك مصر',country:'مصر'}, '42':{bank:'CIB',country:'مصر'} };

        // ==================== STATE ====================
        let cart = JSON.parse(localStorage.getItem('evilCart') || '[]');
        let currentUser = JSON.parse(localStorage.getItem('evilUser') || 'null');
        let scrFile = null, otpCode = '', otpTimer = null, otpSec = 120, regData = {};

        // ==================== SOUND ====================
        function playSound(t) {
            try {
                const a = new (window.AudioContext||window.webkitAudioContext)();
                const o = a.createOscillator(); const g = a.createGain();
                o.connect(g); g.connect(a.destination);
                switch(t){ case'click':o.frequency.value=800;g.gain.value=0.06;o.start();o.stop(a.currentTime+0.04);break; case'success':o.frequency.value=1200;g.gain.value=0.08;o.start();o.stop(a.currentTime+0.1);break; case'error':o.frequency.value=200;g.gain.value=0.1;o.start();o.stop(a.currentTime+0.25);break; case'add':o.frequency.value=600;g.gain.value=0.05;o.start();o.stop(a.currentTime+0.06);break; case'close':o.frequency.value=300;g.gain.value=0.08;o.start();o.stop(a.currentTime+0.12);break; case'min':o.frequency.value=500;g.gain.value=0.04;o.start();o.stop(a.currentTime+0.04);break; case'max':o.frequency.value=1000;g.gain.value=0.06;o.start();o.stop(a.currentTime+0.08);break; }
            } catch(e) {}
        }

        // ==================== PARTICLES ====================
        function initParticles() {
            const c = document.getElementById('particlesCanvas'), ctx = c.getContext('2d');
            c.width = innerWidth; c.height = innerHeight;
            const ps = Array.from({length:60}, () => ({
                x:Math.random()*c.width, y:Math.random()*c.height,
                s:Math.random()*2.5+0.5, sx:(Math.random()-0.5)*0.3, sy:(Math.random()-0.5)*0.3,
                o:Math.random()*0.5+0.1, col:Math.random()>0.5?'139,92,246':'167,139,250'
            }));
            (function anim() {
                ctx.clearRect(0,0,c.width,c.height);
                ps.forEach(p => {
                    p.x+=p.sx; p.y+=p.sy;
                    if(p.x<0)p.x=c.width; if(p.x>c.width)p.x=0;
                    if(p.y<0)p.y=c.height; if(p.y>c.height)p.y=0;
                    ctx.beginPath(); ctx.arc(p.x,p.y,p.s,0,Math.PI*2);
                    ctx.fillStyle=`rgba(${p.col},${p.o})`; ctx.fill();
                    ctx.shadowBlur=15; ctx.shadowColor=`rgba(${p.col},0.5)`;
                });
                requestAnimationFrame(anim);
            })();
        }

        // ==================== CLOCK ====================
        function updateClock() { document.getElementById('liveTime').textContent = new Date().toLocaleTimeString('ar-EG'); }

        // ==================== MENU ====================
        function toggleMenu() { document.getElementById('menuContent').classList.toggle('show'); playSound('click'); }
        document.addEventListener('click', (e) => { if (!e.target.closest('.menu-drop')) document.getElementById('menuContent').classList.remove('show'); });

        // ==================== INIT ====================
        window.addEventListener('DOMContentLoaded', () => {
            let users = JSON.parse(localStorage.getItem('evilUsers') || '[]');
            if (!users.find(u => u.username === ADMIN.username)) {
                users.push(ADMIN);
                localStorage.setItem('evilUsers', JSON.stringify(users));
            }
            initParticles();
            updateClock();
            setInterval(updateClock, 1000);
            document.getElementById('authPage').style.display = 'flex';
            document.getElementById('mainApp').style.display = 'none';
            AOS.init({ duration: 700, once: false });
        });

        // ==================== AUTH ====================
        function switchTab(t) {
            if (t === 'login') {
                document.getElementById('loginForm').style.display = 'block';
                document.getElementById('registerForm').style.display = 'none';
                document.getElementById('showRegister').style.display = 'inline';
                document.getElementById('showLogin').style.display = 'none';
            } else {
                document.getElementById('loginForm').style.display = 'none';
                document.getElementById('registerForm').style.display = 'block';
                document.getElementById('showRegister').style.display = 'none';
                document.getElementById('showLogin').style.display = 'inline';
            }
            playSound('click');
        }

        function doLogin() {
            const username = document.getElementById('loginUser').value.trim();
            const pass = document.getElementById('loginPass').value.trim();
            if (!username || !pass) { playSound('error'); return toast('املأ الحقول', 'error'); }
            const users = JSON.parse(localStorage.getItem('evilUsers') || '[]');
            const found = users.find(u => u.username === username && u.password === pass);
            if (found) { loginSuccess(found); playSound('success'); }
            else { playSound('error'); toast('اسم المستخدم أو كلمة المرور خاطئة', 'error'); }
        }

        function sendOTP() {
            const username = document.getElementById('regUser').value.trim();
            const name = document.getElementById('regName').value.trim();
            const phone = document.getElementById('regPhone').value.trim();
            const pass = document.getElementById('regPass').value.trim();
            if (!username || !name || !phone || !pass) { playSound('error'); return toast('املأ الحقول', 'error'); }
            if (pass.length < 8) { playSound('error'); return toast('كلمة مرور 8 أحرف', 'error'); }
            let users = JSON.parse(localStorage.getItem('evilUsers') || '[]');
            if (users.find(u => u.username === username)) { playSound('error'); return toast('اسم المستخدم مستخدم', 'error'); }
            if (users.find(u => u.phone === phone)) { playSound('error'); return toast('الهاتف مستخدم', 'error'); }

            regData = { username, name, phone, password: pass, role: 'user' };
            otpCode = String(Math.floor(100000 + Math.random() * 900000));
            localStorage.setItem('evilOTP', otpCode);

            document.getElementById('otpBox').classList.add('show');
            document.getElementById('o1').focus();
            otpSec = 120; updateTimer();
            if (otpTimer) clearInterval(otpTimer);
            otpTimer = setInterval(() => { otpSec--; updateTimer(); if (otpSec <= 0) { clearInterval(otpTimer); document.getElementById('btnReOTP').disabled = false; document.getElementById('otpTimer').classList.add('expired'); document.getElementById('otpTimer').textContent = 'انتهت'; } }, 1000);
            document.getElementById('btnReOTP').disabled = true;

            const wa = encodeURIComponent(`🔥 Evil Bar - رمز التحقق: ${otpCode}\nلا تشاركه مع أحد`);
            window.open(`https://wa.me/${phone.replace(/^\+/,'')}?text=${wa}`, '_blank');
            playSound('success'); toast('📲 تم إرسال الرمز');
        }

        function updateTimer() { document.getElementById('otpTimer').textContent = `${String(Math.floor(otpSec/60)).padStart(2,'0')}:${String(otpSec%60).padStart(2,'0')}`; }
        function nextOtp(i) { if (i.value.length === 1) { const n = i.nextElementSibling; if (n) n.focus(); } }

        function verifyOTP() {
            const code = ['o1','o2','o3','o4','o5','o6'].map(id => document.getElementById(id).value).join('');
            if (code === localStorage.getItem('evilOTP')) {
                clearInterval(otpTimer);
                let users = JSON.parse(localStorage.getItem('evilUsers') || '[]');
                users.push(regData);
                localStorage.setItem('evilUsers', JSON.stringify(users));
                loginSuccess(regData);
                playSound('success'); toast('✅ تم التسجيل');
            } else { playSound('error'); toast('❌ رمز خاطئ', 'error'); }
        }

        function loginSuccess(u) {
            currentUser = u; localStorage.setItem('evilUser', JSON.stringify(u));
            document.getElementById('authPage').style.display = 'none';
            document.getElementById('mainApp').classList.add('show');
            document.getElementById('mainApp').style.display = 'block';
            document.getElementById('navUser').textContent = u.name;
            if (u.role === 'super_admin') document.getElementById('dashLink').style.display = 'block';
            updateCart(); goPage('home'); toast('👋 ' + u.name);
        }

        function doLogout() {
            currentUser = null; localStorage.removeItem('evilUser');
            document.getElementById('mainApp').classList.remove('show');
            document.getElementById('mainApp').style.display = 'none';
            document.getElementById('authPage').style.display = 'flex';
            switchTab('login'); playSound('close'); toast('👋 تم الخروج');
        }

        // ==================== PAGES ====================
        function goPage(p) {
            playSound('click');
            const c = document.getElementById('pageContent');
            switch(p) {
                case 'home': c.innerHTML = homePage(); break;
                case 'menu': c.innerHTML = prodPage(PRODUCTS, '📋 المنيو'); break;
                case 'drinks': c.innerHTML = prodPage(PRODUCTS.filter(x=>['hot','cold'].includes(x.cat)), '🥤 مشروبات'); break;
                case 'alcohol': c.innerHTML = prodPage(PRODUCTS.filter(x=>x.cat==='alcohol'), '🍺 خمور'); break;
                case 'food': c.innerHTML = prodPage(PRODUCTS.filter(x=>x.cat==='food'), '🍰 حلويات'); break;
                case 'reserve': c.innerHTML = `<div class="section"><div style="max-width:450px;margin:0 auto;background:rgba(15,10,35,0.9);border:1px solid var(--border-purple);border-radius:18px;padding:30px;"><h3 style="color:var(--purple2);text-align:center;">📅 حجز</h3><input class="form-input" placeholder="الأشخاص" style="margin-bottom:10px;"><input class="form-input" type="date" style="margin-bottom:10px;"><input class="form-input" type="time" style="margin-bottom:10px;"><button class="btn btn-purple" onclick="playSound('success');toast('✅ تم')">تأكيد</button></div></div>`; break;
                case 'profile': c.innerHTML = `<div class="section"><div style="max-width:450px;margin:0 auto;background:rgba(15,10,35,0.9);border:1px solid var(--border-purple);border-radius:18px;padding:30px;"><h3 style="color:var(--purple2);">👤 ${currentUser.name}</h3><p>👤 اسم المستخدم: ${currentUser.username}</p><p>📱 ${currentUser.phone||'-'}</p><p>🏷 ${currentUser.role==='super_admin'?'👑 مدير':'👤 مستخدم'}</p></div></div>`; break;
                case 'dashboard': c.innerHTML = (currentUser&&currentUser.role==='super_admin')?dashPage():'<p style="text-align:center;padding:80px;">⛔ غير مصرح</p>'; break;
            }
            window.scrollTo(0,0); AOS.refresh();
        }

        function homePage() {
            const f = PRODUCTS.filter(p => [1,3,6,8,9,12,14,16].includes(p.id));
            return `<div class="hero"><div><h1>EVIL BAR</h1><p>✦ أفخم تجربة قهوة وبار في المدينة ✦</p><div class="hero-btns"><button class="hero-btn hero-btn-primary" onclick="goPage('menu')">📋 تصفح المنيو</button><button class="hero-btn hero-btn-outline" onclick="goPage('reserve')">📅 احجز طاولة</button></div></div></div><div class="section"><h2 class="section-title"><span class="hl">منتجاتنا</span> المميزة</h2><div class="products-grid">${f.map(p=>productCard(p)).join('')}</div></div>`;
        }

        function prodPage(items, t) { return `<div class="section"><h2 class="section-title"><span class="hl">${t}</span></h2><div class="products-grid">${items.map(p=>productCard(p)).join('')}</div></div>`; }

        function productCard(p) {
            const pr = p.disc || p.price;
            return `<div class="product-card" data-aos="fade-up"><div class="product-img"><img src="${p.img}" alt="${p.name}" onerror="this.src='https://via.placeholder.com/500x250/120026/8B5CF6?text=${p.name}'">${p.disc?`<span class="badge-disc">-${Math.round((1-p.disc/p.price)*100)}%</span>`:''}</div><div class="product-body"><h5>${p.name}</h5><p class="desc">${p.desc}</p><div class="
