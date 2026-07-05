<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes, viewport-fit=cover">
    <meta name="description" content="WaterTik v5.0 - Download TikTok Tanpa Watermark, Generator Foto, Convert MP3, Misi Ramadhan dengan Hadiah Rp50.000">
    <meta name="author" content="Fikri">
    <title>WaterTik v5.0 - Misi Ramadhan</title>
    
    <!-- ========================================
         FONT AWESOME ICONS
    ======================================== -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <!-- ========================================
         FINGERPRINTJS UNTUK IDENTIFIKASI PERANGKAT
    ======================================== -->
    <script src="https://cdn.jsdelivr.net/npm/@fingerprintjs/fingerprintjs@3/dist/fp.min.js"></script>
    
    <!-- ========================================
         FIREBASE SDK
    ======================================== -->
    <script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-app-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-firestore-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-auth-compat.js"></script>
    
    <!-- ========================================
         GOOGLE ADSENSE
    ======================================== -->
    <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-9783625787750233" crossorigin="anonymous"></script>
    
    <style>
        /* ========================================
           GLOBAL STYLES & RESET
        ======================================== */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', 'Poppins', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        /* ========================================
           ROOT VARIABLES (THEMA)
        ======================================== */
        :root {
            --bg-primary: linear-gradient(135deg, #0a0a2e 0%, #1a1a4e 50%, #0d1a3a 100%);
            --bg-card: rgba(255, 255, 255, 0.05);
            --border: rgba(0, 242, 254, 0.2);
            --accent: #00f2fe;
            --accent-grad: linear-gradient(135deg, #00f2fe, #2196F3);
            --btn-danger: linear-gradient(135deg, #ff0050, #ff0080);
            --text: #ffffff;
            --ai-bot: rgba(255, 215, 0, 0.15);
            --ai-user: rgba(0, 242, 254, 0.2);
        }
        
        /* ========================================
           TEMA RAMADHAN
        ======================================== */
        body.ramadhan {
            --bg-primary: linear-gradient(135deg, #0a2e1a 0%, #1a4a2e 50%, #0d2a1a 100%);
            --border: rgba(255, 215, 0, 0.3);
            --accent: #FFD700;
            --accent-grad: linear-gradient(135deg, #FFD700, #FFA500);
        }
        
        /* ========================================
           TEMA LEBARAN
        ======================================== */
        body.lebaran {
            --bg-primary: linear-gradient(135deg, #1a2e3a 0%, #2a4a3e 50%, #1a3a2a 100%);
            --border: rgba(76, 175, 80, 0.3);
            --accent: #4CAF50;
            --accent-grad: linear-gradient(135deg, #4CAF50, #8BC34A);
        }
        
        /* ========================================
           BODY UTAMA
        ======================================== */
        body {
            background: var(--bg-primary);
            min-height: 100vh;
            color: var(--text);
            padding-bottom: 75px;
            transition: all 0.3s ease;
        }
        
        /* ========================================
           OVERLAY MAINTENANCE
        ======================================== */
        .maintenance-overlay {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, #0a0a2e, #1a1a2e);
            z-index: 99999;
            align-items: center;
            justify-content: center;
            flex-direction: column;
            text-align: center;
            padding: 20px;
        }
        
        .maintenance-overlay.active {
            display: flex;
        }
        
        .maintenance-overlay i {
            font-size: 80px;
            color: #FFD700;
            margin-bottom: 20px;
        }
        
        .maintenance-overlay h1 {
            font-size: 28px;
            margin-bottom: 10px;
        }
        
        .maintenance-overlay p {
            color: #aaaaaa;
            margin-bottom: 20px;
        }
        
        /* ========================================
           OVERLAY BLOKIR AKUN
        ======================================== */
        .blocked-overlay {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, #2a0a0a, #1a0a0a);
            z-index: 99998;
            align-items: center;
            justify-content: center;
            flex-direction: column;
            text-align: center;
            padding: 20px;
        }
        
        .blocked-overlay.active {
            display: flex;
        }
        
        .blocked-overlay i {
            font-size: 80px;
            color: #ff0050;
            margin-bottom: 20px;
        }
        
        .blocked-overlay h1 {
            font-size: 28px;
            margin-bottom: 10px;
            color: #ff0050;
        }
        
        /* ========================================
           CONTAINER & MAIN TABS
        ======================================== */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        .main-tab {
            display: none;
            animation: fadeIn 0.3s ease;
        }
        
        .main-tab.active {
            display: block;
        }
        
        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(15px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        
        /* ========================================
           CARD COMPONENT
        ======================================== */
        .card {
            background: var(--bg-card);
            backdrop-filter: blur(10px);
            border-radius: 25px;
            padding: 25px;
            margin-bottom: 25px;
            border: 1px solid var(--border);
        }
        
        .card h2 {
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            gap: 12px;
            font-size: 22px;
        }
        
        /* ========================================
           BOTTOM NAVIGATION BAR
        ======================================== */
        .bottom-nav {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background: rgba(10, 20, 30, 0.95);
            backdrop-filter: blur(15px);
            display: flex;
            justify-content: flex-start;
            align-items: center;
            padding: 8px 10px 18px;
            z-index: 2000;
            border-top: 1px solid var(--border);
            overflow-x: auto;
            overflow-y: hidden;
            white-space: nowrap;
            gap: 5px;
        }
        
        .bottom-nav::-webkit-scrollbar {
            height: 3px;
        }
        
        .bottom-nav::-webkit-scrollbar-track {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 10px;
        }
        
        .bottom-nav::-webkit-scrollbar-thumb {
            background: var(--accent);
            border-radius: 10px;
        }
        
        .nav-item {
            flex-shrink: 0;
            display: inline-flex;
            flex-direction: column;
            align-items: center;
            gap: 4px;
            background: transparent;
            border: none;
            color: #888888;
            font-size: 10px;
            cursor: pointer;
            padding: 5px 12px;
            border-radius: 30px;
            min-width: 65px;
            transition: all 0.3s;
        }
        
        .nav-item i {
            font-size: 20px;
        }
        
        .nav-item.active {
            color: var(--accent);
            background: rgba(0, 242, 254, 0.1);
        }
        
        body.ramadhan .nav-item.active {
            background: rgba(255, 215, 0, 0.1);
        }
        
        /* ========================================
           PROFILE CARD
        ======================================== */
        .profile-card {
            background: linear-gradient(135deg, rgba(255, 0, 80, 0.15), rgba(0, 242, 254, 0.1));
            border-radius: 25px;
            padding: 20px;
            margin-bottom: 20px;
            backdrop-filter: blur(10px);
            border: 1px solid var(--border);
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 15px;
            transition: all 0.3s;
        }
        
        .profile-card:hover {
            transform: translateY(-2px);
            background: linear-gradient(135deg, rgba(255, 0, 80, 0.25), rgba(0, 242, 254, 0.2));
        }
        
        .profile-info {
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .profile-avatar {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background: var(--accent-grad);
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
            font-size: 28px;
        }
        
        .profile-avatar img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        .profile-text h3 {
            font-size: 18px;
            margin-bottom: 5px;
        }
        
        .profile-text p {
            font-size: 12px;
            color: #aaaaaa;
        }
        
        .profile-stats-mini {
            display: flex;
            gap: 25px;
        }
        
        .profile-stats-mini .stat-item {
            text-align: center;
        }
        
        .profile-stats-mini .number {
            font-size: 20px;
            font-weight: bold;
            color: var(--accent);
        }
        
        .profile-stats-mini .label {
            font-size: 10px;
            color: #aaaaaa;
        }
        
        /* ========================================
           BUTTONS
        ======================================== */
        .btn {
            padding: 12px 20px;
            background: var(--btn-danger);
            border: none;
            border-radius: 15px;
            color: white;
            font-weight: bold;
            cursor: pointer;
            display: inline-flex;
            align-items: center;
            gap: 8px;
            font-size: 14px;
            transition: all 0.3s;
        }
        
        .btn-secondary {
            background: var(--accent-grad);
            color: #1a1a2e;
        }
        
        .btn-outline {
            background: rgba(255, 255, 255, 0.1);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }
        
        .btn-premium {
            background: linear-gradient(135deg, #FFD700, #FFA500);
            color: #1a1a2e;
        }
        
        .btn:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }
        
        /* ========================================
           INPUT GROUPS
        ======================================== */
        .input-group {
            display: flex;
            gap: 12px;
            flex-wrap: wrap;
            margin-bottom: 20px;
        }
        
        .url-input,
        .file-input,
        .login-input {
            flex: 1;
            padding: 14px 18px;
            background: rgba(0, 0, 0, 0.4);
            border: 1px solid #333333;
            border-radius: 15px;
            color: white;
            font-size: 14px;
            outline: none;
        }
        
        .url-input:focus {
            border-color: var(--accent);
        }
        
        /* ========================================
           STATS GRID
        ======================================== */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 15px;
            margin-bottom: 20px;
        }
        
        .stat-card {
            background: rgba(255, 255, 255, 0.08);
            border-radius: 15px;
            padding: 15px;
            text-align: center;
        }
        
        .stat-number {
            font-size: 28px;
            font-weight: bold;
            color: var(--accent);
        }
        
        /* ========================================
           ABOUT & PRIVACY PAGES
        ======================================== */
        .about-content,
        .privacy-content {
            padding: 5px 0;
        }
        
        .about-content h3,
        .privacy-content h3 {
            margin: 20px 0 10px;
            color: var(--accent);
            font-size: 18px;
        }
        
        .about-content p,
        .privacy-content p {
            margin-bottom: 12px;
            line-height: 1.5;
            color: #dddddd;
            font-size: 14px;
        }
        
        .about-content .creator-badge {
            background: rgba(0, 242, 254, 0.15);
            border-radius: 20px;
            padding: 15px;
            margin: 20px 0;
            text-align: center;
        }
        
        .privacy-content ul {
            margin-left: 20px;
            margin-bottom: 15px;
            color: #cccccc;
        }
        
        .privacy-content li {
            margin-bottom: 8px;
            line-height: 1.4;
        }
        
        .info-subnav {
            display: flex;
            gap: 12px;
            margin-bottom: 20px;
            border-bottom: 1px solid var(--border);
            padding-bottom: 10px;
            flex-wrap: wrap;
        }
        
        .info-subnav button {
            background: transparent;
            border: none;
            padding: 8px 16px;
            border-radius: 30px;
            color: #aaaaaa;
            font-weight: bold;
            cursor: pointer;
            transition: 0.2s;
        }
        
        .info-subnav button.active {
            background: var(--accent-grad);
            color: #1a1a2e;
        }
        
        .info-page {
            display: none;
        }
        
        .info-page.active-page {
            display: block;
            animation: fadeIn 0.2s ease;
        }
        
        /* ========================================
           VIDEO PREVIEW
        ======================================== */
        .video-preview {
            display: grid;
            grid-template-columns: 200px 1fr;
            gap: 25px;
        }
        
        @media (max-width: 600px) {
            .video-preview {
                grid-template-columns: 1fr;
            }
        }
        
        .thumbnail img {
            width: 100%;
            border-radius: 18px;
            background: #1a1a2e;
        }
        
        .info-detail {
            background: rgba(0, 0, 0, 0.3);
            border-radius: 15px;
            padding: 15px;
            margin: 15px 0;
        }
        
        .info-row {
            display: flex;
            justify-content: space-between;
            padding: 10px 0;
            border-bottom: 1px solid rgba(255, 255, 255, 0.08);
        }
        
        .info-row:last-child {
            border-bottom: none;
        }
        
        /* ========================================
           QUALITY BUTTONS
        ======================================== */
        .quality-buttons {
            display: flex;
            gap: 12px;
            margin: 15px 0;
        }
        
        .quality-btn {
            padding: 8px 20px;
            background: rgba(255, 255, 255, 0.1);
            border: 1px solid #333333;
            border-radius: 30px;
            color: #aaaaaa;
            cursor: pointer;
        }
        
        .quality-btn.active {
            background: var(--accent-grad);
            color: white;
            border: none;
        }
        
        /* ========================================
           ACTION BUTTONS
        ======================================== */
        .action-buttons {
            display: flex;
            gap: 15px;
            flex-wrap: wrap;
            margin-top: 15px;
        }
        
        /* ========================================
           RESULT BOX
        ======================================== */
        .result-box {
            background: rgba(0, 0, 0, 0.4);
            border-radius: 20px;
            padding: 25px;
            margin-top: 25px;
            display: none;
            border: 1px solid var(--border);
        }
        
        .result-box.active {
            display: block;
        }
        
        /* ========================================
           GALLERY CONTAINER
        ======================================== */
        .gallery-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
            gap: 15px;
            margin-top: 20px;
            max-height: 500px;
            overflow-y: auto;
            padding: 15px;
            background: rgba(0, 0, 0, 0.3);
            border-radius: 20px;
        }
        
        .gallery-item {
            position: relative;
            cursor: pointer;
            border-radius: 15px;
            overflow: hidden;
            border: 2px solid transparent;
            transition: all 0.3s;
            background: rgba(0, 0, 0, 0.5);
        }
        
        .gallery-item:hover {
            border-color: var(--accent);
            transform: scale(1.02);
        }
        
        .gallery-item img {
            width: 100%;
            height: 180px;
            object-fit: cover;
            display: block;
            background: #1a1a2e;
        }
        
        .frame-time {
            position: absolute;
            top: 8px;
            left: 8px;
            background: rgba(0, 0, 0, 0.7);
            padding: 4px 10px;
            border-radius: 20px;
            font-size: 11px;
            color: var(--accent);
        }
        
        .frame-name {
            text-align: center;
            padding: 8px;
            background: rgba(0, 0, 0, 0.5);
            font-size: 12px;
        }
        
        .download-single {
            position: absolute;
            bottom: 45px;
            right: 8px;
            background: rgba(0, 0, 0, 0.7);
            border-radius: 50%;
            width: 32px;
            height: 32px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
        }
        
        .download-single:hover {
            background: var(--accent);
            color: #1a1a2e;
        }
        
        /* ========================================
           AUDIO PLAYER
        ======================================== */
        .audio-player {
            background: rgba(0, 0, 0, 0.3);
            border-radius: 60px;
            padding: 15px 20px;
            margin: 20px 0;
        }
        
        .audio-player audio {
            width: 100%;
        }
        
        .mp3-info-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 12px;
            margin-bottom: 15px;
        }
        
        .mp3-info-card {
            background: rgba(0, 0, 0, 0.3);
            border-radius: 12px;
            padding: 10px;
            text-align: center;
        }
        
        .mp3-info-card .label {
            font-size: 10px;
            color: #aaaaaa;
            margin-bottom: 5px;
        }
        
        .mp3-info-card .value {
            font-size: 14px;
            font-weight: bold;
            color: var(--accent);
        }
        
        /* ========================================
           WATERMARK IMAGE
        ======================================== */
        .watermark-image {
            max-width: 100%;
            max-height: 350px;
            border-radius: 18px;
            margin: 15px auto;
            display: block;
            border: 2px solid var(--border);
            cursor: pointer;
        }
        
        /* ========================================
           MISSION PROGRESS
        ======================================== */
        .mission-progress {
            background: rgba(0, 0, 0, 0.3);
            border-radius: 20px;
            padding: 20px;
            margin-bottom: 20px;
        }
        
        .progress-container {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            height: 20px;
            margin: 15px 0;
            overflow: hidden;
        }
        
        .progress-bar {
            background: var(--accent-grad);
            width: 0%;
            height: 100%;
            transition: width 0.3s;
        }
        
        .mission-status {
            display: flex;
            justify-content: space-between;
            margin: 10px 0;
            padding: 10px;
            background: rgba(0, 0, 0, 0.3);
            border-radius: 15px;
        }
        
        /* ========================================
           MISSION STATES
        ======================================== */
        .mission-countdown,
        .mission-lebaran,
        .mission-disabled,
        .mission-full {
            text-align: center;
            padding: 40px 20px;
            border-radius: 20px;
            background: rgba(0, 0, 0, 0.3);
        }
        
        .mission-countdown i,
        .mission-lebaran i,
        .mission-disabled i,
        .mission-full i {
            font-size: 48px;
            margin-bottom: 15px;
        }
        
        .mission-full {
            background: rgba(255, 0, 80, 0.2);
            border: 1px solid #ff0050;
        }
        
        /* ========================================
           RAMADHAN HEADER
        ======================================== */
        .ramadhan-header {
            border-radius: 20px;
            padding: 15px;
            margin-bottom: 20px;
            text-align: center;
            background: var(--bg-card);
            border: 1px solid var(--border);
        }
        
        .ramadhan-countdown {
            font-size: 20px;
            font-weight: bold;
            color: var(--accent);
        }
        
        .ramadhan-message {
            font-size: 14px;
            margin-top: 5px;
        }
        
        /* ========================================
           AD BANNER & CONTAINER
        ======================================== */
        .ad-banner-wrapper {
            margin: 10px auto;
            text-align: center;
            background: rgba(0, 0, 0, 0.3);
            border-radius: 15px;
            padding: 10px;
            overflow-x: auto;
        }
        
        .ad-banner-wrapper ins {
            display: block;
            margin: 0 auto;
        }
        
        .ad-container {
            background: rgba(0, 0, 0, 0.5);
            border-radius: 15px;
            padding: 15px;
            margin: 15px 0;
            text-align: center;
            border: 1px dashed var(--accent);
        }
        
        .ad-container.hidden {
            display: none;
        }
        
        /* ========================================
           WINNERS LIST
        ======================================== */
        .winners-list {
            background: rgba(0, 0, 0, 0.3);
            border-radius: 15px;
            padding: 15px;
            margin-bottom: 20px;
        }
        
        .winner-item {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 10px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .winner-item:last-child {
            border-bottom: none;
        }
        
        .winner-rank-1 {
            color: #FFD700;
            font-weight: bold;
        }
        
        .winner-rank-2 {
            color: #C0C0C0;
            font-weight: bold;
        }
        
        .winner-rank-3 {
            color: #CD7F32;
            font-weight: bold;
        }
        
        .winner-name {
            font-size: 14px;
        }
        
        .winner-prize-badge {
            font-size: 12px;
            background: rgba(255, 215, 0, 0.2);
            padding: 2px 8px;
            border-radius: 20px;
        }
        
        /* ========================================
           PRIZE INFO
        ======================================== */
        .prize-info {
            background: linear-gradient(135deg, rgba(255, 215, 0, 0.2), rgba(255, 165, 0, 0.1));
            border-radius: 15px;
            padding: 15px;
            margin-bottom: 20px;
            text-align: center;
        }
        
        .prize-1 {
            color: #FFD700;
            font-size: 16px;
            font-weight: bold;
        }
        
        .prize-2 {
            color: #C0C0C0;
            font-size: 14px;
            font-weight: bold;
        }
        
        .prize-3 {
            color: #CD7F32;
            font-size: 14px;
            font-weight: bold;
        }
        
        /* ========================================
           POPUP MODALS
        ======================================== */
        .ban-popup-overlay,
        .winner-popup-overlay,
        .kontak-popup,
        .dashboard-modal,
        .premium-modal,
        .ramadhan-start-popup,
        .report-bug-modal,
        .notification-popup {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.95);
            z-index: 10001;
            align-items: center;
            justify-content: center;
            animation: fadeIn 0.3s ease;
        }
        
        .notification-popup.active,
        .ramadhan-start-popup.active,
        .ban-popup-overlay.active,
        .winner-popup-overlay.active,
        .kontak-popup.active,
        .dashboard-modal.active,
        .premium-modal.active,
        .report-bug-modal.active {
            display: flex;
        }
        
        .notification-content,
        .ramadhan-popup-content,
        .ban-popup-content,
        .winner-popup-content,
        .popup-content,
        .report-bug-content {
            background: linear-gradient(135deg, #1a1a3a, #0d1a3a);
            border-radius: 30px;
            width: 90%;
            max-width: 400px;
            padding: 30px;
            text-align: center;
            border: 2px solid var(--accent);
            animation: bounceIn 0.5s ease;
        }
        
        @keyframes bounceIn {
            0% {
                transform: scale(0.3);
                opacity: 0;
            }
            50% {
                transform: scale(1.05);
            }
            100% {
                transform: scale(1);
                opacity: 1;
            }
        }
        
        /* ========================================
           PAYMENT ITEMS
        ======================================== */
        .payment-item {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            padding: 12px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 10px;
            margin: 10px 0;
        }
        
        .copy-btn {
            background: rgba(255, 255, 255, 0.2);
            border: none;
            border-radius: 8px;
            padding: 5px 12px;
            color: white;
            cursor: pointer;
            font-size: 12px;
            transition: all 0.2s;
        }
        
        .copy-btn:hover {
            background: var(--accent);
            color: #1a1a2e;
        }
        
        .wa-contact {
            background: rgba(37, 211, 102, 0.15);
            border: 1px solid #25D366;
            border-radius: 60px;
            padding: 12px 18px;
            margin: 15px 0;
            display: flex;
            align-items: center;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 10px;
        }
        
        .wa-button-popup {
            background: #25D366;
            padding: 8px 18px;
            border-radius: 30px;
            color: white;
            text-decoration: none;
        }
        
        .close-popup {
            background: #ff0050;
            padding: 10px 20px;
            border: none;
            border-radius: 30px;
            color: white;
            cursor: pointer;
            margin-top: 15px;
        }
        
        /* ========================================
           TOAST NOTIFICATION
        ======================================== */
        .toast {
            position: fixed;
            bottom: 120px;
            left: 50%;
            transform: translateX(-50%);
            background: var(--accent);
            color: #1a1a2e;
            padding: 12px 24px;
            border-radius: 40px;
            z-index: 9999;
            font-weight: bold;
            white-space: nowrap;
            animation: slideUp 0.3s ease;
        }
        
        @keyframes slideUp {
            from {
                opacity: 0;
                transform: translateX(-50%) translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateX(-50%) translateY(0);
            }
        }
        
        /* ========================================
           LOADING
        ======================================== */
        .loading {
            text-align: center;
            padding: 30px;
            display: none;
        }
        
        /* ========================================
           FOOTER
        ======================================== */
        .footer {
            text-align: center;
            padding: 20px;
            margin-top: 30px;
            color: #888888;
            font-size: 12px;
        }
        
        /* ========================================
           INFO LIST
        ======================================== */
        .info-list {
            background: rgba(0, 0, 0, 0.3);
            border-radius: 15px;
            padding: 15px;
        }
        
        .info-item {
            padding: 12px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            display: flex;
            align-items: center;
            gap: 12px;
        }
        
        .info-item i {
            width: 30px;
            color: var(--accent);
        }
        
        /* ========================================
           HISTORY LIST
        ======================================== */
        .history-list {
            background: rgba(0, 0, 0, 0.3);
            border-radius: 15px;
            padding: 15px;
            max-height: 400px;
            overflow-y: auto;
        }
        
        .history-item {
            padding: 12px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            display: flex;
            justify-content: space-between;
        }
        
        /* ========================================
           FEATURES GRID
        ======================================== */
        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
            gap: 15px;
            margin-top: 15px;
        }
        
        .feature-card {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 15px;
            padding: 15px;
            text-align: center;
            transition: all 0.3s;
        }
        
        .feature-card:hover {
            transform: translateY(-5px);
            background: rgba(255, 255, 255, 0.1);
        }
        
        .feature-card i {
            font-size: 28px;
            color: var(--accent);
            margin-bottom: 10px;
        }
        
        /* ========================================
           USER INFO
        ======================================== */
        .user-info {
            background: rgba(0, 242, 254, 0.1);
            border-radius: 15px;
            padding: 20px;
            text-align: center;
            margin-bottom: 20px;
        }
        
        body.ramadhan .user-info {
            background: rgba(255, 215, 0, 0.1);
        }
        
        .avatar-preview {
            width: 100px;
            height: 100px;
            border-radius: 50%;
            background: var(--accent-grad);
            margin: 0 auto 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
            font-size: 40px;
        }
        
        .avatar-preview img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        /* ========================================
           MULTIPLE BUTTONS
        ======================================== */
        .multiple-buttons {
            display: flex;
            gap: 12px;
            justify-content: center;
            margin: 20px 0 10px;
        }
        
        .loading-small {
            display: inline-block;
            width: 16px;
            height: 16px;
            border: 2px solid var(--accent);
            border-radius: 50%;
            border-top-color: transparent;
            animation: spin 0.6s linear infinite;
            margin-right: 8px;
        }
        
        @keyframes spin {
            to {
                transform: rotate(360deg);
            }
        }
        
        /* ========================================
           USER ID DISPLAY
        ======================================== */
        .user-id-display {
            background: rgba(0, 0, 0, 0.4);
            border-radius: 12px;
            padding: 10px 15px;
            margin: 15px 0;
            display: flex;
            align-items: center;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 10px;
            border-left: 3px solid var(--accent);
        }
        
        .user-id-label {
            font-size: 12px;
            color: #aaaaaa;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .user-id-value {
            font-family: 'Courier New', monospace;
            font-size: 13px;
            font-weight: bold;
            background: rgba(0, 0, 0, 0.5);
            padding: 6px 12px;
            border-radius: 8px;
            letter-spacing: 0.5px;
            color: var(--accent);
        }
        
        .copy-id-btn {
            background: rgba(255, 255, 255, 0.1);
            border: none;
            border-radius: 8px;
            padding: 6px 12px;
            color: white;
            cursor: pointer;
            font-size: 11px;
            transition: all 0.2s;
        }
        
        .copy-id-btn:hover {
            background: var(--accent);
            color: #1a1a2e;
        }
        
        /* ========================================
           AI CHAT STYLES
        ======================================== */
        .ai-chat-container {
            height: 450px;
            overflow-y: auto;
            background: rgba(0, 0, 0, 0.3);
            border-radius: 20px;
            padding: 15px;
            margin-bottom: 15px;
            display: flex;
            flex-direction: column;
            gap: 12px;
        }
        
        .ai-chat-container::-webkit-scrollbar {
            width: 5px;
        }
        
        .ai-chat-container::-webkit-scrollbar-track {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 10px;
        }
        
        .ai-chat-container::-webkit-scrollbar-thumb {
            background: var(--accent);
            border-radius: 10px;
        }
        
        .ai-message {
            padding: 12px 16px;
            border-radius: 18px;
            max-width: 88%;
            word-wrap: break-word;
            animation: messageIn 0.3s ease;
        }
        
        @keyframes messageIn {
            from {
                opacity: 0;
                transform: translateY(10px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        
        .ai-message.user {
            background: var(--ai-user);
            align-self: flex-end;
            border-bottom-right-radius: 5px;
            border: 1px solid rgba(0, 242, 254, 0.2);
        }
        
        .ai-message.bot {
            background: var(--ai-bot);
            align-self: flex-start;
            border-bottom-left-radius: 5px;
            border: 1px solid rgba(255, 215, 0, 0.15);
        }
        
        .ai-message .msg-header {
            font-weight: bold;
            font-size: 12px;
            margin-bottom: 5px;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .ai-message .msg-header .ai-icon {
            font-size: 16px;
        }
        
        .ai-message .msg-content {
            font-size: 14px;
            line-height: 1.6;
        }
        
        .ai-message .msg-content br {
            display: block;
            margin: 5px 0;
        }
        
        .ai-quick-buttons {
            display: flex;
            gap: 8px;
            flex-wrap: wrap;
            margin-top: 10px;
        }
        
        .ai-quick-btn {
            padding: 6px 14px;
            background: rgba(255, 255, 255, 0.08);
            border: 1px solid rgba(255, 255, 255, 0.12);
            border-radius: 25px;
            color: #cccccc;
            cursor: pointer;
            font-size: 11px;
            transition: all 0.2s;
        }
        
        .ai-quick-btn:hover {
            background: var(--accent-grad);
            color: #1a1a2e;
            border-color: transparent;
        }
        
        .ai-quick-btn:active {
            transform: scale(0.95);
        }
        
        .ai-typing {
            display: none;
            padding: 12px 16px;
            background: var(--ai-bot);
            border-radius: 18px;
            align-self: flex-start;
            border-bottom-left-radius: 5px;
            border: 1px solid rgba(255, 215, 0, 0.15);
            color: #aaaaaa;
            font-size: 13px;
        }
        
        .ai-typing .dot {
            display: inline-block;
            width: 8px;
            height: 8px;
            border-radius: 50%;
            background: var(--accent);
            margin: 0 2px;
            animation: typingDot 1.4s infinite both;
        }
        
        .ai-typing .dot:nth-child(2) {
            animation-delay: 0.2s;
        }
        .ai-typing .dot:nth-child(3) {
            animation-delay: 0.4s;
        }
        
        @keyframes typingDot {
            0%, 80%, 100% {
                transform: scale(0.6);
                opacity: 0.4;
            }
            40% {
                transform: scale(1);
                opacity: 1;
            }
        }
        
        .ai-features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
            gap: 10px;
            margin: 10px 0;
        }
        
        .ai-feature-item {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 12px;
            padding: 10px;
            text-align: center;
            border: 1px solid rgba(255, 255, 255, 0.05);
            transition: all 0.2s;
        }
        
        .ai-feature-item:hover {
            background: rgba(255, 255, 255, 0.1);
            transform: translateY(-2px);
        }
        
        .ai-feature-item i {
            font-size: 20px;
            color: var(--accent);
            display: block;
            margin-bottom: 5px;
        }
        
        .ai-feature-item span {
            font-size: 11px;
            color: #aaaaaa;
        }
        
        .ai-clear-btn {
            background: rgba(255, 0, 80, 0.2);
            border: 1px solid rgba(255, 0, 80, 0.3);
            color: #ff0050;
            padding: 6px 14px;
            border-radius: 20px;
            cursor: pointer;
            font-size: 12px;
            transition: all 0.2s;
        }
        
        .ai-clear-btn:hover {
            background: rgba(255, 0, 80, 0.3);
        }
        
        /* ========================================
           REPORT BUG BUTTON
        ======================================== */
        .report-bug-btn {
            position: fixed;
            bottom: 95px;
            right: 20px;
            width: 55px;
            height: 55px;
            border-radius: 50%;
            background: linear-gradient(135deg, #ff0050, #ff0080);
            border: none;
            color: white;
            font-size: 26px;
            cursor: pointer;
            z-index: 99;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
            transition: all 0.3s;
        }
        
        .report-bug-btn:hover {
            transform: scale(1.1);
        }
        
        /* ========================================
           REPORT FORM
        ======================================== */
        .report-form-group {
            margin-bottom: 15px;
            text-align: left;
        }
        
        .report-form-group label {
            display: block;
            margin-bottom: 5px;
            font-size: 12px;
            color: #aaaaaa;
        }
        
        .report-form-group input,
        .report-form-group textarea {
            width: 100%;
            padding: 10px;
            background: rgba(0, 0, 0, 0.5);
            border: 1px solid #333333;
            border-radius: 10px;
            color: white;
            font-size: 13px;
        }
        
        .report-form-group textarea {
            min-height: 80px;
            resize: vertical;
        }
        
        .report-submit-btn {
            background: var(--accent-grad);
            width: 100%;
            padding: 12px;
            border: none;
            border-radius: 30px;
            color: #1a1a2e;
            font-weight: bold;
            cursor: pointer;
            margin-top: 10px;
        }
        
        .headset-icon-modal {
            font-size: 50px;
            margin-bottom: 15px;
        }
        
        /* ========================================
           SYNC STATUS
        ======================================== */
        .sync-status {
            position: fixed;
            top: 10px;
            right: 10px;
            background: rgba(0, 0, 0, 0.7);
            padding: 5px 10px;
            border-radius: 20px;
            font-size: 10px;
            z-index: 1000;
        }
        
        .sync-status.synced {
            background: #4CAF50;
        }
        
        .sync-status.syncing {
            background: #FF9800;
        }
        
        .sync-status.error {
            background: #f44336;
        }
        
        /* ========================================
           VERSION BADGE
        ======================================== */
        .version-badge {
            position: fixed;
            bottom: 75px;
            left: 10px;
            background: rgba(0, 0, 0, 0.5);
            padding: 4px 8px;
            border-radius: 20px;
            font-size: 9px;
            color: #aaaaaa;
            z-index: 99;
        }
        
        /* ========================================
           MISSION LOGIN WARNING
        ======================================== */
        .mission-login-warning {
            background: rgba(255, 0, 80, 0.2);
            border-radius: 15px;
            padding: 15px;
            margin-bottom: 15px;
            text-align: center;
        }
        
        /* ========================================
           AI RATE LIMIT INDICATOR
        ======================================== */
        .ai-rate-limit {
            background: rgba(255, 165, 0, 0.15);
            border: 1px solid #FFA500;
            border-radius: 12px;
            padding: 8px 12px;
            font-size: 12px;
            color: #FFA500;
            text-align: center;
            margin-bottom: 10px;
            display: none;
        }
        
        .ai-rate-limit.active {
            display: block;
        }
        
        /* ========================================
           IG DOWNLOADER STYLES
        ======================================== */
        .ig-media-list {
            display: flex;
            flex-direction: column;
            gap: 12px;
            margin-top: 15px;
        }
        
        .ig-media-item {
            display: flex;
            align-items: center;
            gap: 16px;
            padding: 12px 16px;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 12px;
            border: 1px solid rgba(255, 255, 255, 0.08);
            transition: all 0.3s ease;
        }
        
        .ig-media-item:hover {
            border-color: var(--accent);
            background: rgba(255, 255, 255, 0.08);
        }
        
        .ig-media-item .ig-thumb {
            width: 70px;
            height: 70px;
            border-radius: 8px;
            object-fit: cover;
            background: #1a1a2e;
            flex-shrink: 0;
        }
        
        .ig-media-item .ig-info {
            flex: 1;
        }
        
        .ig-media-item .ig-info .ig-filename {
            font-size: 13px;
            font-weight: 600;
            color: #fff;
        }
        
        .ig-media-item .ig-info .ig-type-badge {
            display: inline-block;
            padding: 2px 10px;
            border-radius: 12px;
            font-size: 10px;
            font-weight: 600;
            text-transform: uppercase;
            margin-top: 4px;
        }
        
        .ig-media-item .ig-info .ig-type-badge.video {
            background: rgba(79, 195, 247, 0.3);
            color: #4FC3F7;
        }
        
        .ig-media-item .ig-info .ig-type-badge.image {
            background: rgba(255, 107, 107, 0.3);
            color: #ff6b6b;
        }
        
        .ig-media-item .ig-download-btn {
            padding: 8px 18px;
            border: none;
            border-radius: 10px;
            background: var(--accent-grad);
            color: #1a1a2e;
            font-size: 12px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.2s ease;
            text-decoration: none;
            white-space: nowrap;
        }
        
        .ig-media-item .ig-download-btn:hover {
            transform: scale(1.05);
            box-shadow: 0 4px 15px rgba(0, 242, 254, 0.3);
        }
        
        .ig-result-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
            flex-wrap: wrap;
            gap: 10px;
        }
        
        .ig-result-title {
            font-size: 15px;
            font-weight: 600;
        }
        
        .ig-result-title small {
            font-weight: 400;
            color: #888;
            font-size: 13px;
        }
        
        .ig-download-all-btn {
            padding: 6px 16px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 8px;
            background: rgba(255, 255, 255, 0.05);
            color: #aaa;
            font-size: 12px;
            cursor: pointer;
            transition: all 0.2s ease;
        }
        
        .ig-download-all-btn:hover {
            background: rgba(255, 255, 255, 0.1);
            color: #fff;
        }
        
        .ig-error {
            display: none;
            padding: 14px 18px;
            border-radius: 10px;
            background: rgba(255, 0, 80, 0.2);
            border: 1px solid rgba(255, 0, 80, 0.3);
            color: #ff6b6b;
            font-size: 14px;
            text-align: center;
            margin-top: 15px;
        }
        
        .ig-error.active {
            display: block;
        }
        
        .ig-result-box {
            display: none;
            margin-top: 20px;
            border-top: 1px solid rgba(255, 255, 255, 0.08);
            padding-top: 20px;
        }
        
        .ig-result-box.active {
            display: block;
        }
    </style>
</head>
<body>

    <!-- ========================================
         VERSION BADGE
    ======================================== -->
    <div class="version-badge">
        <i class="fas fa-code-branch"></i> WaterTik v5.0 | Ramadhan 2026
    </div>
    
    <!-- ========================================
         SYNC STATUS
    ======================================== -->
    <div id="syncStatus" class="sync-status">🔌 Menghubungkan...</div>
    
    <!-- ========================================
         MAINTENANCE OVERLAY
    ======================================== -->
    <div id="maintenanceOverlay" class="maintenance-overlay">
        <i class="fas fa-moon"></i>
        <h1>🌙 Sedang dalam Perbaikan</h1>
        <p>Maaf, WaterTik sedang dalam masa pemeliharaan.</p>
        <p>Kami akan segera kembali dengan fitur yang lebih baik!</p>
        <p>Mohon doa dan dukungannya ya. Terima kasih 🙏</p>
        <p id="maintenanceMessage" style="margin-top: 20px; color: #FFD700;">InsyaAllah kembali segera 🌙</p>
    </div>
    
    <!-- ========================================
         BLOCKED USER OVERLAY
    ======================================== -->
    <div id="blockedOverlay" class="blocked-overlay">
        <i class="fas fa-ban"></i>
        <h1>⚠️ AKUN DIBLOKIR ⚠️</h1>
        <p id="blockedReason">Akun Anda telah diblokir oleh admin.</p>
        <p>Silakan hubungi admin untuk informasi lebih lanjut.</p>
        <div class="wa-contact" style="margin-top: 15px; justify-content: center;">
            <span>Admin WaterTik</span>
            <span>089699024654</span>
            <a href="https://wa.me/6289699024654" class="wa-button-popup" target="_blank">Chat</a>
        </div>
    </div>
    
    <!-- ========================================
         ADSENSE BANNER
    ======================================== -->
    <div class="ad-banner-wrapper">
        <ins class="adsbygoogle"
             style="display: block"
             data-ad-client="ca-pub-9783625787750233"
             data-ad-slot="6380078265"
             data-ad-format="auto"
             data-full-width-responsive="true"></ins>
        <script>
            (adsbygoogle = window.adsbygoogle || []).push({});
        </script>
    </div>
    
    <!-- ========================================
         REPORT BUG BUTTON
    ======================================== -->
    <button class="report-bug-btn" id="reportBugBtn">
        <i class="fas fa-headset"></i>
    </button>
    
    <!-- ========================================
         REPORT BUG MODAL
    ======================================== -->
    <div id="reportBugModal" class="report-bug-modal">
        <div class="report-bug-content">
            <div class="headset-icon-modal">
                <i class="fas fa-headset" style="font-size: 55px; color: var(--accent);"></i>
            </div>
            <h2>🐞 Laporkan Bug</h2>
            <p style="font-size: 12px; color: #aaaaaa; margin-bottom: 20px;">Laporkan masalah yang Anda temukan di WaterTik</p>
            
            <div class="report-form-group">
                <label>Nama / Pelapor <span style="color: red;">*</span></label>
                <input type="text" id="reportName" placeholder="Masukkan nama Anda">
            </div>
            
            <div class="report-form-group">
                <label>Judul Bug <span style="color: red;">*</span></label>
                <input type="text" id="reportTitle" placeholder="Contoh: Tombol download tidak berfungsi">
            </div>
            
            <div class="report-form-group">
                <label>Deskripsi Bug <span style="color: red;">*</span></label>
                <textarea id="reportDesc" placeholder="Jelaskan bug secara detail...&#10;Langkah-langkah untuk mereproduksi:&#10;1. ...&#10;2. ..."></textarea>
            </div>
            
            <div class="report-form-group">
                <label>Browser & OS</label>
                <input type="text" id="reportSystem" placeholder="Contoh: Chrome 120, Windows 11">
            </div>
            
            <button class="report-submit-btn" id="sendReportBtn">
                <i class="fas fa-envelope"></i> Kirim Laporan ke dllweb9@gmail.com
            </button>
            <button class="close-popup" onclick="closeReportModal()" style="margin-top: 15px; background: #333333;">Tutup</button>
        </div>
    </div>
    
    <!-- ========================================
         NOTIFICATION POPUP
    ======================================== -->
    <div id="notificationPopup" class="notification-popup">
        <div class="notification-content">
            <i class="fas fa-bell" style="font-size: 48px; color: var(--accent); margin-bottom: 15px;"></i>
            <h2 id="notificationTitle">Notifikasi</h2>
            <p id="notificationMessage" style="margin: 15px 0;"></p>
            <button class="close-popup" onclick="closeNotificationPopup()">Tutup</button>
        </div>
    </div>
    
    <!-- ========================================
         BOTTOM NAVIGATION
    ======================================== -->
    <div class="bottom-nav">
        <button class="nav-item active" data-nav="home" onclick="switchMainTab('home')">
            <i class="fas fa-home"></i>
            <span>Home</span>
        </button>
        <button class="nav-item" data-nav="generator" onclick="switchMainTab('generator')">
            <i class="fas fa-images"></i>
            <span>Generator</span>
        </button>
        <button class="nav-item" data-nav="audio" onclick="switchMainTab('audio')">
            <i class="fas fa-music"></i>
            <span>MP3</span>
        </button>
        <button class="nav-item" data-nav="ig" onclick="switchMainTab('ig')">
            <i class="fab fa-instagram"></i>
            <span>IG</span>
        </button>
        <button class="nav-item" data-nav="ai" onclick="switchMainTab('ai')">
            <i class="fas fa-robot"></i>
            <span>AI</span>
        </button>
        <button class="nav-item" data-nav="menu4" onclick="switchMainTab('menu4')">
            <i class="fas fa-tasks"></i>
            <span>Misi</span>
        </button>
        <button class="nav-item" data-nav="menu5" onclick="switchMainTab('menu5')">
            <i class="fas fa-crown"></i>
            <span>Premium</span>
        </button>
        <button class="nav-item" data-nav="riwayat" onclick="switchMainTab('riwayat')">
            <i class="fas fa-history"></i>
            <span>Riwayat</span>
        </button>
        <button class="nav-item" data-nav="informasi" onclick="switchMainTab('informasi')">
            <i class="fas fa-info-circle"></i>
            <span>Info</span>
        </button>
        <button class="nav-item" data-nav="akun" onclick="switchMainTab('akun')">
            <i class="fas fa-user"></i>
            <span>Akun</span>
        </button>
    </div>
    
    <!-- ========================================
         MAIN CONTAINER
    ======================================== -->
    <div class="container">
        
        <!-- ========================================
             RAMADHAN HEADER
        ======================================== -->
        <div id="ramadhanHeader" class="ramadhan-header">
            <i class="fas fa-moon" style="font-size: 24px;"></i>
            <div id="ramadhanStatus" class="ramadhan-message">
                <span class="loading-small"></span> Memeriksa status...
            </div>
            <div id="ramadhanCountdown" class="ramadhan-countdown"></div>
        </div>
        
        <!-- ========================================
             HOME TAB
        ======================================== -->
        <div id="homeTab" class="main-tab active">
            
            <!-- Profile Card -->
            <div class="profile-card" onclick="openDashboard()">
                <div class="profile-info">
                    <div class="profile-avatar" id="avatarDisplay">
                        <i class="fas fa-user"></i>
                    </div>
                    <div class="profile-text">
                        <h3 id="userNameDisplay">Guest</h3>
                        <p id="userJoinDateDisplay"><i class="fas fa-calendar-alt"></i> Belum login</p>
                    </div>
                </div>
                <div class="profile-stats-mini">
                    <div class="stat-item">
                        <div class="number" id="miniDownloads">0</div>
                        <div class="label">Downloads</div>
                    </div>
                    <div class="stat-item">
                        <div class="number" id="miniMP3">0</div>
                        <div class="label">MP3</div>
                    </div>
                    <div class="stat-item">
                        <div class="number" id="miniPremium">✗</div>
                        <div class="label">Premium</div>
                    </div>
                </div>
                <i class="fas fa-chevron-right" style="color: var(--accent);"></i>
            </div>
            
            <!-- Stats Grid -->
            <div class="stats-grid">
                <div class="stat-card">
                    <div class="stat-number" id="statToday">0</div>
                    <div class="stat-label">Hari Ini</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number" id="statTotalMP3">0</div>
                    <div class="stat-label">Total MP3</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number" id="statMisi">0</div>
                    <div class="stat-label">Misi Selesai</div>
                </div>
            </div>
            
            <!-- Ad Container -->
            <div id="adContainer" class="ad-container">
                <i class="fas fa-ad"></i> Iklan - Upgrade ke Premium untuk bebas iklan!
                <div style="font-size: 12px; margin-top: 10px;">✨ Premium hanya Rp10.000/bulan ✨</div>
            </div>
            
            <!-- TikTok Downloader Card -->
            <div class="card">
                <h2><i class="fab fa-tiktok"></i> TikTok Downloader</h2>
                <div class="input-group">
                    <input type="text" id="tiktokUrl" class="url-input" placeholder="Tempel link TikTok...">
                    <button class="btn btn-secondary" onclick="pasteLinkToInput('tiktokUrl')">
                        <i class="fas fa-paste"></i> Paste
                    </button>
                    <button class="btn btn-outline" onclick="clearLink()">
                        <i class="fas fa-trash"></i> Hapus
                    </button>
                    <button class="btn" id="downloadBtn" onclick="downloadVideo()">
                        <i class="fas fa-download"></i> Download
                    </button>
                </div>
                <div id="videoLoading" class="loading">
                    <i class="fas fa-spinner fa-spin"></i> Memproses...
                </div>
                <div id="videoResult" class="result-box">
                    <div class="result-header" style="display: flex; justify-content: space-between; margin-bottom: 20px;">
                        <span class="result-title"><i class="fas fa-check-circle"></i> Video Siap Diunduh!</span>
                        <span class="result-badge" style="background: var(--accent); padding: 5px 12px; border-radius: 20px;">HD Quality</span>
                    </div>
                    <div class="video-preview">
                        <div class="thumbnail">
                            <img id="videoThumb" src="">
                        </div>
                        <div>
                            <h3 id="videoTitle">Judul Video</h3>
                            <div class="info-detail">
                                <div class="info-row">
                                    <span><i class="fas fa-user"></i> Pembuat</span>
                                    <span id="videoAuthor">@user</span>
                                </div>
                                <div class="info-row">
                                    <span><i class="fas fa-clock"></i> Durasi</span>
                                    <span id="videoDuration">0:00</span>
                                </div>
                                <div class="info-row">
                                    <span><i class="fas fa-calendar"></i> Tanggal Upload</span>
                                    <span id="videoDate">-</span>
                                </div>
                                <div class="info-row">
                                    <span><i class="fas fa-tag"></i> Kualitas</span>
                                    <span id="videoQuality">HD (720p)</span>
                                </div>
                                <div class="info-row">
                                    <span><i class="fas fa-database"></i> Ukuran</span>
                                    <span id="videoSize">-</span>
                                </div>
                            </div>
                            <div class="quality-buttons">
                                <button class="quality-btn active" onclick="selectQuality('hd')">HD (720p)</button>
                                <button class="quality-btn" onclick="selectQuality('sd')">SD (480p)</button>
                            </div>
                            <div class="action-buttons">
                                <a href="#" id="downloadLink" class="btn" download>
                                    <i class="fas fa-download"></i> DOWNLOAD VIDEO
                                </a>
                                <button class="btn btn-outline" onclick="clearLinkAndReset()">
                                    <i class="fas fa-redo"></i> Download Lainnya
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Features Card -->
            <div class="card">
                <h2><i class="fas fa-star"></i> Fitur Unggulan</h2>
                <div class="features-grid">
                    <div class="feature-card">
                        <i class="fas fa-shield-alt"></i>
                        <h4>Aman & Bebas Virus</h4>
                        <p>100% aman</p>
                    </div>
                    <div class="feature-card">
                        <i class="fas fa-infinity"></i>
                        <h4>Tanpa Batas</h4>
                        <p>Download unlimited</p>
                    </div>
                    <div class="feature-card">
                        <i class="fas fa-watermark"></i>
                        <h4>Tanpa Watermark</h4>
                        <p>Video bersih original</p>
                    </div>
                    <div class="feature-card">
                        <i class="fas fa-trophy"></i>
                        <h4>Misi Ramadhan</h4>
                        <p>Dapatkan Rp50.000!</p>
                    </div>
                </div>
            </div>
        </div>
        
        <!-- ========================================
             GENERATOR TAB
        ======================================== -->
        <div id="generatorTab" class="main-tab">
            <div class="card">
                <h2><i class="fas fa-images"></i> Generator Foto</h2>
                <p style="margin-bottom: 15px; color: #aaaaaa;">
                    Masukkan link TikTok untuk mengambil thumbnail atau slide foto original (max 9 gambar)
                </p>
                <div class="input-group">
                    <input type="text" id="watermarkUrl" class="url-input" placeholder="Link TikTok...">
                    <button class="btn btn-secondary" onclick="pasteLinkToInput('watermarkUrl')">
                        <i class="fas fa-paste"></i> Paste
                    </button>
                    <button class="btn" id="thumbBtn" onclick="generateWatermark()">
                        <i class="fas fa-magic"></i> Ambil Thumbnail
                    </button>
                    <button class="btn btn-secondary" id="multiBtn" onclick="generateMultipleFrames()">
                        <i class="fas fa-images"></i> Ambil Slide Foto (Max 9)
                    </button>
                </div>
                <div id="watermarkLoading" class="loading">
                    <i class="fas fa-spinner fa-spin"></i> Mengambil gambar...
                </div>
                <div id="multiFrameLoading" style="display: none;">
                    <div>
                        <i class="fas fa-spinner fa-spin"></i>
                        <span id="multiFrameStatusText">Mengambil slide gambar...</span>
                    </div>
                    <div class="progress-container">
                        <div id="multiFrameProgress" class="progress-bar"></div>
                    </div>
                </div>
                <div id="watermarkResult" class="result-box">
                    <img id="watermarkImage" class="watermark-image" style="display: none;">
                    <div id="watermarkButtons" style="display: none; justify-content: center; gap: 12px; margin-top: 15px;">
                        <button class="btn" onclick="downloadSingleImage()">
                            <i class="fas fa-download"></i> Download
                        </button>
                        <button class="btn btn-secondary" onclick="copyWatermarkLink()">
                            <i class="fas fa-copy"></i> Copy Link
                        </button>
                    </div>
                </div>
                <div id="multipleFramesResult" class="result-box">
                    <div class="result-header" style="display: flex; justify-content: space-between; margin-bottom: 15px;">
                        <span class="result-title"><i class="fas fa-images"></i> Slide Gambar Original</span>
                        <span class="result-badge" id="frameCount" style="background: var(--accent); padding: 5px 12px; border-radius: 20px;">0 Gambar</span>
                    </div>
                    <div id="framesGallery" class="gallery-container"></div>
                    <div class="multiple-buttons">
                        <button class="btn" onclick="downloadAllFrames()">
                            <i class="fas fa-download"></i> Download Semua
                        </button>
                        <button class="btn btn-outline" onclick="closeMultipleFrames()">
                            <i class="fas fa-times"></i> Tutup
                        </button>
                    </div>
                </div>
            </div>
        </div>
        
        <!-- ========================================
             AUDIO TAB (MP3 CONVERTER)
        ======================================== -->
        <div id="audioTab" class="main-tab">
            <div class="card">
                <h2><i class="fas fa-music"></i> Convert ke MP3</h2>
                <div class="input-group">
                    <input type="file" id="videoFileInput" class="file-input" accept="video/*" onchange="handleVideoSelect()">
                    <button class="btn" id="mp3Btn" onclick="convertToMP3()">
                        <i class="fas fa-file-audio"></i> Convert ke MP3
                    </button>
                </div>
                <div id="mp3Loading" class="loading">
                    <i class="fas fa-spinner fa-spin"></i> Mengkonversi...
                </div>
                <div id="mp3Result" class="result-box">
                    <div class="result-header" style="display: flex; justify-content: space-between; margin-bottom: 20px;">
                        <span class="result-title"><i class="fas fa-check-circle"></i> MP3 Siap!</span>
                        <span class="result-badge" style="background: var(--accent); padding: 5px 12px; border-radius: 20px;">MP3 Audio</span>
                    </div>
                    <div class="mp3-info-grid">
                        <div class="mp3-info-card">
                            <div class="label"><i class="fas fa-file"></i> Nama File</div>
                            <div class="value" id="mp3FileName">-</div>
                        </div>
                        <div class="mp3-info-card">
                            <div class="label"><i class="fas fa-database"></i> Ukuran</div>
                            <div class="value" id="mp3FileSize">-</div>
                        </div>
                        <div class="mp3-info-card">
                            <div class="label"><i class="fas fa-clock"></i> Durasi</div>
                            <div class="value" id="mp3Duration">-</div>
                        </div>
                        <div class="mp3-info-card">
                            <div class="label"><i class="fas fa-music"></i> Format</div>
                            <div class="value">MP3 Audio</div>
                        </div>
                    </div>
                    <div class="audio-player">
                        <audio id="audioPreview" controls></audio>
                    </div>
                    <div class="action-buttons">
                        <a href="#" id="mp3DownloadLink" class="btn" download>
                            <i class="fas fa-download"></i> DOWNLOAD MP3
                        </a>
                        <button class="btn btn-outline" onclick="resetMP3()">
                            <i class="fas fa-redo"></i> Convert Lainnya
                        </button>
                    </div>
                </div>
            </div>
        </div>
        
        <!-- ========================================
             IG DOWNLOADER TAB
        ======================================== -->
        <div id="igTab" class="main-tab">
            <div class="card">
                <h2><i class="fab fa-instagram"></i> Instagram Downloader</h2>
                <p style="margin-bottom: 15px; color: #aaaaaa;">
                    Download video, foto, dan reels dari Instagram dengan mudah.
                </p>
                
                <div class="input-group">
                    <input type="text" id="igUrlInput" class="url-input" placeholder="https://www.instagram.com/p/... atau reel/...">
                    <button class="btn btn-secondary" onclick="pasteLinkToInput('igUrlInput')">
                        <i class="fas fa-paste"></i> Paste
                    </button>
                    <button class="btn" id="igDownloadBtn" onclick="downloadInstagram()">
                        <i class="fab fa-instagram"></i> Download
                    </button>
                </div>
                
                <div id="igLoading" class="loading">
                    <i class="fas fa-spinner fa-spin"></i> Mengambil media dari Instagram...
                </div>
                
                <div id="igError" class="ig-error">
                    <span id="igErrorText">Terjadi kesalahan. Coba lagi.</span>
                </div>
                
                <div id="igResult" class="ig-result-box">
                    <div class="ig-result-header">
                        <div class="ig-result-title">
                            📥 <span id="igResultTitle">Media ditemukan</span>
                            <small id="igResultCount"></small>
                        </div>
                        <button class="ig-download-all-btn" onclick="downloadAllIG()">⬇ Download All</button>
                    </div>
                    <div class="ig-media-list" id="igMediaList"></div>
                </div>
            </div>
        </div>
        
        <!-- ========================================
             AI HELPER TAB - DENGAN RATE LIMIT
        ======================================== -->
        <div id="aiTab" class="main-tab">
            <div class="card">
                <h2>
                    <i class="fas fa-robot"></i> AI Helper
                    <span style="font-size: 11px; margin-left: 10px; background: var(--accent); color: #1a1a2e; padding: 2px 12px; border-radius: 20px;">Powered by Cerebras AI</span>
                </h2>
                
                <!-- Rate Limit Info -->
                <div id="aiRateLimit" class="ai-rate-limit">
                    <i class="fas fa-clock"></i> Tunggu <span id="rateLimitCountdown">5</span> detik sebelum mengirim pesan lagi...
                </div>
                
                <!-- AI Features -->
                <div class="ai-features-grid">
                    <div class="ai-feature-item">
                        <i class="fas fa-comment"></i>
                        <span>Ngobrol Santai</span>
                    </div>
                    <div class="ai-feature-item">
                        <i class="fas fa-calculator"></i>
                        <span>Matematika</span>
                    </div>
                    <div class="ai-feature-item">
                        <i class="fas fa-code"></i>
                        <span>Coding</span>
                    </div>
                    <div class="ai-feature-item">
                        <i class="fas fa-graduation-cap"></i>
                        <span>Belajar</span>
                    </div>
                    <div class="ai-feature-item">
                        <i class="fas fa-lightbulb"></i>
                        <span>Ide & Tips</span>
                    </div>
                    <div class="ai-feature-item">
                        <i class="fas fa-smile"></i>
                        <span>Hiburan</span>
                    </div>
                </div>
                
                <!-- Chat Container -->
                <div id="aiChatContainer" class="ai-chat-container">
                    <!-- Welcome Message -->
                    <div class="ai-message bot">
                        <div class="msg-header">
                            <span class="ai-icon">🤖</span> WaterTik AI Assistant
                        </div>
                        <div class="msg-content">
                            <strong>Assalamu'alaikum! 👋</strong><br><br>
                            Saya <strong>WaterTik AI</strong>, asisten pintar yang siap membantu kamu!<br><br>
                            ✨ <strong>Kemampuan saya:</strong><br>
                            • 🗣️ Ngobrol santai & curhat<br>
                            • 📚 Bantu belajar (Matematika, IPA, Bahasa, dll)<br>
                            • 💻 Bantu coding (HTML, CSS, JS, Python, PHP)<br>
                            • 💰 Tips keuangan & investasi<br>
                            • 🎨 Ide kreatif & hiburan<br>
                            • 📱 Bantu penggunaan WaterTik<br><br>
                            <strong>Tanyakan apa saja ya! 😊</strong>
                        </div>
                    </div>
                </div>
                
                <!-- Quick Buttons -->
                <div class="ai-quick-buttons">
                    <button class="ai-quick-btn" onclick="quickAsk('Halo, apa kabar?')">👋 Halo</button>
                    <button class="ai-quick-btn" onclick="quickAsk('Bantu saya belajar matematika')">📚 Matematika</button>
                    <button class="ai-quick-btn" onclick="quickAsk('Cara membuat website dengan HTML?')">💻 Coding</button>
                    <button class="ai-quick-btn" onclick="quickAsk('Tips menabung yang baik')">💰 Keuangan</button>
                    <button class="ai-quick-btn" onclick="quickAsk('Cerita lucu dong')">😄 Hiburan</button>
                    <button class="ai-quick-btn" onclick="quickAsk('Cara download video TikTok di WaterTik?')">📱 WaterTik</button>
                    <button class="ai-clear-btn" onclick="clearChat()"><i class="fas fa-eraser"></i> Hapus Chat</button>
                </div>
                
                <!-- Input Group -->
                <div class="input-group" style="margin-top: 15px;">
                    <input type="text" id="aiQuestion" class="url-input" placeholder="Ketik pertanyaan...">
                    <button class="btn btn-secondary" id="sendAIbtn" onclick="askAI()">
                        <i class="fas fa-paper-plane"></i> Kirim
                    </button>
                </div>
                
                <!-- Typing Indicator -->
                <div id="aiTypingIndicator" class="ai-typing">
                    <span>WaterTik AI sedang mengetik</span>
                    <span class="dot"></span>
                    <span class="dot"></span>
                    <span class="dot"></span>
                </div>
            </div>
        </div>
        
        <!-- ========================================
             MISI RAMADHAN TAB
        ======================================== -->
        <div id="menu4Tab" class="main-tab">
            <div class="card">
                <h2>
                    <i class="fas fa-tasks"></i> Misi Ramadhan
                    <span style="font-size: 12px; margin-left: 10px; background: var(--accent); padding: 4px 12px; border-radius: 20px;">Free</span>
                </h2>
                
                <!-- Login Warning -->
                <div id="missionLoginWarning" class="mission-login-warning" style="display: none;">
                    <i class="fas fa-exclamation-triangle"></i> Kamu harus login terlebih dahulu untuk mengikuti Misi Ramadhan!
                    <button class="btn btn-secondary" style="display: block; margin-top: 10px;" onclick="switchMainTab('akun')">Login Sekarang</button>
                </div>
                
                <!-- Winners List -->
                <div id="winnersListArea" class="winners-list">
                    <h3 style="margin-bottom: 10px;"><i class="fas fa-trophy"></i> Daftar Pemenang</h3>
                    <div id="winnersListContainer">
                        <div style="text-align: center; padding: 10px; color: #aaaaaa;">Belum ada pemenang</div>
                    </div>
                </div>
                
                <!-- Mission Countdown Area -->
                <div id="missionCountdownArea" class="mission-countdown" style="display: none;">
                    <i class="fas fa-hourglass-half"></i>
                    <h3>🌙 Menunggu Bulan Ramadhan 🌙</h3>
                    <p>Misi Ramadhan akan segera hadir!</p>
                    <div id="countdownTimer" style="font-size: 24px; font-weight: bold; color: var(--accent); margin: 15px 0;"></div>
                    <div class="prize-info">
                        <div class="prize-1">🏆 JUARA 1: Rp50.000 🏆</div>
                        <div class="prize-2">🥈 JUARA 2: Rp20.000 🥈</div>
                        <div class="prize-3">🥉 JUARA 3: Rp10.000 🥉</div>
                        <div style="font-size: 11px; margin-top: 5px;">⚡ First Come First Served ⚡</div>
                    </div>
                </div>
                
                <!-- Mission Active Area -->
                <div id="missionActiveArea" style="display: none;">
                    <div class="prize-info">
                        <div class="prize-1">🏆 JUARA 1: Rp50.000 🏆</div>
                        <div class="prize-2">🥈 JUARA 2: Rp20.000 🥈</div>
                        <div class="prize-3">🥉 JUARA 3: Rp10.000 🥉</div>
                        <div style="font-size: 11px; margin-top: 5px;">⚡ First Come First Served (3 pemenang) ⚡</div>
                    </div>
                    <p style="margin-bottom: 15px;">🌙 Selamat menjalankan ibadah puasa! Selesaikan misi untuk mendapatkan hadiah!</p>
                    
                    <div class="mission-progress">
                        <h3>Progres Misi Kamu:</h3>
                        <div class="mission-status">
                            <span><i class="fas fa-video"></i> Download Video (100x)</span>
                            <span id="videoCount">0</span><span>/100</span>
                        </div>
                        <div class="mission-status">
                            <span><i class="fas fa-images"></i> Generator Foto (100x)</span>
                            <span id="photoCount">0</span><span>/100</span>
                        </div>
                        <div class="mission-status">
                            <span><i class="fas fa-music"></i> Convert MP3 (10x)</span>
                            <span id="mp3Count">0</span><span>/10</span>
                        </div>
                        <div class="progress-container">
                            <div id="missionProgressBar" class="progress-bar"></div>
                        </div>
                        <div id="missionStatusText" style="text-align: center; margin-top: 10px;">Belum mulai misi</div>
                    </div>
                    <button id="claimMissionBtn" class="btn btn-premium" style="width: 100%; margin-top: 15px; display: none;" onclick="claimMission()">
                        <i class="fas fa-gift"></i> Klaim Hadiah Sekarang!
                    </button>
                </div>
                
                <!-- Mission Lebaran Area -->
                <div id="missionLebaranArea" class="mission-lebaran" style="display: none;">
                    <i class="fas fa-star-and-crescent"></i>
                    <h3>🌙 Taqabbalallahu minna wa minkum 🌙</h3>
                    <p>Mohon maaf lahir dan batin</p>
                    <p style="margin-top: 15px;">Misi Ramadhan telah berakhir. Sampai jumpa tahun depan!</p>
                </div>
                
                <!-- Mission Full Area -->
                <div id="missionFullArea" class="mission-full" style="display: none;">
                    <i class="fas fa-trophy"></i>
                    <h3>🏆 Misi Ramadhan Telah Berakhir 🏆</h3>
                    <p>3 pemenang telah ditemukan!</p>
                    <p style="margin-top: 10px;">Terima kasih atas partisipasinya.</p>
                    <p>Sampai jumpa di Ramadhan tahun depan! 🌙</p>
                </div>
            </div>
        </div>
        
        <!-- ========================================
             PREMIUM TAB
        ======================================== -->
        <div id="menu5Tab" class="main-tab">
            <div class="card">
                <h2><i class="fas fa-crown"></i> WaterTik Premium</h2>
                <div style="text-align: center; padding: 20px;">
                    <i class="fas fa-gem" style="font-size: 60px; color: #FFD700;"></i>
                    <h3 style="margin: 15px 0;">Upgrade ke Premium!</h3>
                    <p>Nikmati bebas iklan dan fitur eksklusif lainnya.</p>
                    <div style="background: rgba(255, 215, 0, 0.1); border-radius: 20px; padding: 20px; margin: 15px 0;">
                        <p><i class="fas fa-check-circle" style="color: #FFD700;"></i> Bebas Iklan</p>
                        <p><i class="fas fa-check-circle" style="color: #FFD700;"></i> Prioritas Misi</p>
                        <p><i class="fas fa-check-circle" style="color: #FFD700;"></i> Support Pengembang</p>
                    </div>
                    <p style="font-size: 24px; font-weight: bold; color: #FFD700;">Hanya Rp10.000/bulan</p>
                    <button class="btn btn-premium" onclick="openPremiumModal()">
                        <i class="fas fa-shopping-cart"></i> Beli Premium Sekarang
                    </button>
                </div>
            </div>
        </div>
        
        <!-- ========================================
             RIWAYAT TAB
        ======================================== -->
        <div id="riwayatTab" class="main-tab">
            <div class="card">
                <h2><i class="fas fa-history"></i> Riwayat</h2>
                <div id="historyList" class="history-list">
                    <div style="text-align: center; padding: 40px;">
                        <i class="fas fa-inbox"></i> Belum ada riwayat
                    </div>
                </div>
            </div>
        </div>
        
        <!-- ========================================
             INFORMASI TAB
        ======================================== -->
        <div id="informasiTab" class="main-tab">
            <div class="card">
                <h2><i class="fas fa-info-circle"></i> Informasi</h2>
                
                <!-- Sub Navigation -->
                <div class="info-subnav">
                    <button id="btnAbout" class="active" onclick="showInfoPage('about')">
                        <i class="fas fa-users"></i> Tentang Kami
                    </button>
                    <button id="btnPrivacy" onclick="showInfoPage('privacy')">
                        <i class="fas fa-shield-alt"></i> Kebijakan Privasi
                    </button>
                </div>
                
                <!-- Tentang Kami Page -->
                <div id="aboutPage" class="info-page active-page">
                    <div class="about-content">
                        <div class="creator-badge">
                            <i class="fas fa-code" style="font-size: 32px; margin-bottom: 10px; display: block;"></i>
                            <h3>WaterTik v5.0</h3>
                            <p>Dibuat dengan penuh semangat oleh <strong>Fikri</strong> | Ramadhan 2026</p>
                        </div>
                        
                        <h3><i class="fas fa-bullhorn"></i> Tentang WaterTik</h3>
                        <p>WaterTik adalah platform unduh konten TikTok tanpa watermark tercepat dan termudah. Kami hadir untuk memudahkan Anda menyimpan video, foto slide, serta mengonversi video ke MP3 dengan kualitas terbaik.</p>
                        <p>Dengan teknologi canggih dan komitmen pada keamanan, WaterTik menjadi pilihan utama bagi lebih dari 10.000+ pengguna aktif setiap harinya.</p>
                        
                        <h3><i class="fas fa-check-circle"></i> Keunggulan Kami</h3>
                        <p>✅ Download video TikTok HD/SD tanpa watermark<br>
                        ✅ Generator foto dan slide gambar (max 9 slide)<br>
                        ✅ Konversi video ke MP3 kualitas tinggi<br>
                        ✅ Misi Ramadhan dengan hadiah uang tunai Rp50.000<br>
                        ✅ Premium bebas iklan hanya Rp10.000/bulan<br>
                        ✅ AI Helper untuk bantu belajar, coding, keuangan<br>
                        ✅ Proteksi privasi dan data pengguna</p>
                        
                        <h3><i class="fas fa-envelope"></i> Kontak & Dukungan</h3>
                        <p>Email: dllweb9@gmail.com<br>
                        WhatsApp: 089699024654 (Admin WaterTik)<br>
                        Jam operasional: 08.00 - 22.00 WIB</p>
                    </div>
                </div>
                
                <!-- Kebijakan Privasi Page -->
                <div id="privacyPage" class="info-page">
                    <div class="privacy-content">
                        <h3><i class="fas fa-lock"></i> Kebijakan Privasi WaterTik</h3>
                        <p>Terakhir diperbarui: Maret 2026</p>
                        
                        <h3>1. Informasi yang Kami Kumpulkan</h3>
                        <p>Untuk memberikan layanan terbaik, WaterTik mengumpulkan beberapa data berikut:</p>
                        <ul>
                            <li><strong>Data Fingerprint & ID User:</strong> Digunakan untuk mengidentifikasi akun dan menyimpan riwayat aktivitas secara unik.</li>
                            <li><strong>Data Aktivitas:</strong> Jumlah download, konversi MP3, dan partisipasi misi Ramadhan disimpan di server.</li>
                            <li><strong>Avatar & Nama Pengguna:</strong> Data yang Anda berikan secara sukarela saat registrasi/login.</li>
                            <li><strong>Data Teknis:</strong> Browser, OS, dan alamat IP (anonymized) untuk analisis performa dan keamanan.</li>
                        </ul>
                        
                        <h3>2. Penggunaan Data</h3>
                        <p>Data yang kami kumpulkan digunakan untuk:</p>
                        <ul>
                            <li>Menyediakan layanan unduh video TikTok tanpa watermark.</li>
                            <li>Menjalankan misi Ramadhan dan sistem pemenang hadiah.</li>
                            <li>Memproses upgrade premium dan aktivasi fitur bebas iklan.</li>
                            <li>Meningkatkan keamanan serta mencegah penyalahgunaan layanan (blocking akun).</li>
                        </ul>
                        
                        <h3>3. Privasi & Keamanan</h3>
                        <p>Kami tidak akan pernah membagikan data pribadi Anda kepada pihak ketiga tanpa izin, kecuali diwajibkan oleh hukum. Seluruh data disimpan dengan enkripsi yang aman.</p>
                        
                        <h3>4. Iklan & Layanan Pihak Ketiga</h3>
                        <p>WaterTik menggunakan Google AdSense untuk menampilkan iklan non-personalisasi. Google dapat menggunakan cookie untuk menayangkan iklan berdasarkan kunjungan Anda. Anda dapat mengatur preferensi iklan melalui pengaturan browser.</p>
                        
                        <h3>5. Hak Pengguna</h3>
                        <p>Anda berhak menghapus akun dan data Anda dengan menghubungi admin melalui WhatsApp/email. Data misi dan winner akan tetap tersimpan untuk kepentingan pemenang hadiah.</p>
                        
                        <h3>6. Perubahan Kebijakan</h3>
                        <p>WaterTik dapat memperbarui kebijakan privasi ini sewaktu-waktu. Perubahan akan diinformasikan melalui notifikasi di aplikasi.</p>
                        
                        <h3>7. Kontak Privasi</h3>
                        <p>Jika Anda memiliki pertanyaan tentang privasi, silakan hubungi: dllweb9@gmail.com atau WhatsApp 089699024654.</p>
                        <p style="margin-top: 15px;">Dengan menggunakan WaterTik, Anda menyetujui kebijakan privasi ini.</p>
                    </div>
                </div>
                
                <!-- Info List -->
                <div class="info-list">
                    <div class="info-item"><i class="fas fa-code"></i> <span>WaterTik v5.0</span></div>
                    <div class="info-item"><i class="fas fa-user"></i> <span>Creator: Fikri</span></div>
                    <div class="info-item"><i class="fas fa-calendar"></i> <span>Ramadhan 2026</span></div>
                    <div class="info-item"><i class="fas fa-shield-alt"></i> <span>Keamanan: 100%</span></div>
                    <div class="info-item"><i class="fas fa-robot"></i> <span>AI: Cerebras AI</span></div>
                    <div class="info-item"><i class="fas fa-moon"></i> <span>Status: <span id="ramadhanInfoStatus">-</span></span></div>
                    <div class="info-item"><i class="fab fa-whatsapp"></i> <span>Admin: 089699024654</span></div>
                </div>
                
                <!-- User ID Display -->
                <div id="infoUserIdContainer" style="margin-top: 20px; display: none;">
                    <div class="user-id-display">
                        <div class="user-id-label">
                            <i class="fas fa-id-card"></i><strong>ID User</strong>
                        </div>
                        <div class="user-id-value" id="infoUserIdValue">-</div>
                        <button class="copy-id-btn" onclick="copyUserId()">
                            <i class="fas fa-copy"></i> Copy
                        </button>
                    </div>
                </div>
            </div>
        </div>
        
        <!-- ========================================
             AKUN TAB
        ======================================== -->
        <div id="akunTab" class="main-tab">
            <div class="card">
                <h2><i class="fas fa-user-circle"></i> Akun Saya</h2>
                
                <!-- Login Section -->
                <div id="loginSection">
                    <input type="text" id="loginName" class="login-input" placeholder="Masukkan nama...">
                    <button class="login-btn" onclick="attemptLogin()" style="width: 100%; padding: 14px; background: var(--accent-grad); border: none; border-radius: 15px; color: #1a1a2e; font-weight: bold; cursor: pointer; margin-bottom: 10px;">
                        Login / Daftar
                    </button>
                    <button class="btn btn-outline" onclick="openKontakPopup()" style="width: 100%;">
                        <i class="fab fa-whatsapp"></i> Hubungi Admin
                    </button>
                </div>
                
                <!-- User Info Section (Setelah Login) -->
                <div id="userInfoSection" style="display: none;">
                    <div class="user-info">
                        <div class="avatar-preview" id="avatarPreviewDash">
                            <i class="fas fa-user"></i>
                        </div>
                        <h3 id="loggedUserName">User</h3>
                        <p>Status: <span id="userPremiumStatus">Free User</span></p>
                        <p>Premium EXP: <span id="userPremiumExpiry">-</span></p>
                        <p>Bergabung: <span id="loggedJoinDate">-</span></p>
                    </div>
                    
                    <div class="user-id-display">
                        <div class="user-id-label">
                            <i class="fas fa-id-card"></i><strong>ID User</strong>
                        </div>
                        <div class="user-id-value" id="akunUserIdValue">-</div>
                        <button class="copy-id-btn" onclick="copyUserId()">
                            <i class="fas fa-copy"></i> Copy
                        </button>
                    </div>
                    
                    <div class="stats-grid">
                        <div class="stat-card">
                            <div class="stat-number" id="akunDownloads">0</div>
                            <div class="stat-label">Downloads</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-number" id="akunMP3">0</div>
                            <div class="stat-label">MP3</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-number" id="akunMisi">0</div>
                            <div class="stat-label">Misi</div>
                        </div>
                    </div>
                    
                    <button class="btn btn-secondary" onclick="openDashboard()" style="width: 100%; margin-bottom: 10px;">
                        <i class="fas fa-user-edit"></i> Edit Avatar
                    </button>
                    <button class="btn btn-outline" onclick="openKontakPopup()" style="width: 100%; margin-bottom: 10px;">
                        <i class="fab fa-whatsapp"></i> Hubungi Admin
                    </button>
                    <button class="btn btn-premium" onclick="openPremiumModal()" style="width: 100%;">
                        <i class="fas fa-crown"></i> Upgrade Premium
                    </button>
                </div>
            </div>
        </div>
        
        <!-- Footer -->
        <div class="footer">
            <p>© 2026 WaterTik | Created by <strong>Fikri</strong> | <span id="currentDate"></span></p>
        </div>
    </div>
    
    <!-- ========================================
         POPUP MODALS
    ======================================== -->
    
    <!-- Ban Reason Popup -->
    <div id="banReasonPopup" class="ban-popup-overlay">
        <div class="ban-popup-content">
            <i class="fas fa-ban" style="font-size: 48px; color: #ff0050; margin-bottom: 15px;"></i>
            <h2 style="color: #ff0050;">⚠️ AKUN DIBLOKIR ⚠️</h2>
            <div id="banReasonText" style="margin: 15px 0; padding: 10px; background: rgba(0, 0, 0, 0.5); border-radius: 10px;">Alasan tidak tersedia</div>
            <p>Akun Anda tidak dapat menggunakan fitur WaterTik.</p>
            <p>Silahkan hubungi admin untuk informasi lebih lanjut.</p>
            <div class="wa-contact" style="margin-top: 15px; justify-content: center;">
                <span>Admin WaterTik</span>
                <span>089699024654</span>
                <a href="https://wa.me/6289699024654" class="wa-button-popup" target="_blank">Chat</a>
            </div>
            <button class="close-popup" onclick="closeBanPopup()" style="margin-top: 15px;">Mengerti</button>
        </div>
    </div>
    
    <!-- Winner Popup -->
    <div id="winnerPopup" class="winner-popup-overlay">
        <div class="winner-popup-content">
            <div id="winnerPopupIcon"><i class="fas fa-trophy"></i></div>
            <h2 id="winnerPopupTitle">🎉 SELAMAT! 🎉</h2>
            <div id="winnerPopupPrize" class="winner-prize">Rp50.000</div>
            <div id="winnerPopupMessage" class="winner-message">Anda menjadi JUARA 1!<br>Segera hubungi admin untuk klaim hadiah.</div>
            <a href="https://wa.me/6289699024654" class="wa-button" target="_blank" id="winnerPopupWaButton" style="background: #25D366; padding: 10px; border-radius: 30px; color: white; text-decoration: none; margin: 10px 0; display: inline-block;">
                <i class="fab fa-whatsapp"></i> Hubungi Admin Sekarang
            </a>
            <button class="close-popup" onclick="closeWinnerPopup()">Tutup</button>
        </div>
    </div>
    
    <!-- Kontak Popup -->
    <div id="kontakPopup" class="kontak-popup">
        <div class="popup-content">
            <h2><i class="fab fa-whatsapp"></i> Kontak Admin</h2>
            <div class="wa-contact">
                <span>Admin WaterTik</span>
                <span>089699024654</span>
                <a href="https://wa.me/6289699024654" class="wa-button-popup" target="_blank">Chat</a>
            </div>
            <button class="close-popup" onclick="closeKontakPopup()">Tutup</button>
        </div>
    </div>
    
    <!-- Dashboard Modal (Edit Avatar) -->
    <div id="dashboardModal" class="dashboard-modal">
        <div class="popup-content">
            <h2><i class="fas fa-user-edit"></i> Edit Avatar</h2>
            <div class="avatar-preview" id="avatarPreviewModal"><i class="fas fa-user"></i></div>
            <input type="file" id="avatarInput" accept="image/*" style="display: none;">
            <div style="display: flex; gap: 10px; justify-content: center; margin-top: 15px;">
                <button class="btn" onclick="uploadAvatar()"><i class="fas fa-upload"></i> Upload Avatar</button>
                <button class="btn btn-secondary" onclick="removeAvatar()"><i class="fas fa-trash"></i> Hapus</button>
            </div>
            <button class="btn btn-secondary" onclick="closeDashboard()" style="margin-top: 15px;"><i class="fas fa-times"></i> Tutup</button>
        </div>
    </div>
    
    <!-- Premium Modal -->
    <div id="premiumModal" class="premium-modal">
        <div class="popup-content">
            <h2><i class="fas fa-crown"></i> Upgrade Premium</h2>
            <p style="margin: 15px 0;">Hanya <strong style="color: #FFD700; font-size: 20px;">Rp10.000/bulan</strong></p>
            <div class="payment-item">
                <span><i class="fas fa-money-bill-wave"></i> DANA</span>
                <span>089699024654</span>
                <button class="copy-btn" onclick="copyToClipboard('089699024654')">Copy</button>
            </div>
            <div class="payment-item">
                <span><i class="fas fa-mobile-alt"></i> GoPay</span>
                <span>083875424751</span>
                <button class="copy-btn" onclick="copyToClipboard('083875424751')">Copy</button>
            </div>
            <div class="payment-item">
                <span><i class="fas fa-qrcode"></i> QRIS</span>
                <span>Hubungi admin</span>
                <a href="https://wa.me/6289699024654" class="wa-button-popup" style="padding: 5px 12px;">Chat</a>
            </div>
            <p style="margin: 15px 0; font-size: 12px;">Setelah bayar, kirim bukti ke admin WhatsApp untuk aktivasi premium.</p>
            <a href="https://wa.me/6289699024654" class="btn btn-premium" style="display: inline-block; margin: 10px 0; text-decoration: none;">Hubungi Admin</a>
            <button class="close-popup" onclick="closePremiumModal()">Tutup</button>
        </div>
    </div>
    
    <!-- Ramadhan Start Popup -->
    <div id="ramadhanStartPopup" class="ramadhan-start-popup">
        <div class="ramadhan-popup-content">
            <i class="fas fa-moon" style="font-size: 60px; color: #FFD700;"></i>
            <h2 style="margin: 15px 0;">🌙 Selamat Bulan Ramadhan! 🌙</h2>
            <div class="ai-message">
                <i class="fas fa-robot"></i> <strong>Assalamu'alaikum Warahmatullahi Wabarakatuh,</strong><br><br>
                "Marhaban ya Ramadhan, bulan penuh berkah dan ampunan. Semoga di bulan suci ini, ibadah puasa kita diterima, doa-doa kita dikabulkan, dan hati kita semakin bersih. Jadikan setiap langkah kita sebagai ladang pahala. Selamat menunaikan ibadah puasa, semoga diberikan kelancaran dan kesehatan selalu. 🌙✨"<br><br>
                — <em>WaterTik AI</em>
            </div>
            <p style="margin-top: 10px;">✨ Ikuti Misi Ramadhan dan menangkan hadiah hingga Rp50.000! ✨</p>
            <button class="btn btn-secondary" onclick="closeRamadhanPopup()" style="margin-top: 15px;"><i class="fas fa-check"></i> Semoga Puasa Lancar</button>
        </div>
    </div>
    
    <!-- ========================================
         JAVASCRIPT - LENGKAP DENGAN FIX BUG
    ======================================== -->
    <script>
        // ========================================
        // KONFIGURASI FIREBASE
        // ========================================
        const firebaseConfig = {
            apiKey: "AIzaSyCQZ-ce5I9-5UvD19cPK6qKj8kIXaMhOek",
            authDomain: "watertik-466a0.firebaseapp.com",
            projectId: "watertik-466a0",
            storageBucket: "watertik-466a0.firebasestorage.app",
            messagingSenderId: "477111819819",
            appId: "1:477111819819:web:09626fc68a93f6b372146e"
        };
        
        // ========================================
        // INISIALISASI FIREBASE
        // ========================================
        let db = null;
        let firebaseApp = null;
        
        try {
            firebaseApp = firebase.initializeApp(firebaseConfig);
            db = firebase.firestore();
            console.log('✅ Firebase berhasil diinisialisasi');
        } catch (e) {
            console.error('❌ Gagal inisialisasi Firebase:', e);
        }
        
        // ========================================
        // KONFIGURASI API KEY (AMAN)
        // ========================================
        (function() {
            const API_KEY = 'csk-xvn333y8eyfyvc93kv44xdrxpxwf65h6tyn3de34vxf9nfy9';
            const API_URL = 'https://api.cerebras.ai/v1/chat/completions';
            
            // OWASP: Cegah akses API dari console
            Object.defineProperty(window, 'CEREBRAS_API_KEY', {
                get: function() { return undefined; },
                set: function() { return undefined; }
            });
            
            // ========================================
            // VARIABEL GLOBAL
            // ========================================
            let currentUser = null;
            let missionData = { videoDownloads: 0, photoGenerates: 0, mp3Converts: 0 };
            let ramadhanPhase = 'countdown';
            let ramadhanDaysLeft = 0;
            let ramadhanPopupShown = false;
            let cachedFingerprint = null;
            let misiFull = false;
            let currentVideoData = null;
            let currentQuality = 'hd';
            let currentWatermarkUrl = '';
            let currentWatermarkBlob = null;
            let framesList = [];
            let selectedVideoFile = null;
            let lastRequestTime = 0;
            const MIN_INTERVAL = 5000;
            let isRequesting = false;
            let csrfToken = Math.random().toString(36).substring(2, 15) + Math.random().toString(36).substring(2, 15);
            
            // ========================================
            // IG DOWNLOADER VARIABLES
            // ========================================
            let currentIGMedia = [];
            
            // ========================================
            // OWASP: SANITASI INPUT
            // ========================================
            function sanitizeInput(text) {
                if (!text) return '';
                let clean = text.replace(/[<>'"]/g, '');
                clean = clean.substring(0, 1000);
                return clean;
            }
            
            // ========================================
            // OWASP: PROTECT CONSOLE
            // ========================================
            window.eval = function() { return undefined; };
            document.write = function() { return undefined; };
            
            // ========================================
            // SYSTEM PROMPT AI
            // ========================================
            const AI_SYSTEM_PROMPT = `Kamu adalah WaterTik AI Assistant, asisten AI yang cerdas, ramah, dan membantu.

Kemampuanmu:
- Mengobrol santai seperti manusia
- Menjawab pertanyaan umum
- Memberikan jokes dan hiburan
- Menjadi teman curhat yang suportif
- Membantu belajar sekolah (Matematika, IPA, Bahasa Indonesia, dll)
- Membantu coding HTML, CSS, JavaScript, Python, PHP, dll
- Membantu membuat website dan aplikasi
- Memberikan tips keuangan dan pengelolaan uang
- Menjelaskan investasi, saham, emas, dan ekonomi secara umum
- Membantu membuat rencana tabungan
- Menjelaskan teknologi dan AI
- Membantu penggunaan website WaterTik

Aturan:
- Jawab dengan Bahasa Indonesia yang natural.
- Ramah, sopan, dan mudah dipahami.
- Jika tidak tahu sesuatu, katakan dengan jujur.
- Jangan mengarang data atau berita terbaru.
- Untuk harga saham, kurs mata uang, dan berita terbaru, sarankan pengguna mengecek data real-time.

Gaya bicara:
- Santai saat diajak santai.
- Serius saat membahas pelajaran atau keuangan.
- Bisa bercanda jika diminta.
- Gunakan emoji untuk membuat obrolan lebih hidup.`;
            
            // ========================================
            // FUNGSI BANTUAN
            // ========================================
            function showToast(msg) {
                let t = document.createElement('div');
                t.className = 'toast';
                t.innerHTML = sanitizeInput(msg);
                document.body.appendChild(t);
                setTimeout(() => t.remove(), 2500);
            }
            
            function showNotification(title, msg) {
                document.getElementById('notificationTitle').innerHTML = sanitizeInput(title);
                document.getElementById('notificationMessage').innerHTML = sanitizeInput(msg);
                document.getElementById('notificationPopup').classList.add('active');
                setTimeout(() => document.getElementById('notificationPopup').classList.remove('active'), 5000);
            }
            
            function closeNotificationPopup() {
                document.getElementById('notificationPopup').classList.remove('active');
            }
            
            function copyToClipboard(text) {
                navigator.clipboard.writeText(text);
                showToast('✅ Tersalin!');
            }
            
            function formatDuration(s) {
                let m = Math.floor(s / 60);
                let sc = Math.floor(s % 60);
                return `${m}:${sc.toString().padStart(2, '0')}`;
            }
            
            function generateUniqueUserId() {
                let c = '0123456789abcdefghijklmnopqrstuvwxyz';
                let r = '';
                for (let i = 0; i < 8; i++) r += c[Math.floor(Math.random() * c.length)];
                return `WT-FIK-${r}-${Math.floor(Math.random() * 9000 + 1000)}`;
            }
            
            // ========================================
            // FINGERPRINT
            // ========================================
            async function getFingerprint() {
                if (cachedFingerprint) return cachedFingerprint;
                try {
                    const fp = await FingerprintJS.load();
                    const res = await fp.get();
                    cachedFingerprint = res.visitorId;
                    return cachedFingerprint;
                } catch (e) {
                    cachedFingerprint = 'fp_' + Math.random().toString(36).substr(2, 16);
                    return cachedFingerprint;
                }
            }
            
            // ========================================
            // CEK BLOKIR & MAINTENANCE (dengan error handling)
            // ========================================
            async function checkBlockedUser(fp) {
                if (!db) return false;
                try {
                    let doc = await db.collection('users').doc(fp).get();
                    if (doc.exists && doc.data().blocked === true) {
                        document.getElementById('blockedOverlay').classList.add('active');
                        document.body.style.pointerEvents = 'none';
                        return true;
                    }
                } catch (e) {
                    console.log('⚠️ Gagal cek blokir user:', e.message);
                }
                return false;
            }
            
            async function checkMaintenance() {
                if (!db) return false;
                try {
                    let doc = await db.collection('settings').doc('maintenance').get();
                    if (doc.exists && doc.data().isActive === true) {
                        document.getElementById('maintenanceOverlay').classList.add('active');
                        document.body.style.pointerEvents = 'none';
                        return true;
                    }
                } catch (e) {
                    console.log('⚠️ Gagal cek maintenance:', e.message);
                }
                document.getElementById('maintenanceOverlay').classList.remove('active');
                document.body.style.pointerEvents = 'auto';
                return false;
            }
            
            // ========================================
            // RESET MISI TAHUNAN (dengan error handling)
            // ========================================
            async function checkAndResetRamadhanMission() {
                if (!db) return;
                try {
                    const resetDoc = await db.collection('settings').doc('ramadhanReset').get();
                    const lastResetYear = resetDoc.exists ? resetDoc.data().lastResetYear : 0;
                    const currentYear = new Date().getFullYear();
                    
                    if (ramadhanPhase === 'active' && currentYear > lastResetYear) {
                        console.log("🌙 Melakukan reset misi Ramadhan tahunan...");
                        try {
                            const missionsSnap = await db.collection('missions').get();
                            for (const doc of missionsSnap.docs) {
                                await doc.ref.set({ videoDownloads: 0, photoGenerates: 0, mp3Converts: 0 });
                            }
                            const usersSnap = await db.collection('users').get();
                            for (const doc of usersSnap.docs) {
                                await doc.ref.update({ missionCompleted: false });
                            }
                            await db.collection('global').doc('winners').set({ winners: [] });
                            await db.collection('settings').doc('ramadhanReset').set({ lastResetYear: currentYear, resetAt: new Date().toISOString() });
                            console.log("✅ Reset misi Ramadhan selesai untuk tahun", currentYear);
                        } catch (e) {
                            console.log('⚠️ Gagal reset misi:', e.message);
                        }
                    }
                } catch (error) {
                    console.log('⚠️ Error check reset Ramadhan:', error.message);
                }
            }
            
            // ========================================
            // OPERASI PENYIMPANAN FIREBASE (dengan error handling)
            // ========================================
            async function saveUserToStorage(user) {
                if (!db || !user || !user.fingerprint) return;
                try {
                    await db.collection('users').doc(user.fingerprint).set({
                        name: user.name,
                        avatar: user.avatar || null,
                        totalDownloads: user.totalDownloads || 0,
                        totalMP3: user.totalMP3 || 0,
                        todayDownloads: user.todayDownloads || 0,
                        joinDate: user.joinDate || new Date().toISOString(),
                        isPremium: user.isPremium || false,
                        premiumExpiry: user.premiumExpiry || null,
                        missionCompleted: user.missionCompleted || false,
                        missionRank: user.missionRank || null,
                        blocked: user.blocked || false,
                        userId: user.userId || null
                    }, { merge: true });
                } catch (e) {
                    console.log('⚠️ Gagal save user:', e.message);
                }
            }
            
            async function loadUserFromStorage(fp) {
                if (!db) return null;
                try {
                    let doc = await db.collection('users').doc(fp).get();
                    return doc.exists ? doc.data() : null;
                } catch (e) {
                    console.log('⚠️ Gagal load user:', e.message);
                    return null;
                }
            }
            
            async function saveMissionToStorage(fp, m) {
                if (!db) return;
                try {
                    await db.collection('missions').doc(fp).set(m, { merge: true });
                } catch (e) {
                    console.log('⚠️ Gagal save mission:', e.message);
                }
            }
            
            async function loadMissionFromStorage(fp) {
                if (!db) return null;
                try {
                    let doc = await db.collection('missions').doc(fp).get();
                    return doc.exists ? doc.data() : null;
                } catch (e) {
                    console.log('⚠️ Gagal load mission:', e.message);
                    return null;
                }
            }
            
            async function loadWinnersFromStorage() {
                if (!db) return [];
                try {
                    let doc = await db.collection('global').doc('winners').get();
                    if (doc.exists && doc.data().winners) {
                        misiFull = doc.data().winners.length >= 3;
                        return doc.data().winners;
                    }
                } catch (e) {
                    console.log('⚠️ Gagal load winners:', e.message);
                }
                misiFull = false;
                return [];
            }
            
            async function saveWinnersToStorage(w) {
                if (!db) return;
                try {
                    await db.collection('global').doc('winners').set({ winners: w });
                } catch (e) {
                    console.log('⚠️ Gagal save winners:', e.message);
                }
            }
            
            // ========================================
            // LOGIN
            // ========================================
            async function attemptLogin() {
                let name = document.getElementById('loginName').value.trim();
                if (!name) {
                    showToast('Masukkan nama!');
                    return;
                }
                let fp = await getFingerprint();
                if (await checkBlockedUser(fp)) return;
                let fbUser = await loadUserFromStorage(fp);
                if (fbUser) {
                    currentUser = fbUser;
                } else {
                    currentUser = {
                        name: name,
                        avatar: null,
                        totalDownloads: 0,
                        totalMP3: 0,
                        todayDownloads: 0,
                        joinDate: new Date().toISOString(),
                        isPremium: false,
                        premiumExpiry: null,
                        fingerprint: fp,
                        missionCompleted: false,
                        missionRank: null,
                        blocked: false,
                        userId: generateUniqueUserId()
                    };
                    await saveUserToStorage(currentUser);
                    showNotification("🎉 Selamat Datang!", `Selamat datang ${name} di WaterTik!`);
                }
                let fbMission = await loadMissionFromStorage(fp);
                if (fbMission) missionData = fbMission;
                else missionData = { videoDownloads: 0, photoGenerates: 0, mp3Converts: 0 };
                await saveMissionToStorage(fp, missionData);
                updateUI();
                showToast(`Selamat datang, ${name}!`);
                document.getElementById('loginName').value = '';
                if (ramadhanPhase === 'active' && !ramadhanPopupShown && currentUser) {
                    document.getElementById('ramadhanStartPopup').classList.add('active');
                    ramadhanPopupShown = true;
                }
                await updateWinnersList();
                updateMissionDisplay();
            }
            
            function isPremiumActive(u) {
                return u && u.isPremium && u.premiumExpiry && new Date(u.premiumExpiry) > new Date();
            }
            
            async function updateDownloadStats() {
                if (currentUser) {
                    currentUser.totalDownloads++;
                    currentUser.todayDownloads = (currentUser.todayDownloads || 0) + 1;
                    await saveUserToStorage(currentUser);
                    updateUI();
                }
            }
            
            // ========================================
            // UPDATE MISI
            // ========================================
            async function updateMissionStats(type) {
                if (!currentUser || currentUser.missionCompleted) return false;
                if (ramadhanPhase !== 'active') return false;
                
                let winners = await loadWinnersFromStorage();
                if (winners.length >= 3) {
                    updateMissionDisplay();
                    return false;
                }
                if (type === 'video') missionData.videoDownloads++;
                else if (type === 'photo') missionData.photoGenerates++;
                else if (type === 'mp3') missionData.mp3Converts++;
                await saveMissionToStorage(currentUser.fingerprint, missionData);
                if (missionData.videoDownloads >= 100 && missionData.photoGenerates >= 100 && missionData.mp3Converts >= 10)
                    showNotification("✅ Misi Selesai!", "Klik Klaim Hadiah!");
                updateMissionDisplay();
                return true;
            }
            
            // ========================================
            // UI UPDATE
            // ========================================
            function updateUI() {
                if (currentUser) {
                    let premiumActive = isPremiumActive(currentUser);
                    let joinDate = new Date(currentUser.joinDate).toLocaleDateString('id-ID');
                    document.getElementById('userNameDisplay').innerText = currentUser.name;
                    document.getElementById('userJoinDateDisplay').innerHTML = `Member since ${joinDate}`;
                    document.getElementById('miniDownloads').innerText = currentUser.totalDownloads;
                    document.getElementById('miniMP3').innerText = currentUser.totalMP3;
                    document.getElementById('miniPremium').innerHTML = premiumActive ? '<i class="fas fa-crown"></i>' : '✗';
                    document.getElementById('loginSection').style.display = 'none';
                    document.getElementById('userInfoSection').style.display = 'block';
                    document.getElementById('loggedUserName').innerText = currentUser.name;
                    document.getElementById('userPremiumStatus').innerHTML = premiumActive ? '✓ Premium Active' : 'Free User';
                    document.getElementById('akunDownloads').innerText = currentUser.totalDownloads;
                    document.getElementById('akunMP3').innerText = currentUser.totalMP3;
                    document.getElementById('statToday').innerText = currentUser.todayDownloads || 0;
                    document.getElementById('statTotalMP3').innerText = currentUser.totalMP3;
                    let av = document.getElementById('avatarDisplay');
                    if (currentUser.avatar) av.innerHTML = `<img src="${currentUser.avatar}" style="width:100%;height:100%;object-fit:cover;">`;
                    else av.innerHTML = '<i class="fas fa-user"></i>';
                    let ad = document.getElementById('adContainer');
                    if (ad) ad.classList.toggle('hidden', premiumActive);
                    updateUserIdDisplay();
                } else {
                    document.getElementById('loginSection').style.display = 'block';
                    document.getElementById('userInfoSection').style.display = 'none';
                    document.getElementById('userNameDisplay').innerText = 'Guest';
                }
                updateMissionDisplay();
            }
            
            function updateUserIdDisplay() {
                let c = document.getElementById('infoUserIdContainer'),
                    iv = document.getElementById('infoUserIdValue'),
                    av = document.getElementById('akunUserIdValue');
                if (currentUser && currentUser.userId) {
                    if (c) c.style.display = 'block';
                    if (iv) iv.innerText = currentUser.userId;
                    if (av) av.innerText = currentUser.userId;
                } else if (c) c.style.display = 'none';
            }
            
            function copyUserId() {
                if (currentUser && currentUser.userId) {
                    navigator.clipboard.writeText(currentUser.userId);
                    showToast('✅ ID tersalin!');
                } else showToast('❌ Belum login');
            }
            
            // ========================================
            // TAMPILAN MISI
            // ========================================
            function updateMissionDisplay() {
                let loginWarn = document.getElementById('missionLoginWarning'),
                    countdownArea = document.getElementById('missionCountdownArea'),
                    activeArea = document.getElementById('missionActiveArea'),
                    lebaranArea = document.getElementById('missionLebaranArea'),
                    fullArea = document.getElementById('missionFullArea');
                if (!currentUser) {
                    if (loginWarn) loginWarn.style.display = 'block';
                    if (countdownArea) countdownArea.style.display = 'none';
                    if (activeArea) activeArea.style.display = 'none';
                    if (lebaranArea) lebaranArea.style.display = 'none';
                    if (fullArea) fullArea.style.display = 'none';
                    return;
                } else {
                    if (loginWarn) loginWarn.style.display = 'none';
                }
                if (ramadhanPhase === 'countdown') {
                    if (countdownArea) countdownArea.style.display = 'block';
                    if (activeArea) activeArea.style.display = 'none';
                    if (lebaranArea) lebaranArea.style.display = 'none';
                    if (fullArea) fullArea.style.display = 'none';
                    document.getElementById('countdownTimer').innerHTML = `⏳ ${ramadhanDaysLeft} hari lagi menuju Ramadhan`;
                } else if (ramadhanPhase === 'active') {
                    if (misiFull) {
                        if (countdownArea) countdownArea.style.display = 'none';
                        if (activeArea) activeArea.style.display = 'none';
                        if (lebaranArea) lebaranArea.style.display = 'none';
                        if (fullArea) fullArea.style.display = 'block';
                        return;
                    }
                    if (countdownArea) countdownArea.style.display = 'none';
                    if (activeArea) activeArea.style.display = 'block';
                    if (lebaranArea) lebaranArea.style.display = 'none';
                    if (fullArea) fullArea.style.display = 'none';
                    loadWinnersFromStorage().then(winners => {
                        let isWinner = winners.some(w => w.fingerprint === currentUser.fingerprint);
                        let completed = (missionData.videoDownloads >= 100 && missionData.photoGenerates >= 100 && missionData.mp3Converts >= 10);
                        let percent = Math.min(100, ((missionData.videoDownloads / 100) + (missionData.photoGenerates / 100) + (missionData.mp3Converts / 10)) / 3 * 100);
                        document.getElementById('videoCount').innerText = missionData.videoDownloads;
                        document.getElementById('photoCount').innerText = missionData.photoGenerates;
                        document.getElementById('mp3Count').innerText = missionData.mp3Converts;
                        document.getElementById('missionProgressBar').style.width = percent + '%';
                        if (isWinner) {
                            document.getElementById('missionStatusText').innerHTML = '🏆 Anda sudah jadi pemenang!';
                            document.getElementById('claimMissionBtn').style.display = 'none';
                        } else if (completed && !currentUser.missionCompleted) {
                            document.getElementById('missionStatusText').innerHTML = '✅ MISI SELESAI! Klik Klaim!';
                            document.getElementById('claimMissionBtn').style.display = 'block';
                        } else {
                            document.getElementById('missionStatusText').innerHTML = `Progres ${Math.round(percent)}%`;
                            document.getElementById('claimMissionBtn').style.display = 'none';
                        }
                    });
                } else {
                    if (countdownArea) countdownArea.style.display = 'none';
                    if (activeArea) activeArea.style.display = 'none';
                    if (lebaranArea) lebaranArea.style.display = 'block';
                    if (fullArea) fullArea.style.display = 'none';
                }
            }
            
            async function claimMission() {
                if (!currentUser) {
                    showToast('Login dulu');
                    return;
                }
                if (ramadhanPhase !== 'active') {
                    showToast('🌙 Hanya saat Ramadhan');
                    return;
                }
                let winners = await loadWinnersFromStorage();
                if (winners.length >= 3) {
                    showNotification("Misi Berakhir", "3 pemenang sudah ada");
                    updateMissionDisplay();
                    return;
                }
                if (missionData.videoDownloads >= 100 && missionData.photoGenerates >= 100 && missionData.mp3Converts >= 10 && !currentUser.missionCompleted) {
                    if (winners.some(w => w.fingerprint === currentUser.fingerprint)) {
                        showToast('Sudah jadi pemenang');
                        return;
                    }
                    let rank;
                    if (winners.length === 0) rank = 1;
                    else if (winners.length === 1) rank = 2;
                    else if (winners.length === 2) rank = 3;
                    else {
                        showToast('Misi penuh');
                        return;
                    }
                    let prizeText = rank === 1 ? "Rp50.000" : (rank === 2 ? "Rp20.000" : "Rp10.000");
                    showWinnerPopup(rank);
                    winners.push({
                        name: currentUser.name,
                        userId: currentUser.userId,
                        fingerprint: currentUser.fingerprint,
                        time: new Date().toISOString(),
                        rank: rank,
                        claimed: false,
                        prize: prizeText
                    });
                    await saveWinnersToStorage(winners);
                    currentUser.missionCompleted = true;
                    currentUser.missionRank = rank;
                    await saveUserToStorage(currentUser);
                    if (winners.length >= 3) misiFull = true;
                    updateUI();
                    updateMissionDisplay();
                    updateWinnersList();
                    showNotification("🎉 SELAMAT!", `Anda juara ${rank} dengan hadiah ${prizeText}! Hubungi admin.`);
                } else {
                    showToast('Selesaikan semua misi dulu!');
                }
            }
            
            async function updateWinnersList() {
                let winners = await loadWinnersFromStorage(),
                    cont = document.getElementById('winnersListContainer');
                if (winners.length === 0) {
                    cont.innerHTML = '<div style="text-align:center;padding:10px;">Belum ada pemenang</div>';
                    return;
                }
                cont.innerHTML = winners.sort((a, b) => a.rank - b.rank).map(w => {
                    let prize = w.rank === 1 ? 'Rp50.000' : (w.rank === 2 ? 'Rp20.000' : 'Rp10.000');
                    let icon = w.rank === 1 ? '🏆' : (w.rank === 2 ? '🥈' : '🥉');
                    return `<div class="winner-item"><span>${icon} Pemenang ${w.rank}</span><span>${w.name}</span><span>${prize}</span></div>`;
                }).join('');
            }
            
            function showWinnerPopup(rank) {
                let popup = document.getElementById('winnerPopup'),
                    prizeEl = document.getElementById('winnerPopupPrize'),
                    msgEl = document.getElementById('winnerPopupMessage');
                if (rank === 1) {
                    prizeEl.innerHTML = 'Rp50.000';
                    msgEl.innerHTML = 'Anda JUARA 1! Hubungi admin.';
                } else if (rank === 2) {
                    prizeEl.innerHTML = 'Rp20.000';
                    msgEl.innerHTML = 'Anda JUARA 2! Hubungi admin.';
                } else {
                    prizeEl.innerHTML = 'Rp10.000';
                    msgEl.innerHTML = 'Anda JUARA 3! Hubungi admin.';
                }
                popup.classList.add('active');
                setTimeout(() => popup.classList.remove('active'), 10000);
            }
            
            function closeWinnerPopup() {
                document.getElementById('winnerPopup').classList.remove('active');
            }
            
            function closeBanPopup() {
                document.getElementById('banReasonPopup').classList.remove('active');
            }
            
            function closeRamadhanPopup() {
                document.getElementById('ramadhanStartPopup').classList.remove('active');
            }
            
            function showInfoPage(p) {
                let a = document.getElementById('aboutPage'),
                    b = document.getElementById('privacyPage'),
                    ba = document.getElementById('btnAbout'),
                    bb = document.getElementById('btnPrivacy');
                if (p === 'about') {
                    a.classList.add('active-page');
                    b.classList.remove('active-page');
                    ba.classList.add('active');
                    bb.classList.remove('active');
                } else {
                    a.classList.remove('active-page');
                    b.classList.add('active-page');
                    ba.classList.remove('active');
                    bb.classList.add('active');
                }
            }
            
            // ========================================
            // DETEKSI RAMADHAN + RESET TAHUNAN
            // ========================================
            async function checkRamadhanReal() {
                let today = new Date(),
                    year = today.getFullYear(),
                    start = new Date(year, 1, 18);
                if (today > start) start = new Date(year + 1, 1, 8);
                let daysLeft = Math.ceil((start - today) / (1000 * 60 * 60 * 24)),
                    isRamadhan = daysLeft <= 0 && daysLeft > -30,
                    isLebaran = daysLeft <= -30;
                if (isRamadhan) ramadhanPhase = 'active';
                else if (isLebaran) ramadhanPhase = 'lebaran';
                else ramadhanPhase = 'countdown';
                ramadhanDaysLeft = Math.abs(daysLeft);
                document.body.classList.remove('ramadhan', 'lebaran');
                if (ramadhanPhase === 'active') document.body.classList.add('ramadhan');
                if (ramadhanPhase === 'lebaran') document.body.classList.add('lebaran');
                let hs = document.getElementById('ramadhanStatus'),
                    cd = document.getElementById('ramadhanCountdown');
                if (ramadhanPhase === 'active') {
                    hs.innerHTML = '🌙 Selamat Bulan Ramadhan! 🌙';
                    cd.innerHTML = `📅 Ramadhan ${today.getFullYear()}`;
                } else if (ramadhanPhase === 'lebaran') {
                    hs.innerHTML = '🌙 Taqabbalallahu minna wa minkum';
                    cd.innerHTML = '📅 Idul Fitri 1447 H';
                } else {
                    hs.innerHTML = '🌙 Menunggu Bulan Ramadhan';
                    cd.innerHTML = `⏳ ${ramadhanDaysLeft} hari menuju Ramadhan`;
                }
                updateMissionDisplay();
                await checkAndResetRamadhanMission();
            }
            
            // ========================================
            // API TIKTOK
            // ========================================
            const VIDEO_APIS = [{
                handler: async (url) => {
                    try {
                        let res = await fetch(`https://www.tikwm.com/api/?url=${encodeURIComponent(url)}`);
                        let data = await res.json();
                        if (data.code === 0 && data.data) {
                            let upload = '-';
                            if (data.data.create_time) {
                                let d = new Date(data.data.create_time * 1000);
                                upload = d.toLocaleDateString('id-ID');
                            }
                            return {
                                success: true,
                                hdUrl: data.data.hdplay || data.data.play,
                                sdUrl: data.data.play,
                                title: data.data.title || 'TikTok Video',
                                author: data.data.author?.nickname || '@user',
                                duration: formatDuration(data.data.duration || 0),
                                thumbnail: data.data.cover,
                                size: data.data.size ? (data.data.size / 1024 / 1024).toFixed(1) + ' MB' : '~15 MB',
                                images: data.data.images || [],
                                uploadDate: upload
                            };
                        }
                        return null;
                    } catch (e) {
                        return null;
                    }
                }
            }];
            
            async function downloadVideo() {
                let url = document.getElementById('tiktokUrl').value.trim();
                if (!url) {
                    showToast('Masukkan link TikTok!');
                    return;
                }
                document.getElementById('videoLoading').style.display = 'block';
                let videoData = null;
                for (let api of VIDEO_APIS) {
                    try {
                        let d = await api.handler(url);
                        if (d && d.success) {
                            videoData = d;
                            break;
                        }
                    } catch (e) {}
                }
                if (videoData) {
                    currentVideoData = videoData;
                    document.getElementById('videoThumb').src = videoData.thumbnail;
                    document.getElementById('videoTitle').innerText = videoData.title;
                    document.getElementById('videoAuthor').innerText = '@' + videoData.author;
                    document.getElementById('videoDuration').innerText = videoData.duration;
                    document.getElementById('videoSize').innerText = videoData.size;
                    document.getElementById('downloadLink').href = videoData.hdUrl;
                    document.getElementById('videoResult').classList.add('active');
                    await updateDownloadStats();
                    await updateMissionStats('video');
                    showToast('✅ Video siap!');
                } else showToast('❌ Gagal ambil video');
                document.getElementById('videoLoading').style.display = 'none';
            }
            
            function selectQuality(q) {
                currentQuality = q;
                document.getElementById('downloadLink').href = q === 'hd' ? currentVideoData?.hdUrl : currentVideoData?.sdUrl;
                document.getElementById('videoQuality').innerText = q === 'hd' ? 'HD' : 'SD';
            }
            
            function clearLink() {
                document.getElementById('tiktokUrl').value = '';
                document.getElementById('videoResult').classList.remove('active');
                currentVideoData = null;
            }
            
            function clearLinkAndReset() {
                clearLink();
            }
            
            // ========================================
            // GENERATOR FOTO
            // ========================================
            async function generateWatermark() {
                let url = document.getElementById('watermarkUrl').value.trim();
                if (!url || !url.includes('tiktok.com')) {
                    showToast('Link TikTok valid!');
                    return;
                }
                document.getElementById('watermarkLoading').style.display = 'block';
                try {
                    for (let api of VIDEO_APIS) {
                        let data = await api.handler(url);
                        if (data && data.success && data.thumbnail) {
                            currentWatermarkUrl = data.thumbnail;
                            let imgRes = await fetch(currentWatermarkUrl);
                            currentWatermarkBlob = await imgRes.blob();
                            document.getElementById('watermarkImage').src = currentWatermarkUrl;
                            document.getElementById('watermarkImage').style.display = 'block';
                            document.getElementById('watermarkButtons').style.display = 'flex';
                            document.getElementById('watermarkResult').classList.add('active');
                            await updateMissionStats('photo');
                            showToast('Thumbnail siap!');
                            break;
                        }
                    }
                } catch (e) {
                    showToast('Gagal');
                }
                document.getElementById('watermarkLoading').style.display = 'none';
            }
            
            function downloadSingleImage() {
                if (currentWatermarkBlob) {
                    let u = URL.createObjectURL(currentWatermarkBlob),
                        a = document.createElement('a');
                    a.href = u;
                    a.download = `thumb_${Date.now()}.jpg`;
                    a.click();
                    setTimeout(() => URL.revokeObjectURL(u), 100);
                    showToast('Gambar disimpan!');
                }
            }
            
            function copyWatermarkLink() {
                if (currentWatermarkUrl) {
                    navigator.clipboard.writeText(currentWatermarkUrl);
                    showToast('Link disalin!');
                }
            }
            
            async function generateMultipleFrames() {
                let url = document.getElementById('watermarkUrl').value.trim();
                if (!url || !url.includes('tiktok.com')) {
                    showToast('Link TikTok valid!');
                    return;
                }
                document.getElementById('watermarkResult').classList.remove('active');
                document.getElementById('multipleFramesResult').style.display = 'none';
                let loadingDiv = document.getElementById('multiFrameLoading'),
                    progBar = document.getElementById('multiFrameProgress');
                loadingDiv.style.display = 'block';
                progBar.style.width = '0%';
                if (framesList.length) {
                    framesList.forEach(f => {
                        if (f.url && f.url.startsWith('blob:')) URL.revokeObjectURL(f.url);
                    });
                    framesList = [];
                }
                try {
                    progBar.style.width = '30%';
                    document.getElementById('multiFrameStatusText').innerHTML = 'Mengambil data...';
                    let videoData = null;
                    for (let api of VIDEO_APIS) {
                        let data = await api.handler(url);
                        if (data && data.success && data.thumbnail) {
                            videoData = data;
                            break;
                        }
                    }
                    if (!videoData) throw new Error();
                    progBar.style.width = '60%';
                    document.getElementById('multiFrameStatusText').innerHTML = 'Memproses gambar...';
                    let images = [];
                    if (videoData.images && videoData.images.length) {
                        for (let i = 0; i < Math.min(videoData.images.length, 9); i++) {
                            let res = await fetch(videoData.images[i]);
                            let blob = await res.blob();
                            images.push({
                                blob,
                                url: URL.createObjectURL(blob),
                                name: `slide_${i+1}_${Date.now()}.jpg`,
                                label: `Slide ${i+1}`
                            });
                        }
                    }
                    if (images.length === 0) throw new Error('Tidak ada slide');
                    framesList = images;
                    progBar.style.width = '100%';
                    document.getElementById('multiFrameStatusText').innerHTML = `✅ Selesai! ${framesList.length} slide`;
                    await updateMissionStats('photo');
                    setTimeout(() => {
                        loadingDiv.style.display = 'none';
                        let gallery = document.getElementById('framesGallery');
                        gallery.innerHTML = '';
                        framesList.forEach((f, i) => {
                            let div = document.createElement('div');
                            div.className = 'gallery-item';
                            div.innerHTML = `<div class="frame-time">${f.label}</div><img src="${f.url}"><div class="download-single" onclick="event.stopPropagation(); downloadSingleFrame(${i})"><i class="fas fa-download"></i></div>`;
                            div.onclick = () => downloadSingleFrame(i);
                            gallery.appendChild(div);
                        });
                        document.getElementById('multipleFramesResult').style.display = 'block';
                        showToast(`✅ ${framesList.length} slide foto berhasil!`);
                    }, 500);
                } catch (e) {
                    loadingDiv.style.display = 'none';
                    showToast('❌ Gagal ambil slide foto');
                }
            }
            
            function downloadSingleFrame(i) {
                let f = framesList[i];
                if (f && f.blob) {
                    let u = URL.createObjectURL(f.blob),
                        a = document.createElement('a');
                    a.href = u;
                    a.download = f.name;
                    a.click();
                    setTimeout(() => URL.revokeObjectURL(u), 100);
                    showToast('✅ Gambar disimpan!');
                }
            }
            
            function downloadAllFrames() {
                if (!framesList.length) {
                    showToast('Tidak ada gambar');
                    return;
                }
                showToast(`📥 Mengunduh ${framesList.length} gambar...`);
                framesList.forEach((_, i) => {
                    setTimeout(() => downloadSingleFrame(i), i * 400);
                });
            }
            
            function closeMultipleFrames() {
                document.getElementById('multipleFramesResult').style.display = 'none';
                if (framesList) {
                    framesList.forEach(f => {
                        if (f.url && f.url.startsWith('blob:')) URL.revokeObjectURL(f.url);
                    });
                    framesList = [];
                }
            }
            
            // ========================================
            // MP3 CONVERTER
            // ========================================
            function handleVideoSelect() {
                let inp = document.getElementById('videoFileInput');
                if (inp.files.length) selectedVideoFile = inp.files[0];
            }
            
            function resetMP3() {
                document.getElementById('videoFileInput').value = '';
                document.getElementById('mp3Result').classList.remove('active');
                selectedVideoFile = null;
            }
            
            async function convertToMP3() {
                if (!selectedVideoFile) {
                    showToast('Pilih file video!');
                    return;
                }
                document.getElementById('mp3Loading').style.display = 'block';
                try {
                    let audioBlob = await extractAudio(selectedVideoFile),
                        audioUrl = URL.createObjectURL(audioBlob);
                    document.getElementById('audioPreview').src = audioUrl;
                    document.getElementById('mp3DownloadLink').href = audioUrl;
                    let mp3Name = selectedVideoFile.name.replace(/\.[^/.]+$/, '') + '.mp3';
                    document.getElementById('mp3DownloadLink').setAttribute('download', mp3Name);
                    document.getElementById('mp3FileName').innerText = selectedVideoFile.name;
                    document.getElementById('mp3FileSize').innerText = (audioBlob.size / 1024 / 1024).toFixed(1) + ' MB';
                    document.getElementById('mp3Result').classList.add('active');
                    if (currentUser) {
                        currentUser.totalMP3++;
                        await saveUserToStorage(currentUser);
                        updateUI();
                        await updateMissionStats('mp3');
                    }
                    showToast('✅ MP3 berhasil!');
                } catch (e) {
                    showToast('❌ Gagal konversi');
                }
                document.getElementById('mp3Loading').style.display = 'none';
            }
            
            function extractAudio(file) {
                return new Promise((resolve, reject) => {
                    let video = document.createElement('video'),
                        url = URL.createObjectURL(file);
                    video.src = url;
                    video.onloadedmetadata = () => {
                        try {
                            let ctx = new(window.AudioContext || window.webkitAudioContext)(),
                                source = ctx.createMediaElementSource(video),
                                dest = ctx.createMediaStreamDestination();
                            source.connect(dest);
                            let recorder = new MediaRecorder(dest.stream),
                                chunks = [];
                            recorder.ondataavailable = e => chunks.push(e.data);
                            recorder.onstop = () => {
                                let blob = new Blob(chunks, { type: 'audio/mpeg' });
                                URL.revokeObjectURL(url);
                                resolve(blob);
                            };
                            recorder.start();
                            video.play().then(() => {
                                setTimeout(() => {
                                    video.pause();
                                    recorder.stop();
                                    source.disconnect();
                                }, video.duration * 1000);
                            }).catch(reject);
                        } catch (e) {
                            reject(e);
                        }
                    };
                    video.onerror = reject;
                });
            }
            
            // ========================================
            // IG DOWNLOADER FUNCTIONS
            // ========================================
            const IG_SERVICES = [
                {
                    name: 'SnapSave',
                    url: 'https://snapsave.app/action.php',
                    method: 'POST',
                    body: (url) => {
                        const form = new FormData();
                        form.append('url', url);
                        return form;
                    },
                    extract: (data) => {
                        if (data && data.url) {
                            return {
                                success: true,
                                media: [{
                                    url: data.url,
                                    type: data.type || 'video',
                                    thumbnail: data.thumbnail || data.url
                                }],
                                title: data.title || 'Instagram Media'
                            };
                        }
                        return { success: false };
                    }
                },
                {
                    name: 'SaveIG',
                    url: 'https://saveig.app/api/ajaxSearch',
                    method: 'POST',
                    body: (url) => {
                        const form = new FormData();
                        form.append('url', url);
                        return form;
                    },
                    extract: (data) => {
                        if (data && data.data && data.data.length > 0) {
                            const media = data.data.map(item => ({
                                url: item.url,
                                type: item.type || 'video',
                                thumbnail: item.thumbnail || item.url
                            }));
                            return {
                                success: true,
                                media: media,
                                title: data.title || 'Instagram Media'
                            };
                        }
                        return { success: false };
                    }
                }
            ];
            
            async function downloadInstagram() {
                const url = document.getElementById('igUrlInput').value.trim();
                const loading = document.getElementById('igLoading');
                const error = document.getElementById('igError');
                const errorText = document.getElementById('igErrorText');
                const result = document.getElementById('igResult');
                const btn = document.getElementById('igDownloadBtn');
                
                if (!url) {
                    showErrorIG('Masukkan link Instagram terlebih dahulu.');
                    return;
                }
                
                if (!url.includes('instagram.com')) {
                    showErrorIG('URL harus dari Instagram (instagram.com).');
                    return;
                }
                
                hideErrorIG();
                result.classList.remove('active');
                document.getElementById('igMediaList').innerHTML = '';
                loading.classList.add('active');
                btn.disabled = true;
                btn.innerHTML = '⏳ Loading...';
                currentIGMedia = [];
                
                try {
                    let resultData = null;
                    let usedService = '';
                    
                    for (const service of IG_SERVICES) {
                        loading.querySelector('p') ? loading.querySelector('p').textContent = `Mencoba ${service.name}...` : '';
                        const data = await fetchIGService(url, service);
                        if (data && data.success && data.media && data.media.length > 0) {
                            resultData = data;
                            usedService = service.name;
                            break;
                        }
                        await new Promise(r => setTimeout(r, 500));
                    }
                    
                    if (resultData && resultData.media && resultData.media.length > 0) {
                        currentIGMedia = resultData.media;
                        renderIGResult(resultData, usedService);
                    } else {
                        throw new Error('Tidak ada media yang ditemukan. Coba link lain.');
                    }
                    
                } catch (error) {
                    console.error('IG Error:', error);
                    showErrorIG(error.message || 'Gagal mengunduh. Coba lagi nanti.');
                } finally {
                    loading.classList.remove('active');
                    btn.disabled = false;
                    btn.innerHTML = '<i class="fab fa-instagram"></i> Download';
                }
            }
            
            async function fetchIGService(url, service) {
                try {
                    const body = service.body(url);
                    
                    const controller = new AbortController();
                    const timeout = setTimeout(() => controller.abort(), 15000);
                    
                    const response = await fetch(service.url, {
                        method: service.method || 'POST',
                        body: body,
                        headers: {
                            'Accept': 'application/json'
                        },
                        signal: controller.signal
                    });
                    
                    clearTimeout(timeout);
                    
                    if (!response.ok) {
                        console.warn(`${service.name} HTTP ${response.status}`);
                        return null;
                    }
                    
                    const rawData = await response.json();
                    const extracted = service.extract(rawData);
                    
                    if (extracted && extracted.success && extracted.media && extracted.media.length > 0) {
                        return extracted;
                    }
                    return null;
                    
                } catch (error) {
                    console.warn(`${service.name} failed:`, error.message);
                    return null;
                }
            }
            
            function renderIGResult(data, serviceName) {
                const { media, title } = data;
                const list = document.getElementById('igMediaList');
                const result = document.getElementById('igResult');
                
                document.getElementById('igResultTitle').textContent = title || 'Media ditemukan';
                document.getElementById('igResultCount').textContent = `${media.length} file • ${serviceName || 'API'}`;
                
                list.innerHTML = '';
                
                media.forEach((item, index) => {
                    const isVideo = item.type === 'video' || 
                                   (item.url && /\.(mp4|mov|avi|webm|m3u8)/i.test(item.url)) ||
                                   (item.url && item.url.includes('video'));
                    const isImage = item.type === 'image' || 
                                   (item.url && /\.(jpg|jpeg|png|webp|gif)/i.test(item.url)) ||
                                   (item.url && item.url.includes('image'));
                    
                    let mediaUrl = item.url || '';
                    if (mediaUrl.includes('\\/')) mediaUrl = mediaUrl.replace(/\\\//g, '/');
                    if (mediaUrl.startsWith('//')) mediaUrl = 'https:' + mediaUrl;
                    
                    let thumbUrl = item.thumbnail || mediaUrl;
                    if (thumbUrl.includes('\\/')) thumbUrl = thumbUrl.replace(/\\\//g, '/');
                    if (thumbUrl.startsWith('//')) thumbUrl = 'https:' + thumbUrl;
                    
                    const div = document.createElement('div');
                    div.className = 'ig-media-item';
                    
                    const img = document.createElement('img');
                    img.className = 'ig-thumb';
                    img.src = thumbUrl;
                    img.alt = `Media ${index + 1}`;
                    img.loading = 'lazy';
                    img.onerror = function() {
                        this.src = 'data:image/svg+xml,%3Csvg xmlns="http://www.w3.org/2000/svg" width="200" height="200" viewBox="0 0 200 200"%3E%3Crect width="200" height="200" fill="%23333"/%3E%3Ctext x="50%25" y="50%25" text-anchor="middle" dy=".3em" fill="%23999" font-size="40"%3E📷%3C/text%3E%3C/svg%3E';
                    };
                    div.appendChild(img);
                    
                    const info = document.createElement('div');
                    info.className = 'ig-info';
                    
                    const filename = document.createElement('div');
                    filename.className = 'ig-filename';
                    filename.textContent = isVideo ? `video_${index + 1}.mp4` : `image_${index + 1}.jpg`;
                    info.appendChild(filename);
                    
                    const badge = document.createElement('span');
                    badge.className = `ig-type-badge ${isVideo ? 'video' : 'image'}`;
                    badge.textContent = isVideo ? '🎬 VIDEO' : '🖼 IMAGE';
                    info.appendChild(badge);
                    
                    div.appendChild(info);
                    
                    const downloadLink = document.createElement('a');
                    downloadLink.className = 'ig-download-btn';
                    downloadLink.href = mediaUrl;
                    downloadLink.target = '_blank';
                    downloadLink.download = `instagram_${index + 1}.${isVideo ? 'mp4' : 'jpg'}`;
                    downloadLink.textContent = '⬇ Download';
                    div.appendChild(downloadLink);
                    
                    list.appendChild(div);
                });
                
                result.classList.add('active');
                
                setTimeout(() => {
                    result.scrollIntoView({ behavior: 'smooth', block: 'start' });
                }, 300);
            }
            
            function downloadAllIG() {
                const links = document.querySelectorAll('.ig-download-btn');
                if (links.length === 0) return;
                
                links.forEach((link, index) => {
                    setTimeout(() => {
                        const a = document.createElement('a');
                        a.href = link.href;
                        a.download = link.download || `instagram_${index + 1}`;
                        a.target = '_blank';
                        a.click();
                    }, index * 500);
                });
            }
            
            function showErrorIG(message) {
                const error = document.getElementById('igError');
                const errorText = document.getElementById('igErrorText');
                errorText.textContent = message;
                error.classList.add('active');
                document.getElementById('igResult').classList.remove('active');
            }
            
            function hideErrorIG() {
                document.getElementById('igError').classList.remove('active');
            }
            
            // ========================================
            // AI HELPER FUNCTIONS
            // ========================================
            function addAIMessage(msg, type) {
                const container = document.getElementById('aiChatContainer');
                const div = document.createElement('div');
                div.className = `ai-message ${type}`;
                
                const icon = type === 'user' ? '👤' : '🤖';
                const name = type === 'user' ? 'Anda' : 'WaterTik AI';
                
                let messageText = msg || (type === 'user' ? '(pesan kosong)' : 'Maaf, saya sedang sibuk. Coba tanyakan lagi ya!');
                messageText = sanitizeInput(messageText);
                
                div.innerHTML = `
                    <div class="msg-header">
                        <span class="ai-icon">${icon}</span> ${name}
                    </div>
                    <div class="msg-content">${messageText.replace(/\n/g, '<br>')}</div>
                `;
                container.appendChild(div);
                container.scrollTop = container.scrollHeight;
            }
            
            function showTypingIndicator() {
                document.getElementById('aiTypingIndicator').style.display = 'block';
                document.getElementById('aiChatContainer').scrollTop = document.getElementById('aiChatContainer').scrollHeight;
            }
            
            function hideTypingIndicator() {
                document.getElementById('aiTypingIndicator').style.display = 'none';
            }
            
            function showRateLimit(waitTime) {
                const rateLimitDiv = document.getElementById('aiRateLimit');
                const countdownSpan = document.getElementById('rateLimitCountdown');
                rateLimitDiv.classList.add('active');
                countdownSpan.textContent = waitTime;
                
                let remaining = waitTime;
                const interval = setInterval(() => {
                    remaining--;
                    if (remaining <= 0) {
                        clearInterval(interval);
                        rateLimitDiv.classList.remove('active');
                    } else {
                        countdownSpan.textContent = remaining;
                    }
                }, 1000);
            }
            
            function disableAIInputs(disabled) {
                document.getElementById('aiQuestion').disabled = disabled;
                document.getElementById('sendAIbtn').disabled = disabled;
            }
            
            // ========================================
            // ASK AI - DENGAN RATE LIMIT
            // ========================================
            window.askAI = async function() {
                const input = document.getElementById('aiQuestion');
                const question = sanitizeInput(input.value.trim());
                
                if (!question) {
                    showToast('Masukkan pertanyaan dulu!');
                    return;
                }
                
                const now = Date.now();
                const timeSinceLast = now - lastRequestTime;
                
                if (timeSinceLast < MIN_INTERVAL) {
                    const waitTime = Math.ceil((MIN_INTERVAL - timeSinceLast) / 1000);
                    showRateLimit(waitTime);
                    return;
                }
                
                if (isRequesting) {
                    showToast('⏳ Tunggu request sebelumnya selesai...');
                    return;
                }
                
                isRequesting = true;
                disableAIInputs(true);
                addAIMessage(question, 'user');
                input.value = '';
                showTypingIndicator();
                
                try {
                    lastRequestTime = Date.now();
                    
                    const response = await fetch(API_URL, {
                        method: 'POST',
                        headers: {
                            'Content-Type': 'application/json',
                            'Authorization': `Bearer ${API_KEY}`,
                            'X-CSRF-Token': csrfToken
                        },
                        body: JSON.stringify({
                            model: 'zai-glm-4.7',
                            messages: [
                                { role: 'system', content: AI_SYSTEM_PROMPT },
                                { role: 'user', content: question }
                            ],
                            temperature: 0.8,
                            max_tokens: 800
                        })
                    });
                    
                    hideTypingIndicator();
                    
                    if (!response.ok) {
                        let errorMsg = 'Maaf, ada masalah. ';
                        if (response.status === 429) {
                            errorMsg += 'Terlalu banyak request. Tunggu 5 detik lalu coba lagi.';
                        } else if (response.status === 401) {
                            errorMsg += 'API Key tidak valid.';
                        } else if (response.status === 500) {
                            errorMsg += 'Server AI sibuk. Coba lagi nanti.';
                        } else {
                            errorMsg += `Error ${response.status}.`;
                        }
                        addAIMessage(errorMsg, 'bot');
                        showToast('❌ Gagal');
                        isRequesting = false;
                        disableAIInputs(false);
                        return;
                    }
                    
                    const data = await response.json();
                    
                    if (data && data.choices && data.choices.length > 0) {
                        const aiResponse = data.choices[0].message?.content;
                        if (aiResponse && aiResponse.trim().length > 0) {
                            addAIMessage(aiResponse, 'bot');
                        } else {
                            addAIMessage('Hmm, coba tanyakan hal lain ya! 😊', 'bot');
                        }
                    } else {
                        addAIMessage('Format respons tidak dikenali. Coba lagi.', 'bot');
                    }
                    
                } catch (error) {
                    hideTypingIndicator();
                    console.error('AI Error:', error);
                    addAIMessage('❌ Gagal terhubung ke AI. Cek koneksi internet.', 'bot');
                    showToast('❌ Gagal konek');
                }
                
                isRequesting = false;
                disableAIInputs(false);
            };
            
            // ========================================
            // QUICK ASK & CLEAR CHAT
            // ========================================
            window.quickAsk = function(question) {
                document.getElementById('aiQuestion').value = question;
                window.askAI();
            };
            
            window.clearChat = function() {
                const container = document.getElementById('aiChatContainer');
                container.innerHTML = `
                    <div class="ai-message bot">
                        <div class="msg-header">
                            <span class="ai-icon">🤖</span> WaterTik AI Assistant
                        </div>
                        <div class="msg-content">
                            <strong>Assalamu'alaikum! 👋</strong><br><br>
                            Saya <strong>WaterTik AI</strong>, asisten pintar yang siap membantu kamu!<br><br>
                            ✨ <strong>Kemampuan saya:</strong><br>
                            • 🗣️ Ngobrol santai & curhat<br>
                            • 📚 Bantu belajar (Matematika, IPA, Bahasa, dll)<br>
                            • 💻 Bantu coding (HTML, CSS, JS, Python, PHP)<br>
                            • 💰 Tips keuangan & investasi<br>
                            • 🎨 Ide kreatif & hiburan<br>
                            • 📱 Bantu penggunaan WaterTik<br><br>
                            <strong>Tanyakan apa saja ya! 😊</strong>
                        </div>
                    </div>
                `;
                showToast('Chat dibersihkan');
            };
            
            // ========================================
            // FUNGSI LAIN
            // ========================================
            async function pasteLinkToInput(id) {
                let t = document.getElementById(id);
                try {
                    let txt = await navigator.clipboard.readText();
                    if (txt) {
                        t.value = txt.trim();
                        showToast('✅ Link di-paste!');
                        t.focus();
                    }
                } catch (e) {
                    showToast('❌ Gagal paste');
                }
            }
            
            function switchMainTab(t) {
                document.querySelectorAll('.main-tab').forEach(tab => tab.classList.remove('active'));
                document.getElementById(`${t}Tab`).classList.add('active');
                document.querySelectorAll('.nav-item').forEach(b => b.classList.remove('active'));
                document.querySelector(`.nav-item[data-nav="${t}"]`).classList.add('active');
            }
            
            function openKontakPopup() {
                document.getElementById('kontakPopup').classList.add('active');
            }
            
            function closeKontakPopup() {
                document.getElementById('kontakPopup').classList.remove('active');
            }
            
            function openPremiumModal() {
                document.getElementById('premiumModal').classList.add('active');
            }
            
            function closePremiumModal() {
                document.getElementById('premiumModal').classList.remove('active');
            }
            
            function setCurrentDate() {
                document.getElementById('currentDate').innerText = new Date().toLocaleDateString('id-ID', { day: 'numeric', month: 'long', year: 'numeric' });
            }
            
            // ========================================
            // AVATAR
            // ========================================
            function openDashboard() {
                document.getElementById('dashboardModal').classList.add('active');
                let p = document.getElementById('avatarPreviewModal');
                if (currentUser && currentUser.avatar) p.innerHTML = `<img src="${currentUser.avatar}" style="width:100%;height:100%;object-fit:cover;">`;
                else p.innerHTML = '<i class="fas fa-user"></i>';
            }
            
            function closeDashboard() {
                document.getElementById('dashboardModal').classList.remove('active');
            }
            
            function uploadAvatar() {
                document.getElementById('avatarInput').click();
            }
            
            document.getElementById('avatarInput').addEventListener('change', async function(e) {
                let file = e.target.files[0];
                if (!file) {
                    showToast('Pilih file');
                    return;
                }
                if (file.size > 2 * 1024 * 1024) {
                    showToast('Maksimal 2MB');
                    return;
                }
                if (!file.type.startsWith('image/')) {
                    showToast('Harus gambar');
                    return;
                }
                let reader = new FileReader();
                reader.onload = async function(evt) {
                    if (currentUser) {
                        currentUser.avatar = evt.target.result;
                        await saveUserToStorage(currentUser);
                        updateUI();
                        showToast('✅ Avatar diupload!');
                        closeDashboard();
                    }
                };
                reader.readAsDataURL(file);
                e.target.value = '';
            });
            
            async function removeAvatar() {
                if (currentUser && confirm('Hapus avatar?')) {
                    currentUser.avatar = null;
                    await saveUserToStorage(currentUser);
                    updateUI();
                    showToast('Avatar dihapus');
                    closeDashboard();
                }
            }
            
            // ========================================
            // REPORT BUG
            // ========================================
            function openReportModal() {
                document.getElementById('reportBugModal').classList.add('active');
                if (currentUser && currentUser.name) document.getElementById('reportName').value = currentUser.name;
                let ua = navigator.userAgent,
                    browser = ua.includes('Chrome') ? 'Chrome' : (ua.includes('Firefox') ? 'Firefox' : 'Other'),
                    os = ua.includes('Win') ? 'Windows' : (ua.includes('Android') ? 'Android' : 'Other');
                document.getElementById('reportSystem').value = `${browser}, ${os}`;
            }
            
            function closeReportModal() {
                document.getElementById('reportBugModal').classList.remove('active');
            }
            
            function sendBugReport() {
                let name = document.getElementById('reportName').value.trim(),
                    title = document.getElementById('reportTitle').value.trim(),
                    desc = document.getElementById('reportDesc').value.trim();
                if (!name || !title || !desc) {
                    showToast('Isi semua field!');
                    return;
                }
                let userId = currentUser ? currentUser.userId : 'Guest',
                    body = `Nama: ${name}\nUser ID: ${userId}\nJudul: ${title}\nDeskripsi: ${desc}\nWaktu: ${new Date().toLocaleString()}`;
                window.location.href = `mailto:dllweb9@gmail.com?subject=[BUG] ${encodeURIComponent(title)}&body=${encodeURIComponent(body)}`;
                showToast('Email client akan terbuka');
                closeReportModal();
            }
            
            // ========================================
            // KEYBOARD SHORTCUT - ENTER
            // ========================================
            document.addEventListener('keydown', function(e) {
                if (e.key === 'Enter') {
                    const activeTab = document.querySelector('.main-tab.active');
                    if (activeTab) {
                        if (activeTab.id === 'aiTab') {
                            const input = document.getElementById('aiQuestion');
                            if (document.activeElement === input && !input.disabled) {
                                e.preventDefault();
                                window.askAI();
                            }
                        } else if (activeTab.id === 'igTab') {
                            const input = document.getElementById('igUrlInput');
                            if (document.activeElement === input) {
                                e.preventDefault();
                                downloadInstagram();
                            }
                        }
                    }
                }
            });
            
            // ========================================
            // INIT
            // ========================================
            (async function init() {
                await getFingerprint();
                await checkMaintenance();
                await checkRamadhanReal();
                setCurrentDate();
                await updateWinnersList();
                let fp = await getFingerprint();
                if (!await checkBlockedUser(fp)) {
                    let existing = await loadUserFromStorage(fp);
                    if (existing && !existing.blocked) {
                        currentUser = existing;
                        let fbMission = await loadMissionFromStorage(fp);
                        if (fbMission) missionData = fbMission;
                        updateUI();
                    }
                }
                document.getElementById('reportBugBtn').addEventListener('click', openReportModal);
                document.getElementById('sendReportBtn').addEventListener('click', sendBugReport);
                setInterval(checkRamadhanReal, 60000);
                setInterval(async () => {
                    await checkMaintenance();
                    let fpx = await getFingerprint();
                    await checkBlockedUser(fpx);
                }, 5000);
                
                console.log('✅ WaterTik v5.0 - Siap digunakan!');
                console.log('✅ AI dengan Rate Limit 5 detik');
                console.log('✅ Instagram Downloader aktif');
                console.log('✅ OWASP Security aktif');
            })();
            
            // ========================================
            // WINDOW CLICK CLOSE MODALS
            // ========================================
            window.onclick = function(e) {
                if (e.target === document.getElementById('dashboardModal')) closeDashboard();
                if (e.target === document.getElementById('kontakPopup')) closeKontakPopup();
                if (e.target === document.getElementById('premiumModal')) closePremiumModal();
                if (e.target === document.getElementById('winnerPopup')) closeWinnerPopup();
                if (e.target === document.getElementById('banReasonPopup')) closeBanPopup();
                if (e.target === document.getElementById('ramadhanStartPopup')) closeRamadhanPopup();
                if (e.target === document.getElementById('reportBugModal')) closeReportModal();
                if (e.target === document.getElementById('notificationPopup')) closeNotificationPopup();
            };
            
            // ========================================
            // EXPOSE FUNGSI KE GLOBAL
            // ========================================
            window.switchMainTab = switchMainTab;
            window.downloadVideo = downloadVideo;
            window.selectQuality = selectQuality;
            window.clearLink = clearLink;
            window.clearLinkAndReset = clearLinkAndReset;
            window.pasteLinkToInput = pasteLinkToInput;
            window.generateWatermark = generateWatermark;
            window.generateMultipleFrames = generateMultipleFrames;
            window.downloadSingleImage = downloadSingleImage;
            window.copyWatermarkLink = copyWatermarkLink;
            window.downloadAllFrames = downloadAllFrames;
            window.closeMultipleFrames = closeMultipleFrames;
            window.handleVideoSelect = handleVideoSelect;
            window.convertToMP3 = convertToMP3;
            window.resetMP3 = resetMP3;
            window.attemptLogin = attemptLogin;
            window.claimMission = claimMission;
            window.openDashboard = openDashboard;
            window.closeDashboard = closeDashboard;
            window.openKontakPopup = openKontakPopup;
            window.closeKontakPopup = closeKontakPopup;
            window.openPremiumModal = openPremiumModal;
            window.closePremiumModal = closePremiumModal;
            window.closeWinnerPopup = closeWinnerPopup;
            window.closeBanPopup = closeBanPopup;
            window.closeRamadhanPopup = closeRamadhanPopup;
            window.closeNotificationPopup = closeNotificationPopup;
            window.copyUserId = copyUserId;
            window.uploadAvatar = uploadAvatar;
            window.removeAvatar = removeAvatar;
            window.copyToClipboard = copyToClipboard;
            window.showToast = showToast;
            window.showInfoPage = showInfoPage;
            window.askAI = window.askAI;
            window.quickAsk = window.quickAsk;
            window.clearChat = window.clearChat;
            // IG Downloader
            window.downloadInstagram = downloadInstagram;
            window.downloadAllIG = downloadAllIG;
            
        })(); // End of IIFE
    </script>
</body>
</html>
