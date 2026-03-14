<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>BOOMER CASES</title>
    <script src="https://telegram.org/js/telegram-web-app.js"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
        }

        :root {
            --bg-dark: #0a0c15;
            --bg-card: #141a26;
            --accent: #ffd700;
            --accent-glow: rgba(255, 215, 0, 0.3);
            --text: #ffffff;
            --text-secondary: #b0b7c9;
            --border: #2a3342;
        }

        body {
            background: var(--bg-dark);
            color: var(--text);
            min-height: 100vh;
            padding: 16px;
            padding-bottom: 80px;
            background-image: radial-gradient(circle at 10% 20%, rgba(255, 215, 0, 0.05) 0%, transparent 40%);
        }

        /* Шапка профиля */
        .glass-card {
            background: var(--bg-card);
            border-radius: 28px;
            padding: 20px;
            margin-bottom: 20px;
            border: 1px solid var(--border);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
            backdrop-filter: blur(10px);
        }

        .profile-header {
            display: flex;
            align-items: center;
            gap: 16px;
        }

        .avatar {
            width: 70px;
            height: 70px;
            background: linear-gradient(135deg, var(--accent), #ffaa00);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 32px;
            border: 3px solid var(--accent);
            box-shadow: 0 0 30px var(--accent-glow);
        }

        .stars-badge {
            display: flex;
            align-items: center;
            gap: 8px;
            background: rgba(255, 215, 0, 0.15);
            padding: 8px 18px;
            border-radius: 40px;
            width: fit-content;
            border: 1px solid rgba(255, 215, 0, 0.3);
        }

        .stars-count {
            color: var(--accent);
            font-size: 24px;
            font-weight: bold;
        }

        /* Навигация */
        .nav-tabs {
            display: flex;
            background: var(--bg-card);
            padding: 6px;
            border-radius: 50px;
            margin-bottom: 20px;
            border: 1px solid var(--border);
            flex-wrap: wrap;
        }

        .nav-tab {
            flex: 1;
            text-align: center;
            padding: 12px 5px;
            border-radius: 44px;
            color: var(--text-secondary);
            font-weight: 600;
            cursor: pointer;
            transition: all 0.2s;
            font-size: 14px;
        }

        .nav-tab.active {
            background: var(--accent);
            color: #000;
            box-shadow: 0 0 20px var(--accent-glow);
        }

        /* Кнопки */
        .btn {
            background: linear-gradient(135deg, var(--accent), #ffaa00);
            color: #000;
            border: none;
            padding: 16px;
            border-radius: 50px;
            font-size: 16px;
            font-weight: bold;
            width: 100%;
            cursor: pointer;
            transition: all 0.2s;
            margin: 5px 0;
            box-shadow: 0 5px 20px var(--accent-glow);
        }

        .btn:active {
            transform: scale(0.97);
        }

        /* Кейсы */
        .cases-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 12px;
            margin-bottom: 20px;
        }

        .case-card {
            background: var(--bg-card);
            border-radius: 24px;
            padding: 20px 15px;
            text-align: center;
            border: 1px solid var(--border);
            cursor: pointer;
            transition: all 0.2s;
        }

        .case-card:active {
            transform: scale(0.97);
            border-color: var(--accent);
        }

        .case-emoji {
            font-size: 40px;
            margin-bottom: 10px;
        }

        .case-name {
            font-weight: 600;
            margin-bottom: 8px;
            font-size: 14px;
        }

        .case-price {
            color: var(--accent);
            font-size: 24px;
            font-weight: bold;
        }

        /* LIVE лента */
        .live-feed {
            background: var(--bg-card);
            border-radius: 24px;
            padding: 15px;
            margin-bottom: 20px;
        }

        .live-item {
            display: flex;
            justify-content: space-between;
            padding: 8px;
            border-bottom: 1px solid var(--border);
        }

        /* Модальное окно */
        .modal {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(0,0,0,0.95);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 1000;
        }

        .modal.active {
            display: flex;
        }

        .modal-content {
            background: var(--bg-card);
            padding: 30px;
            border-radius: 30px;
            text-align: center;
            border: 2px solid var(--accent);
            max-width: 85%;
        }

        .modal-emoji {
            font-size: 70px;
            margin-bottom: 15px;
        }

        /* Нижняя навигация */
        .bottom-nav {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background: var(--bg-card);
            backdrop-filter: blur(20px);
            display: flex;
            justify-content: space-around;
            padding: 12px 8px 20px;
            border-top: 1px solid var(--border);
        }

        .nav-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            color: var(--text-secondary);
            font-size: 11px;
            gap: 4px;
            cursor: pointer;
        }

        .nav-item.active {
            color: var(--accent);
        }

        .nav-icon {
            font-size: 22px;
        }
    </style>
