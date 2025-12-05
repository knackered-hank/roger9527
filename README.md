# roger9527
<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Roger - 遊戲與實況的傳奇高金生</title>
    <style>
        /* ===================================
        CSS 樣式區
        ===================================
        */
        :root {
            --primary-color: #007aff;
            --dark-bg: #1d1d1f;
            --light-text: #f5f5f7;
            --dark-text: #1d1d1f;
            --font-serif: 'SF Pro Display', 'Helvetica Neue', Helvetica, Arial, sans-serif;
            scroll-behavior: smooth;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: var(--font-serif);
        }

        body {
            background-color: #000;
            color: var(--light-text);
            overflow-x: hidden;
        }

        /* 導覽列 */
        .navbar {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 44px;
            background-color: rgba(0, 0, 0, 0.8);
            backdrop-filter: blur(10px);
            z-index: 1000;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        .navbar a {
            color: var(--light-text);
            text-decoration: none;
            margin: 0 15px;
            font-size: 14px;
            opacity: 0.8;
            transition: opacity 0.3s;
        }
        .navbar a:hover {
            opacity: 1;
        }

        /* 區塊通用樣式 */
        .section {
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            position: relative;
            overflow: hidden;
            padding: 100px 20px;
        }

        .section h2 {
            font-size: 56px;
            font-weight: 700;
            margin-bottom: 20px;
        }

        .section p {
            font-size: 24px;
            max-width: 800px;
            margin-bottom: 30px;
            line-height: 1.5;
        }

        .cta-button {
            display: inline-block;
            background-color: var(--primary-color);
            color: #fff;
            padding: 12px 25px;
            border-radius: 999px;
            text-decoration: none;
            font-weight: 600;
            font-size: 17px;
            transition: background-color 0.3s;
        }
        .cta-button:hover {
            background-color: #006ee6;
        }

        /* 1. 主視覺 - 沉浸式標題 */
        #hero {
            background-color: #000;
            color: #fff;
            height: 100vh;
        }

        #hero h1 {
            font-size: 80px;
            font-weight: 900;
            letter-spacing: -0.5px;
            opacity: 0;
            transform: translateY(20px);
        }
        
        #hero h3 {
            font-size: 32px;
            font-weight: 500;
            opacity: 0;
            transform: translateY(20px);
        }

        /* 2. 特點介紹 - 視覺卡片 */
        #features {
            background-color: var(--dark-bg);
            color: var(--light-text);
        }
        .feature-card {
            max-width: 1000px;
            width: 100%;
            margin: 40px 0;
            display: flex;
            align-items: center;
            justify-content: space-between;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 20px;
            padding: 40px;
            opacity: 0;
            transform: translateY(50px);
        }

        .feature-card:nth-child(even) {
            flex-direction: row-reverse;
        }

        .feature-text {
            flex: 1;
            padding: 0 40px;
            text-align: left;
        }

        .feature-text h3 {
            font-size: 36px;
            font-weight: 700;
            color: var(--primary-color);
            margin-bottom: 15px;
        }

        .feature-text p {
            font-size: 20px;
            margin-bottom: 0;
        }

        .feature-image {
            width: 400px;
            height: 250px;
            background-color: #333;
            border-radius: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 16px;
            color: #ccc;
            overflow: hidden;
        }
        .feature-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        /* 3. 傳奇語錄區 (已修改為靜態顯示) */
        #immersive-scroll {
            background-color: #fff;
            color: var(--dark-text);
            /* 移除 300vh，讓其高度由內容決定 */
            min-height: 50vh; 
            padding: 100px 20px;
            /* 確保內容在區塊內居中 */
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
        }

        /* 新增的語錄樣式，用於固定顯示在頁面中央 */
        .static-quote {
            font-size: 96px;
            font-weight: 900;
            color: var(--dark-text);
            margin: 20px 0; /* 給予上下間距 */
            line-height: 1.2;
            text-align: center;
        }

        /* 4. 遊戲生涯 - 圖片畫廊 */
        #gallery {
            background-color: var(--dark-bg);
            padding: 150px 0;
        }

        .gallery-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 20px;
            max-width: 1200px;
            margin-top: 50px;
        }

        .gallery-item {
            width: 100%;
            height: 300px;
            background-color: #444;
            border-radius: 10px;
            overflow: hidden;
            opacity: 0.1;
            transform: scale(0.9);
            transition: all 0.5s;
        }

        .gallery-item.visible {
            opacity: 1;
            transform: scale(1);
        }

        .gallery-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        /* 5. 結尾行動呼籲 */
        #cta-end {
            background-color: #000;
            color: #fff;
        }
        #cta-end h2 {
            font-size: 64px;
        }

        /* 註腳 */
        footer {
            background-color: #111;
            padding: 40px 20px;
            font-size: 14px;
            color: #888;
        }

        /* RWD 調整 */
        @media (max-width: 768px) {
            .section h2 {
                font-size: 40px;
            }
            .section p {
                font-size: 18px;
            }
            #hero h1 {
                font-size: 50px;
            }
            #hero h3 {
                font-size: 24px;
            }
            .feature-card {
                flex-direction: column;
                padding: 20px;
            }
            .feature-card:nth-child(even) {
                flex-direction: column;
            }
            .feature-text {
                padding: 20px 0;
                text-align: center;
            }
            .feature-image {
                width: 100%;
                height: 200px;
            }
            .gallery-grid {
                grid-template-columns: repeat(2, 1fr);
            }
            .static-quote {
                font-size: 56px; /* 行動版字體縮小 */
            }
        }
    </style>
