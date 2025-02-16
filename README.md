<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ramadhan Countdown</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r121/three.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/vanta@latest/dist/vanta.birds.min.js"></script>
    <script>
      window.addEventListener("DOMContentLoaded", ()=>{
        VANTA.BIRDS({
          el: "#vanta",
          mouseControls: true,
          touchControls: true,
          gyroControls: false,
          minHeight: 200.00,
          minWidth: 200.00,
          scale: 1.00,
          scaleMobile: 1.00,
          wingSpan: 40.00,
          speedLimit: 8.00,
          separation: 100.00,
          alignment: 43.00,
          quantity: 4.00,
          backgroundAlpha:0.0,
        })
        setTimeout(()=>{
        document.querySelector('main').style.opacity='1';
        document.querySelector('main').style.filter='none';
        },1000)
      })
    </script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Amiri:wght@700&family=Poppins:wght@400;600&display=swap');

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            background: url('bg.png');
            font-family: 'Poppins', sans-serif;
            object-fit: cover;
            background-repeat: no-repeat;
            background-size: cover;
        }
        #vanta{
  z-index: 0;
  position: absolute;
  left: 0;
  right: 0;
  width: 100%;
  height: 100vh;     
}
#dev{
  position: absolute;
  left: 0;
  bottom: 0;
  color: darkgrey;
z-index: 10;
}
#dev a{
  color: aqua;
}
       

        .container {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 2rem;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
            border: 1px solid rgba(255, 255, 255, 0.2);
            text-align: center;
            position: relative;
            z-index: 1;
            max-width: 90%;
            width: 600px;
        }

        .title {
            color: #fff;
            font-size: 2.5rem;
            margin-bottom: 2rem;
            text-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
            position: relative;
        }

        .title::after {
            content: 'رمضان';
            font-family: 'Amiri', serif;
            position: absolute;
            top: -20px;
            right: -20px;
            font-size: 1.5rem;
            opacity: 0.5;
            color: gold;
        }

        .countdown {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 1rem;
            margin-bottom: 2rem;
        }

        .countdown-item {
            background: rgba(255, 255, 255, 0.15);
            padding: 1rem;
            border-radius: 10px;
            color: #fff;
            position: relative;
            overflow: hidden;
        }

        .countdown-item::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(45deg, transparent, rgba(255, 255, 255, 0.1), transparent);
            transform: translateX(-100%);
            animation: shine 3s infinite;
        }

        .number {
            font-size: 3rem;
            font-weight: 600;
            margin-bottom: 0.5rem;
            text-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
        }

        .label {
            font-size: 0.9rem;
            opacity: 0.8;
        }

        .message {
            color: #fff;
            font-size: 1.1rem;
            margin-top: 1rem;
            position: relative;
        }

        .moon {
            position: absolute;
            top: -50px;
            right: -50px;
            width: 100px;
            height: 100px;
            background: radial-gradient(circle at 30% 30%, #ffd700, transparent);
            opacity: 0.2;
            border-radius: 50%;
            animation: glow 2s ease-in-out infinite;
        }

        @keyframes shine {
            0% { transform: translateX(-100%); }
            100% { transform: translateX(100%); }
        }

        @keyframes glow {
            0%, 100% { opacity: 0.2; }
            50% { opacity: 0.4; }
        }

  

        @media (max-width: 600px) {
            .countdown {
                grid-template-columns: repeat(2, 1fr);
            }
            
            .title {
                font-size: 2rem;
            }

            .number {
                font-size: 2.5rem;
            }
        }
    </style>
</head>
<body>
  <span id="dev">developed by <a href="https://multiai.id/creations/ramadhan-countdown-3d" target="_blank" rel="noopener noreferrer">irfan</a></span>
  <div id="vanta"></div>
    <div class="container">
        <div class="moon"></div>
        <h1 class="title">Ramadan Countdown</h1>
        <div class="countdown">
            <div class="countdown-item">
                <div class="number" id="days">00</div>
                <div class="label">Days</div>
            </div>
            <div class="countdown-item">
                <div class="number" id="hours">00</div>
                <div class="label">Hours</div>
            </div>
            <div class="countdown-item">
                <div class="number" id="minutes">00</div>
                <div class="label">Minutes</div>
            </div>
            <div class="countdown-item">
                <div class="number" id="seconds">00</div>
                <div class="label">Seconds</div>
            </div>
        </div>
        <div class="message">
            Ramadan akan tiba, insyaAllah 28 Februari 2025 🌙 ✨
        </div>
    </div>

    <script>
        function updateCountdown() {
            const ramadanDate = new Date('February 28, 2025 00:00:00').getTime();
            const now = new Date().getTime();
            const distance = ramadanDate - now;

            const days = Math.floor(distance / (1000 * 60 * 60 * 24));
            const hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
            const seconds = Math.floor((distance % (1000 * 60)) / 1000);

            document.getElementById('days').textContent = String(days).padStart(2, '0');
            document.getElementById('hours').textContent = String(hours).padStart(2, '0');
            document.getElementById('minutes').textContent = String(minutes).padStart(2, '0');
            document.getElementById('seconds').textContent = String(seconds).padStart(2, '0');

            if (distance < 0) {
                clearInterval(countdownInterval);
                document.querySelector('.message').textContent = 'Ramadan Mubarak! 🌙';
            }
        }

        const countdownInterval = setInterval(updateCountdown, 1000);
        updateCountdown();
    </script>
</body>
</html>
