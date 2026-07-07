<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Evil Bar - إيفل بار | Luxury Cafe & Bar</title>
    
    <!-- Bootstrap 5 RTL -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.rtl.min.css" rel="stylesheet">
    <!-- Font Awesome 6 -->
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" rel="stylesheet">
    <!-- AOS Animation -->
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">
    
    <style>
        :root {
            --bg: #04000d;
            --bg2: #0a001a;
            --bg3: #120026;
            --purple: #8B5CF6;
            --purple2: #A78BFA;
            --purple3: #C4B5FD;
            --purple-dark: #6D28D9;
            --gold: #F59E0B;
            --white: #fff;
            --gray: #999;
            --gray2: #666;
            --red: #ef4444;
            --green: #10b981;
            --orange: #f59e0b;
            --glass: rgba(15,10,35,0.85);
            --border-purple: rgba(139,92,246,0.25);
            --shadow-purple: 0 0 30px rgba(139,92,246,0.3);
            --shadow-purple2: 0 0 60px rgba(139,92,246,0.5);
            --radius: 16px;
            --transition: all 0.3s cubic-bezier(0.4,0,0.2,1);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }
        
        body {
            background: var(--bg);
            color: var(--white);
            font-family: 'Segoe UI', Tahoma, sans-serif;
            min-height: 100vh;
            overflow-x: hidden;
        }

        ::-webkit-scrollbar { width: 6px; }
        ::-webkit-scrollbar-track { background: var(--bg); }
        ::-webkit-scrollbar-thumb { background: var(--purple); border-radius: 10px; }

        /* Particles */
        #particlesCanvas {
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            z-index: 0;
            pointer-events: none;
        }

        /* Preloader */
        #preloader {
            position: fixed; top: 0; left: 0;
            width: 100%; height: 100%;
            background: #020008;
            z-index: 99999;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
            transition: opacity 0.4s, visibility 0.4s;
        }
        #preloader.hidden { opacity: 0; visibility: hidden; }
        .preloader-ring {
            width: 60px; height: 60px;
            border: 3px solid transparent;
            border-top-color: var(--purple);
            border-right-color: var(--purple2);
            border-radius: 50%;
            animation: spin 0.8s linear infinite;
        }
        @keyframes spin { to { transform: rotate(360deg); } }
        .preloader-text {
            color: var(--purple2);
            font-size: 24px;
            font-weight: 900;
            margin-top: 12px;
            letter-spacing: 6px;
            animation: pulse 1.5s infinite;
            text-shadow: 0 0 20px rgba(139,92,246,0.5);
        }
        @keyframes pulse {
            0%,100% { opacity: 1; }
            50% { opacity: 0.5; }
        }

        /* Auth Page */
        #authPage {
            display: flex;
            min-height: 100vh;
            align-items: center;
            justify-content: center;
            padding: 20px;
            position: relative;
            z-index: 1;
        }
        .auth-card {
            background: var(--glass);
            backdrop-filter: blur(30px);
            -webkit-backdrop-filter: blur(30px);
            border: 1px solid var(--border-purple);
            border-radius: 24px;
            padding: 35px 28px;
            width: 100%;
            max-width: 430px;
            box-shadow: var(--shadow-purple2);
            animation: slideUp 0.6s ease;
        }
        @keyframes slideUp {
            from { opacity: 0; transform: translateY(30px) scale(0.95); }
            to { opacity: 1; transform: translateY(0) scale(1); }
        }
        .auth-logo {
            text-align: center;
            margin-bottom: 25px;
        }
        .auth-icon {
            font-size: 50px;
            animation: float 3s ease-in-out infinite;
        }
        @keyframes float {
            0%,100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }
        .auth-title {
            font-size: 36px;
            font-weight: 900;
            background: linear-gradient(135deg, var(--purple-dark), var(--purple2), var(--purple3));
            background-size: 300% 300%;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: shimmer 3s infinite;
            letter-spacing: 5px;
        }
        @keyframes shimmer {
            0%,100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }
        .auth-subtitle {
            color: var(--gray);
            font-size: 14px;
            margin-top: 5px;
            letter-spacing: 2px;
        }

        /* Tabs */
        .auth-tabs {
            display: flex;
            gap: 6px;
            background: rgba(255,255,255,0.03);
            border-radius: 14px;
            padding: 5px;
            margin-bottom: 22px;
        }
        .auth-tab {
            flex: 1;
            padding: 12px;
            text-align: center;
            border: none;
            background: transparent;
            color: var(--gray);
            border-radius: 12px;
            cursor: pointer;
            font-size: 14px;
            font-weight: 600;
            transition: var(--transition);
        }
        .auth-tab.active {
            background: linear-gradient(135deg, var(--purple-dark), var(--purple));
            color: #fff;
            font-weight: 700;
            box-shadow: var(--shadow-purple);
        }
        .auth-tab:hover:not(.active) {
            color: var(--white);
            background: rgba(255,255,255,0.05);
        }

        /* Form */
        .form-group {
            margin-bottom: 15px;
        }
        .form-label {
            display: block;
            margin-bottom: 6px;
            color: var(--gray2);
            font-size: 13px;
            font-weight: 600;
        }
        .form-input {
            width: 100%;
            padding: 14px 16px;
            background: rgba(255,255,255,0.04);
            border: 1.5px solid rgba(255,255,255,0.1);
            border-radius: 12px;
            color: var(--white);
            font-size: 15px;
            transition: var(--transition);
            font-family: 'Segoe UI', Tahoma, sans-serif;
        }
        .form-input:focus {
            outline: none;
            border-color: var(--purple);
            box-shadow: 0 0 0 3px rgba(139,92,246,0.1);
        }
        .form-input::placeholder {
            color: rgba(255,255,255,0.2);
        }

        /* Buttons */
        .btn {
            width: 100%;
            padding: 14px;
            border: none;
            border-radius: 12px;
            font-size: 15px;
            font-weight: 700;
            cursor: pointer;
            transition: var(--transition);
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            margin-bottom: 8px;
            font-family: 'Segoe UI', Tahoma, sans-serif;
        }
        .btn-purple {
            background: linear-gradient(135deg, var(--purple-dark), var(--purple), var(--purple2));
            color: #fff;
            position: relative;
            overflow: hidden;
        }
        .btn-purple::after {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent 40%, rgba(255,255,255,0.2) 50%, transparent 60%);
            animation: btnShine 3s infinite;
        }
        @keyframes btnShine {
            0% { transform: translateX(-100%) rotate(45deg); }
            100% { transform: translateX(100%) rotate(45deg); }
        }
        .btn-purple:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 30px rgba(139,92,246,0.5);
        }
        .btn-outline {
            background: transparent;
            border: 2px solid var(--border-purple);
            color: var(--purple2);
        }
        .btn-outline:hover {
            background: rgba(139,92,246,0.08);
            border-color: var(--purple);
        }
        .btn-google {
            background: #fff;
            color: #333;
        }
        .btn-google:hover {
            background: #f0f0f0;
        }
        .btn-red {
            background: var(--red);
            color: #fff;
        }
        .btn-green {
            background: var(--green);
            color: #fff;
        }
        .btn-sm {
            width: auto;
            padding: 8px 16px;
            font-size: 13px;
        }

        /* OTP */
        .otp-section {
            display: none;
            animation: fadeIn 0.3s ease;
        }
        .otp-section.show {
            display: block;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(-10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .otp-inputs {
            display: flex;
            gap: 8px;
            justify-content: center;
            margin: 18px 0;
        }
        .otp-inputs input {
            width: 48px;
            height: 52px;
            text-align: center;
            font-size: 22px;
            font-weight: 700;
            background: rgba(255,255,255,0.04);
            border: 2px solid rgba(255,255,255,0.12);
            border-radius: 10px;
            color: var(--purple2);
            transition: var(--transition);
        }
        .otp-inputs input:focus {
            outline: none;
            border-color: var(--purple);
            box-shadow: 0 0 15px rgba(139,92,246,0.2);
        }
        .timer-text {
            text-align: center;
            color: var(--purple2);
            font-weight: 700;
            font-size: 16px;
            margin: 10px 0;
        }
        .timer-text.expired {
            color: var(--red);
        }

        /* Divider */
        .divider {
            display: flex;
            align-items: center;
            gap: 15px;
            margin: 18px 0;
            color: var(--gray2);
            font-size: 12px;
        }
        .divider::before,
        .divider::after {
            content: '';
            flex: 1;
            height: 1px;
            background: rgba(255,255,255,0.08);
        }
        .auth-link {
            color: var(--purple2);
            cursor: pointer;
            font-weight: 600;
        }
        .auth-link:hover {
            text-decoration: underline;
        }

        /* Main App */
        #mainApp {
            display: none;
            position: relative;
            z-index: 1;
        }
        #mainApp.show {
            display: block;
        }

        /* Top Bar */
        .top-bar {
            background: #020008;
            border-bottom: 1px solid rgba(139,92,246,0.08);
            padding: 8px 18px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            font-size: 12px;
            color: var(--gray);
        }
        .top-dots {
            display: flex;
            gap: 6px;
        }
        .dot {
            width: 8px;
            height: 8px;
            border-radius: 50%;
            cursor: pointer;
            transition: 0.2s;
        }
        .dot:hover {
            transform: scale(1.4);
        }
        .dot.red { background: var(--red); }
        .dot.orange { background: var(--orange); }
        .dot.green { background: var(--green); }

        /* Menu Trigger (3 dots) */
        .menu-trigger {
            position: relative;
        }
        .menu-btn {
            background: none;
            border: none;
            color: var(--purple2);
            font-size: 24px;
            cursor: pointer;
            padding: 5px 12px;
            border-radius: 8px;
            transition: var(--transition);
        }
        .menu-btn:hover {
            background: rgba(139,92,246,0.1);
        }
        .menu-dropdown {
            display: none;
            position: absolute;
            top: 40px;
            right: 0;
            background: rgba(15,8,35,0.98);
            border: 1px solid var(--border-purple);
            border-radius: 14px;
            padding: 6px;
            z-index: 200;
            min-width: 200px;
            box-shadow: var(--shadow-purple2);
            backdrop-filter: blur(20px);
        }
        .menu-dropdown.open {
            display: block;
            animation: fadeIn 0.2s ease;
        }
        .menu-dropdown a {
            display: block;
            padding: 10px 15px;
            color: var(--white);
            text-decoration: none;
            border-radius: 8px;
            font-size: 13px;
            cursor: pointer;
            transition: var(--transition);
        }
        .menu-dropdown a:hover {
            background: rgba(139,92,246,0.15);
            color: var(--purple2);
        }

        /* Navbar */
        .navbar-ev {
            background: rgba(4,0,13,0.9);
            backdrop-filter: blur(25px);
            -webkit-backdrop-filter: blur(25px);
            border-bottom: 1px solid rgba(139,92,246,0.08);
            padding: 12px 18px;
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
            display: flex;
            align-items: center;
            gap: 8px;
            color: var(--purple2);
            font-size: 22px;
            font-weight: 900;
            text-decoration: none;
            letter-spacing: 3px;
            cursor: pointer;
            transition: var(--transition);
        }
        .brand:hover {
            color: var(--purple3);
        }
        .brand-icon {
            font-size: 28px;
            animation: float 3s ease-in-out infinite;
        }
        .nav-actions {
            display: flex;
            align-items: center;
            gap: 8px;
        }
        .cart-btn {
            position: relative;
            background: rgba(139,92,246,0.1);
            border: 1px solid var(--border-purple);
            color: var(--purple2);
            padding: 8px 16px;
            border-radius: 50px;
            cursor: pointer;
            font-weight: 600;
            font-size: 13px;
            transition: var(--transition);
        }
        .cart-btn:hover {
            background: var(--purple);
            color: #fff;
        }
        .cart-badge {
            position: absolute;
            top: -6px;
            right: -6px;
            background: var(--purple);
            color: #fff;
            border-radius: 50%;
            width: 20px;
            height: 20px;
            font-size: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 900;
        }

        /* Hero */
        .hero {
            min-height: 80vh;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            position: relative;
            background: radial-gradient(ellipse at center, rgba(139,92,246,0.05) 0%, transparent 70%);
        }
        .hero h1 {
            font-size: clamp(45px, 9vw, 90px);
            font-weight: 900;
            background: linear-gradient(135deg, var(--purple-dark), var(--purple2), var(--purple3), var(--purple2));
            background-size: 300% 300%;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: shimmer 4s infinite;
            letter-spacing: 8px;
        }
        .hero p {
            font-size: 18px;
            color: var(--gray);
            margin: 15px 0 25px;
        }
        .hero-btns {
            display: flex;
            gap: 12px;
            justify-content: center;
            flex-wrap: wrap;
        }
        .hero-btn {
            padding: 15px 32px;
            border-radius: 50px;
            font-size: 15px;
            font-weight: 700;
            cursor: pointer;
            transition: var(--transition);
            text-decoration: none;
            display: inline-flex;
            align-items: center;
            gap: 8px;
        }
        .hero-btn-primary {
            background: linear-gradient(135deg, var(--purple-dark), var(--purple));
            color: #fff;
            border: none;
        }
        .hero-btn-primary:hover {
            transform: translateY(-4px);
            box-shadow: 0 15px 40px rgba(139,92,246,0.5);
        }
        .hero-btn-outline {
            background: transparent;
            border: 2px solid var(--purple);
            color: var(--purple2);
        }
        .hero-btn-outline:hover {
            background: var(--purple);
            color: #fff;
            transform: translateY(-4px);
        }

        /* Sections */
        .section {
            padding: 60px 18px;
        }
        .section-title {
            text-align: center;
            font-size: 30px;
            font-weight: 900;
            margin-bottom: 35px;
        }
        .section-title .hl {
            color: var(--purple2);
        }
        .section-title::after {
            content: '';
            display: block;
            width: 55px;
            height: 3px;
            background: linear-gradient(90deg, transparent, var(--purple), transparent);
            margin: 12px auto 0;
        }

        /* Products */
        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
            gap: 18px;
            max-width: 1100px;
            margin: 0 auto;
        }
        .product-card {
            background: rgba(15,10,35,0.9);
            border: 1px solid rgba(255,255,255,0.05);
            border-radius: 16px;
            overflow: hidden;
            transition: var(--transition);
        }
        .product-card:hover {
            transform: translateY(-7px);
            border-color: var(--border-purple);
            box-shadow: 0 20px 50px rgba(0,0,0,0.5), var(--shadow-purple);
        }
        .product-img {
            height: 200px;
            overflow: hidden;
            position: relative;
        }
        .product-img img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: 0.5s;
        }
        .product-card:hover .product-img img {
            transform: scale(1.1);
        }
        .badge-disc {
            position: absolute;
            top: 10px;
            left: 10px;
            background: var(--red);
            color: #fff;
            padding: 3px 10px;
            border-radius: 15px;
            font-size: 11px;
            font-weight: 700;
        }
        .product-body {
            padding: 16px;
        }
        .product-body h5 {
            font-size: 16px;
            font-weight: 700;
            margin-bottom: 4px;
        }
        .product-body .desc {
            color: var(--gray);
            font-size: 12px;
            margin-bottom: 8px;
        }
        .price-row {
            display: flex;
            align-items: center;
            gap: 8px;
            margin-bottom: 6px;
        }
        .price-old {
            text-decoration: line-through;
            color: var(--gray2);
            font-size: 13px;
        }
        .price-current {
            color: var(--purple2);
            font-size: 20px;
            font-weight: 900;
        }
        .stars {
            color: var(--orange);
            font-size: 12px;
            margin-bottom: 10px;
        }
        .btn-add {
            width: 100%;
            padding: 10px;
            background: linear-gradient(135deg, var(--purple-dark), var(--purple));
            color: #fff;
            border: none;
            border-radius: 10px;
            font-weight: 700;
            cursor: pointer;
            font-size: 14px;
            transition: var(--transition);
        }
        .btn-add:hover {
            box-shadow: 0 5px 20px rgba(139,92,246,0.4);
        }

        /* Cart Sidebar */
        .cart-overlay {
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: rgba(0,0,0,0.8);
            z-index: 2000;
            display: none;
        }
        .cart-overlay.open { display: block; }
        .cart-sidebar {
            position: fixed;
            top: 0;
            right: -420px;
            width: 400px;
            height: 100%;
            background: var(--bg3);
            z-index: 2001;
            transition: right 0.35s;
            border-left: 1px solid var(--border-purple);
            padding: 22px;
            overflow-y: auto;
        }
        .cart-sidebar.open { right: 0; }

        /* Payment Modal */
        .modal-overlay {
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: rgba(0,0,0,0.9);
            z-index: 3000;
            display: none;
            align-items: center;
            justify-content: center;
        }
        .modal-overlay.open { display: flex; }
        .modal-dialog {
            background: var(--bg3);
            border: 2px solid var(--border-purple);
            border-radius: 22px;
            padding: 26px;
            width: 90%;
            max-width: 500px;
            max-height: 85vh;
            overflow-y: auto;
        }

        .payment-tabs {
            display: flex;
            gap: 6px;
            margin-bottom: 18px;
        }
        .payment-tab {
            flex: 1;
            padding: 10px;
            text-align: center;
            border: none;
            background: transparent;
            color: var(--gray);
            border-radius: 10px;
            cursor: pointer;
            font-size: 13px;
            font-weight: 600;
            transition: var(--transition);
        }
        .payment-tab.active {
            background: linear-gradient(135deg, var(--purple-dark), var(--purple));
            color: #fff;
        }

        .visa-preview {
            background: linear-gradient(135deg, #1a1f71, #2a3f91);
            border-radius: 14px;
            padding: 20px;
            color: #fff;
            margin-bottom: 15px;
        }
        .vodafone-preview {
            background: linear-gradient(135deg, #e60000, #cc0000);
            border-radius: 14px;
            padding: 20px;
            text-align: center;
            color: #fff;
            margin-bottom: 15px;
        }
        .vodafone-number {
            font-size: 22px;
            font-weight: 900;
            background: rgba(255,255,255,0.2);
            padding: 10px;
            border-radius: 8px;
            margin: 10px 0;
        }

        /* Dashboard */
        .stat-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
            gap: 14px;
            margin-bottom: 20px;
        }
        .stat-box {
            background: rgba(15,10,35,0.9);
            border: 1px solid rgba(255,255,255,0.05);
            border-radius: 14px;
            padding: 20px;
            text-align: center;
        }
        .stat-box h2 {
            font-size: 32px;
            color: var(--purple2);
        }

        table {
            width: 100%;
            border-collapse: collapse;
            font-size: 13px;
        }
        th {
            background: rgba(139,92,246,0.08);
            color: var(--purple2);
            padding: 10px;
            text-align: right;
        }
        td {
            padding: 8px 10px;
            border-bottom: 1px solid rgba(255,255,255,0.03);
        }

        .status-pending { background: var(--orange); color: #000; padding: 2px 8px; border-radius: 15px; font-size: 10px; font-weight: 700; }
        .status-approved { background: var(--green); color: #fff; padding: 2px 8px; border-radius: 15px; font-size: 10px; font-weight: 700; }
        .status-rejected { background: var(--red); color: #fff; padding: 2px 8px; border-radius: 15px; font-size: 10px; font-weight: 700; }

        /* Toast */
        .toast-container {
            position: fixed;
            bottom: 25px;
            right: 25px;
            z-index: 9999;
            display: flex;
            flex-direction: column;
            gap: 10px;
        }
        .toast-item {
            background: var(--bg3);
            border: 1px solid var(--border-purple);
            padding: 15px 20px;
            border-radius: 14px;
            color: #fff;
            font-weight: 600;
            font-size: 14px;
            animation: toastIn 0.35s;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
            display: flex;
            align-items: center;
            gap: 10px;
            min-width: 260px;
        }
        .toast-item.success { border-right: 4px solid var(--green); }
        .toast-item.error { border-right: 4px solid var(--red); }
        @keyframes toastIn {
            from { opacity: 0; transform: translateX(70px); }
            to { opacity: 1; transform: translateX(0); }
        }

        /* Footer */
        footer {
            background: #020008;
            border-top: 1px solid rgba(139,92,246,0.06);
            padding: 30px 20px;
            text-align: center;
            color: var(--gray);
            font-size: 13px;
        }
        footer a {
            color: var(--gray);
            text-decoration: none;
            margin: 0 8px;
            transition: var(--transition);
        }
        footer a:hover { color: var(--purple2); }

        /* Responsive */
        @media (max-width: 768px) {
            .hero h1 { font-size: 36px; letter-spacing: 4px; }
            .cart-sidebar { width: 100%; right: -100%; }
            .products-grid { grid-template-columns: repeat(auto-fill, minmax(155px, 1fr)); gap: 12px; }
            .product-img { height: 150px; }
        }
    </style>
</head>
<body>

    <!-- Particles Background -->
    <canvas id="particlesCanvas"></canvas>

    <!-- Preloader -->
    <div id="preloader">
        <div class="preloader-ring"></div>
        <div class="preloader-text">EVIL BAR</div>
    </div>

    <!-- Toast Container -->
    <div class="toast-container" id="toastContainer"></div>

    <!-- ==================== AUTH PAGE ==================== -->
    <div id="authPage">
        <div class="auth-card">
            <div class="auth-logo">
                <div class="auth-icon">🔥</div>
                <h1 class="auth-title">EVIL BAR</h1>
                <p class="auth-subtitle">✦ أفخم كافيه وبار في المدينة ✦</p>
            </div>

            <div class="auth-tabs">
                <button class="auth-tab active" onclick="switchTab('login')">🔑 دخول</button>
                <button class="auth-tab" onclick="switchTab('register')">📱 برقم الهاتف</button>
            </div>

            <!-- Login Form -->
            <div id="loginForm">
                <div class="form-group">
                    <label class="form-label">📱 الهاتف أو 📧 البريد</label>
                    <input type="text" class="form-input" id="loginId" placeholder="010xxxxxxxx أو email" dir="ltr">
                </div>
                <div class="form-group">
                    <label class="form-label">🔒 كلمة المرور</label>
                    <input type="password" class="form-input" id="loginPass" placeholder="••••••••">
                </div>
                <button class="btn btn-purple" onclick="doLogin()">
                    <i class="fas fa-sign-in-alt"></i> تسجيل الدخول
                </button>
                <button class="btn btn-google" onclick="googleLogin()">
                    <i class="fab fa-google"></i> Google
                </button>
                <p style="text-align:center;margin-top:10px;font-size:10px;color:var(--gray2);">
                    المدير: 01026966717 | 308191
                </p>
            </div>

            <!-- Register Form (Phone Only) -->
            <div id="registerForm" style="display:none;">
                <div class="form-group">
                    <label class="form-label">👤 الاسم الكامل</label>
                    <input type="text" class="form-input" id="regName" placeholder="الاسم الكامل">
                </div>
                <div class="form-group">
                    <label class="form-label">📱 رقم الهاتف</label>
                    <input type="tel" class="form-input" id="regPhone" placeholder="01xxxxxxxxx" dir="ltr">
                    <small style="color:var(--gray);font-size:10px;">سيصلك رمز تحقق عبر الواتساب</small>
                </div>
                <div class="form-group">
                    <label class="form-label">🔒 كلمة المرور (8 أحرف على الأقل)</label>
                    <input type="password" class="form-input" id="regPass" placeholder="••••••••">
                </div>
                <button class="btn btn-purple" onclick="sendWhatsAppOTP()">
                    <i class="fab fa-whatsapp"></i> إرسال رمز التحقق
                </button>

                <!-- OTP Section -->
                <div class="otp-section" id="otpBox">
                    <p style="text-align:center;color:var(--gray);font-size:12px;margin-top:12px;">
                        أدخل رمز التحقق المكون من 6 أرقام
                    </p>
                    <div class="otp-inputs">
                        <input type="text" maxlength="1" oninput="nextOtp(this)" id="o1">
                        <input type="text" maxlength="1" oninput="nextOtp(this)" id="o2">
                        <input type="text" maxlength="1" oninput="nextOtp(this)" id="o3">
                        <input type="text" maxlength="1" oninput="nextOtp(this)" id="o4">
                        <input type="text" maxlength="1" oninput="nextOtp(this)" id="o5">
                        <input type="text" maxlength="1" oninput="nextOtp(this)" id="o6">
                    </div>
                    <div class="timer-text" id="otpTimer">02:00</div>
                    <button class="btn btn-purple" onclick="verifyOTPAndRegister()">
                        <i class="fas fa-check-circle"></i> تأكيد الرمز
                    </button>
                    <button class="btn btn-outline" id="btnResendOtp" onclick="sendWhatsAppOTP()" disabled>
                        <i class="fas fa-redo"></i> إعادة الإرسال
                    </button>
                </div>

                <button class="btn btn-outline" style="margin-top:8px;" onclick="switchTab('login')">
                    ⬅ العودة للدخول
                </button>
            </div>
        </div>
    </div>

    <!-- ==================== MAIN APP ==================== -->
    <div id="mainApp">
        <!-- Top Bar -->
        <div class="top-bar">
            <div class="top-dots">
                <span class="dot red" onclick="playSound('close')"></span>
                <span class="dot orange" onclick="playSound('min')"></span>
                <span class="dot green" onclick="playSound('max')"></span>
            </div>
            <span>🕐 <span id="liveTime"></span></span>
            <div class="menu-trigger">
                <button class="menu-btn" onclick="toggleMenu()">⋮</button>
                <div class="menu-dropdown" id="menuDropdown">
                    <a onclick="goPage('home');toggleMenu()">🏠 الرئيسية</a>
                    <a onclick="goPage('menu');toggleMenu()">📋 المنيو</a>
                    <a onclick="goPage('drinks');toggleMenu()">🥤 مشروبات</a>
                    <a onclick="goPage('alcohol');toggleMenu()">🍺 خمور</a>
                    <a onclick="goPage('food');toggleMenu()">🍰 حلويات</a>
                    <a onclick="goPage('reserve');toggleMenu()">📅 حجز طاولة</a>
                    <a onclick="goPage('dashboard');toggleMenu()" id="dashMenuLink" style="display:none;">📊 لوحة التحكم</a>
                    <a onclick="goPage('profile');toggleMenu()">👤 حسابي</a>
                    <hr style="border-color:rgba(255,255,255,0.06);margin:4px 0;">
                    <a onclick="doLogout();toggleMenu()" style="color:var(--red);">🚪 خروج</a>
                </div>
            </div>
        </div>

        <!-- Navbar -->
        <nav class="navbar-ev">
            <a class="brand" onclick="goPage('home')">
                <span class="brand-icon">🔥</span>EVIL BAR
            </a>
            <div class="nav-actions">
                <button class="cart-btn" onclick="toggleCart()">
                    🛒 <span class="cart-badge" id="cartBadge">0</span>
                </button>
                <span style="color:var(--purple2);font-weight:600;font-size:13px;">
                    👤 <span id="navUser"></span>
                </span>
            </div>
        </nav>

        <!-- Page Content -->
        <div id="pageContent"></div>

        <!-- Footer -->
        <footer>
            <h4 style="color:var(--purple2);">🔥 EVIL BAR</h4>
            <p>أفخم كافيه وبار في المدينة | منذ 2020</p>
            <div style="margin:10px 0;">
                <a href="#" onclick="goPage('home')">الرئيسية</a>
                <a href="#" onclick="goPage('menu')">المنيو</a>
                <a href="#">اتصل بنا</a>
                <a href="#">الخصوصية</a>
            </div>
            <p style="font-size:11px;">© 2024 Evil Bar. All rights reserved.</p>
        </footer>
    </div>

    <!-- Cart Sidebar -->
    <div class="cart-overlay" id="cartOverlay" onclick="toggleCart()"></div>
    <div class="cart-sidebar" id="cartSidebar">
        <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:15px;">
            <h4 style="color:var(--purple2);">🛒 سلة المشتريات</h4>
            <button onclick="toggleCart()" style="background:none;border:none;color:#fff;font-size:18px;cursor:pointer;">✕</button>
        </div>
        <div id="cartItemsList"></div>
        <hr style="border-color:rgba(255,255,255,0.06);margin:15px 0;">
        <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:10px;">
            <span>الإجمالي:</span>
            <span style="color:var(--purple2);font-size:24px;font-weight:900;" id="cartTotal">0 ج.م</span>
        </div>
        <button class="btn btn-purple" onclick="openPayment()">
            <i class="fas fa-credit-card"></i> ادفع الآن
        </button>
        <button class="btn btn-red" onclick="clearCart()" style="margin-top:6px;">
            <i class="fas fa-trash"></i> تفريغ السلة
        </button>
    </div>

    <!-- Payment Modal -->
    <div class="modal-overlay" id="payModal">
        <div class="modal-dialog">
            <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:15px;">
                <h4 style="color:var(--purple2);">💳 إتمام الدفع</h4>
                <button onclick="closePayment()" style="background:none;border:none;color:#fff;font-size:18px;cursor:pointer;">✕</button>
            </div>

            <div class="payment-tabs">
                <button class="payment-tab active" onclick="switchPay('visa')">💳 فيزا</button>
                <button class="payment-tab" onclick="switchPay('vodafone')">📱 فودافون كاش</button>
            </div>

            <!-- Visa -->
            <div id="payVisa">
                <div class="visa-preview">
                    <div style="font-size:28px;font-weight:900;">VISA</div>
                    <div style="font-size:16px;letter-spacing:4px;margin-top:8px;">•••• •••• •••• ••••</div>
                </div>
                <div class="form-group">
                    <label class="form-label">👤 الاسم على البطاقة</label>
                    <input type="text" class="form-input" id="cardName" placeholder="AHMED MOHAMED">
                </div>
                <div class="form-group">
                    <label class="form-label">💳 رقم البطاقة</label>
                    <input type="text" class="form-input" id="cardNum" placeholder="0000 0000 0000 0000" maxlength="19" oninput="formatCard(this)" dir="ltr">
                </div>
                <div style="display:flex;gap:10px;">
                    <div class="form-group" style="flex:1;">
                        <label class="form-label">📅 تاريخ الانتهاء</label>
                        <input type="text" class="form-input" id="cardExp" placeholder="MM/YY" maxlength="5" dir="ltr">
                    </div>
                    <div class="form-group" style="flex:1;">
                        <label class="form-label">🔒 رمز CVV</label>
                        <input type="password" class="form-input" id="cardCVV" placeholder="***" maxlength="4" dir="ltr">
                    </div>
                </div>
                <div id="visaErrors" style="display:none;background:rgba(239,68,68,0.1);border:1px solid var(--red);border-radius:10px;padding:12px;margin-bottom:12px;color:var(--red);font-size:12px;"></div>
                <p style="color:var(--gray);font-size:13px;">💰 المبلغ: <span style="color:var(--purple2);font-weight:700;font-size:18px;" id="visaAmt"></span></p>
                <button class="btn btn-purple" onclick="validateVisa()">
                    <i class="fas fa-shield-alt"></i> فحص ودفع
                </button>
            </div>

            <!-- Vodafone Cash -->
            <div id="payVodafone" style="display:none;">
                <div class="vodafone-preview">
                    <h5>📱 فودافون كاش</h5>
                    <p style="font-size:12px;">حول المبلغ إلى:</p>
                    <div class="vodafone-number">
                        01026966717
                        <button onclick="copyVodafone()" style="background:#fff;color:#000;border:none;padding:5px 10px;border-radius:6px;cursor:pointer;margin-right:8px;font-weight:700;">📋 نسخ</button>
                    </div>
                    <p style="font-size:11px;">الاسم: Evil Bar</p>
                </div>
                <div class="form-group">
                    <label class="form-label">📱 رقم هاتفك المحول منه (إجباري)</label>
                    <input type="tel" class="form-input" id="senderPhone" placeholder="01xxxxxxxxx" dir="ltr">
                </div>
                <div class="form-group">
                    <label class="form-label">👤 اسمك في فودافون كاش</label>
                    <input type="text" class="form-input" id="senderName" placeholder="الاسم الكامل">
                </div>
                <div style="border:2px dashed rgba(139,92,246,0.3);border-radius:12px;padding:20px;text-align:center;cursor:pointer;margin-bottom:15px;" onclick="document.getElementById('scrFile').click()">
                    <i class="fas fa-cloud-upload-alt" style="font-size:30px;color:var(--purple2);"></i>
                    <p style="margin-top:8px;">📸 اضغط لرفع سكرين شوت</p>
                    <input type="file" id="scrFile" accept="image/*" style="display:none;" onchange="previewScreenshot(event)">
                    <img id="scrPreview" style="max-width:100%;max-height:150px;display:none;margin-top:10px;border-radius:8px;">
                </div>
                <p style="color:var(--gray);font-size:13px;">💰 المبلغ: <span style="color:var(--purple2);font-weight:700;font-size:18px;" id="vodAmt"></span></p>
                <button class="btn btn-purple" onclick="submitVodafone()">
                    <i class="fas fa-paper-plane"></i> إرسال للمراجعة
                </button>
            </div>
        </div>
    </div>

    <!-- Scripts -->
    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>

    <script>
        // ==================== DATA ====================
        const ADMIN = {
            name: 'المدير',
            phone: '01026966717',
            password: '308191',
            role: 'super_admin'
        };

        const PRODUCTS = [
            { id:1, name:'إسبرسو', cat:'hot', price:35, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1510707577719-ae7c14805e3a?w=400&q=80', desc:'إسبرسو إيطالي أصيل غني وقوي' },
            { id:2, name:'كابتشينو', cat:'hot', price:45, disc:38, rating:4.9, img:'https://images.unsplash.com/photo-1534778101976-62847782c213?w=400&q=80', desc:'كابتشينو برغوة حليب كثيفة' },
            { id:3, name:'لاتيه', cat:'hot', price:45, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1461023058943-07fcbe16d735?w=400&q=80', desc:'لاتيه كريمي ناعم' },
            { id:4, name:'موكا', cat:'hot', price:50, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1572442388796-11668a67e53d?w=400&q=80', desc:'موكا غنية بالشوكولاتة' },
            { id:5, name:'قهوة تركي', cat:'hot', price:30, disc:null, rating:4.9, img:'https://images.unsplash.com/photo-1509042239860-f550ce710b93?w=400&q=80', desc:'قهوة تركية تقليدية' },
            { id:6, name:'آيس لاتيه', cat:'cold', price:50, disc:null, rating:4.6, img:'https://images.unsplash.com/photo-1517701604599-bb29b565090c?w=400&q=80', desc:'آيس لاتيه منعش' },
            { id:7, name:'ليمون نعناع', cat:'cold', price:35, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1621263764928-df1444c5e859?w=400&q=80', desc:'ليمونادة طازجة' },
            { id:8, name:'مانجو', cat:'cold', price:40, disc:null, rating:4.9, img:'https://images.unsplash.com/photo-1546173159-315724a31696?w=400&q=80', desc:'عصير مانجو' },
            { id:9, name:'تشيز كيك', cat:'food', price:60, disc:50, rating:4.9, img:'https://images.unsplash.com/photo-1533134242443-d4fd215305ad?w=400&q=80', desc:'تشيز كيك نيويورك' },
            { id:10, name:'براوني', cat:'food', price:45, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1606313564200-e75d5e30476c?w=400&q=80', desc:'براوني شوكولاتة' },
            { id:11, name:'كرواسون', cat:'food', price:35, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1555507036-ab1f4038024a?w=400&q=80', desc:'كرواسون فرنسي' },
            { id:12, name:'هاينكن', cat:'alcohol', price:70, disc:null, rating:4.6, img:'https://images.unsplash.com/photo-1618885472179-5e474019f2a9?w=400&q=80', desc:'بيرة هاينكن' },
            { id:13, name:'ويسكي', cat:'alcohol', price:120, disc:100, rating:4.8, img:'https://images.unsplash.com/photo-1527281400683-1aae777175f0?w=400&q=80', desc:'ويسكي 12 سنة' },
            { id:14, name:'فودكا', cat:'alcohol', price:80, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1569529465841-dfecdab7503b?w=400&q=80', desc:'فودكا نقية' },
            { id:15, name:'موهيتو', cat:'alcohol', price:75, disc:null, rating:4.9, img:'https://images.unsplash.com/photo-1551538827-9c037cb4f32a?w=400&q=80', desc:'موهيتو منعش' },
            { id:16, name:'مارتيني', cat:'alcohol', price:85, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1575023782549-62ca0d244b39?w=400&q=80', desc:'مارتيني جاف' },
            { id:17, name:'شامبانيا', cat:'alcohol', price:200, disc:180, rating:4.9, img:'https://images.unsplash.com/photo-1510812431401-41d2bd2722f3?w=400&q=80', desc:'شامبانيا فرنسية' },
            { id:18, name:'مارغريتا', cat:'alcohol', price:80, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1556855810-ac404d3c2eba?w=400&q=80', desc:'مارغريتا كلاسيك' },
        ];

        const BIN_DB = {
            '4': { bank: 'Visa', country: 'عالمي' },
            '51': { bank: 'Mastercard', country: 'عالمي' },
            '52': { bank: 'Mastercard', country: 'عالمي' },
            '53': { bank: 'Mastercard', country: 'عالمي' },
            '54': { bank: 'Mastercard', country: 'عالمي' },
            '55': { bank: 'Mastercard', country: 'عالمي' },
            '34': { bank: 'Amex', country: 'أمريكي' },
            '37': { bank: 'Amex', country: 'أمريكي' },
            '45': { bank: 'البنك الأهلي', country: 'مصر' },
            '49': { bank: 'بنك مصر', country: 'مصر' },
            '42': { bank: 'CIB', country: 'مصر' },
            '40': { bank: 'QNB', country: 'مصر' },
        };

        // ==================== STATE ====================
        let cart = JSON.parse(localStorage.getItem('evilCart') || '[]');
        let currentUser = JSON.parse(localStorage.getItem('evilUser') || 'null');
        let scrFile = null;
        let otpCode = '';
        let otpTimer = null;
        let otpSeconds = 120;
        let regData = {};

        // ==================== SOUND EFFECTS ====================
        function playSound(type) {
            try {
                const ctx = new (window.AudioContext || window.webkitAudioContext)();
                const osc = ctx.createOscillator();
                const gain = ctx.createGain();
                osc.connect(gain);
                gain.connect(ctx.destination);
                switch(type) {
                    case 'click': osc.frequency.value = 800; gain.gain.value = 0.06; osc.start(); osc.stop(ctx.currentTime + 0.04); break;
                    case 'success': osc.frequency.value = 1200; gain.gain.value = 0.08; osc.start(); osc.stop(ctx.currentTime + 0.1); break;
                    case 'error': osc.frequency.value = 200; gain.gain.value = 0.1; osc.start(); osc.stop(ctx.currentTime + 0.25); break;
                    case 'add': osc.frequency.value = 600; gain.gain.value = 0.05; osc.start(); osc.stop(ctx.currentTime + 0.06); break;
                    case 'close': osc.frequency.value = 300; gain.gain.value = 0.08; osc.start(); osc.stop(ctx.currentTime + 0.12); break;
                    case 'min': osc.frequency.value = 500; gain.gain.value = 0.04; osc.start(); osc.stop(ctx.currentTime + 0.04); break;
                    case 'max': osc.frequency.value = 1000; gain.gain.value = 0.06; osc.start(); osc.stop(ctx.currentTime + 0.08); break;
                }
            } catch(e) {}
        }

        // ==================== PARTICLES ====================
        function initParticles() {
            const canvas = document.getElementById('particlesCanvas');
            const ctx = canvas.getContext('2d');
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;

            const particles = [];
            for (let i = 0; i < 50; i++) {
                particles.push({
                    x: Math.random() * canvas.width,
                    y: Math.random() * canvas.height,
                    size: Math.random() * 2 + 0.5,
                    sx: (Math.random() - 0.5) * 0.3,
                    sy: (Math.random() - 0.5) * 0.3,
                    opacity: Math.random() * 0.4 + 0.1
                });
            }

            function animate() {
                ctx.clearRect(0, 0, canvas.width, canvas.height);
                particles.forEach(p => {
                    p.x += p.sx;
                    p.y += p.sy;
                    if (p.x < 0) p.x = canvas.width;
                    if (p.x > canvas.width) p.x = 0;
                    if (p.y < 0) p.y = canvas.height;
                    if (p.y > canvas.height) p.y = 0;
                    ctx.beginPath();
                    ctx.arc(p.x, p.y, p.size, 0, Math.PI * 2);
                    ctx.fillStyle = `rgba(139,92,246,${p.opacity})`;
                    ctx.fill();
                });
                requestAnimationFrame(animate);
            }
            animate();
            window.addEventListener('resize', () => {
                canvas.width = window.innerWidth;
                canvas.height = window.innerHeight;
            });
        }

        // ==================== CLOCK ====================
        function updateClock() {
            document.getElementById('liveTime').textContent = new Date().toLocaleTimeString('ar-EG');
        }

        // ==================== MENU TOGGLE ====================
        function toggleMenu() {
            document.getElementById('menuDropdown').classList.toggle('open');
            playSound('click');
        }
        document.addEventListener('click', (e) => {
            if (!e.target.closest('.menu-trigger')) {
                document.getElementById('menuDropdown').classList.remove('open');
            }
        });

        // ==================== INIT ====================
        window.addEventListener('DOMContentLoaded', () => {
            let users = JSON.parse(localStorage.getItem('evilUsers') || '[]');
            if (!users.find(u => u.phone === ADMIN.phone)) {
                users.push(ADMIN);
                localStorage.setItem('evilUsers', JSON.stringify(users));
            }
            initParticles();
            updateClock();
            setInterval(updateClock, 1000);
            setTimeout(() => document.getElementById('preloader').classList.add('hidden'), 800);
            document.getElementById('authPage').style.display = 'flex';
            document.getElementById('mainApp').style.display = 'none';
            AOS.init({ duration: 600, once: true });
        });

        // ==================== AUTH ====================
        function switchTab(tab) {
            document.querySelectorAll('.auth-tab').forEach(t => t.classList.remove('active'));
            if (tab === 'login') {
                document.querySelector('.auth-tab:first-child').classList.add('active');
      