</head>
<body>

    <nav class="navbar">
        <a href="#hero">首頁</a>
        <a href="#features">個人特色</a>
        <a href="#immersive-scroll">傳奇語錄</a>
        <a href="#gallery">經典時刻</a>
        <a href="#cta-end">追蹤他</a>
    </nav>

    <section id="hero" class="section">
        <h3 id="hero-subheading">一位傳奇、一個時代。</h3>
        <h1 id="hero-heading">Roger</h1>
        <p>從爐石戰記到實況圈的頂峰，他的風格無人能複製。</p>
        <a href="#features" class="cta-button">探索羅傑的宇宙</a>
    </section>

    <section id="features" class="section">
        <h2>絕無僅有的實況風格</h2>
        <p>幽默、真實、反應快。羅傑總能在每個遊戲中找到獨特的「節目效果」。</p>

        <div class="feature-card feature-1">
            <div class="feature-text">
                <h3>爐石戰記的傳奇</h3>
                <p>他曾是臺灣爐石界最受尊敬的選手之一，以精湛的技術和獨特的牌組構築聞名，更曾代表台灣在國際舞台上發光發熱，詳見綠拉札事件。</p>
            </div>
            <div class="feature-image">
                <img src="https://bnetcmsus-a.akamaihd.net/cms/gallery/GTICL2DQ51FF1412323226298.jpg" alt="羅傑-爐石傳奇">
            </div>
        </div>

        <div class="feature-card feature-2">
            <div class="feature-text">
                <h3>聊天室的鬼才互動</h3>
                <p>他獨特的「羅氏幽默」總能讓聊天室沸騰。他與觀眾間的互嗆與對話，本身就是一場高水準的表演。</p>
            </div>
            <div class="feature-image">
                <img src="https://img.league-funny.com/imgur/17277840606_n.png" alt="羅傑-幽默大師">
            </div>
        </div>

        <div class="feature-card feature-3">
            <div class="feature-text">
                <h3>「節目效果」製造機</h3>
                <p>無論是爐石、英雄聯盟還是各種合作實況，羅傑總有辦法讓平淡的流程變得爆笑且引人入勝。他是真正的流量密碼。</p>
            </div>
            <div class="feature-image">
                <img src="https://i.imgur.com/bSTJWsc.jpg" alt="羅傑-節目效果">
            </div>
        </div>
    </section>

    <section id="immersive-scroll" class="section">
        <div class="static-quote">
            「帥哥登場！」 - 直播的霸氣開場白
        </div>
        <div class="static-quote">
            「你是2486！」 - 時事全沾鍋的自信
        </div>
    </section>

    <section id="gallery" class="section">
        <h2>經典時刻回顧</h2>
        <p>那些在實況中創造的傳奇瞬間，成為了無數觀眾的共同回憶。</p>

        <div class="gallery-grid">
            <div class="gallery-item">
                <img src="https://scontent.ftpe8-4.fna.fbcdn.net/v/t39.30808-6/480905138_644615718103864_5277370975872205119_n.jpg?_nc_cat=104&_nc_cb=99be929b-f3b7c874&ccb=1-7&_nc_sid=aa7b47&_nc_ohc=qR8i_mPj-VIQ7kNvwHcES2Z&_nc_oc=AdkVpVQCG-YEd4MZ6Or8aACVBQa93lobOob87b0GQWIXB3owpMRKu0RNs8b_NVZjh1Q&_nc_zt=23&_nc_ht=scontent.ftpe8-4.fna&_nc_gid=6B0o1SnuPSF8HVBTAl4Txw&oh=00_AflIXBV0cND1MjuRrr6Bz8YBHZki6ij0iNuEH4ELM8iacg&oe=69385875" alt="現場活動照片">
            </div>
            <div class="gallery-item">
                <img src="https://media.nownews.com/nn_media/thumbnail/2025/04/1746009022712-2cd5a2c17e78440fb861a3bf117bc0e4-800x504.webp?unShow=false" alt="經典時刻 2">
            </div>
            <div class="gallery-item">
                <img src="https://img.league-funny.com/imgur/17190313244_n.png" alt="經典時刻 3">
            </div>
        </div>
    </section>

    <section id="cta-end" class="section">
        <h2>別只是聽說，親自瞻仰羅傑的魅力。</h2>
        <p>立即殺去檢舉他的 Twitch 頻道，不錯過任何一個傳奇時刻。</p>
        <a href="https://www.twitch.tv/roger9527" target="_blank" class="cta-button">前往 Twitch 頻道</a>
    </section>

    <footer>
        <p>&copy; 2025 Roger Fan Site. All rights reserved. 僅為懷念與致哀目的製作，非官方網站。</p>
    </footer>


    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const heroHeading = document.getElementById('hero-heading');
            const heroSubheading = document.getElementById('hero-subheading');
            const featureCards = document.querySelectorAll('.feature-card');
            // 移除了 scrollQuotes 相關定義
            const galleryItems = document.querySelectorAll('.gallery-item');
            

            // 1. Hero 區塊動畫 (載入即出現)
            setTimeout(() => {
                heroHeading.style.transition = 'opacity 1s, transform 1s';
                heroSubheading.style.transition = 'opacity 1s, transform 1s 0.3s';
                heroHeading.style.opacity = '1';
                heroHeading.style.transform = 'translateY(0)';
                heroSubheading.style.opacity = '1';
                heroSubheading.style.transform = 'translateY(0)';
            }, 100);


            // 2. 滾動觀察器
            const observerOptions = {
                root: null,
                rootMargin: '0px',
                threshold: 0.2
            };

            const observer = new IntersectionObserver((entries, observer) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        // 特點卡片 (Feature Cards) 漸入
                        if (entry.target.classList.contains('feature-card')) {
                            entry.target.style.transition = 'opacity 1s, transform 1s';
                            entry.target.style.opacity = '1';
                            entry.target.style.transform = 'translateY(0)';
                            observer.unobserve(entry.target);
                        }
                        
                        // 畫廊圖片 (Gallery Items) 彈出
                        if (entry.target.classList.contains('gallery-item')) {
                            entry.target.classList.add('visible');
                        }
                    } else {
                         // 離開視圖時，Gallery items 重置
                        if (entry.target.classList.contains('gallery-item')) {
                            entry.target.classList.remove('visible');
                        }
                    }
                });
            }, observerOptions);

            // 註冊觀察器
            featureCards.forEach(card => observer.observe(card));
            galleryItems.forEach(item => observer.observe(item));

            // 移除了 3. 沉浸式滾動效果 (Immersive Scroll) 的所有 JavaScript 邏輯
            
        });
    </script>
</body>
</html>
