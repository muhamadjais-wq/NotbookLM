# NotbookLM
<!DOCTYPE html>
<html lang="ms" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Menguasai NotebookLM: Panduan Interaktif</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Chosen Palette: "Professional Tech" (Tailwind Stone neutrals with Blue accents) -->
    <!-- Application Structure Plan: The SPA abandons the linear 6-slide structure for a 5-section thematic/functional flow: [Pengenalan, Input, Output, Interaksi, Arahan]. This is navigated by a sticky top bar with smooth scrolling. This structure allows users to explore features based on their own questions (What is it? How do I add info? What do I get out? How do I interact? How do I use it well?) which is more intuitive for a web app than a passive presentation. -->
    <!-- Visualization & Content Choices:
        - Report Info (Slide 2: Source Types) -> Goal: Inform -> Viz: HTML Card Grid (w/ Unicode icons) -> Interaction: Hover -> Justification: Visually separates and presents each allowed input type clearly.
        - Report Info (Slide 3: Output Types) -> Goal: Organize/Inform -> Viz: JS-powered Tabbed Interface -> Interaction: Click tabs (Peta Minda, Garis Masa, etc.) to reveal descriptions -> Justification: More interactive and space-efficient than a long bullet list.
        - Report Info (Slides 4/5: Learning Tools) -> Goal: Organize/Compare -> Viz: 2-Column Grid w/ native <details> accordions -> Interaction: Click to expand/collapse -> Justification: Groups related features (Integrity vs. Audio) and hides details until requested.
        - Report Info (Slide 6: Prompting) -> Goal: Inform (Process) -> Viz: HTML/CSS 3-Step Process Flow Diagram -> Interaction: None (visual only) -> Justification: Clearly visualizes the 3-step sequence.
        - Report Info (Slide 6: Warnings) -> Goal: Inform (Warn) -> Viz: HTML/CSS Callout Box -> Interaction: None -> Justification: Visually distinct block for important "what not to do" info.
        -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <style>
        body {
            font-family: 'Inter', sans-serif;
        }
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap');
        
        .nav-link.active {
            @apply text-blue-600 border-blue-600;
        }
        .tab-button.active {
            @apply border-blue-600 text-blue-600;
        }
        .tab-content {
            display: none;
        }
        .tab-content.active {
            display: block;
        }
        details[open] summary ~ * {
            animation: sweep .5s ease-in-out;
        }
        @keyframes sweep {
            0% {opacity: 0; transform: translateY(-10px)}
            100% {opacity: 1; transform: translateY(0)}
        }
    </style>
