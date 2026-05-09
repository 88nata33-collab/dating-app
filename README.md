<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>💖 Резонанс | Знакомства на частоте твоего сердца</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }
        .app-container { max-width: 1400px; margin: 0 auto; }
        .header {
            background: rgba(255,255,255,0.95);
            border-radius: 20px;
            padding: 20px 30px;
            margin-bottom: 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
        }
        .logo {
            font-size: 28px;
            font-weight: bold;
            background: linear-gradient(135deg, #667eea, #764ba2);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }
        .resonance-status {
            display: flex;
            align-items: center;
            gap: 10px;
            padding: 8px 16px;
            background: #f0f0f0;
            border-radius: 50px;
            font-size: 12px;
        }
        .resonance-dot {
            width: 10px;
            height: 10px;
            border-radius: 50%;
            background: #4ade80;
            animation: pulse 2s infinite;
        }
        @keyframes pulse {
            0%, 100% { opacity: 1; transform: scale(1); }
            50% { opacity: 0.5; transform: scale(1.2); }
        }
        .main-grid {
            display: grid;
            grid-template-columns: 1fr 1.2fr;
            gap: 20px;
        }
        .profile-card {
            background: white;
            border-radius: 30px;
            overflow: hidden;
            box-shadow: 0 20px 60px rgba(0,0,0,0.2);
            transition: transform 0.3s;
        }
        .profile-card:hover { transform: translateY(-5px); }
        .profile-image {
            width: 100%;
            height: 350px;
            background: linear-gradient(135deg, #667eea, #764ba2);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 80px;
        }
        .profile-info { padding: 25px; }
        .profile-name { font-size: 28px; font-weight: bold; margin-bottom: 5px; }
        .profile-age { color: #666; margin-bottom: 15px; }
        .profile-bio { color: #444; line-height: 1.5; margin-bottom: 20px; }
        .resonance-wave {
            background: #f8f9fa;
            border-radius: 15px;
            padding: 15px;
            text-align: center;
            margin: 15px 0;
        }
        .frequency-badge {
            display: inline-block;
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            padding: 5px 15px;
            border-radius: 50px;
            font-size: 14px;
            margin: 5px;
        }
        .action-buttons {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }
        .btn {
            flex: 1;
            padding: 12px;
            border: none;
            border-radius: 50px;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
        }
        .btn-like {
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            color: white;
        }
        .btn-like:hover { transform: scale(1.05); }
        .btn-pass {
            background: #e0e0e0;
            color: #666;
        }
        .btn-pass:hover { background: #d0d0d0; transform: scale(1.05); }
        .matches-panel {
            background: white;
            border-radius: 30px;
            padding: 25px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.1);
        }
        .matches-title {
            font-size: 24px;
            font-weight: bold;
            margin-bottom: 20px;
        }
        .match-item {
            display: flex;
            align-items: center;
            gap: 15px;
            padding: 15px;
            margin-bottom: 10px;
            background: #f8f9fa;
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.3s;
        }
        .match-item:hover {
            background: #e8e9ff;
            transform: translateX(5px);
        }
        .match-avatar {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background: linear-gradient(135deg, #667eea, #764ba2);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 24px;
            font-weight: bold;
        }
        .match-info { flex: 1; }
        .match-name { font-weight: bold; font-size: 16px; }
        .match-resonance { font-size: 12px; color: #667eea; }
        .match-score {
            background: #4ade80;
            color: white;
            padding: 5px 10px;
            border-radius: 20px;
            font-size: 12px;
        }
        .user-profile {
            background: white;
            border-radius: 30px;
            padding: 25px;
            margin-bottom: 20px;
        }
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.8);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }
        .modal.active { display: flex; }
        .chat-container {
            width: 400px;
            max-width: 90%;
            height: 600px;
            background: white;
            border-radius: 30px;
            display: flex;
            flex-direction: column;
            overflow: hidden;
        }
        .chat-header {
            padding: 20px;
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            display: flex;
            justify-content: space-between;
        }
        .chat-messages {
            flex: 1;
            overflow-y: auto;
            padding: 20px;
        }
        .message {
            margin-bottom: 15px;
            display: flex;
        }
        .message.user { justify-content: flex-end; }
        .message-bubble {
            max-width: 70%;
            padding: 10px 15px;
            border-radius: 20px;
            background: #f0f0f0;
        }
        .message.user .message-bubble {
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
        }
        .chat-input {
            padding: 20px;
            border-top: 1px solid #e0e0e0;
            display: flex;
            gap: 10px;
        }
        .chat-input input {
            flex: 1;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 25px;
            outline: none;
        }
        .chat-input button {
            padding: 10px 20px;
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            border: none;
            border-radius: 25px;
            cursor: pointer;
        }
        @media (max-width: 768px) {
            .main-grid { grid-template-columns: 1fr; }
        }
    </style>
</head>
<body>
    <div class="app-container">
        <div class="header">
            <div class="logo">💖 Резонанс | Знакомства</div>
            <div class="resonance-status">
                <div class="resonance-dot"></div>
                <span id="resonanceStatus">Ядро активно</span>
            </div>
        </div>

        <div class="user-profile">
            <h2 id="currentUserName">Загрузка...</h2>
            <p id="currentUserFreq">Частота: -- Hz</p>
        </div>

        <div class="main-grid">
            <div class="profile-card">
                <div class="profile-image" id="profileImage">💑</div>
                <div class="profile-info">
                    <div class="profile-name" id="profileName">Имя</div>
                    <div class="profile-age" id="profileAge">Возраст</div>
                    <div class="profile-bio" id="profileBio">Описание</div>
                    <div class="resonance-wave">
                        <div>🎵 Резонансная частота</div>
                        <div><span class="frequency-badge" id="profileFreq">--- Hz</span></div>
                        <div style="margin-top:10px" id="compatibilityText"></div>
                    </div>
                    <div class="action-buttons">
                        <button class="btn btn-pass" onclick="app.pass()">❌ Пропустить</button>
                        <button class="btn btn-like" onclick="app.like()">💖 Нравится</button>
                    </div>
                </div>
            </div>

            <div class="matches-panel">
                <div class="matches-title">💕 Совпадения <span id="matchesCount">(0)</span></div>
                <div id="matchesList">
                    <div style="text-align:center; color:#999; padding:40px;">Лайкай анкеты!</div>
                </div>
            </div>
        </div>
    </div>

    <div class="modal" id="chatModal">
        <div class="chat-container">
            <div class="chat-header">
                <span id="chatPartnerName">Чат</span>
                <button onclick="app.closeChat()" style="background:none; border:none; color:white; font-size:24px;">✕</button>
            </div>
            <div class="chat-messages" id="chatMessages">
                <div class="message"><div class="message-bubble">Привет! Давай общаться 💫</div></div>
            </div>
            <div class="chat-input">
                <input type="text" id="chatInput" placeholder="Напиши сообщение..." onkeypress="if(event.key==='Enter') app.sendMessage()">
                <button onclick="app.sendMessage()">→</button>
            </div>
        </div>
    </div>

    <script>
        // ========== РЕЗОНАНСНОЕ ЯДРО ==========
        class ResonanceEngine {
            constructor() {
                this.frequency = 60;
                this.coherence = 0.5;
                this.couplings = new Map();
            }
            
            calculateResonance(f1, f2) {
                const diff = Math.abs(f1 - f2);
                return Math.exp(-diff * diff / 100);
            }
            
            addCoupling(userId, freq) {
                const score = this.calculateResonance(this.frequency, freq);
                this.couplings.set(userId, score);
                return score;
            }
            
            updateCoherence() {
                if (this.couplings.size === 0) this.coherence = 0.5;
                else {
                    let sum = 0;
                    for (let s of this.couplings.values()) sum += s;
                    this.coherence = sum / this.couplings.size;
                }
                return this.coherence;
            }
        }
        
        // ========== ПРИЛОЖЕНИЕ ==========
        class DatingApp {
            constructor() {
                this.resonance = new ResonanceEngine();
                this.profiles = [];
                this.likes = new Map();
                this.matches = new Map();
                this.currentIndex = 0;
                this.currentProfile = null;
                this.chatPartner = null;
                this.init();
            }
            
            init() {
                // Создаём анкеты
                const names = ['Анна', 'Максим', 'Екатерина', 'Дмитрий', 'Ольга', 'Алексей', 'Мария', 'Иван'];
                const bios = [
                    'Люблю путешествия и фото 📸',
                    'Программист, играю на гитаре 🎸',
                    'Йога и здоровое питание 🧘',
                    'Книги и кофе 📚☕',
                    'Активный отдых 🏔️',
                    'Художник, творчество 🎨',
                    'Готовлю лучше всех 🍳',
                    'Путешественник 🌍'
                ];
                
                for (let i = 0; i < 16; i++) {
                    this.profiles.push({
                        id: i,
                        name: names[i % names.length] + (i > 7 ? ' ✨' : ''),
                        age: 20 + Math.floor(Math.random() * 30),
                        bio: bios[i % bios.length],
                        frequency: 40 + Math.random() * 80
                    });
                }
                
                this.currentUser = { name: 'Ты', frequency: this.resonance.frequency };
                document.getElementById('currentUserName').innerHTML = '👤 ' + this.currentUser.name;
                this.loadNext();
                this.startLoop();
                window.app = this;
            }
            
            loadNext() {
                if (this.currentIndex >= this.profiles.length) this.currentIndex = 0;
                this.currentProfile = this.profiles[this.currentIndex];
                
                document.getElementById('profileName').textContent = this.currentProfile.name;
                document.getElementById('profileAge').textContent = this.currentProfile.age + ' лет';
                document.getElementById('profileBio').textContent = this.currentProfile.bio;
                document.getElementById('profileFreq').textContent = this.currentProfile.frequency.toFixed(0) + ' Hz';
                
                const score = this.resonance.calculateResonance(this.resonance.frequency, this.currentProfile.frequency);
                const percent = Math.round(score * 100);
                document.getElementById('compatibilityText').innerHTML = `Совместимость: ${percent}%`;
            }
            
            like() {
                const profile = this.currentProfile;
                const score = this.resonance.addCoupling(profile.id, profile.frequency);
                this.likes.set(profile.id, { profile, score });
                
                // 30% шанс взаимности
                if (Math.random() < 0.3) {
                    this.matches.set(profile.id, { profile, score, messages: [] });
                    this.updateMatches();
                    this.showMsg('💕 Взаимный интерес!');
                }
                
                this.currentIndex++;
                this.loadNext();
            }
            
            pass() {
                this.currentIndex++;
                this.loadNext();
            }
            
            updateMatches() {
                const container = document.getElementById('matchesList');
                const count = this.matches.size;
                document.getElementById('matchesCount').innerHTML = `(${count})`;
                
                if (count === 0) {
                    container.innerHTML = '<div style="text-align:center; color:#999; padding:40px;">Лайкай анкеты!</div>';
                    return;
                }
                
                container.innerHTML = Array.from(this.matches.values()).map(m => `
                    <div class="match-item" onclick="app.openChat(${m.profile.id})">
                        <div class="match-avatar">${m.profile.name[0]}</div>
                        <div class="match-info">
                            <div class="match-name">${m.profile.name}, ${m.profile.age}</div>
                            <div class="match-resonance">🎵 ${m.profile.frequency.toFixed(0)} Hz</div>
                        </div>
                        <div class="match-score">💖</div>
                    </div>
                `).join('');
            }
            
            openChat(userId) {
                this.chatPartner = this.matches.get(userId);
                document.getElementById('chatPartnerName').textContent = this.chatPartner.profile.name;
                document.getElementById('chatModal').classList.add('active');
                this.renderChat();
            }
            
            closeChat() {
                document.getElementById('chatModal').classList.remove('active');
                this.chatPartner = null;
            }
            
            renderChat() {
                const container = document.getElementById('chatMessages');
                const msgs = this.chatPartner.messages || [];
                if (msgs.length === 0) {
                    container.innerHTML = '<div class="message"><div class="message-bubble">Привет! 💫</div></div>';
                } else {
                    container.innerHTML = msgs.map(m => `
                        <div class="message ${m.from === 'me' ? 'user' : ''}">
                            <div class="message-bubble">${m.text}</div>
                        </div>
                    `).join('');
                }
                container.scrollTop = container.scrollHeight;
            }
            
            sendMessage() {
                const input = document.getElementById('chatInput');
                const text = input.value.trim();
                if (!text || !this.chatPartner) return;
                
                this.chatPartner.messages = this.chatPartner.messages || [];
                this.chatPartner.messages.push({ from: 'me', text });
                this.renderChat();
                input.value = '';
                
                // Ответ через 1 секунду
                setTimeout(() => {
                    const answers = ['Круто! Расскажи ещё 😊', 'У нас много общего!', 'Ты мне нравишься 💕', 'Давай встретимся?'];
                    const reply = answers[Math.floor(Math.random() * answers.length)];
                    this.chatPartner.messages.push({ from: 'them', text: reply });
                    this.renderChat();
                }, 1000);
            }
            
            showMsg(text) {
                const div = document.createElement('div');
                div.style.cssText = 'position:fixed; bottom:20px; right:20px; background:#764ba2; color:white; padding:15px 25px; border-radius:50px; z-index:1000;';
                div.textContent = text;
                document.body.appendChild(div);
                setTimeout(() => div.remove(), 2000);
            }
            
            startLoop() {
                setInterval(() => {
                    this.resonance.updateCoherence();
                    const status = this.resonance.coherence > 0.6 ? '🔥 Высокий резонанс' : '📡 Настройка';
                    document.getElementById('resonanceStatus').innerHTML = status + ' ' + this.resonance.coherence.toFixed(2);
                }, 1000);
            }
        }
        
        // ЗАПУСК
        const app = new DatingApp();
        console.log('💖 Сайт знакомств запущен!');
    </script>
</body>
</html>
