<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AVA Theater - Premium Ads Portal</title>
    <style>
        :root {
            --bg-color: #060810;
            --anime-gradient: linear-gradient(135deg, #ff6b00, #ff0055, #7000ff);
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            background-color: var(--bg-color);
            color: #ffffff;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 40px 15px;
            position: relative;
            overflow-x: hidden;
        }

        /* پس‌زمینه کهکشانی متحرک نئونی اختصاصی */
        body::before {
            content: "";
            position: fixed;
            top: 0; left: 0; width: 100%; height: 200%;
            background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="140" height="140" viewBox="0 0 140 140"><text x="15" y="30" fill="rgba(0, 240, 255, 0.35)" font-size="18">🎥</text><text x="85" y="25" fill="rgba(0, 255, 170, 0.30)" font-size="16">🎬</text><text x="50" y="65" fill="rgba(0, 240, 255, 0.30)" font-size="15">📺</text><text x="110" y="70" fill="rgba(0, 255, 170, 0.35)" font-size="17">🎞️</text><text x="75" y="115" fill="rgba(0, 255, 170, 0.38)" font-size="18">🍿</text><text x="115" y="120" fill="rgba(0, 240, 255, 0.30)" font-size="15">🕶️</text><text x="80" y="75" fill="rgba(255, 255, 255, 0.35)" font-size="10">✨</text></svg>');
            background-repeat: repeat;
            z-index: -1;
            animation: spaceScroll 30s linear infinite;
        }

        @keyframes spaceScroll {
            0% { transform: translateY(0); }
            100% { transform: translateY(-50%); }
        }

        /* کانتینر اصلی برای چیدمان عمودی تبلیغات */
        .ads-list-container {
            width: 100%;
            max-width: 500px;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 50px; /* ایجاد فاصله مناسب و شیک بین هر جایگاه تبلیغاتی */
            z-index: 10;
        }

        /* هولدرهای اختصاصی برای مدیریت بارگذاری تبلیغات */
        .native-ad-wrapper {
            width: 100%;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 80px; /* فضای رزرو شده برای جلوگیری از پرش صفحه هنگام رفرش */
        }
    </style>
</head>
<body>

    <div class="ads-list-container">

        <div class="native-ad-wrapper" id="ad-slot-1">
            <script async="async" data-cfasync="false" src="https://pl29741961.effectivecpmnetwork.com/46fa53bab184d6979bf4dbeee413d25f/invoke.js"></script>
            <div id="container-46fa53bab184d6979bf4dbeee413d25f"></div>
        </div>

        <div class="native-ad-wrapper" id="ad-slot-2">
            <script async="async" data-cfasync="false" src="https://speedingdeadlyplays.com/0d866ffd8b3f981a046a0ed94c6cefd6/invoke.js"></script>
            <div id="container-0d866ffd8b3f981a046a0ed94c6cefd6"></div>
        </div>

        <div class="native-ad-wrapper" id="ad-slot-3">
            <script async="async" data-cfasync="false" src="https://speedingdeadlyplays.com/a369b6bbe836a87b50274bebdab286c1/invoke.js"></script>
            <div id="container-a369b6bbe836a87b50274bebdab286c1"></div>
        </div>

        <div class="native-ad-wrapper" id="ad-slot-4">
            <script async="async" data-cfasync="false" src="https://speedingdeadlyplays.com/5b664706bd72b8402ee0b2e55cf5b2a2/invoke.js"></script>
            <div id="container-5b664706bd72b8402ee0b2e55cf5b2a2"></div>
        </div>

    </div>

    <script>
        // دیتابیس کانفیگ اسکریپت‌ها و آیدی کانتینرها برای رفرش خودکار
        const adsConfig = [
            { slotId: 'ad-slot-1', containerId: 'container-46fa53bab184d6979bf4dbeee413d25f', src: 'https://pl29741961.effectivecpmnetwork.com/46fa53bab184d6979bf4dbeee413d25f/invoke.js' },
            { slotId: 'ad-slot-2', containerId: 'container-0d866ffd8b3f981a046a0ed94c6cefd6', src: 'https://speedingdeadlyplays.com/0d866ffd8b3f981a046a0ed94c6cefd6/invoke.js' },
            { slotId: 'ad-slot-3', containerId: 'container-a369b6bbe836a87b50274bebdab286c1', src: 'https://speedingdeadlyplays.com/a369b6bbe836a87b50274bebdab286c1/invoke.js' },
            { slotId: 'ad-slot-4', containerId: 'container-5b664706bd72b8402ee0b2e55cf5b2a2', src: 'https://speedingdeadlyplays.com/5b664706bd72b8402ee0b2e55cf5b2a2/invoke.js' }
        ];

        // تابع اصلی بازسازی و بارگذاری مجدد زنده اسکریپت تبلیغات
        function refreshAllNativeAds() {
            adsConfig.forEach(ad => {
                const wrapper = document.getElementById(ad.slotId);
                if (wrapper) {
                    wrapper.innerHTML = ''; // پاکسازی بنر قدیمی جهت فراخوانی مجدد ایمپرشن جدید
                    
                    const scriptNode = document.createElement('script');
                    scriptNode.async = true;
                    scriptNode.setAttribute('data-cfasync', 'false');
                    scriptNode.src = ad.src;
                    
                    const divNode = document.createElement('div');
                    divNode.id = ad.containerId;
                    
                    wrapper.appendChild(scriptNode);
                    wrapper.appendChild(divNode);
                }
            });
        }

        // فعال‌سازی تایمر خودکار روی ۶۰۰۰۰ میلی‌ثانیه (دقیقاً هر ۱ دقیقه یک‌بار رفرش زنده)
        setInterval(refreshAllNativeAds, 60000);
    </script>
</body>
</html>
