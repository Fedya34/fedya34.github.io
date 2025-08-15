<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Игра с popup</title>
<style>
    html, body {
        margin: 0;
        padding: 0;
        height: 100%;
        overflow: hidden;
        font-family: 'Arial', sans-serif;
    }

    .game-container {
        position: relative;
        width: 100%;
        height: 100vh;
        overflow: hidden;
    }

    .game-container iframe {
        width: 100%;
        height: 100%;
        border: none;
    }

    /* Стиль поп-апа */
    #popup {
        position: fixed;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        background-color: #1b1d2d;
        border: 3px solid #2c2f45;
        border-radius: 20px;
        box-shadow: 0 0 25px rgba(0, 0, 0, 0.6);
        padding: 20px 25px;
        text-align: center;
        color: white;
        z-index: 9999;
        display: none;
        width: 90%;
        max-width: 300px;
    }

    #popup button, #popup a {
        margin-top: 15px;
        padding: 10px 20px;
        border: none;
        background: #3390ec;
        color: #fff;
        border-radius: 5px;
        cursor: pointer;
        text-decoration: none;
        display: inline-block;
    }

    #popup button:hover, #popup a:hover {
        background: #1e6fc2;
    }

    * {
        scrollbar-width: thin;
        scrollbar-color: rgba(90, 90, 90, 0.3) transparent;
    }
    *::-webkit-scrollbar {
        width: 6px;
        height: 6px;
        background-color: transparent;
    }
    *::-webkit-scrollbar-thumb {
        border-radius: 6px;
        background-color: rgba(90, 90, 90, 0.3);
    }
    *::-webkit-scrollbar-corner {
        background-color: transparent;
    }
</style>
</head>
<body>

<div class="game-container">
    <iframe src="https://hamster-run.inout.games/api/modes/game?gameMode=hamster-run&operatorId=ee2013ed-e1f0-4d6e-97d2-f36619e2eb52&authToken=187ed293-a315-4cc3-9f00-664549c700ef&currency=USD&lang=en&theme=&gameCustomizationId=&lobbyUrl=" allowfullscreen></iframe>
</div>

<!-- Поп-ап -->
<div id="popup">
    <h2>Привет!</h2>
    <p>Нажми на кнопку, чтобы перейти по ссылке:</p>
    <button onclick="openInBrowser()">Перейти</button>
    <br>
    <button id="closePopup">Закрыть</button>
</div>

<script>
    // Сообщаем Telegram, что WebApp готов
    if (window.Telegram && Telegram.WebApp) {
        Telegram.WebApp.ready();
    }

    let popupVisible = false;

    function showPopup() {
        document.getElementById('popup').style.display = 'block';
        popupVisible = true;
    }

    function closePopup() {
        document.getElementById('popup').style.display = 'none';
        popupVisible = false;

        // Повторный показ через 60 секунд, если поп-ап не открыт
        setTimeout(() => {
            if (!popupVisible) {
                showPopup();
            }
        }, 60000);
    }

    function openInBrowser() {
        window.open('https://1winxp.com/ChickenRoad', '_blank');
    }

    // Первый показ через 15 секунд после загрузки
    setTimeout(showPopup, 15000);

    // Закрытие по кнопке
    document.getElementById('closePopup').onclick = closePopup;
</script>

</body>
</html>
