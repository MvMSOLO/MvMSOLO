<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MvMSOLO - AI Powered Site</title>
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
            max-width: 900px;
            margin: 20px auto;
            padding: 20px;
            background-color: rgba(0, 0, 0, 0.7);
            border-radius: 10px;
        }
        .btn {
            background-color: #ff0000;
            padding: 10px;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 18px;
            margin-top: 10px;
        }
        #subscribers, #liveViews, #popularVideo, #shortsVideo, #timeNow {
            font-size: 20px;
            font-weight: bold;
            margin-top: 10px;
        }
    </style>
</head>
<body>

    <h1>🎮 Welcome to MvMSOLO Official Site 🎮</h1>
    
    <div class="container">
        <h2>📢 My Goal: 1 Million Subscribers</h2>
        <p>Subscribe to my channel and help me reach my dream! 🎯</p>
        <p>Current Subscribers:</p>
        <div id="subscribers">Loading...</div>
        <p>Live Viewers:</p>
        <div id="liveViews">Loading...</div>

        <button class="btn" onclick="window.location.href='https://www.youtube.com/@MvMSOLO'">Subscribe Now</button>
    </div>

    <div class="container">
        <h2>🔥 Most Popular Video</h2>
        <div id="popularVideo">Loading...</div>
    </div>

    <div class="container">
        <h2>📢 Latest Shorts</h2>
        <div id="shortsVideo">Loading...</div>
    </div>

    <div class="container">
        <h2>🕰 Current Time</h2>
        <div id="timeNow">Loading...</div>
    </div>

    <script>
        const API_KEY = "SIZNING_YOUTUBE_API_KEY";
        const CHANNEL_ID = "UCFrmniXG_EnNC8006SV8UhQ";

        async function getSubscribers() {
            const url = `https://www.googleapis.com/youtube/v3/channels?part=statistics&id=${CHANNEL_ID}&key=${API_KEY}`;
            try {
                let response = await fetch(url);
                let data = await response.json();
                document.getElementById("subscribers").innerText = data.items[0].statistics.subscriberCount + " Subscribers";
            } catch (error) {
                document.getElementById("subscribers").innerText = "Failed to load";
            }
        }

        async function getPopularVideo() {
            const url = `https://www.googleapis.com/youtube/v3/search?part=snippet&channelId=${CHANNEL_ID}&maxResults=1&order=viewCount&type=video&key=${API_KEY}`;
            try {
                let response = await fetch(url);
                let data = await response.json();
                let videoId = data.items[0].id.videoId;
                document.getElementById("popularVideo").innerHTML = `<iframe width="560" height="315" src="https://www.youtube.com/embed/${videoId}" frameborder="0" allowfullscreen></iframe>`;
            } catch (error) {
                document.getElementById("popularVideo").innerText = "Failed to load.";
            }
        }

        async function getShortsVideo() {
            const url = `https://www.googleapis.com/youtube/v3/search?part=snippet&channelId=${CHANNEL_ID}&maxResults=1&order=date&type=video&key=${API_KEY}`;
            try {
                let response = await fetch(url);
                let data = await response.json();
                let videoId = data.items[0].id.videoId;
                document.getElementById("shortsVideo").innerHTML = `<iframe width="560" height="315" src="https://www.youtube.com/embed/${videoId}" frameborder="0" allowfullscreen></iframe>`;
            } catch (error) {
                document.getElementById("shortsVideo").innerText = "Failed to load.";
            }
        }

        function updateTime() {
            let now = new Date();
            document.getElementById("timeNow").innerText = now.toLocaleTimeString();
        }

        setInterval(updateTime, 1000);
        getSubscribers();
        getPopularVideo();
        getShortsVideo();
    </script>

</body>
</html>
