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
        #subscribers, #liveViews {
            font-size: 24px;
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
        <h2>🎬 Latest Live Stream</h2>
        <div id="liveVideo">Loading...</div>
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

        async function getLatestLiveStream() {
            const url = `https://www.googleapis.com/youtube/v3/search?part=snippet&channelId=${CHANNEL_ID}&type=video&eventType=live&maxResults=1&key=${API_KEY}`;
            try {
                let response = await fetch(url);
                let data = await response.json();
                if (data.items.length > 0) {
                    let videoId = data.items[0].id.videoId;
                    document.getElementById("liveVideo").innerHTML = `<iframe width="560" height="315" src="https://www.youtube.com/embed/${videoId}" frameborder="0" allowfullscreen></iframe>`;
                    getLiveViews(videoId);
                } else {
                    document.getElementById("liveVideo").innerText = "No live stream currently.";
                    document.getElementById("liveViews").innerText = "N/A";
                }
            } catch (error) {
                document.getElementById("liveVideo").innerText = "Failed to load live stream.";
                document.getElementById("liveViews").innerText = "N/A";
            }
        }

        async function getLiveViews(videoId) {
            const url = `https://www.googleapis.com/youtube/v3/videos?part=liveStreamingDetails&id=${videoId}&key=${API_KEY}`;
            try {
                let response = await fetch(url);
                let data = await response.json();
                document.getElementById("liveViews").innerText = data.items[0].liveStreamingDetails.concurrentViewers + " Live Viewers";
            } catch (error) {
                document.getElementById("liveViews").innerText = "N/A";
            }
        }

        getSubscribers();
        getLatestLiveStream();
    </script>

</body>
</html>
