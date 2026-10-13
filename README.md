# university-website<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>جامعة المنصورة الأهلية | Mansoura National University</title>
  <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700;900&display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
<style>
  /* ===== المتغيرات ===== */
  :root {
    --primary: #0a2540;
    --secondary: #1e5b8a;
    --accent: #c9a227;
    --accent-light: #e6c757;
    --light: #f8f9fa;
    --white: #ffffff;
    --text: #2c3e50;
    --gray: #6c757d;
    --shadow: 0 10px 40px rgba(0,0,0,0.1);
    --shadow-lg: 0 20px 60px rgba(10,37,64,0.2);
    --transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'Cairo', sans-serif;
    color: var(--text);
    background: var(--white);
    overflow-x: hidden;
    line-height: 1.7;
  }

  /* ===== شريط التنقل ===== */
  header {
    position: fixed;
    top: 0; right: 0; left: 0;
    z-index: 1000;
    background: rgba(255,255,255,0.95);
    backdrop-filter: blur(20px);
    box-shadow: 0 2px 20px rgba(0,0,0,0.08);
    transition: var(--transition);
  }

  .topbar {
    background: var(--primary);
    color: var(--white);
    padding: 8px 5%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-size: 0.85rem;
  }

  .topbar-info span { margin-left: 20px; }
  .topbar-info i { color: var(--accent); margin-left: 5px; }

  .topbar-social a {
    color: var(--white);
    margin-right: 12px;
    transition: var(--transition);
    font-size: 1rem;
  }
  .topbar-social a:hover { color: var(--accent); transform: translateY(-2px); }

  nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 15px 5%;
  }

  .logo {
    display: flex;
    align-items: center;
    gap: 12px;
    font-weight: 900;
    font-size: 1.5rem;
    color: var(--primary);
  }

  .logo-icon {
    width: 50px; height: 50px;
    background: linear-gradient(135deg, var(--primary), var(--secondary));
    border-radius: 12px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: var(--accent);
    font-size: 1.6rem;
    box-shadow: var(--shadow);
  }

  .logo-text small {
    display: block;
    font-size: 0.7rem;
    color: var(--gray);
    font-weight: 400;
    letter-spacing: 2px;
  }

  .nav-menu {
    display: flex;
    list-style: none;
    gap: 35px;
  }

  .nav-menu a {
    text-decoration: none;
    color: var(--text);
    font-weight: 600;
    font-size: 1rem;
    position: relative;
    transition: var(--transition);
    padding: 5px 0;
  }

  .nav-menu a::after {
    content: '';
    position: absolute;
    bottom: -5px; right: 0;
    width: 0; height: 3px;
    background: var(--accent);
    transition: var(--transition);
    border-radius: 3px;
  }

  .nav-menu a:hover { color: var(--secondary); }
  .nav-menu a:hover::after { width: 100%; }

  .btn-nav {
    background: linear-gradient(135deg, var(--accent), var(--accent-light));
    color: var(--primary);
    padding: 12px 28px;
    border-radius: 30px;
    text-decoration: none;
    font-weight: 700;
    transition: var(--transition);
    box-shadow: 0 5px 20px rgba(201,162,39,0.3);
  }

  .btn-nav:hover {
    transform: translateY(-3px);
    box-shadow: 0 10px 30px rgba(201,162,39,0.5);
  }

  .menu-toggle {
    display: none;
    font-size: 1.8rem;
    color: var(--primary);
    cursor: pointer;
    background: none;
    border: none;
  }

  /* ===== Hero Section ===== */
  .hero {
    height: 100vh;
    min-height: 700px;
    position: relative;
    display: flex;
    align-items: center;
    padding: 0 5%;
    margin-top: 100px;
    background: linear-gradient(135deg, rgba(10,37,64,0.9), rgba(30,91,138,0.85)),
                url('https://images.unsplash.com/photo-1562774053-701939374585?w=1920') center/cover;
    overflow: hidden;
  }

  .hero::before {
    content: '';
    position: absolute;
    top: -50%; left: -50%;
    width: 200%; height: 200%;
    background: radial-gradient(circle, rgba(201,162,39,0.15) 0%, transparent 60%);
    animation: rotate 30s linear infinite;
  }

  @keyframes rotate {
    from { transform: rotate(0deg); }
    to { transform: rotate(360deg); }
  }

  .hero-content {
    position: relative;
    z-index: 2;
    max-width: 750px;
    color: var(--white);
    animation: fadeInUp 1.2s ease;
  }

  @keyframes fadeInUp {
    from { opacity: 0; transform: translateY(50px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .hero-badge {
    display: inline-block;
    background: rgba(201,162,39,0.2);
    border: 1px solid var(--accent);
    color: var(--accent);
    padding: 8px 20px;
    border-radius: 30px;
    font-size: 0.9rem;
    font-weight: 600;
    margin-bottom: 25px;
    backdrop-filter: blur(10px);
  }

  .hero h1 {
    font-size: 3.5rem;
    font-weight: 900;
    line-height: 1.2;
    margin-bottom: 20px;
  }

  .hero h1 span {
    background: linear-gradient(135deg, var(--accent), var(--accent-light));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .hero p {
    font-size: 1.2rem;
    margin-bottom: 35px;
    opacity: 0.95;
    max-width: 600px;
  }

  .hero-buttons {
    display: flex;
    gap: 20px;
    flex-wrap: wrap;
  }

  .btn {
    padding: 15px 35px;
    border-radius: 50px;
    text-decoration: none;
    font-weight: 700;
    font-size: 1rem;
    transition: var(--transition);
    display: inline-flex;
    align-items: center;
    gap: 10px;
    cursor: pointer;
    border: none;
    font-family: inherit;
  }

  .btn-primary {
    background: linear-gradient(135deg, var(--accent), var(--accent-light));
    color: var(--primary);
    box-shadow: 0 10px 30px rgba(201,162,39,0.4);
  }

  .btn-primary:hover {
    transform: translateY(-5px);
    box-shadow: 0 15px 40px rgba(201,162,39,0.6);
  }

  .btn-outline {
    background: transparent;
    color: var(--white);
    border: 2px solid var(--white);
  }

  .btn-outline:hover {
    background: var(--white);
    color: var(--primary);
    transform: translateY(-5px);
  }

  /* ===== Stats ===== */
  .stats {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 0;
    background: var(--primary);
    padding: 60px 5%;
    position: relative;
    z-index: 3;
  }

  .stat-item {
    text-align: center;
    color: var(--white);
    padding: 20px;
    border-left: 1px solid rgba(255,255,255,0.1);
    transition: var(--transition);
  }

  .stat-item:first-child { border-left: none; }

  .stat-item:hover { background: rgba(201,162,39,0.1); }

  .stat-icon {
    font-size: 2.5rem;
    color: var(--accent);
    margin-bottom: 15px;
  }

  .stat-number {
    font-size: 2.8rem;
    font-weight: 900;
    color: var(--white);
    line-height: 1;
  }

  .stat-label {
    font-size: 1rem;
    opacity: 0.8;
    margin-top: 8px;
  }

  /* ===== Sections General ===== */
  section { padding: 100px 5%; }

  .section-header {
    text-align: center;
    max-width: 700px;
    margin: 0 auto 70px;
  }

  .section-tag {
    color: var(--accent);
    font-weight: 700;
    font-size: 1rem;
    letter-spacing: 3px;
    text-transform: uppercase;
    margin-bottom: 15px;
    display: block;
  }

  .section-title {
    font-size: 2.8rem;
    font-weight: 900;
    color: var(--primary);
    margin-bottom: 20px;
    line-height: 1.2;
  }

  .section-desc {
    color: var(--gray);
    font-size: 1.1rem;
  }

  /* ===== About ===== */
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 70px;
    align-items: center;
  }

  .about-image {
    position: relative;
    border-radius: 20px;
    overflow: hidden;
    box-shadow: var(--shadow-lg);
  }

  .about-image img {
    width: 100%;
    height: 500px;
    object-fit: cover;
    transition: var(--transition);
  }

  .about-image:hover img { transform: scale(1.05); }

  .about-badge {
    position: absolute;
    bottom: 30px; right: 30px;
    background: var(--accent);
    color: var(--primary);
    padding: 20px 30px;
    border-radius: 15px;
    font-weight: 900;
    font-size: 1.2rem;
    box-shadow: var(--shadow);
  }

  .about-badge span {
    display: block;
    font-size: 2.5rem;
    line-height: 1;
  }

  .about-content h2 {
    font-size: 2.2rem;
    color: var(--primary);
    margin-bottom: 20px;
    font-weight: 900;
  }

  .about-content p {
    color: var(--gray);
    margin-bottom: 20px;
    font-size: 1.05rem;
  }

  .about-features {
    list-style: none;
    margin-top: 30px;
  }

  .about-features li {
    display: flex;
    align-items: center;
    gap: 15px;
    padding: 12px 0;
    font-weight: 600;
    color: var(--text);
  }

  .about-features i {
    width: 35px; height: 35px;
    background: rgba(201,162,39,0.15);
    color: var(--accent);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
  }

  /* ===== Programs ===== */
  .programs { background: var(--light); }

  .programs-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 30px;
  }

  .program-card {
    background: var(--white);
    border-radius: 20px;
    overflow: hidden;
    box-shadow: 0 5px 25px rgba(0,0,0,0.06);
    transition: var(--transition);
    cursor: pointer;
  }

  .program-card:hover {
    transform: translateY(-10px);
    box-shadow: var(--shadow-lg);
  }

  .program-image {
    height: 220px;
    position: relative;
    overflow: hidden;
  }

  .program-image img {
    width: 100%; height: 100%;
    object-fit: cover;
    transition: var(--transition);
  }

  .program-card:hover .program-image img { transform: scale(1.1); }

  .program-icon {
    position: absolute;
    bottom: -25px; right: 25px;
    width: 60px; height: 60px;
    background: linear-gradient(135deg, var(--accent), var(--accent-light));
    border-radius: 15px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.6rem;
    color: var(--primary);
    box-shadow: var(--shadow);
  }

  .program-body {
    padding: 40px 25px 25px;
  }

  .program-body h3 {
    font-size: 1.4rem;
    color: var(--primary);
    margin-bottom: 12px;
    font-weight: 700;
  }

  .program-body p {
    color: var(--gray);
    margin-bottom: 20px;
    font-size: 0.95rem;
  }

  .program-meta {
    display: flex;
    justify-content: space-between;
    padding-top: 20px;
    border-top: 1px solid #eee;
    font-size: 0.9rem;
    color: var(--gray);
  }

  .program-meta i { color: var(--accent); margin-left: 5px; }

  /* ===== News ===== */
  .news-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
    gap: 30px;
  }

  .news-card {
    background: var(--white);
    border-radius: 20px;
    overflow: hidden;
    box-shadow: 0 5px 25px rgba(0,0,0,0.06);
    transition: var(--transition);
  }

  .news-card:hover {
    transform: translateY(-8px);
    box-shadow: var(--shadow-lg);
  }

  .news-image {
    height: 200px;
    overflow: hidden;
    position: relative;
  }

  .news-image img {
    width: 100%; height: 100%;
    object-fit: cover;
    transition: var(--transition);
  }

  .news-card:hover .news-image img { transform: scale(1.1); }

  .news-date {
    position: absolute;
    top: 20px; right: 20px;
    background: var(--accent);
    color: var(--primary);
    padding: 10px 15px;
    border-radius: 10px;
    text-align: center;
    font-weight: 700;
    line-height: 1.2;
  }

  .news-date span { display: block; font-size: 1.5rem; }

  .news-body { padding: 25px; }

  .news-body .category {
    color: var(--accent);
    font-size: 0.85rem;
    font-weight: 700;
    letter-spacing: 1px;
    text-transform: uppercase;
  }

  .news-body h3 {
    color: var(--primary);
    margin: 12px 0;
    font-size: 1.2rem;
    font-weight: 700;
    line-height: 1.4;
  }

  .news-body p { color: var(--gray); font-size: 0.95rem; }

  .news-link {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    color: var(--secondary);
    font-weight: 700;
    text-decoration: none;
    margin-top: 15px;
    transition: var(--transition);
  }

  .news-link:hover { gap: 15px; color: var(--accent); }

  /* ===== CTA ===== */
  .cta {
    background: linear-gradient(135deg, var(--primary), var(--secondary));
    padding: 80px 5%;
    text-align: center;
    color: var(--white);
    position: relative;
    overflow: hidden;
  }

  .cta::before {
    content: '';
    position: absolute;
    top: -50%; right: -20%;
    width: 500px; height: 500px;
    background: radial-gradient(circle, rgba(201,162,39,0.2), transparent);
    border-radius: 50%;
  }

  .cta-content { position: relative; z-index: 2; max-width: 700px; margin: 0 auto; }

  .cta h2 {
    font-size: 2.5rem;
    font-weight: 900;
    margin-bottom: 20px;
  }

  .cta p { font-size: 1.15rem; margin-bottom: 35px; opacity: 0.95; }

  /* ===== Footer ===== */
  footer {
    background: #061729;
    color: #a8b4c0;
    padding: 70px 5% 0;
  }

  .footer-grid {
    display: grid;
    grid-template-columns: 1.5fr 1fr 1fr 1.5fr;
    gap: 50px;
    padding-bottom: 50px;
    border-bottom: 1px solid rgba(255,255,255,0.08);
  }

  .footer-col h4 {
    color: var(--white);
    font-size: 1.2rem;
    margin-bottom: 25px;
    font-weight: 700;
    position: relative;
    padding-bottom: 12px;
  }

  .footer-col h4::after {
    content: '';
    position: absolute;
    bottom: 0; right: 0;
    width: 40px; height: 3px;
    background: var(--accent);
    border-radius: 3px;
  }

  .footer-col p { margin-bottom: 15px; font-size: 0.95rem; }

  .footer-col ul { list-style: none; }
  .footer-col ul li { margin-bottom: 12px; }

  .footer-col ul a {
    color: #a8b4c0;
    text-decoration: none;
    transition: var(--transition);
    font-size: 0.95rem;
    display: inline-flex;
    align-items: center;
    gap: 8px;
  }

  .footer-col ul a:hover { color: var(--accent); padding-right: 5px; }

  .footer-col ul a i { font-size: 0.7rem; }

  .footer-social {
    display: flex;
    gap: 12px;
    margin-top: 20px;
  }

  .footer-social a {
    width: 40px; height: 40px;
    background: rgba(255,255,255,0.08);
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: var(--white);
    text-decoration: none;
    transition: var(--transition);
  }

  .footer-social a:hover {
    background: var(--accent);
    color: var(--primary);
    transform: translateY(-3px);
  }

  .newsletter {
    display: flex;
    background: rgba(255,255,255,0.05);
    border-radius: 10px;
    overflow: hidden;
    margin-top: 15px;
  }

  .newsletter input {
    flex: 1;
    padding: 14px 18px;
    border: none;
    background: transparent;
    color: var(--white);
    font-family: inherit;
    outline: none;
  }

  .newsletter input::placeholder { color: #6b7a8a; }

  .newsletter button {
    background: var(--accent);
    color: var(--primary);
    border: none;
    padding: 0 22px;
    cursor: pointer;
    font-size: 1.1rem;
    transition: var(--transition);
  }

  .newsletter button:hover { background: var(--accent-light); }

  .footer-bottom {
    text-align: center;
    padding: 25px 0;
    font-size: 0.9rem;
  }

  .footer-bottom span { color: var(--accent); font-weight: 700; }

  /* ===== Scroll Top ===== */
  .scroll-top {
    position: fixed;
    bottom: 30px; left: 30px;
    width: 50px; height: 50px;
    background: linear-gradient(135deg, var(--accent), var(--accent-light));
    color: var(--primary);
    border: none;
    border-radius: 50%;
    font-size: 1.2rem;
    cursor: pointer;
    box-shadow: var(--shadow);
    opacity: 0;
    visibility: hidden;
    transition: var(--transition);
    z-index: 999;
  }

  .scroll-top.show { opacity: 1; visibility: visible; }
  .scroll-top:hover { transform: translateY(-5px); }

  /* ===== Responsive ===== */
  @media (max-width: 992px) {
    .hero h1 { font-size: 2.5rem; }
    .about-grid { grid-template-columns: 1fr; gap: 40px; }
    .stats { grid-template-columns: repeat(2, 1fr); }
    .footer-grid { grid-template-columns: 1fr 1fr; }
    .section-title { font-size: 2rem; }
  }

  @media (max-width: 768px) {
    .topbar-info span:not(:first-child) { display: none; }
    .menu-toggle { display: block; }
    .btn-nav { display: none; }

    .nav-menu {
      position: fixed;
      top: 0; right: -100%;
      width: 280px; height: 100vh;
      background: var(--white);
      flex-direction: column;
      padding: 100px 30px;
      gap: 25px;
      box-shadow: -10px 0 40px rgba(0,0,0,0.1);
      transition: var(--transition);
    }

    .nav-menu.active { right: 0; }

    .hero { height: auto; padding: 100px 5% 80px; text-align: center; }
    .hero h1 { font-size: 2rem; }
    .hero p { font-size: 1rem; }
    .hero-buttons { justify-content: center; }

    .stats { grid-template-columns: 1fr 1fr; padding: 40px 5%; }
    .stat-number { font-size: 2rem; }

    section { padding: 70px 5%; }
    .footer-grid { grid-template-columns: 1fr; gap: 35px; }
    .cta h2 { font-size: 1.8rem; }
  }
</style>
</head>
<body>

<!-- ===== Header ===== -->
<header>
  <div class="topbar">
    <div class="topbar-info">
      <span><i class="fas fa-phone"></i> +20 123 456 7890</span>
      <span><i class="fas fa-envelope"></i> info@future.edu</span>
      <span><i class="fas fa-map-marker-alt"></i> القاهرة، مصر</span>
    </div>
    <div class="topbar-social">
      <a href="#"><i class="fab fa-facebook-f"></i></a>
      <a href="#"><i class="fab fa-twitter"></i></a>
      <a href="#"><i class="fab fa-instagram"></i></a>
      <a href="#"><i class="fab fa-linkedin-in"></i></a>
      <a href="#"><i class="fab fa-youtube"></i></a>
    </div>
  </div>

  <nav>
    <div class="logo">
      <div class="logo-icon"><i class="fas fa-graduation-cap"></i></div>
      <div class="logo-text">
        جامعة المستقبل
        <small>FUTURE UNIVERSITY</small>
      </div>
    </div>

    <ul class="nav-menu" id="navMenu">
      <li><a href="#home">الرئيسية</a></li>
      <li><a href="#about">عن الجامعة</a></li>
      <li><a href="#programs">الكليات</a></li>
      <li><a href="#news">الأخبار</a></li>
      <li><a href="#contact">اتصل بنا</a></li>
    </ul>

    <a href="#" class="btn-nav"><i class="fas fa-user-plus"></i> سجل الآن</a>
    <button class="menu-toggle" id="menuToggle"><i class="fas fa-bars"></i></button>
  </nav>
</header>

<!-- ===== Hero ===== -->
<section class="hero" id="home">
  <div class="hero-content">
    <span class="hero-badge"><i class="fas fa-award"></i> جامعة معتمدة دولياً</span>
    <h1>ابنِ <span>مستقبلك</span> معنا بأفضل تعليم جامعي</h1>
    <p>نقدم تعليماً أكاديمياً متميزاً يجمع بين الأصالة والابتكار، مع نخبة من الأساتذة والخبراء في مختلف المجالات لتحقيق طموحاتك.</p>
    <div class="hero-buttons">
      <a href="#programs" class="btn btn-primary"><i class="fas fa-book-open"></i> استكشف الكليات</a>
      <a href="#about" class="btn btn-outline"><i class="fas fa-play"></i> تعرف علينا</a>
    </div>
  </div>
</section>

<!-- ===== Stats ===== -->
<div class="stats">
  <div class="stat-item">
    <div class="stat-icon"><i class="fas fa-user-graduate"></i></div>
    <div class="stat-number" data-count="25000">0</div>
    <div class="stat-label">طالب وطالبة</div>
  </div>
  <div class="stat-item">
    <div class="stat-icon"><i class="fas fa-chalkboard-teacher"></i></div>
    <div class="stat-number" data-count="850">0</div>
    <div class="stat-label">عضو هيئة تدريس</div>
  </div>
  <div class="stat-item">
    <div class="stat-icon"><i class="fas fa-building-columns"></i></div>
    <div class="stat-number" data-count="12">0</div>
    <div class="stat-label">كلية أكاديمية</div>
  </div>
  <div class="stat-item">
    <div class="stat-icon"><i class="fas fa-trophy"></i></div>
    <div class="stat-number" data-count="45">0</div>
    <div class="stat-label">عام من التميز</div>
  </div>
</div>

<!-- ===== About ===== -->
<section id="about">
  <div class="about-grid">
    <div class="about-image">
      <img src="https://images.unsplash.com/photo-1541339907198-e08756dedf3f?w=800" alt="حرم الجامعة">
      <div class="about-badge">
        <span>45+</span>
        عاماً من التميز
      </div>
    </div>

    <div class="about-content">
      <span class="section-tag">من نحن</span>
      <h2>جامعة رائدة في التعليم والبحث العلمي</h2>
      <p>تأسست جامعة المستقبل عام 1980 لتكون منارة للعلم والمعرفة في المنطقة العربية. نسعى لتخريج أجيال قادرة على المنافسة عالمياً ومواكبة متطلبات سوق العمل.</p>
      <p>نوفر بيئة أكاديمية محفزة تجمع بين التعليم النظري والتطبيق العملي، مع شراكات دولية مع أفضل الجامعات العالمية.</p>

      <ul class="about-features">
        <li><i class="fas fa-check"></i> اعتماد أكاديمي دولي معترف به</li>
        <li><i class="fas fa-check"></i> برامج دراسية متطورة ومبتكرة</li>
        <li><i class="fas fa-check"></i> حرم جامعي مجهز بأحدث التقنيات</li>
        <li><i class="fas fa-check"></i> فرص تدريب وتبادل طلابي دولي</li>
      </ul>

      <a href="#" class="btn btn-primary" style="margin-top:25px;"><i class="fas fa-arrow-left"></i> اقرأ المزيد</a>
    </div>
  </div>
</section>

<!-- ===== Programs ===== -->
<section class="programs" id="programs">
  <div class="section-header">
    <span class="section-tag">برامجنا الأكاديمية</span>
    <h2 class="section-title">الكليات والبرامج الدراسية</h2>
    <p class="section-desc">اختر من بين مجموعة واسعة من التخصصات المصممة لتلبية احتياجات سوق العمل</p>
  </div>

  <div class="programs-grid">
    <div class="program-card">
      <div class="program-image">
        <img src="https://images.unsplash.com/photo-1518770660439-4636190af475?w=600" alt="هندسة">
        <div class="program-icon"><i class="fas fa-microchip"></i></div>
      </div>
      <div class="program-body">
        <h3>كلية الهندسة</h3>
        <p>برامج متقدمة في الهندسة المدنية والميكانيكية والكهربائية والروبوتات.</p>
        <div class="program-meta">
          <span><i class="fas fa-clock"></i> 5 سنوات</span>
          <span><i class="fas fa-user-graduate"></i> بكالوريوس</span>
        </div>
      </div>
    </div>

    <div class="program-card">
      <div class="program-image">
        <img src="https://images.unsplash.com/photo-1576091160399-112ba8d25d1d?w=600" alt="طب">
        <div class="program-icon"><i class="fas fa-stethoscope"></i></div>
      </div>
      <div class="program-body">
        <h3>كلية الطب</h3>
        <p>تخريج أطباء مؤهلين وفق أحدث المعايير العالمية مع تدريب عملي مكثف.</p>
        <div class="program-meta">
          <span><i class="fas fa-clock"></i> 6 سنوات</span>
          <span><i class="fas fa-user-graduate"></i> بكالوريوس</span>
        </div>
      </div>
    </div>

    <div class="program-card">
      <div class="program-image">
        <img src="https://images.unsplash.com/photo-1517245386807-bb43f82c33c4?w=600" alt="حاسبات">
        <div class="program-icon"><i class="fas fa-laptop-code"></i></div>
      </div>
      <div class="program-body">
        <h3>كلية الحاسبات والذكاء الاصطناعي</h3>
        <p>برامج في علوم الحاسب، هندسة البرمجيات، والأمن السيبراني والذكاء الاصطناعي.</p>
        <div class="program-meta">
          <span><i class="fas fa-clock"></i> 4 سنوات</span>
          <span><i class="fas fa-user-graduate"></i> بكالوريوس</span>
        </div>
      </div>
    </div>

    <div class="program-card">
      <div class="program-image">
        <img src="https://images.unsplash.com/photo-1554224155-6726b3ff858f?w=600" alt="إدارة">
        <div class="program-icon"><i class="fas fa-chart-line"></i></div>
      </div>
      <div class="program-body">
        <h3>كلية إدارة الأعمال</h3>
        <p>تخصصات في المحاسبة، التسويق، التمويل، وإدارة الموارد البشرية.</p>
        <div class="program-meta">
          <span><i class="fas fa-clock"></i> 4 سنوات</span>
          <span><i class="fas fa-user-graduate"></i> بكالوريوس</span>
        </div>
      </div>
    </div>

    <div class="program-card">
      <div class="program-image">
        <img src="https://images.unsplash.com/photo-1503676260728-1c00da094a0b?w=600" alt="آداب">
        <div class="program-icon"><i class="fas fa-book"></i></div>
      </div>
      <div class="program-body">
        <h3>كلية الآداب والعلوم الإنسانية</h3>
        <p>برامج في اللغات، التاريخ، الجغرافيا، وعلم النفس والاجتماع.</p>
        <div class="program-meta">
          <span><i class="fas fa-clock"></i> 4 سنوات</span>
          <span><i class="fas fa-user-graduate"></i> بكالوريوس</span>
        </div>
      </div>
    </div>

    <div class="program-card">
      <div class="program-image">
        <img src="https://images.unsplash.com/photo-1581091226825-a6a2a5aee158?w=600" alt="علوم">
        <div class="program-icon"><i class="fas fa-flask"></i></div>
      </div>
      <div class="program-body">
        <h3>كلية العلوم</h3>
        <p>تخصصات في الفيزياء، الكيم
