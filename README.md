<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MvMSOLO - Official Site</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: linear-gradient(45deg, #141e30, #243b55);
            color: white;
            text-align: center;
            margin: 0;
            padding: 0;
            transition: background 0.5s;
        }
        .container {
            max-width: 90%;
            margin: 20px auto;
            padding: 15px;
            background-color: rgba(0, 0, 0, 0.7);
            border-radius: 10px;
            box-sizing: border-box;
        }
        .btn {
            background-color: #ff0000;
            padding: 10px 15px;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
            margin-top: 10px;
        }
        #subscribers, #liveViews {
            font-size: 20px;
            font-weight: bold;
            margin-top: 10px;
        }
        #fact {
            font-style: italic;
            margin-top: 10px;
        }
        iframe {
            width: 100%;
            height: auto;
            aspect-ratio: 16 / 9;
            border-radius: 5px;
        }
        .dark-mode {
            background: linear-gradient(45deg, #000000, #222222);
        }
        @media (max-width: 600px) {
            .btn {
                font-size: 14px;
                padding: 8px 12px;
            }
            #subscribers, #liveViews {
                font-size: 18px;
            }
            .container {
                padding: 10px;
            }
        }
    </style>
</head>
<body>

    <h1>🎮 Welcome to MvMSOLO Official Site 🎮</h1>
    
    <div class="container">
        <h2>🔥 My Most Popular Video</h2>
        <iframe src="https://www.youtube.com/embed/yvuDhCpcJeA" frameborder="0" allowfullscreen></iframe>

        <h2>📢 My Goal: 1 Million Subscribers</h2>
        <p>Subscribe to my channel and help me reach my dream! 🎯</p>
        <p>Current Subscribers:</p>
        <div id="subscribers">Loading...</div>
        <p>Live Viewers:</p>
        <div id="liveViews">Loading...</div>

        <button class="btn" onclick="window.location.href='https://www.youtube.com/@MvMSOLO'">Subscribe Now</button>
    </div>

    <div class="container">
        <h2>⚽ Random Football Fact</h2>
        <p id="fact">Loading...</p>
        <button class="btn" onclick="randomFact()">🔄 Refresh Fact</button>
    </div>

    <div class="container">
        <h2>🎬 Latest Video</h2>
        <div id="latestVideo">Loading...</div>
    </div>

    <div class="container">
        <h2>🌍 Weather Update</h2>
        <div id="weather">Loading...</div>
    </div>

    <div class="container">
        <h2>📝 Leave a Comment</h2>
        <textarea id="commentBox" rows="4" cols="50" placeholder="Write your comment..."></textarea>
        <br>
        <button class="btn" onclick="alert('Comment submitted!')">Submit</button>
    </div>

    <div class="container">
        <h2>⏳ Next Giveaway Countdown</h2>
        <div id="countdown">Loading...</div>
    </div>

    <button class="btn" onclick="toggleDarkMode()">🌙 Toggle Dark Mode</button>

    <script>
        function randomFact() {
            const facts = [
                "Cristiano Ronaldo is the only player to win league titles in England, Spain, and Italy.",
                "Lionel Messi has the most Ballon d'Or wins in history.",
                "The fastest goal in World Cup history was scored in 10.8 seconds.",
                "Real Madrid has won the most Champions League titles.",
                "A goalkeeper once scored a goal from 101 meters away."
            ];
            document.getElementById("fact").innerText = facts[Math.floor(Math.random() * facts.length)];
        }

        function toggleDarkMode() {
            document.body.classList.toggle("dark-mode");
        }

        function updateCountdown() {
            const giveawayDate = new Date("2025-03-01T00:00:00");
            const now = new Date();
            const diff = giveawayDate - now;
            const days = Math.floor(diff / (1000 * 60 * 60 * 24));
            document.getElementById("countdown").innerText = `${days} days left!`;
        }

        updateCountdown();
        randomFact();
    </script>

</body>
</html>
