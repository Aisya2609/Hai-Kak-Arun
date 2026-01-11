<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kado Spesial untuk Kak Arun!</title>
    <style>
        body {
            background-color: #fce4ec; /* Pink sangat muda */
            font-family: 'Comic Sans MS', cursive, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            overflow: hidden;
            color: #d63384;
            position: relative;
        }

        .container {
            text-align: center;
            background: rgba(255, 255, 255, 0.95);
            padding: 30px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(255, 105, 180, 0.3);
            max-width: 85%;
            border: 2px dashed #ffb6c1;
            z-index: 10;
        }

        /* --- KADO --- */
        .gift-box-wrapper {
            position: relative;
            width: 200px;
            height: 200px;
            margin: 40px auto;
            cursor: pointer;
            perspective: 1000px;
            transition: transform 0.5s;
            animation: shake 2s infinite; /* Efek goyang */
            z-index: 15;
        }

        .gift-box-wrapper.open {
            animation: none; /* Hentikan goyang saat terbuka */
            transform: scale(1.1);
        }

        .gift-lid {
            background-color: #ff69b4; /* Pink cerah */
            width: 220px;
            height: 50px;
            position: absolute;
            top: -20px;
            left: -10px;
            border-radius: 10px;
            z-index: 2;
            transition: top 0.5s ease-out, transform 0.5s ease-out;
            box-shadow: 0 5px 10px rgba(0,0,0,0.2);
        }

        .gift-box-wrapper.open .gift-lid {
            top: -100px; /* Tutup terangkat jauh */
            transform: rotateX(20deg) scale(0.8);
        }

        .gift-base {
            background-color: #ffb6c1; /* Pink muda */
            width: 200px;
            height: 150px;
            position: absolute;
            bottom: 0;
            left: 0;
            border-radius: 10px;
            z-index: 1;
            box-shadow: inset 0 -5px 10px rgba(0,0,0,0.1);
        }

        .ribbon-vertical {
            background-color: #ffcc00; /* Kuning emas */
            width: 30px;
            height: 200px;
            position: absolute;
            left: 50%;
            transform: translateX(-50%);
            z-index: 3;
        }

        .ribbon-horizontal {
            background-color: #ffcc00; /* Kuning emas */
            width: 220px;
            height: 30px;
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            left: -10px;
            z-index: 3;
        }

        .ribbon-bow {
            background-color: #ffcc00; /* Kuning emas */
            width: 50px;
            height: 50px;
            border-radius: 50%;
            position: absolute;
            top: -40px;
            left: 50%;
            transform: translateX(-50%);
            z-index: 4;
            box-shadow: 0 3px 5px rgba(0,0,0,0.2);
        }

        /* --- END KADO --- */

        .btn-universal {
            background: linear-gradient(45deg, #ff85a2, #ffb6c1);
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 25px;
            cursor: pointer;
            font-size: 1rem;
            margin: 10px;
            transition: 0.3s;
        }
        .btn-universal:hover {
            background: linear-gradient(45deg, #ffb6c1, #ff85a2);
            transform: scale(1.05);
        }

        .heart {
            position: absolute;
            pointer-events: none;
            animation: fly 3s linear forwards;
            font-size: 24px;
            z-index: 1;
        }

        @keyframes fly {
            0% { transform: translateY(0) scale(1); opacity: 1; }
            100% { transform: translateY(-600px) rotate(360deg) scale(0); opacity: 0; }
        }

        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            10%, 30%, 50%, 70%, 90% { transform: translateX(-5px); }
            20%, 40%, 60%, 80% { transform: translateX(5px); }
        }

        .hidden { display: none; }
        .typing { font-weight: bold; line-height: 1.5; }
        
        .nama-ayu {
            color: #b8860b; /* Gold */
            font-size: 1.1rem;
            display: block;
            margin-top: 10px;
        }
    </style>
</head>
<body onclick="spawnHearts(event)">

    <div id="slide0" class="container">
        <h1>Halo Kakak Arun... ✨</h1>
        <p>Adik imut punya kado spesial buat Kakak!</p>
        <div class="gift-box-wrapper" onclick="openGift()">
            <div class="gift-lid"></div>
            <div class="ribbon-vertical"></div>
            <div class="ribbon-horizontal"></div>
            <div class="ribbon-bow"></div>
            <div class="gift-base"></div>
        </div>
        <p>Tekan kadonya ya!</p>
    </div>

    <div id="slide1" class="container hidden">
        <p id="text1" class="typing"></p>
        <div id="btn-next-1" class="hidden">
            <button class="btn-universal" onclick="nextSlide(2)">Oke, Adik Imut! 👋</button>
        </div>
    </div>

    <div id="slide2" class="container hidden">
        <h2>Bagaimana perasaan Kakak hari ini?</h2>
        <button class="btn-universal" onclick="nextSlide(3)">😊 Senang Banget</button>
        <button class="btn-universal" onclick="nextSlide(3)">🥺 Lagi Sedih</button>
        <button class="btn-universal" onclick="nextSlide(3)">💪 Full Semangat!</button>
    </div>

    <div id="slide3" class="container hidden">
        <p id="text3" class="typing"></p>
        <b class="nama-ayu">Ni Gusti Cokro Sri Ayu Nurazahra 🌸</b>
        <br>
        <button class="btn-universal" onclick="nextSlide(4)">Buka Pesan Spesial! 🎁</button>
    </div>

    <div id="slide4" class="container hidden">
        <h2>Pesan Semangat untuk Kak Arun Besok!</h2>
        <p style="font-size: 1.2rem; line-height: 1.6; color: #ff69b4;">
            "Hai Kakak Arun, apapun yang terjadi hari ini,
            ingat ya, besok adalah lembaran baru.
            Adik imut selalu ada buat Kakak.
            <br>
            <br>
            **Semangat ya untuk besok\!**
            Senyum terus, karena senyum Kakak itu indah! 🥰
            <br>
            <br>
            Salam sayang dari adik imutmu:
            <b class="nama-ayu" style="font-size: 1.3rem;">Ni Gusti Cokro Sri Ayu Nurazahra</b>"
        </p>
        <button class="btn-universal" onclick="location.reload()">Ulangi Kadonya 🤗</button>
    </div>

    <script>
        function spawnHearts(e) {
            for(let i=0; i<3; i++) {
                const heart = document.createElement('div');
                heart.classList.add('heart');
                heart.innerHTML = ['❤️', '💖', '✨', '🌸', '🌟'][Math.floor(Math.random() * 5)];
                heart.style.left = (e ? e.clientX : Math.random() * window.innerWidth) + (Math.random() * 40 - 20) + 'px';
                heart.style.top = (e ? e.clientY : window.innerHeight) + 'px';
                document.body.appendChild(heart);
                setTimeout(() => heart.remove(), 3000);
            }
        }

        function typeWriter(text, elementId, speed, callback) {
            let i = 0;
            let elem = document.getElementById(elementId);
            elem.innerHTML = "";
            function type() {
                if (i < text.length) {
                    elem.innerHTML += text.charAt(i);
                    i++;
                    setTimeout(type, speed);
                } else if (callback) {
                    callback();
                }
            }
            type();
        }

        function openGift() {
            document.querySelector('.gift-box-wrapper').classList.add('open');
            // Ledakan lope-lope saat kado dibuka
            for(let i=0; i<20; i++) setTimeout(spawnHearts, i * 80);
            setTimeout(() => {
                nextSlide(1);
                typeWriter("Hai Kakak Arun, Selamat Malam... Gimana hari ini? Adik imut kangen tau! 😊", "text1", 80, () => {
                    document.getElementById('btn-next-1').classList.remove('hidden');
                });
            }, 1000); // Tunda sebentar biar animasi kado selesai
        }

        function nextSlide(n) {
            document.querySelectorAll('.container').forEach(el => el.classList.add('hidden'));
            document.getElementById('slide' + n).classList.remove('hidden');
            if (n === 3) {
                typeWriter("Apapun yang Kakak rasain, Kakak hebat banget hari ini! Jangan lupa istirahat ya, Kakak Arun sayang. Semangat terus! ✨", "text3", 60);
            }
            if (n === 4) {
                 // Hujan hati terus menerus di slide terakhir
                setInterval(spawnHearts, 400);
            }
        }

        // Mulai tampilan awal
        window.onload = () => {
            document.getElementById('slide0').classList.remove('hidden');
        };
    </script>
</body>
</html>
