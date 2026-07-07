<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Evil Bar - إيفل بار | أفخم كافيه وبار</title>
    
    <!-- Bootstrap 5 RTL -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.rtl.min.css" rel="stylesheet">
    <!-- Font Awesome -->
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" rel="stylesheet">
    <!-- AOS -->
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700;900&family=Playfair+Display:wght@400;700;900&family=El+Messiri:wght@400;600;700&display=swap" rel="stylesheet">

    <style>
        :root {
            --bg: #020202;
            --bg2: #0a0a0a;
            --bg3: #111111;
            --gold: #D4AF37;
            --gold2: #FFD700;
            --gold3: #F4D03F;
            --gold-dark: #8B7500;
            --white: #ffffff;
            --gray: #999999;
            --gray2: #666666;
            --red: #e74c3c;
            --green: #2ecc71;
            --blue: #3498db;
            --glass: rgba(15, 15, 15, 0.75);
            --glass2: rgba(20, 20, 20, 0.85);
            --border-gold: rgba(212, 175, 55, 0.25);
            --border-gold2: rgba(212, 175, 55, 0.5);
            --shadow-gold: 0 0 20px rgba(212, 175, 55, 0.2);
            --shadow-gold2: 0 0 40px rgba(212, 175, 55, 0.4);
            --shadow-gold3: 0 0 60px rgba(212, 175, 55, 0.6);
            --radius: 16px;
            --radius2: 24px;
            --transition: all 0.35s cubic-bezier(0.4, 0, 0.2, 1);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }
        html { scroll-behavior: smooth; }
        
        body {
            background: var(--bg);
            color: var(--white);
            font-family: 'Cairo', 'Segoe UI', sans-serif;
            overflow-x: hidden;
            min-height: 100vh;
            line-height: 1.6;
        }

        /* Scrollbar */
        ::-webkit-scrollbar { width: 6px; }
        ::-webkit-scrollbar-track { background: var(--bg); }
        ::-webkit-scrollbar-thumb { background: linear-gradient(var(--gold-dark), var(--gold)); border-radius: 10px; }

        /* ============ PARTICLES CANVAS ============ */
        #particlesCanvas {
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            z-index: 0;
            pointer-events: none;
        }

        /* ============ PRELOADER ============ */
        #preloader {
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: #000;
            z-index: 99999;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
            transition: opacity 0.6s ease, visibility 0.6s ease;
        }
        #preloader.hidden { opacity: 0; visibility: hidden; }
        
        .preloader-ring {
            width: 80px; height: 80px;
            border: 3px solid transparent;
            border-top-color: var(--gold);
            border-right-color: var(--gold2);
            border-radius: 50%;
            animation: preloaderSpin 1.2s cubic-bezier(0.68, -0.55, 0.27, 1.55) infinite;
        }
        @keyframes preloaderSpin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        .preloader-text {
            color: var(--gold);
            font-family: 'Playfair Display', serif;
            font-size: 32px;
            font-weight: 900;
            letter-spacing: 6px;
            margin-top: 20px;
            animation: preloaderPulse 1.5s ease-in-out infinite;
            text-shadow: var(--shadow-gold2);
        }
        @keyframes preloaderPulse {
            0%, 100% { opacity: 1; transform: scale(1); }
            50% { opacity: 0.6; transform: scale(1.06); }
        }

        /* ============ GLASS MORPHISM ============ */
        .glass {
            background: var(--glass);
            backdrop-filter: blur(25px);
            -webkit-backdrop-filter: blur(25px);
            border: 1px solid var(--border-gold);
            border-radius: var(--radius2);
            box-shadow: var(--shadow-gold);
        }
        .glass-card {
            background: var(--glass2);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border: 1px solid var(--border-gold);
            border-radius: var(--radius);
            transition: var(--transition);
        }
        .glass-card:hover {
            border-color: var(--border-gold2);
            box-shadow: var(--shadow-gold2);
            transform: translateY(-4px);
        }

        /* ============ AUTH PAGE ============ */
        #authPage {
            position: relative;
            z-index: 1;
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 20px;
        }
        
        .auth-container {
            width: 100%;
            max-width: 460px;
            animation: authSlideIn 0.7s cubic-bezier(0.22, 0.61, 0.36, 1);
        }
        @keyframes authSlideIn {
            from { opacity: 0; transform: translateY(40px) scale(0.96); }
            to { opacity: 1; transform: translateY(0) scale(1); }
        }

        .auth-header {
            text-align: center;
            margin-bottom: 30px;
        }
        .auth-logo {
            font-family: 'Playfair Display', serif;
            font-size: 46px;
            font-weight: 900;
            background: linear-gradient(135deg, #8B7500 0%, var(--gold) 30%, var(--gold3) 50%, var(--gold) 70%, #8B7500 100%);
            background-size: 300% 300%;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: goldShimmer 4s ease infinite;
            letter-spacing: 8px;
            text-shadow: none;
        }
        @keyframes goldShimmer {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }
        .auth-subtitle {
            color: var(--gray);
            font-size: 15px;
            margin-top: 8px;
            letter-spacing: 2px;
        }

        /* Auth Tabs */
        .auth-tabs {
            display: flex;
            gap: 6px;
            background: rgba(255,255,255,0.03);
            border-radius: 14px;
            padding: 5px;
            margin-bottom: 25px;
        }
        .auth-tab {
            flex: 1;
            padding: 12px 10px;
            text-align: center;
            border: none;
            background: transparent;
            color: var(--gray);
            border-radius: 11px;
            cursor: pointer;
            font-size: 13px;
            font-weight: 600;
            transition: var(--transition);
            font-family: 'Cairo', sans-serif;
            white-space: nowrap;
        }
        .auth-tab.active {
            background: linear-gradient(135deg, var(--gold-dark), var(--gold));
            color: #000;
            font-weight: 700;
            box-shadow: var(--shadow-gold);
        }
        .auth-tab:hover:not(.active) {
            color: var(--white);
            background: rgba(255,255,255,0.05);
        }

        /* Form Inputs */
        .form-group {
            margin-bottom: 16px;
        }
        .form-group label {
            display: block;
            margin-bottom: 6px;
            color: var(--gray2);
            font-size: 12px;
            font-weight: 600;
            letter-spacing: 0.5px;
        }
        .form-input {
            width: 100%;
            padding: 14px 16px;
            background: rgba(255,255,255,0.03);
            border: 1.5px solid rgba(255,255,255,0.1);
            border-radius: 12px;
            color: var(--white);
            font-size: 15px;
            font-family: 'Cairo', sans-serif;
            transition: var(--transition);
        }
        .form-input:focus {
            outline: none;
            border-color: var(--gold);
            box-shadow: 0 0 0 4px rgba(212, 175, 55, 0.08);
            background: rgba(255,255,255,0.06);
        }
        .form-input::placeholder {
            color: rgba(255,255,255,0.2);
        }

        /* Buttons */
        .btn {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            padding: 14px 24px;
            border: none;
            border-radius: 12px;
            font-size: 15px;
            font-weight: 700;
            cursor: pointer;
            transition: var(--transition);
            font-family: 'Cairo', sans-serif;
            letter-spacing: 0.5px;
            width: 100%;
        }
        .btn-gold {
            background: linear-gradient(135deg, #7A6500 0%, var(--gold) 50%, var(--gold3) 100%);
            color: #000;
            position: relative;
            overflow: hidden;
        }
        .btn-gold::after {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent 40%, rgba(255,255,255,0.3) 50%, transparent 60%);
            animation: btnShine 3s infinite;
        }
        @keyframes btnShine {
            0% { transform: translateX(-100%) rotate(45deg); }
            100% { transform: translateX(100%) rotate(45deg); }
        }
        .btn-gold:hover {
            transform: translateY(-3px);
            box-shadow: var(--shadow-gold3);
        }
        .btn-outline {
            background: transparent;
            border: 2px solid var(--border-gold);
            color: var(--gold);
        }
        .btn-outline:hover {
            background: rgba(212,175,55,0.1);
            border-color: var(--gold);
        }
        .btn-google {
            background: #ffffff;
            color: #333;
            font-weight: 600;
            border: 2px solid #ddd;
        }
        .btn-google:hover {
            background: #f5f5f5;
            transform: translateY(-2px);
        }
        .btn-danger {
            background: var(--red);
            color: #fff;
        }
        .btn-success {
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
            animation: fadeSlideIn 0.4s ease;
        }
        .otp-section.active {
            display: block;
        }
        @keyframes fadeSlideIn {
            from { opacity: 0; transform: translateY(-15px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .otp-inputs {
            display: flex;
            gap: 8px;
            justify-content: center;
            margin: 20px 0;
        }
        .otp-inputs input {
            width: 50px;
            height: 55px;
            text-align: center;
            font-size: 24px;
            font-weight: 700;
            background: rgba(255,255,255,0.04);
            border: 2px solid rgba(255,255,255,0.15);
            border-radius: 12px;
            color: var(--gold);
            transition: var(--transition);
            font-family: 'Cairo', sans-serif;
        }
        .otp-inputs input:focus {
            outline: none;
            border-color: var(--gold);
            box-shadow: var(--shadow-gold);
            background: rgba(255,255,255,0.08);
        }
        .timer-text {
            text-align: center;
            color: var(--gold);
            font-weight: 700;
            font-size: 16px;
            margin: 8px 0 15px;
        }
        .timer-text.expired {
            color: var(--red);
        }

        .divider {
            display: flex;
            align-items: center;
            gap: 15px;
            margin: 20px 0;
            color: var(--gray2);
            font-size: 12px;
        }
        .divider::before,
        .divider::after {
            content: '';
            flex: 1;
            height: 1px;
            background: rgba(255,255,255,0.1);
        }

        .auth-link {
            color: var(--gold);
            cursor: pointer;
            text-decoration: none;
            font-weight: 600;
            transition: var(--transition);
        }
        .auth-link:hover {
            color: var(--gold2);
            text-shadow: var(--shadow-gold);
        }

        /* ============ MAIN APP ============ */
        #mainApp {
            display: none;
            position: relative;
            z-index: 1;
        }
        #mainApp.active {
            display: block;
            animation: fadeSlideIn 0.5s ease;
        }

        /* Navbar */
        .navbar-evil {
            position: sticky;
            top: 0;
            z-index: 1000;
            background: rgba(5, 5, 5, 0.85);
            backdrop-filter: blur(30px);
            -webkit-backdrop-filter: blur(30px);
            border-bottom: 1px solid rgba(212, 175, 55, 0.12);
            padding: 10px 0;
            transition: var(--transition);
        }
        .navbar-evil.scrolled {
            box-shadow: 0 5px 30px rgba(0,0,0,0.6);
            background: rgba(2, 2, 2, 0.95);
        }

        .brand {
            font-family: 'Playfair Display', serif;
            font-size: 26px;
            font-weight: 900;
            color: var(--gold);
            text-decoration: none;
            letter-spacing: 4px;
            transition: var(--transition);
        }
        .brand:hover {
            color: var(--gold2);
            text-shadow: var(--shadow-gold2);
        }

        .nav-link {
            color: var(--white) !important;
            margin: 0 3px;
            padding: 8px 14px !important;
            border-radius: 10px;
            cursor: pointer;
            font-weight: 600;
            font-size: 13px;
            transition: var(--transition);
            text-decoration: none;
        }
        .nav-link:hover,
        .nav-link.active {
            color: var(--gold) !important;
            background: rgba(212, 175, 55, 0.08);
        }

        .nav-btn {
            padding: 8px 14px;
            border-radius: 50px;
            cursor: pointer;
            font-weight: 600;
            font-size: 13px;
            transition: var(--transition);
            border: none;
            font-family: 'Cairo', sans-serif;
        }
        .nav-btn-cart {
            background: transparent;
            border: 1.5px solid rgba(255,255,255,0.2);
            color: var(--white);
            position: relative;
        }
        .nav-btn-cart:hover {
            border-color: var(--gold);
            color: var(--gold);
        }
        .nav-btn-user {
            background: rgba(212,175,55,0.1);
            border: 1.5px solid var(--border-gold);
            color: var(--gold);
        }
        .nav-btn-user:hover {
            background: var(--gold);
            color: #000;
        }
        .cart-badge {
            position: absolute;
            top: -7px;
            right: -7px;
            background: var(--gold);
            color: #000;
            border-radius: 50%;
            width: 22px;
            height: 22px;
            font-size: 11px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 900;
            animation: badgePop 0.3s ease;
        }
        @keyframes badgePop {
            0% { transform: scale(0); }
            50% { transform: scale(1.3); }
            100% { transform: scale(1); }
        }

        /* Hero */
        .hero {
            min-height: 90vh;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            position: relative;
            background: radial-gradient(ellipse at center, rgba(212,175,55,0.05) 0%, transparent 70%);
        }
        .hero-content {
            position: relative;
            z-index: 1;
        }
        .hero-title {
            font-family: 'Playfair Display', serif;
            font-size: clamp(50px, 10vw, 100px);
            font-weight: 900;
            background: linear-gradient(135deg, #6B5B00, var(--gold), var(--gold3), var(--gold));
            background-size: 300% 300%;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: goldShimmer 5s ease infinite;
            letter-spacing: 10px;
            line-height: 1.2;
        }
        .hero-subtitle {
            font-size: clamp(16px, 2.5vw, 22px);
            color: var(--gray);
            margin: 20px 0 30px;
            letter-spacing: 3px;
            animation: fadeSlideIn 1s ease 0.3s both;
        }
        .hero-btns {
            display: flex;
            gap: 15px;
            justify-content: center;
            flex-wrap: wrap;
            animation: fadeSlideIn 1s ease 0.6s both;
        }
        .hero-btn {
            padding: 16px 35px;
            border-radius: 50px;
            font-size: 16px;
            font-weight: 700;
            cursor: pointer;
            transition: var(--transition);
            text-decoration: none;
            display: inline-flex;
            align-items: center;
            gap: 8px;
            font-family: 'Cairo', sans-serif;
            letter-spacing: 1px;
        }
        .hero-btn-primary {
            background: linear-gradient(135deg, #7A6500, var(--gold));
            color: #000;
            border: none;
        }
        .hero-btn-primary:hover {
            transform: translateY(-5px);
            box-shadow: var(--shadow-gold3);
        }
        .hero-btn-outline {
            background: transparent;
            border: 2px solid var(--gold);
            color: var(--gold);
        }
        .hero-btn-outline:hover {
            background: var(--gold);
            color: #000;
            transform: translateY(-5px);
        }

        .scroll-indicator {
            position: absolute;
            bottom: 30px;
            left: 50%;
            transform: translateX(-50%);
            animation: bounceDown 2s infinite;
        }
        .scroll-indicator span {
            display: block;
            width: 10px;
            height: 10px;
            border-right: 2px solid var(--gold);
            border-bottom: 2px solid var(--gold);
            transform: rotate(45deg);
            margin: -5px;
            animation: scrollArrow 2s infinite;
        }
        .scroll-indicator span:nth-child(2) { animation-delay: 0.2s; }
        .scroll-indicator span:nth-child(3) { animation-delay: 0.4s; }
        @keyframes scrollArrow {
            0% { opacity: 0; transform: rotate(45deg) translate(-10px, -10px); }
            50% { opacity: 1; }
            100% { opacity: 0; transform: rotate(45deg) translate(10px, 10px); }
        }
        @keyframes bounceDown {
            0%, 100% { transform: translateX(-50%) translateY(0); }
            50% { transform: translateX(-50%) translateY(15px); }
        }

        /* Sections */
        .section {
            padding: 80px 0;
            position: relative;
        }
        .section-dark {
            background: var(--bg2);
        }
        .section-title {
            text-align: center;
            font-size: clamp(28px, 4vw, 40px);
            font-weight: 900;
            margin-bottom: 50px;
            letter-spacing: 2px;
        }
        .section-title .gold-text {
            color: var(--gold);
        }
        .section-title::after {
            content: '';
            display: block;
            width: 80px;
            height: 3px;
            background: linear-gradient(90deg, transparent, var(--gold), transparent);
            margin: 15px auto 0;
        }

        /* Products Grid */
        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
            gap: 22px;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 15px;
        }

        .product-card {
            background: rgba(18, 18, 18, 0.9);
            border: 1px solid rgba(255,255,255,0.06);
            border-radius: 18px;
            overflow: hidden;
            transition: var(--transition);
            position: relative;
        }
        .product-card:hover {
            transform: translateY(-8px);
            border-color: var(--border-gold);
            box-shadow: 0 20px 50px rgba(0,0,0,0.5), var(--shadow-gold);
        }
        .product-img {
            height: 220px;
            overflow: hidden;
            position: relative;
        }
        .product-img img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.6s ease;
        }
        .product-card:hover .product-img img {
            transform: scale(1.1);
        }
        .product-badge {
            position: absolute;
            top: 12px;
            left: 12px;
            background: var(--red);
            color: #fff;
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 11px;
            font-weight: 700;
            animation: pulseBadge 2s infinite;
        }
        @keyframes pulseBadge {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.08); }
        }
        .product-actions {
            position: absolute;
            top: 12px;
            right: 12px;
            display: flex;
            flex-direction: column;
            gap: 7px;
            opacity: 0;
            transform: translateX(15px);
            transition: var(--transition);
        }
        .product-card:hover .product-actions {
            opacity: 1;
            transform: translateX(0);
        }
        .product-act-btn {
            width: 36px;
            height: 36px;
            border-radius: 50%;
            border: none;
            background: rgba(0,0,0,0.7);
            color: var(--gold);
            cursor: pointer;
            transition: var(--transition);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 14px;
            backdrop-filter: blur(10px);
        }
        .product-act-btn:hover {
            background: var(--gold);
            color: #000;
            transform: scale(1.1);
        }
        .product-body {
            padding: 18px;
        }
        .product-body h5 {
            font-size: 17px;
            font-weight: 700;
            margin-bottom: 4px;
        }
        .product-body .desc {
            color: var(--gray);
            font-size: 12px;
            margin-bottom: 10px;
            line-height: 1.4;
        }
        .product-price-row {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 8px;
        }
        .price-old {
            text-decoration: line-through;
            color: var(--gray2);
            font-size: 13px;
        }
        .price-current {
            color: var(--gold);
            font-size: 22px;
            font-weight: 900;
        }
        .product-rating {
            color: var(--gold);
            font-size: 12px;
            margin-bottom: 12px;
        }
        .btn-add {
            width: 100%;
            padding: 11px;
            background: linear-gradient(135deg, #7A6500, var(--gold));
            color: #000;
            border: none;
            border-radius: 10px;
            font-weight: 700;
            cursor: pointer;
            transition: var(--transition);
            font-family: 'Cairo', sans-serif;
            font-size: 14px;
        }
        .btn-add:hover {
            box-shadow: var(--shadow-gold2);
            letter-spacing: 0.5px;
        }

        /* Cart Sidebar */
        .cart-overlay {
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: rgba(0,0,0,0.8);
            z-index: 2000;
            display: none;
            backdrop-filter: blur(5px);
        }
        .cart-overlay.open { display: block; }
        .cart-sidebar {
            position: fixed;
            top: 0; right: -450px;
            width: 400px; height: 100%;
            background: #0d0d0d;
            z-index: 2001;
            transition: right 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            border-left: 1px solid var(--border-gold);
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
            backdrop-filter: blur(8px);
        }
        .modal-overlay.open { display: flex; }
        .modal-dialog {
            background: #111;
            border: 2px solid var(--border-gold);
            border-radius: var(--radius2);
            padding: 28px;
            width: 90%;
            max-width: 480px;
            max-height: 85vh;
            overflow-y: auto;
            animation: modalIn 0.4s cubic-bezier(0.22, 0.61, 0.36, 1);
        }
        @keyframes modalIn {
            from { opacity: 0; transform: scale(0.9) translateY(20px); }
            to { opacity: 1; transform: scale(1) translateY(0); }
        }

        /* Dashboard */
        .dash-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
            gap: 18px;
            margin-bottom: 30px;
        }
        .dash-stat {
            background: rgba(18,18,18,0.9);
            border: 1px solid rgba(255,255,255,0.06);
            border-radius: var(--radius);
            padding: 25px;
            text-align: center;
            transition: var(--transition);
        }
        .dash-stat:hover {
            border-color: var(--border-gold);
            transform: translateY(-3px);
            box-shadow: var(--shadow-gold);
        }
        .dash-stat h2 {
            font-size: 38px;
            font-weight: 900;
            color: var(--gold);
        }
        .dash-stat p {
            color: var(--gray);
            margin-top: 5px;
            font-size: 14px;
        }

        .table-evil {
            width: 100%;
            border-collapse: collapse;
            font-size: 14px;
        }
        .table-evil th {
            background: rgba(212,175,55,0.08);
            color: var(--gold);
            padding: 14px;
            text-align: right;
            font-weight: 700;
            border-bottom: 2px solid var(--border-gold);
        }
        .table-evil td {
            padding: 12px 14px;
            border-bottom: 1px solid rgba(255,255,255,0.04);
        }
        .table-evil tr:hover td {
            background: rgba(255,255,255,0.02);
        }

        /* AI Chat */
        .ai-box {
            background: #080808;
            border: 1px solid var(--border-gold);
            border-radius: var(--radius);
            padding: 18px;
            margin-top: 25px;
        }
        .ai-messages {
            max-height: 280px;
            overflow-y: auto;
            margin-bottom: 12px;
            padding: 8px;
        }
        .ai-msg {
            padding: 10px 14px;
            margin: 6px 0;
            border-radius: 10px;
            font-size: 14px;
            animation: fadeSlideIn 0.3s ease;
        }
        .ai-msg.user {
            background: rgba(255,255,255,0.04);
            text-align: right;
        }
        .ai-msg.bot {
            background: rgba(212,175,55,0.08);
            color: var(--gold);
            text-align: left;
        }

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
            background: #1a1a1a;
            border: 1px solid var(--border-gold);
            padding: 16px 22px;
            border-radius: 14px;
            color: #fff;
            font-weight: 600;
            font-size: 14px;
            animation: toastSlideIn 0.4s cubic-bezier(0.22, 0.61, 0.36, 1);
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
            display: flex;
            align-items: center;
            gap: 10px;
            min-width: 280px;
        }
        .toast-item.success { border-right: 4px solid var(--green); }
        .toast-item.error { border-right: 4px solid var(--red); }
        @keyframes toastSlideIn {
            from { opacity: 0; transform: translateX(80px); }
            to { opacity: 1; transform: translateX(0); }
        }

        /* Footer */
        .footer {
            background: #020202;
            border-top: 1px solid rgba(212,175,55,0.1);
            padding: 40px 20px 25px;
            text-align: center;
        }
        .footer a {
            color: var(--gray);
            text-decoration: none;
            margin: 0 10px;
            transition: var(--transition);
            font-size: 14px;
        }
        .footer a:hover { color: var(--gold); }

        /* Responsive */
        @media (max-width: 768px) {
            .hero-title { font-size: 38px; letter-spacing: 5px; }
            .hero-btn { padding: 12px 25px; font-size: 14px; }
            .cart-sidebar { width: 100%; right: -100%; }
            .products-grid { grid-template-columns: repeat(auto-fill, minmax(155px, 1fr)); gap: 12px; }
            .product-img { height: 160px; }
            .auth-container { padding: 15px; }
        }
    </style>
