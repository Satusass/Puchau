<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Invitación</title>
    <style>
        body {
            text-align: center;
            font-family: Arial, sans-serif;
            background-color: #ffe6e6;
            margin-top: 50px;
        }
        .container {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
            display: inline-block;
            max-width: 90%;
        }
        button {
            margin: 10px;
            padding: 15px 25px;
            font-size: 18px;
            border: none;
            cursor: pointer;
            border-radius: 5px;
        }
        .yes {
            background-color: #ff4d4d;
            color: white;
        }
        .no {
            background-color: #4d79ff;
            color: white;
        }
        .hidden {
            display: none;
        }
        .balloons {
            position: fixed;
            top: 100%;
            left: 50%;
            transform: translateX(-50%);
            font-size: 50px;
            opacity: 0;
            animation: floatUp 3s ease-out forwards;
        }
        @keyframes floatUp {
            0% { top: 100%; opacity: 1; }
            100% { top: -10%; opacity: 0; }
        }
    </style>
</head>
<body>

    <div class="container">
        <h2>Te invito a cenar mañana conmigo luego de una ardua tarde de estudio.</h2>
        <button class="yes" id="yesBtn">Sí</button>
        <button class="no" id="noBtn">No</button>
        <p id="forceText" class="hidden">Pues ni modo, tienes que aceptar 😜</p>
    </div>

    <script>
        document.getElementById("yesBtn").addEventListener("click", showLove);
        document.getElementById("yesBtn").addEventListener("touchend", showLove);
        document.getElementById("noBtn").addEventListener("click", forceYes);
        document.getElementById("noBtn").addEventListener("touchend", forceYes);

        function forceYes() {
            document.getElementById('noBtn').style.display = "none";
            document.getElementById('forceText').classList.remove('hidden');
        }

        function showLove() {
            alert("Gracias por aceptar, te amo ❤️");
            createBalloons();
        }

        function createBalloons() {
            for (let i = 0; i < 10; i++) {
                let balloon = document.createElement("div");
                balloon.classList.add("balloons");
                balloon.innerHTML = "🎈";
                balloon.style.left = Math.random() * 100 + "vw";
                balloon.style.animationDuration = (Math.random() * 2 + 2) + "s";
                document.body.appendChild(balloon);
                setTimeout(() => { balloon.remove(); }, 3000);
            }
        }
    </script>

</body>
</html>
