<!DOCTYPE html>
<html lang="bn">
<head>
    <!-- meta tag -->
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no"/>
    
    <title>Easy Earning Bot</title>
    
    <!-- css & font -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
    
    <style>
        :root {
            --primary-color: #2ed914;
            --primary-hover: #3bff21;
            --secondary-color: #2a2a2e;
            --background-color: #1c1c1f;
            --text-color: #f0f0f0;
            --text-muted-color: #a0a0a0;
            --accent-color: #ff8c00;
            --card-bg: #252528;
        }
        * { box-sizing: border-box; -webkit-tap-highlight-color: transparent; }
        body {
            margin: 0; 
            padding: 0; 
            background-color: var(--background-color); 
            color: var(--text-color);
            font-family: 'Segoe UI', 'Roboto', sans-serif; 
            display: flex; 
            justify-content: center; 
            align-items: center;
            height: 100vh; 
        }
        .container {
            width: 100%; max-width: 400px;
            height: 100%;
            background: var(--background-color);
            display: flex; flex-direction: column;
            overflow: hidden; position: relative;
        }
        main { flex-grow: 1; overflow-y: auto; padding: 20px; padding-bottom: 80px; }
        .view { display: none; }
        .view.active { display: block; }
        /* Simplified styles... keep your previous CSS */
    </style>
    
    <!-- Telegram SDK -->
    <script src="https://telegram.org/js/telegram-web-app.js"></script>
    <!-- Monetag SDK -->
    <script src='//libtl.com/sdk.js' data-zone='9961805' data-sdk='show_9961805'></script>
</head>
<body>

    <!-- MAIN CONTAINER -->
    <div class="container">
        <main id="main-content">
            <!-- HOME VIEW -->
            <div id="home-view" class="view active">
                <div class="user-header-card">
                    <div class="user-avatar" id="profile-pic">EE</div>
                    <div class="user-info">
                        <h2 class="username" id="username">Loading...</h2>
                        <p class="title">Welcome Back!</p>
                    </div>
                </div>
                <div class="balance-card">
                    <p class="label">Total Balance</p>
                    <h1 class="balance-value" id="balance-value">৳0.00</h1>
                    <p class="points-value"><i class="fa-solid fa-coins"></i> <span id="points-value">0</span> Points</p>
                </div>
                <h2 class="section-title">Quick Actions</h2>
                <div class="task-card" onclick="showView('tasks-view')">
                    <div class="task-icon"><i class="fa-solid fa-list-check"></i></div>
                    <div class="task-details"><h3>View Tasks</h3><p>Watch ads and complete tasks to earn points.</p></div>
                </div>
                <div class="task-card" onclick="openWithdrawModal()">
                    <div class="task-icon"><i class="fa-solid fa-wallet"></i></div>
                    <div class="task-details"><h3>Withdraw Funds</h3><p>Request to withdraw your available balance.</p></div>
                </div>
            </div>

            <!-- TASKS VIEW -->
            <div id="tasks-view" class="view">
                <h2 class="section-title">Earning Tasks</h2>
                <div class="task-card" onclick="showRewardedInterstitial()">
                    <div class="task-icon"><i class="fa-solid fa-rectangle-ad"></i></div>
                    <div class="task-details"><h3>Rewarded Ad</h3><p>Watch a full-screen ad to earn rewards.</p></div>
                </div>
            </div>
        </main>

        <nav class="footer-nav">
            <button class="nav-button active" onclick="showView('home-view')"><i class="icon fa-solid fa-house"></i>Home</button>
            <button class="nav-button" onclick="showView('tasks-view')"><i class="icon fa-solid fa-list-check"></i>Tasks</button>
        </nav>
    </div>
  
    <!-- JS -->
    <script>
        let points = 0;
        let balance = 0.00;
        let tgUser = null;

        document.addEventListener('DOMContentLoaded', () => {
            initApp();
        });

        function initApp() {
            if (window.Telegram && Telegram.WebApp) {
                Telegram.WebApp.ready();
                Telegram.WebApp.expand();
                tgUser = Telegram.WebApp.initDataUnsafe.user;
            }
            updateDisplay();
        }

        function showView(viewId) {
            document.querySelectorAll('.view').forEach(v => v.classList.remove('active'));
            document.getElementById(viewId).classList.add('active');
        }

        function updateDisplay() {
            document.getElementById('points-value').textContent = points;
            document.getElementById('balance-value').textContent = `৳${balance.toFixed(2)}`;
        }

        function grantReward() {
            const rewardAmount = 2;
            balance += rewardAmount;
            points += 2;
            updateDisplay();
            alert(`✅ You earned ৳${rewardAmount.toFixed(2)}. Balance: ৳${balance.toFixed(2)}`);
        }

        // Monetag ad call
        function showRewardedInterstitial() {
            if (typeof window.show_9961805 !== 'function') {
                return alert('Ad provider not ready. Try again later.');
            }
            window.show_9961805()
                .then(grantReward)
                .catch(e => {
                    console.error('Ad error:', e);
                    alert('Ad failed to load.');
                });
        }

        function openWithdrawModal() {
            alert("Withdrawal system coming soon!");
        }
    </script>
</body>
</html>