</head>
<body>
    <!-- Шапка профиля -->
    <div class="glass-card">
        <div class="profile-header">
            <div class="avatar" id="avatar">👤</div>
            <div style="flex:1">
                <h2 id="username">Загрузка...</h2>
                <div class="stars-badge">
                    <span>⭐</span>
                    <span class="stars-count" id="stars">0</span>
                </div>
            </div>
        </div>
    </div>

    <!-- Навигация -->
    <div class="nav-tabs">
        <div class="nav-tab active" onclick="showPage('main')">🏠 Главная</div>
        <div class="nav-tab" onclick="showPage('cases')">🎁 Кейсы</div>
        <div class="nav-tab" onclick="showPage('inventory')">📦 Инвентарь</div>
        <div class="nav-tab" onclick="showPage('top')">🏆 Топ</div>
        <div class="nav-tab" onclick="showPage('profile')">👤 Профиль</div>
    </div>

    <!-- Контент -->
    <div id="content">
        <!-- Главная -->
        <div id="main-page">
            <!-- LIVE лента -->
            <div class="live-feed">
                <h3 style="color: var(--accent); margin-bottom: 10px;">🔴 LIVE</h3>
                <div id="liveFeed"></div>
            </div>

            <!-- Популярные кейсы -->
            <h3 style="margin-bottom: 15px; color: var(--accent);">🔥 ПОПУЛЯРНЫЕ КЕЙСЫ</h3>
            <div class="cases-grid" id="popularCases"></div>

            <!-- Ежедневный бонус -->
            <div class="glass-card">
                <h3 style="color: var(--accent); margin-bottom: 10px;">📦 ЕЖЕДНЕВНЫЙ БОНУС</h3>
                <button class="btn" onclick="claimDaily()">ЗАБРАТЬ 100⭐</button>
            </div>
        </div>

        <!-- Кейсы -->
        <div id="cases-page" style="display: none;">
            <h3 style="margin-bottom: 15px; color: var(--accent);">🎁 ВСЕ КЕЙСЫ</h3>
            <div class="cases-grid" id="allCases"></div>
        </div>

        <!-- Инвентарь -->
        <div id="inventory-page" style="display: none;">
            <div class="glass-card">
                <h3 style="margin-bottom: 15px; color: var(--accent);">📦 ИНВЕНТАРЬ</h3>
                <div class="cases-grid" id="inventory"></div>
            </div>
        </div>

        <!-- Топ -->
        <div id="top-page" style="display: none;">
            <div class="glass-card">
                <h3 style="margin-bottom: 15px; color: var(--accent);">🏆 ТОП ИГРОКОВ</h3>
                <div id="topList"></div>
            </div>
        </div>

        <!-- Профиль -->
        <div id="profile-page" style="display: none;">
            <div class="glass-card">
                <h3 style="margin-bottom: 15px; color: var(--accent);">👤 ПРОФИЛЬ</h3>
                <div style="text-align: center;">
                    <div style="font-size: 20px; margin-bottom: 10px;" id="profileName"></div>
                    <div style="font-size: 16px; color: var(--accent);" id="profileStars"></div>
                    <div style="margin-top: 20px;">
                        <p>👥 Рефералов: <span id="referrals">0</span></p>
                        <p>🎨 NFT: <span id="nftCount">0</span></p>
                        <p>📊 Всего заработано: <span id="totalEarned">0</span>⭐</p>
                    </div>
                    <div style="margin-top: 20px;">
                        <p>📞 Связаться с админом:</p>
                        <button class="btn" onclick="copyAdmin()">@your_username</button>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Нижняя навигация -->
    <div class="bottom-nav">
        <div class="nav-item active" onclick="showPage('main')">
            <span class="nav-icon">🏠</span>
            <span>Главная</span>
        </div>
        <div class="nav-item" onclick="showPage('cases')">
            <span class="nav-icon">🎁</span>
            <span>Кейсы</span>
        </div>
        <div class="nav-item" onclick="showPage('inventory')">
            <span class="nav-icon">📦</span>
            <span>Инвентарь</span>
        </div>
        <div class="nav-item" onclick="showPage('top')">
            <span class="nav-icon">🏆</span>
            <span>Топ</span>
        </div>
        <div class="nav-item" onclick="showPage('profile')">
            <span class="nav-icon">👤</span>
            <span>Профиль</span>
        </div>
    </div>

    <!-- Модальное окно -->
    <div class="modal" id="modal">
        <div class="modal-content">
            <div class="modal-emoji" id="modalEmoji">🎉</div>
            <h2 id="modalTitle"></h2>
            <p id="modalText"></p>
            <button class="btn" onclick="closeModal()">OK</button>
        </div>
    </div>

    <script>
        let tg = Telegram.WebApp;
        tg.ready();
        tg.expand();

        // ========== БАЗА ДАННЫХ ==========
        let user = {
            id: null,
            username: '',
            stars: 100,
            total_earned: 100,
            nft: [],
            inventory: [],
            referrals: 0,
            lastDaily: null
        };

        // Загружаем данные пользователя
        let tgUser = tg.initDataUnsafe?.user;
        if (tgUser) {
            user.id = tgUser.id;
            user.username = tgUser.first_name || 'Игрок';
        }

        // Сохраняем данные
        function saveUserData() {
            tg.sendData(JSON.stringify({
                stars: user.stars,
                total_earned: user.total_earned,
                nft: user.nft,
                inventory: user.inventory,
                referrals: user.referrals,
                lastDaily: user.lastDaily
            }));
        }

        // ========== ВСЕ КЕЙСЫ ==========
        const allCases = [
            {id: 1, name: 'FREE', price: 1, emoji: '🎁'},
            {id: 2, name: 'STARTER', price: 5, emoji: '⭐'},
            {id: 3, name: 'BASIC', price: 10, emoji: '📦'},
            {id: 4, name: 'SILVER', price: 15, emoji: '🥈'},
            {id: 5, name: 'GOLD', price: 25, emoji: '🥇'},
            {id: 6, name: 'PLATINUM', price: 39, emoji: '💎'},
            {id: 7, name: 'DIAMOND', price: 49, emoji: '🔷'},
            {id: 8, name: 'RUBY', price: 69, emoji: '🔴'},
            {id: 9, name: 'EMERALD', price: 79, emoji: '💚'},
            {id: 10, name: 'SAPPHIRE', price: 89, emoji: '💙'},
            {id: 11, name: 'AMETHYST', price: 99, emoji: '💜'},
            {id: 12, name: 'OPAL', price: 129, emoji: '✨'},
            {id: 13, name: 'PEARL', price: 149, emoji: '🦪'},
            {id: 14, name: 'JADE', price: 169, emoji: '🍀'},
            {id: 15, name: 'ONYX', price: 199, emoji: '⚫'},
            {id: 16, name: 'CRYSTAL', price: 249, emoji: '🔮'},
            {id: 17, name: 'MYSTIC', price: 299, emoji: '🌀'},
            {id: 18, name: 'LEGEND', price: 399, emoji: '🌟'},
            {id: 19, name: 'MYTHIC', price: 499, emoji: '⚡'},
            {id: 20, name: 'COSMIC', price: 699, emoji: '🌌'},
            {id: 21, name: 'GALAXY', price: 899, emoji: '🌠'},
            {id: 22, name: 'NEBULA', price: 999, emoji: '☁️'},
            {id: 23, name: 'PEPE', price: 16000, emoji: '🐸'},
            {id: 24, name: 'GOAT', price: 18000, emoji: '🐐'},
        ];

        // ========== NFT ПОДАРКИ ==========
        const nftItems = [
            {name: 'Обычный NFT', value: 600, emoji: '🎨'},
            {name: 'Bear Reggae', value: 18000, emoji: '🧸🎸'},
            {name: 'Beer Bear', value: 25000, emoji: '🧸🍺'},
            {name: 'Gold Bear', value: 50000, emoji: '🧸🥇'},
            {name: 'Diamond Bear', value: 100000, emoji: '🧸💎'},
            {name: 'Rainbow Bear', value: 250000, emoji: '🧸🌈'},
            {name: 'Galaxy Bear', value: 500000, emoji: '🧸🌌'},
            {name: 'Cosmic Bear', value: 750000, emoji: '🧸🚀'},
            {name: 'Legend Bear', value: 1000000, emoji: '🧸👑'},
            {name: 'Immortal Bear', value: 2500000, emoji: '🧸♾️'}
        ];

        // ========== ОТКРЫТИЕ КЕЙСА ==========
        function openCase(caseId) {
            let caseData = allCases.find(c => c.id === caseId);
            if (user.stars < caseData.price) {
                showModal('❌ Ошибка', 'Недостаточно звёзд', '😢');
                return;
            }

            user.stars -= caseData.price;
            showModal('🎲', 'Крутится...', '🎰');

            setTimeout(() => {
                let win = 0;
                let giftName = '';
                let isNFT = false;

                // Кейс за 16000⭐ (только NFT)
                if (caseData.price === 16000) {
                    let nft = nftItems[Math.floor(Math.random() * nftItems.length)];
                    isNFT = true;
                    giftName = nft.name;
                    user.nft.push(giftName);
                    user.inventory.push({name: giftName, value: nft.value, emoji: nft.emoji});
                }
                
                // Кейс за 18000⭐ (шанс на Immortal Bear)
                else if (caseData.price === 18000) {
                    if (Math.random() < 0.0001) { // 0.01% на Immortal Bear
                        isNFT = true;
                        giftName = 'Immortal Bear';
                        user.nft.push(giftName);
                        user.inventory.push({name: giftName, value: 2500000, emoji: '🧸♾️'});
                    } else {
                        let nft = nftItems[Math.floor(Math.random() * nftItems.length)];
                        isNFT = true;
                        giftName = nft.name;
                        user.nft.push(giftName);
                        user.inventory.push({name: giftName, value: nft.value, emoji: nft.emoji});
                    }
                }
                
                // Обычные кейсы
                else {
                    win = Math.floor(Math.random() * 50) + 10;
                    giftName = win + ' ⭐';
                }

                if (!isNFT) {
                    user.stars += win;
                    user.total_earned += win;
                }

                // Добавляем в LIVE ленту
                addToLive(user.username, `открыл ${caseData.name}`, giftName);

                showModal('🎉 РЕЗУЛЬТАТ!', giftName, isNFT ? '🎨' : '⭐');
                saveUserData();
                updateUI();
            }, 1500);
        }

        // ========== LIVE ЛЕНТА ==========
        let liveFeed = [];

        function addToLive(username, action, item) {
            liveFeed.unshift({
                username: username,
                action: action,
                item: item,
                time: new Date().toLocaleTimeString().slice(0,5)
            });
            if (liveFeed.length > 10) liveFeed.pop();
            renderLive();
        }

        function renderLive() {
            let html = '';
            liveFeed.forEach(l => {
                html += `<div class="live-item">
                    <span>${l.username}</span>
                    <span>${l.action}</span>
                    <span style="color:var(--accent)">${l.item}</span>
                </div>`;
            });
            document.getElementById('liveFeed').innerHTML = html || 'Пока ничего нет';
        }

        // ========== ЕЖЕДНЕВНЫЙ БОНУС ==========
        function claimDaily() {
            let now = new Date();
            if (user.lastDaily) {
                let last = new Date(user.lastDaily);
                if (now - last < 24*60*60*1000) {
                    showModal('⏳ Подожди', 'Бонус через 24ч', '⌛');
                    return;
                }
            }

            user.lastDaily = now;
            user.stars += 100;
            user.total_earned += 100;
            
            showModal('✅ Бонус!', '+100⭐', '🎁');
            saveUserData();
            updateUI();
        }

        // ========== ОБНОВЛЕНИЕ ИНТЕРФЕЙСА ==========
        function updateUI() {
            document.getElementById('username').textContent = user.username;
            document.getElementById('stars').textContent = user.stars;
            document.getElementById('profileName').textContent = user.username;
            document.getElementById('profileStars').textContent = user.stars + '⭐';
            document.getElementById('referrals').textContent = user.referrals;
            document.getElementById('nftCount').textContent = user.nft.length;
            document.getElementById('totalEarned').textContent = user.total_earned;
        }

        // ========== ПОКАЗ СТРАНИЦ ==========
        function showPage(page) {
            document.querySelectorAll('[id$="-page"]').forEach(p => p.style.display = 'none');
            document.getElementById(page + '-page').style.display = 'block';
        }

        // ========== МОДАЛЬНОЕ ОКНО ==========
        function showModal(title, text, emoji) {
            document.getElementById('modalTitle').textContent = title;
            document.getElementById('modalText').textContent = text;
            document.getElementById('modalEmoji').textContent = emoji;
            document.getElementById('modal').classList.add('active');
        }

        function closeModal() {
            document.getElementById('modal').classList.remove('active');
        }

        // ========== КОПИРОВАТЬ АДМИНА ==========
        function copyAdmin() {
            navigator.clipboard.writeText('@your_username');
            showModal('✅ Скопировано!', '@your_username', '📋');
        }

        // ========== ОТОБРАЖЕНИЕ КЕЙСОВ ==========
        function renderCases() {
            let html = '';
            allCases.forEach(c => {
                html += `<div class="case-card" onclick="openCase(${c.id})">
                    <div class="case-emoji">${c.emoji}</div>
                    <div class="case-name">${c.name}</div>
                    <div class="case-price">${c.price}⭐</div>
                </div>`;
            });
            document.getElementById('allCases').innerHTML = html;
            
            let popular = allCases.slice(0, 4);
            html = '';
            popular.forEach(c => {
                html += `<div class="case-card" onclick="openCase(${c.id})">
                    <div class="case-emoji">${c.emoji}</div>
                    <div class="case-name">${c.name}</div>
                    <div class="case-price">${c.price}⭐</div>
                </div>`;
            });
            document.getElementById('popularCases').innerHTML = html;
        }

        // ========== ЗАПУСК ==========
        renderCases();
        updateUI();
    </script>
</body>
</html>
