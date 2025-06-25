<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ديوان الشعراء</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        body {
            background: linear-gradient(135deg, #1a2a6c, #b21f1f, #fdbb2d);
            color: #2c3e50;
            line-height: 1.6;
            min-height: 100vh;
            padding: 20px;
        }
        .container {
            max-width: 1200px;
            margin: 0 auto;
        }
        header {
            text-align: center;
            padding: 2rem 0;
            margin-bottom: 2rem;
            background: rgba(255, 255, 255, 0.9);
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
        }
        h1 {
            font-size: 3.5rem;
            margin-bottom: 1rem;
            color: #8B0000;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
        }
        .tabs {
            display: flex;
            justify-content: center;
            margin-bottom: 2rem;
            background: white;
            border-radius: 50px;
            padding: 10px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        .tab-btn {
            padding: 15px 40px;
            font-size: 1.3rem;
            font-weight: bold;
            background: none;
            border: none;
            cursor: pointer;
            transition: all 0.3s ease;
            border-radius: 50px;
            margin: 0 5px;
        }
        .tab-btn.active {
            background: #8B0000;
            color: white;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }
        .content {
            display: none;
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.25);
            min-height: 500px;
        }
        .content.active {
            display: block;
            animation: fadeIn 0.8s ease;
        }
        .poets-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 25px;
            margin-top: 20px;
        }
        .poet-card {
            background: linear-gradient(135deg, #f5f7fa, #e4e7ec);
            border-radius: 15px;
            overflow: hidden;
            transition: transform 0.4s, box-shadow 0.4s;
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.1);
            cursor: pointer;
        }
        .poet-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2);
        }
        .poet-img {
            height: 220px;
            background-size: cover;
            background-position: center;
        }
        .poet-info {
            padding: 20px;
            text-align: center;
        }
        .poet-name {
            font-size: 1.8rem;
            margin-bottom: 10px;
            color: #8B0000;
        }
        .poet-bio {
            font-size: 1.1rem;
            color: #555;
            line-height: 1.5;
        }
        .poems-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
            gap: 25px;
            margin-top: 20px;
        }
        .poem-card {
            background: linear-gradient(to bottom right, #fff, #f8f9fa);
            border-radius: 15px;
            padding: 25px;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.08);
            transition: all 0.3s ease;
            border: 1px solid #eee;
        }
        .poem-card:hover {
            transform: scale(1.02);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.15);
        }
        .poem-title {
            font-size: 1.8rem;
            color: #8B0000;
            margin-bottom: 15px;
            padding-bottom: 10px;
            border-bottom: 2px dashed #e0e0e0;
        }
        .poem-content {
            font-size: 1.3rem;
            line-height: 1.8;
            color: #333;
            font-style: italic;
            white-space: pre-line;
        }
        .poem-meta {
            margin-top: 20px;
            font-size: 1.1rem;
            color: #666;
            text-align: left;
            padding-top: 15px;
            border-top: 1px dashed #e0e0e0;
        }
        footer {
            text-align: center;
            padding: 30px;
            margin-top: 40px;
            color: white;
            font-size: 1.2rem;
            background: rgba(0, 0, 0, 0.4);
            border-radius: 15px;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        @media (max-width: 768px) {
            .poets-grid, .poems-container {
                grid-template-columns: 1fr;
            }
            h1 {
                font-size: 2.5rem;
            }
            .tab-btn {
                padding: 12px 25px;
                font-size: 1.1rem;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>ديـــوان الشــعراء</h1>
            <p>منصة تجمع إبداعات الشعر العربي عبر العصور</p>
        </header>

        <div class="tabs">
            <button class="tab-btn active" data-tab="poets">قائمة الشعراء</button>
            <button class="tab-btn" data-tab="poems">القصائد</button>
        </div>

        <!-- واجهة الشعراء -->
        <div id="poets" class="content active">
            <div class="poets-grid" id="poets-container">
                <!-- سيتم ملؤه بالشعراء من خلال الجافاسكريبت -->
            </div>
        </div>

        <!-- واجهة القصائد -->
        <div id="poems" class="content">
            <div class="poems-container" id="poems-container">
                <!-- سيتم ملؤه بالقصائد من خلال الجافاسكريبت -->
            </div>
        </div>

        <footer>
            <p>جميع الحقوق محفوظة © 2023 | ديوان الشعراء | القصائد مخزنة داخل الكود</p>
        </footer>
    </div>

    <script>
        // قاعدة البيانات الكاملة للشعراء والقصائد مخزنة داخل الكود
        const poetryData = {
            poets: [
                {
                    id: 1,
                    name: "المتنبي",
                    bio: "أعظم شعراء العربية، اشتهر بقوة ألفاظه وبلاغة معانيه",
                    era: "العصر العباسي",
                    img: "linear-gradient(45deg, #6a11cb, #2575fc)"
                },
                {
                    id: 2,
                    name: "أحمد شوقي",
                    bio: "أمير الشعراء، جمع بين الثقافة العربية والغربية",
                    era: "العصر الحديث",
                    img: "linear-gradient(45deg, #ff416c, #ff4b2b)"
                },
                {
                    id: 3,
                    name: "نزار قباني",
                    bio: "شاعر الحب والمرأة، تميز بأسلوبه الرومانسي الجريء",
                    era: "القرن العشرين",
                    img: "linear-gradient(45deg, #00c6ff, #0072ff)"
                },
                {
                    id: 4,
                    name: "محمود درويش",
                    bio: "شاعر المقاومة الفلسطينية، مزج بين الذاتي والوطني",
                    era: "القرن العشرين",
                    img: "linear-gradient(45deg, #11998e, #38ef7d)"
                }
            ],
            poems: [
                {
                    id: 1,
                    poetId: 1,
                    title: "على قدر أهل العزم",
                    content: `عَلَى قَدْرِ أَهْلِ العَزْمِ تَأْتِي العَزَائِمُ
وَتأْتِي عَلَى قَدْرِ الكِرَامِ المَكَارِمُ
وتَعْظُمُ فِي عَيْنِ الصّغِيرِ صِغَارُهَا
وتَصْغُرُ فِي عَيْنِ العَظِيمِ العَظَائِمُ`,
                    year: 350
                },
                {
                    id: 2,
                    poetId: 2,
                    title: "نهج البردة",
                    content: `ريمٌ على القاعِ بين البانِ والعلمِ
أحلَ سفكَ دمي في الأشهرِ الحرمِ
يا لائمي في هواه والهوى قدرٌ
لو شفَّك الوجد لم تعذل ولم تلمِ`,
                    year: 1910
                },
                {
                    id: 3,
                    poetId: 3,
                    title: "رسالة حب",
                    content: `أحبك..
أحبك حتي الثمالة
حتي دخول السجن
حتي الموت
أحبك حتي الجنون
أحبك حتي السخرية مني
حتي الاستشهاد في سبيل عينيك`,
                    year: 1961
                },
                {
                    id: 4,
                    poetId: 4,
                    title: "سجل أنا عربي",
                    content: `سجِّل!
أنا عربي
ورقمُ بطاقتي خمسونَ ألف
وأطفالي ثمانيةٌ
وتاسعُهم سيأتي بعدَ صيف!
فهل تغضب؟`,
                    year: 1964
                },
                {
                    id: 5,
                    poetId: 1,
                    title: "الخيل والليل",
                    content: `الخَيْلُ وَاللّيْلُ وَالبَيْداءُ تَعرِفُني
وَالسّيفُ وَالرّمحُ والقرْطاسُ وَالقَلَمُ
سَلاَمٌ مِنْ صَبا بَرَدى أَرَقُّ وَدَمْعٌ
يُذيبُ الحَديدَ قَبلَ الزَّبَرْجَدِ`,
                    year: 347
                }
            ]
        };

        // تهيئة الموقع
        document.addEventListener('DOMContentLoaded', function() {
            // إنشاء واجهة الشعراء
            renderPoets();
            
            // إنشاء واجهة القصائد
            renderPoems();
            
            // إضافة أحداث للأزرار
            setupTabs();
        });

        function renderPoets() {
            const container = document.getElementById('poets-container');
            container.innerHTML = '';
            
            poetryData.poets.forEach(poet => {
                const card = document.createElement('div');
                card.className = 'poet-card';
                card.innerHTML = `
                    <div class="poet-img" style="background: ${poet.img}"></div>
                    <div class="poet-info">
                        <h2 class="poet-name">${poet.name}</h2>
                        <p class="poet-era">${poet.era}</p>
                        <p class="poet-bio">${poet.bio}</p>
                    </div>
                `;
                container.appendChild(card);
            });
        }

        function renderPoems() {
            const container = document.getElementById('poems-container');
            container.innerHTML = '';
            
            poetryData.poems.forEach(poem => {
                const poet = poetryData.poets.find(p => p.id === poem.poetId);
                const card = document.createElement('div');
                card.className = 'poem-card';
                card.innerHTML = `
                    <h3 class="poem-title">${poem.title}</h3>
                    <div class="poem-content">${poem.content}</div>
                    <div class="poem-meta">
                        <strong>الشاعر:</strong> ${poet.name}<br>
                        <strong>العام:</strong> ${poem.year} م
                    </div>
                `;
                container.appendChild(card);
            });
        }

        function setupTabs() {
            const tabs = document.querySelectorAll('.tab-btn');
            
            tabs.forEach(tab => {
                tab.addEventListener('click', () => {
                    // إزالة النشاط من جميع الأزرار
                    tabs.forEach(t => t.classList.remove('active'));
                    
                    // إضافة النشاط للزر المختار
                    tab.classList.add('active');
                    
                    // إخفاء جميع المحتويات
                    document.querySelectorAll('.content').forEach(c => {
                        c.classList.remove('active');
                    });
                    
                    // إظهار المحتوى المختار
                    const tabId = tab.getAttribute('data-tab');
                    document.getElementById(tabId).classList.add('active');
                });
            });
        }
    </script>
</body>
</html>
