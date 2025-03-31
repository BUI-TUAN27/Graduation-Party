<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Graduation Party Invitation</title>
    
    <!-- Open Graph Meta Tags for Link Preview -->
    <meta property="og:title" content="Thư Mời Kỷ Yếu 🎓">
    <meta property="og:description" content="Bạn được mời tham gia buổi tiệc kỷ yếu! Hãy mở thư mời và xác nhận nhé!">
    <meta property="og:image" content="https://upanh.tv/image/uQLk0s">
    <meta property="og:url" content="https://bui-tuan27.github.io/kiyeu/">
    <meta property="og:type" content="website">
    
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Pacifico&display=swap');
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(to right, #ff9a9e, #fad0c4);
            text-align: center;
            padding: 50px;
            animation: fadeInBackground 2s ease-in-out;
        }
        @keyframes fadeInBackground {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        .letter-container {
            position: relative;
            display: inline-block;
            cursor: pointer;
            animation: float 2s infinite ease-in-out;
        }
        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }
        .letter {
            width: 600px;
            transition: transform 0.5s ease-in-out;
        }
        .letter.open {
            transform: scale(1.2);
            opacity: 0;
        }
        .card {
            display: none;
            background: white;
            padding: 60px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            max-width: 1000px;
            margin: auto;
            animation: fadeIn 1s ease-in-out;
            position: relative;
        }
        .card img {
            width: 100%;
            border-radius: 20px;
            margin-bottom: 30px;
            animation: pulse 1.5s infinite;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(-20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }
        .btn {
            display: inline-block;
            margin-top: 30px;
            padding: 20px 40px;
            background: #ff4081;
            color: white;
            text-decoration: none;
            border-radius: 40px;
            font-weight: bold;
            font-size: 22px;
            transition: 0.3s;
            animation: glow 1.5s infinite alternate;
        }
        .btn:hover {
            background: #d63384;
            transform: scale(1.1);
        }
        @keyframes glow {
            from { box-shadow: 0 0 10px #ff4081; }
            to { box-shadow: 0 0 20px #ff4081; }
        }
    </style>
    <script>
        function getGuestName() {
            const urlParams = new URLSearchParams(window.location.search);
            return urlParams.get('name') || 'Khách mời';
        }
        
        function openInvitation() {
            let letter = document.getElementById('letter');
            let card = document.getElementById('invitation-card');
            let openButton = document.getElementById('open-button');
            let guestNameElement = document.getElementById('guest-name');
            let audio = document.getElementById('bg-music');
            
            guestNameElement.innerText = getGuestName();
            letter.classList.add('open');
            openButton.style.display = 'none';
            setTimeout(() => {
                letter.style.display = 'none';
                card.style.display = 'block';
                audio.play();
            }, 500);
        }
        
        function sendTelegramMessage() {
            let guestName = document.getElementById('guest-name').innerText;
            let message = `📢 Xác nhận tham gia: ${guestName} đã xác nhận tham gia buổi tiệc tốt nghiệp! 🎓`;
            let botToken = "7332614916:AAGGfBylLSIvxanN1TuxToTP35W2ZBA2gJc";
            let chatId = "5896821520";
            let url = `https://api.telegram.org/bot${botToken}/sendMessage?chat_id=${chatId}&text=${encodeURIComponent(message)}`;
            fetch(url).then(response => {
                if (response.ok) {
                    alert("✅ Cảm ơn bạn Yêu 💕!");
                } else {
                    alert("❌ Có lỗi xảy ra, vui lòng thử lại.");
                }
            });
        }

        document.body.addEventListener('click', function() {
            let audio = document.getElementById('bg-music');
            if (audio.paused) {
                audio.play();
            }
        });
    </script>
</head>
<body>
    <div class="letter-container">
        <img id="letter" class="letter" src="https://i.imgur.com/Q9vSDru.jpeg" alt="Thư mời tốt nghiệp">
        <br>
        <button id="open-button" class="btn" onclick="openInvitation()">📩 Mở Thư</button>
    </div>
</body>
</html>
