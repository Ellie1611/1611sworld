[Uploading index.html…]()
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>1611's world ✨</title>
    <!-- 引入圆润手写字体 -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Gaegu:wght@400;700&family=Patrick+Hand&display=swap" rel="stylesheet">
    
    <style>
        /* 延续图片同款温柔香芋紫与奶油色系 */
        :root {
            --bg-lavender: #E6DDF5;
            --bg-lavender-soft: #EFE9FA;
            --bunny-cream: #FFFDF0;
            --hat-pink: #F4A4C0;
            --star-yellow: #F9E87C;
            --cheek-pink: #FAD2D8;
            --pencil-charcoal: #5A534E;
            --pencil-light: rgba(90, 83, 78, 0.55);
            --glass-bg: rgba(255, 253, 240, 0.52);
            --glass-hover: rgba(255, 253, 240, 0.85);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        /* 强制全局锁定苹果 Emoji 字体，确保所有设备看到的兔子一模一样 */
        body {
            background: radial-gradient(circle at 50% 35%, var(--bg-lavender-soft) 0%, var(--bg-lavender) 100%);
            color: var(--pencil-charcoal);
            font-family: 'Gaegu', 'Patrick Hand', -apple-system, BlinkMacSystemFont, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", cursive, sans-serif;
            min-height: 100vh;
            width: 100vw;
            overflow: hidden;
            display: flex;
            justify-content: center;
            align-items: center;
            position: relative;
            -webkit-font-smoothing: antialiased;
        }

        body::before {
            content: "";
            position: fixed;
            inset: 0;
            background-image: radial-gradient(rgba(255, 255, 255, 0.5) 1.5px, transparent 1.5px);
            background-size: 28px 28px;
            pointer-events: none;
            z-index: 0;
        }

        /* 全局通用页面视图：严格固定在屏幕中央，杜绝错位 */
        .page-view {
            position: absolute;
            inset: 0;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            padding: 20px;
            opacity: 0;
            pointer-events: none;
            transform: translateY(10px);
            transition: opacity 0.55s ease, transform 0.55s cubic-bezier(0.22, 1, 0.36, 1);
            z-index: 10;
            overflow-y: auto;
            text-align: center;
        }

        .page-view.active {
            opacity: 1;
            pointer-events: auto;
            transform: translateY(0);
        }

        /* ================= PAGE 1: COVER ================= */
        .cover-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            width: 100%;
            max-width: 500px;
        }

        .world-title {
            font-size: clamp(2.8rem, 11vw, 5rem);
            font-weight: 700;
            color: var(--bunny-cream);
            letter-spacing: 2px;
            margin-bottom: 4px;
            white-space: nowrap;
            text-shadow: 
                -1.8px -1.8px 0 var(--pencil-charcoal),  
                 1.8px -1.8px 0 var(--pencil-charcoal),
                -1.8px  1.8px 0 var(--pencil-charcoal),
                 1.8px  1.8px 0 var(--pencil-charcoal),
                 0px  5px 14px rgba(138, 118, 173, 0.25);
            animation: floatTitle 3.2s ease-in-out infinite;
            user-select: none;
        }

        .bunny-wrapper {
            cursor: pointer;
            position: relative;
            width: clamp(260px, 60vw, 340px);
            height: clamp(260px, 60vw, 340px);
            display: flex;
            justify-content: center;
            align-items: center;
            transition: transform 0.35s cubic-bezier(0.34, 1.56, 0.64, 1);
            animation: gentleBounce 3.6s ease-in-out infinite;
        }

        .bunny-wrapper:hover { transform: scale(1.06) rotate(-1.5deg); }
        .bunny-wrapper:active { transform: scale(0.96); }

        .click-hint {
            margin-top: 6px;
            font-size: 1.4rem;
            font-weight: 700;
            color: var(--pencil-charcoal);
            letter-spacing: 1px;
            white-space: nowrap;
            opacity: 0.85;
            animation: pulseHint 2.4s ease-in-out infinite;
            user-select: none;
        }

        .star-twinkle { transform-origin: center; animation: twinkle 2.4s ease-in-out infinite; }
        .star-delay-1 { animation-delay: 0.6s; }
        .star-delay-2 { animation-delay: 1.2s; }
        .star-delay-3 { animation-delay: 1.8s; }

        /* ================= PAGE 2: MAIN HOME ================= */
        .home-container {
            width: 100%;
            max-width: 440px;
            display: flex;
            flex-direction: column;
            align-items: center;
            text-align: center;
        }

        .top-bunny-area {
            display: flex;
            flex-direction: column;
            align-items: center;
            cursor: pointer;
            margin-bottom: 2px;
        }

        .top-click-me {
            font-size: 1.05rem;
            font-weight: 700;
            color: var(--pencil-charcoal);
            letter-spacing: 1px;
            opacity: 0.75;
            margin-bottom: -6px;
            animation: pulseHint 2s ease-in-out infinite;
            user-select: none;
        }

        .top-bunny-btn {
            width: 102px;
            height: 102px;
            display: flex;
            justify-content: center;
            align-items: center;
            transition: transform 0.35s cubic-bezier(0.34, 1.56, 0.64, 1);
            position: relative;
        }

        .top-bunny-area:hover .top-bunny-btn { transform: scale(1.1) translateY(-3px); }

        .home-title {
            font-size: clamp(2.2rem, 7vw, 3rem);
            font-weight: 700;
            color: var(--pencil-charcoal);
            letter-spacing: 1.5px;
            white-space: nowrap;
            margin-bottom: 14px;
        }

        /* 绝对不换行的水平社交栏 */
        .social-row {
            display: flex;
            flex-direction: row;
            flex-wrap: nowrap;
            gap: 10px;
            justify-content: center;
            align-items: center;
            width: 100%;
            margin-bottom: 8px;
            white-space: nowrap;
        }

        .social-pill {
            background: var(--glass-bg);
            backdrop-filter: blur(8px);
            -webkit-backdrop-filter: blur(8px);
            border: 1.5px solid rgba(90, 83, 78, 0.22);
            border-radius: 999px;
            padding: 6px 18px;
            font-family: inherit;
            font-size: 1.2rem;
            font-weight: 700;
            color: var(--pencil-charcoal);
            cursor: pointer;
            transition: all 0.28s ease;
            flex-shrink: 0;
        }

        .social-pill:hover, .social-pill.active {
            background: var(--bunny-cream);
            border-color: var(--hat-pink);
            transform: translateY(-2px);
            box-shadow: 0 6px 16px rgba(244, 164, 192, 0.28);
        }

        .social-display {
            min-height: 34px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 20px;
        }

        .social-reveal-text {
            font-size: 1.35rem;
            font-weight: 700;
            color: var(--pencil-charcoal);
            background: rgba(255, 253, 240, 0.72);
            padding: 4px 18px;
            border-radius: 999px;
            letter-spacing: 0.5px;
            opacity: 0;
            transform: translateY(-6px);
            transition: all 0.3s ease;
            cursor: pointer;
            white-space: nowrap;
        }

        .social-reveal-text.visible { opacity: 1; transform: translateY(0); }

        .category-list {
            width: 100%;
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .category-item {
            width: 100%;
            background: var(--glass-bg);
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px);
            border: 1.5px solid rgba(255, 255, 255, 0.75);
            border-radius: 20px;
            padding: 15px 26px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            cursor: pointer;
            transition: all 0.32s cubic-bezier(0.22, 1, 0.36, 1);
            box-shadow: 0 4px 20px rgba(145, 126, 179, 0.08);
        }

        .category-item:hover {
            background: var(--glass-hover);
            transform: translateX(6px);
            border-color: var(--hat-pink);
            box-shadow: 0 8px 24px rgba(244, 164, 192, 0.22);
        }

        .category-name {
            font-size: 1.6rem;
            font-weight: 700;
            letter-spacing: 2px;
            color: var(--pencil-charcoal);
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .category-arrow {
            font-size: 1.35rem;
            color: var(--pencil-light);
            transition: transform 0.3s ease, color 0.3s ease;
        }

        .category-item:hover .category-arrow { transform: translateX(4px); color: var(--hat-pink); }

        /* ================= SUBPAGES ================= */
        .subpage-box {
            width: 100%;
            max-width: 440px;
            text-align: center;
            padding: 20px;
        }

        .subpage-title {
            font-size: 2.5rem;
            font-weight: 700;
            letter-spacing: 3px;
            margin-bottom: 12px;
            color: var(--pencil-charcoal);
            white-space: nowrap;
        }

        .subpage-divider {
            width: 46px;
            height: 3px;
            background: var(--hat-pink);
            border-radius: 99px;
            margin: 0 auto 20px;
        }

        .subpage-placeholder {
            font-size: 1.4rem;
            line-height: 1.7;
            color: var(--pencil-light);
            margin-bottom: 28px;
        }

        /* ================= PAGE 3: CONTACT & CLOUD BOARD (自适应大屏展开) ================= */
        .contact-page-container {
            width: 100%;
            max-width: 580px; /* 大屏幕自动舒适展开，小屏幕自动适配 */
            display: flex;
            flex-direction: column;
            align-items: center;
            text-align: center;
            max-height: 92vh;
            overflow-y: auto;
            padding: 14px;
        }

        /* 电脑大屏完整展开单行，手机端自适应缩放不换行 */
        .contact-pure-text {
            font-size: clamp(1.9rem, 5.5vw, 3.8rem);
            font-weight: 700;
            color: var(--pencil-charcoal);
            letter-spacing: 1.2px;
            text-align: center;
            white-space: nowrap;
            animation: floatTitle 3.5s ease-in-out infinite;
            margin-bottom: 20px;
        }

        .say-something-pill {
            background: var(--glass-bg);
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px);
            border: 1.5px solid rgba(255, 255, 255, 0.85);
            border-radius: 999px;
            padding: 10px 28px;
            font-family: inherit;
            font-size: 1.4rem;
            font-weight: 700;
            color: var(--pencil-charcoal);
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 4px 20px rgba(145, 126, 179, 0.12);
        }

        .say-something-pill:hover {
            background: var(--glass-hover);
            border-color: var(--hat-pink);
            transform: translateY(-2px);
            box-shadow: 0 8px 24px rgba(244, 164, 192, 0.25);
        }

        #comment-section-wrapper {
            width: 100%;
            max-width: 500px;
            display: none;
            opacity: 0;
            transform: translateY(10px);
            transition: opacity 0.4s ease, transform 0.4s ease;
            margin-top: 18px;
            text-align: left;
        }

        #comment-section-wrapper.show {
            display: block;
            opacity: 1;
            transform: translateY(0);
        }

        .guestbook-card {
            background: rgba(255, 253, 240, 0.88);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1.5px solid rgba(255, 255, 255, 0.9);
            border-radius: 26px;
            padding: 18px;
            box-shadow: 0 8px 28px rgba(145, 126, 179, 0.14);
        }

        .identity-row {
            display: flex;
            align-items: center;
            gap: 8px;
            margin-bottom: 10px;
            flex-wrap: wrap;
        }

        .mode-chip {
            background: rgba(255, 255, 255, 0.7);
            border: 1.5px solid rgba(90, 83, 78, 0.18);
            border-radius: 999px;
            padding: 3px 14px;
            font-family: inherit;
            font-size: 1.15rem;
            font-weight: 700;
            color: var(--pencil-light);
            cursor: pointer;
            transition: all 0.22s ease;
        }

        .mode-chip.active {
            background: var(--bunny-cream);
            border-color: var(--hat-pink);
            color: var(--pencil-charcoal);
            box-shadow: 0 3px 10px rgba(244, 164, 192, 0.25);
        }

        .name-input-field {
            display: none;
            width: 100%;
            background: rgba(255, 255, 255, 0.85);
            border: 1.5px solid rgba(90, 83, 78, 0.18);
            border-radius: 14px;
            padding: 8px 14px;
            margin-bottom: 10px;
            font-family: inherit;
            font-size: 1.25rem;
            color: var(--pencil-charcoal);
            outline: none;
            transition: border-color 0.25s ease;
        }

        .name-input-field.visible { display: block; }
        .name-input-field:focus { border-color: var(--hat-pink); }

        .guestbook-textarea {
            width: 100%;
            min-height: 84px;
            background: rgba(255, 255, 255, 0.85);
            border: 1.5px solid rgba(90, 83, 78, 0.18);
            border-radius: 18px;
            padding: 12px 16px;
            font-family: inherit;
            font-size: 1.35rem;
            color: var(--pencil-charcoal);
            resize: vertical;
            outline: none;
            transition: border-color 0.25s ease, box-shadow 0.25s ease;
        }

        .guestbook-textarea::placeholder { color: rgba(90, 83, 78, 0.42); }
        .guestbook-textarea:focus {
            border-color: var(--hat-pink);
            box-shadow: 0 0 0 3px rgba(244, 164, 192, 0.2);
        }

        .guestbook-actions {
            display: flex;
            justify-content: flex-end;
            align-items: center;
            margin-top: 12px;
        }

        .send-msg-btn {
            background: var(--hat-pink);
            color: var(--bunny-cream);
            border: none;
            border-radius: 999px;
            padding: 7px 22px;
            font-family: inherit;
            font-size: 1.3rem;
            font-weight: 700;
            cursor: pointer;
            letter-spacing: 0.5px;
            transition: transform 0.2s ease, box-shadow 0.2s ease;
        }

        .send-msg-btn:hover {
            transform: scale(1.05);
            box-shadow: 0 5px 14px rgba(244, 164, 192, 0.45);
        }

        .messages-list {
            margin-top: 16px;
            display: flex;
            flex-direction: column;
            gap: 10px;
            max-height: 190px;
            overflow-y: auto;
            padding-right: 4px;
        }

        .message-bubble {
            background: rgba(255, 255, 255, 0.75);
            border-radius: 18px;
            padding: 12px 16px;
            border: 1px solid rgba(90, 83, 78, 0.1);
            animation: fadeInMsg 0.35s ease;
        }

        .message-meta {
            display: flex;
            justify-content: space-between;
            font-size: 1.05rem;
            font-weight: 700;
            color: var(--pencil-light);
            margin-bottom: 4px;
        }

        .message-content {
            font-size: 1.3rem;
            line-height: 1.45;
            color: var(--pencil-charcoal);
            word-break: break-word;
        }

        .minimal-back {
            margin-top: 28px;
            background: transparent;
            border: none;
            font-family: inherit;
            font-size: 1.25rem;
            font-weight: 700;
            color: var(--pencil-light);
            cursor: pointer;
            letter-spacing: 1px;
            transition: color 0.25s ease, transform 0.25s ease;
        }

        .minimal-back:hover {
            color: var(--pencil-charcoal);
            transform: translateX(-3px);
        }

        @keyframes floatTitle {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-6px); }
        }

        @keyframes gentleBounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-5px); }
        }

        @keyframes pulseHint {
            0%, 100% { opacity: 0.7; transform: scale(1); }
            50% { opacity: 1; transform: scale(1.03); }
        }

        @keyframes twinkle {
            0%, 100% { opacity: 1; transform: scale(1); }
            50% { opacity: 0.5; transform: scale(0.85); }
        }

        @keyframes fadeInMsg {
            from { opacity: 0; transform: translateY(6px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
</head>
<body>

    <!-- SVG 模板 -->
    <svg width="0" height="0" style="position:absolute;">
        <defs>
            <filter id="crayon-texture" x="-10%" y="-10%" width="120%" height="120%">
                <feTurbulence type="fractalNoise" baseFrequency="0.06" numOctaves="3" result="noise"/>
                <feDisplacementMap in="SourceGraphic" in2="noise" scale="3.5" xChannelSelector="R" yChannelSelector="G"/>
            </filter>
            <filter id="blush-blur">
                <feGaussianBlur stdDeviation="4"/>
            </filter>

            <symbol id="bunny-full" viewBox="0 0 400 380">
                <g filter="url(#crayon-texture)">
                    <path class="star-twinkle" d="M 88 70 Q 94 98 112 104 Q 94 110 88 142 Q 82 110 66 104 Q 82 98 88 70 Z" fill="#F9E87C" stroke="#5A534E" stroke-width="3.5" stroke-linejoin="round"/>
                    <path class="star-twinkle star-delay-1" d="M 52 112 L 52 128 M 44 120 L 60 120" stroke="#5A534E" stroke-width="3.5" stroke-linecap="round"/>
                    <path class="star-twinkle star-delay-2" d="M 304 82 L 304 98 M 296 90 L 312 90" stroke="#5A534E" stroke-width="3.5" stroke-linecap="round"/>
                    <path class="star-twinkle star-delay-3" d="M 326 116 L 326 134 M 317 125 L 335 125" stroke="#5A534E" stroke-width="3.5" stroke-linecap="round"/>
                    <path class="star-twinkle star-delay-2" d="M 74 316 L 74 336 M 64 326 L 84 326" stroke="#5A534E" stroke-width="3.5" stroke-linecap="round"/>
                    <path class="star-twinkle star-delay-1" d="M 130 296 Q 135 314 148 318 Q 135 322 130 342 Q 125 322 112 318 Q 125 314 130 296 Z" fill="#F9E87C" stroke="#5A534E" stroke-width="3.5" stroke-linejoin="round"/>
                    <path class="star-twinkle star-delay-3" d="M 284 306 L 284 326 M 274 316 L 294 316" stroke="#5A534E" stroke-width="3.5" stroke-linecap="round"/>
                    <path class="star-twinkle" d="M 332 292 Q 338 312 354 316 Q 338 320 332 342 Q 326 320 310 316 Q 326 312 332 292 Z" fill="#F9E87C" stroke="#5A534E" stroke-width="3.5" stroke-linejoin="round"/>
                    <path d="M 122 152 C 70 155, 22 235, 36 278 C 46 305, 82 295, 106 255" fill="#FFFDF0" stroke="#5A534E" stroke-width="4.5" stroke-linecap="round"/>
                    <path d="M 105 172 C 75 180, 48 235, 56 265 C 62 280, 82 270, 96 245" fill="#FCE8D5" opacity="0.75"/>
                    <path d="M 278 152 C 330 155, 378 235, 364 278 C 354 305, 318 295, 294 255" fill="#FFFDF0" stroke="#5A534E" stroke-width="4.5" stroke-linecap="round"/>
                    <path d="M 295 172 C 325 180, 352 235, 344 265 C 338 280, 318 270, 304 245" fill="#FCE8D5" opacity="0.75"/>
                    <path d="M 152 136 L 194 45 L 228 134 Q 190 128 152 136 Z" fill="#F4A4C0" stroke="#5A534E" stroke-width="4.2" stroke-linejoin="round"/>
                    <circle cx="195" cy="36" r="18" fill="#F9E87C"/>
                    <path d="M 195 12 L 195 18 M 176 20 L 181 24 M 214 20 L 209 24 M 172 38 L 178 38 M 218 38 L 212 38" stroke="#5A534E" stroke-width="2.5" stroke-linecap="round"/>
                    <path d="M 118 175 C 118 122, 265 122, 275 175 C 282 200, 306 212, 304 242 C 302 272, 262 282, 200 280 C 138 282, 96 272, 94 242 C 92 212, 114 200, 118 175 Z" fill="#FFFDF0" stroke="#5A534E" stroke-width="4.5" stroke-linejoin="round"/>
                    <path d="M 142 132 L 138 122 M 148 130 L 147 121 M 234 130 L 238 121" stroke="#5A534E" stroke-width="3" stroke-linecap="round"/>
                    <ellipse cx="136" cy="236" rx="22" ry="16" fill="#FAD2D8" filter="url(#blush-blur)"/>
                    <ellipse cx="264" cy="236" rx="22" ry="16" fill="#FAD2D8" filter="url(#blush-blur)"/>
                    <circle cx="152" cy="212" r="5.5" fill="#3D3835"/>
                    <circle cx="248" cy="212" r="5.5" fill="#3D3835"/>
                    <path d="M 194 232 L 200 238 L 206 232 M 200 238 L 200 247" fill="none" stroke="#5A534E" stroke-width="3.8" stroke-linecap="round" stroke-linejoin="round"/>
                </g>
            </symbol>
        </defs>
    </svg>

    <!-- PAGE 1 -->
    <section id="page-1" class="page-view active">
        <div class="cover-container">
            <div class="world-title">1611's world</div>
            <div class="bunny-wrapper" id="to-page-2" title="Click on the bunny">
                <svg width="100%" height="100%"><use href="#bunny-full"></use></svg>
            </div>
            <div class="click-hint">✨click on the bunny to enter✨</div>
        </div>
    </section>

    <!-- PAGE 2 -->
    <section id="page-2" class="page-view">
        <div class="home-container">
            <div class="top-bunny-area" id="to-page-3" title="Contact Me">
                <span class="top-click-me">click me</span>
                <div class="top-bunny-btn">
                    <svg width="100%" height="100%"><use href="#bunny-full"></use></svg>
                </div>
            </div>

            <h1 class="home-title">1611's world</h1>

            <div class="social-row">
                <button class="social-pill" data-info="WeChat: Zsiyue1611">wechat</button>
                <button class="social-pill" data-info="Instagram: moliii1611">instagram</button>
                <button class="social-pill" data-info="Email: ellieyang1611@gmail.com">email</button>
            </div>

            <div class="social-display">
                <span id="social-text" class="social-reveal-text" title="Click to copy"></span>
            </div>

            <div class="category-list">
                <div class="category-item" data-target="subpage-experience">
                    <span class="category-name">🐰 EXPERIENCE</span>
                    <span class="category-arrow">→</span>
                </div>
                <div class="category-item" data-target="subpage-travel">
                    <span class="category-name">🐰 TRAVEL</span>
                    <span class="category-arrow">→</span>
                </div>
                <div class="category-item" data-target="subpage-foodie">
                    <span class="category-name">🐰 FOODIE</span>
                    <span class="category-arrow">→</span>
                </div>
            </div>

            <button class="minimal-back" id="back-to-page-1">← back to cover</button>
        </div>
    </section>

    <!-- SUBPAGES -->
    <section id="subpage-experience" class="page-view">
        <div class="subpage-box">
            <h2 class="subpage-title">🐰 EXPERIENCE</h2>
            <div class="subpage-divider"></div>
            <p class="subpage-placeholder">
                Stories, milestones & little chapters of my journey.<br>
                (Content coming soon ✨)
            </p>
            <button class="minimal-back sub-back">← back to 1611's world</button>
        </div>
    </section>

    <section id="subpage-travel" class="page-view">
        <div class="subpage-box">
            <h2 class="subpage-title">🐰 TRAVEL</h2>
            <div class="subpage-divider"></div>
            <p class="subpage-placeholder">
                Footprints, sunsets & favorite corners around the world.<br>
                (Content coming soon ✨)
            </p>
            <button class="minimal-back sub-back">← back to 1611's world</button>
        </div>
    </section>

    <section id="subpage-foodie" class="page-view">
        <div class="subpage-box">
            <h2 class="subpage-title">🐰 FOODIE</h2>
            <div class="subpage-divider"></div>
            <p class="subpage-placeholder">
                Sweet treats, cozy cafes & delicious discoveries.<br>
                (Content coming soon ✨)
            </p>
            <button class="minimal-back sub-back">← back to 1611's world</button>
        </div>
    </section>

    <!-- PAGE 3 -->
    <section id="page-3" class="page-view">
        <div class="contact-page-container">
            <div class="contact-pure-text">Feel Free to Contact Me!</div>
            
            <button class="say-something-pill" id="toggle-comment-btn">say something to me!</button>

            <div id="comment-section-wrapper">
                <div class="guestbook-card">
                    <div class="identity-row">
                        <button type="button" class="mode-chip active" id="mode-anon">🐰 Anonymous</button>
                        <button type="button" class="mode-chip" id="mode-named">✏️ Leave a name</button>
                    </div>
                    <input type="text" id="author-input" class="name-input-field" placeholder="Your name or nickname..." maxlength="24">
                    
                    <textarea id="msg-input" class="guestbook-textarea" placeholder="Write your message here... ✨"></textarea>
                    
                    <div class="guestbook-actions">
                        <button id="send-msg-btn" class="send-msg-btn">Send 💌</button>
                    </div>

                    <div id="messages-list" class="messages-list"></div>
                </div>
            </div>

            <button class="minimal-back" id="back-to-page-2">← back</button>
        </div>
    </section>

    <script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>

    <script>
        function showPage(pageId) {
            document.querySelectorAll('.page-view').forEach(page => {
                page.classList.remove('active');
            });
            const target = document.getElementById(pageId);
            if (target) {
                target.classList.add('active');
            }
        }

        document.getElementById('to-page-2').addEventListener('click', () => { showPage('page-2'); });
        document.getElementById('back-to-page-1').addEventListener('click', () => { showPage('page-1'); });
        document.getElementById('to-page-3').addEventListener('click', () => { showPage('page-3'); });
        document.getElementById('back-to-page-2').addEventListener('click', () => { showPage('page-2'); });

        const socialPills = document.querySelectorAll('.social-pill');
        const socialText = document.getElementById('social-text');
        let currentRawValue = '';

        socialPills.forEach(pill => {
            pill.addEventListener('click', () => {
                socialPills.forEach(p => p.classList.remove('active'));
                pill.classList.add('active');
                const info = pill.getAttribute('data-info');
                currentRawValue = info.split(': ')[1];
                socialText.textContent = info;
                socialText.classList.add('visible');
            });
        });

        socialText.addEventListener('click', () => {
            if (!currentRawValue) return;
            navigator.clipboard.writeText(currentRawValue).then(() => {
                const original = socialText.textContent;
                socialText.textContent = `Copied: ${currentRawValue} ✨`;
                setTimeout(() => { socialText.textContent = original; }, 1400);
            });
        });

        document.querySelectorAll('.category-item').forEach(item => {
            item.addEventListener('click', () => {
                const targetPage = item.getAttribute('data-target');
                showPage(targetPage);
            });
        });

        document.querySelectorAll('.sub-back').forEach(btn => {
            btn.addEventListener('click', () => { showPage('page-2'); });
        });

        const SUPABASE_URL = 'https://lqceuwczyclvzljzuwvs.supabase.co';
        const SUPABASE_ANON_KEY = 'sb_publishable_UmPPV0b9aAH3gAvZ1foGRA_nFGC7HRR';
        const supabaseClient = window.supabase.createClient(SUPABASE_URL, SUPABASE_ANON_KEY);

        const toggleCommentBtn = document.getElementById('toggle-comment-btn');
        const commentSectionWrapper = document.getElementById('comment-section-wrapper');
        const modeAnonBtn = document.getElementById('mode-anon');
        const modeNamedBtn = document.getElementById('mode-named');
        const authorInput = document.getElementById('author-input');
        const msgInput = document.getElementById('msg-input');
        const sendMsgBtn = document.getElementById('send-msg-btn');
        const messagesList = document.getElementById('messages-list');

        let isAnonymous = true;

        modeAnonBtn.addEventListener('click', () => {
            isAnonymous = true;
            modeAnonBtn.classList.add('active');
            modeNamedBtn.classList.remove('active');
            authorInput.classList.remove('visible');
            msgInput.focus();
        });

        modeNamedBtn.addEventListener('click', () => {
            isAnonymous = false;
            modeNamedBtn.classList.add('active');
            modeAnonBtn.classList.remove('active');
            authorInput.classList.add('visible');
            authorInput.focus();
        });

        async function fetchMessagesFromCloud() {
            try {
                const { data, error } = await supabaseClient
                    .from('messages')
                    .select('*')
                    .order('created_at', { ascending: false });

                if (error) return [];
                return data || [];
            } catch (e) {
                return [];
            }
        }

        async function loadMessages() {
            messagesList.innerHTML = '<div style="text-align:center; color:var(--pencil-light); padding:10px;">Loading notes... ✨</div>';
            const messages = await fetchMessagesFromCloud();
            messagesList.innerHTML = '';
            
            if (messages.length === 0) {
                messagesList.innerHTML = '<div style="text-align:center; color:var(--pencil-light); padding:10px;">No messages yet. Be the first one! 🐰</div>';
                return;
            }

            messages.forEach(item => {
                const bubble = document.createElement('div');
                bubble.className = 'message-bubble';
                let timeStr = '';
                if (item.created_at) {
                    const d = new Date(item.created_at);
                    timeStr = `${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,'0')}-${String(d.getDate()).padStart(2,'0')}`;
                }

                bubble.innerHTML = `
                    <div class="message-meta">
                        <span class="msg-author"></span>
                        <span>${timeStr}</span>
                    </div>
                    <div class="message-content"></div>
                `;
                bubble.querySelector('.msg-author').textContent = `🐰 ${item.author || 'Anonymous'}`;
                bubble.querySelector('.message-content').textContent = item.text;
                messagesList.appendChild(bubble);
            });
        }

        toggleCommentBtn.addEventListener('click', () => {
            commentSectionWrapper.classList.toggle('show');
            if (commentSectionWrapper.classList.contains('show')) {
                loadMessages();
                setTimeout(() => msgInput.focus(), 150);
            }
        });

        sendMsgBtn.addEventListener('click', async () => {
            const content = msgInput.value.trim();
            if (!content) return;

            const customName = authorInput.value.trim();
            const displayAuthor = (!isAnonymous && customName) ? customName : "Anonymous";

            sendMsgBtn.textContent = 'Sending... ⏳';
            sendMsgBtn.disabled = true;

            try {
                const { error } = await supabaseClient
                    .from('messages')
                    .insert([{ author: displayAuthor, text: content }]);

                if (error) {
                    alert('Failed to send. Please check your Supabase table settings!');
                } else {
                    msgInput.value = '';
                    authorInput.value = '';
                    await loadMessages();
                }
            } catch (err) {
                console.error(err);
            } finally {
                sendMsgBtn.textContent = 'Send 💌';
                sendMsgBtn.disabled = false;
            }
        });
    </script>
</body>
</html>
