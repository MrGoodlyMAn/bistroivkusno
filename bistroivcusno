<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes">
    <title>🍲 Бюджетные рецепты · до 1000 ₽</title>
    <!-- Стили: аккуратно, минималистично, с акцентом на цену -->
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: system-ui, 'Segoe UI', 'Helvetica Neue', 'Inter', sans-serif;
        }

        body {
            background: #f9f7f3;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 24px 16px;
        }

        .card {
            max-width: 780px;
            width: 100%;
            background: #ffffff;
            border-radius: 36px;
            box-shadow: 0 18px 35px -8px rgba(0, 0, 0, 0.08), 0 8px 16px -6px rgba(0, 0, 0, 0.02);
            padding: 32px 28px;
            transition: all 0.2s ease;
            border: 1px solid #f1ede8;
        }

        h1 {
            font-size: 2.2rem;
            font-weight: 650;
            letter-spacing: -0.02em;
            color: #1e1e1e;
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 6px;
        }

        .subhead {
            display: flex;
            justify-content: space-between;
            align-items: baseline;
            flex-wrap: wrap;
            margin-bottom: 28px;
            border-bottom: 1.5px dashed #dad3cb;
            padding-bottom: 16px;
        }

        .budget-badge {
            background: #e8f3e2;
            color: #1f5e3b;
            padding: 8px 18px;
            border-radius: 80px;
            font-weight: 600;
            font-size: 1.05rem;
            box-shadow: inset 0 0 0 1px #c3dbc0;
        }

        .generator-area {
            display: flex;
            flex-direction: column;
            align-items: center;
            margin: 16px 0 28px;
        }

        .btn-generate {
            background: #1e1e1e;
            color: white;
            border: none;
            padding: 18px 40px;
            border-radius: 100px;
            font-size: 1.5rem;
            font-weight: 580;
            letter-spacing: -0.01em;
            cursor: pointer;
            box-shadow: 0 6px 0 #0b0b0b;
            transition: all 0.12s;
            width: fit-content;
            min-width: 280px;
            border: 1px solid #333;
            margin-bottom: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 12px;
        }

        .btn-generate:hover {
            background: #2b2b2b;
            transform: translateY(-2px);
            box-shadow: 0 8px 0 #0b0b0b;
        }

        .btn-generate:active {
            transform: translateY(3px);
            box-shadow: 0 3px 0 #0b0b0b;
        }

        .hint {
            color: #6b5e54;
            font-weight: 430;
            font-size: 0.98rem;
        }

        /* карточка рецепта */
        .recipe-panel {
            background: #fefcf9;
            border-radius: 28px;
            padding: 24px 26px;
            margin-top: 20px;
            border: 1px solid #ede6de;
            box-shadow: inset 0 1px 3px rgba(255,255,255,0.9), 0 8px 18px -8px rgba(46, 34, 18, 0.06);
        }

        .recipe-header {
            display: flex;
            flex-wrap: wrap;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 18px;
        }

        .recipe-title {
            font-size: 1.9rem;
            font-weight: 700;
            color: #1a1e1b;
            letter-spacing: -0.02em;
            line-height: 1.2;
        }

        .price-tag {
            background: #1e3d2f;
            color: #f5f0e0;
            padding: 10px 22px;
            border-radius: 60px;
            font-weight: 700;
            font-size: 1.8rem;
            line-height: 1;
            box-shadow: 0 4px 0 #0f241b;
            border: 1px solid #346b51;
            white-space: nowrap;
        }

        .price-tag small {
            font-size: 1rem;
            font-weight: 500;
            opacity: 0.9;
        }

        .meta-row {
            display: flex;
            flex-wrap: wrap;
            gap: 24px 40px;
            margin: 18px 0 22px;
            color: #3b3a36;
            font-weight: 470;
            border-top: 1px solid #e7dfd6;
            padding-top: 18px;
        }

        .meta-item {
            display: flex;
            align-items: baseline;
            gap: 8px;
        }

        .meta-label {
            font-weight: 600;
            color: #5f554a;
            text-transform: uppercase;
            font-size: 0.8rem;
            letter-spacing: 0.5px;
        }

        .ingredients-box, .steps-box {
            margin: 24px 0 18px;
        }

        .section-title {
            font-weight: 680;
            font-size: 1.25rem;
            margin-bottom: 14px;
            color: #1e1e1e;
            border-left: 6px solid #c7b7a2;
            padding-left: 16px;
        }

        .ingredient-list {
            list-style: none;
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
            gap: 10px 14px;
        }

        .ingredient-list li {
            display: flex;
            align-items: center;
            gap: 8px;
            background: #ffffffd4;
            padding: 8px 14px;
            border-radius: 60px;
            border: 1px solid #e0d6cc;
            font-size: 1rem;
        }

        .ingredient-emoji {
            font-size: 1.3rem;
        }

        .steps-list {
            padding-left: 6px;
            list-style: none;
            counter-reset: step-counter;
        }

        .steps-list li {
            counter-increment: step-counter;
            margin-bottom: 14px;
            display: flex;
            gap: 16px;
            align-items: flex-start;
        }

        .steps-list li::before {
            content: counter(step-counter);
            background: #c7b7a2;
            color: #1e1e1e;
            font-weight: 700;
            width: 28px;
            height: 28px;
            border-radius: 30px;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            flex-shrink: 0;
            margin-top: -2px;
            border: 1px solid #b1a18e;
        }

        .total-cost-note {
            background: #f3efe9;
            border-radius: 24px;
            padding: 14px 22px;
            margin-top: 26px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 12px;
            font-size: 1.05rem;
            border: 1px solid #ddd2c4;
        }

        .cost-ok {
            background: #1f5e3b20;
            padding: 5px 16px;
            border-radius: 40px;
            color: #1f5e3b;
            font-weight: 650;
        }

        .footer-note {
            margin-top: 22px;
            text-align: center;
            color: #6b6258;
            font-size: 0.9rem;
        }

        .empty-message {
            text-align: center;
            color: #7e766b;
            padding: 16px;
            font-style: italic;
        }

        /* адаптив */
        @media (max-width: 550px) {
            .card {
                padding: 24px 18px;
            }
            h1 {
                font-size: 1.9rem;
            }
            .btn-generate {
                font-size: 1.3rem;
                padding: 16px 24px;
                min-width: 220px;
            }
            .recipe-title {
                font-size: 1.6rem;
            }
            .price-tag {
                font-size: 1.5rem;
                padding: 8px 18px;
            }
        }
    </style>
