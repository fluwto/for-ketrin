<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
    <title>Happy Birthday Ketrin!</title>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;600;800&family=Pacifico&family=Cormorant+Garamond:ital,wght@0,400;0,600;1,400&display=swap" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.9.2/dist/confetti.browser.min.js"></script>
    <style>
        *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

        /* ---- ANIMATIONS ---- */
        @keyframes gradientMove {
            0%   { background-position: 0% 50%; }
            50%  { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }
        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50%       { transform: translateY(-10px); }
        }
        @keyframes scaleIn {
            from { opacity: 0; transform: scale(0.9) translateY(12px); }
            to   { opacity: 1; transform: scale(1) translateY(0); }
        }
        @keyframes rise {
            0%   { transform: translateY(110vh); opacity: 0.85; }
            85%  { opacity: 0.6; }
            100% { transform: translateY(-15vh); opacity: 0; }
        }
        @keyframes noteReveal {
            from { opacity: 0; transform: translateY(18px) scale(0.97); }
            to   { opacity: 1; transform: translateY(0) scale(1); }
        }

        /* ---- BODY ---- */
        body {
            background: linear-gradient(-45deg, #ffdde1, #f5b8c4, #fbc2eb, #b8d4f5);
            background-size: 400% 400%;
            animation: gradientMove 14s ease infinite;
            font-family: 'Montserrat', sans-serif;
            color: #c2185b;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            /* FIX: iOS Safari 100vh bug — use min-height with padding instead */
            min-height: -webkit-fill-available;
            min-height: 100dvh;
            overflow-x: hidden;
            padding: 28px 0;
            /* FIX: background transition so mode swap isn't instant */
            transition: color 0.7s ease, background 0.9s ease;
        }

        /* FIX: iOS Safari fill-available needs this on html too */
        html {
            height: -webkit-fill-available;
        }

        /* ---- FLOATING EMOJIS ---- */
        #emoji-layer {
            position: fixed;
            inset: 0;
            pointer-events: none;
            z-index: 0;
            overflow: hidden;
        }
        .rising-emoji {
            position: absolute;
            bottom: -50px;
            opacity: 0.8;
            animation: rise linear forwards;
            user-select: none;
        }

        /* ---- CARD ---- */
        .container {
            background: rgba(255, 255, 255, 0.45);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            padding: 44px 38px 40px;
            border-radius: 28px;
            box-shadow: 0 8px 36px rgba(216, 27, 96, 0.14);
            border: 1px solid rgba(255,255,255,0.7);
            width: min(390px, 92vw);
            position: relative;
            z-index: 10;
            text-align: center;
            animation: scaleIn 0.65s cubic-bezier(0.34, 1.4, 0.64, 1) both;
            transition: background 0.8s ease, box-shadow 0.8s ease,
                        border-color 0.8s ease, border-radius 0.8s ease;
        }

        /* ---- PHOTO ---- */
        .img-wrapper {
            position: relative;
            display: block;
            margin: 0 auto 16px;
            /* FIX: webkit fallback for older Android WebViews */
            width: -webkit-fit-content;
            width: fit-content;
        }
        img#profile-pic {
            width: 168px;
            height: 168px;
            border-radius: 50%;
            object-fit: cover;
            border: 5px solid white;
            box-shadow: 0 8px 28px rgba(0,0,0,0.1);
            animation: float 4.5s ease-in-out infinite;
            display: block;
            transition: border-color 0.6s ease, box-shadow 0.6s ease,
                        border-radius 0.6s ease, opacity 0.28s ease;
        }

        /* ---- BADGE ---- */
        .badge {
            display: inline-block;
            font-size: 11px;
            font-weight: 700;
            letter-spacing: 2px;
            text-transform: uppercase;
            color: #c2185b;
            background: rgba(194, 24, 91, 0.08);
            padding: 4px 14px;
            border-radius: 20px;
            margin-bottom: 10px;
            transition: all 0.5s ease;
        }

        /* ---- HEADING ---- */
        h1 {
            font-family: 'Pacifico', cursive;
            font-size: 30px;
            margin: 0 0 8px;
            color: #c2185b;
            text-shadow: 1px 2px 8px rgba(255,255,255,0.55);
            transition: all 0.5s ease;
        }

        /* ---- TOGGLE ---- */
        .switch-container {
            margin: 18px 0 16px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 14px;
            font-weight: 700;
            font-size: 12px;
            text-transform: uppercase;
            letter-spacing: 1.5px;
        }
        .switch {
            position: relative;
            display: inline-block;
            width: 60px;
            height: 32px;
        }
        .switch input { opacity: 0; width: 0; height: 0; }
        .slider {
            position: absolute;
            cursor: pointer;
            inset: 0;
            background: #f48fb1;
            transition: 0.45s;
            border-radius: 32px;
        }
        .slider:before {
            position: absolute;
            content: "";
            height: 24px; width: 24px;
            left: 4px; bottom: 4px;
            background: white;
            transition: 0.45s cubic-bezier(0.34, 1.5, 0.64, 1);
            border-radius: 50%;
            box-shadow: 0 2px 5px rgba(0,0,0,0.18);
        }
        input:checked + .slider { background: #444; }
        input:checked + .slider:before { transform: translateX(28px); }

        /* ---- MESSAGE ---- */
        #message {
            font-size: 14.5px;
            line-height: 1.75;
            font-weight: 500;
            color: #6d3350;
            min-height: 50px;
            transition: opacity 0.32s ease, transform 0.32s ease, color 0.5s ease;
        }
        #message.fade-out {
            opacity: 0;
            transform: translateY(6px);
        }

        /* ---- CTA BUTTON ---- */
        .cta-button {
            display: inline-block;
            margin-top: 22px;
            padding: 13px 30px;
            background: linear-gradient(135deg, #f06292, #e91e8c);
            color: white;
            font-family: 'Montserrat', sans-serif;
            font-weight: 700;
            font-size: 13.5px;
            border-radius: 28px;
            border: 1.5px solid transparent;
            box-shadow: 0 4px 18px rgba(233, 30, 140, 0.28);
            cursor: pointer;
            -webkit-appearance: none;
            transition: transform 0.25s ease, box-shadow 0.25s ease,
                        background 0.6s ease, border-radius 0.6s ease,
                        color 0.4s ease, border-color 0.4s ease,
                        letter-spacing 0.4s ease, font-size 0.4s ease;
        }
        .cta-button:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 24px rgba(233, 30, 140, 0.38);
        }
        .cta-button:active { transform: scale(0.97); }

        /* ---- LOVE NOTE OVERLAY ---- */
        /* FIX: use opacity+visibility instead of display toggle so animation works on all browsers */
        #note-overlay {
            position: fixed;
            inset: 0;
            z-index: 100;
            background: rgba(0,0,0,0.4);
            backdrop-filter: blur(5px);
            -webkit-backdrop-filter: blur(5px);
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 20px;
            /* hidden state */
            opacity: 0;
            visibility: hidden;
            transition: opacity 0.3s ease, visibility 0.3s ease;
        }
        #note-overlay.open {
            opacity: 1;
            visibility: visible;
        }
        /* FIX: max-height + scroll so note doesn't clip on short phones */
        .note-card {
            background: #fffaf9;
            border-radius: 20px;
            padding: 38px 32px 32px;
            max-width: 355px;
            width: 100%;
            max-height: 85vh;
            overflow-y: auto;
            -webkit-overflow-scrolling: touch;
            box-shadow: 0 24px 64px rgba(0,0,0,0.18);
            text-align: left;
            position: relative;
            animation: noteReveal 0.4s cubic-bezier(0.34, 1.3, 0.64, 1) both;
        }
        .note-label {
            font-size: 10px;
            font-weight: 800;
            letter-spacing: 3px;
            text-transform: uppercase;
            color: #e91e8c;
            margin-bottom: 14px;
        }
        .note-card h2 {
            font-family: 'Cormorant Garamond', serif;
            font-size: 26px;
            font-weight: 600;
            color: #2d1a24;
            margin-bottom: 18px;
            line-height: 1.2;
        }
        .note-card .note-body {
            font-family: 'Cormorant Garamond', serif;
            font-size: 17.5px;
            line-height: 1.9;
            color: #4a2535;
            font-style: italic;
        }
        .note-card .note-body p { margin-bottom: 12px; }
        .note-card .note-body p:last-child { margin-bottom: 0; }
        .note-sign {
            margin-top: 22px;
            font-family: 'Pacifico', cursive;
            font-size: 17px;
            color: #e91e8c;
        }
        .note-close {
            position: absolute;
            top: 14px; right: 16px;
            background: none;
            border: none;
            font-size: 20px;
            color: #ccc;
            cursor: pointer;
            line-height: 1;
            transition: color 0.2s;
            padding: 4px 6px;
            -webkit-appearance: none;
        }
        .note-close:hover { color: #666; }

        /* ==============================
           BADDIE MODE
        ============================== */
        body.baddie-mode {
            background: linear-gradient(-45deg, #111, #181818, #141414, #0d0d0d);
            background-size: 400% 400%;
            animation: gradientMove 18s ease infinite;
            color: #d0d0d0;
        }
        .baddie-mode .container {
            background: rgba(16, 16, 16, 0.78);
            border-color: rgba(255,255,255,0.06);
            box-shadow: 0 8px 40px rgba(0,0,0,0.55);
            border-radius: 18px;
        }
        .baddie-mode img#profile-pic {
            border-color: #222;
            border-radius: 14px;
            box-shadow: 0 8px 30px rgba(0,0,0,0.55);
        }
        .baddie-mode .badge {
            background: rgba(255,255,255,0.05);
            color: #555;
            letter-spacing: 3.5px;
        }
        .baddie-mode h1 {
            font-family: 'Cormorant Garamond', serif;
            font-size: 34px;
            font-weight: 600;
            letter-spacing: 4px;
            color: #ebebeb;
            text-shadow: none;
        }
        .baddie-mode #message { color: #777; }
        .baddie-mode .cta-button {
            background: transparent;
            border-color: rgba(255,255,255,0.2);
            color: #aaa;
            box-shadow: none;
            border-radius: 5px;
            letter-spacing: 3px;
            font-size: 10.5px;
            text-transform: uppercase;
        }
        .baddie-mode .cta-button:hover {
            border-color: rgba(255,255,255,0.55);
            color: #eee;
            transform: translateY(-2px);
            box-shadow: none;
        }

        /* Baddie note card */
        .baddie-mode .note-card {
            background: #0f0f0f;
            border: 1px solid rgba(255,255,255,0.07);
        }
        .baddie-mode .note-label  { color: #555; letter-spacing: 4px; }
        .baddie-mode .note-card h2 { color: #e5e5e5; }
        .baddie-mode .note-card .note-body { color: #888; }
        .baddie-mode .note-sign   { color: #aaa; font-family: 'Montserrat', sans-serif; font-size: 14px; font-weight: 600; }
        .baddie-mode .note-close  { color: #333; }
        .baddie-mode .note-close:hover { color: #888; }
    </style>
</head>
<body>

    <div id="emoji-layer"></div>

    <div class="container">
        <div class="img-wrapper">
            <img id="profile-pic"
                 src="https://github.com/rezawahyuramadhani01-droid/ketrin-birthday/raw/main/cutie-photo.jpg"
                 alt="Ketrin">
        </div>

        <div class="badge" id="badge">🎂 It's Your Day</div>
        <h1 id="greeting">Happy Birthday, Ketrin!</h1>

        <div class="switch-container">
            <span>Cutie</span>
            <label class="switch">
                <input type="checkbox" id="mode-toggle">
                <span class="slider"></span>
            </label>
            <span>Baddie</span>
        </div>

        <p id="message">To the girl who makes every day brighter — even from far away. Hope your birthday feels as special as you are. ✨</p>

        <button class="cta-button" id="cta-btn">A Letter For You 💌</button>
    </div>

    <!-- LOVE NOTE -->
    <div id="note-overlay" role="dialog" aria-modal="true" aria-label="Birthday letter">
        <div class="note-card">
            <button class="note-close" id="note-close-btn" aria-label="Close">✕</button>
            <div class="note-label"  id="note-label">A note from Reza</div>
            <h2 id="note-title">For you, on your birthday.</h2>
            <div class="note-body"  id="note-body"></div>
            <div class="note-sign"  id="note-sign">— Reza 🤍</div>
        </div>
    </div>

    <!-- Preload both images to eliminate swap flicker -->
    <img src="https://github.com/rezawahyuramadhani01-droid/ketrin-birthday/raw/main/baddie-photo.jpg" style="display:none" aria-hidden="true">
    <img src="https://github.com/rezawahyuramadhani01-droid/ketrin-birthday/raw/main/cutie-photo.jpg"  style="display:none" aria-hidden="true">

    <audio id="audio-cutie"  src="https://github.com/rezawahyuramadhani01-droid/ketrin-birthday/raw/refs/heads/main/Cutie-song.mp3"  loop preload="auto"></audio>
    <!-- FIX: baddie audio preloads only when first needed, saves data -->
    <audio id="audio-baddie" src="https://github.com/rezawahyuramadhani01-droid/ketrin-birthday/raw/refs/heads/main/Baddie-song.mp3" loop preload="none"></audio>

<script>
/* ---- ELEMENTS ---- */
// FIX: renamed from 'body' to '$body' to avoid shadowing document.body global
const $body       = document.body;
const toggle      = document.getElementById('mode-toggle');
const greeting    = document.getElementById('greeting');
const msgEl       = document.getElementById('message');
const profilePic  = document.getElementById('profile-pic');
const badge       = document.getElementById('badge');
const ctaBtn      = document.getElementById('cta-btn');
const audioCutie  = document.getElementById('audio-cutie');
const audioBaddie = document.getElementById('audio-baddie');
const emojiLayer  = document.getElementById('emoji-layer');
const noteOverlay = document.getElementById('note-overlay');

/* ---- LOVE NOTE CONTENT ---- */
const notes = {
    cutie: {
        label: 'A note from Reza 💌',
        title: 'For you, on your birthday.',
        body: [
            'I wish I could be there with you today — to see your smile in person, to hold your hand, to celebrate you the way you truly deserve.',
            'But even from this distance, I want you to feel how much you mean to me. Every day feels a little warmer just knowing you\'re in my life.',
            'Happy birthday, Ketrin. I hope today gives you even a fraction of the happiness you give me.'
        ],
        sign: '— Reza 🤍'
    },
    baddie: {
        label: 'From Reza',
        title: 'Real talk.',
        body: [
            'The distance is hard. Some days I really hate it.',
            'But then I think about you — how certain I feel, how much you\'re worth every bit of it — and I\'d do it all over again.',
            'You don\'t need me there for today to be great. You carry the whole room just by being you. Happy birthday. Miss you more than I say.'
        ],
        sign: '— Reza'
    }
};

/* ---- LOVE NOTE OPEN / CLOSE ---- */
let noteIsOpen = false;

function openNote() {
    // FIX: guard against re-opening while already open
    if (noteIsOpen) return;
    noteIsOpen = true;

    const mode = $body.classList.contains('baddie-mode') ? 'baddie' : 'cutie';
    const n = notes[mode];
    document.getElementById('note-label').textContent = n.label;
    document.getElementById('note-title').textContent = n.title;
    const bodyEl = document.getElementById('note-body');
    bodyEl.innerHTML = n.body.map(p => `<p>${p}</p>`).join('');
    document.getElementById('note-sign').textContent = n.sign;
    noteOverlay.classList.add('open');
}

function closeNote() {
    noteIsOpen = false;
    noteOverlay.classList.remove('open');
}

ctaBtn.addEventListener('click', openNote);
document.getElementById('note-close-btn').addEventListener('click', closeNote);
noteOverlay.addEventListener('click', e => { if (e.target === noteOverlay) closeNote(); });
document.addEventListener('keydown', e => { if (e.key === 'Escape') closeNote(); });

/* ---- FLOATING EMOJIS (cutie only) ---- */
const cutieEmojis = ['🎂','🎀','💕','✨','🌸','🎁','💖','🌷','🥳','🦋'];
let emojiInterval;

function spawnEmoji() {
    const el = document.createElement('span');
    el.className = 'rising-emoji';
    el.textContent = cutieEmojis[Math.floor(Math.random() * cutieEmojis.length)];
    // FIX: capped at 88vw to prevent right-edge clipping
    el.style.left = (Math.random() * 88) + 'vw';
    const dur = 7 + Math.random() * 5;
    el.style.animation = `rise ${dur}s linear forwards`;
    el.style.fontSize = (13 + Math.random() * 11) + 'px';
    emojiLayer.appendChild(el);
    setTimeout(() => el.remove(), dur * 1000);
}
function startEmojis() { clearInterval(emojiInterval); emojiInterval = setInterval(spawnEmoji, 1200); }
function stopEmojis()  { clearInterval(emojiInterval); emojiLayer.innerHTML = ''; }
startEmojis();

/* ---- CONFETTI ---- */
function fireCutieConfetti() {
    const colors = ['#ff9a9e','#fbc2eb','#ffdde1','#f48fb1','#ffffff','#ffb3c1'];
    confetti({ particleCount: 90, spread: 72, origin: { y: 0.55 }, colors, scalar: 1.05 });
    setTimeout(() => confetti({ particleCount: 45, spread: 44, origin: { x: 0.08, y: 0.6 }, colors }), 350);
    setTimeout(() => confetti({ particleCount: 45, spread: 44, origin: { x: 0.92, y: 0.6 }, colors }), 580);
}

/* ---- AUDIO ---- */
let audioUnlocked = false;
let pendingAudio  = audioCutie;

function playAudio(el) {
    pendingAudio = el;
    if (audioUnlocked) el.play().catch(() => {});
}

// FIX: use 'click' for iOS compatibility (touchstart + passive:true blocks synchronous play)
// Both listeners are passive:true for performance consistency
['click', 'touchstart'].forEach(evt => {
    document.addEventListener(evt, function unlock() {
        if (audioUnlocked) return;
        audioUnlocked = true;
        if (pendingAudio) pendingAudio.play().catch(() => {});
        document.removeEventListener('click',      unlock);
        document.removeEventListener('touchstart', unlock);
    }, { passive: true });
});

/* ---- IMAGE SWAP ---- */
function swapImage(src) {
    profilePic.style.opacity = '0';
    setTimeout(() => {
        profilePic.src = src;
        profilePic.onload = () => { profilePic.style.opacity = '1'; };
        // fallback if image is already cached
        setTimeout(() => { profilePic.style.opacity = '1'; }, 350);
    }, 250);
}

/* ---- MESSAGE FADE ---- */
function fadeMessage(text) {
    msgEl.classList.add('fade-out');
    setTimeout(() => {
        msgEl.textContent = text;
        msgEl.classList.remove('fade-out');
    }, 340);
}

/* ---- MODE TOGGLE ---- */
toggle.addEventListener('change', function () {
    if (this.checked) {
        // BADDIE
        audioCutie.pause();
        // FIX: don't reset currentTime — preserve playback position when switching back
        playAudio(audioBaddie);
        swapImage("https://github.com/rezawahyuramadhani01-droid/ketrin-birthday/raw/main/baddie-photo.jpg");
        $body.classList.add('baddie-mode');
        greeting.textContent = "Ketrin.";
        badge.textContent    = "✦ your day";
        fadeMessage("You don't need a party to know your worth. You already know. 🖤");
        ctaBtn.textContent   = "A Letter For You";
        stopEmojis();
        // close note if open when switching modes
        if (noteIsOpen) closeNote();
    } else {
        // CUTIE
        audioBaddie.pause();
        playAudio(audioCutie);
        swapImage("https://github.com/rezawahyuramadhani01-droid/ketrin-birthday/raw/main/cutie-photo.jpg");
        $body.classList.remove('baddie-mode');
        greeting.textContent = "Happy Birthday, Ketrin!";
        badge.textContent    = "🎂 It's Your Day";
        fadeMessage("To the girl who makes every day brighter — even from far away. Hope your birthday feels as special as you are. ✨");
        ctaBtn.textContent   = "A Letter For You 💌";
        startEmojis();
        fireCutieConfetti();
        if (noteIsOpen) closeNote();
    }
});

/* ---- PAGE LOAD ---- */
window.addEventListener('load', () => setTimeout(fireCutieConfetti, 800));
</script>
</body>
</html>
