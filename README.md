*🎆 Explosion Fireworks with Deep Bass Sound 🔊*

An immersive Three.js fireworks experience featuring high-density particle explosions, cinematic bloom, and procedural deep bass explosion sound designed with the Web Audio API. The show starts on click and runs with configurable physics, visuals, and audio controls via a sleek GUI panel.

​
✨ Features

    🎇 High-performance particle fireworks:

        20k+ particles per explosion.

        Mono / dual / tri-color bursts with varied brightness and depth.

    🌌 Cinematic visuals:

        UnrealBloom post-processing for glowing explosions.

        Starfield background and subtle motion trails.

        Fog-based atmospheric depth for a space-like feel.

    ​

🔊 Procedural deep explosion sound:

    Sub-bass boom, filtered noise rumble, and sharp crack transient.

    Dynamics compressor/limiter for clean and controlled output.

    ​

🎛 Interactive controls (lil-gui):

    Tweak particle count, size, gravity, explosion force, and fade speed.

    Toggle auto-launch, explosion sound, and master volume.

        ​

    🖱 Click-to-start overlay:

        Complies with browser audio policies (user-gesture audio unlock).

        Clear UX: “CLICK TO START” to launch the show.

🧱 Tech Stack

    🧩 Three.js (ES modules via import map)

​

🎥 Post-processing: EffectComposer, RenderPass, UnrealBloomPass

🧪 UI: lil-gui for real-time parameter control

​

🎶 Audio: Web Audio API (oscillators, noise buffer, filters, compressor)

🌐 Core: HTML + CSS + JavaScript (no bundler required)
🚀 Getting Started
1️⃣ Clone or download

bash
git clone <https://github.com/NikDev345/cracker-animation>

2️⃣ Run a local server

Because this uses ES modules + import maps, serve over HTTP:

bash
# Python 3
python -m http.server 8000

# or Node.js
npx serve .

Then open in your browser:

text
http://localhost:8000

Use the latest Chrome, Edge, or Firefox for best results (modern ES module & import map support).

​
🧠 How It Works
🎇 Fireworks System

    Each firework is a Firework class instance with:

        🚀 Rocket phase: a bright point rises with slight horizontal noise until it slows or reaches its target height.

        💥 Explosion phase: tens of thousands of particles spawn at the rocket’s position.

    For every particle:

        A random direction on a sphere is generated (using theta and phi).

        Speed is derived from explosionForce with some variation.

        Color is selected from 1–3 generated HSL hues (mono/dual/tri) with random brightness.

    Gravity, friction, and fade speed define how particles float, fall, and vanish.

    When all particle lifetimes reach zero, geometry/materials are cleaned up to avoid memory leaks.

    ​

🔊 Audio Engine

    Audio is initialized only after the first click on the overlay to satisfy autoplay restrictions.

    The deep explosion sound is fully procedural:

        Low sine sub-bass sweep (50 Hz ➝ ~20 Hz).

        Low-pass filtered noise layer for rumble/air.

        Short triangle “crack” for the transient impact.

    A dynamics compressor acts as a limiter to prevent clipping and keep the sound punchy and safe.

    ​

🌌 Post-Processing & Trails

    An EffectComposer renders the scene with an UnrealBloomPass for glowing highlights.

    ​

    A large transparent black plane in front of the camera creates a simple motion trail effect by slightly darkening previous frames each render.

🎚 Controls

The GUI in the bottom-right corner lets you tune the show in real time:
Particles 🌟

    particleCount – Number of particles per explosion.

    particleSize – Visual size of each sprite.

    fadeSpeed – How quickly particles fade out.

Physics 🧪

    explosionForce – Initial launch speed of particles.

    hoverDuration – Time before gravity fully pulls them down.

    gravity – Downward acceleration.

Deep Audio 🔊

    soundEnabled – Toggle explosion sound on/off.

    volume – Master volume for the audio engine.

Launch 🎇

    autoLaunch – Automatically trigger fireworks over time.

    launchInterval – Base delay between automatic launches (ms).

🎮 Usage

    Open the project in a supported browser.

    Click on “CLICK TO START”:

        Overlay disappears.

        Audio context is initialized.

        First firework launches instantly.

    Enjoy the show and tweak the GUI sliders to experiment:

        Crank up particleCount & bloomStrength for insane visuals.

        Lower gravity for dreamy, floaty fireworks.

        Boost volume for a chest-rattling bass explosion (use good headphones!).

        ​

🌍 Browser Support

    ✔ Modern Chrome / Edge / Firefox (ES modules + import maps + Web Audio).

    ​

    ❌ Very old browsers or IE are not supported.

If you later move to a bundler (Vite, Webpack, etc.), you can drop the import map and use local module imports instead.
🧩 Future Ideas

    Add orbiting camera or cinematic camera paths.

    Create shaped fireworks (rings, hearts, text, logos).

    Add preset buttons (e.g., “Cinematic”, “Chill”, “Festival”, “Insane”).

    Add screenshot / video capture integration.

    Mobile performance mode with adaptive particle counts.

📜 License

    This project is licensed under the MIT License – feel free to use, modify, and share with attribution.
