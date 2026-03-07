
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday Hizdi!</title>
    <style>
        :root {
            --pink-bg: #FFC0CB;
            --cream: #FFFDD0;
            --dark-cream: #F5F5DC;
            --hot-pink: #d81b60;
        }

        body {
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: var(--pink-bg);
            font-family: 'Arial', sans-serif;
            overflow: hidden;
        }

        .main-container {
            width: 320px;
            height: 220px;
            perspective: 1200px;
        }

        .card-inner {
            position: relative;
            width: 100%;
            height: 100%;
            transition: transform 1.2s cubic-bezier(0.645, 0.045, 0.355, 1);
            transform-style: preserve-3d;
        }

        .is-flipped {
            transform: rotateY(180deg);
        }

        .front, .back {
            position: absolute;
            width: 100%;
            height: 100%;
            backface-visibility: hidden;
            border-radius: 15px;
            box-shadow: 0 15px 35px rgba(0,0,0,0.2);
        }

        /* FRONT: ENVELOPE */
        .envelope-wrapper {
            position: relative;
            width: 100%;
            height: 100%;
            cursor: pointer;
        }

        .envelope {
            position: absolute;
            bottom: 0;
            width: 100%;
            height: 100%;
            background-color: var(--cream);
            border-radius: 0 0 10px 10px;
            z-index: 2;
        }

        .envelope::before {
            content: "";
            position: absolute;
            top: 0;
            z-index: 4;
            border-top: 110px solid var(--dark-cream);
            border-left: 160px solid transparent;
            border-right: 160px solid transparent;
            transform-origin: top;
            transition: transform 0.6s ease;
        }

        .letter {
            position: absolute;
            bottom: 10px;
            left: 10%;
            width: 80%;
            height: 180px;
            background-color: white;
            padding: 15px;
            box-sizing: border-box;
            text-align: center;
            display: flex;
            justify-content: center;
            align-items: center;
            transition: transform 0.8s ease;
            z-index: 1;
        }

        .letter h1 {
            color: var(--hot-pink);
            font-size: 22px;
            font-weight: 900;
            margin: 0;
        }

        .open .letter { transform: translateY(-140px); z-index: 3; }
        .open .envelope::before { transform: rotateX(180deg); z-index: 0; }

        /* BACK: VIDEO PLAYER */
        .back {
            background-color: #000;
            transform: rotateY(180deg);
            overflow: hidden;
        }

        video {
            width: 100%;
            height: 100%;
            object-fit: contain;
        }

        /* REPLAY BUTTON */
        #replayBtn {
            display: none;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            z-index: 10;
            padding: 12px 24px;
            background-color: var(--hot-pink);
            color: white;
            border: none;
            border-radius: 25px;
            font-weight: bold;
            cursor: pointer;
            box-shadow: 0 4px 15px rgba(0,0,0,0.3);
        }

        .instruction {
            margin-top: 80px;
            color: var(--hot-pink);
            font-weight: bold;
        }
    </style>
</head>
<body>

    <div class="main-container">
        <div class="card-inner" id="card">
            
            <div class="front">
                <div class="envelope-wrapper" id="env" onclick="openSurprise()">
                    <div class="letter">
                        <h1><b>HAPPY <br> BIRTHDAY HIZDI 🖕🖕🥳🥳</b></h1>
                    </div>
                    <div class="envelope"></div>
                </div>
            </div>

            <div class="back">
                <button id="replayBtn" onclick="restartVideo()">WATCH AGAIN</button>
                <video id="bdayVideo" playsinline>
                    <source src="IMG_6748.MOV" type="video/quicktime">
                    <source src="IMG_6748.MOV" type="video/mp4">
                </video>
            </div>

        </div>
    </div>

    <div class="instruction" id="hint">Tap the Envelope!</div>

    <script>
        const card = document.getElementById('card');
        const video = document.getElementById('bdayVideo');
        const env = document.getElementById('env');
        const hint = document.getElementById('hint');
        const replayBtn = document.getElementById('replayBtn');

        function openSurprise() {
            env.classList.add('open');
            hint.style.opacity = '0';
            
            setTimeout(() => {
                card.classList.add('is-flipped');
                video.play();
            }, 1500);
        }

        // Show Replay button when video ends
        video.onended = function() {
            replayBtn.style.display = 'block';
        };

        function restartVideo() {
            replayBtn.style.display = 'none';
            video.currentTime = 0;
            video.play();
        }
    </script>
    suny aint coming back 
</body>
</html>
