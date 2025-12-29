# the-count<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>💖 Countdown Until I See You Amor 💖</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background: #ffe6f0;
            color: #333;
            padding: 50px;
        }
        h1, h2, h3 {
            color: #e91e63;
        }
        .metric {
            display: inline-block;
            margin: 10px 20px;
            padding: 20px;
            background: #fff0f5;
            border-radius: 10px;
            box-shadow: 2px 2px 10px rgba(0,0,0,0.1);
        }
        .metric h2 {
            margin: 0;
        }
        .metric p {
            margin: 5px 0 0;
            font-size: 1.2em;
        }
    </style>
</head>
<body>
    <h1>💖 Countdown Until I See You Amor 💖</h1>

    <h3>⏰ Current Time</h3>
    <p><strong>Jorge's time (Texas):</strong> <span id="texas-time"></span></p>
    <p><strong>Carli's time (Utah):</strong> <span id="utah-time"></span></p>

    <hr>

    <h3>⏳ Time Remaining</h3>
    <div class="metric">
        <h2 id="days">0</h2>
        <p>Days</p>
    </div>
    <div class="metric">
        <h2 id="hours">0</h2>
        <p>Hours</p>
    </div>
    <div class="metric">
        <h2 id="minutes">0</h2>
        <p>Minutes</p>
    </div>
    <div class="metric">
        <h2 id="seconds">0</h2>
        <p>Seconds</p>
    </div>

    <h3 id="message">I miss you Carli :)</h3>
    <p>Every second is one second closer to you 💕</p>

    <script>
        const targetUtah = new Date('2026-01-04T23:00:00-07:00'); // Utah is UTC-7
        const texasTimeZone = 'America/Chicago';
        const utahTimeZone = 'America/Denver';

        function updateClock() {
            const now = new Date();

            // Display current times
            document.getElementById('texas-time').innerText = now.toLocaleString('en-US', { timeZone: texasTimeZone, hour12: true });
            document.getElementById('utah-time').innerText = now.toLocaleString('en-US', { timeZone: utahTimeZone, hour12: true });

            // Calculate remaining time
            const nowUtah = new Date(now.toLocaleString('en-US', { timeZone: utahTimeZone }));
            let remainingMs = targetUtah - nowUtah;

            if (remainingMs <= 0) {
                document.getElementById('days').innerText = 0;
                document.getElementById('hours').innerText = 0;
                document.getElementById('minutes').innerText = 0;
                document.getElementById('seconds').innerText = 0;
                document.getElementById('message').innerHTML = "✨ It’s finally Sunday ✨<br>11:00 PM Utah Time ❤️<br>I get to see you ❤️<br>I’ve been counting every second.";
            } else {
                const days = Math.floor(remainingMs / (1000 * 60 * 60 * 24));
                const hours = Math.floor((remainingMs % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
                const minutes = Math.floor((remainingMs % (1000 * 60 * 60)) / (1000 * 60));
                const seconds = Math.floor((remainingMs % (1000 * 60)) / 1000);

                document.getElementById('days').innerText = days;
                document.getElementById('hours').innerText = hours;
                document.getElementById('minutes').innerText = minutes;
                document.getElementById('seconds').innerText = seconds;
            }
        }

        setInterval(updateClock, 1000);
        updateClock();
    </script>
</body>
</html>
