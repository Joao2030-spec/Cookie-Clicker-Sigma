<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cookie Clicker Ultimate</title>
    <style>
        body {
            text-align: center;
            font-family: Arial, sans-serif;
            background-color: #222;
            color: #fff;
        }
        .cookie {
            width: 150px;
            cursor: pointer;
            transition: transform 0.1s;
        }
        .cookie:active {
            transform: scale(0.9);
        }
        .container {
            margin-top: 50px;
        }
        .shop {
            margin-top: 20px;
        }
        button {
            padding: 10px;
            margin: 5px;
            cursor: pointer;
            background-color: #ff9800;
            border: none;
            color: white;
            font-size: 16px;
            border-radius: 5px;
        }
        button:hover {
            background-color: #e68900;
        }
        .stats {
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Cookie Clicker Ultimate</h1>
        <h2>Cookies: <span id="cookieCount">0</span></h2>
        <h3>Cookies Per Second: <span id="cpsCount">0</span></h3>
        <img src="https://upload.wikimedia.org/wikipedia/commons/a/a5/Red_Apple.jpg" class="cookie" id="cookie" onclick="addCookie()">
        <div class="shop">
            <h3>Upgrades</h3>
            <button onclick="buyUpgrade(1)">Cursor (Cost: <span id="cursorCost">10</span>)</button>
            <button onclick="buyUpgrade(10)">Grandma (Cost: <span id="grandmaCost">100</span>)</button>
            <button onclick="buyUpgrade(50)">Factory (Cost: <span id="factoryCost">500</span>)</button>
            <button onclick="buyUpgrade(200)">Mine (Cost: <span id="mineCost">2000</span>)</button>
            <button onclick="buyUpgrade(1000)">Bank (Cost: <span id="bankCost">10000</span>)</button>
        </div>
        <div class="stats">
            <p>Total Clicks: <span id="totalClicks">0</span></p>
            <p>Total Cookies Earned: <span id="totalCookies">0</span></p>
        </div>
    </div>

    <script>
        let cookies = 0;
        let cps = 0;
        let cursorCost = 10;
        let grandmaCost = 100;
        let factoryCost = 500;
        let mineCost = 2000;
        let bankCost = 10000;
        let totalClicks = 0;
        let totalCookies = 0;

        function addCookie() {
            cookies++;
            totalCookies++;
            totalClicks++;
            updateDisplay();
        }

        function buyUpgrade(type) {
            if (type === 1 && cookies >= cursorCost) {
                cookies -= cursorCost;
                cps += 1;
                cursorCost = Math.floor(cursorCost * 1.2);
                document.getElementById('cursorCost').textContent = cursorCost;
            } else if (type === 10 && cookies >= grandmaCost) {
                cookies -= grandmaCost;
                cps += 10;
                grandmaCost = Math.floor(grandmaCost * 1.3);
                document.getElementById('grandmaCost').textContent = grandmaCost;
            } else if (type === 50 && cookies >= factoryCost) {
                cookies -= factoryCost;
                cps += 50;
                factoryCost = Math.floor(factoryCost * 1.5);
                document.getElementById('factoryCost').textContent = factoryCost;
            } else if (type === 200 && cookies >= mineCost) {
                cookies -= mineCost;
                cps += 200;
                mineCost = Math.floor(mineCost * 1.7);
                document.getElementById('mineCost').textContent = mineCost;
            } else if (type === 1000 && cookies >= bankCost) {
                cookies -= bankCost;
                cps += 1000;
                bankCost = Math.floor(bankCost * 2);
                document.getElementById('bankCost').textContent = bankCost;
            }
            updateDisplay();
        }

        function updateDisplay() {
            document.getElementById('cookieCount').textContent = cookies;
            document.getElementById('cpsCount').textContent = cps;
            document.getElementById('totalClicks').textContent = totalClicks;
            document.getElementById('totalCookies').textContent = totalCookies;
        }

        setInterval(() => {
            cookies += cps;
            totalCookies += cps;
            updateDisplay();
        }, 1000);
    </script>
</body>
</html>