</head>
<body>

<div class="card">
    <h1>
        <span>🍳 Генератор рецептов</span>
        <span style="font-size: 1.8rem;">👩‍🍳</span>
    </h1>
    <div class="subhead">
        <span style="font-weight: 450;">Сытные блюда · всегда доступно</span>
        <span class="budget-badge">💰 лимит: 1000 ₽</span>
    </div>

    <div class="generator-area">
        <button class="btn-generate" id="generateBtn">
            <span>✨</span> Сгенерировать рецепт <span>🍲</span>
        </button>
        <div class="hint">Каждое блюдо стоит ≤ 1000 рублей · цены приближены к реальным</div>
    </div>

    <!-- Сюда рендерится рецепт -->
    <div id="recipeContainer" class="recipe-panel">
        <!-- динамический контент -->
    </div>
    <div class="footer-note">
        ⏱️ Быстро · просто · бюджетно
    </div>
</div>

<script>
    (function() {
        "use strict";

        // ---------- БАЗА БЮДЖЕТНЫХ РЕЦЕПТОВ (до 1000 руб) ----------
        // Каждый рецепт содержит: название, время, порции, список ингредиентов (с примерной стоимостью),
        // шаги, и итоговую сумму (проверено, ≤ 1000)
        const recipes = [
            {
                name: "🥔 Картофельная запеканка с фаршем",
                time: "60 мин",
                servings: "4 порции",
                ingredients: [
                    { emoji: "🥔", name: "Картофель (1 кг)", cost: 45 },
                    { emoji: "🥩", name: "Фарш свино-говяжий (400 г)", cost: 220 },
                    { emoji: "🧅", name: "Лук репчатый (2 шт)", cost: 15 },
                    { emoji: "🥛", name: "Молоко (150 мл)", cost: 22 },
                    { emoji: "🧀", name: "Сыр (100 г)", cost: 85 },
                    { emoji: "🥚", name: "Яйцо (1 шт)", cost: 12 },
                    { emoji: "🧂", name: "Соль, перец, масло", cost: 8 }
                ],
                steps: [
                    "Картофель очистить, отварить до готовности, размять в пюре с молоком и яйцом.",
                    "Лук мелко нарезать, обжарить с фаршем 7–10 минут, посолить, поперчить.",
                    "В форму выложить половину пюре, затем фарш, сверху остальное пюре.",
                    "Посыпать тёртым сыром, запекать 25 минут при 190°C до румяной корочки."
                ],
                // вычисляемая сумма (ручной контроль)
                totalCost: 407 
            },
            {
                name: "🍝 Спагетти с томатным соусом и фрикадельками",
                time: "45 мин",
                servings: "3–4 порции",
                ingredients: [
                    { emoji: "🍝", name: "Спагетти (400 г)", cost: 58 },
                    { emoji: "🍅", name: "Томаты в с/с (400 г)", cost: 95 },
                    { emoji: "🥩", name: "Фарш куриный (350 г)", cost: 180 },
                    { emoji: "🧅", name: "Лук (1 шт)", cost: 8 },
                    { emoji: "🧄", name: "Чеснок (2 зуб.)", cost: 5 },
                    { emoji: "🌿", name: "Базилик, масло", cost: 12 },
                    { emoji: "🧀", name: "Пармезан (по желанию, 30 г)", cost: 55 }
                ],
                steps: [
                    "Лук и чеснок измельчить, обжарить. Добавить фарш, слепить небольшие фрикадельки, обжарить.",
                    "Влить томаты, тушить 12–15 мин, добавить базилик.",
                    "Отварить спагетти до al dente, смешать с соусом.",
                    "При подаче посыпать тёртым сыром."
                ],
                totalCost: 413
            },
            {
                name: "🥞 Сырники из творога со сметаной",
                time: "25 мин",
                servings: "3 порции",
                ingredients: [
                    { emoji: "🥣", name: "Творог 5-9% (400 г)", cost: 135 },
                    { emoji: "🥚", name: "Яйцо (1 шт)", cost: 12 },
                    { emoji: "🌾", name: "Мука (4 ст.л.)", cost: 6 },
                    { emoji: "🍚", name: "Сахар (2 ст.л.)", cost: 3 },
                    { emoji: "🧂", name: "Соль, ванилин", cost: 2 },
                    { emoji: "🧈", name: "Масло для жарки", cost: 10 },
                    { emoji: "🥛", name: "Сметана (150 г)", cost: 45 }
                ],
                steps: [
                    "Творог размять с яйцом, сахаром, солью, ванилином и мукой.",
                    "Сформировать сырники, обвалять в муке.",
                    "Обжарить на среднем огне с двух сторон до золотистой корочки.",
                    "Подавать со сметаной."
                ],
                totalCost: 213
            },
            {
                name: "🍛 Плов с курицей (простой)",
                time: "70 мин",
                servings: "5–6 порций",
                ingredients: [
                    { emoji: "🍚", name: "Рис длиннозёрный (400 г)", cost: 52 },
                    { emoji: "🍗", name: "Куриные бёдра (600 г)", cost: 210 },
                    { emoji: "🥕", name: "Морковь (3 шт)", cost: 24 },
                    { emoji: "🧅", name: "Лук (2 шт)", cost: 14 },
                    { emoji: "🧄", name: "Чеснок (головка)", cost: 18 },
                    { emoji: "🌿", name: "Зира, барбарис, масло", cost: 20 },
                    { emoji: "🧂", name: "Соль, перец", cost: 3 }
                ],
                steps: [
                    "Мясо нарезать, обжарить в казане. Добавить лук, затем морковь соломкой.",
                    "Всыпать специи, влить кипяток (примерно 600 мл), тушить 20 мин (зирвак).",
                    "Засыпать промытый рис, воткнуть головку чеснока, долить воду на 1 см выше риса.",
                    "Готовить под крышкой на малом огне 25–30 мин, затем дать настояться."
                ],
                totalCost: 341
            },
            {
                name: "🥗 Салат «Сытный» с тунцом и фасолью",
                time: "15 мин",
                servings: "3 порции",
                ingredients: [
                    { emoji: "🐟", name: "Тунец консерв. (1 банка)", cost: 155 },
                    { emoji: "🥫", name: "Фасоль красная консерв.", cost: 75 },
                    { emoji: "🍅", name: "Помидоры (2 шт)", cost: 48 },
                    { emoji: "🥒", name: "Огурец (1 шт)", cost: 22 },
                    { emoji: "🧅", name: "Лук красный (1/2)", cost: 7 },
                    { emoji: "🌿", name: "Зелень, масло оливк.", cost: 22 },
                    { emoji: "🍋", name: "Лимонный сок", cost: 8 }
                ],
                steps: [
                    "Слить жидкость с тунца и фасоли. Фасоль промыть.",
                    "Овощи нарезать кубиками, лук тонкими полукольцами.",
                    "Всё смешать, заправить маслом и лимонным соком, посолить.",
                    "Украсить зеленью."
                ],
                totalCost: 337
            },
            {
                name: "🥣 Гороховый суп с копчёностями",
                time: "80 мин",
                servings: "6 порций",
                ingredients: [
                    { emoji: "🫘", name: "Горох колотый (300 г)", cost: 38 },
                    { emoji: "🥓", name: "Копчёные рёбрышки/грудинка (250 г)", cost: 185 },
                    { emoji: "🥔", name: "Картофель (3 шт)", cost: 22 },
                    { emoji: "🥕", name: "Морковь (1 шт)", cost: 9 },
                    { emoji: "🧅", name: "Лук (1 шт)", cost: 8 },
                    { emoji: "🌿", name: "Лавровый лист, специи", cost: 4 },
                    { emoji: "🧂", name: "Соль, масло", cost: 5 }
                ],
                steps: [
                    "Горох замочить на 2-3 часа (или использовать быстровар).",
                    "Копчёности залить водой, варить 30 мин. Добавить горох, варить ещё 30 мин.",
                    "Добавить нарезанный картофель, зажарку из лука и моркови. Варить до готовности.",
                    "Приправить лавровым листом, дать настояться."
                ],
                totalCost: 271
            },
            {
                name: "🍳 Омлет с овощами и ветчиной",
                time: "20 мин",
                servings: "2 порции",
                ingredients: [
                    { emoji: "🥚", name: "Яйца (4 шт)", cost: 48 },
                    { emoji: "🥛", name: "Молоко (60 мл)", cost: 8 },
                    { emoji: "🍖", name: "Ветчина (120 г)", cost: 95 },
                    { emoji: "🍅", name: "Помидор (1 шт)", cost: 22 },
                    { emoji: "🫑", name: "Перец болгарский (1/2)", cost: 30 },
                    { emoji: "🧀", name: "Сыр (50 г)", cost: 45 },
                    { emoji: "🧂", name: "Соль, масло", cost: 5 }
                ],
                steps: [
                    "Яйца взбить с молоком и солью.",
                    "Овощи и ветчину нарезать, слегка обжарить на сковороде.",
                    "Залить яичной смесью, готовить под крышкой 7–10 мин.",
                    "Посыпать сыром за 2 мин до готовности."
                ],
                totalCost: 253
            },
            {
                name: "🌮 Лаваш с начинкой (курица + сыр)",
                time: "25 мин",
                servings: "4 шт (2 порции)",
                ingredients: [
                    { emoji: "🌯", name: "Лаваш тонкий (2 листа)", cost: 38 },
                    { emoji: "🍗", name: "Куриное филе (300 г)", cost: 165 },
                    { emoji: "🧀", name: "Сыр сулугуни/моцарелла (150 г)", cost: 135 },
                    { emoji: "🍅", name: "Помидор (1 шт)", cost: 18 },
                    { emoji: "🥬", name: "Листья салата", cost: 35 },
                    { emoji: "🧄", name: "Соус (сметана+чеснок)", cost: 22 }
                ],
                steps: [
                    "Курицу отварить/обжарить, нарезать полосками.",
                    "Лаваш смазать соусом, выложить сыр, курицу, помидоры и салат.",
                    "Свернуть плотный рулет, обжарить на сухой сковороде до хруста.",
                    "Разрезать пополам."
                ],
                totalCost: 413
            }
        ];

        // ---------- ФУНКЦИИ РЕНДЕРИНГА ----------
        const container = document.getElementById('recipeContainer');

        // Форматирование цены
        function formatPrice(value) {
            return value.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ' ') + ' ₽';
        }

        // Отрисовка рецепта
        function renderRecipe(recipe) {
            if (!recipe) {
                container.innerHTML = `<div class="empty-message">👩‍🍳 Нажмите кнопку — появится вкусный рецепт</div>`;
                return;
            }

            // Собираем список ингредиентов с ценой
            const ingredientsHtml = recipe.ingredients.map(ing => {
                return `<li><span class="ingredient-emoji">${ing.emoji}</span> ${ing.name} <span style="margin-left: auto; font-weight: 450; color: #3f5c3f;">≈${ing.cost}₽</span></li>`;
            }).join('');

            // Шаги
            const stepsHtml = recipe.steps.map(step => `<li>${step}</li>`).join('');

            // Убеждаемся, что сумма не превышает 1000 (на всякий случай)
            const isUnderBudget = recipe.totalCost <= 1000;
            const budgetClass = isUnderBudget ? 'cost-ok' : '';
            const budgetMessage = isUnderBudget ? '✅ Укладывается в 1000 ₽' : '⚠️';

            // Итоговый блок
            const totalBlock = `
                <div class="total-cost-note">
                    <span style="display: flex; align-items: center; gap: 12px;">
                        <span style="font-size: 2rem;">🧾</span> 
                        <span><strong>Общая стоимость блюда</strong><br><span style="font-size: 0.9rem;">(примерные цены ингредиентов)</span></span>
                    </span>
                    <span style="display: flex; align-items: center; gap: 10px;">
                        <span style="font-size: 2.2rem; font-weight: 750;">${formatPrice(recipe.totalCost)}</span>
                        <span class="${budgetClass}">${budgetMessage}</span>
                    </span>
                </div>
            `;

            const html = `
                <div class="recipe-header">
                    <div class="recipe-title">${recipe.name}</div>
                    <div class="price-tag">
                        ${recipe.totalCost} <small>₽</small>
                    </div>
                </div>
                <div class="meta-row">
                    <div class="meta-item"><span class="meta-label">⏱️ Время</span> ${recipe.time}</div>
                    <div class="meta-item"><span class="meta-label">🍽️ Порций</span> ${recipe.servings}</div>
                </div>

                <div class="ingredients-box">
                    <div class="section-title">🛒 Ингредиенты</div>
                    <ul class="ingredient-list">
                        ${ingredientsHtml}
                    </ul>
                </div>

                <div class="steps-box">
                    <div class="section-title">📋 Приготовление</div>
                    <ol class="steps-list">
                        ${stepsHtml}
                    </ol>
                </div>

                ${totalBlock}
            `;
            container.innerHTML = html;
        }

        // Генерация случайного рецепта (всегда до 1000)
        function generateRandomRecipe() {
            const randomIndex = Math.floor(Math.random() * recipes.length);
            return recipes[randomIndex];
        }

        // Обработчик кнопки
        function handleGenerate() {
            const newRecipe = generateRandomRecipe();
            renderRecipe(newRecipe);
        }

        // При загрузке показать приветственный рецепт (любой, но уложимся в бюджет)
        function setInitialRecipe() {
            // Например, первый рецепт или случайный. Используем случайный, чтобы было интереснее.
            const initial = generateRandomRecipe();
            renderRecipe(initial);
        }

        // Вешаем слушатель
        const generateBtn = document.getElementById('generateBtn');
        generateBtn.addEventListener('click', handleGenerate);

        // Старт
        setInitialRecipe();

        // Дополнительно: проверка в консоль, что все рецепты ≤ 1000 (для спокойствия)
        if (recipes.every(r => r.totalCost <= 1000)) {
            console.log('✅ Все рецепты соответствуют бюджету (≤ 1000 руб)');
        } else {
            console.warn('⚠️ Есть рецепт дороже 1000 — исправьте базу');
        }
    })();
</script>

</body>
</html>
