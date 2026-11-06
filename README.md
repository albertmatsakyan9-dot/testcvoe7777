<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Своё — безопасный маркетплейс рядом с домом</title>
<style>
  :root {
    --brand: #2563eb;
    --brand-dark: #1e40af;
    --accent: #10b981;
    --bg: #f8fafc;
    --card: #ffffff;
    --text: #0f172a;
    --muted: #64748b;
    --border: #e2e8f0;
    --danger: #ef4444;
    --radius: 14px;
    --shadow: 0 4px 20px rgba(15, 23, 42, 0.06);
  }
  * { box-sizing: border-box; margin: 0; padding: 0; }
  body {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
    background: var(--bg);
    color: var(--text);
    line-height: 1.5;
  }
  a { color: inherit; text-decoration: none; }
  button { font-family: inherit; cursor: pointer; border: none; }

  /* ===== HEADER ===== */
  header {
    background: var(--card);
    border-bottom: 1px solid var(--border);
    position: sticky;
    top: 0;
    z-index: 100;
  }
  .header-inner {
    max-width: 1200px;
    margin: 0 auto;
    padding: 12px 20px;
    display: flex;
    align-items: center;
    gap: 20px;
  }
  .logo {
    font-size: 22px;
    font-weight: 800;
    color: var(--brand);
    letter-spacing: -0.5px;
    display: flex;
    align-items: center;
    gap: 6px;
  }
  .logo span { color: var(--text); }
  .logo-dot {
    width: 10px; height: 10px;
    background: var(--accent);
    border-radius: 50%;
    display: inline-block;
  }
  .search-bar {
    flex: 1;
    display: flex;
    background: var(--bg);
    border: 1px solid var(--border);
    border-radius: 10px;
    overflow: hidden;
  }
  .search-bar input {
    flex: 1;
    padding: 10px 14px;
    border: none;
    background: transparent;
    font-size: 14px;
    outline: none;
  }
  .search-bar button {
    padding: 0 20px;
    background: var(--brand);
    color: #fff;
    font-weight: 600;
    font-size: 14px;
  }
  .search-bar button:hover { background: var(--brand-dark); }
  .header-actions { display: flex; gap: 10px; align-items: center; }
  .btn-ghost {
    padding: 9px 16px;
    background: transparent;
    border: 1px solid var(--border);
    border-radius: 10px;
    font-size: 14px;
    font-weight: 500;
    color: var(--text);
  }
  .btn-ghost:hover { background: var(--bg); }
  .btn-primary {
    padding: 9px 18px;
    background: var(--brand);
    color: #fff;
    border-radius: 10px;
    font-weight: 600;
    font-size: 14px;
  }
  .btn-primary:hover { background: var(--brand-dark); }

  /* ===== HERO ===== */
  .hero {
    max-width: 1200px;
    margin: 0 auto;
    padding: 40px 20px 20px;
  }
  .hero h1 {
    font-size: 32px;
    font-weight: 800;
    letter-spacing: -0.8px;
    margin-bottom: 8px;
  }
  .hero p { color: var(--muted); font-size: 16px; }
  .hero-badges { display: flex; gap: 10px; margin-top: 16px; flex-wrap: wrap; }
  .badge {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    padding: 6px 12px;
    background: #ecfdf5;
    color: #047857;
    border-radius: 999px;
    font-size: 13px;
    font-weight: 600;
  }

  /* ===== CATEGORIES ===== */
  .categories {
    max-width: 1200px;
    margin: 0 auto;
    padding: 10px 20px;
    display: flex;
    gap: 10px;
    overflow-x: auto;
    scrollbar-width: none;
  }
  .categories::-webkit-scrollbar { display: none; }
  .cat-chip {
    padding: 9px 16px;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 999px;
    font-size: 14px;
    white-space: nowrap;
    font-weight: 500;
    transition: 0.15s;
  }
  .cat-chip:hover, .cat-chip.active {
    background: var(--brand);
    color: #fff;
    border-color: var(--brand);
  }

  /* ===== LAYOUT ===== */
  .container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 20px;
    display: grid;
    grid-template-columns: 1fr 320px;
    gap: 24px;
  }
  .section-title {
    font-size: 20px;
    font-weight: 700;
    margin-bottom: 16px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .section-title a { font-size: 14px; color: var(--brand); font-weight: 600; }

  /* ===== LISTINGS GRID ===== */
  .grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
    gap: 16px;
  }
  .card {
    background: var(--card);
    border-radius: var(--radius);
    overflow: hidden;
    box-shadow: var(--shadow);
    transition: transform 0.15s, box-shadow 0.15s;
    cursor: pointer;
    border: 1px solid var(--border);
  }
  .card:hover {
    transform: translateY(-3px);
    box-shadow: 0 10px 30px rgba(15, 23, 42, 0.12);
  }
  .card-img {
    height: 150px;
    background: linear-gradient(135deg, #e0e7ff, #c7d2fe);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 42px;
    position: relative;
  }
  .escrow-tag {
    position: absolute;
    top: 8px; left: 8px;
    background: rgba(16, 185, 129, 0.95);
    color: #fff;
    font-size: 11px;
    font-weight: 700;
    padding: 4px 8px;
    border-radius: 6px;
    display: flex;
    align-items: center;
    gap: 4px;
  }
  .card-body { padding: 12px; }
  .card-price { font-size: 18px; font-weight: 800; margin-bottom: 4px; }
  .card-title {
    font-size: 14px;
    color: var(--text);
    margin-bottom: 8px;
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
    overflow: hidden;
    min-height: 40px;
  }
  .card-meta {
    display: flex;
    align-items: center;
    justify-content: space-between;
    font-size: 12px;
    color: var(--muted);
  }
  .seller {
    display: flex;
    align-items: center;
    gap: 4px;
  }
  .verified { color: var(--brand); font-weight: 700; }

  /* ===== SIDEBAR ===== */
  aside { display: flex; flex-direction: column; gap: 16px; }
  .panel {
    background: var(--card);
    border-radius: var(--radius);
    padding: 18px;
    box-shadow: var(--shadow);
    border: 1px solid var(--border);
  }
  .panel h3 {
    font-size: 15px;
    font-weight: 700;
    margin-bottom: 12px;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .panel p { font-size: 13px; color: var(--muted); margin-bottom: 12px; }
  .escrow-steps { list-style: none; font-size: 13px; }
  .escrow-steps li {
    display: flex;
    gap: 10px;
    padding: 8px 0;
    border-bottom: 1px dashed var(--border);
  }
  .escrow-steps li:last-child { border-bottom: none; }
  .step-num {
    width: 22px; height: 22px;
    background: var(--brand);
    color: #fff;
    border-radius: 50%;
    font-size: 12px;
    font-weight: 700;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
  }
  .full-btn { width: 100%; text-align: center; padding: 11px; }

  /* ===== MODAL ===== */
  .overlay {
    position: fixed;
    inset: 0;
    background: rgba(15, 23, 42, 0.5);
    display: none;
    align-items: center;
    justify-content: center;
    z-index: 200;
    padding: 20px;
  }
  .overlay.open { display: flex; }
  .modal {
    background: var(--card);
    border-radius: 18px;
    max-width: 460px;
    width: 100%;
    padding: 24px;
    box-shadow: 0 20px 60px rgba(0,0,0,0.3);
    animation: pop 0.2s ease;
  }
  @keyframes pop {
    from { transform: scale(0.95); opacity: 0; }
    to { transform: scale(1); opacity: 1; }
  }
  .modal h2 { font-size: 20px; margin-bottom: 6px; }
  .modal .price { font-size: 24px; font-weight: 800; margin: 12px 0; }
  .escrow-box {
    background: #f0fdf4;
    border: 1px solid #bbf7d0;
    border-radius: 10px;
    padding: 12px;
    font-size: 13px;
    color: #166534;
    margin-bottom: 16px;
  }
  .modal-actions { display: flex; gap: 10px; }
  .modal-actions button { flex: 1; padding: 11px; border-radius: 10px; font-weight: 600; }
  .btn-cancel { background: var(--bg); color: var(--text); border: 1px solid var(--border); }
  .btn-buy { background: var(--accent); color: #fff; }
  .btn-buy:hover { background: #059669; }

  /* ===== TOAST ===== */
  .toast {
    position: fixed;
    bottom: 24px;
    left: 50%;
    transform: translateX(-50%) translateY(100px);
    background: var(--text);
    color: #fff;
    padding: 12px 22px;
    border-radius: 10px;
    font-size: 14px;
    font-weight: 500;
    opacity: 0;
    transition: 0.3s;
    z-index: 300;
  }
  .toast.show { transform: translateX(-50%) translateY(0); opacity: 1; }

  /* ===== FOOTER ===== */
  footer {
    max-width: 1200px;
    margin: 40px auto 0;
    padding: 24px 20px;
    border-top: 1px solid var(--border);
    color: var(--muted);
    font-size: 13px;
    text-align: center;
  }

  /* ===== RESPONSIVE ===== */
  @media (max-width: 900px) {
    .container { grid-template-columns: 1fr; }
    aside { order: -1; }
    .header-actions .btn-ghost { display: none; }
  }
  @media (max-width: 600px) {
    .hero h1 { font-size: 24px; }
    .search-bar button { padding: 0 14px; }
    .grid { grid-template-columns: repeat(2, 1fr); gap: 10px; }
    .card-img { height: 120px; font-size: 32px; }
    .header-actions .btn-primary { padding: 8px 12px; font-size: 13px; }
  }
</style>
</head>
<body>

<!-- HEADER -->
<header>
  <div class="header-inner">
    <div class="logo">своё<span class="logo-dot"></span></div>
    <div class="search-bar">
      <input type="text" id="searchInput" placeholder="Что ищете? Например, iPhone 13">
      <button onclick="doSearch()">Найти</button>
    </div>
    <div class="header-actions">
      <button class="btn-ghost" onclick="showToast('Вход через Госуслуги — демо')">Войти</button>
      <button class="btn-primary" onclick="showToast('Размещение объявления — демо')">+ Разместить</button>
    </div>
  </div>
</header>

<!-- HERO -->
<section class="hero">
  <h1>Безопасные сделки рядом с домом</h1>
  <p>Деньги замораживаются до получения товара. Продавцы проверены.</p>
  <div class="hero-badges">
    <span class="badge">🛡️ Эскроу-защита</span>
    <span class="badge">✅ Верификация продавцов</span>
    <span class="badge">📍 Только ваш район</span>
  </div>
</section>

<!-- CATEGORIES -->
<nav class="categories" id="categories">
  <button class="cat-chip active" onclick="filterCat(this, 'all')">Все</button>
  <button class="cat-chip" onclick="filterCat(this, 'Электроника')">Электроника</button>
  <button class="cat-chip" onclick="filterCat(this, 'Мебель')">Мебель</button>
  <button class="cat-chip" onclick="filterCat(this, 'Детское')">Детское</button>
  <button class="cat-chip" onclick="filterCat(this, 'Авто')">Авто</button>
  <button class="cat-chip" onclick="filterCat(this, 'Одежда')">Одежда</button>
  <button class="cat-chip" onclick="filterCat(this, 'Услуги')">Услуги</button>
</nav>

<!-- MAIN -->
<div class="container">
  <main>
    <div class="section-title">
      <span>Объявления рядом</span>
      <a href="#" onclick="showToast('Сортировка — демо'); return false;">Сначала дешёвые</a>
    </div>
    <div class="grid" id="grid"></div>
  </main>

  <aside>
    <div class="panel">
      <h3>🛡️ Как работает защита</h3>
      <ul class="escrow-steps">
        <li><span class="step-num">1</span> Покупатель платит — деньги замораживаются</li>
        <li><span class="step-num">2</span> Продавец отправляет товар</li>
        <li><span class="step-num">3</span> Покупатель подтверждает получение</li>
        <li><span class="step-num">4</span> Продавец получает деньги</li>
      </ul>
    </div>

    <div class="panel">
      <h3>📍 Ваш район</h3>
      <p>Показываем объявления в радиусе 5 км. Меньше доставки — больше экономии.</p>
      <button class="btn-primary full-btn" onclick="showToast('Геолокация — демо')">Определить район</button>
    </div>

    <div class="panel">
      <h3>💚 Гарантия первой сделки</h3>
      <p>Застрахуем вашу первую покупку до 30 000 ₽ за счёт платформы.</p>
      <button class="btn-ghost full-btn" onclick="showToast('Активация гарантии — демо')">Активировать</button>
    </div>
  </aside>
</div>

<footer>
  © 2026 «Своё» — демо-прототип. Безопасный маркетплейс для локальной торговли.
</footer>

<!-- MODAL -->
<div class="overlay" id="overlay" onclick="if(event.target===this) closeModal()">
  <div class="modal">
    <h2 id="mTitle">Товар</h2>
    <p style="font-size:13px;color:var(--muted)" id="mSeller">Продавец</p>
    <div class="price" id="mPrice">0 ₽</div>
    <div class="escrow-box">
      🛡️ <strong>Защита «Своё»:</strong> деньги замораживаются на счёте платформы и переходят продавцу только после подтверждения получения товара.
    </div>
    <div class="modal-actions">
      <button class="btn-cancel" onclick="closeModal()">Отмена</button>
      <button class="btn-buy" onclick="buyNow()">Купить с защитой</button>
    </div>
  </div>
</div>

<!-- TOAST -->
<div class="toast" id="toast"></div>

<script>
  // ===== ДАННЫЕ =====
  const listings = [
    { id: 1, title: "iPhone 13 128GB, идеальное состояние", price: 42000, cat: "Электроника", icon: "📱", seller: "Алексей К.", verified: true, escrow: true, dist: "0.8 км" },
    { id: 2, title: "Диван-кровать IKEA, б/у 1 год", price: 12000, cat: "Мебель", icon: "🛋️", seller: "Мария П.", verified: true, escrow: true, dist: "1.2 км" },
    { id: 3, title: "Детская коляска Yoyo, комплект", price: 18500, cat: "Детское", icon: "🍼", seller: "Ольга С.", verified: true, escrow: true, dist: "0.5 км" },
    { id: 4, title: "Велосипед горный Trek, 19 рама", price: 27000, cat: "Авто", icon: "🚲", seller: "Дмитрий В.", verified: false, escrow: false, dist: "2.1 км" },
    { id: 5, title: "Куртка зимняя The North Face, L", price: 8900, cat: "Одежда", icon: "🧥", seller: "Иван Р.", verified: true, escrow: true, dist: "0.9 км" },
    { id: 6, title: "Ноутбук MacBook Air M1, 256GB", price: 55000, cat: "Электроника", icon: "💻", seller: "Сергей Л.", verified: true, escrow: true, dist: "1.5 км" },
    { id: 7, title: "Ремонт квартир под ключ", price: 0, cat: "Услуги", icon: "🔧", seller: "ИП СтройПро", verified: true, escrow: false, dist: "3.0 км", priceText: "от 5 000 ₽/м²" },
    { id: 8, title: "Стол письменный дубовый", price: 7500, cat: "Мебель", icon: "🪑", seller: "Анна Т.", verified: true, escrow: true, dist: "1.1 км" },
  ];

  let currentCat = 'all';
  let currentItem = null;

  const grid = document.getElementById('grid');

  function fmt(n) {
    return n.toLocaleString('ru-RU') + ' ₽';
  }

  function render() {
    const list = currentCat === 'all'
      ? listings
      : listings.filter(l => l.cat === currentCat);

    grid.innerHTML = list.map(l => `
      <div class="card" onclick="openModal(${l.id})">
        <div class="card-img" style="background:linear-gradient(135deg,#e0e7ff,#c7d2fe)">
          ${l.icon}
          ${l.escrow ? '<span class="escrow-tag">🛡️ Эскроу</span>' : ''}
        </div>
        <div class="card-body">
          <div class="card-price">${l.priceText || fmt(l.price)}</div>
          <div class="card-title">${l.title}</div>
          <div class="card-meta">
            <span class="seller">
              ${l.verified ? '<span class="verified">✔</span>' : ''}
              ${l.seller}
            </span>
            <span>${l.dist}</span>
          </div>
        </div>
      </div>
    `).join('');
  }

  function filterCat(btn, cat) {
    document.querySelectorAll('.cat-chip').forEach(c => c.classList.remove('active'));
    btn.classList.add('active');
    currentCat = cat;
    render();
  }

  // ===== MODAL =====
  function openModal(id) {
    currentItem = listings.find(l => l.id === id);
    document.getElementById('mTitle').textContent = currentItem.title;
    document.getElementById('mSeller').textContent = 'Продавец: ' + currentItem.seller + (currentItem.verified ? ' ✔ проверен' : '');
    document.getElementById('mPrice').textContent = currentItem.priceText || fmt(currentItem.price);
    document.getElementById('overlay').classList.add('open');
  }

  function closeModal() {
    document.getElementById('overlay').classList.remove('open');
    currentItem = null;
  }

  function buyNow() {
    if (!currentItem) return;
    closeModal();
    showToast('✅ Сделка создана! Деньги заморожены до получения товара');
  }

  // ===== SEARCH =====
  function doSearch() {
    const q = document.getElementById('searchInput').value.trim().toLowerCase();
    if (!q) { render(); return; }
    const found = listings.filter(l => l.title.toLowerCase().includes(q));
    grid.innerHTML = found.length ? found.map(l => `
      <div class="card" onclick="openModal(${l.id})">
        <div class="card-img">${l.icon}</div>
        <div class="card-body">
          <div class="card-price">${l.priceText || fmt(l.price)}</div>
          <div class="card-title">${l.title}</div>
          <div class="card-meta"><span>${l.seller}</span><span>${l.dist}</span></div>
        </div>
      </div>
    `).join('') : '<p style="color:var(--muted);padding:20px">Ничего не найдено 😕</p>';
  }

  // ===== TOAST =====
  let toastTimer;
  function showToast(msg) {
    const t = document.getElementById('toast');
    t.textContent = msg;
    t.classList.add('show');
    clearTimeout(toastTimer);
    toastTimer = setTimeout(() => t.classList.remove('show'), 3000);
  }

  // ===== INIT =====
  render();
</script>
</body>
</html>