</head>
<body class="bg-stone-50 text-stone-800 antialiased">

    <header class="sticky top-0 z-50 w-full bg-white/90 backdrop-blur-md shadow-sm border-b border-stone-200">
        <nav class="container mx-auto px-4 py-3 flex justify-between items-center">
            <div class="text-xl font-bold text-stone-900">
                NotebookLM
            </div>
            <div class="hidden md:flex space-x-1 items-center">
                <a href="#pengenalan" class="nav-link text-stone-600 hover:text-blue-600 px-3 py-2 border-b-2 border-transparent transition-all duration-300">Pengenalan</a>
                <a href="#input" class="nav-link text-stone-600 hover:text-blue-600 px-3 py-2 border-b-2 border-transparent transition-all duration-300">Input (Sumber)</a>
                <a href="#output" class="nav-link text-stone-600 hover:text-blue-600 px-3 py-2 border-b-2 border-transparent transition-all duration-300">Output (Laporan)</a>
                <a href="#interaksi" class="nav-link text-stone-600 hover:text-blue-600 px-3 py-2 border-b-2 border-transparent transition-all duration-300">Interaksi (Pembelajaran)</a>
                <a href="#arahan" class="nav-link text-stone-600 hover:text-blue-600 px-3 py-2 border-b-2 border-transparent transition-all duration-300">Amalan Terbaik</a>
            </div>
            <button id="mobile-menu-btn" class="md:hidden p-2 rounded-md text-stone-600 hover:bg-stone-100">
                <span class="text-2xl">☰</span>
            </button>
        </nav>
        <div id="mobile-menu" class="hidden md:hidden absolute top-full left-0 w-full bg-white shadow-lg py-2">
            <a href="#pengenalan" class="nav-link block text-stone-600 hover:bg-stone-50 px-4 py-3">Pengenalan</a>
            <a href="#input" class="nav-link block text-stone-600 hover:bg-stone-50 px-4 py-3">Input (Sumber)</a>
            <a href="#output" class="nav-link block text-stone-600 hover:bg-stone-50 px-4 py-3">Output (Laporan)</a>
            <a href="#interaksi" class="nav-link block text-stone-600 hover:bg-stone-50 px-4 py-3">Interaksi (Pembelajaran)</a>
            <a href="#arahan" class="nav-link block text-stone-600 hover:bg-stone-50 px-4 py-3">Amalan Terbaik</a>
        </div>
    </header>

    <main class="container mx-auto px-4 py-8 md:py-16">

        <section id="pengenalan" class="min-h-[80vh] flex flex-col justify-center text-center">
            <h1 class="text-4xl md:text-6xl font-bold text-stone-900 mb-4">Menguasai NotebookLM</h1>
            <p class="text-xl md:text-2xl text-blue-700 font-semibold mb-8">Pembantu Penyelidikan AI Berasaskan Sumber Anda</p>
            <p class="max-w-3xl mx-auto text-lg text-stone-700 mb-12">
                Selamat datang ke panduan interaktif untuk NotebookLM. Bahagian ini memperkenalkan konsep teras di sebalik alat yang hebat ini. Terokai bahagian lain untuk menyelami cara ia mengurus sumber, menjana cerapan, dan menyokong pembelajaran anda.
            </p>
            <div class="grid md:grid-cols-2 gap-6 max-w-4xl mx-auto text-left">
                <div class="bg-white p-6 rounded-lg shadow-md border border-stone-200">
                    <h3 class="text-xl font-semibold text-stone-900 mb-2">🧠 Grounded AI (AI Berasaskan Sumber)</h3>
                    <p class="text-stone-700">NotebookLM direka untuk hanya menggunakan maklumat daripada sumber yang ANDA muat naik. Ia tidak akan mencari di web atau menggunakan pengetahuan luar melainkan diarahkan.</p>
                </div>
                <div class="bg-white p-6 rounded-lg shadow-md border border-stone-200">
                    <h3 class="text-xl font-semibold text-stone-900 mb-2">🚫 Tiada Halusinasi</h3>
                    <p class="text-stone-700">Dengan hanya merujuk sumber anda, NotebookLM secara efektif mengelakkan risiko "halusinasi" AI (mereka-reka fakta), memastikan integriti fakta dalam setiap jawapan.</p>
                </div>
            </div>
        </section>

        <section id="input" class="py-16 md:py-24">
            <h2 class="text-3xl md:text-4xl font-bold text-center text-stone-900 mb-4">Membina Basis Pengetahuan Anda</h2>
            <p class="text-lg text-center text-stone-700 max-w-3xl mx-auto mb-12">
                Kekuatan NotebookLM bermula dengan sumber yang anda sediakan. Ia boleh mengintegrasikan pelbagai jenis format ke dalam satu "Basis Pengetahuan Peribadi" yang komprehensif, membolehkan AI merujuk silang semua maklumat anda.
            </p>
            <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-5 gap-6 max-w-6xl mx-auto">
                <div class="bg-white p-6 rounded-lg shadow-md border border-stone-200 text-center transition-transform hover:scale-105 duration-300">
                    <span class="text-5xl mb-3 block">📄</span>
                    <h3 class="text-lg font-semibold text-stone-900">Fail PDF</h3>
                </div>
                <div class="bg-white p-6 rounded-lg shadow-md border border-stone-200 text-center transition-transform hover:scale-105 duration-300">
                    <span class="text-5xl mb-3 block">📑</span>
                    <h3 class="text-lg font-semibold text-stone-900">Google Docs & Slides</h3>
                </div>
                <div class="bg-white p-6 rounded-lg shadow-md border border-stone-200 text-center transition-transform hover:scale-105 duration-300">
                    <span class="text-5xl mb-3 block">🌐</span>
                    <h3 class="text-lg font-semibold text-stone-900">Pautan Web & Artikel</h3>
                </div>
                <div class="bg-white p-6 rounded-lg shadow-md border border-stone-200 text-center transition-transform hover:scale-105 duration-300">
                    <span class="text-5xl mb-3 block">📺</span>
                    <h3 class="text-lg font-semibold text-stone-900">Video YouTube</h3>
                    <p class="text-sm text-stone-600">(dengan transkrip)</p>
                </div>
                <div class="bg-white p-6 rounded-lg shadow-md border border-stone-200 text-center transition-transform hover:scale-105 duration-300 col-span-2 md:col-span-1">
                    <span class="text-5xl mb-3 block">🎧</span>
                    <h3 class="text-lg font-semibold text-stone-900">Fail Audio</h3>
                    <p class="text-sm text-stone-600">(Kuliah, Mesyuarat)</p>
                </div>
            </div>
        </section>

        <section id="output" class="py-16 md:py-24 bg-white rounded-xl shadow-lg border border-stone-200">
            <h2 class="text-3xl md:text-4xl font-bold text-center text-stone-900 mb-4">Menjana Cerapan & Laporan Tersusun</h2>
            <p class="text-lg text-center text-stone-700 max-w-3xl mx-auto mb-12">
                Setelah sumber anda dimuat naik, NotebookLM cemerlang dalam mensintesis maklumat. Ia bukan sekadar ringkasan; ia mencipta output berstruktur yang membantu anda memahami bahan kompleks dengan pantas. Klik tab di bawah untuk meneroka format output yang berbeza.
            </p>
            <div class="max-w-4xl mx-auto">
                <div class="flex flex-wrap justify-center border-b border-stone-300 mb-6">
                    <button class="tab-button text-lg font-semibold px-6 py-3 border-b-2 transition-all duration-300 active" data-tab="peta-minda">Peta Minda</button>
                    <button class="tab-button text-lg font-semibold px-6 py-3 border-b-2 border-transparent text-stone-600 hover:text-stone-900 transition-all duration-300" data-tab="garis-masa">Garis Masa</button>
                    <button class="tab-button text-lg font-semibold px-6 py-3 border-b-2 border-transparent text-stone-600 hover:text-stone-900 transition-all duration-300" data-tab="faq">Soalan Lazim (FAQ)</button>
                    <button class="tab-button text-lg font-semibold px-6 py-3 border-b-2 border-transparent text-stone-600 hover:text-stone-900 transition-all duration-300" data-tab="garis-kasar">Garis Kasar</button>
                </div>

                <div id="peta-minda-content" class="tab-content active px-4">
                    <h3 class="text-2xl font-semibold text-blue-700 mb-3">🗺️ Peta Minda Interaktif</h3>
                    <p class="text-stone-700 text-lg">
                        NotebookLM boleh menjana peta minda untuk memvisualisasikan perkaitan antara konsep dalam sumber anda.
                    </p>
                    <p class="text-stone-700 text-lg mt-2">
                        Ini bukan gambar statik; anda boleh <strong class="text-stone-900">mengklik pada mana-mana Node (topik kecil)</strong> untuk bertanya soalan fokus tentang topik itu sahaja, membolehkan anda menyelam lebih dalam ke dalam subjek tertentu.
                    </p>
                </div>
                <div id="garis-masa-content" class="tab-content px-4">
                    <h3 class="text-2xl font-semibold text-blue-700 mb-3">⏳ Garis Masa (Timeline)</h3>
                    <p class="text-stone-700 text-lg">
                        Jika sumber anda mengandungi peristiwa sejarah, langkah proses, atau data kronologi, NotebookLM boleh mengekstraknya dan menyusunnya ke dalam garis masa yang jelas. Ini membantu anda memahami urutan peristiwa dengan mudah.
                    </p>
                </div>
                <div id="faq-content" class="tab-content px-4">
                    <h3 class="text-2xl font-semibold text-blue-700 mb-3">❓ Soalan Lazim (FAQ)</h3>
                    <p class="text-stone-700 text-lg">
                        Tukar dokumen yang padat kepada format Soalan & Jawapan yang mudah dihadam. AI akan mengenal pasti soalan-soalan penting yang boleh dijawab oleh teks anda dan memberikan jawapan yang padat (dengan petikan) untuk setiap satu.
                    </p>
                </div>
                <div id="garis-kasar-content" class="tab-content px-4">
                    <h3 class="text-2xl font-semibold text-blue-700 mb-3">📋 Garis Kasar Pembentangan</h3>
                    <p class="text-stone-700 text-lg">
                        Perlu membuat pembentangan dengan cepat? NotebookLM boleh menjana garis kasar yang kemas dan tersusun, lengkap dengan <strong class="text-stone-900">isi perbincangan utama</strong> dan <strong class="text-stone-900">bukti sokongan</strong> yang diambil terus daripada sumber anda, semuanya dengan petikan yang betul.
                    </p>
                </div>
            </div>
        </section>

        <section id="interaksi" class="py-16 md:py-24">
            <h2 class="text-3xl md:text-4xl font-bold text-center text-stone-900 mb-4">Pembelajaran Aktif & Interaksi Audio</h2>
            <p class="text-lg text-center text-stone-700 max-w-3xl mx-auto mb-12">
                NotebookLM bukan sekadar alat rujukan pasif. Ia menyediakan ciri interaktif untuk mengesahkan fakta dan menguji pemahaman anda, serta keupayaan audio yang unik untuk pembelajaran semasa dalam perjalanan. Terokai ciri-ciri di bawah.
            </p>
            <div class="grid md:grid-cols-2 gap-8 max-w-6xl mx-auto">
                <div class="bg-white p-6 rounded-lg shadow-md border border-stone-200">
                    <h3 class="text-2xl font-semibold text-stone-900 mb-6">🔍 Integriti Fakta & Pembelajaran</h3>
                    <details class="mb-4 border-b border-stone-200 pb-4">
                        <summary class="text-xl font-semibold text-stone-800 cursor-pointer hover:text-blue-700 list-none">
                            <span class="mr-2">🔗</span> Pembuktian Rujukan (Citations)
                        </summary>
                        <p class="text-stone-700 mt-3 pl-6">
                            Setiap jawapan, ringkasan, atau cerapan yang dijana disertakan dengan petikan yang jelas. Mengklik petikan ini membawa anda terus ke bahagian yang tepat dalam dokumen sumber asal untuk verifikasi segera.
                        </p>
                    </details>
                    <details class="mb-4 border-b border-stone-200 pb-4">
                        <summary class="text-xl font-semibold text-stone-800 cursor-pointer hover:text-blue-700 list-none">
                            <span class="mr-2">🗂️</span> Flashcard
                        </summary>
                        <p class="text-stone-700 mt-3 pl-6">
                            Menghafal istilah dan konsep utama menjadi mudah. NotebookLM boleh menjana 'flashcard' secara automatik berdasarkan bahan sumber anda untuk membantu anda belajar dengan pantas.
                        </p>
                    </details>
                    <details>
                        <summary class="text-xl font-semibold text-stone-800 cursor-pointer hover:text-blue-700 list-none">
                            <span class="mr-2">📝</span> Kuiz Boleh Disesuaikan
                        </summary>
                        <p class="text-stone-700 mt-3 pl-6">
                            Uji pemahaman anda dengan kuiz yang dijana oleh AI. Jika jawapan anda salah, AI akan memberikan huraian terperinci mengapa ia salah, lengkap dengan petikan rujukan untuk anda kaji semula.
                        </p>
                    </details>
                </div>

                <div class="bg-white p-6 rounded-lg shadow-md border border-stone-200">
                    <h3 class="text-2xl font-semibold text-stone-900 mb-6">🎙️ Keupayaan Audio & Interaksi</h3>
                    <details class="mb-4 border-b border-stone-200 pb-4">
                        <summary class="text-xl font-semibold text-stone-800 cursor-pointer hover:text-blue-700 list-none">
                            <span class="mr-2">🎧</span> Ikhtisar Audio (Audio Overviews)
                        </summary>
                        <p class="text-stone-700 mt-3 pl-6">
                            Tukar sumber anda menjadi audio gaya podcast untuk pembelajaran *hands-free* dan *eyes-free*. Anda boleh memilih format yang berbeza:
                            <ul class="list-disc list-inside mt-2 pl-2">
                                <li><strong>Brief:</strong> Ringkasan pantas.</li>
                                <li><strong>Critique:</strong> Kritikan kelemahan dan kekuatan.</li>
                                <li><strong>Debate:</strong> Perbahasan sudut pandangan berbeza.</li>
                            </ul>
                        </p>
                    </details>
                    <details>
                        <summary class="text-xl font-semibold text-stone-800 cursor-pointer hover:text-blue-700 list-none">
                            <span class="mr-2">🗣️</span> Interaksi Hos AI
                        </summary>
                        <p class="text-stone-700 mt-3 pl-6">
                            Semasa audio dimainkan, anda tidak perlu berhenti untuk bertanya. Anda boleh mencelah untuk berinteraksi dengan Hos AI, bertanya soalan lanjut, atau meminta penjelasan tentang istilah yang baru disebut.
                        </p>
                    </details>
                </div>
            </div>
        </section>
        
        <section id="arahan" class="py-16 md:py-24">
            <h2 class="text-3xl md:text-4xl font-bold text-center text-stone-900 mb-4">Amalan Terbaik: Menguasai Arahan (Prompting)</h2>
            <p class="text-lg text-center text-stone-700 max-w-3xl mx-auto mb-12">
                Untuk mendapatkan hasil yang paling fokus dan berguna, kualiti arahan (prompt) anda adalah kunci. Ikuti tiga langkah utama ini untuk memaksimumkan kecekapan NotebookLM dan memastikan jawapan sentiasa relevan dengan sumber anda.
            </p>

            <div class="flex flex-col md:flex-row justify-between items-center md:items-start gap-6 md:gap-4 max-w-6xl mx-auto mb-12">
                
                <div class="flex flex-col items-center text-center w-full md:w-1/3 px-4">
                    <div class="flex items-center justify-center w-16 h-16 rounded-full bg-blue-600 text-white text-2xl font-bold mb-4 flex-shrink-0">1</div>
                    <h3 class="text-xl font-semibold text-stone-900 mb-2">Tentukan Peranan & Matlamat</h3>
                    <p class="text-stone-700">Beritahu AI apa yang anda mahu ia lakukan.<br><em>Cth: "Bertindak sebagai Tutor Sejarah" atau "Jana perbandingan dua sumber."</em></p>
                </div>

                <div class="text-stone-300 text-2xl hidden md:block mt-8">→</div>

                <div class="flex flex-col items-center text-center w-full md:w-1/3 px-4">
                    <div class="flex items-center justify-center w-16 h-16 rounded-full bg-blue-600 text-white text-2xl font-bold mb-4 flex-shrink-0">2</div>
                    <h3 class="text-xl font-semibold text-stone-900 mb-2">Berorientasikan Sumber (WAJIB)</h3>
                    <p class="text-stone-700">Wajibkan AI menggunakan sumber anda dan sertakan petikan.<br><em>Cih: "Berdasarkan semua sumber yang dimuat naik" & "Sediakan petikan."</em></p>
                </div>
                
                <div class="text-stone-300 text-2xl hidden md:block mt-8">→</div>

                <div class="flex flex-col items-center text-center w-full md:w-1/3 px-4">
                    <div class="flex items-center justify-center w-16 h-16 rounded-full bg-blue-600 text-white text-2xl font-bold mb-4 flex-shrink-0">3</div>
                    <h3 class="text-xl font-semibold text-stone-900 mb-2">Tetapkan Format & Had</h3>
                    <p class="text-stone-700">Beritahu AI bagaimana jawapan itu kelihatan dan panjangnya.<br><em>Cth: "Jana dalam bentuk jadual" atau "Hadkan jawapan kepada 300 perkataan."</em></p>
                </div>
            </div>

            <div class="max-w-3xl mx-auto mt-16 bg-red-50 border-l-4 border-red-500 text-red-800 p-6 rounded-lg shadow-md">
                <h4 class="text-xl font-bold mb-3">Peringatan Penting: Perkara yang Perlu Dielakkan</h4>
                <p class="text-lg">Untuk memastikan NotebookLM kekal "grounded", elakkan arahan yang menggalakkan spekulasi atau mencari maklumat di luar sumber anda.
                <ul class="list-disc list-inside mt-2 font-medium">
                    <li>Elakkan: "Apa pendapat anda tentang...?"</li>
                    <li>Elakkan: "Guna Google untuk mencari data terkini..."</li>
                </ul>
                </p>
            </div>
        </section>

    </main>

    <footer class="border-t border-stone-200 bg-stone-100">
        <div class="container mx-auto px-4 py-6 text-center text-stone-600">
            Panduan Interaktif NotebookLM | Dicipta sebagai Aplikasi Web Satu Halaman.
        </div>
    </footer>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            
            const navLinks = document.querySelectorAll('.nav-link');
            const sections = document.querySelectorAll('main section');
            const mobileMenuBtn = document.getElementById('mobile-menu-btn');
            const mobileMenu = document.getElementById('mobile-menu');

            mobileMenuBtn.addEventListener('click', () => {
                mobileMenu.classList.toggle('hidden');
            });

            navLinks.forEach(link => {
                link.addEventListener('click', (e) => {
                    e.preventDefault();
                    const targetId = link.getAttribute('href');
                    const targetElement = document.querySelector(targetId);
                    if (targetElement) {
                        targetElement.scrollIntoView({ behavior: 'smooth', block: 'start' });
                    }
                    if (mobileMenu.classList.contains('hidden') === false) {
                        mobileMenu.classList.add('hidden');
                    }
                });
            });

            const observerOptions = {
                root: null,
                rootMargin: '0px',
                threshold: 0.4
            };

            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    const id = entry.target.getAttribute('id');
                    const navLink = document.querySelector(`.nav-link[href="#${id}"]`);
                    
                    if (entry.isIntersecting) {
                        document.querySelectorAll('.nav-link.active').forEach(link => link.classList.remove('active'));
                        if (navLink) {
                            navLink.classList.add('active');
                            const mobileNavLink = document.querySelector(`#mobile-menu .nav-link[href="#${id}"]`);
                            if(mobileNavLink) mobileNavLink.classList.add('active');
                        }
                    }
                });
            }, observerOptions);

            sections.forEach(section => {
                observer.observe(section);
            });

            const tabButtons = document.querySelectorAll('.tab-button');
            const tabContents = document.querySelectorAll('.tab-content');

            tabButtons.forEach(button => {
                button.addEventListener('click', () => {
                    
                    tabButtons.forEach(btn => btn.classList.remove('active'));
                    button.classList.add('active');

                    const tabId = button.getAttribute('data-tab');
                    
                    tabContents.forEach(content => {
                        if (content.id === `${tabId}-content`) {
                            content.classList.add('active');
                        } else {
                            content.classList.remove('active');
                        }
                    });
                });
            });
        });
    </script>
</body>
</html>
