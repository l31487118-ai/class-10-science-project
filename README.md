<!DOCTYPE html>
<html lang="en" class="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PROJECT ATHER-9 // Futuristic NASA Ion Thruster Engine Command & Blueprint Hub</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts: Orbitron & Inter -->
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;600;800;900&family=Inter:wght@300;400;500;600;700&family=JetBrains+Mono:wght@400;600&display=swap" rel="stylesheet">
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                        orbitron: ['Orbitron', 'sans-serif'],
                        mono: ['JetBrains Mono', 'monospace'],
                    },
                    colors: {
                        cyber: {
                            950: '#020613',
                            900: '#050c1e',
                            800: '#0a162e',
                            700: '#0f2248',
                            cyan: '#00f0ff',
                            neon: '#39ff14',
                            orange: '#ff6b00',
                            purple: '#a855f7',
                            magenta: '#ff007f'
                        }
                    }
                }
            }
        }
    </script>
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #020613;
            color: #e2e8f0;
            overflow-x: hidden;
            background-image: 
                radial-gradient(circle at 50% 0%, rgba(0, 240, 255, 0.08) 0%, transparent 60%),
                linear-gradient(to bottom, rgba(5, 12, 30, 0.8), rgba(2, 6, 19, 0.98));
        }

        /* Scanline Overlay Effect */
        .scanlines {
            background: linear-gradient(
                to bottom,
                rgba(255,255,255,0),
                rgba(255,255,255,0) 50%,
                rgba(0, 0, 0, 0.3) 50%,
                rgba(0, 0, 0, 0.3)
            );
            background-size: 100% 4px;
        }

        /* Glowing Effects */
        .glow-cyan {
            box-shadow: 0 0 20px rgba(0, 240, 255, 0.25), inset 0 0 15px rgba(0, 240, 255, 0.1);
            border: 1px solid rgba(0, 240, 255, 0.4);
        }
        .glow-orange {
            box-shadow: 0 0 20px rgba(255, 107, 0, 0.25), inset 0 0 15px rgba(255, 107, 0, 0.1);
            border: 1px solid rgba(255, 107, 0, 0.4);
        }
        .glow-neon {
            box-shadow: 0 0 20px rgba(57, 255, 20, 0.25), inset 0 0 15px rgba(57, 255, 20, 0.1);
            border: 1px solid rgba(57, 255, 20, 0.4);
        }
        .glow-text-cyan {
            text-shadow: 0 0 10px rgba(0, 240, 255, 0.8), 0 0 20px rgba(0, 240, 255, 0.4);
        }
        .glow-text-orange {
            text-shadow: 0 0 10px rgba(255, 107, 0, 0.8), 0 0 20px rgba(255, 107, 0, 0.4);
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 5px;
            height: 5px;
        }
        ::-webkit-scrollbar-track {
            background: #050c1e;
        }
        ::-webkit-scrollbar-thumb {
            background: #00f0ff;
            border-radius: 2px;
        }

        /* Hud Clip Paths */
        .hud-corner {
            clip-path: polygon(0 0, calc(100% - 12px) 0, 100% 12px, 100% 100%, 12px 100%, 0 calc(100% - 12px));
        }

        @keyframes pulse-fast {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.4; }
        }
        .animate-pulse-fast {
            animation: pulse-fast 1.2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
        }
    </style>
