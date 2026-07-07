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
            --bg: #050505; --bg2: #0d0d0d; --gold: #D4AF37; --gold2: #FFD700;
            --white: #fff; --gray: #999; --red: #e74c3c; --green: #2ecc71;
        }
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body {
            background: var(--bg); color: var(--white);
            font-family: 'Segoe UI', Tahoma, sans-serif; min-height: 100vh;
        }
        #preloader {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: #000; z-index: 99999; display: flex;
            align-items: center; justify-content: center; flex-direction: column;
        }
        .loader-spin {
            width: 60px; height: 60px; border: 3px solid #333;
            border-top-color: var(--gold); border-radius: 50%;
            animation: spin 1s linear infinite;
        }
        @keyframes spin { to { transform: rotate(360deg); } }
        .loader-text { color: var(--gold); margin-top: 15px; font-size: 20px; font-weight: bold; }

        /* Auth */
        #authPage {
            min-height: 100vh; display: flex; align-items: center;
            justify-content: center; padding: 20px;
        }
        .auth-box {
            background: #111; border: 1px solid rgba(212,175,55,0.3);
            border-radius: 20px; padding: 30px; width: 100%; max-width: 420px;
        }
        .auth-box h2 { color: var(--gold); text-align: center; margin-bottom: 20px; font-size: 28px; }
        .auth-tabs { display: flex; gap: 5px; margin-bottom: 20px; }
        .auth-tab {
            flex: 1; padding: 10px; text-align: center; background: #222;
            border: 1px solid #333; color: #fff; border-radius: 10px;
            cursor: pointer; font-size: 13px;
        }
        .auth-tab.active { background: var(--gold); color: #000; border-color: var(--gold); font-weight: bold; }
        .inp {
            width: 100%; padding: 12px; margin-bottom: 12px; background: #1a1a1a;
            border: 1px solid #333; border-radius: 10px; color: #fff; font-size: 15px;
        }
        .inp:focus { outline: none; border-color: var(--gold); }
        .btn {
            width: 100%; padding: 14px; border: none; border-radius: 10px;
            font-size: 16px; font-weight: bold; cursor: pointer; margin-bottom: 8px;
        }
        .btn-gold { background: var(--gold); color: #000; }
        .btn-gold:hover { background: #c49b2c; }
        .btn-red { background: var(--red); color: #fff; }
        .btn-green { background: var(--green); color: #fff; }
        .btn-outline { background: transparent; border: 1px solid var(--gold); color: var(--gold); }

        /* Main App */
        #mainApp { display: none; }
        .navbar {
            background: #0a0a0a; border-bottom: 1px solid rgba(212,175,55,0.2);
            padding: 12px 20px; position: sticky; top: 0; z-index: 100;
            display: flex; align-items: center; justify-content: space-between;
            flex-wrap: wrap; gap: 10px;
        }
        .brand { color: var(--gold); font-size: 24px; font-weight: 900; text-decoration: none; }
        .nav-links { display: flex; gap: 10px; flex-wrap: wrap; }
        .nav-links a {
            color: #fff; text-decoration: none; padding: 8px 12px;
            border-radius: 8px; font-size: 14px; cursor: pointer;
        }
        .nav-links a:hover, .nav-links a.active { color: var(--gold); background: rgba(212,175,55,0.1); }

        .hero {
            min-height: 80vh; display: flex; align-items: center; justify-content: center;
            text-align: center; background: linear-gradient(rgba(0,0,0,0.8),rgba(0,0,0,0.9)), url('https://images.unsplash.com/photo-1470337458703-46ad1756a187?w=1920');
            background-size: cover; background-position: center;
        }
        .hero h1 { font-size: 60px; color: var(--gold); font-weight: 900; }
        .hero p { font-size: 20px; color: #ccc; margin: 15px 0; }

        .section { padding: 60px 20px; }
        .section-title { text-align: center; font-size: 32px; margin-bottom: 40px; }
        .gold { color: var(--gold); }

        .products-grid {
            display: grid; grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 20px; max-width: 1200px; margin: 0 auto;
        }
        .product-card {
            background: #111; border: 1px solid #222; border-radius: 15px;
            overflow: hidden; transition: 0.3s;
        }
        .product-card:hover { border-color: var(--gold); transform: translateY(-5px); }
        .product-img { height: 200px; overflow: hidden; position: relative; }
        .product-img img { width: 100%; height: 100%; object-fit: cover; }
        .product-badge {
            position: absolute; top: 10px; left: 10px;
            background: var(--red); color: #fff; padding: 4px 10px;
            border-radius: 20px; font-size: 12px;
        }
        .product-body { padding: 15px; }
        .product-body h5 { margin-bottom: 5px; }
        .product-body .desc { color: #888; font-size: 13px; margin-bottom: 10px; }
        .price { color: var(--gold); font-size: 22px; font-weight: bold; }
        .price-old { text-decoration: line-through; color: #666; font-size: 14px; margin-left: 8px; }

        .cart-sidebar {
            position: fixed; top: 0; right: -400px; width: 380px; height: 100%;
            background: #111; z-index: 200; transition: 0.3s; padding: 20px;
            overflow-y: auto; border-left: 1px solid rgba(212,175,55,0.3);
        }
        .cart-sidebar.open { right: 0; }
        .cart-overlay {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.7); z-index: 199; display: none;
        }
        .cart-overlay.open { display: block; }

        .modal-overlay {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.9); z-index: 300; display: none;
            align-items: center; justify-content: center;
        }
        .modal-overlay.open { display: flex; }
        .modal-box {
            background: #111; border: 2px solid var(--gold); border-radius: 20px;
            padding: 25px; width: 90%; max-width: 500px; max-height: 80vh; overflow-y: auto;
        }

        .dashboard-grid {
            display: grid; grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 15px; margin-bottom: 30px;
        }
        .stat-box {
            background: #111; border: 1px solid #222; border-radius: 15px;
            padding: 20px; text-align: center;
        }
        .stat-box h3 { font-size: 36px; color: var(--gold); }
        .stat-box p { color: #888; }

        .table-dark { width: 100%; border-collapse: collapse; margin-top: 20px; }
        .table-dark th { background: #1a1a1a; color: var(--gold); padding: 12px; text-align: right; }
        .table-dark td { padding: 12px; border-bottom: 1px solid #222; }

        .ai-chat {
            background: #0a0a0a; border: 1px solid rgba(212,175,55,0.3);
            border-radius: 15px; padding: 15px; margin-top: 20px;
        }
        .ai-messages { max-height: 300px; overflow-y: auto; margin-bottom: 10px; }
        .ai-msg { padding: 10px; margin: 5px 0; border-radius: 10px; }
        .ai-msg.user { background: #1a1a1a; }
        .ai-msg.bot { background: rgba(212,175,55,0.1); color: var(--gold); }

        .toast {
            position: fixed; bottom: 20px; right: 20px; z-index: 999;
            padding: 15px 20px; border-radius: 10px; color: #fff; font-weight: bold;
            transform: translateX(120%); transition: 0.3s;
        }
        .toast.show { transform: translateX(0); }
        .toast.ok { background: var(--green); }
        .toast.err { background: var(--red); }

        footer {
            background: #0a0a0a; border-top: 1px solid rgba(212,175,55,0.2);
            padding: 30px; text-align: center; color: #888;
        }

        @media (max-width: 768px) {
            .hero h1 { font-size: 36px; }
            .cart-sidebar { width: 100%; right: -100%; }
            .navbar { flex-direction: column; }
        }
    </style>
</head>
<body>

    <!-- Preloader -->
    <div id="preloader">
        <div class="loader-spin"></div>
        <div class="loader-text">EVIL BAR</div>
    </div>

    <!-- Toast -->
    <div class="toast" id="toast"></div>

    <!-- ========== AUTH PAGE ========== -->
    <div id="authPage">
        <div class="auth-box">
            <h2>🔥 EVIL BAR</h2>
            <div class="auth-tabs">
                <button class="auth-tab active" onclick="switchTab('login')">دخول</button>
                <button class="auth-tab" onclick="switchTab('register')">حساب جديد</button>
            </div>

            <!-- Login -->
            <div id="tabLogin">
                <input type="text" class="inp" id="loginId" placeholder="الهاتف أو البريد" dir="ltr">
                <input type="password" class="inp" id="loginPass" placeholder="كلمة المرور">
                <button class="btn btn-gold" onclick="doLogin()">🚀 دخول</button>
                <button class="btn btn-outline" onclick="googleLogin()"><i class="fab fa-google"></i> Google</button>
                <p style="text-align:center;margin-top:10px;font-size:12px;color:#888;">
                    المدير: 01026966717 | 308191
                </p>
            </div>

            <!-- Register -->
            <div id="tabRegister" style="display:none;">
                <input type="text" class="inp" id="regName" placeholder="الاسم">
                <input type="email" class="inp" id="regEmail" placeholder="البريد" dir="ltr">
                <input type="tel" class="inp" id="regPhone" placeholder="الهاتف" dir="ltr">
                <input type="password" class="inp" id="regPass" placeholder="كلمة المرور">
                <button class="btn btn-gold" onclick="doRegister()">إنشاء حساب</button>
            </div>
        </div>
    </div>

    <!-- ========== MAIN APP ========== -->
    <div id="mainApp">
        <!-- Navbar -->
        <nav class="navbar">
            <a class="brand" href="#" onclick="showPage('home')">🔥 EVIL BAR</a>
            <div class="nav-links">
                <a href="#" onclick="showPage('home')" class="active">الرئيسية</a>
                <a href="#" onclick="showPage('menu')">المنيو</a>
                <a href="#" onclick="showPage('drinks')">🥤 مشروبات</a>
                <a href="#" onclick="showPage('alcohol')">🍺 خمور</a>
                <a href="#" onclick="showPage('food')">🍰 أكل</a>
                <a href="#" onclick="showPage('reserve')">حجز</a>
                <a href="#" id="dashLink" style="display:none;" onclick="showPage('dashboard')">📊 لوحة التحكم</a>
                <a href="#" onclick="showPage('profile')">👤 <span id="navUser"></span></a>
                <button class="btn btn-gold" style="width:auto;padding:8px 15px;font-size:13px;" onclick="toggleCart()">🛒 <span id="cartCount">0</span></button>
                <button class="btn btn-red" style="width:auto;padding:8px 15px;font-size:13px;" onclick="logout()">🚪</button>
            </div>
        </nav>

        <!-- Content -->
        <div id="pageContent"></div>

        <!-- Footer -->
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
        <div id="cartItems"></div>
        <hr style="border-color:#333;margin:15px 0;">
        <h4>الإجمالي: <span style="color:var(--gold);" id="cartTotal">0</span> ج.م</h4>
        <button class="btn btn-gold" onclick="openPayment()" style="margin-top:10px;">💳 ادفع الآن</button>
        <button class="btn btn-red" onclick="clearCart()" style="margin-top:5px;">🗑 تفريغ</button>
    </div>

    <!-- Payment Modal -->
    <div class="modal-overlay" id="paymentModal">
        <div class="modal-box">
            <div style="display:flex;justify-content:space-between;margin-bottom:15px;">
                <h4 style="color:var(--gold);">💳 الدفع</h4>
                <button onclick="closePayment()" style="background:none;border:none;color:#fff;font-size:20px;cursor:pointer;">✕</button>
            </div>
            <div class="auth-tabs" style="margin-bottom:15px;">
                <button class="auth-tab active" onclick="switchPayTab('visa')">💳 فيزا</button>
                <button class="auth-tab" onclick="switchPayTab('vodafone')">📱 فودافون كاش</button>
            </div>
            <div id="payVisa">
                <div style="background:linear-gradient(135deg,#1a1f71,#2a3f91);border-radius:15px;padding:20px;margin-bottom:15px;color:#fff;">
                    <div style="font-size:30px;font-weight:900;">VISA</div>
                    <div style="font-size:20px;letter-spacing:3px;margin:10px 0;" id="visaPreview">•••• •••• •••• ••••</div>
                </div>
                <input class="inp" id="cardName" placeholder="الاسم على البطاقة">
                <input class="inp" id="cardNum" placeholder="رقم البطاقة" maxlength="19" oninput="formatCard(this)">
                <div style="display:flex;gap:10px;">
                    <input class="inp" id="cardExp" placeholder="MM/YY" maxlength="5" style="flex:1;">
                    <input class="inp" id="cardCVV" placeholder="CVV" maxlength="3" style="flex:1;">
                </div>
                <p>المبلغ: <span style="color:var(--gold);" id="visaAmt"></span></p>
                <button class="btn btn-gold" onclick="payVisa()">ادفع بالفيزا</button>
            </div>
            <div id="payVodafone" style="display:none;">
                <div style="background:#e60000;border-radius:15px;padding:20px;text-align:center;color:#fff;margin-bottom:15px;">
                    <h4>📱 فودافون كاش</h4>
                    <div style="font-size:26px;font-weight:900;margin:10px 0;background:rgba(255,255,255,0.2);padding:10px;border-radius:10px;">
                        01026966717
                        <button onclick="copyNum()" style="background:#fff;color:#000;border:none;padding:5px 10px;border-radius:5px;cursor:pointer;margin-right:10px;">نسخ</button>
                    </div>
                    <p>الاسم: Evil Bar</p>
                </div>
                <div style="border:2px dashed rgba(212,175,55,0.4);border-radius:10px;padding:20px;text-align:center;cursor:pointer;margin-bottom:15px;" onclick="document.getElementById('scrFile').click()">
                    📸 اضغط لرفع سكرين شوت التحويل
                    <input type="file" id="scrFile" accept="image/*" style="display:none;" onchange="previewScr(event)">
                    <img id="scrPreview" style="max-width:100%;max-height:150px;display:none;margin-top:10px;border-radius:10px;">
                </div>
                <p>المبلغ: <span style="color:var(--gold);" id="vodAmt"></span></p>
                <button class="btn btn-gold" onclick="payVodafone()">إرسال التحويل</button>
            </div>
        </div>
    </div>

    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
    <script>
        // ========== DATA ==========
        const ADMIN = { name:'المدير', phone:'01026966717', password:'308191', role:'super_admin' };

        const PRODUCTS = [
            // Hot Drinks
            { id:1, name:'إسبرسو', cat:'hot', price:35, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1510707577719-ae7c14805e3a?w=400', desc:'إسبرسو إيطالي أصيل' },
            { id:2, name:'كابتشينو', cat:'hot', price:45, disc:38, rating:4.9, img:'https://images.unsplash.com/photo-1534778101976-62847782c213?w=400', desc:'كابتشينو برغوة كثيفة' },
            { id:3, name:'لاتيه', cat:'hot', price:45, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1461023058943-07fcbe16d735?w=400', desc:'لاتيه كريمي' },
            { id:4, name:'موكا', cat:'hot', price:50, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1572442388796-11668a67e53d?w=400', desc:'موكا شوكولاتة' },
            { id:5, name:'أمريكانو', cat:'hot', price:40, disc:35, rating:4.6, img:'https://images.unsplash.com/photo-1551030173-122aabc4489c?w=400', desc:'أمريكانو كلاسيك' },
            { id:6, name:'قهوة تركي', cat:'hot', price:30, disc:null, rating:4.9, img:'https://images.unsplash.com/photo-1509042239860-f550ce710b93?w=400', desc:'قهوة تركية تقليدية' },
            { id:7, name:'فلات وايت', cat:'hot', price:45, disc:null, rating:4.5, img:'https://images.unsplash.com/photo-1495474472287-4d71bcdd2085?w=400', desc:'فلات وايت أسترالي' },

            // Cold Drinks
            { id:8, name:'آيس لاتيه', cat:'cold', price:50, disc:null, rating:4.6, img:'https://images.unsplash.com/photo-1517701604599-bb29b565090c?w=400', desc:'آيس لاتيه منعش' },
            { id:9, name:'آيس موكا', cat:'cold', price:55, disc:48, rating:4.7, img:'https://images.unsplash.com/photo-1461023058943-07fcbe16d735?w=400', desc:'آيس موكا' },
            { id:10, name:'ليمون نعناع', cat:'cold', price:35, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1621263764928-df1444c5e859?w=400', desc:'ليمونادة طازجة' },
            { id:11, name:'عصير برتقال', cat:'cold', price:30, disc:null, rating:4.5, img:'https://images.unsplash.com/photo-1621506289937-a8e4df240d0b?w=400', desc:'عصير طبيعي' },
            { id:12, name:'مانجو', cat:'cold', price:40, disc:null, rating:4.9, img:'https://images.unsplash.com/photo-1546173159-315724a31696?w=400', desc:'عصير مانجو' },
            { id:13, name:'سموذي فراولة', cat:'cold', price:45, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1553530666-ba11a7da3888?w=400', desc:'سموذي طبيعي' },
            { id:14, name:'مياه معدنية', cat:'cold', price:10, disc:null, rating:4.0, img:'https://images.unsplash.com/photo-1616118132534-381148898bb4?w=400', desc:'مياه نقية' },

            // Food
            { id:15, name:'تشيز كيك', cat:'food', price:60, disc:50, rating:4.9, img:'https://images.unsplash.com/photo-1533134242443-d4fd215305ad?w=400', desc:'تشيز كيك نيويورك' },
            { id:16, name:'براوني', cat:'food', price:45, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1606313564200-e75d5e30476c?w=400', desc:'براوني شوكولاتة' },
            { id:17, name:'تيراميسو', cat:'food', price:65, disc:null, rating:4.9, img:'https://images.unsplash.com/photo-1571877227200-a0d98ea607e9?w=400', desc:'تيراميسو إيطالي' },
            { id:18, name:'كوكيز', cat:'food', price:25, disc:null, rating:4.6, img:'https://images.unsplash.com/photo-1499636136210-6f4ee915583e?w=400', desc:'كوكيز طازج' },
            { id:19, name:'كرواسون', cat:'food', price:35, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1555507036-ab1f4038024a?w=400', desc:'كرواسون فرنسي' },
            { id:20, name:'كيك شوكولاتة', cat:'food', price:70, disc:60, rating:4.9, img:'https://images.unsplash.com/photo-1578985545062-69928b1d9587?w=400', desc:'كيك ثلاثي' },

            // Alcohol
            { id:21, name:'ستيلا', cat:'alcohol', price:60, disc:null, rating:4.5, img:'https://images.unsplash.com/photo-1566633806327-68e152aaf26d?w=400', desc:'بيرة ستيلا' },
            { id:22, name:'هاينكن', cat:'alcohol', price:70, disc:null, rating:4.6, img:'https://images.unsplash.com/photo-1618885472179-5e474019f2a9?w=400', desc:'بيرة هاينكن' },
            { id:23, name:'كورونا', cat:'alcohol', price:65, disc:null, rating:4.4, img:'https://images.unsplash.com/photo-1559526324-593bc073d938?w=400', desc:'بيرة كورونا' },
            { id:24, name:'فودكا', cat:'alcohol', price:80, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1569529465841-dfecdab7503b?w=400', desc:'فودكا نقية' },
            { id:25, name:'أبسولوت', cat:'alcohol', price:90, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1569529465841-dfecdab7503b?w=400', desc:'أبسولوت فودكا' },
            { id:26, name:'سميرنوف', cat:'alcohol', price:75, disc:null, rating:4.5, img:'https://images.unsplash.com/photo-1569529465841-dfecdab7503b?w=400', desc:'سميرنوف فودكا' },
            { id:27, name:'ويسكي', cat:'alcohol', price:120, disc:100, rating:4.8, img:'https://images.unsplash.com/photo-1527281400683-1aae777175f0?w=400', desc:'ويسكي 12 سنة' },
            { id:28, name:'جاك دانيلز', cat:'alcohol', price:110, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1580189094344-0b8b452b1e56?w=400', desc:'جاك دانيلز' },
            { id:29, name:'شيفاز', cat:'alcohol', price:130, disc:null, rating:4.9, img:'https://images.unsplash.com/photo-1527281400683-1aae777175f0?w=400', desc:'شيفاز ريجال' },
            { id:30, name:'بلاك ليبل', cat:'alcohol', price:150, disc:null, rating:4.9, img:'https://images.unsplash.com/photo-1527281400683-1aae777175f0?w=400', desc:'جوني ووكر بلاك' },
            { id:31, name:'ريد ليبل', cat:'alcohol', price:100, disc:null, rating:4.6, img:'https://images.unsplash.com/photo-1527281400683-1aae777175f0?w=400', desc:'جوني ووكر ريد' },
            { id:32, name:'روم', cat:'alcohol', price:85, disc:null, rating:4.5, img:'https://images.unsplash.com/photo-1514218953589-2d7d37efd2dc?w=400', desc:'روم كوبي' },
            { id:33, name:'باكاردي', cat:'alcohol', price:95, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1514218953589-2d7d37efd2dc?w=400', desc:'باكاردي روم' },
            { id:34, name:'جين', cat:'alcohol', price:80, disc:null, rating:4.4, img:'https://images.unsplash.com/photo-1514218953589-2d7d37efd2dc?w=400', desc:'جين لندن' },
            { id:35, name:'تيكيلا', cat:'alcohol', price:90, disc:null, rating:4.6, img:'https://images.unsplash.com/photo-1514218953589-2d7d37efd2dc?w=400', desc:'تيكيلا مكسيكية' },
            { id:36, name:'نبيذ أحمر', cat:'alcohol', price:100, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1510812431401-41d2bd2722f3?w=400', desc:'نبيذ أحمر فرنسي' },
            { id:37, name:'نبيذ أبيض', cat:'alcohol', price:90, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1510812431401-41d2bd2722f3?w=400', desc:'نبيذ أبيض' },
            { id:38, name:'شامبانيا', cat:'alcohol', price:200, disc:180, rating:4.9, img:'https://images.unsplash.com/photo-1510812431401-41d2bd2722f3?w=400', desc:'شامبانيا فرنسية' },
            { id:39, name:'موهيتو', cat:'alcohol', price:75, disc:null, rating:4.9, img:'https://images.unsplash.com/photo-1551538827-9c037cb4f32a?w=400', desc:'موهيتو منعش' },
            { id:40, name:'مارغريتا', cat:'alcohol', price:80, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1556855810-ac404d3c2eba?w=400', desc:'مارغريتا كلاسيك' },
            { id:41, name:'بينا كولادا', cat:'alcohol', price:85, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1551538827-9c037cb4f32a?w=400', desc:'بينا كولادا' },
            { id:42, name:'مارتيني', cat:'alcohol', price:85, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1575023782549-62ca0d244b39?w=400', desc:'مارتيني جاف' },
        ];

        // ========== STATE ==========
        let cart = JSON.parse(localStorage.getItem('ecart') || '[]');
        let user = JSON.parse(localStorage.getItem('euser') || 'null');
        let scrFile = null;

        // ========== INIT ==========
        window.onload = function() {
            // Ensure admin exists
            let users = JSON.parse(localStorage.getItem('eusers') || '[]');
            if (!users.find(u => u.phone === ADMIN.phone)) {
                users.push(ADMIN);
                localStorage.setItem('eusers', JSON.stringify(users));
            }
            // Auto login admin for testing
            if (!user) {
                user = ADMIN;
                localStorage.setItem('euser', JSON.stringify(user));
            }
            // Hide preloader
            setTimeout(() => {
                document.getElementById('preloader').style.display = 'none';
                showMainApp();
            }, 1000);
            AOS.init({ duration: 600, once: true });
        };

        // ========== AUTH ==========
        function switchTab(tab) {
            document.querySelectorAll('.auth-tab').forEach(t => t.classList.remove('active'));
            event.target.classList.add('active');
            document.getElementById('tabLogin').style.display = tab === 'login' ? 'block' : 'none';
            document.getElementById('tabRegister').style.display = tab === 'register' ? 'block' : 'none';
        }

        function doLogin() {
            const id = document.getElementById('loginId').value.trim();
            const pass = document.getElementById('loginPass').value.trim();
            if (!id || !pass) return toast('املأ الحقول', 'err');
            const users = JSON.parse(localStorage.getItem('eusers') || '[]');
            const found = users.find(u => (u.phone === id || u.email === id) && u.password === pass);
            if (found) { user = found; localStorage.setItem('euser', JSON.stringify(user)); showMainApp(); toast('👋 ' + user.name); }
            else toast('بيانات خاطئة', 'err');
        }

        function doRegister() {
            const name = document.getElementById('regName').value.trim();
            const email = document.getElementById('regEmail').value.trim();
            const phone = document.getElementById('regPhone').value.trim();
            const pass = document.getElementById('regPass').value.trim();
            if (!name || !email || !pass) return toast('املأ الحقول', 'err');
            let users = JSON.parse(localStorage.getItem('eusers') || '[]');
            if (users.find(u => u.email === email)) return toast('البريد مستخدم', 'err');
            if (email === ADMIN.email || phone === ADMIN.phone) return toast('لا يمكن', 'err');
            const newUser = { name, email, phone, password: pass, role: 'user' };
            users.push(newUser);
            localStorage.setItem('eusers', JSON.stringify(users));
            user = newUser;
            localStorage.setItem('euser', JSON.stringify(user));
            showMainApp();
            toast('✅ تم التسجيل');
        }

        function googleLogin() {
            const gmail = prompt('أدخل بريد Google:');
            if (gmail) {
                let users = JSON.parse(localStorage.getItem('eusers') || '[]');
                let u = users.find(x => x.email === gmail);
                if (!u) { u = { name: gmail.split('@')[0], email: gmail, phone: '', password: '', role: 'user', google: true }; users.push(u); localStorage.setItem('eusers', JSON.stringify(users)); }
                user = u; localStorage.setItem('euser', JSON.stringify(user)); showMainApp(); toast('👋 ' + u.name);
            }
        }

        function logout() {
            user = null; localStorage.removeItem('euser');
            document.getElementById('mainApp').style.display = 'none';
            document.getElementById('authPage').style.display = 'flex';
            toast('تم الخروج');
        }

        // ========== MAIN APP ==========
        function showMainApp() {
            document.getElementById('authPage').style.display = 'none';
            document.getElementById('mainApp').style.display = 'block';
            document.getElementById('navUser').textContent = user.name;
            if (user.role === 'super_admin') document.getElementById('dashLink').style.display = 'inline';
            updateCart();
            showPage('home');
        }

        function showPage(page) {
            const c = document.getElementById('pageContent');
            let items;
            switch (page) {
                case 'home': c.innerHTML = renderHome(); break;
                case 'menu': c.innerHTML = renderProducts(PRODUCTS, 'المنيو الكامل'); break;
                case 'drinks': items = PRODUCTS.filter(p => p.cat === 'hot' || p.cat === 'cold'); c.innerHTML = renderProducts(items, '🥤 المشروبات'); break;
                case 'alcohol': items = PRODUCTS.filter(p => p.cat === 'alcohol'); c.innerHTML = renderProducts(items, '🍺 المشروبات الكحولية'); break;
                case 'food': items = PRODUCTS.filter(p => p.cat === 'food'); c.innerHTML = renderProducts(items, '🍰 المأكولات والحلويات'); break;
                case 'reserve': c.innerHTML = renderReserve(); break;
                case 'profile': c.innerHTML = renderProfile(); break;
                case 'dashboard': c.innerHTML = user.role === 'super_admin' ? renderDashboard() : '<p>غير مصرح</p>'; break;
            }
            document.querySelectorAll('.nav-links a').forEach(l => l.classList.remove('active'));
            window.scrollTo(0, 0);
        }

        function renderHome() {
            const feat = PRODUCTS.filter(p => [1,3,8,10,15,17,22,27,39].includes(p.id));
            return `
                <div class="hero">
                    <div>
                        <h1>🔥 EVIL BAR</h1>
                        <p>✦ أفخم كافيه وبار في المدينة ✦</p>
                        <button class="btn btn-gold" style="width:auto;display:inline-flex;padding:15px 30px;font-size:18px;" onclick="showPage('menu')">📋 تصفح المنيو</button>
                        <button class="btn btn-outline" style="width:auto;display:inline-flex;padding:15px 30px;font-size:18px;margin-right:10px;" onclick="showPage('reserve')">🍽 حجز طاولة</button>
                    </div>
                </div>
                <div class="section">
                    <h2 class="section-title"><span class="gold">منتجاتنا</span> المميزة</h2>
                    <div class="products-grid">${feat.map(p => productCard(p)).join('')}</div>
                </div>
            `;
        }

        function renderProducts(items, title) {
            return `
                <div class="section">
                    <h2 class="section-title"><span class="gold">${title}</span></h2>
                    <div class="products-grid">${items.map(p => productCard(p)).join('')}</div>
                </div>
            `;
        }

        function productCard(p) {
            const price = p.disc || p.price;
            return `
                <div class="product-card" data-aos="fade-up">
                    <div class="product-img">
                        <img src="${p.img}" alt="${p.name}" onerror="this.src='https://via.placeholder.com/400x250/111/d4af37?text=${p.name}'">
                        ${p.disc ? `<span class="product-badge">-${Math.round((1-p.disc/p.price)*100)}%</span>` : ''}
                    </div>
                    <div class="product-body">
                        <h5>${p.name}</h5>
                        <p class="desc">${p.desc}</p>
                        <div>
                            ${p.disc ? `<span class="price-old">${p.price}ج.م</span>` : ''}
                            <span class="price">${price} ج.م</span>
                        </div>
                        <div style="color:var(--gold);margin:8px 0;">${'★'.repeat(Math.floor(p.rating))} ${p.rating}</div>
                        <button class="btn btn-gold" style="width:100%;padding:10px;font-size:14px;" onclick="addToCart(${p.id})">🛒 أضف للسلة</button>
                    </div>
                </div>
            `;
        }

        function renderReserve() {
            return `
                <div class="section"><div style="max-width:500px;margin:0 auto;background:#111;border:1px solid rgba(212,175,55,0.3);border-radius:20px;padding:30px;">
                    <h3 style="color:var(--gold);text-align:center;">🍽 حجز طاولة</h3>
                    <input class="inp" placeholder="عدد الأشخاص">
                    <input class="inp" type="date">
                    <input class="inp" type="time">
                    <textarea class="inp" rows="3" placeholder="ملاحظات"></textarea>
                    <button class="btn btn-gold" onclick="toast('✅ تم الحجز')">تأكيد</button>
                </div></div>
            `;
        }

        function renderProfile() {
            if (!user) return '';
            return `
                <div class="section"><div style="max-width:500px;margin:0 auto;background:#111;border:1px solid rgba(212,175,55,0.3);border-radius:20px;padding:30px;">
                    <h3 style="color:var(--gold);">👤 ${user.name}</h3>
                    <p>📧 ${user.email || '-'}</p>
                    <p>📱 ${user.phone || '-'}</p>
                    <p>🏷 ${user.role === 'super_admin' ? '👑 مدير النظام' : 'مستخدم'}</p>
                    ${user.google ? '<p>🔗 مسجل عبر Google</p>' : ''}
                </div></div>
            `;
        }

        function renderDashboard() {
            const users = JSON.parse(localStorage.getItem('eusers') || '[]');
            const payments = JSON.parse(localStorage.getItem('epayments') || '[]');
            const orders = JSON.parse(localStorage.getItem('eorders') || '[]');
            const rev = payments.reduce((s, p) => s + p.amount, 0);
            return `
                <div class="section">
                    <h2 class="section-title">📊 <span class="gold">لوحة التحكم</span></h2>
                    <p style="text-align:center;color:var(--gold);">👑 ${user.name} - المدير الرئيسي</p>
                    <div class="dashboard-grid" style="max-width:1200px;margin:0 auto;">
                        <div class="stat-box"><h3>${users.length}</h3><p>👥 مستخدمين</p></div>
                        <div class="stat-box"><h3>${orders.length}</h3><p>📦 طلبات</p></div>
                        <div class="stat-box"><h3>${payments.length}</h3><p>💳 مدفوعات</p></div>
                        <div class="stat-box"><h3>${rev} ج.م</h3><p>💰 إيرادات</p></div>
                        <div class="stat-box"><h3>${PRODUCTS.length}</h3><p>☕ منتجات</p></div>
                    </div>

                    <div style="max-width:1200px;margin:0 auto;">
                        <button class="btn btn-gold" style="width:auto;display:inline-flex;margin:5px;" onclick="addProduct()">➕ إضافة منتج</button>
                        <button class="btn btn-outline" style="width:auto;display:inline-flex;margin:5px;" onclick="editProducts()">✏️ تعديل منتج</button>
                        <button class="btn btn-red" style="width:auto;display:inline-flex;margin:5px;" onclick="deleteProduct()">🗑 حذف منتج</button>
                        <button class="btn btn-green" style="width:auto;display:inline-flex;margin:5px;" onclick="exportData()">📥 تصدير البيانات</button>
                        <button class="btn btn-outline" style="width:auto;display:inline-flex;margin:5px;" onclick="showNotifications()">🔔 الإشعارات</button>
                    </div>

                    <h4 style="color:var(--gold);margin-top:30px;">💳 المدفوعات</h4>
                    <div style="overflow-x:auto;"><table class="table-dark">
                        <tr><th>#</th><th>العميل</th><th>الطريقة</th><th>المبلغ</th><th>التاريخ</th></tr>
                        ${payments.length === 0 ? '<tr><td colspan="5">لا توجد</td></tr>' : payments.reverse().slice(0,20).map(p => `
                            <tr><td>${p.id}</td><td>${p.userName}</td><td>${p.method}</td><td style="color:var(--gold);">${p.amount}ج.م</td><td>${p.date}</td></tr>
                        `).join('')}
                    </table></div>

                    <h4 style="color:var(--gold);margin-top:30px;">👥 المستخدمين</h4>
                    <div style="overflow-x:auto;"><table class="table-dark">
                        <tr><th>الاسم</th><th>الهاتف</th><th>البريد</th><th>الدور</th></tr>
                        ${users.map(u => `<tr><td>${u.name}${u.phone===ADMIN.phone?' 👑':''}</td><td>${u.phone||'-'}</td><td>${u.email||'-'}</td><td>${u.role==='super_admin'?'مدير':'مستخدم'}</td></tr>`).join('')}
                    </table></div>

                    <!-- AI Chat -->
                    <div class="ai-chat">
                        <h4 style="color:var(--gold);">🤖 مساعد Evil Bar الذكي</h4>
                        <div class="ai-messages" id="aiMessages">
                            <div class="ai-msg bot">👋 مرحباً! أنا مساعد Evil Bar. كيف أقدر أساعدك؟</div>
                        </div>
                        <div style="display:flex;gap:10px;">
                            <input class="inp" id="aiInput" placeholder="اسألني أي شيء عن الكافيه..." style="margin:0;" onkeypress="if(event.key==='Enter')sendAI()">
                            <button class="btn btn-gold" style="width:auto;" onclick="sendAI()">إرسال</button>
                        </div>
                    </div>
                </div>
            `;
        }

        function sendAI() {
            const input = document.getElementById('aiInput');
            const msg = input.value.trim();
            if (!msg) return;
            const msgs = document.getElementById('aiMessages');
            msgs.innerHTML += `<div class="ai-msg user">👤 ${msg}</div>`;
            input.value = '';
            const responses = [
                'يمكنك إدارة المنتجات من أزرار لوحة التحكم أعلاه 🛠',
                'إجمالي الإيرادات يظهر في لوحة الإحصائيات 📊',
                'لإضافة منتج جديد اضغط على زر "إضافة منتج" ➕',
                'جميع المدفوعات مسجلة في جدول المدفوعات 💳',
                'يمكنك تصدير البيانات بصيغة JSON 📥',
                'عدد المنتجات الحالي: ' + PRODUCTS.length + ' منتج ☕',
                'المدير الرئيسي هو: ' + ADMIN.name + ' 👑',
                'فودافون كاش: 01026966717 📱',
                'أي استفسار آخر؟ 😊'
            ];
            const reply = responses[Math.floor(Math.random() * responses.length)];
            setTimeout(() => {
                msgs.innerHTML += `<div class="ai-msg bot">🤖 ${reply}</div>`;
                msgs.scrollTop = msgs.scrollHeight;
            }, 500);
        }

        function addProduct() {
            const name = prompt('اسم المنتج:');
            if (!name) return;
            const cat = prompt('الفئة (hot/cold/food/alcohol):');
            const price = parseInt(prompt('السعر:'));
            if (!name || !cat || !price) return;
            PRODUCTS.push({
                id: Date.now(),
                name,
                cat,
                price,
                disc: null,
                rating: 5,
                img: 'https://via.placeholder.com/400x250/111/d4af37?text=' + name,
                desc: 'منتج جديد'
            });
            showPage('dashboard');
            toast('✅ تمت الإضافة');
        }

        function editProducts() {
            const list = PRODUCTS.map((p, i) => `${i+1}. ${p.name} - ${p.price}ج.م`).join('\n');
            const idx = parseInt(prompt('اختر رقم المنتج للتعديل:\n' + list));
            if (!idx || idx < 1 || idx > PRODUCTS.length) return;
            const p = PRODUCTS[idx - 1];
            const name = prompt('الاسم:', p.name);
            const price = parseInt(prompt('السعر:', p.price));
            if (name) p.name = name;
            if (price) p.price = price;
            showPage('dashboard');
            toast('✅ تم التعديل');
        }

        function deleteProduct() {
            const list = PRODUCTS.map((p, i) => `${i+1}. ${p.name}`).join('\n');
            const idx = parseInt(prompt('رقم المنتج للحذف:\n' + list));
            if (!idx || idx < 1 || idx > PRODUCTS.length) return;
            PRODUCTS.splice(idx - 1, 1);
            showPage('dashboard');
            toast('🗑 تم الحذف');
        }

        function exportData() {
            const data = { products: PRODUCTS, payments: JSON.parse(localStorage.getItem('epayments') || '[]'), users: JSON.parse(localStorage.getItem('eusers') || '[]') };
            const blob = new Blob([JSON.stringify(data, null, 2)], { type: 'application/json' });
            const a = document.createElement('a');
            a.href = URL.createObjectURL(blob);
            a.download = 'evil_bar_data.json';
            a.click();
            toast('📥 تم التصدير');
        }

        function showNotifications() {
            const payments = JSON.parse(localStorage.getItem('epayments') || '[]');
            alert('🔔 إشعارات المدفوعات:\n\n' + payments.slice(-5).reverse().map(p => `${p.userName} - ${p.amount}ج.م - ${p.method} - ${p.date}`).join('\n') || 'لا توجد إشعارات');
        }

        // ========== CART ==========
        function addToCart(id) {
            const p = PRODUCTS.find(x => x.id === id);
            if (!p) return;
            const ex = cart.find(i => i.productId === id);
            if (ex) ex.qty++;
            else cart.push({ productId: id, qty: 1, price: p.disc || p.price, name: p.name, img: p.img });
            saveCart();
            toast('✅ ' + p.name);
        }

        function removeFromCart(i) { cart.splice(i, 1); saveCart(); }
        function clearCart() { cart = []; saveCart(); toast('🗑 تم التفريغ'); }
        function saveCart() { localStorage.setItem('ecart', JSON.stringify(cart)); updateCart(); }

        function updateCart() {
            const count = cart.reduce((s, i) => s + i.qty, 0);
            const total = cart.reduce((s, i) => s + (i.price * i.qty), 0);
            document.getElementById('cartCount').textContent = count;
            document.getElementById('cartTotal').textContent = total;
            document.getElementById('visaAmt').textContent = total + ' ج.م';
            document.getElementById('vodAmt').textContent = total + ' ج.م';
            const list = document.getElementById('cartItems');
            if (cart.length === 0) list.innerHTML = '<p style="color:#888;">السلة فارغة</p>';
            else list.innerHTML = cart.map((item, i) => `
                <div style="display:flex;align-items:center;gap:10px;padding:8px;background:#1a1a1a;border-radius:8px;margin-bottom:8px;">
                    <img src="${item.img}" width="40" height="40" style="border-radius:5px;">
                    <div style="flex:1;"><strong>${item.name}</strong><br><small style="color:var(--gold);">${item.price}ج.م × ${item.qty}</small></div>
                    <button onclick="removeFromCart(${i})" style="background:var(--red);color:#fff;border:none;padding:5px 10px;border-radius:5px;cursor:pointer;">🗑</button>
                </div>
            `).join('');
        }

        function toggleCart() {
            document.getElementById('cartSidebar').classList.toggle('open');
            document.getElementById('cartOverlay').classList.toggle('open');
        }

        // ========== PAYMENT ==========
        function openPayment() {
            if (cart.length === 0) return toast('السلة فارغة', 'err');
            const total = cart.reduce((s, i) => s + (i.price * i.qty), 0);
            document.getElementById('visaAmt').textContent = total + ' ج.م';
            document.getElementById('vodAmt').textContent = total + ' ج.م';
            document.getElementById('paymentModal').classList.add('open');
        }

        function closePayment() {
            document.getElementById('paymentModal').classList.remove('open');
            scrFile = null;
            document.getElementById('scrPreview').style.display = 'none';
        }

        function switchPayTab(tab) {
            document.querySelectorAll('#paymentModal .auth-tab').forEach(t => t.classList.remove('active'));
            document.getElementById('payVisa').style.display = tab === 'visa' ? 'block' : 'none';
            document.getElementById('payVodafone').style.display = tab === 'vodafone' ? 'block' : 'none';
            if (tab === 'visa') document.querySelector('#paymentModal .auth-tab:first-child').classList.add('active');
            else document.querySelector('#paymentModal .auth-tab:last-child').classList.add('active');
        }

        function formatCard(input) {
            let v = input.value.replace(/\D/g, '').substring(0, 16);
            input.value = v.replace(/(\d{4})(?=\d)/g, '$1 ');
            document.getElementById('visaPreview').textContent = input.value || '•••• •••• •••• ••••';
        }

        function payVisa() {
            const name = document.getElementById('cardName').value.trim();
            const num = document.getElementById('cardNum').value.replace(/\s/g, '');
            if (!name || num.length < 16) return toast('بيانات البطاقة غير مكتملة', 'err');
            completePayment('فيزا');
        }

        function copyNum() {
            navigator.clipboard.writeText('01026966717');
            toast('📋 تم نسخ الرقم');
        }

        function previewScr(e) {
            const f = e.target.files[0];
            if (f) {
                scrFile = f;
                const r = new FileReader();
                r.onload = ev => {
                    document.getElementById('scrPreview').src = ev.target.result;
                    document.getElementById('scrPreview').style.display = 'block';
                };
                r.readAsDataURL(f);
            }
        }

        function payVodafone() {
            if (!scrFile) return toast('ارفع سكرين شوت التحويل', 'err');
            completePayment('فودافون كاش');
        }

        function completePayment(method) {
            const total = cart.reduce((s, i) => s + (i.price * i.qty), 0);
            const payment = {
                id: Date.now(),
                userName: user?.name || 'زائر',
                userPhone: user?.phone || '',
                method,
                amount: total,
                date: new Date().toLocaleDateString('ar-EG') + ' ' + new Date().toLocaleTimeString('ar-EG'),
                status: 'مكتمل'
            };
            const payments = JSON.parse(localStorage.getItem('epayments') || '[]');
            payments.push(payment);
            localStorage.setItem('epayments', JSON.stringify(payments));
            const orders = JSON.parse(localStorage.getItem('eorders') || '[]');
            orders.push({ ...payment, items: [...cart], status: 'قيد التجهيز' });
            localStorage.setItem('eorders', JSON.stringify(orders));
            cart = [];
            saveCart();
            closePayment();
            toggleCart();
            toast('✅ تم الدفع بنجاح! ' + total + ' ج.م');
        }

        // ========== TOAST ==========
        function toast(msg, type = 'ok') {
            const t = document.getElementById('toast');
            t.textContent = msg;
            t.className = 'toast ' + type + ' show';
            setTimeout(() => t.classList.remove('show'), 3000);
        }
    </script>
</body>
</html>