</head>
<body>

    <!-- Particles -->
    <canvas id="particlesCanvas"></canvas>

    <!-- Preloader -->
    <div id="preloader">
        <div class="preloader-ring"></div>
        <div class="preloader-text">EVIL BAR</div>
    </div>

    <!-- Toast -->
    <div class="toast-container" id="toastContainer"></div>

    <!-- ==================== AUTH PAGE ==================== -->
    <div id="authPage">
        <div class="auth-container">
            <div class="glass" style="padding: 35px 28px;">
                <div class="auth-header">
                    <div class="auth-logo">EVIL BAR</div>
                    <p class="auth-subtitle">✦ أفخم كافيه وبار ✦</p>
                </div>

                <!-- Tabs -->
                <div class="auth-tabs" id="authTabs">
                    <button class="auth-tab active" onclick="switchAuthTab('email')">
                        <i class="fas fa-envelope"></i> البريد
                    </button>
                    <button class="auth-tab" onclick="switchAuthTab('phone')">
                        <i class="fas fa-mobile-alt"></i> الهاتف
                    </button>
                    <button class="auth-tab" onclick="switchAuthTab('google')">
                        <i class="fab fa-google"></i> Google
                    </button>
                </div>

                <!-- Email Login -->
                <div id="tabEmail">
                    <div class="form-group">
                        <label>البريد الإلكتروني أو رقم الهاتف</label>
                        <input type="text" class="form-input" id="loginId" placeholder="example@email.com" dir="ltr">
                    </div>
                    <div class="form-group">
                        <label>كلمة المرور</label>
                        <input type="password" class="form-input" id="loginPass" placeholder="••••••••">
                    </div>
                    <button class="btn btn-gold" onclick="loginEmail()">
                        <i class="fas fa-sign-in-alt"></i> تسجيل الدخول
                    </button>
                    <p style="text-align:center;margin-top:12px;font-size:11px;color:var(--gray2);">
                        المدير: 01026966717 | 308191
                    </p>
                </div>

                <!-- Phone Login -->
                <div id="tabPhone" style="display:none;">
                    <div class="form-group">
                        <label>رقم الهاتف</label>
                        <input type="tel" class="form-input" id="phoneNumber" placeholder="01xxxxxxxxx" dir="ltr">
                        <small style="color:var(--gray2);font-size:11px;">سيصلك رمز تحقق SMS</small>
                    </div>
                    <button class="btn btn-gold" id="btnSendOTP" onclick="sendOTP()">
                        <i class="fas fa-paper-plane"></i> إرسال رمز التحقق
                    </button>

                    <!-- OTP Section -->
                    <div class="otp-section" id="otpSection">
                        <p style="text-align:center;color:var(--gray2);font-size:13px;margin-top:15px;">
                            أدخل رمز التحقق المكون من 6 أرقام
                        </p>
                        <div class="otp-inputs" id="otpInputs">
                            <input type="text" maxlength="1" oninput="otpNext(this)" onkeydown="otpPrev(event,this)" id="otp1">
                            <input type="text" maxlength="1" oninput="otpNext(this)" onkeydown="otpPrev(event,this)" id="otp2">
                            <input type="text" maxlength="1" oninput="otpNext(this)" onkeydown="otpPrev(event,this)" id="otp3">
                            <input type="text" maxlength="1" oninput="otpNext(this)" onkeydown="otpPrev(event,this)" id="otp4">
                            <input type="text" maxlength="1" oninput="otpNext(this)" onkeydown="otpPrev(event,this)" id="otp5">
                            <input type="text" maxlength="1" oninput="otpNext(this)" onkeydown="otpPrev(event,this)" id="otp6">
                        </div>
                        <div class="timer-text" id="timerText">02:00</div>
                        <button class="btn btn-gold" onclick="verifyOTP()">
                            <i class="fas fa-check-circle"></i> تأكيد الرمز
                        </button>
                        <button class="btn btn-outline" style="margin-top:8px;" id="btnResend" onclick="sendOTP()" disabled>
                            <i class="fas fa-redo"></i> إعادة الإرسال
                        </button>
                    </div>
                </div>

                <!-- Google Login -->
                <div id="tabGoogle" style="display:none;">
                    <p style="text-align:center;color:var(--gray2);margin-bottom:18px;">
                        اختر حساب Google للمتابعة
                    </p>
                    <button class="btn btn-google" onclick="loginGoogle()">
                        <i class="fab fa-google"></i> تسجيل الدخول بـ Google
                    </button>
                </div>

                <div class="divider"><span>أو</span></div>

                <p style="text-align:center;font-size:13px;">
                    ليس لديك حساب؟
                    <span class="auth-link" onclick="showRegister()">إنشاء حساب جديد</span>
                </p>

                <!-- Register -->
                <div id="registerSection" style="display:none;animation:fadeSlideIn 0.4s ease;">
                    <div class="form-group"><label>الاسم الكامل</label><input type="text" class="form-input" id="regName"></div>
                    <div class="form-group"><label>البريد الإلكتروني</label><input type="email" class="form-input" id="regEmail" dir="ltr"></div>
                    <div class="form-group"><label>رقم الهاتف</label><input type="tel" class="form-input" id="regPhone" dir="ltr"></div>
                    <div class="form-group"><label>كلمة المرور</label><input type="password" class="form-input" id="regPass"></div>
                    <button class="btn btn-gold" onclick="registerUser()">إنشاء حساب</button>
                    <button class="btn btn-outline" style="margin-top:8px;" onclick="hideRegister()">العودة</button>
                </div>
            </div>
        </div>
    </div>

    <!-- ==================== MAIN APP ==================== -->
    <div id="mainApp">
        <!-- Navbar -->
        <nav class="navbar-evil" id="navbar">
            <div class="container">
                <div class="d-flex justify-content-between align-items-center flex-wrap gap-2">
                    <a class="brand" href="#" onclick="showPage('home')">EVIL BAR</a>
                    <div class="d-flex align-items-center gap-2 flex-wrap">
                        <a class="nav-link active" href="#" onclick="showPage('home')">🏠 الرئيسية</a>
                        <a class="nav-link" href="#" onclick="showPage('menu')">📋 المنيو</a>
                        <a class="nav-link" href="#" onclick="showPage('drinks')">🥤 مشروبات</a>
                        <a class="nav-link" href="#" onclick="showPage('alcohol')">🍺 خمور</a>
                        <a class="nav-link" href="#" onclick="showPage('food')">🍰 حلويات</a>
                        <a class="nav-link" href="#" onclick="showPage('reserve')">📅 حجز</a>
                        <a class="nav-link" href="#" id="dashLink" style="display:none;" onclick="showPage('dashboard')">📊 لوحة التحكم</a>
                        <button class="nav-btn nav-btn-cart" onclick="toggleCart()">
                            🛒 <span class="cart-badge" id="cartBadge">0</span>
                        </button>
                        <button class="nav-btn nav-btn-user" onclick="showPage('profile')">
                            <i class="fas fa-user"></i> <span id="navUserName"></span>
                        </button>
                        <button class="btn btn-danger btn-sm" onclick="logout()">🚪 خروج</button>
                    </div>
                </div>
            </div>
        </nav>

        <!-- Content -->
        <div id="pageContent"></div>

        <!-- Footer -->
        <footer class="footer">
            <h4 style="color:var(--gold);font-family:'Playfair Display',serif;">EVIL BAR</h4>
            <p style="color:var(--gray);">أفخم كافيه وبار في المدينة | منذ 2020</p>
            <div style="margin:15px 0;">
                <a href="#" onclick="showPage('home')">الرئيسية</a>
                <a href="#" onclick="showPage('menu')">المنيو</a>
                <a href="#">اتصل بنا</a>
                <a href="#">الخصوصية</a>
            </div>
            <p style="color:var(--gray2);font-size:12px;">© 2024 Evil Bar. Developed by <span style="color:var(--gold);">The Developer</span></p>
        </footer>
    </div>

    <!-- Cart Sidebar -->
    <div class="cart-overlay" id="cartOverlay" onclick="toggleCart()"></div>
    <div class="cart-sidebar" id="cartSidebar">
        <div class="d-flex justify-content-between align-items-center mb-3">
            <h5 style="color:var(--gold);"><i class="fas fa-shopping-cart"></i> سلة المشتريات</h5>
            <button class="btn-close btn-close-white" onclick="toggleCart()"></button>
        </div>
        <div id="cartItems"></div>
        <hr style="border-color:rgba(255,255,255,0.08);margin:15px 0;">
        <div class="d-flex justify-content-between align-items-center mb-3">
            <span style="font-size:18px;">الإجمالي:</span>
            <span style="color:var(--gold);font-size:26px;font-weight:900;" id="cartTotal">0 ج.م</span>
        </div>
        <button class="btn btn-gold" onclick="openPayment()"><i class="fas fa-credit-card"></i> ادفع الآن</button>
        <button class="btn btn-outline" style="margin-top:8px;" onclick="clearCart()"><i class="fas fa-trash"></i> تفريغ السلة</button>
    </div>

    <!-- Payment Modal -->
    <div class="modal-overlay" id="paymentModal">
        <div class="modal-dialog">
            <div class="d-flex justify-content-between align-items-center mb-3">
                <h4 style="color:var(--gold);">💳 إتمام الدفع</h4>
                <button class="btn-close btn-close-white" onclick="closePayment()"></button>
            </div>
            <div class="auth-tabs" style="margin-bottom:18px;">
                <button class="auth-tab active" onclick="switchPayTab('visa')">💳 فيزا</button>
                <button class="auth-tab" onclick="switchPayTab('vodafone')">📱 فودافون كاش</button>
            </div>
            <div id="payVisa">
                <div style="background:linear-gradient(135deg,#1a1f71,#2a3f91);border-radius:14px;padding:20px;color:#fff;margin-bottom:15px;">
                    <div style="font-size:28px;font-weight:900;">VISA</div>
                    <div style="font-size:18px;letter-spacing:3px;margin:8px 0;">•••• •••• •••• ••••</div>
                </div>
                <input class="form-input" id="cardName" placeholder="الاسم على البطاقة" style="margin-bottom:10px;">
                <input class="form-input" id="cardNum" placeholder="رقم البطاقة" maxlength="19" oninput="formatCard(this)" style="margin-bottom:10px;" dir="ltr">
                <div style="display:flex;gap:10px;margin-bottom:10px;">
                    <input class="form-input" id="cardExp" placeholder="MM/YY" maxlength="5" style="flex:1;" dir="ltr">
                    <input class="form-input" id="cardCVV" placeholder="CVV" maxlength="3" style="flex:1;" dir="ltr" type="password">
                </div>
                <p style="color:var(--gray);">المبلغ: <span style="color:var(--gold);font-weight:700;" id="visaAmt"></span></p>
                <button class="btn btn-gold" onclick="payVisa()">ادفع بالفيزا</button>
            </div>
            <div id="payVodafone" style="display:none;">
                <div style="background:#e60000;border-radius:14px;padding:20px;text-align:center;color:#fff;margin-bottom:15px;">
                    <h5>📱 فودافون كاش</h5>
                    <div style="font-size:24px;font-weight:900;background:rgba(255,255,255,0.2);padding:12px;border-radius:10px;margin:10px 0;">
                        01026966717
                        <button onclick="copyVodafone()" style="background:#fff;color:#000;border:none;padding:6px 12px;border-radius:6px;cursor:pointer;margin-right:8px;font-weight:700;">📋 نسخ</button>
                    </div>
                    <p style="font-size:13px;">الاسم: Evil Bar</p>
                </div>
                <div style="border:2px dashed rgba(212,175,55,0.4);border-radius:12px;padding:20px;text-align:center;cursor:pointer;margin-bottom:15px;" onclick="document.getElementById('scrFile').click()">
                    <i class="fas fa-cloud-upload-alt" style="font-size:30px;color:var(--gold);"></i>
                    <p style="margin-top:8px;">اضغط لرفع سكرين شوت التحويل</p>
                    <input type="file" id="scrFile" accept="image/*" style="display:none;" onchange="previewScreenshot(event)">
                    <img id="scrPreview" style="max-width:100%;max-height:150px;display:none;margin-top:10px;border-radius:8px;">
                </div>
                <p style="color:var(--gray);">المبلغ: <span style="color:var(--gold);font-weight:700;" id="vodAmt"></span></p>
                <button class="btn btn-gold" onclick="payVodafone()">إرسال إشعار التحويل</button>
            </div>
        </div>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>

    <script>
        // ==================== ADMIN ====================
        const ADMIN = {
            name: 'المدير',
            phone: '01026966717',
            password: '308191',
            role: 'super_admin'
        };

        // ==================== PRODUCTS ====================
        const PRODUCTS = [
            { id:1, name:'إسبرسو', cat:'hot', price:35, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1510707577719-ae7c14805e3a?w=400&q=80', desc:'إسبرسو إيطالي أصيل غني وقوي' },
            { id:2, name:'كابتشينو', cat:'hot', price:45, disc:38, rating:4.9, img:'https://images.unsplash.com/photo-1534778101976-62847782c213?w=400&q=80', desc:'كابتشينو برغوة حليب كثيفة' },
            { id:3, name:'لاتيه', cat:'hot', price:45, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1461023058943-07fcbe16d735?w=400&q=80', desc:'لاتيه كريمي ناعم مع حليب' },
            { id:4, name:'موكا', cat:'hot', price:50, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1572442388796-11668a67e53d?w=400&q=80', desc:'موكا غنية بالشوكولاتة' },
            { id:5, name:'أمريكانو', cat:'hot', price:40, disc:35, rating:4.6, img:'https://images.unsplash.com/photo-1551030173-122aabc4489c?w=400&q=80', desc:'أمريكانو كلاسيكي منعش' },
            { id:6, name:'قهوة تركي', cat:'hot', price:30, disc:null, rating:4.9, img:'https://images.unsplash.com/photo-1509042239860-f550ce710b93?w=400&q=80', desc:'قهوة تركية تقليدية' },
            { id:7, name:'فلات وايت', cat:'hot', price:45, disc:null, rating:4.5, img:'https://images.unsplash.com/photo-1495474472287-4d71bcdd2085?w=400&q=80', desc:'فلات وايت أسترالي' },
            { id:8, name:'آيس لاتيه', cat:'cold', price:50, disc:null, rating:4.6, img:'https://images.unsplash.com/photo-1517701604599-bb29b565090c?w=400&q=80', desc:'آيس لاتيه منعش مثلج' },
            { id:9, name:'آيس موكا', cat:'cold', price:55, disc:48, rating:4.7, img:'https://images.unsplash.com/photo-1461023058943-07fcbe16d735?w=400&q=80', desc:'آيس موكا بالشوكولاتة' },
            { id:10, name:'ليمون نعناع', cat:'cold', price:35, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1621263764928-df1444c5e859?w=400&q=80', desc:'ليمونادة طازجة بالنعناع' },
            { id:11, name:'عصير برتقال', cat:'cold', price:30, disc:null, rating:4.5, img:'https://images.unsplash.com/photo-1621506289937-a8e4df240d0b?w=400&q=80', desc:'عصير برتقال طبيعي 100%' },
            { id:12, name:'مانجو', cat:'cold', price:40, disc:null, rating:4.9, img:'https://images.unsplash.com/photo-1546173159-315724a31696?w=400&q=80', desc:'عصير مانجو طازج' },
            { id:13, name:'سموذي فراولة', cat:'cold', price:45, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1553530666-ba11a7da3888?w=400&q=80', desc:'سموذي فراولة طبيعي' },
            { id:14, name:'مياه معدنية', cat:'cold', price:10, disc:null, rating:4.0, img:'https://images.unsplash.com/photo-1616118132534-381148898bb4?w=400&q=80', desc:'مياه معدنية نقية' },
            { id:15, name:'تشيز كيك', cat:'food', price:60, disc:50, rating:4.9, img:'https://images.unsplash.com/photo-1533134242443-d4fd215305ad?w=400&q=80', desc:'تشيز كيك نيويورك الأصلية' },
            { id:16, name:'براوني', cat:'food', price:45, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1606313564200-e75d5e30476c?w=400&q=80', desc:'براوني شوكولاتة بلجيكية' },
            { id:17, name:'تيراميسو', cat:'food', price:65, disc:null, rating:4.9, img:'https://images.unsplash.com/photo-1571877227200-a0d98ea607e9?w=400&q=80', desc:'تيراميسو إيطالي أصيل' },
            { id:18, name:'كوكيز', cat:'food', price:25, disc:null, rating:4.6, img:'https://images.unsplash.com/photo-1499636136210-6f4ee915583e?w=400&q=80', desc:'كوكيز طازج يومياً' },
            { id:19, name:'كرواسون', cat:'food', price:35, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1555507036-ab1f4038024a?w=400&q=80', desc:'كرواسون فرنسي طازج' },
            { id:20, name:'كيك شوكولاتة', cat:'food', price:70, disc:60, rating:4.9, img:'https://images.unsplash.com/photo-1578985545062-69928b1d9587?w=400&q=80', desc:'كيك شوكولاتة ثلاثي' },
            { id:21, name:'ستيلا', cat:'alcohol', price:60, disc:null, rating:4.5, img:'https://images.unsplash.com/photo-1566633806327-68e152aaf26d?w=400&q=80', desc:'بيرة ستيلا المحلية' },
            { id:22, name:'هاينكن', cat:'alcohol', price:70, disc:null, rating:4.6, img:'https://images.unsplash.com/photo-1618885472179-5e474019f2a9?w=400&q=80', desc:'بيرة هاينكن الهولندية' },
            { id:23, name:'كورونا', cat:'alcohol', price:65, disc:null, rating:4.4, img:'https://images.unsplash.com/photo-1559526324-593bc073d938?w=400&q=80', desc:'بيرة كورونا المكسيكية' },
            { id:24, name:'فودكا', cat:'alcohol', price:80, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1569529465841-dfecdab7503b?w=400&q=80', desc:'فودكا نقية ممتازة' },
            { id:25, name:'أبسولوت', cat:'alcohol', price:90, disc:null, rating:4.7, img:'https://images.unsplash.com/photo-1569529465841-dfecdab7503b?w=400&q=80', desc:'أبسولوت فودكا سويدية' },
            { id:26, name:'سميرنوف', cat:'alcohol', price:75, disc:null, rating:4.5, img:'https://images.unsplash.com/photo-1569529465841-dfecdab7503b?w=400&q=80', desc:'سميرنوف فودكا' },
            { id:27, name:'ويسكي', cat:'alcohol', price:120, disc:100, rating:4.8, img:'https://images.unsplash.com/photo-1527281400683-1aae777175f0?w=400&q=80', desc:'ويسكي سكوتش 12 سنة' },
            { id:28, name:'جاك دانيلز', cat:'alcohol', price:110, disc:null, rating:4.8, img:'https://images.unsplash.com/photo-1580189094344-0b8b452b1e56?w=400&q=80', desc:'جاك دانيلز تينيسي' },
            { id:29, name:'شيفاز', cat:'alcohol', price:130, disc:null, rating:4.9, img:'https://images.unsplash.com/photo-1527281400683-1aae777175f0?w=400&q=80', desc:'شيفاز ريجال 12 سنة' },
            { id:30, name:'بلاك ليبل', cat:'alcohol', pr