</head>
<body class="min-h-screen flex flex-col antialiased selection:bg-cyber-cyan selection:text-black">

    <div class="pointer-events-none fixed inset-0 z-50 scanlines opacity-30"></div>

    <!-- TOP HUD HEADER -->
    <header class="border-b border-cyber-cyan/30 bg-cyber-900/90 backdrop-blur-md sticky top-0 z-40 px-4 py-3">
        <div class="max-w-7xl mx-auto flex flex-wrap items-center justify-between gap-4">
            
            <!-- Logo & Code System Name -->
            <div class="flex items-center space-x-4">
                <div class="relative flex items-center justify-center w-12 h-12 bg-cyber-800/80 border border-cyber-cyan rounded-lg glow-cyan">
                    <i class="fa-solid fa-atom text-2xl text-cyber-cyan animate-spin" style="animation-duration: 8s;"></i>
                    <span class="absolute -top-1 -right-1 flex h-3 w-3">
                        <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-cyber-cyan opacity-75"></span>
                        <span class="relative inline-flex rounded-full h-3 w-3 bg-cyber-cyan"></span>
                    </span>
                </div>
                <div>
                    <div class="flex items-center space-x-2">
                        <h1 class="font-orbitron font-black text-xl text-white tracking-widest glow-text-cyan">PROJECT ATHER-9</h1>
                        <span class="px-2 py-0.5 text-[10px] font-mono font-bold uppercase tracking-wider bg-cyber-cyan/20 text-cyber-cyan border border-cyber-cyan/40 rounded">NEXT-GEN PLASMA THRUSTER</span>
                    </div>
                    <p class="text-xs font-mono text-gray-400">NASA-SPEC ELECTROSTATIC HALL & GRIDDED ION PROPULSION CORE</p>
                </div>
            </div>

            <!-- Status HUD Telemetry Pill -->
            <div class="flex items-center space-x-6 text-xs font-mono bg-cyber-950/80 border border-cyber-cyan/30 px-4 py-2 rounded-lg hud-corner">
                <div class="flex items-center space-x-2">
                    <span class="text-gray-400">SYSTEM:</span>
                    <span id="sys-status" class="text-cyber-neon font-bold flex items-center gap-1.5">
                        <i class="fa-solid fa-circle text-[8px] animate-pulse"></i> READY // NOMINAL
                    </span>
                </div>
                <div class="hidden sm:flex items-center space-x-2 border-l border-cyber-cyan/20 pl-4">
                    <span class="text-gray-400">REACTOR TEMP:</span>
                    <span id="sys-temp-head" class="text-cyber-cyan font-bold">14,200 K</span>
                </div>
                <div class="hidden md:flex items-center space-x-2 border-l border-cyber-cyan/20 pl-4">
                    <span class="text-gray-400">PLUME EFFICIENCY:</span>
                    <span id="sys-eff-head" class="text-cyber-neon font-bold">96.8%</span>
                </div>
            </div>

            <!-- Action Buttons -->
            <div class="flex items-center space-x-2">
                <button onclick="toggleEmergencyOverdrive()" id="overdrive-btn" class="px-3 py-2 bg-cyber-orange/20 hover:bg-cyber-orange/40 text-cyber-orange border border-cyber-orange/60 font-orbitron text-xs font-bold rounded transition-all glow-orange flex items-center gap-2">
                    <i class="fa-solid fa-bolt animate-bounce"></i> OVERDRIVE MODE
                </button>
            </div>
        </div>
    </header>

    <main class="flex-1 max-w-7xl w-full mx-auto px-4 py-6 space-y-6">

        <!-- SECTION 1: VISUAL REAL-TIME PLASMA & PARTICLE ACCELERATION ENGINE -->
        <section class="bg-cyber-900/80 rounded-xl border border-cyber-cyan/40 p-5 glow-cyan relative overflow-hidden backdrop-blur-lg">
            
            <!-- Canvas Header Toolbar -->
            <div class="flex flex-wrap items-center justify-between pb-4 border-b border-cyber-cyan/20 gap-3">
                <div class="flex items-center space-x-3">
                    <div class="w-3 h-3 bg-cyber-cyan rounded-full animate-ping"></div>
                    <h2 class="font-orbitron font-bold text-lg text-white tracking-wider flex items-center gap-2">
                        <span>LIVE PLASMA CHAMBER & PARTICLE ACCELERATOR</span>
                    </h2>
                </div>

                <div class="flex items-center space-x-2 text-xs font-mono">
                    <button onclick="setVisualMode('simulation')" id="view-btn-sim" class="px-3 py-1.5 rounded bg-cyber-cyan text-cyber-950 font-bold font-orbitron transition-all">
                        <i class="fa-solid fa-play mr-1"></i> DYNAMIC SIM
                    </button>
                    <button onclick="setVisualMode('blueprint')" id="view-btn-blue" class="px-3 py-1.5 rounded bg-cyber-800 text-cyber-cyan border border-cyber-cyan/40 hover:bg-cyber-700 font-orbitron transition-all">
                        <i class="fa-solid fa-drafting-compass mr-1"></i> BLUEPRINT SCHEMATIC
                    </button>
                </div>
            </div>

            <!-- Canvas Visualization Container -->
            <div class="relative bg-cyber-950 rounded-lg border border-cyber-cyan/30 mt-4 overflow-hidden h-[420px] shadow-inner flex items-center justify-center">
                <canvas id="plasmaCanvas" class="w-full h-full block cursor-crosshair"></canvas>

                <!-- Floating Controls Overlay on Canvas -->
                <div class="absolute top-4 left-4 bg-cyber-900/90 border border-cyber-cyan/40 p-3 rounded-lg text-xs font-mono space-y-2 backdrop-blur-md hidden sm:block">
                    <div class="text-cyber-cyan font-bold font-orbitron flex items-center gap-2">
                        <i class="fa-solid fa-microchip"></i> LIVE CHAMBER DIAGNOSTICS
                    </div>
                    <div class="grid grid-cols-2 gap-x-4 gap-y-1 text-gray-300">
                        <span>GAS SPECIES:</span> <span class="text-white font-bold">XENON (Xe)</span>
                        <span>ION CHARGE:</span> <span class="text-cyber-cyan font-bold">+1 SINGLE-ION</span>
                        <span>MAG CONFINEMENT:</span> <span id="diag-mag" class="text-cyber-neon font-bold">0.18 T</span>
                        <span>GRID POTENTIAL:</span> <span id="diag-volt" class="text-cyber-orange font-bold">2.50 kV</span>
                    </div>
                </div>

                <!-- Particle Type Legend -->
                <div class="absolute bottom-4 right-4 bg-cyber-900/90 border border-cyber-cyan/40 px-3 py-2 rounded-lg text-[11px] font-mono space-y-1 backdrop-blur-md">
                    <div class="text-gray-400 font-bold mb-1 border-b border-cyber-cyan/20 pb-0.5">PARTICLE KEY</div>
                    <div class="flex items-center space-x-2">
                        <span class="w-2.5 h-2.5 rounded-full bg-cyber-cyan shadow-[0_0_8px_#00f0ff]"></span>
                        <span class="text-white">Xenon Ion (Xe+)</span>
                    </div>
                    <div class="flex items-center space-x-2">
                        <span class="w-2.5 h-2.5 rounded-full bg-cyber-orange shadow-[0_0_8px_#ff6b00]"></span>
                        <span class="text-white">Stripped Electron (e-)</span>
                    </div>
                    <div class="flex items-center space-x-2">
                        <span class="w-2.5 h-2.5 rounded-full bg-gray-400"></span>
                        <span class="text-gray-400">Neutral Xenon Gas (Xe)</span>
                    </div>
                </div>
            </div>
        </section>

        <!-- SECTION 2: TELEMETRY HUD & QUANTUM METRICS -->
        <section class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4">
            
            <!-- Metric 1: Thrust Force -->
            <div class="bg-cyber-900/90 border border-cyber-cyan/30 rounded-xl p-4 glow-cyan relative overflow-hidden">
                <div class="flex justify-between items-start mb-2">
                    <span class="text-xs font-mono text-gray-400">TOTAL THRUST FORCE</span>
                    <i class="fa-solid fa-rocket text-cyber-cyan"></i>
                </div>
                <div class="flex items-baseline space-x-2">
                    <span id="metric-thrust" class="font-orbitron font-black text-3xl text-white glow-text-cyan">236.4</span>
                    <span class="text-sm font-mono text-cyber-cyan">mN</span>
                </div>
                <div class="mt-2 w-full bg-cyber-950 h-1.5 rounded-full overflow-hidden border border-cyber-cyan/20">
                    <div id="bar-thrust" class="bg-cyber-cyan h-full transition-all duration-300" style="width: 60%;"></div>
                </div>
                <span class="text-[10px] font-mono text-gray-500 mt-1 block">CALCULATED FROM MASS FLOW & EXHAUST VELOCITY</span>
            </div>

            <!-- Metric 2: Specific Impulse (Isp) -->
            <div class="bg-cyber-900/90 border border-cyber-cyan/30 rounded-xl p-4 glow-cyan relative overflow-hidden">
                <div class="flex justify-between items-start mb-2">
                    <span class="text-xs font-mono text-gray-400">SPECIFIC IMPULSE (Isp)</span>
                    <i class="fa-solid fa-gauge-high text-cyber-neon"></i>
                </div>
                <div class="flex items-baseline space-x-2">
                    <span id="metric-isp" class="font-orbitron font-black text-3xl text-white text-cyber-neon">4,280</span>
                    <span class="text-sm font-mono text-cyber-neon">sec</span>
                </div>
                <div class="mt-2 w-full bg-cyber-950 h-1.5 rounded-full overflow-hidden border border-cyber-neon/20">
                    <div id="bar-isp" class="bg-cyber-neon h-full transition-all duration-300" style="width: 75%;"></div>
                </div>
                <span class="text-[10px] font-mono text-gray-500 mt-1 block">FUEL EFFICIENCY (10X HIGHER THAN CHEMICAL ROCKETS)</span>
            </div>

            <!-- Metric 3: Beam Exhaust Speed -->
            <div class="bg-cyber-900/90 border border-cyber-cyan/30 rounded-xl p-4 glow-cyan relative overflow-hidden">
                <div class="flex justify-between items-start mb-2">
                    <span class="text-xs font-mono text-gray-400">BEAM EXHAUST VELOCITY</span>
                    <i class="fa-solid fa-wind text-cyber-orange"></i>
                </div>
                <div class="flex items-baseline space-x-2">
                    <span id="metric-speed" class="font-orbitron font-black text-3xl text-white text-cyber-orange">42.0</span>
                    <span class="text-sm font-mono text-cyber-orange">km/s</span>
                </div>
                <div class="mt-2 w-full bg-cyber-950 h-1.5 rounded-full overflow-hidden border border-cyber-orange/20">
                    <div id="bar-speed" class="bg-cyber-orange h-full transition-all duration-300" style="width: 70%;"></div>
                </div>
                <span class="text-[10px] font-mono text-gray-500 mt-1 block">ELECTROSTATIC ACCELERATION SPEED</span>
            </div>

            <!-- Metric 4: Power Consumption -->
            <div class="bg-cyber-900/90 border border-cyber-cyan/30 rounded-xl p-4 glow-cyan relative overflow-hidden">
                <div class="flex justify-between items-start mb-2">
                    <span class="text-xs font-mono text-gray-400">TOTAL POWER DRAW</span>
                    <i class="fa-solid fa-bolt text-cyber-purple"></i>
                </div>
                <div class="flex items-baseline space-x-2">
                    <span id="metric-power" class="font-orbitron font-black text-3xl text-white text-cyber-purple">5.25</span>
                    <span class="text-sm font-mono text-cyber-purple">kW</span>
                </div>
                <div class="mt-2 w-full bg-cyber-950 h-1.5 rounded-full overflow-hidden border border-cyber-purple/20">
                    <div id="bar-power" class="bg-cyber-purple h-full transition-all duration-300" style="width: 50%;"></div>
                </div>
                <span class="text-[10px] font-mono text-gray-500 mt-1 block">SUPPLIED VIA SOLAR ARRAYS / NUCLEAR REACTOR</span>
            </div>

        </section>

        <!-- SECTION 3: SYSTEM CONTROL DECK & INTERACTIVE BLUEPRINT SPEC SHEET -->
        <section class="grid grid-cols-1 lg:grid-cols-3 gap-6">
            
            <!-- Left 2 Columns: Futuristic Sliders Deck -->
            <div class="lg:col-span-2 bg-cyber-900/90 border border-cyber-cyan/30 rounded-xl p-6 glow-cyan space-y-6 backdrop-blur-lg">
                <div class="flex justify-between items-center pb-3 border-b border-cyber-cyan/20">
                    <h3 class="font-orbitron font-bold text-white tracking-wider text-base flex items-center gap-2">
                        <i class="fa-solid fa-sliders text-cyber-cyan"></i>
                        <span>PROPULSION CONTROL DECK</span>
                    </h3>
                    <button onclick="resetToNASAStandard()" class="px-3 py-1 bg-cyber-800 hover:bg-cyber-700 text-cyber-cyan border border-cyber-cyan/40 text-xs font-mono rounded transition-all">
                        <i class="fa-solid fa-rotate-left mr-1"></i> RESET NASA SPECS
                    </button>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    
                    <!-- Slider 1: Accelerator Grid Voltage -->
                    <div class="bg-cyber-950 p-4 rounded-lg border border-cyber-cyan/20 space-y-2">
                        <div class="flex justify-between items-center">
                            <label for="sliderVoltage" class="text-xs font-mono text-gray-300">ELECTROSTATIC GRID VOLTAGE</label>
                            <span id="val-voltage" class="font-mono text-cyber-cyan font-bold text-sm">2.50 kV</span>
                        </div>
                        <input type="range" id="sliderVoltage" min="0.5" max="6.0" step="0.1" value="2.5" oninput="updateSystemCalculations()" class="w-full accent-cyber-cyan bg-cyber-800 h-2 rounded cursor-pointer">
                        <div class="flex justify-between text-[10px] font-mono text-gray-500">
                            <span>0.5 kV (Idle)</span>
                            <span>6.0 kV (Max Ion Velocity)</span>
                        </div>
                    </div>

                    <!-- Slider 2: Xenon Propellant Mass Flow Rate -->
                    <div class="bg-cyber-950 p-4 rounded-lg border border-cyber-cyan/20 space-y-2">
                        <div class="flex justify-between items-center">
                            <label for="sliderFlow" class="text-xs font-mono text-gray-300">XENON PROPELLANT FLOW</label>
                            <span id="val-flow" class="font-mono text-cyber-neon font-bold text-sm">5.5 mg/s</span>
                        </div>
                        <input type="range" id="sliderFlow" min="1.0" max="15.0" step="0.5" value="5.5" oninput="updateSystemCalculations()" class="w-full accent-cyber-neon bg-cyber-800 h-2 rounded cursor-pointer">
                        <div class="flex justify-between text-[10px] font-mono text-gray-500">
                            <span>1.0 mg/s (Low Density)</span>
                            <span>15.0 mg/s (High Thrust)</span>
                        </div>
                    </div>

                    <!-- Slider 3: Magnetic Confinement Field -->
                    <div class="bg-cyber-950 p-4 rounded-lg border border-cyber-cyan/20 space-y-2">
                        <div class="flex justify-between items-center">
                            <label for="sliderMag" class="text-xs font-mono text-gray-300">MAGNETIC FIELD (TESLA)</label>
                            <span id="val-mag" class="font-mono text-cyber-orange font-bold text-sm">0.18 T</span>
                        </div>
                        <input type="range" id="sliderMag" min="0.05" max="0.50" step="0.01" value="0.18" oninput="updateSystemCalculations()" class="w-full accent-cyber-orange bg-cyber-800 h-2 rounded cursor-pointer">
                        <div class="flex justify-between text-[10px] font-mono text-gray-500">
                            <span>0.05 T (Loose Plasma)</span>
                            <span>0.50 T (Tight Pinch)</span>
                        </div>
                    </div>

                    <!-- Slider 4: RF Ionization Power -->
                    <div class="bg-cyber-950 p-4 rounded-lg border border-cyber-cyan/20 space-y-2">
                        <div class="flex justify-between items-center">
                            <label for="sliderRF" class="text-xs font-mono text-gray-300">RF IONIZATION POWER</label>
                            <span id="val-rf" class="font-mono text-cyber-purple font-bold text-sm">1.80 kW</span>
                        </div>
                        <input type="range" id="sliderRF" min="0.5" max="4.0" step="0.1" value="1.8" oninput="updateSystemCalculations()" class="w-full accent-cyber-purple bg-cyber-800 h-2 rounded cursor-pointer">
                        <div class="flex justify-between text-[10px] font-mono text-gray-500">
                            <span>0.5 kW (Low Ion Rate)</span>
                            <span>4.0 kW (Full Ionization)</span>
                        </div>
                    </div>

                </div>

                <!-- Live Physics Explainer Note -->
                <div class="bg-cyber-950/80 p-4 rounded-lg border border-cyber-cyan/30 flex items-start space-x-3 text-xs font-mono text-gray-300">
                    <i class="fa-solid fa-lightbulb text-cyber-cyan text-base mt-0.5"></i>
                    <div>
                        <span class="text-cyber-cyan font-bold block mb-1">PHYSICS DYNAMICS SUMMARY:</span>
                        <p id="physics-note" class="leading-relaxed">
                            Increasing Electrostatic Grid Voltage directly accelerates positively charged Xenon ions (Xe+) to ultra-high speeds, yielding maximum Isp. Increasing Propellant Flow Rate provides more ion density for higher absolute thrust force (mN).
                        </p>
                    </div>
                </div>
            </div>

            <!-- Right Column: Interactive Component Inspector -->
            <div class="bg-cyber-900/90 border border-cyber-cyan/30 rounded-xl p-6 glow-cyan space-y-4 backdrop-blur-lg flex flex-col justify-between">
                <div>
                    <div class="flex items-center space-x-2 pb-3 border-b border-cyber-cyan/20 mb-4">
                        <i class="fa-solid fa-cubes text-cyber-cyan"></i>
                        <h3 class="font-orbitron font-bold text-white text-sm">COMPONENT INSPECTOR</h3>
                    </div>

                    <!-- Component Selection Selector -->
                    <div class="space-y-2 mb-4 font-mono text-xs">
                        <button onclick="selectComponent('chamber')" id="comp-btn-chamber" class="w-full text-left p-2.5 rounded bg-cyber-cyan/20 border border-cyber-cyan text-cyber-cyan font-bold transition-all flex justify-between items-center">
                            <span>1. DISCHARGE CHAMBER</span>
                            <i class="fa-solid fa-chevron-right text-xs"></i>
                        </button>
                        <button onclick="selectComponent('grids')" id="comp-btn-grids" class="w-full text-left p-2.5 rounded bg-cyber-950 hover:bg-cyber-800 border border-cyber-cyan/20 text-gray-300 transition-all flex justify-between items-center">
                            <span>2. ACCELERATOR GRIDS</span>
                            <i class="fa-solid fa-chevron-right text-xs"></i>
                        </button>
                        <button onclick="selectComponent('neutralizer')" id="comp-btn-neutralizer" class="w-full text-left p-2.5 rounded bg-cyber-950 hover:bg-cyber-800 border border-cyber-cyan/20 text-gray-300 transition-all flex justify-between items-center">
                            <span>3. HOLLOW CATHODE NEUTRALIZER</span>
                            <i class="fa-solid fa-chevron-right text-xs"></i>
                        </button>
                        <button onclick="selectComponent('magnets')" id="comp-btn-magnets" class="w-full text-left p-2.5 rounded bg-cyber-950 hover:bg-cyber-800 border border-cyber-cyan/20 text-gray-300 transition-all flex justify-between items-center">
                            <span>4. MAGNETIC RINGS</span>
                            <i class="fa-solid fa-chevron-right text-xs"></i>
                        </button>
                    </div>

                    <!-- Dynamic Spec Card -->
                    <div class="bg-cyber-950 p-4 rounded-lg border border-cyber-cyan/30 font-mono text-xs space-y-2">
                        <h4 id="comp-title" class="font-orbitron font-bold text-cyber-cyan text-sm">DISCHARGE & IONIZATION CHAMBER</h4>
                        <p id="comp-desc" class="text-gray-300 leading-relaxed">
                            Where neutral Xenon gas atoms are bombarded by high-energy electrons emitted by the internal discharge cathode, stripping electrons off Xenon atoms to generate dense plasma.
                        </p>
                        <div class="pt-2 border-t border-cyber-cyan/20 text-[11px] text-gray-400 space-y-1">
                            <div>MATERIAL: <span id="comp-mat" class="text-white">TITANIUM-MOLYBDENUM ALLOY</span></div>
                            <div>OPERATING TEMP: <span id="comp-temp" class="text-cyber-orange">1,200 °C</span></div>
                        </div>
                    </div>
                </div>

                <div class="pt-4 border-t border-cyber-cyan/20 text-center">
                    <span class="text-[10px] font-mono text-gray-500">PROJECT ATHER-9 ARCHITECTURE // NASA SPECIFICATION CLASS</span>
                </div>
            </div>

        </section>

    </main>

    <!-- Footer -->
    <footer class="border-t border-cyber-cyan/20 bg-cyber-900/80 py-4 text-center text-xs font-mono text-gray-500 mt-auto">
        <p>PROJECT ATHER-9 // HIGH-POWER ION PROPULSION SIMULATION PLATFORM</p>
    </footer>

    <script>
        // Global Simulation State Variables
        let canvas, ctx;
        let particles = [];
        let visualMode = 'simulation'; // 'simulation' or 'blueprint'
        let isOverdrive = false;
        let selectedComponent = 'chamber';

        // Physics Parameters
        let voltage = 2.5; // kV
        let flowRate = 5.5; // mg/s
        let magneticField = 0.18; // Tesla
        let rfPower = 1.8; // kW

        window.onload = function() {
            canvas = document.getElementById('plasmaCanvas');
            ctx = canvas.getContext('2d');
            resizeCanvas();

            // Spawn Initial Particle Swarm
            initParticles();

            // Run Physics Calculations
            updateSystemCalculations();

            // Start Animation Loop
            animate();
        };

        window.addEventListener('resize', resizeCanvas);

        function resizeCanvas() {
            if (!canvas) return;
            canvas.width = canvas.parentElement.clientWidth;
            canvas.height = canvas.parentElement.clientHeight;
        }

        function initParticles() {
            particles = [];
            const count = 120;
            for (let i = 0; i < count; i++) {
                particles.push(spawnParticle());
            }
        }

        function spawnParticle() {
            const chamberEndX = canvas.width * 0.45;
            const rand = Math.random();
            let type = 'neutral';
            
            if (rand < 0.6) type = 'ion';
            else if (rand < 0.85) type = 'electron';

            return {
                x: Math.random() * chamberEndX,
                y: canvas.height / 2 + (Math.random() - 0.5) * (canvas.height * 0.4),
                vx: Math.random() * 1.2 + 0.5,
                vy: (Math.random() - 0.5) * 0.8,
                radius: type === 'electron' ? 2 : (type === 'ion' ? 4 : 3.5),
                type: type,
                charge: type === 'ion' ? 1 : (type === 'electron' ? -1 : 0),
                life: Math.random() * 100
            };
        }

        function setVisualMode(mode) {
            visualMode = mode;
            const btnSim = document.getElementById('view-btn-sim');
            const btnBlue = document.getElementById('view-btn-blue');

            if (mode === 'simulation') {
                btnSim.className = 'px-3 py-1.5 rounded bg-cyber-cyan text-cyber-950 font-bold font-orbitron transition-all';
                btnBlue.className = 'px-3 py-1.5 rounded bg-cyber-800 text-cyber-cyan border border-cyber-cyan/40 hover:bg-cyber-700 font-orbitron transition-all';
            } else {
                btnBlue.className = 'px-3 py-1.5 rounded bg-cyber-cyan text-cyber-950 font-bold font-orbitron transition-all';
                btnSim.className = 'px-3 py-1.5 rounded bg-cyber-800 text-cyber-cyan border border-cyber-cyan/40 hover:bg-cyber-700 font-orbitron transition-all';
            }
        }

        function toggleEmergencyOverdrive() {
            isOverdrive = !isOverdrive;
            const btn = document.getElementById('overdrive-btn');
            if (isOverdrive) {
                document.getElementById('sliderVoltage').value = 5.5;
                document.getElementById('sliderFlow').value = 12.0;
                document.getElementById('sliderRF').value = 3.8;
                btn.className = 'px-3 py-2 bg-cyber-orange text-black font-orbitron text-xs font-bold rounded transition-all glow-orange animate-pulse flex items-center gap-2';
                btn.innerHTML = '<i class="fa-solid fa-triangle-exclamation"></i> OVERDRIVE ACTIVE!';
            } else {
                btn.className = 'px-3 py-2 bg-cyber-orange/20 hover:bg-cyber-orange/40 text-cyber-orange border border-cyber-orange/60 font-orbitron text-xs font-bold rounded transition-all glow-orange flex items-center gap-2';
                btn.innerHTML = '<i class="fa-solid fa-bolt animate-bounce"></i> OVERDRIVE MODE';
            }
            updateSystemCalculations();
        }

        function resetToNASAStandard() {
            document.getElementById('sliderVoltage').value = 2.5;
            document.getElementById('sliderFlow').value = 5.5;
            document.getElementById('sliderMag').value = 0.18;
            document.getElementById('sliderRF').value = 1.8;
            isOverdrive = false;
            const btn = document.getElementById('overdrive-btn');
            btn.className = 'px-3 py-2 bg-cyber-orange/20 hover:bg-cyber-orange/40 text-cyber-orange border border-cyber-orange/60 font-orbitron text-xs font-bold rounded transition-all glow-orange flex items-center gap-2';
            btn.innerHTML = '<i class="fa-solid fa-bolt animate-bounce"></i> OVERDRIVE MODE';
            updateSystemCalculations();
        }

        function updateSystemCalculations() {
            voltage = parseFloat(document.getElementById('sliderVoltage').value);
            flowRate = parseFloat(document.getElementById('sliderFlow').value);
            magneticField = parseFloat(document.getElementById('sliderMag').value);
            rfPower = parseFloat(document.getElementById('sliderRF').value);

            // Update UI Slider Text Labels
            document.getElementById('val-voltage').innerText = voltage.toFixed(2) + ' kV';
            document.getElementById('val-flow').innerText = flowRate.toFixed(1) + ' mg/s';
            document.getElementById('val-mag').innerText = magneticField.toFixed(2) + ' T';
            document.getElementById('val-rf').innerText = rfPower.toFixed(2) + ' kW';

            // Diagnostics overlay
            document.getElementById('diag-mag').innerText = magneticField.toFixed(2) + ' T';
            document.getElementById('diag-volt').innerText = voltage.toFixed(2) + ' kV';

            // Real Physics Equations (Scaled for Telemetry UI)
            const velocityKmS = Math.sqrt(voltage) * 26.5; // km/s
            const isp = Math.round(velocityKmS * 101.9); // seconds
            const thrustN = (flowRate * 1e-6) * (velocityKmS * 1000); // mN
            const thrustmN = thrustN * 1000 * 1.6;
            const powerKW = (0.5 * (flowRate * 1e-6) * Math.pow(velocityKmS * 1000, 2)) / 1000 + rfPower;

            // Render Metrics
            document.getElementById('metric-thrust').innerText = thrustmN.toFixed(1);
            document.getElementById('metric-isp').innerText = isp.toLocaleString();
            document.getElementById('metric-speed').innerText = velocityKmS.toFixed(1);
            document.getElementById('metric-power').innerText = powerKW.toFixed(2);

            // Progress Bars
            document.getElementById('bar-thrust').style.width = Math.min(100, (thrustmN / 500) * 100) + '%';
            document.getElementById('bar-isp').style.width = Math.min(100, (isp / 7000) * 100) + '%';
            document.getElementById('bar-speed').style.width = Math.min(100, (velocityKmS / 70) * 100) + '%';
            document.getElementById('bar-power').style.width = Math.min(100, (powerKW / 12) * 100) + '%';

            // Reactor Temperature Header Update
            const chamberTemp = Math.round(12000 + rfPower * 1800 + voltage * 800);
            document.getElementById('sys-temp-head').innerText = chamberTemp.toLocaleString() + ' K';

            // Physics Explanation Note Update
            const note = document.getElementById('physics-note');
            if (voltage > 4.5) {
                note.innerHTML = `<span class="text-cyber-orange font-bold">HIGH ACCELERATION STATE:</span> Grid potential at ${voltage.toFixed(2)} kV generates extreme electrostatic force, giving hyper-velocity exhaust beams at ${velocityKmS.toFixed(1)} km/s!`;
            } else if (flowRate > 10.0) {
                note.innerHTML = `<span class="text-cyber-neon font-bold">HIGH DENSITY PLUME:</span> Propellant mass flow rate boosted to ${flowRate.toFixed(1)} mg/s, creating dense ion beam output for heavy thrust maneuvers.`;
            } else {
                note.innerHTML = `Increasing Grid Voltage accelerates positively charged Xenon ions (Xe+) to ultra-high speeds (Isp). Mass Flow Rate controls raw thrust output (mN).`;
            }
        }

        function selectComponent(comp) {
            selectedComponent = comp;
            const comps = ['chamber', 'grids', 'neutralizer', 'magnets'];
            comps.forEach(c => {
                const btn = document.getElementById(`comp-btn-${c}`);
                if (c === comp) {
                    btn.className = 'w-full text-left p-2.5 rounded bg-cyber-cyan/20 border border-cyber-cyan text-cyber-cyan font-bold transition-all flex justify-between items-center shadow-[0_0_10px_rgba(0,240,255,0.2)]';
                } else {
                    btn.className = 'w-full text-left p-2.5 rounded bg-cyber-950 hover:bg-cyber-800 border border-cyber-cyan/20 text-gray-300 transition-all flex justify-between items-center';
                }
            });

            const title = document.getElementById('comp-title');
            const desc = document.getElementById('comp-desc');
            const mat = document.getElementById('comp-mat');
            const temp = document.getElementById('comp-temp');

            if (comp === 'chamber') {
                title.innerText = 'DISCHARGE & IONIZATION CHAMBER';
                desc.innerText = 'High-frequency electromagnetic coils blast neutral Xenon gas with electrons, stripping them away to form a glowing plasma state (+1 Ions & Free Electrons).';
                mat.innerText = 'TITANIUM-MOLYBDENUM ALLOY';
                temp.innerText = '1,450 °C';
            } else if (comp === 'grids') {
                title.innerText = 'DUAL ACCELERATOR GRIDS';
                desc.innerText = 'Perforated electrostatic metal plates (Screen Grid + Accelerator Grid) charged up to 6.0 kV that grab positive ions and violently shoot them out at supersonic speeds.';
                mat.innerText = 'CARBON-CARBON / GRAPHITE GRID';
                temp.innerText = '850 °C';
            } else if (comp === 'neutralizer') {
                title.innerText = 'HOLLOW CATHODE NEUTRALIZER';
                desc.innerText = 'Sprays a continuous stream of negative electrons directly into the exiting ion beam. Without this, the spacecraft would build a huge negative static charge and pull the ions back!';
                mat.innerText = 'LANTHANUM HEXABORIDE (LaB6)';
                temp.innerText = '1,650 °C';
            } else if (comp === 'magnets') {
                title.innerText = 'HALL EFFECT MAGNETIC RINGS';
                desc.innerText = 'Powerful permanent magnet rings that trap electrons in a spiral motion inside the chamber, drastically increasing ionization efficiency.';
                mat.innerText = 'SAMARIUM-COBALT (SmCo)';
                temp.innerText = '320 °C';
            }
        }

        function animate() {
            if (!canvas || !ctx) return;

            // Dark Cyber BG Clear
            ctx.fillStyle = 'rgba(2, 6, 19, 0.25)';
            ctx.fillRect(0, 0, canvas.width, canvas.height);

            const centerY = canvas.height / 2;
            const gridX = canvas.width * 0.45;

            if (visualMode === 'simulation') {
                // Render Engine Schematic Frame Outline
                ctx.strokeStyle = 'rgba(0, 240, 255, 0.4)';
                ctx.lineWidth = 2;

                // Main Chamber
                ctx.fillStyle = 'rgba(10, 22, 46, 0.4)';
                ctx.beginPath();
                ctx.roundRect(30, centerY - 100, gridX - 30, 200, 12);
                ctx.fill();
                ctx.stroke();

                // Gas Inlet Tube
                ctx.strokeStyle = 'rgba(0, 240, 255, 0.6)';
                ctx.beginPath();
                ctx.moveTo(10, centerY);
                ctx.lineTo(30, centerY);
                ctx.stroke();

                // High Voltage Grid Plates
                ctx.strokeStyle = '#ff6b00';
                ctx.lineWidth = 4;
                // Grid 1 (Positive Screen)
                ctx.beginPath();
                ctx.moveTo(gridX, centerY - 105);
                ctx.lineTo(gridX, centerY + 105);
                ctx.stroke();

                // Grid 2 (Negative Accelerator)
                ctx.strokeStyle = '#00f0ff';
                ctx.beginPath();
                ctx.moveTo(gridX + 15, centerY - 105);
                ctx.lineTo(gridX + 15, centerY + 105);
                ctx.stroke();

                // Neutralizer Cathode (Top Right)
                ctx.fillStyle = '#a855f7';
                ctx.beginPath();
                ctx.roundRect(gridX + 50, centerY - 120, 35, 20, 4);
                ctx.fill();

                // Neutralizer electron beam spraying down into exhaust
                ctx.strokeStyle = 'rgba(168, 85, 247, 0.6)';
                ctx.lineWidth = 2;
                ctx.beginPath();
                ctx.moveTo(gridX + 67, centerY - 100);
                ctx.lineTo(gridX + 80, centerY - 20);
                ctx.stroke();

                // Update & Render Particles
                particles.forEach(p => {
                    if (p.x < gridX) {
                        p.x += p.vx * (flowRate / 5);
                        p.y += p.vy + Math.sin(p.x * 0.05) * (0.5 / magneticField);

                        if (p.type === 'neutral' && Math.random() < (rfPower * 0.02)) {
                            p.type = 'ion';
                            p.charge = 1;
                        }
                    } else {
                        const gridSpeed = Math.sqrt(voltage) * 4;
                        p.x += gridSpeed * (p.type === 'ion' ? 1.5 : 0.8);
                        p.y += (Math.random() - 0.5) * 0.8;
                    }

                    if (p.x > canvas.width) {
                        p.x = 35;
                        p.y = centerY + (Math.random() - 0.5) * 160;
                        p.type = Math.random() < 0.7 ? 'ion' : 'neutral';
                    }

                    ctx.save();
                    ctx.beginPath();
                    if (p.type === 'ion') {
                        ctx.fillStyle = '#00f0ff';
                        ctx.shadowColor = '#00f0ff';
                        ctx.shadowBlur = 10;
                        ctx.arc(p.x, p.y, p.radius, 0, Math.PI * 2);
                        ctx.fill();
                    } else if (p.type === 'electron') {
                        ctx.fillStyle = '#ff6b00';
                        ctx.shadowColor = '#ff6b00';
                        ctx.shadowBlur = 8;
                        ctx.arc(p.x, p.y, p.radius, 0, Math.PI * 2);
                        ctx.fill();
                    } else {
                        ctx.fillStyle = '#64748b';
                        ctx.arc(p.x, p.y, p.radius, 0, Math.PI * 2);
                        ctx.fill();
                    }
                    ctx.restore();
                });

                // Exhaust Plume Glow Gradient
                const plumeGrad = ctx.createLinearGradient(gridX + 15, centerY, canvas.width, centerY);
                plumeGrad.addColorStop(0, 'rgba(0, 240, 255, 0.4)');
                plumeGrad.addColorStop(0.5, 'rgba(168, 85, 247, 0.2)');
                plumeGrad.addColorStop(1, 'rgba(0, 240, 255, 0)');
                ctx.fillStyle = plumeGrad;
                ctx.fillRect(gridX + 15, centerY - 90, canvas.width - gridX, 180);

            } else {
                ctx.strokeStyle = '#00f0ff';
                ctx.lineWidth = 1;
                ctx.fillStyle = 'rgba(0, 240, 255, 0.03)';

                for (let x = 0; x < canvas.width; x += 40) {
                    ctx.beginPath();
                    ctx.moveTo(x, 0);
                    ctx.lineTo(x, canvas.height);
                    ctx.strokeStyle = 'rgba(0, 240, 255, 0.08)';
                    ctx.stroke();
                }
                for (let y = 0; y < canvas.height; y += 40) {
                    ctx.beginPath();
                    ctx.moveTo(0, y);
                    ctx.lineTo(canvas.width, y);
                    ctx.strokeStyle = 'rgba(0, 240, 255, 0.08)';
                    ctx.stroke();
                }

                ctx.fillStyle = '#00f0ff';
                ctx.font = '12px Orbitron, sans-serif';
                ctx.fillText('NASA/JPL SPECIFICATIONS // CROSS-SECTION SCHEMATIC', 40, 40);

                ctx.strokeStyle = '#00f0ff';
                ctx.lineWidth = 1.5;

                ctx.strokeRect(60, centerY - 110, gridX - 60, 220);
                ctx.strokeRect(gridX, centerY - 120, 20, 240);
                ctx.strokeRect(gridX + 25, centerY - 120, 15, 240);

                ctx.beginPath();
                ctx.moveTo(120, centerY - 110);
                ctx.lineTo(160, centerY - 150);
                ctx.lineTo(260, centerY - 150);
                ctx.stroke();
                ctx.fillText('1. RF IONIZATION COIL', 265, centerY - 146);

                ctx.beginPath();
                ctx.moveTo(gridX + 10, centerY - 120);
                ctx.lineTo(gridX + 30, centerY - 160);
                ctx.lineTo(gridX + 120, centerY - 160);
                ctx.stroke();
                ctx.fillText('2. DUAL-STAGE ACCELERATOR GRIDS', gridX + 125, centerY - 156);
            }

            requestAnimationFrame(animate);
        }
    </script>
</body>
</html>
