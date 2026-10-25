<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Робот-пылесос CleanBot X1 — Магазин БытТех</title>
    <style>
        /* ===== Базовые сбросы и шрифты ===== */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Roboto, system-ui, sans-serif;
            background: #f5f7fa;
            color: #1e2b3c;
            line-height: 1.5;
            padding: 24px;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: #ffffff;
            border-radius: 32px;
            box-shadow: 0 20px 40px -12px rgba(0, 20, 30, 0.15);
            padding: 32px;
        }

        /* ===== Шапка / хлебные крошки ===== */
        .breadcrumbs {
            font-size: 0.9rem;
            color: #5e6f88;
            margin-bottom: 24px;
            display: flex;
            gap: 8px;
            align-items: center;
        }

        .breadcrumbs a {
            color: #2a6df4;
            text-decoration: none;
        }

        .breadcrumbs a:hover {
            text-decoration: underline;
        }

        /* ===== Основная сетка товара ===== */
        .product-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 48px;
            margin-bottom: 40px;
        }

        /* ===== Галерея ===== */
        .gallery {
            display: flex;
            flex-direction: column;
            gap: 16px;
        }

        .main-image {
            background: #eef1f6;
            border-radius: 24px;
            padding: 24px;
            display: flex;
            justify-content: center;
            align-items: center;
            aspect-ratio: 1 / 1;
            overflow: hidden;
        }

        .main-image img {
            width: 100%;
            height: 100%;
            object-fit: contain;
            transition: transform 0.2s ease;
        }

        .main-image img:hover {
            transform: scale(1.02);
        }

        .thumbnails {
            display: flex;
            gap: 12px;
        }

        .thumb {
            width: 80px;
            height: 80px;
            background: #eef1f6;
            border-radius: 16px;
            padding: 8px;
            cursor: pointer;
            border: 2px solid transparent;
            transition: border-color 0.2s;
        }

        .thumb:hover,
        .thumb.active {
            border-color: #2a6df4;
        }

        .thumb img {
            width: 100%;
            height: 100%;
            object-fit: contain;
        }

        /* ===== Информация о товаре ===== */
        .product-info {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .badge {
            display: inline-block;
            background: #ffd966;
            color: #1e2b3c;
            font-weight: 600;
            font-size: 0.8rem;
            padding: 4px 12px;
            border-radius: 20px;
            width: fit-content;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        h1 {
            font-size: 2.2rem;
            font-weight: 700;
            line-height: 1.2;
            letter-spacing: -0.02em;
        }

        .rating {
            display: flex;
            align-items: center;
            gap: 8px;
            color: #ffb347;
            font-size: 1.1rem;
        }

        .rating span {
            color: #5e6f88;
            font-size: 0.9rem;
            margin-left: 4px;
        }

        .price-block {
            display: flex;
            align-items: baseline;
            gap: 16px;
            margin: 8px 0;
        }

        .current-price {
            font-size: 2.4rem;
            font-weight: 800;
            color: #1e2b3c;
        }

        .old-price {
            font-size: 1.3rem;
            color: #9aa8bb;
            text-decoration: line-through;
        }

        .discount {
            background: #e6f0ff;
            color: #2a6df4;
            font-weight: 700;
            padding: 4px 10px;
            border-radius: 12px;
            font-size: 0.9rem;
        }

        /* ===== Опции (цвет) ===== */
        .option-group {
            display: flex;
            flex-direction: column;
            gap: 8px;
        }

        .option-label {
            font-weight: 600;
            font-size: 0.95rem;
            color: #3a4b62;
        }

        .color-options {
            display: flex;
            gap: 12px;
        }

        .color-btn {
            width: 44px;
            height: 44px;
            border-radius: 50%;
            border: 2px solid #d0d8e5;
            cursor: pointer;
            transition: all 0.15s;
            padding: 3px;
        }

        .color-btn:hover,
        .color-btn.selected {
            border-color: #2a6df4;
            transform: scale(1.05);
        }

        .color-btn[data-color="white"] { background: #f0f2f5; }
        .color-btn[data-color="black"] { background: #2d2f33; }
        .color-btn[data-color="blue"]  { background: #b3c7e6; }

        /* ===== Кнопка «Купить» ===== */
        .buy-btn {
            background: #2a6df4;
            color: white;
            border: none;
            font-size: 1.2rem;
            font-weight: 700;
            padding: 18px 32px;
            border-radius: 40px;
            cursor: pointer;
            transition: background 0.2s, transform 0.1s;
            margin-top: 12px;
            letter-spacing: 0.3px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        .buy-btn:hover {
            background: #1a4fd0;
        }

        .buy-btn:active {
            transform: scale(0.98);
        }

        /* ===== Характеристики ===== */
        .specs {
            margin-top: 40px;
            border-top: 1px solid #e2e8f2;
            padding-top: 32px;
        }

        .specs h2 {
            font-size: 1.5rem;
            margin-bottom: 20px;
        }

        .specs-list {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 16px;
            list-style: none;
        }

        .specs-list li {
            background: #f8faff;
            padding: 12px 18px;
            border-radius: 16px;
            font-size: 0.95rem;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .specs-list li::before {
            content: "✓";
            color: #2a6df4;
            font-weight: 700;
        }

        /* ===== Подвал / доставка ===== */
        .footer-info {
            margin-top: 40px;
            display: flex;
            gap: 24px;
            flex-wrap: wrap;
            background: #f8faff;
            border-radius: 24px;
            padding: 24px 32px;
            font-size: 0.95rem;
            color: #3a4b62;
        }

        .footer-info div {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        /* ===== Адаптив ===== */
        @media (max-width: 800px) {
            .product-grid {
                grid-template-columns: 1fr;
                gap: 24px;
            }

            .container {
                padding: 20px;
            }

            h1 {
                font-size: 1.8rem;
            }

            .current-price {
                font-size: 2rem;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Навигация / хлебные крошки -->
        <nav class="breadcrumbs" aria-label="Навигация">
            <a href="#">Главная</a>
            <span>/</span>
            <a href="#">Бытовая техника</a>
            <span>/</span>
            <a href="#">Роботы-пылесосы</a>
            <span>/</span>
            <span aria-current="page">CleanBot X1</span>
        </nav>

        <!-- Основная сетка -->
        <div class="product-grid">
            <!-- Галерея -->
            <section class="gallery" aria-label="Галерея изображений">
                <div class="main-image">
                    <img id="mainImg" src="https://placehold.co/600x600/eef1f6/1e2b3c?text=CleanBot+X1" alt="Робот-пылесос CleanBot X1, белый">
                </div>
                <div class="thumbnails" role="group" aria-label="Миниатюры">
                    <div class="thumb active" onclick="changeImage(this, 'https://placehold.co/600x600/eef1f6/1e2b3c?text=CleanBot+X1')">
                        <img src="https://placehold.co/80x80/eef1f6/1e2b3c?text=1" alt="Вид спереди">
                    </div>
                    <div class="thumb" onclick="changeImage(this, 'https://placehold.co/600x600/d9e2f0/1e2b3c?text=CleanBot+Side')">
                        <img src="https://placehold.co/80x80/d9e2f0/1e2b3c?text=2" alt="Вид сбоку">
                    </div>
                    <div class="thumb" onclick="changeImage(this, 'https://placehold.co/600x600/c2d4ec/1e2b3c?text=CleanBot+Top')">
                        <img src="https://placehold.co/80x80/c2d4ec/1e2b3c?text=3" alt="Вид сверху">
                    </div>
                </div>
            </section>

            <!-- Информация о товаре -->
            <section class="product-info" aria-label="Информация о товаре">
                <div class="badge">Хит продаж</div>
                <h1>Робот-пылесос CleanBot X1 с влажной уборкой</h1>

                <div class="rating" aria-label="Рейтинг 4.8 из 5">
                    ★★★★★ <span>4.8 · 127 отзывов</span>
                </div>

                <div class="price-block">
                    <span class="current-price">24 990 ₽</span>
                    <span class="old-price">32 990 ₽</span>
                    <span class="discount">−24%</span>
                </div>

                <!-- Выбор цвета -->
                <div class="option-group">
                    <span class="option-label">Цвет:</span>
                    <div class="color-options" role="radiogroup" aria-label="Выбор цвета">
                        <button class="color-btn selected" data-color="white" aria-label="Белый" role="radio" aria-checked="true"></button>
                        <button class="color-btn" data-color="black" aria-label="Чёрный" role="radio" aria-checked="false"></button>
                        <button class="color-btn" data-color="blue" aria-label="Голубой" role="radio" aria-checked="false"></button>
                    </div>
                </div>

                <!-- Кнопка покупки -->
                <button class="buy-btn" onclick="alert('Товар добавлен в корзину!')">
                    🛒 Добавить в корзину
                </button>

                <!-- Блок преимуществ -->
                <div class="footer-info" style="margin-top: 20px; padding: 16px 20px;">
                    <div>🚚 Доставка завтра</div>
                    <div>🛡️ Гарантия 2 года</div>
                    <div>↩️ Возврат 30 дней</div>
                </div>
            </section>
        </div>

        <!-- Характеристики -->
        <section class="specs">
            <h2>Ключевые характеристики</h2>
            <ul class="specs-list">
                <li>Мощность всасывания: 2700 Па</li>
                <li>Время работы: до 180 минут</li>
                <li>Влажная уборка: есть</li>
                <li>Построение карты: LiDAR</li>
                <li>Объём пылесборника: 0.4 л</li>
                <li>Управление: приложение и голос</li>
                <li>Зарядная станция: самоочистка</li>
                <li>Уровень шума: 58 дБ</li>
            </ul>
        </section>

        <!-- Мета-информация -->
        <footer style="margin-top: 32px; font-size: 0.85rem; color: #7b8aa0; border-top: 1px solid #e2e8f2; padding-top: 20px;">
            <p>Артикул: CB-X1-2026 · Производитель: CleanTech · Страна: Китай</p>
        </footer>
    </div>

    <script>
        // Интерактив: смена главного изображения по клику на миниатюру
        function changeImage(thumbElement, newSrc) {
            // Убираем active у всех миниатюр
            document.querySelectorAll('.thumb').forEach(t => t.classList.remove('active'));
            // Добавляем active текущей
            thumbElement.classList.add('active');
            // Меняем главное изображение
            const mainImg = document.getElementById('mainImg');
            if (mainImg) {
                mainImg.src = newSrc;
            }
        }

        // Интерактив: выбор цвета
        document.querySelectorAll('.color-btn').forEach(btn => {
            btn.addEventListener('click', function() {
                // Снимаем selected со всех
                document.querySelectorAll('.color-btn').forEach(b => {
                    b.classList.remove('selected');
                    b.setAttribute('aria-checked', 'false');
                });
                // Устанавливаем на текущую
                this.classList.add('selected');
                this.setAttribute('aria-checked', 'true');
            });
        });
    </script>
</body>
</html>
