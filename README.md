<!DOCTYPE html>
<html lang="pt-PT">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Estúdio de Estilo Masculino IA</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://unpkg.com/lucide@latest"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;600;700;800&display=swap');
        
        :root { font-family: 'Plus Jakarta Sans', sans-serif; }
        
        .scrollbar-hide::-webkit-scrollbar { display: none; }
        .scrollbar-hide { -ms-overflow-style: none; scrollbar-width: none; }

        .preview-glass {
            background: rgba(255, 255, 255, 0.7);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.3);
        }

        @keyframes pulse-ring {
            0% { transform: scale(0.8); opacity: 0.5; }
            50% { transform: scale(1.1); opacity: 0.3; }
            100% { transform: scale(0.8); opacity: 0.5; }
        }
        .active-ring { animation: pulse-ring 2s cubic-bezier(0.4, 0, 0.6, 1) infinite; }
    </style>
</head>
<body class="bg-[#f3f4f6] min-h-screen flex items-center justify-center p-4 md:p-6 lg:p-10">

    <div class="max-w-6xl w-full bg-white rounded-[2.5rem] shadow-2xl overflow-hidden flex flex-col lg:flex-row border border-gray-200">
        
        <!-- Lado Esquerdo: Visualização -->
        <div class="lg:w-1/2 relative min-h-[450px] bg-slate-100 flex flex-col">
            
            <!-- Tabs Superior -->
            <div class="absolute top-6 left-1/2 -translate-x-1/2 z-20 flex bg-white/50 backdrop-blur-md p-1.5 rounded-2xl shadow-lg border border-white/40">
                <button onclick="setView('2d')" id="tab-2d" class="flex items-center gap-2 px-6 py-2.5 text-sm font-bold rounded-xl transition-all duration-300 bg-white text-indigo-600 shadow-sm">
                    <i data-lucide="layout" class="w-4 h-4"></i> Draft
                </button>
                <button onclick="setView('ai')" id="tab-ai" class="flex items-center gap-2 px-6 py-2.5 text-sm font-bold rounded-xl transition-all duration-300 text-slate-500 hover:text-slate-800">
                    <i data-lucide="sparkles" class="w-4 h-4"></i> Realista
                </button>
            </div>

            <!-- Área de Preview 2D -->
            <div id="preview-2d" class="flex-1 flex flex-col items-center justify-center relative transition-all duration-500 opacity-100">
                <div class="absolute inset-0 opacity-[0.05]" style="background-image: radial-gradient(#4f46e5 1px, transparent 1px); background-size: 24px 24px;"></div>
                
                <div class="relative z-10 flex flex-col items-center scale-125 md:scale-[1.4] transition-transform duration-700">
                    <!-- Shirt -->
                    <svg width="100" height="100" viewBox="0 0 100 100" class="drop-shadow-2xl">
                        <path id="svg-shirt" d="M25 25 L40 15 L50 20 L60 15 L75 25 L85 50 L75 55 L75 90 L25 90 L25 55 L15 50 Z" fill="#1e3a8a" class="transition-colors duration-500"/>
                        <path d="M40 15 L50 26 L60 15 L50 20 Z" fill="rgba(0,0,0,0.1)"/>
                        <line x1="50" y1="26" x2="50" y2="90" stroke="rgba(0,0,0,0.1)" stroke-width="1.5"/>
                    </svg>
                    <!-- Pants -->
                    <svg width="80" height="110" viewBox="0 0 80 110" class="drop-shadow-xl -mt-1 relative z-[5]">
                        <path id="svg-pants" d="M10 5 L70 5 L75 105 L45 105 L40 40 L35 105 L5 105 Z" fill="#d1d5db" class="transition-colors duration-500"/>
                        <path d="M10 5 L70 5 L68 15 L12 15 Z" fill="rgba(0,0,0,0.05)"/>
                    </svg>
                    <!-- Shoes -->
                    <div class="flex gap-4 -mt-2">
                        <svg width="35" height="25" viewBox="0 0 40 30">
                            <path id="svg-shoes-l" d="M5 25 C 5 15, 10 10, 35 10 C 38 10, 38 25, 38 25 Z" fill="#451a03" class="transition-colors duration-500" />
                            <rect x="5" y="24" width="33" height="2.5" fill="rgba(0,0,0,0.3)" rx="1" />
                        </svg>
                        <svg width="35" height="25" viewBox="0 0 40 30" style="transform: scaleX(-1)">
                            <path id="svg-shoes-r" d="M5 25 C 5 15, 10 10, 35 10 C 38 10, 38 25, 38 25 Z" fill="#451a03" class="transition-colors duration-500" />
                            <rect x="5" y="24" width="33" height="2.5" fill="rgba(0,0,0,0.3)" rx="1" />
                        </svg>
                    </div>
                </div>
            </div>

            <!-- Área de Preview AI (Hidden) -->
            <div id="preview-ai" class="hidden flex-1 relative bg-slate-900 overflow-hidden">
                <div id="ai-placeholder" class="absolute inset-0 flex flex-col items-center justify-center p-12 text-center text-white">
                    <div class="w-20 h-20 bg-indigo-600/20 rounded-full flex items-center justify-center mb-6">
                        <i data-lucide="wand-2" class="w-10 h-10 text-indigo-400"></i>
                    </div>
                    <h3 class="text-xl font-bold mb-2">Motor de Renderização IA</h3>
                    <p class="text-slate-400 text-sm max-w-xs">Clique no botão abaixo para gerar uma fotografia realista baseada na sua configuração.</p>
                </div>

                <div id="ai-loading" class="hidden absolute inset-0 z-10 bg-slate-950/80 backdrop-blur-md flex flex-col items-center justify-center text-white">
                    <div class="w-16 h-16 border-4 border-white/10 border-t-indigo-500 rounded-full animate-spin"></div>
                    <p class="mt-6 font-bold tracking-widest uppercase animate-pulse">A gerar fotografia...</p>
                </div>

                <img id="ai-img" src="" class="hidden w-full h-full object-cover" alt="Resultado IA">
                
                <div id="ai-actions" class="hidden absolute bottom-6 right-6 flex gap-3">
                    <button onclick="downloadImage()" class="p-4 bg-white/10 hover:bg-white/20 backdrop-blur-md rounded-2xl text-white transition-all">
                        <i data-lucide="download" class="w-5 h-5"></i>
                    </button>
                    <button onclick="generateImage()" class="p-4 bg-indigo-600 hover:bg-indigo-500 rounded-2xl text-white shadow-xl transition-all">
                        <i data-lucide="refresh-cw" class="w-5 h-5"></i>
                    </button>
                </div>
            </div>

            <!-- Info Bar Inferior -->
            <div class="p-6 bg-white/50 backdrop-blur-md border-t border-gray-200 mt-auto flex justify-between items-center">
                <div>
                    <p class="text-[10px] font-extrabold uppercase tracking-widest text-indigo-600 mb-1">Look Selecionado</p>
                    <h4 id="summary-text" class="text-sm font-semibold text-slate-800">Casual Urbano</h4>
                </div>
                <button id="main-action-btn" onclick="generateImage()" class="hidden bg-indigo-600 hover:bg-indigo-700 text-white px-6 py-3 rounded-2xl font-bold text-sm shadow-lg shadow-indigo-200 transition-all flex items-center gap-2">
                    <i data-lucide="wand-2" class="w-4 h-4"></i> Gerar Agora
                </button>
            </div>
        </div>

        <!-- Lado Direito: Controlos -->
        <div class="lg:w-1/2 p-6 md:p-10 lg:p-12 overflow-y-auto max-h-screen scrollbar-hide">
            
            <header class="mb-10">
                <h1 class="text-3xl font-extrabold tracking-tight text-slate-900 uppercase">Estúdio de Estilo</h1>
                <p class="text-slate-500 mt-2 font-medium">Personalize cada detalhe da sua indumentária.</p>
            </header>

            <div class="space-y-10">
                <!-- Shirt Section -->
                <section>
                    <div class="flex justify-between items-center mb-4">
                        <label class="text-[11px] font-bold uppercase tracking-widest text-slate-400">01. Parte Superior</label>
                        <span id="label-shirt" class="text-xs font-bold text-indigo-600 bg-indigo-50 px-3 py-1 rounded-lg">Branco Oxford</span>
                    </div>
                    <div id="grid-shirt" class="flex gap-4 overflow-x-auto pb-4 scrollbar-hide"></div>
                </section>

                <!-- Pants Section -->
                <section>
                    <div class="flex justify-between items-center mb-4">
                        <label class="text-[11px] font-bold uppercase tracking-widest text-slate-400">02. Parte Inferior</label>
                        <span id="label-pants" class="text-xs font-bold text-indigo-600 bg-indigo-50 px-3 py-1 rounded-lg">Cáqui Areia</span>
                    </div>
                    <div id="grid-pants" class="flex gap-4 overflow-x-auto pb-4 scrollbar-hide"></div>
                </section>

                <!-- Shoes Section -->
                <section>
                    <div class="flex justify-between items-center mb-4">
                        <label class="text-[11px] font-bold uppercase tracking-widest text-slate-400">03. Calçado</label>
                        <span id="label-shoes" class="text-xs font-bold text-indigo-600 bg-indigo-50 px-3 py-1 rounded-lg">Couro Castanho</span>
                    </div>
                    <div id="grid-shoes" class="flex gap-4 overflow-x-auto pb-4 scrollbar-hide"></div>
                </section>
            </div>

            <!-- Botões de Rodapé -->
            <div class="mt-12 flex gap-4">
                <button onclick="randomize()" class="flex-1 flex items-center justify-center gap-2 py-4 bg-slate-50 hover:bg-slate-100 text-slate-600 rounded-2xl font-bold transition-all active:scale-95">
                    <i data-lucide="shuffle" class="w-4 h-4"></i> Random
                </button>
                <button onclick="copyLook()" class="flex-[2] flex items-center justify-center gap-2 py-4 bg-slate-900 hover:bg-black text-white rounded-2xl font-bold transition-all active:scale-95 shadow-xl shadow-slate-200">
                    <i data-lucide="copy" class="w-4 h-4"></i> Copiar Look
                </button>
            </div>
        </div>
    </div>

    <!-- Toast -->
    <div id="toast" class="fixed bottom-10 left-1/2 -translate-x-1/2 z-[100] transform translate-y-32 opacity-0 transition-all duration-500 pointer-events-none">
        <div class="bg-slate-900 text-white px-8 py-4 rounded-3xl shadow-2xl flex items-center gap-3">
            <i data-lucide="info" class="w-5 h-5 text-indigo-400"></i>
            <span id="toast-msg" class="text-sm font-bold uppercase tracking-wider">Ação concluída</span>
        </div>
    </div>

    <script>
        const apiKey = ""; 

        // Paleta Completa Baseada no Pedido
        const BASE_COLORS = [
            // Pretos
            { id: 'black', name: 'Preto', hex: '#111111', prompt: 'classic matte black' },
            { id: 'abs_black', name: 'Preto Absoluto', hex: '#000000', prompt: 'absolute pitch black' },
            { id: 'deep_black', name: 'Preto Profundo', hex: '#050505', prompt: 'deep intense black' },
            { id: 'onyx', name: 'Preto Ônix', hex: '#353839', prompt: 'onyx black carbon texture' },
            { id: 'matte_black', name: 'Preto Fosco', hex: '#28282b', prompt: 'matte finish deep black' },
            { id: 'gloss_black', name: 'Preto Brilhante', hex: '#1a1a1a', prompt: 'glossy reflective black' },
            // Azuis
            { id: 'blue', name: 'Azul', hex: '#2563eb', prompt: 'vibrant blue' },
            { id: 'royal_blue', name: 'Azul Royal', hex: '#4169e1', prompt: 'rich royal blue' },
            { id: 'navy', name: 'Azul Marinho', hex: '#1e3a5f', prompt: 'dark navy blue' },
            { id: 'sky_blue', name: 'Azul Céu', hex: '#87ceeb', prompt: 'soft sky blue' },
            { id: 'turquoise', name: 'Azul Turquesa', hex: '#40e0d0', prompt: 'turquoise blue' },
            { id: 'petrol', name: 'Azul Petróleo', hex: '#005f69', prompt: 'dark petrol blue-green' },
            { id: 'cobalt', name: 'Azul Bic', hex: '#0047ab', prompt: 'cobalt bic blue' },
            { id: 'sapphire', name: 'Azul Safira', hex: '#0f52ba', prompt: 'sapphire gemstone blue' },
            // Cinzas
            { id: 'grey', name: 'Cinza', hex: '#888f98', prompt: 'classic grey' },
            { id: 'light_grey', name: 'Cinza Claro', hex: '#d3d3d3', prompt: 'light heather grey' },
            { id: 'dark_grey', name: 'Cinza Escuro', hex: '#4b5563', prompt: 'dark slate grey' },
            { id: 'med_grey', name: 'Cinza Médio', hex: '#9ca3af', prompt: 'medium neutral grey' },
            { id: 'graphite', name: 'Cinza Grafite', hex: '#4b4b4b', prompt: 'dark graphite grey' },
            { id: 'charcoal', name: 'Cinza Chumbo', hex: '#36454f', prompt: 'deep charcoal charcoal grey' },
            { id: 'silver', name: 'Cinza Prata', hex: '#c0c0c0', prompt: 'metallic silver grey' },
            { id: 'smoke', name: 'Cinza Fumaça', hex: '#708090', prompt: 'smoke grey blue-toned' }
        ];

        const CONFIG = {
            shirt: [
                { id: 'white', name: 'Branco Oxford', hex: '#FFFFFF', prompt: 'crisp white luxury cotton shirt' },
                ...BASE_COLORS,
                { id: 'sage', name: 'Verde Sálvia', hex: '#a7f3d0', prompt: 'sage green linen' },
                { id: 'burgundy', name: 'Vinho Tinto', hex: '#7f1d1d', prompt: 'burgundy wool' }
            ],
            pants: [
                { id: 'khaki', name: 'Cáqui Areia', hex: '#d6d3d1', prompt: 'khaki sand chinos' },
                ...BASE_COLORS,
                { id: 'denim', name: 'Jeans Indigo', hex: '#1d4ed8', prompt: 'dark indigo denim' }
            ],
            shoes: [
                { id: 'brown', name: 'Couro Castanho', hex: '#451a03', prompt: 'dark brown leather' },
                ...BASE_COLORS,
                { id: 'white-s', name: 'Sneakers Brancos', hex: '#f8fafc', prompt: 'white leather sneakers' }
            ]
        };

        let state = {
            shirt: CONFIG.shirt[0],
            pants: CONFIG.pants[0],
            shoes: CONFIG.shoes[0],
            view: '2d',
            isGenerating: false,
            lastImage: null
        };

        function init() {
            lucide.createIcons();
            renderSelectors();
            updateUI();
        }

        function renderSelectors() {
            ['shirt', 'pants', 'shoes'].forEach(type => {
                const container = document.getElementById(`grid-${type}`);
                container.innerHTML = '';
                
                CONFIG[type].forEach(item => {
                    const isActive = state[type].id === item.id;
                    const btn = document.createElement('button');
                    btn.className = `w-14 h-14 rounded-2xl border-4 shrink-0 transition-all duration-300 transform hover:scale-110 active:scale-90 ${isActive ? 'border-indigo-600 scale-105 shadow-lg active-ring' : 'border-white shadow-sm'}`;
                    btn.style.backgroundColor = item.hex;
                    btn.title = item.name;
                    btn.onclick = () => {
                        state[type] = item;
                        updateUI();
                        renderSelectors();
                        if(state.view === 'ai') resetAiView();
                    };
                    container.appendChild(btn);
                });
            });
        }

        function updateUI() {
            document.getElementById('label-shirt').innerText = state.shirt.name;
            document.getElementById('label-pants').innerText = state.pants.name;
            document.getElementById('label-shoes').innerText = state.shoes.name;
            document.getElementById('summary-text').innerText = `${state.shirt.name} + ${state.pants.name}`;

            document.getElementById('svg-shirt').style.fill = state.shirt.hex;
            document.getElementById('svg-pants').style.fill = state.pants.hex;
            document.getElementById('svg-shoes-l').style.fill = state.shoes.hex;
            document.getElementById('svg-shoes-r').style.fill = state.shoes.hex;
        }

        function setView(mode) {
            state.view = mode;
            const tab2d = document.getElementById('tab-2d');
            const tabAi = document.getElementById('tab-ai');
            const preview2d = document.getElementById('preview-2d');
            const previewAi = document.getElementById('preview-ai');
            const mainActionBtn = document.getElementById('main-action-btn');

            if (mode === '2d') {
                tab2d.className = 'flex items-center gap-2 px-6 py-2.5 text-sm font-bold rounded-xl transition-all duration-300 bg-white text-indigo-600 shadow-sm';
                tabAi.className = 'flex items-center gap-2 px-6 py-2.5 text-sm font-bold rounded-xl transition-all duration-300 text-slate-500 hover:text-slate-800';
                preview2d.classList.remove('hidden');
                previewAi.classList.add('hidden');
                mainActionBtn.classList.add('hidden');
            } else {
                tabAi.className = 'flex items-center gap-2 px-6 py-2.5 text-sm font-bold rounded-xl transition-all duration-300 bg-white text-indigo-600 shadow-sm';
                tab2d.className = 'flex items-center gap-2 px-6 py-2.5 text-sm font-bold rounded-xl transition-all duration-300 text-slate-500 hover:text-slate-800';
                previewAi.classList.remove('hidden');
                preview2d.classList.add('hidden');
                mainActionBtn.classList.remove('hidden');
            }
        }

        function resetAiView() {
            document.getElementById('ai-img').classList.add('hidden');
            document.getElementById('ai-placeholder').classList.remove('hidden');
            document.getElementById('ai-actions').classList.add('hidden');
            state.lastImage = null;
        }

        async function generateImage() {
            if (state.isGenerating) return;
            
            setView('ai');
            state.isGenerating = true;
            const loader = document.getElementById('ai-loading');
            const imgEl = document.getElementById('ai-img');
            const placeholder = document.getElementById('ai-placeholder');
            const actions = document.getElementById('ai-actions');

            loader.classList.remove('hidden');
            imgEl.classList.add('hidden');
            placeholder.classList.add('hidden');
            actions.classList.add('hidden');

            const prompt = `Hyper-realistic professional fashion street photography of the man from the reference image, walking on a european cobblestone street in front of classic buildings. He wears a ${state.shirt.prompt} button-up shirt with rolled sleeves, ${state.pants.prompt} pleated chinos, and ${state.shoes.prompt} loafers. The lighting is golden hour, shot on a Sony A7R IV, 8k resolution.`;

            const makeRequest = async () => {
                const response = await fetch(`https://generativelanguage.googleapis.com/v1beta/models/imagen-4.0-generate-001:predict?key=${apiKey}`, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify({
                        instances: [{ prompt }],
                        parameters: { sampleCount: 1 }
                    })
                });

                if (!response.ok) throw new Error('API_FAIL');
                const data = await response.json();
                return `data:image/png;base64,${data.predictions[0].bytesBase64Encoded}`;
            };

            const runWithRetry = async (retries = 5, delay = 1000) => {
                try {
                    return await makeRequest();
                } catch (err) {
                    if (retries > 0) {
                        await new Promise(r => setTimeout(r, delay));
                        return runWithRetry(retries - 1, delay * 2);
                    }
                    throw err;
                }
            };

            try {
                const imageUrl = await runWithRetry();
                state.lastImage = imageUrl;
                imgEl.src = imageUrl;
                imgEl.onload = () => {
                    loader.classList.add('hidden');
                    imgEl.classList.remove('hidden');
                    actions.classList.remove('hidden');
                };
            } catch (err) {
                showToast("Erro na ligação à IA. Tente novamente.");
                loader.classList.add('hidden');
                placeholder.classList.remove('hidden');
            } finally {
                state.isGenerating = false;
            }
        }

        function randomize() {
            state.shirt = CONFIG.shirt[Math.floor(Math.random() * CONFIG.shirt.length)];
            state.pants = CONFIG.pants[Math.floor(Math.random() * CONFIG.pants.length)];
            state.shoes = CONFIG.shoes[Math.floor(Math.random() * CONFIG.shoes.length)];
            updateUI();
            renderSelectors();
            showToast("Estilo baralhado!");
        }

        function copyLook() {
            const text = `Meu Look IA:\nPeça Superior: ${state.shirt.name}\nPeça Inferior: ${state.pants.name}\nCalçado: ${state.shoes.name}`;
            const el = document.createElement('textarea');
            el.value = text;
            document.body.appendChild(el);
            el.select();
            document.execCommand('copy');
            document.body.removeChild(el);
            showToast("Look copiado para o clipboard!");
        }

        function downloadImage() {
            if (!state.lastImage) return;
            const a = document.createElement('a');
            a.href = state.lastImage;
            a.download = `look-masculino-${Date.now()}.png`;
            a.click();
        }

        function showToast(msg) {
            const toast = document.getElementById('toast');
            document.getElementById('toast-msg').innerText = msg;
            toast.classList.remove('translate-y-32', 'opacity-0');
            setTimeout(() => {
                toast.classList.add('translate-y-32', 'opacity-0');
            }, 3000);
        }

        window.onload = init;
    </script>
</body>
</html>

