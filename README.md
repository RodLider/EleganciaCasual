
<html lang="pt-PT">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Estúdio de Estilo Masculino com IA</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Lucide Icons -->
    <script src="https://unpkg.com/lucide@latest"></script>
    
    <style>
        /* Estilos personalizados para a barra de rolagem */
        .scrollbar-thin::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        .scrollbar-thin::-webkit-scrollbar-track {
            background: transparent;
        }
        .scrollbar-thin::-webkit-scrollbar-thumb {
            background-color: #e2e8f0;
            border-radius: 20px;
        }
        .scrollbar-thin {
            scrollbar-width: thin;
            scrollbar-color: #e2e8f0 transparent;
        }
    </style>
</head>
<body class="min-h-screen bg-[#f4f2ef] flex items-center justify-center p-4 md:p-8 font-sans text-slate-800">

    <!-- Container Principal -->
    <div class="max-w-6xl w-full bg-white rounded-[2rem] shadow-2xl overflow-hidden flex flex-col lg:flex-row border border-stone-200">
        
        <!-- Lado Esquerdo: Imagem de Inspiração Original -->
        <div class="lg:w-5/12 relative h-[250px] lg:h-auto bg-slate-200">
            <img 
                src="image.png" 
                alt="Inspiração de moda masculina" 
                class="absolute inset-0 w-full h-full object-cover"
                onerror="this.src='https://images.unsplash.com/photo-1617137984095-74e4e5e3613f?q=80&w=800&auto=format&fit=crop';"
            />
            <div class="absolute inset-0 bg-gradient-to-t from-black/70 via-black/20 to-transparent"></div>
            
            <div class="absolute bottom-6 left-6 text-white">
                <div class="flex items-center gap-2 mb-1">
                    <i data-lucide="sparkles" class="w-5 h-5 text-amber-300"></i>
                    <p class="text-xs font-bold tracking-widest uppercase text-amber-300">A Sua Referência</p>
                </div>
                <h2 class="text-2xl font-light">Elegância Casual</h2>
                <p class="text-sm opacity-80 mt-1 max-w-[250px]">Utilize esta silhueta como inspiração para as combinações ao lado.</p>
            </div>
        </div>

        <!-- Lado Direito: Estúdio de Cores Interativo -->
        <div class="lg:w-7/12 p-6 md:p-8 flex flex-col bg-[#faf9f8]">
            
            <div class="mb-4 flex flex-col sm:flex-row sm:items-center justify-between gap-4">
                <div>
                    <h1 class="text-2xl font-bold text-slate-800 flex items-center gap-2">
                        <i data-lucide="palette" class="w-7 h-7 text-indigo-600"></i>
                        Estúdio de Estilo
                    </h1>
                    <p class="text-sm text-slate-500 mt-1">Personalize e visualize a sua combinação.</p>
                </div>

                <!-- Abas de Visualização -->
                <div class="flex bg-slate-200 p-1 rounded-xl self-start shrink-0">
                    <button id="btn-view-2d" class="flex items-center gap-2 px-4 py-2 text-sm font-medium rounded-lg transition-all bg-white text-slate-800 shadow-sm" onclick="setViewMode('2d')">
                        <i data-lucide="image" class="w-4 h-4"></i> 2D
                    </button>
                    <button id="btn-view-ai" class="flex items-center gap-2 px-4 py-2 text-sm font-medium rounded-lg transition-all text-slate-500 hover:text-slate-700" onclick="setViewMode('ai')">
                        <i data-lucide="camera" class="w-4 h-4"></i> Realista (IA)
                    </button>
                </div>
            </div>

            <!-- Área do Visor (Manequim 2D ou Foto IA) -->
            <div class="bg-white rounded-3xl p-4 shadow-sm border border-slate-200 flex flex-col items-center justify-center min-h-[360px] mb-6 relative overflow-hidden">
                
                <!-- VISUALIZAÇÃO 2D -->
                <div id="view-2d-container" class="w-full h-full flex flex-col items-center justify-center">
                    <div class="absolute inset-0 opacity-[0.03]" style="background-image: radial-gradient(circle at 2px 2px, #000 1px, transparent 0); background-size: 20px 20px;"></div>
                    <div class="flex flex-col items-center relative z-10 scale-110 mt-4">
                        
                        <!-- SVG Camisa -->
                        <svg width="120" height="120" viewBox="0 0 100 100" class="transition-all duration-300 drop-shadow-md">
                            <path class="svg-shirt-color" d="M25 25 L40 15 L50 20 L60 15 L75 25 L85 50 L75 55 L75 90 L25 90 L25 55 L15 50 Z" fill="#1e3a5f" />
                            <path d="M40 15 L50 28 L60 15 L50 20 Z" fill="rgba(0,0,0,0.2)" />
                            <path d="M25 25 L40 15 L50 20 L25 35 Z" fill="rgba(255,255,255,0.05)" />
                            <line x1="50" y1="28" x2="50" y2="90" stroke="rgba(0,0,0,0.15)" stroke-width="2" />
                            <circle cx="50" cy="45" r="1.5" fill="rgba(0,0,0,0.3)" />
                            <circle cx="50" cy="60" r="1.5" fill="rgba(0,0,0,0.3)" />
                            <circle cx="50" cy="75" r="1.5" fill="rgba(0,0,0,0.3)" />
                        </svg>

                        <!-- SVG Calça -->
                        <svg width="96" height="132" viewBox="0 0 80 110" class="transition-all duration-300 drop-shadow-md z-10 -mt-2">
                            <path class="svg-pants-color" d="M15 5 L65 5 L70 15 L10 15 Z" fill="#ece6da" />
                            <path d="M15 5 L65 5 L70 15 L10 15 Z" fill="rgba(0,0,0,0.08)" />
                            <path class="svg-pants-color" d="M10 15 L70 15 L75 105 L45 105 L40 40 L35 105 L5 105 Z" fill="#ece6da" />
                            <line x1="40" y1="15" x2="40" y2="40" stroke="rgba(0,0,0,0.15)" stroke-width="2" />
                            <line x1="25" y1="20" x2="25" y2="100" stroke="rgba(0,0,0,0.1)" stroke-width="1" />
                            <line x1="55" y1="20" x2="55" y2="100" stroke="rgba(0,0,0,0.1)" stroke-width="1" />
                        </svg>

                        <!-- SVG Sapatos -->
                        <div class="flex gap-5 pt-2">
                            <svg width="42" height="54" viewBox="0 0 40 50" style="transform: rotate(-5deg)" class="transition-all duration-300 drop-shadow-md">
                                <path class="svg-shoes-color" d="M12 5 C 12 5, 28 5, 28 12 L 32 38 C 32 46, 24 46, 20 46 C 16 46, 8 46, 8 38 L 12 12 Z" fill="#4a3020" />
                                <path d="M12 12 C 16 20, 24 20, 28 12" fill="none" stroke="rgba(0,0,0,0.3)" stroke-width="1.5"/>
                                <path d="M16 20 L 24 20 L 22 26 L 18 26 Z" fill="rgba(0,0,0,0.15)"/>
                                <path d="M8 38 C 8 46, 16 46, 20 46 C 24 46, 32 46, 32 38 L 33 38 C 33 48, 24 48, 20 48 C 16 48, 7 48, 7 38 Z" fill="#222" />
                            </svg>
                            <svg width="42" height="54" viewBox="0 0 40 50" style="transform: scaleX(-1) rotate(-5deg)" class="transition-all duration-300 drop-shadow-md">
                                <path class="svg-shoes-color" d="M12 5 C 12 5, 28 5, 28 12 L 32 38 C 32 46, 24 46, 20 46 C 16 46, 8 46, 8 38 L 12 12 Z" fill="#4a3020" />
                                <path d="M12 12 C 16 20, 24 20, 28 12" fill="none" stroke="rgba(0,0,0,0.3)" stroke-width="1.5"/>
                                <path d="M16 20 L 24 20 L 22 26 L 18 26 Z" fill="rgba(0,0,0,0.15)"/>
                                <path d="M8 38 C 8 46, 16 46, 20 46 C 24 46, 32 46, 32 38 L 33 38 C 33 48, 24 48, 20 48 C 16 48, 7 48, 7 38 Z" fill="#222" />
                            </svg>
                        </div>
                    </div>
                </div>

                <!-- VISUALIZAÇÃO IA -->
                <div id="view-ai-container" class="hidden w-full h-full flex flex-col items-center justify-center relative min-h-[320px]">
                    
                    <!-- Estado Inicial (Sem imagem) -->
                    <div id="ai-prompt-state" class="text-center p-6">
                        <i data-lucide="camera" class="w-12 h-12 text-slate-300 mx-auto mb-3"></i>
                        <h3 class="text-lg font-semibold text-slate-700">Gerar Fotografia</h3>
                        <p class="text-sm text-slate-500 mt-2 mb-6 max-w-[280px]">
                            A nossa IA irá criar uma fotografia realista de um modelo a vestir as cores que selecionou em baixo.
                        </p>
                        <button onclick="generateRealisticPhoto()" class="bg-indigo-600 hover:bg-indigo-700 text-white px-6 py-3 rounded-xl font-medium transition-colors shadow-md flex items-center gap-2 mx-auto">
                            <i data-lucide="sparkles" class="w-4 h-4"></i> Gerar Foto Agora
                        </button>
                    </div>

                    <!-- Estado A Gerar & Imagem Pronta -->
                    <div id="ai-image-state" class="hidden relative w-full h-full flex items-center justify-center">
                        
                        <div id="ai-loader" class="absolute inset-0 z-20 bg-white/80 backdrop-blur-sm flex flex-col items-center justify-center rounded-2xl">
                            <i data-lucide="loader-2" class="w-10 h-10 text-indigo-600 animate-spin mb-3"></i>
                            <span class="text-sm font-medium text-slate-700 animate-pulse">A gerar fotografia realista...</span>
                        </div>

                        <img id="ai-result-img" src="" alt="Look gerado por IA" class="max-h-[340px] rounded-2xl object-cover shadow-sm transition-opacity duration-500 opacity-0" />
                        
                        <div id="ai-actions" class="hidden absolute bottom-3 right-3 flex gap-2">
                            <button onclick="handleDownloadImage()" class="bg-white/90 backdrop-blur text-slate-800 p-2.5 rounded-lg shadow-md hover:bg-indigo-50 hover:text-indigo-600 transition-colors" title="Guardar fotografia">
                                <i data-lucide="download" class="w-4 h-4"></i>
                            </button>
                            <button onclick="generateRealisticPhoto()" class="bg-white/90 backdrop-blur text-slate-800 p-2.5 rounded-lg shadow-md hover:bg-white transition-colors" title="Gerar nova variação">
                                <i data-lucide="refresh-cw" class="w-4 h-4"></i>
                            </button>
                        </div>
                    </div>
                </div>

            </div>

            <!-- Controles de Cores (Gerados dinamicamente via JS) -->
            <div class="flex-1 grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-1 xl:grid-cols-3 gap-x-6 gap-y-2">
                
                <div class="mb-5 w-full">
                    <div class="flex justify-between items-end mb-2">
                        <span class="text-sm font-semibold text-slate-700 uppercase tracking-wide">1. Camisa</span>
                        <span id="label-shirt" class="text-xs text-slate-500 bg-white border border-slate-200 px-2 py-1 rounded-md shadow-sm">Azul Marinho</span>
                    </div>
                    <div id="container-shirt" class="flex gap-2 sm:gap-3 flex-wrap max-h-32 overflow-y-auto p-1 scrollbar-thin"></div>
                </div>

                <div class="mb-5 w-full">
                    <div class="flex justify-between items-end mb-2">
                        <span class="text-sm font-semibold text-slate-700 uppercase tracking-wide">2. Calça</span>
                        <span id="label-pants" class="text-xs text-slate-500 bg-white border border-slate-200 px-2 py-1 rounded-md shadow-sm">Creme/Areia</span>
                    </div>
                    <div id="container-pants" class="flex gap-2 sm:gap-3 flex-wrap max-h-32 overflow-y-auto p-1 scrollbar-thin"></div>
                </div>

                <div class="mb-5 w-full">
                    <div class="flex justify-between items-end mb-2">
                        <span class="text-sm font-semibold text-slate-700 uppercase tracking-wide">3. Sapatos</span>
                        <span id="label-shoes" class="text-xs text-slate-500 bg-white border border-slate-200 px-2 py-1 rounded-md shadow-sm">Marrom Escuro</span>
                    </div>
                    <div id="container-shoes" class="flex gap-2 sm:gap-3 flex-wrap max-h-32 overflow-y-auto p-1 scrollbar-thin"></div>
                </div>

            </div>

            <!-- Botões de Ação -->
            <div class="flex gap-3 mt-2 pt-5 border-t border-slate-200">
                <button onclick="handleRandomize()" class="flex-1 flex items-center justify-center gap-2 bg-white border border-slate-300 hover:bg-slate-50 text-slate-700 py-3 rounded-xl font-medium transition-colors shadow-sm">
                    <i data-lucide="shuffle" class="w-4 h-4"></i> Sortear Cores
                </button>
                <button onclick="handleCopyPalette()" class="flex-1 flex items-center justify-center gap-2 bg-slate-900 hover:bg-slate-800 text-white py-3 rounded-xl font-medium transition-colors shadow-md">
                    <i data-lucide="copy" class="w-4 h-4"></i> Copiar Look
                </button>
            </div>

        </div>
    </div>

    <!-- Notificação Toast -->
    <div id="toast" class="hidden fixed bottom-6 right-6 z-50 bg-slate-800 text-white px-6 py-3 rounded-xl shadow-2xl flex items-center gap-3 transition-opacity duration-300 opacity-0">
        <i data-lucide="check" class="w-5 h-5 text-emerald-400"></i>
        <span id="toast-message" class="font-medium">Mensagem</span>
    </div>

    <script>
        // --- DADOS DAS CORES ---
        const tonsDePretoAzulCinza = [
            { id: 'black', name: 'Preto', en: 'black', hex: '#111111' },
            { id: 'absoluteblack', name: 'Preto Absoluto', en: 'pitch black', hex: '#000000' },
            { id: 'deepblack', name: 'Preto Profundo', en: 'deep black', hex: '#0a0a0a' },
            { id: 'onyx', name: 'Preto Ônix', en: 'onyx black', hex: '#353839' },
            { id: 'matteblack', name: 'Preto Fosco', en: 'matte black', hex: '#28282b' },
            { id: 'glossyblack', name: 'Preto Brilhante', en: 'glossy black', hex: '#1a1a1a' },
            { id: 'blue', name: 'Azul', en: 'blue', hex: '#2563eb' },
            { id: 'royalblue', name: 'Azul Royal', en: 'royal blue', hex: '#4169e1' },
            { id: 'navy', name: 'Azul Marinho', en: 'navy blue', hex: '#1e3a5f' },
            { id: 'skyblue', name: 'Azul Céu', en: 'sky blue', hex: '#87ceeb' },
            { id: 'turquoise', name: 'Azul Turquesa', en: 'turquoise blue', hex: '#40e0d0' },
            { id: 'petrol', name: 'Azul Petróleo', en: 'petrol blue', hex: '#005f69' },
            { id: 'bic', name: 'Azul Bic', en: 'cobalt blue', hex: '#0047ab' },
            { id: 'sapphire', name: 'Azul Safira', en: 'sapphire blue', hex: '#0f52ba' },
            { id: 'grey', name: 'Cinza', en: 'grey', hex: '#888f98' },
            { id: 'lightgrey', name: 'Cinza Claro', en: 'light grey', hex: '#d3d3d3' },
            { id: 'darkgrey', name: 'Cinza Escuro', en: 'dark grey', hex: '#4b5563' },
            { id: 'mediumgrey', name: 'Cinza Médio', en: 'medium grey', hex: '#9ca3af' },
            { id: 'graphite', name: 'Cinza Grafite', en: 'graphite grey', hex: '#4b4b4b' },
            { id: 'charcoal', name: 'Cinza Chumbo', en: 'charcoal grey', hex: '#36454f' },
            { id: 'silver', name: 'Cinza Prata', en: 'silver grey', hex: '#c0c0c0' },
            { id: 'smoke', name: 'Cinza Fumaça', en: 'smoke grey', hex: '#708090' },
        ];

        const shirtColors = [
            { id: 'white', name: 'Branco', en: 'white', hex: '#f8fafc' },
            { id: 'burgundy', name: 'Vinho', en: 'burgundy', hex: '#631c26' },
            { id: 'olive', name: 'Verde Oliva', en: 'olive green', hex: '#44533c' },
            { id: 'pink', name: 'Rosa Claro', en: 'light pink', hex: '#fbcfe8' },
            { id: 'mustard', name: 'Mostarda', en: 'mustard yellow', hex: '#d97706' },
            { id: 'mint', name: 'Verde Menta', en: 'mint green', hex: '#a7f3d0' },
            ...tonsDePretoAzulCinza
        ];

        const pantsColors = [
            { id: 'cream', name: 'Creme/Areia', en: 'cream', hex: '#ece6da' },
            { id: 'khaki', name: 'Caqui', en: 'khaki', hex: '#cbb89b' },
            { id: 'olive', name: 'Verde Oliva', en: 'olive green', hex: '#4d533c' },
            { id: 'brown', name: 'Marrom', en: 'brown', hex: '#5c4033' },
            ...tonsDePretoAzulCinza
        ];

        const shoesColors = [
            { id: 'brown', name: 'Marrom Escuro', en: 'dark brown', hex: '#4a3020' },
            { id: 'tan', name: 'Caramelo', en: 'tan', hex: '#a67b5b' },
            { id: 'oxblood', name: 'Bordô', en: 'oxblood', hex: '#4a1c1c' },
            { id: 'white', name: 'Branco', en: 'white sneakers', hex: '#f8fafc' },
            ...tonsDePretoAzulCinza
        ];

        // --- ESTADO DA APLICAÇÃO ---
        let currentShirt = shirtColors.find(c => c.id === 'navy') || shirtColors[0];
        let currentPants = pantsColors.find(c => c.id === 'cream') || pantsColors[0];
        let currentShoes = shoesColors.find(c => c.id === 'brown') || shoesColors[0];
        let currentAiImageUrl = null;
        const apiKey = ""; // A chave é injetada automaticamente pelo ambiente

        // --- FUNÇÕES UTILITÁRIAS ---
        function isLight(hex) {
            const c = hex.substring(1);
            const rgb = parseInt(c, 16);
            const r = (rgb >> 16) & 0xff;
            const g = (rgb >> 8) & 0xff;
            const b = (rgb >> 0) & 0xff;
            const luma = 0.2126 * r + 0.7152 * g + 0.0722 * b;
            return luma > 150;
        }

        function showToast(message) {
            const toast = document.getElementById('toast');
            document.getElementById('toast-message').textContent = message;
            
            toast.classList.remove('hidden');
            setTimeout(() => toast.classList.remove('opacity-0'), 10);

            setTimeout(() => {
                toast.classList.add('opacity-0');
                setTimeout(() => toast.classList.add('hidden'), 300);
            }, 3000);
        }

        // --- ATUALIZAÇÃO DA INTERFACE ---
        function updateSVGColors() {
            document.querySelectorAll('.svg-shirt-color').forEach(el => el.setAttribute('fill', currentShirt.hex));
            document.querySelectorAll('.svg-pants-color').forEach(el => el.setAttribute('fill', currentPants.hex));
            document.querySelectorAll('.svg-shoes-color').forEach(el => el.setAttribute('fill', currentShoes.hex));
            
            document.getElementById('label-shirt').textContent = currentShirt.name;
            document.getElementById('label-pants').textContent = currentPants.name;
            document.getElementById('label-shoes').textContent = currentShoes.name;
        }

        function renderSelectors() {
            const createSelector = (containerId, options, selectedColor, type) => {
                const container = document.getElementById(containerId);
                container.innerHTML = '';
                
                options.forEach(opt => {
                    const isSelected = selectedColor.id === opt.id;
                    const light = isLight(opt.hex);
                    const btn = document.createElement('button');
                    
                    // Base classes
                    let classes = 'w-9 h-9 sm:w-10 sm:h-10 shrink-0 rounded-full flex items-center justify-center transition-all duration-300 focus:outline-none ';
                    
                    if (isSelected) {
                        classes += 'ring-2 ring-offset-2 ring-slate-800 scale-110 shadow-md';
                        const checkColor = light ? 'text-slate-800' : 'text-white';
                        btn.innerHTML = `<i data-lucide="check" class="w-4 h-4 sm:w-5 sm:h-5 ${checkColor}"></i>`;
                    } else {
                        classes += 'hover:scale-105 hover:shadow-sm border border-slate-300';
                    }
                    
                    btn.className = classes;
                    btn.style.backgroundColor = opt.hex;
                    btn.title = opt.name;
                    
                    btn.onclick = () => {
                        if (type === 'shirt') currentShirt = opt;
                        if (type === 'pants') currentPants = opt;
                        if (type === 'shoes') currentShoes = opt;
                        
                        resetAiImageState();
                        updateSVGColors();
                        renderSelectors();
                    };
                    
                    container.appendChild(btn);
                });
            };

            createSelector('container-shirt', shirtColors, currentShirt, 'shirt');
            createSelector('container-pants', pantsColors, currentPants, 'pants');
            createSelector('container-shoes', shoesColors, currentShoes, 'shoes');
            
            // Re-inicializa os ícones após alterar o DOM
            lucide.createIcons();
        }

        function setViewMode(mode) {
            const btn2d = document.getElementById('btn-view-2d');
            const btnAi = document.getElementById('btn-view-ai');
            const view2d = document.getElementById('view-2d-container');
            const viewAi = document.getElementById('view-ai-container');

            if (mode === '2d') {
                btn2d.className = 'flex items-center gap-2 px-4 py-2 text-sm font-medium rounded-lg transition-all bg-white text-slate-800 shadow-sm';
                btnAi.className = 'flex items-center gap-2 px-4 py-2 text-sm font-medium rounded-lg transition-all text-slate-500 hover:text-slate-700';
                view2d.classList.remove('hidden');
                viewAi.classList.add('hidden');
            } else {
                btnAi.className = 'flex items-center gap-2 px-4 py-2 text-sm font-medium rounded-lg transition-all bg-indigo-600 text-white shadow-sm';
                btn2d.className = 'flex items-center gap-2 px-4 py-2 text-sm font-medium rounded-lg transition-all text-slate-500 hover:text-slate-700';
                viewAi.classList.remove('hidden');
                view2d.classList.add('hidden');
            }
        }

        function resetAiImageState() {
            currentAiImageUrl = null;
            document.getElementById('ai-prompt-state').classList.remove('hidden');
            document.getElementById('ai-image-state').classList.add('hidden');
            const imgEl = document.getElementById('ai-result-img');
            imgEl.src = '';
            imgEl.classList.remove('opacity-100');
            imgEl.classList.add('opacity-0');
        }

        // --- AÇÕES PRINCIPAIS ---
        function handleRandomize() {
            currentShirt = shirtColors[Math.floor(Math.random() * shirtColors.length)];
            currentPants = pantsColors[Math.floor(Math.random() * pantsColors.length)];
            currentShoes = shoesColors[Math.floor(Math.random() * shoesColors.length)];
            
            resetAiImageState();
            updateSVGColors();
            renderSelectors();
        }

        function handleCopyPalette() {
            const text = `O Meu Look: Camisa ${currentShirt.name}, Calça ${currentPants.name}, Sapatos ${currentShoes.name}.`;
            
            const textArea = document.createElement("textarea");
            textArea.value = text;
            document.body.appendChild(textArea);
            textArea.select();
            document.execCommand("copy");
            document.body.removeChild(textArea);

            showToast('Combinação copiada com sucesso!');
        }

        async function generateRealisticPhoto() {
            document.getElementById('ai-prompt-state').classList.add('hidden');
            document.getElementById('ai-image-state').classList.remove('hidden');
            document.getElementById('ai-loader').classList.remove('hidden');
            document.getElementById('ai-actions').classList.add('hidden');
            
            const imgEl = document.getElementById('ai-result-img');
            imgEl.classList.remove('opacity-100');
            imgEl.classList.add('opacity-0');

            const promptText = `handsome man male model wearing ${currentShirt.en} button-down shirt and ${currentPants.en} tailored trousers and ${currentShoes.en} leather shoes, full body, plain studio background, fashion photography, photorealistic, 8k, elegant styling`;

            const fetchImage = async (retries = 5, delay = 1000) => {
                try {
                    const response = await fetch(`https://generativelanguage.googleapis.com/v1beta/models/imagen-4.0-generate-001:predict?key=${apiKey}`, {
                        method: 'POST',
                        headers: { 'Content-Type': 'application/json' },
                        body: JSON.stringify({
                            instances: { prompt: promptText },
                            parameters: { sampleCount: 1 }
                        })
                    });

                    if (!response.ok) throw new Error('Falha na resposta da API');
                    
                    const result = await response.json();
                    const base64Image = result.predictions?.[0]?.bytesBase64Encoded;
                    
                    if (!base64Image) throw new Error('Sem dados de imagem');
                    
                    return `data:image/png;base64,${base64Image}`;
                } catch (error) {
                    if (retries > 0) {
                        await new Promise(resolve => setTimeout(resolve, delay));
                        return fetchImage(retries - 1, delay * 2);
                    }
                    throw error;
                }
            };

            try {
                const url = await fetchImage();
                currentAiImageUrl = url;
                
                imgEl.src = url;
                imgEl.onload = () => {
                    document.getElementById('ai-loader').classList.add('hidden');
                    imgEl.classList.remove('opacity-0');
                    imgEl.classList.add('opacity-100');
                    document.getElementById('ai-actions').classList.remove('hidden');
                };
            } catch (error) {
                resetAiImageState();
                showToast("Erro ao gerar imagem. Tente novamente.");
            }
        }

        function handleDownloadImage() {
            if (!currentAiImageUrl) return;
            
            const link = document.createElement('a');
            link.href = currentAiImageUrl;
            link.download = `meu-look-${currentShirt.id}-${currentPants.id}-${currentShoes.id}.png`;
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
            
            showToast('Fotografia guardada com sucesso!');
        }

        // Inicialização
        document.addEventListener('DOMContentLoaded', () => {
            lucide.createIcons();
            updateSVGColors();
            renderSelectors();
        });

    </script>
</body>
</html>

