<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Evil Bar - إيفل بار</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.rtl.min.css" rel="stylesheet">
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" rel="stylesheet">
    <style>
        :root {
            --bg: #04000d; --purple: #8B5CF6; --purple2: #A78BFA;
            --white: #fff; --gray: #999; --red: #ef4444; --green: #10b981;
            --orange: #f59e0b; --glass: rgba(15,10,35,0.9);
            --border: rgba(139,92,246,0.3);
        }
        * { margin:0; padding:0; box-sizing:border-box; }
        body {
            background: var(--bg); color: var(--white);
            font-family: 'Segoe UI', Tahoma, sans-serif; min-height: 100vh;
        }

        /* Auth */
        #authPage {
            display: flex; min-height: 100vh; align-items: center;
            justify-content: center; padding: 20px;
        }
        .auth-card {
            background: var(--glass); backdrop-filter: blur(20px);
            border: 1px solid var(--border); border-radius: 20px;
            padding: 30px 25px; width: 100%; max-width: 400px;
            box-shadow: 0 0 40px rgba(139,92,246,0.3);
        }
        .auth-card h2 { text-align: center; color: var(--purple2); font-size: 30px; margin-bottom: 20px; }

        .inp {
            width: 100%; padding: 13px 15px; margin-bottom: 10px;
            background: rgba(255,255,255,0.04); border: 1px solid rgba(255,255,255,0.1);
            border-radius: 10px; color: #fff; font-size: 15px;
        }
        .inp:focus { outline: none; border-color: var(--purple); }

        .btn {
            width: 100%; padding: 14px; border: none; border-radius: 10px;
            font-size: 15px; font-weight: 700; cursor: pointer; margin-bottom: 8px;
        }
        .btn-p { background: var(--purple); color: #fff; }
        .btn-p:hover { background: #7C3AED; }
        .btn-o { background: transparent; border: 2px solid var(--border); color: var(--purple2); }
        .btn-r { background: var(--red); color: #fff; }
        .btn-g { background: var(--green); color: #fff; }
        .btn-sm { width: auto; padding: 6px 14px; font-size: 12px; }

        .link { color: var(--purple2); cursor: pointer; font-weight: 600; }
        .link:hover { text-decoration: underline; }

        /* Main */
        #mainApp { display: none; }
        #mainApp.show { display: block; }

        .top-bar {
            background: #020008; padding: 8px 15px; display: flex;
            justify-content: space-between; font-size: 12px; color: var(--gray);
        }
        .navbar {
            background: rgba(4,0,13,0.9); backdrop-filter: blur(20px);
            padding: 12px 15px; display: flex; justify-content: space-between;
            align-items: center; position: sticky; top: 0; z-index: 100;
        }
        .brand { color: var(--purple2); font-size: 22px; font-weight: 900; cursor: pointer; }
        .cart-btn {
            position: relative; background: rgba(139,92,246,0.1);
            border: 1px solid var(--border); color: var(--purple2);
            padding: 8px 14px; border-radius: 50px; cursor: pointer; font-size: 13px;
        }
        .cart-badge {
            position: absolute; top: -6px; right: -6px; background: var(--purple);
            color: #fff; border-radius: 50%; width: 18px; height: 18px;
            font-size: 10px; display: flex; align-items: center; justify-content: center;
        }

        /* Menu */
        .menu-drop { position: relative; }
        .menu-btn {
            background: none; border: none; color: var(--purple2);
            font-size: 22px; cursor: pointer; padding: 5px 10px;
        }
        .menu-content {
            display: none; position: absolute; top: 35px; right: 0;
            background: rgba(15,10,35,0.98); border: 1px solid var(--border);
            border-radius: 12px; padding: 5px; z-index: 200; min-width: 180px;
        }
        .menu-content.show { display: block; }
        .menu-content a {
            display: block; padding: 10px 14px; color: #fff;
            text-decoration: none; border-radius: 8px; font-size: 13px; cursor: pointer;
        }
        .menu-content a:hover { background: rgba(139,92,246,0.2); color: var(--purple2); }

        .hero {
            min-height: 80vh; display: flex; align-items: center;
            justify-content: center; text-align: center; padding: 20px;
        }
        .hero h1 { font-size: 60px; color: var(--purple2); font-weight: 900; }
        .hero p { font-size: 18px; color: var(--gray); margin: 15px 0; }

        .section { padding: 50px 15px; }
        .section-title { text-align: center; font-size: 28px; margin-bottom: 30px; }
        .section-title span { color: var(--purple2); }

        .products-grid {
            display: grid; grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
            gap: 15px; max-width: 1000px; margin: 0 auto;
        }
        .product-card {
            background: rgba(15,10,35,0.9); border: 1px solid rgba(255,255,255,0.05);
            border-radius: 14px; overflow: hidden;
        }
        .product-img { height: 170px; overflow: hidden; position: relative; }
        .product-img img { width: 100%; height: 100%; object-fit: cover; }
        .badge { position: absolute; top: 8px; left: 8px; background: var(--red); color: #fff; padding: 2px 8px; border-radius: 15px; font-size: 10px; }
        .product-body { padding: 14px; }
        .product-body h5 { font-size: 15px; margin-bottom: 3px; }
        .price { color: var(--purple2); font-size: 18px; font-weight: 900; }
        .price-old { text-decoration: line-through; color: #666; font-size: 12px; margin-left: 6px; }
        .btn-add {
            width: 100%; padding: 9px; background: var(--purple); color: #fff;
            border: none; border-radius: 8px; cursor: pointer; font-size: 13px; margin-top: 8px;
        }

        /* Cart */
        .cart-overlay {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.8); z-index: 2000; display: none;
        }
        .cart-overlay.open { display: block; }
        .cart-sidebar {
            position: fixed; top: 0; right: -400px; width: 380px; height: 100%;
            background: #120026; z-index: 2001; transition: right 0.3s;
            border-left: 1px solid var(--border); padding: 20px; overflow-y: auto;
        }
        .cart-sidebar.open { right: 0; }

        /* Modal */
        .modal-overlay {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.9); z-index: 3000; display: none;
            align-items: center; justify-content: center;
        }
        .modal-overlay.open { display: flex; }
        .modal-box {
            background: #120026; border: 1px solid var(--border);
            border-radius: 18px; padding: 22px; width: 90%; max-width: 480px;
        }

        .toast {
            position: fixed; bottom: 20px; right: 20px; z-index: 9999;
            background: #120026; border: 1px solid var(--border);
            padding: 14px 18px; border-radius: 12px; color: #fff; font-weight: 600;
            transform: translateX(120%); transition: 0.3s;
        }
        .toast.show { transform: translateX(0); }
        .toast.ok { border-right: 3px solid var(--green); }
        .toast.err { border-right: 3px solid var(--red); }

        footer { background: #020008; padding: 25px; text-align: center; color: var(--gray); font-size: 13px; }

        @media (max-width: 768px) {
            .hero h1 { font-size: 36px; }
            .cart-sidebar { width: 100%; right: -100%; }
        }
    </style>
</head>
<body>

    <div class="toast" id="toast"></div>

    <!-- AUTH PAGE -->
    <div id="authPage">
        <div class="auth-card">
            <h2>🔥 EVIL BAR</h2>

            <div id="loginForm">
                <input type="text" class="inp" id="loginUser" placeholder="👤 اسم المستخدم">
                <input type="password" class="inp" id="loginPass" placeholder="🔒 كلمة المرور">
                <button class="btn btn-p" onclick="doLogin()">🚀 تسجيل الدخول</button>
                <p style="text-align:center;font-size:11px;color:var(--gray);">
                    المدير: mostafaelsarnoby | 308191
                </p>
            </div>

            <div id="registerForm" style="display:none;">
                <input type="text" class="inp" id="regUser" placeholder="👤 اسم المستخدم">
                <input type="text" class="inp" id="regName" placeholder="👤 الاسم الكامل">
                <input type="tel" class="inp" id="regPhone" placeholder="📱 رقم الهاتف">
                <input type="password" class="inp" id="regPass" placeholder="🔒 كلمة المرور">
                <button class="btn btn-p" onclick="doRegister()">✅ إنشاء حساب</button>
                <button class="btn btn-o" onclick="showLogin()">⬅ العودة للدخول</button>
            </div>

            <p style="text-align:center;margin-top:12px;">
                <span class="link" onclick="showRegister()" id="regLink">📝 إنشاء حساب جديد</span>
                <span class="link" onclick="showLogin()" id="loginLink" style="display:none;">🔑 تسجيل الدخول</span>
            </p>
        </div>
    </div>

    <!-- MAIN APP -->
    <div id="mainApp">
        <div class="top-bar">
            <span>🕐 <span id="liveTime"></span></span>
            <div class="menu-drop">
                <button class="menu-btn" onclick="toggleMenu()">⋮</button>
                <div class="menu-content" id="menuContent">
                    <a onclick="goPage('home');toggleMenu()">🏠 الرئيسية</a>
                    <a onclick="goPage('menu');toggleMenu()">📋 المنيو</a>
                    <a onclick="goPage('drinks');toggleMenu()">🥤 مشروبات</a>
                    <a onclick="goPage('alcohol');toggleMenu()">🍺 خمور</a>
                    <a onclick="goPage('food');toggleMenu()">🍰 حلويات</a>
                    <a onclick="goPage('reserve');toggleMenu()">📅 حجز</a>
                    <a onclick="goPage('dashboard');toggleMenu()" id="dashLink" style="display:none;">📊 لوحة التحكم</a>
                    <a onclick="doLogout();toggleMenu()" style="color:var(--red);">🚪 خروج</a>
                </div>
            </div>
        </div>

        <nav class="navbar">
            <a class="brand" onclick="goPage('home')">🔥 EVIL BAR</a>
            <div style="display:flex;align-items:center;gap:10px;">
                <button class="cart-btn" onclick="toggleCart()">🛒 <span class="cart-badge" id="cartBadge">0</span></button>
                <span style="color:var(--purple2);">👤 <span id="navUser"></span></span>
            </div>
        </nav>

        <div id="pageContent"></div>
        <footer><p>🔥 EVIL BAR © 2024</p></footer>
    </div>

    <!-- Cart -->
    <div class="cart-overlay" id="cartOverlay" onclick="toggleCart()"></div>
    <div class="cart-sidebar" id="cartSidebar">
        <div style="display:flex;justify-content:space-between;margin-bottom:12px;">
            <h4 style="color:var(--purple2);">🛒 السلة</h4>
            <button onclick="toggleCart()" style="background:none;border:none;color:#fff;font-size:18px;cursor:pointer;">✕</button>
        </div>
        <div id="cartItems"></div>
        <hr style="border-color:rgba(255,255,255,0.06);margin:12px 0;">
        <h4>الإجمالي: <span style="color:var(--purple2);" id="cartTotal">0 ج.م</span></h4>
        <button class="btn btn-p" onclick="openPayment()">💳 ادفع</button>
        <button class="btn btn-r" onclick="clearCart()" style="margin-top:6px;">🗑 تفريغ</button>
    </div>

    <!-- Payment -->
    <div class="modal-overlay" id="payModal">
        <div class="modal-box">
            <div style="display:flex;justify-content:space-between;margin-bottom:12px;">
                <h4 style="color:var(--purple2);">💳 الدفع</h4>
                <button onclick="closePayment()" style="background:none;border:none;color:#fff;font-size:18px;cursor:pointer;">✕</button>
            </div>
            <div style="display:flex;gap:5px;margin-bottom:12px;">
                <button class="btn btn-p btn-sm" onclick="switchPay('visa')" style="flex:1;">💳 فيزا</button>
                <button class="btn btn-o btn-sm" onclick="switchPay('vodafone')" style="flex:1;">📱 فودافون كاش</button>
            </div>
            <div id="payVisa">
                <input class="inp" id="cardName" placeholder="👤 الاسم"><input class="inp" id="cardNum" placeholder="💳 رقم البطاقة" maxlength="19" oninput="formatCard(this)">
                <div style="display:flex;gap:8px;"><input class="inp" id="cardExp" placeholder="MM/YY" maxlength="5" style="flex:1;"><input class="inp" id="cardCVV" placeholder="CVV" maxlength="4" type="password" style="flex:1;"></div>
                <p>💰 <span style="color:var(--purple2);" id="visaAmt"></span></p>
                <button class="btn btn-p" onclick="validateVisa()">🔍 فحص ودفع</button>
            </div>
            <div id="payVodafone" style="display:none;">
                <div style="background:#e60000;border-radius:10px;padding:12px;text-align:center;color:#fff;margin-bottom:10px;">📱 فودافون كاش<br><b>01026966717</b> <button onclick="copyVodafone()" style="background:#fff;color:#000;border:none;padding:3px 8px;border-radius:4px;cursor:pointer;">نسخ</button></div>
                <input class="inp" id="senderPhone" placeholder="📱 رقمك"><input class="inp" id="senderName" placeholder="👤 اسمك">
                <div style="border:1px dashed var(--border);border-radius:8px;padding:12px;text-align:center;cursor:pointer;margin-bottom:10px;" onclick="document.getElementById('scrFile').click()">📸 سكرين شوت<input type="file" id="scrFile" accept="image/*" style="display:none;" onchange="prevScr(event)"><img id="scrPreview" style="max-width:100%;max-height:100px;display:none;margin-top:5px;"></div>
                <p>💰 <span style="color:var(--purple2);" id="vodAmt"></span></p>
                <button class="btn btn-p" onclick="submitVodafone()">📤 إرسال</button>
            </div>
        </div>
    </div>

    <script>
        const ADMIN = { username:'mostafaelsarnoby', password:'308191', name:'مصطفى الصرنوبي', role:'super_admin' };
        const PRODUCTS = [
            { id:1, name:'إسبرسو', cat:'hot', price:35, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1510707577719-ae7c14805e3a?w=400', desc:'إسبرسو إيطالي أصيل' },
            { id:2, name:'كابتشينو', cat:'hot', price:45, disc:38, rating:4.9, img:'https://images.unsplash.com/photo-1534778101976-62847782c213?w=400', desc:'كابتشينو برغوة' },
            { id:3, name:'لاتيه', cat:'hot', price:45, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1461023058943-07fcbe16d735?w=400', desc:'لاتيه كريمي' },
            { id:4, name:'موكا', cat:'hot', price:50, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1572442388796-11668a67e53d?w=400', desc:'موكا شوكولاتة' },
            { id:5, name:'قهوة تركي', cat:'hot', price:30, disc:null, rating:4.9, img:'https://images.unsplash.com/photo-1509042239860-f550ce710b93?w=400', desc:'قهوة تركية' },
            { id:6, name:'آيس لاتيه', cat:'cold', price:50, disc:null, rating:4.6, img:'https://images.unsplash.com/photo-1517701604599-bb29b565090c?w=400', desc:'آيس لاتيه' },
            { id:7, name:'ليمون نعناع', cat:'cold', price:35, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1621263764928-df1444c5e859?w=400', desc:'ليمونادة' },
            { id:8, name:'مانجو', cat:'cold', price:40, disc:null, rating:4.9, img:'https://images.unsplash.com/photo-1546173159-315724a31696?w=400', desc:'عصير مانجو' },
            { id:9, name:'تشيز كيك', cat:'food', price:60, disc:50, rating:4.9, img:'https://images.unsplash.com/photo-1533134242443-d4fd215305ad?w=400', desc:'تشيز كيك' },
            { id:10, name:'براوني', cat:'food', price:45, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1606313564200-e75d5e30476c?w=400', desc:'براوني' },
            { id:11, name:'كرواسون', cat:'food', price:35, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1555507036-ab1f4038024a?w=400', desc:'كرواسون' },
            { id:12, name:'هاينكن', cat:'alcohol', price:70, disc:null, rating:4.6, img:'https://images.unsplash.com/photo-1618885472179-5e474019f2a9?w=400', desc:'بيرة هاينكن' },
            { id:13, name:'ويسكي', cat:'alcohol', price:120, disc:100, rating:4.8, img:'https://images.unsplash.com/photo-1527281400683-1aae777175f0?w=400', desc:'ويسكي 12 سنة' },
            { id:14, name:'فودكا', cat:'alcohol', price:80, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1569529465841-dfecdab7503b?w=400', desc:'فودكا نقية' },
            { id:15, name:'موهيتو', cat:'alcohol', price:75, disc:null, rating:4.9, img:'https://images.unsplash.com/photo-1551538827-9c037cb4f32a?w=400', desc:'موهيتو منعش' },
            { id:16, name:'مارتيني', cat:'alcohol', price:85, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1575023782549-62ca0d244b39?w=400', desc:'مارتيني جاف' },
        ];

        let cart = JSON.parse(localStorage.getItem('evilCart')||'[]');
        let currentUser = JSON.parse(localStorage.getItem('evilUser')||'null');
        let scrFile = null;

        // INIT
        window.onload = function() {
            let users = JSON.parse(localStorage.getItem('evilUsers')||'[]');
            if (!users.find(u => u.username === ADMIN.username)) {
                users.push(ADMIN);
                localStorage.setItem('evilUsers', JSON.stringify(users));
            }
            document.getElementById('authPage').style.display = 'flex';
            document.getElementById('mainApp').style.display = 'none';
            setInterval(() => {
                document.getElementById('liveTime').textContent = new Date().toLocaleTimeString('ar-EG');
            }, 1000);
        };

        // MENU
        function toggleMenu() { document.getElementById('menuContent').classList.toggle('show'); }
        document.addEventListener('click', (e) => { if (!e.target.closest('.menu-drop')) document.getElementById('menuContent').classList.remove('show'); });

        // AUTH
        function showRegister() {
            document.getElementById('loginForm').style.display = 'none';
            document.getElementById('registerForm').style.display = 'block';
            document.getElementById('regLink').style.display = 'none';
            document.getElementById('loginLink').style.display = 'inline';
        }
        function showLogin() {
            document.getElementById('loginForm').style.display = 'block';
            document.getElementById('registerForm').style.display = 'none';
            document.getElementById('regLink').style.display = 'inline';
            document.getElementById('loginLink').style.display = 'none';
        }

        function doLogin() {
            const u = document.getElementById('loginUser').value.trim();
            const p = document.getElementById('loginPass').value.trim();
            if (!u || !p) return toast('املأ الحقول', 'err');
            const users = JSON.parse(localStorage.getItem('evilUsers')||'[]');
            const found = users.find(x => x.username === u && x.password === p);
            if (found) { loginSuccess(found); } else { toast('خطأ في البيانات', 'err'); }
        }

        function doRegister() {
            const username = document.getElementById('regUser').value.trim();
            const name = document.getElementById('regName').value.trim();
            const phone = document.getElementById('regPhone').value.trim();
            const pass = document.getElementById('regPass').value.trim();
            if (!username || !name || !phone || !pass) return toast('املأ الحقول', 'err');
            if (pass.length < 8) return toast('كلمة مرور 8 أحرف', 'err');
            let users = JSON.parse(localStorage.getItem('evilUsers')||'[]');
            if (users.find(x => x.username === username)) return toast('اسم المستخدم مستخدم', 'err');
            if (users.find(x => x.phone === phone)) return toast('الهاتف مستخدم', 'err');
            const user = { username, name, phone, password: pass, role: 'user' };
            users.push(user);
            localStorage.setItem('evilUsers', JSON.stringify(users));
            loginSuccess(user);
            toast('✅ تم إنشاء الحساب');
        }

        function loginSuccess(u) {
            currentUser = u;
            localStorage.setItem('evilUser', JSON.stringify(u));
            document.getElementById('authPage').style.display = 'none';
            document.getElementById('mainApp').classList.add('show');
            document.getElementById('mainApp').style.display = 'block';
            document.getElementById('navUser').textContent = u.name;
            if (u.role === 'super_admin') document.getElementById('dashLink').style.display = 'block';
            updateCart();
            goPage('home');
            toast('👋 ' + u.name);
        }

        function doLogout() {
            currentUser = null;
            localStorage.removeItem('evilUser');
            document.getElementById('mainApp').classList.remove('show');
            document.getElementById('mainApp').style.display = 'none';
            document.getElementById('authPage').style.display = 'flex';
            showLogin();
            toast('👋 تم الخروج');
        }

        // PAGES
        function goPage(p) {
            const c = document.getElementById('pageContent');
            switch(p) {
                case 'home': c.innerHTML = `<div class="hero"><div><h1>EVIL BAR</h1><p>أفخم كافيه وبار</p><button class="btn btn-p" style="width:auto;padding:14px 28px;" onclick="goPage('menu')">📋 المنيو</button></div></div><div class="section"><h2 class="section-title"><span>منتجات</span> مميزة</h2><div class="products-grid">${PRODUCTS.filter(x=>[1,3,6,8,9,12,14,16].includes(x.id)).map(p=>productCard(p)).join('')}</div></div>`; break;
                case 'menu': c.innerHTML = prodPage(PRODUCTS, '📋 المنيو'); break;
                case 'drinks': c.innerHTML = prodPage(PRODUCTS.filter(x=>['hot','cold'].includes(x.cat)), '🥤 مشروبات'); break;
                case 'alcohol': c.innerHTML = prodPage(PRODUCTS.filter(x=>x.cat==='alcohol'), '🍺 خمور'); break;
                case 'food': c.innerHTML = prodPage(PRODUCTS.filter(x=>x.cat==='food'), '🍰 حلويات'); break;
                case 'reserve': c.innerHTML = `<div class="section"><div style="max-width:450px;margin:0 auto;background:var(--glass);border:1px solid var(--border);border-radius:16px;padding:25px;"><h3 style="color:var(--purple2);text-align:center;">📅 حجز</h3><input class="inp" placeholder="الأشخاص"><input class="inp" type="date"><input class="inp" type="time"><button class="btn btn-p" onclick="toast('✅ تم')">تأكيد</button></div></div>`; break;
                case 'dashboard': c.innerHTML = (currentUser&&currentUser.role==='super_admin')?dashPage():'<p style="text-align:center;padding:80px;">⛔ غير مصرح</p>'; break;
            }
            window.scrollTo(0,0);
        }

        function prodPage(items, t) { return `<div class="section"><h2 class="section-title"><span>${t}</span></h2><div class="products-grid">${items.map(p=>productCard(p)).join('')}</div></div>`; }
        function productCard(p) {
            const pr = p.disc || p.price;
            return `<div class="product-card"><div class="product-img"><img src="${p.img}" alt="${p.name}">${p.disc?`<span class="badge">-${Math.round((1-p.disc/p.price)*100)}%</span>`:''}</div><div class="product-body"><h5>${p.name}</h5><p style="color:var(--gray);font-size:11px;">${p.desc}</p><div>${p.disc?`<span class="price-old">${p.price}ج.م</span>`:''}<span class="price">${pr} ج.م</span></div><button class="btn-add" onclick="addToCart(${p.id})">🛒 أضف</button></div></div>`;
        }

        function dashPage() {
            const users = JSON.parse(localStorage.getItem('evilUsers')||'[]');
            const payments = JSON.parse(localStorage.getItem('evilPayments')||'[]');
            const pending = payments.filter(p=>p.status==='قيد المراجعة');
            const rev = payments.filter(p=>p.status==='مكتمل').reduce((s,p)=>s+p.amount,0);
            return `<div class="section"><h2 class="section-title">📊 <span>لوحة التحكم</span></h2><p style="text-align:center;color:var(--purple2);">👑 ${currentUser.name}</p><div style="display:grid;grid-template-columns:repeat(auto-fill,minmax(150px,1fr));gap:12px;max-width:800px;margin:0 auto 20px;"><div style="background:rgba(15,10,35,0.9);border:1px solid rgba(255,255,255,0.05);border-radius:12px;padding:18px;text-align:center;"><h2 style="color:var(--purple2);">${users.length}</h2><p>👥 مستخدمين</p></div><div style="background:rgba(15,10,35,0.9);border:1px solid rgba(255,255,255,0.05);border-radius:12px;padding:18px;text-align:center;"><h2 style="color:var(--purple2);">${payments.length}</h2><p>💳 مدفوعات</p></div><div style="background:rgba(15,10,35,0.9);border:1px solid rgba(255,255,255,0.05);border-radius:12px;padding:18px;text-align:center;"><h2 style="color:var(--purple2);">${rev}ج.م</h2><p>💰 إيرادات</p></div><div style="background:rgba(15,10,35,0.9);border:1px solid rgba(255,255,255,0.05);border-radius:12px;padding:18px;text-align:center;"><h2 style="color:var(--purple2);">${pending.length}</h2><p>⏳ مراجعة</p></div></div>${pending.length>0?`<div style="max-width:800px;margin:15px auto;background:rgba(245,158,11,0.1);border:1px solid var(--orange);border-radius:12px;padding:15px;"><h4 style="color:var(--orange);">⏳ مراجعة</h4>${pending.map(p=>`<div style="background:#120026;padding:10px;border-radius:8px;margin:6px 0;display:flex;justify-content:space-between;"><div><strong>${p.userName}</strong> | ${p.amount}ج.م<br><small>${p.senderPhone||''}</small></div><div><button class="btn btn-g btn-sm" onclick="approve(${p.id})">✅</button><button class="btn btn-r btn-sm" onclick="reject(${p.id})">❌</button></div></div>`).join('')}</div>`:''}</div>`;
        }

        function approve(id) { let p=JSON.parse(localStorage.getItem('evilPayments')||'[]'); const i=p.findIndex(x=>x.id===id); if(i>-1){p[i].status='مكتمل';localStorage.setItem('evilPayments',JSON.stringify(p));goPage('dashboard');toast('✅ تم');} }
        function reject(id) { let p=JSON.parse(localStorage.getItem('evilPayments')||'[]'); const i=p.findIndex(x=>x.id===id); if(i>-1){p[i].status='مرفوض';localStorage.setItem('evilPayments',JSON.stringify(p));goPage('dashboard');toast('❌ تم');} }

        // CART
        function addToCart(id) { const p=PRODUCTS.find(x=>x.id===id); if(!p)return; const ex=cart.find(i=>i.productId===id); if(ex)ex.qty++; else cart.push({productId:id,qty:1,price:p.disc||p.price,name:p.name,img:p.img}); saveCart(); toast('✅ '+p.name); }
        function removeCart(i){cart.splice(i,1);saveCart();} function qtyCart(i,d){cart[i].qty+=d;if(cart[i].qty<=0)cart.splice(i,1);saveCart();}
        function clearCart(){cart=[];saveCart();toast('🗑 تم');} function saveCart(){localStorage.setItem('evilCart',JSON.stringify(cart));updateCart();}
        function updateCart(){
            const cnt=cart.reduce((s,i)=>s+i.qty,0),tot=cart.reduce((s,i)=>s+(i.price*i.qty),0);
            document.getElementById('cartBadge').textContent=cnt; document.getElementById('cartTotal').textContent=tot+' ج.م';
            document.getElementById('visaAmt').textContent=tot+' ج.م'; document.getElementById('vodAmt').textContent=tot+' ج.م';
            const l=document.getElementById('cartItems');
            if(cart.length===0)l.innerHTML='<p style="color:var(--gray);">فارغة</p>';
            else l.innerHTML=cart.map((item,i)=>`<div style="display:flex;align-items:center;gap:6px;padding:6px;margin-bottom:5px;"><span>${item.name}</span> <span style="color:var(--purple2);">${item.price}ج.م×${item.qty}</span> <button onclick="removeCart(${i})" style="background:var(--red);color:#fff;border:none;padding:3px 6px;border-radius:4px;cursor:pointer;">حذف</button></div>`).join('');
        }
        function toggleCart(){document.getElementById('cartSidebar').classList.toggle('open');document.getElementById('cartOverlay').classList.toggle('open');}

        // PAYMENT
        function openPayment(){if(cart.length===0)return toast('سلة فارغة','err');const t=cart.reduce((s,i)=>s+(i.price*i.qty),0);document.getElementById('visaAmt').textContent=t+' ج.م';document.getElementById('vodAmt').textContent=t+' ج.م';document.getElementById('payModal').classList.add('open');}
        function closePayment(){document.getElementById('payModal').classList.remove('open');scrFile=null;document.getElementById('scrPreview').style.display='none';}
        function switchPay(t){document.getElementById('payVisa').style.display=t==='visa'?'block':'none';document.getElementById('payVodafone').style.display=t==='vodafone'?'block':'none';}
        function formatCard(i){let v=i.value.replace(/\D/g,'').substring(0,16);i.value=v.replace(/(\d{4})(?=\d)/g,'$1 ');}
        function luhnCheck(num){let s=0,alt=false;for(let i=num.length-1;i>=0;i--){let d=parseInt(num[i]);if(alt){d*=2;if(d>9)d-=9;}s+=d;alt=!alt;}return s%10===0;}

        function validateVisa(){
            const n=document.getElementById('cardName').value.trim(),num=document.getElementById('cardNum').value.replace(/\s/g,''),exp=document.getElementById('cardExp').value.trim(),cvv=document.getElementById('cardCVV').value.trim();
            if(!n||!luhnCheck(num)||num.length<13||!exp||!cvv||cvv.length<3) return toast('بيانات غير صالحة','err');
            if(/^(\d)\1+$/.test(num)) return toast('بطاقة وهمية','err');
            completePay('💳 فيزا');
        }

        function submitVodafone(){
            const ph=document.getElementById('senderPhone').value.trim(),nm=document.getElementById('senderName').value.trim();
            if(!ph||!nm) return toast('املأ البيانات','err');
            if(!scrFile) return toast('ارفع سكرين شوت','err');
            const t=cart.reduce((s,i)=>s+(i.price*i.qty),0);
            const pay={id:Date.now(),userName:currentUser?.name||'زائر',senderPhone:ph,senderName:nm,method:'📱 فودافون كاش',amount:t,status:'قيد المراجعة',date:new Date().toLocaleDateString('ar-EG')};
            let ps=JSON.parse(localStorage.getItem('evilPayments')||'[]');ps.push(pay);localStorage.setItem('evilPayments',JSON.stringify(ps));
            cart=[];saveCart();closePayment();toggleCart();toast('📤 تم الإرسال');
        }

        function copyVodafone(){navigator.clipboard.writeText('01026966717');toast('📋 تم');}
        function prevScr(e){const f=e.target.files[0];if(f){scrFile=f;const r=new FileReader();r.onload=ev=>{document.getElementById('scrPreview').src=ev.target.result;document.getElementById('scrPreview').style.display='block';};r.readAsDataURL(f);}}

        function completePay(m){
            const t=cart.reduce((s,i)=>s+(i.price*i.qty),0);
            const pay={id:Date.now(),userName:currentUser?.name||'زائر',method:m,amount:t,status:'مكتمل',date:new Date().toLocaleDateString('ar-EG')};
            let ps=JSON.parse(localStorage.getItem('evilPayments')||'[]');ps.push(pay);localStorage.setItem('evilPayments',JSON.stringify(ps));
            cart=[];saveCart();closePayment();toggleCart();toast('🎉 تم! '+t+' ج.م');
        }

        function toast(m,t='ok'){const el=document.getElementById('toast');el.textContent=m;el.className='toast '+t+' show';setTimeout(()=>el.classList.remove('show'),2500);}
    </script>
</body>
</html>
