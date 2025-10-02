<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Easy Earning Bot</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(to bottom right, #6a11cb, #2575fc);
            color: #fff;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: flex-start;
            min-height: 100vh;
            padding: 20px;
            margin: 0;
        }

        h1 {
            margin-top: 40px;
            font-size: 2.5em;
            text-shadow: 2px 2px 8px rgba(0,0,0,0.3);
        }

        .welcome-msg {
            background: rgba(255, 255, 255, 0.2);
            padding: 15px 25px;
            border-radius: 12px;
            font-size: 1.2em;
            margin: 20px 0;
            text-align: center;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            animation: fadeIn 2s ease-in-out;
        }

        @keyframes fadeIn {
            0% {opacity: 0; transform: translateY(-20px);}
            100% {opacity: 1; transform: translateY(0);}
        }

        .ad-container {
            width: 100%;
            max-width: 500px;
            background: rgba(255, 255, 255, 0.1);
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0 8px 20px rgba(0,0,0,0.3);
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .ad-title {
            font-size: 1.3em;
            margin-bottom: 15px;
        }

        .ad-box {
            width: 100%;
            min-height: 200px;
            background: rgba(255,255,255,0.2);
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 20px;
        }

        button {
            background: #fff;
            color: #2575fc;
            border: none;
            padding: 12px 25px;
            font-size: 1em;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        button:hover {
            background: #f0f0f0;
            transform: scale(1.05);
        }

        footer {
            margin-top: auto;
            font-size: 0.9em;
            opacity: 0.7;
        }
    </style>
</head>
<body>
    <h1>Easy Earning Bot</h1>

    <!-- Animated Welcome Message -->
    <div class="welcome-msg">
        Welcome! Watch ads below to earn rewards.
    </div>

    <!-- Ad Container -->
    <div class="ad-container">
        <div class="ad-title">Your Ad</div>
        <div class="ad-box" id="adBox">
            <!-- Monetag ad -->
            <script src="//libtl.com/sdk.js" data-zone="9961805" data-sdk="show_9961805"></script>
        </div>
        <button onclick="refreshAd()">Refresh Ad</button>
    </div>

    <footer>© 2025 Easy Earning Bot</footer>

    <script>
        // Refresh ad function
        function refreshAd() {
            const adBox = document.getElementById('adBox');
            adBox.innerHTML = ""; // Clear previous ad
            const script = document.createElement('script');
            script.src = "//libtl.com/sdk.js";
            script.setAttribute('data-zone', '9961805');
            script.setAttribute('data-sdk', 'show_9961805');
            script.async = true;
            adBox.appendChild(script);
        }
    </script>
</body>
</html>
