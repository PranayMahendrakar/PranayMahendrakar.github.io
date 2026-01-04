
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pranay M. Mahendrakar | AI Visionary & Innovator</title>
    
    <!-- Premium Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;600;700;800;900&family=Rajdhani:wght@300;400;500;600;700&family=Exo+2:wght@100;200;300;400;500;600;700;800;900&family=Audiowide&family=Syncopate:wght@400;700&family=Black+Ops+One&display=swap" rel="stylesheet">
    
    <!-- Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
    
    <!-- Libraries -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/vanilla-tilt@1.8.1/dist/vanilla-tilt.min.js"></script>
    
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&display=swap');
        
        :root {
            /* Cyberpunk Color Palette */
            --neon-cyan: #00fff9;
            --neon-magenta: #ff00ff;
            --neon-yellow: #ffff00;
            --neon-orange: #ff6b00;
            --neon-blue: #00a8ff;
            --neon-purple: #9d00ff;
            --neon-pink: #ff0080;
            --neon-green: #00ff88;
            
            /* Dark Theme */
            --bg-dark: #000000;
            --bg-darker: #050505;
            --bg-card: rgba(10, 10, 20, 0.8);
            --bg-glass: rgba(255, 255, 255, 0.03);
            
            /* Text */
            --text-primary: #ffffff;
            --text-secondary: #b0b0b0;
            --text-muted: #707070;
            
            /* Gradients */
            --gradient-cyber: linear-gradient(135deg, #00fff9 0%, #ff00ff 50%, #ffff00 100%);
            --gradient-fire: linear-gradient(135deg, #ff6b00 0%, #ff0080 50%, #9d00ff 100%);
            --gradient-ocean: linear-gradient(135deg, #00a8ff 0%, #00fff9 50%, #00ff88 100%);
            --gradient-aurora: linear-gradient(135deg, #9d00ff 0%, #00fff9 25%, #ff00ff 50%, #00ff88 75%, #ffff00 100%);
            
            /* Typography */
            --font-display: 'Orbitron', sans-serif;
            --font-heading: 'Exo 2', sans-serif;
            --font-body: 'Rajdhani', sans-serif;
            --font-accent: 'Audiowide', cursive;
            --font-mono: 'Space Mono', monospace;
            
            /* Effects */
            --glow-cyan: 0 0 20px rgba(0, 255, 249, 0.5), 0 0 40px rgba(0, 255, 249, 0.3), 0 0 60px rgba(0, 255, 249, 0.1);
            --glow-magenta: 0 0 20px rgba(255, 0, 255, 0.5), 0 0 40px rgba(255, 0, 255, 0.3), 0 0 60px rgba(255, 0, 255, 0.1);
            --glow-orange: 0 0 20px rgba(255, 107, 0, 0.5), 0 0 40px rgba(255, 107, 0, 0.3), 0 0 60px rgba(255, 107, 0, 0.1);
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        html {
            scroll-behavior: smooth;
            font-size: 16px;
        }
        
        body {
            font-family: var(--font-body);
            background: var(--bg-dark);
            color: var(--text-primary);
            overflow-x: hidden;
            cursor: none;
        }
        
        /* Custom Cursor */
        .cursor {
            width: 20px;
            height: 20px;
            border: 2px solid var(--neon-cyan);
            border-radius: 50%;
            position: fixed;
            pointer-events: none;
            z-index: 99999;
            transition: transform 0.1s, border-color 0.3s;
            transform: translate(-50%, -50%);
        }
        
        .cursor-dot {
            width: 6px;
            height: 6px;
            background: var(--neon-magenta);
            border-radius: 50%;
            position: fixed;
            pointer-events: none;
            z-index: 99999;
            transform: translate(-50%, -50%);
        }
        
        .cursor.hover {
            transform: translate(-50%, -50%) scale(2);
            border-color: var(--neon-magenta);
            background: rgba(255, 0, 255, 0.1);
        }
        
        /* Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        
        ::-webkit-scrollbar-track {
            background: var(--bg-darker);
        }
        
        ::-webkit-scrollbar-thumb {
            background: var(--gradient-cyber);
            border-radius: 4px;
        }
        
        /* Selection */
        ::selection {
            background: var(--neon-magenta);
            color: var(--bg-dark);
        }
        
        /* Canvas Backgrounds */
        #bg-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -10;
        }
        
        /* Noise Overlay */
        .noise-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 9998;
            opacity: 0.03;
            background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)'/%3E%3C/svg%3E");
        }
        
        /* Grid Lines */
        .grid-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -5;
            background-image: 
                linear-gradient(rgba(0, 255, 249, 0.03) 1px, transparent 1px),
                linear-gradient(90deg, rgba(0, 255, 249, 0.03) 1px, transparent 1px);
            background-size: 100px 100px;
            perspective: 1000px;
            transform-style: preserve-3d;
        }
        
        /* Scanlines */
        .scanlines {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 9997;
            background: repeating-linear-gradient(
                0deg,
                rgba(0, 0, 0, 0.1) 0px,
                rgba(0, 0, 0, 0.1) 1px,
                transparent 1px,
                transparent 2px
            );
            opacity: 0.1;
        }
        
        /* Navigation */
        .navbar {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            z-index: 1000;
            padding: 1rem 2rem;
            background: rgba(0, 0, 0, 0.8);
            backdrop-filter: blur(20px);
            border-bottom: 1px solid rgba(0, 255, 249, 0.2);
        }
        
        .nav-container {
            max-width: 1600px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            font-family: var(--font-display);
            font-size: 1.5rem;
            font-weight: 900;
            text-decoration: none;
            background: var(--gradient-cyber);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            text-shadow: var(--glow-cyan);
            letter-spacing: 3px;
            position: relative;
        }
        
        .logo::before {
            content: 'PRANAY.AI';
            position: absolute;
            left: 2px;
            top: 2px;
            background: var(--gradient-fire);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            opacity: 0.5;
            z-index: -1;
        }
        
        .nav-links {
            display: flex;
            gap: 0.5rem;
            list-style: none;
        }
        
        .nav-link {
            font-family: var(--font-heading);
            font-size: 0.9rem;
            font-weight: 600;
            color: var(--text-secondary);
            text-decoration: none;
            padding: 0.75rem 1.25rem;
            border: 1px solid transparent;
            border-radius: 4px;
            transition: all 0.3s ease;
            position: relative;
            text-transform: uppercase;
            letter-spacing: 1px;
        }
        
        .nav-link::before {
            content: '';
            position: absolute;
            bottom: 0;
            left: 50%;
            width: 0;
            height: 2px;
            background: var(--gradient-cyber);
            transition: all 0.3s ease;
            transform: translateX(-50%);
        }
        
        .nav-link:hover {
            color: var(--neon-cyan);
            border-color: rgba(0, 255, 249, 0.3);
            background: rgba(0, 255, 249, 0.05);
            text-shadow: var(--glow-cyan);
        }
        
        .nav-link:hover::before {
            width: 80%;
        }
        
        .mobile-menu {
            display: none;
            background: none;
            border: 2px solid var(--neon-cyan);
            color: var(--neon-cyan);
            font-size: 1.5rem;
            padding: 0.5rem;
            cursor: pointer;
            border-radius: 4px;
        }
        
        /* Hero Section */
        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            position: relative;
            padding: 120px 2rem 2rem;
            overflow: hidden;
        }
        
        .hero-container {
            max-width: 1600px;
            margin: 0 auto;
            width: 100%;
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            align-items: center;
        }
        
        .hero-content {
            position: relative;
            z-index: 10;
        }
        
        .hero-badge {
            display: inline-flex;
            align-items: center;
            gap: 0.75rem;
            padding: 0.75rem 1.5rem;
            background: rgba(0, 255, 249, 0.1);
            border: 1px solid rgba(0, 255, 249, 0.3);
            border-radius: 50px;
            margin-bottom: 2rem;
            animation: pulse-glow 2s infinite;
        }
        
        @keyframes pulse-glow {
            0%, 100% { box-shadow: 0 0 20px rgba(0, 255, 249, 0.2); }
            50% { box-shadow: 0 0 40px rgba(0, 255, 249, 0.4); }
        }
        
        .hero-badge .dot {
            width: 10px;
            height: 10px;
            background: var(--neon-green);
            border-radius: 50%;
            animation: blink 1s infinite;
        }
        
        @keyframes blink {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.3; }
        }
        
        .hero-badge span {
            font-family: var(--font-mono);
            font-size: 0.85rem;
            color: var(--neon-cyan);
            text-transform: uppercase;
            letter-spacing: 2px;
        }
        
        .hero-title {
            font-family: var(--font-display);
            font-size: clamp(2.5rem, 6vw, 5rem);
            font-weight: 900;
            line-height: 1.1;
            margin-bottom: 1.5rem;
            text-transform: uppercase;
            letter-spacing: 2px;
        }
        
        .hero-title .line {
            display: block;
            overflow: hidden;
        }
        
        .hero-title .greeting {
            font-size: 0.5em;
            color: var(--text-secondary);
            font-weight: 400;
            letter-spacing: 8px;
            margin-bottom: 0.5rem;
        }
        
        .hero-title .name {
            background: var(--gradient-aurora);
            background-size: 300% 300%;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: gradient-shift 5s ease infinite;
            position: relative;
        }
        
        @keyframes gradient-shift {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }
        
        .hero-subtitle {
            font-family: var(--font-accent);
            font-size: clamp(1rem, 2vw, 1.5rem);
            margin-bottom: 2rem;
            display: flex;
            flex-wrap: wrap;
            gap: 1rem;
            align-items: center;
        }
        
        .hero-subtitle .tag {
            padding: 0.5rem 1rem;
            border: 1px solid;
            border-radius: 4px;
            font-size: 0.9rem;
            letter-spacing: 2px;
        }
        
        .hero-subtitle .tag:nth-child(1) {
            border-color: var(--neon-cyan);
            color: var(--neon-cyan);
            text-shadow: var(--glow-cyan);
        }
        
        .hero-subtitle .tag:nth-child(2) {
            border-color: var(--neon-magenta);
            color: var(--neon-magenta);
            text-shadow: var(--glow-magenta);
        }
        
        .hero-subtitle .tag:nth-child(3) {
            border-color: var(--neon-orange);
            color: var(--neon-orange);
            text-shadow: var(--glow-orange);
        }
        
        .hero-description {
            font-size: 1.1rem;
            color: var(--text-secondary);
            line-height: 1.8;
            margin-bottom: 2rem;
            max-width: 550px;
        }
        
        .hero-stats {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 1.5rem;
            margin-bottom: 2.5rem;
            padding: 1.5rem;
            background: var(--bg-glass);
            border: 1px solid rgba(0, 255, 249, 0.1);
            border-radius: 12px;
        }
        
        .hero-stat {
            text-align: center;
            position: relative;
        }
        
        .hero-stat::after {
            content: '';
            position: absolute;
            right: 0;
            top: 50%;
            transform: translateY(-50%);
            width: 1px;
            height: 60%;
            background: linear-gradient(180deg, transparent, rgba(0, 255, 249, 0.3), transparent);
        }
        
        .hero-stat:last-child::after {
            display: none;
        }
        
        .hero-stat-number {
            font-family: var(--font-display);
            font-size: 2rem;
            font-weight: 900;
            background: var(--gradient-cyber);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            display: block;
        }
        
        .hero-stat-label {
            font-family: var(--font-mono);
            font-size: 0.7rem;
            color: var(--text-muted);
            text-transform: uppercase;
            letter-spacing: 1px;
        }
        
        .hero-buttons {
            display: flex;
            gap: 1rem;
            flex-wrap: wrap;
        }
        
        .btn {
            font-family: var(--font-heading);
            font-size: 0.95rem;
            font-weight: 700;
            padding: 1rem 2rem;
            border-radius: 4px;
            text-decoration: none;
            text-transform: uppercase;
            letter-spacing: 2px;
            display: inline-flex;
            align-items: center;
            gap: 0.75rem;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
            cursor: none;
        }
        
        .btn-primary {
            background: var(--gradient-cyber);
            color: var(--bg-dark);
            border: none;
            box-shadow: var(--glow-cyan);
        }
        
        .btn-primary::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.3), transparent);
            transition: left 0.5s ease;
        }
        
        .btn-primary:hover::before {
            left: 100%;
        }
        
        .btn-primary:hover {
            transform: translateY(-3px) scale(1.02);
            box-shadow: 0 0 40px rgba(0, 255, 249, 0.6);
        }
        
        .btn-outline {
            background: transparent;
            color: var(--neon-magenta);
            border: 2px solid var(--neon-magenta);
        }
        
        .btn-outline:hover {
            background: var(--neon-magenta);
            color: var(--bg-dark);
            box-shadow: var(--glow-magenta);
            transform: translateY(-3px);
        }
        
        /* Hero Image */
        .hero-visual {
            position: relative;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        
        .hero-image-wrapper {
            position: relative;
            width: 450px;
            height: 450px;
        }
        
        /* Rotating Rings */
        .orbit-ring {
            position: absolute;
            border: 1px solid;
            border-radius: 50%;
            animation: orbit 20s linear infinite;
        }
        
        .orbit-ring-1 {
            width: 100%;
            height: 100%;
            border-color: rgba(0, 255, 249, 0.3);
            top: 0;
            left: 0;
        }
        
        .orbit-ring-2 {
            width: 120%;
            height: 120%;
            border-color: rgba(255, 0, 255, 0.2);
            top: -10%;
            left: -10%;
            animation-duration: 25s;
            animation-direction: reverse;
        }
        
        .orbit-ring-3 {
            width: 140%;
            height: 140%;
            border-color: rgba(255, 107, 0, 0.15);
            top: -20%;
            left: -20%;
            animation-duration: 30s;
        }
        
        @keyframes orbit {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }
        
        /* Floating Particles on Orbit */
        .orbit-particle {
            position: absolute;
            width: 12px;
            height: 12px;
            background: var(--neon-cyan);
            border-radius: 50%;
            box-shadow: var(--glow-cyan);
        }
        
        .orbit-particle-1 {
            top: 0;
            left: 50%;
            transform: translateX(-50%);
        }
        
        .orbit-particle-2 {
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            background: var(--neon-magenta);
            box-shadow: var(--glow-magenta);
        }
        
        /* Hexagon Frame */
        .hex-frame {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
        }
        
        .hex-frame svg {
            width: 100%;
            height: 100%;
            filter: drop-shadow(0 0 10px rgba(0, 255, 249, 0.5));
        }
        
        /* Profile Image */
        .hero-image-container {
            position: absolute;
            width: 80%;
            height: 80%;
            top: 10%;
            left: 10%;
            border-radius: 50%;
            overflow: hidden;
            border: 3px solid var(--neon-cyan);
            box-shadow: 
                0 0 30px rgba(0, 255, 249, 0.3),
                inset 0 0 30px rgba(0, 255, 249, 0.1);
        }
        
        .hero-image-container img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            filter: saturate(1.1) contrast(1.05);
        }
        
        /* Glitch Effect on Image */
        .hero-image-container::before,
        .hero-image-container::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: inherit;
            opacity: 0;
        }
        
        .hero-image-wrapper:hover .hero-image-container::before {
            animation: glitch-1 0.3s ease;
        }
        
        .hero-image-wrapper:hover .hero-image-container::after {
            animation: glitch-2 0.3s ease 0.1s;
        }
        
        @keyframes glitch-1 {
            0%, 100% { opacity: 0; transform: translate(0); }
            20% { opacity: 0.8; transform: translate(-5px, 5px); filter: hue-rotate(90deg); }
            40% { opacity: 0.8; transform: translate(5px, -5px); }
            60% { opacity: 0; }
        }
        
        @keyframes glitch-2 {
            0%, 100% { opacity: 0; transform: translate(0); }
            20% { opacity: 0.8; transform: translate(5px, -5px); filter: hue-rotate(-90deg); }
            40% { opacity: 0.8; transform: translate(-5px, 5px); }
            60% { opacity: 0; }
        }
        
        /* Floating Badges */
        .floating-badge {
            position: absolute;
            background: rgba(0, 0, 0, 0.9);
            backdrop-filter: blur(10px);
            border: 1px solid;
            border-radius: 8px;
            padding: 0.75rem 1rem;
            display: flex;
            align-items: center;
            gap: 0.5rem;
            font-family: var(--font-mono);
            font-size: 0.8rem;
            animation: float 4s ease-in-out infinite;
            z-index: 20;
        }
        
        .floating-badge i {
            font-size: 1rem;
        }
        
        .badge-1 {
            top: 5%;
            right: -10%;
            border-color: var(--neon-cyan);
            color: var(--neon-cyan);
            animation-delay: 0s;
        }
        
        .badge-2 {
            bottom: 25%;
            left: -15%;
            border-color: var(--neon-magenta);
            color: var(--neon-magenta);
            animation-delay: 1s;
        }
        
        .badge-3 {
            bottom: 5%;
            right: 5%;
            border-color: var(--neon-orange);
            color: var(--neon-orange);
            animation-delay: 2s;
        }
        
        .badge-4 {
            top: 25%;
            left: -20%;
            border-color: var(--neon-green);
            color: var(--neon-green);
            animation-delay: 1.5s;
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0) rotate(0deg); }
            50% { transform: translateY(-15px) rotate(2deg); }
        }
        
        /* Section Styles */
        .section {
            padding: 6rem 2rem;
            position: relative;
        }
        
        .section-container {
            max-width: 1600px;
            margin: 0 auto;
        }
        
        .section-header {
            text-align: center;
            margin-bottom: 4rem;
        }
        
        .section-tag {
            font-family: var(--font-mono);
            font-size: 0.9rem;
            color: var(--neon-cyan);
            text-transform: uppercase;
            letter-spacing: 4px;
            margin-bottom: 1rem;
            display: inline-block;
        }
        
        .section-title {
            font-family: var(--font-display);
            font-size: clamp(2rem, 5vw, 4rem);
            font-weight: 900;
            text-transform: uppercase;
            letter-spacing: 4px;
            background: var(--gradient-cyber);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            position: relative;
            display: inline-block;
        }
        
        .section-title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 3px;
            background: var(--gradient-cyber);
            border-radius: 2px;
        }
        
        .section-subtitle {
            font-size: 1.1rem;
            color: var(--text-secondary);
            margin-top: 1.5rem;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
        }
        
        /* About Section */
        .about {
            background: linear-gradient(180deg, var(--bg-dark) 0%, var(--bg-darker) 100%);
        }
        
        .about-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            align-items: center;
        }
        
        .about-content h3 {
            font-family: var(--font-heading);
            font-size: 2rem;
            font-weight: 700;
            margin-bottom: 1.5rem;
            color: var(--text-primary);
        }
        
        .about-content h3 span {
            color: var(--neon-cyan);
        }
        
        .about-content p {
            font-size: 1.05rem;
            color: var(--text-secondary);
            line-height: 1.9;
            margin-bottom: 1.5rem;
        }
        
        .about-highlights {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 1rem;
            margin-top: 2rem;
        }
        
        .highlight-item {
            display: flex;
            align-items: center;
            gap: 1rem;
            padding: 1rem;
            background: var(--bg-glass);
            border: 1px solid rgba(0, 255, 249, 0.1);
            border-radius: 8px;
            transition: all 0.3s ease;
        }
        
        .highlight-item:hover {
            border-color: var(--neon-cyan);
            background: rgba(0, 255, 249, 0.05);
            transform: translateX(10px);
        }
        
        .highlight-item i {
            font-size: 1.25rem;
            color: var(--neon-cyan);
            width: 24px;
        }
        
        .highlight-item span {
            font-family: var(--font-heading);
            font-weight: 600;
            color: var(--text-secondary);
        }
        
        /* Stats Cards */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 1.5rem;
        }
        
        .stat-card {
            background: var(--bg-card);
            border: 1px solid rgba(0, 255, 249, 0.1);
            border-radius: 16px;
            padding: 2rem;
            text-align: center;
            transition: all 0.4s ease;
            position: relative;
            overflow: hidden;
        }
        
        .stat-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 3px;
            background: var(--gradient-cyber);
            transform: scaleX(0);
            transition: transform 0.4s ease;
        }
        
        .stat-card:hover {
            border-color: var(--neon-cyan);
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(0, 255, 249, 0.1);
        }
        
        .stat-card:hover::before {
            transform: scaleX(1);
        }
        
        .stat-icon {
            width: 70px;
            height: 70px;
            margin: 0 auto 1.5rem;
            background: linear-gradient(135deg, rgba(0, 255, 249, 0.1), rgba(255, 0, 255, 0.1));
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.75rem;
            color: var(--neon-cyan);
        }
        
        .stat-number {
            font-family: var(--font-display);
            font-size: 3rem;
            font-weight: 900;
            background: var(--gradient-aurora);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        .stat-label {
            font-family: var(--font-mono);
            font-size: 0.85rem;
            color: var(--text-muted);
            text-transform: uppercase;
            letter-spacing: 2px;
            margin-top: 0.5rem;
        }
        
        /* Experience Section */
        .experience {
            background: var(--bg-darker);
        }
        
        .timeline {
            position: relative;
            max-width: 1000px;
            margin: 0 auto;
        }
        
        .timeline::before {
            content: '';
            position: absolute;
            left: 50%;
            top: 0;
            bottom: 0;
            width: 2px;
            background: linear-gradient(180deg, var(--neon-cyan), var(--neon-magenta), var(--neon-orange));
            transform: translateX(-50%);
        }
        
        .timeline-item {
            position: relative;
            margin-bottom: 3rem;
        }
        
        .timeline-item:nth-child(odd) .timeline-content {
            margin-right: calc(50% + 40px);
            text-align: right;
        }
        
        .timeline-item:nth-child(even) .timeline-content {
            margin-left: calc(50% + 40px);
        }
        
        .timeline-dot {
            position: absolute;
            left: 50%;
            top: 30px;
            transform: translateX(-50%);
            width: 20px;
            height: 20px;
            background: var(--neon-cyan);
            border-radius: 50%;
            border: 4px solid var(--bg-darker);
            box-shadow: var(--glow-cyan);
            z-index: 10;
        }
        
        .timeline-content {
            background: var(--bg-card);
            border: 1px solid rgba(0, 255, 249, 0.1);
            border-radius: 12px;
            padding: 1.5rem;
            transition: all 0.3s ease;
        }
        
        .timeline-content:hover {
            border-color: var(--neon-cyan);
            transform: scale(1.02);
            box-shadow: 0 10px 30px rgba(0, 255, 249, 0.1);
        }
        
        .timeline-date {
            display: inline-block;
            font-family: var(--font-mono);
            font-size: 0.8rem;
            padding: 0.4rem 1rem;
            background: var(--gradient-fire);
            color: var(--bg-dark);
            border-radius: 20px;
            margin-bottom: 1rem;
            font-weight: 700;
        }
        
        .timeline-title {
            font-family: var(--font-heading);
            font-size: 1.25rem;
            font-weight: 700;
            color: var(--text-primary);
            margin-bottom: 0.5rem;
        }
        
        .timeline-company {
            font-family: var(--font-accent);
            font-size: 0.95rem;
            color: var(--neon-cyan);
            margin-bottom: 0.75rem;
        }
        
        .timeline-description {
            font-size: 0.95rem;
            color: var(--text-secondary);
            line-height: 1.7;
        }
        
        /* Skills Section */
        .skills {
            background: var(--bg-dark);
        }
        
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
        }
        
        .skill-card {
            background: var(--bg-card);
            border: 1px solid rgba(0, 255, 249, 0.1);
            border-radius: 16px;
            padding: 2rem;
            transition: all 0.4s ease;
            position: relative;
            overflow: hidden;
        }
        
        .skill-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 4px;
            height: 100%;
            background: var(--gradient-cyber);
        }
        
        .skill-card:hover {
            border-color: var(--neon-cyan);
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(0, 255, 249, 0.1);
        }
        
        .skill-card-header {
            display: flex;
            align-items: center;
            gap: 1rem;
            margin-bottom: 1.5rem;
        }
        
        .skill-card-icon {
            width: 55px;
            height: 55px;
            background: linear-gradient(135deg, rgba(0, 255, 249, 0.15), rgba(255, 0, 255, 0.15));
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            color: var(--neon-cyan);
        }
        
        .skill-card h3 {
            font-family: var(--font-heading);
            font-size: 1.25rem;
            font-weight: 700;
            color: var(--text-primary);
        }
        
        .skill-list {
            list-style: none;
        }
        
        .skill-item {
            display: flex;
            align-items: center;
            gap: 1rem;
            padding: 0.75rem 0;
            color: var(--text-secondary);
            transition: all 0.3s ease;
            border-bottom: 1px solid rgba(255, 255, 255, 0.05);
        }
        
        .skill-item:last-child {
            border-bottom: none;
        }
        
        .skill-item:hover {
            color: var(--neon-cyan);
            transform: translateX(10px);
        }
        
        .skill-item i {
            color: var(--neon-magenta);
            font-size: 0.8rem;
        }
        
        /* Projects Section */
        .projects {
            background: var(--bg-darker);
        }
        
        .projects-filter {
            display: flex;
            justify-content: center;
            gap: 1rem;
            margin-bottom: 3rem;
            flex-wrap: wrap;
        }
        
        .filter-btn {
            font-family: var(--font-heading);
            font-size: 0.9rem;
            font-weight: 600;
            padding: 0.75rem 1.5rem;
            background: transparent;
            border: 1px solid rgba(0, 255, 249, 0.3);
            border-radius: 4px;
            color: var(--text-secondary);
            cursor: pointer;
            transition: all 0.3s ease;
            text-transform: uppercase;
            letter-spacing: 1px;
        }
        
        .filter-btn:hover,
        .filter-btn.active {
            background: var(--gradient-cyber);
            color: var(--bg-dark);
            border-color: transparent;
            box-shadow: var(--glow-cyan);
        }
        
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(380px, 1fr));
            gap: 2rem;
        }
        
        .project-card {
            background: var(--bg-card);
            border: 1px solid rgba(0, 255, 249, 0.1);
            border-radius: 16px;
            padding: 2rem;
            transition: all 0.4s ease;
            position: relative;
            overflow: hidden;
        }
        
        .project-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 3px;
            background: var(--gradient-cyber);
            transform: scaleX(0);
            transition: transform 0.4s ease;
        }
        
        .project-card:hover {
            border-color: var(--neon-cyan);
            transform: translateY(-10px);
            box-shadow: 0 25px 50px rgba(0, 255, 249, 0.15);
        }
        
        .project-card:hover::before {
            transform: scaleX(1);
        }
        
        .project-icon {
            width: 70px;
            height: 70px;
            background: linear-gradient(135deg, rgba(0, 255, 249, 0.15), rgba(255, 0, 255, 0.15));
            border-radius: 16px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.75rem;
            color: var(--neon-cyan);
            margin-bottom: 1.5rem;
        }
        
        .project-category {
            display: inline-block;
            font-family: var(--font-mono);
            font-size: 0.75rem;
            padding: 0.4rem 0.8rem;
            background: rgba(255, 0, 255, 0.15);
            color: var(--neon-magenta);
            border-radius: 4px;
            margin-bottom: 1rem;
            text-transform: uppercase;
            letter-spacing: 1px;
        }
        
        .project-title {
            font-family: var(--font-heading);
            font-size: 1.35rem;
            font-weight: 700;
            color: var(--text-primary);
            margin-bottom: 1rem;
        }
        
        .project-description {
            font-size: 0.95rem;
            color: var(--text-secondary);
            line-height: 1.7;
            margin-bottom: 1.5rem;
        }
        
        .project-stats {
            display: flex;
            gap: 1.5rem;
            margin-bottom: 1.5rem;
            padding: 1rem;
            background: rgba(0, 255, 249, 0.03);
            border-radius: 8px;
        }
        
        .project-stat {
            font-size: 0.85rem;
            color: var(--text-muted);
        }
        
        .project-stat strong {
            color: var(--neon-cyan);
            font-family: var(--font-display);
        }
        
        .project-tech {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
        }
        
        .tech-tag {
            font-family: var(--font-mono);
            font-size: 0.75rem;
            padding: 0.4rem 0.75rem;
            background: rgba(0, 255, 249, 0.1);
            color: var(--neon-cyan);
            border-radius: 4px;
        }
        
        /* Publications Section */
        .publications {
            background: var(--bg-dark);
        }
        
        .publications-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(380px, 1fr));
            gap: 2rem;
        }
        
        .publication-card {
            background: var(--bg-card);
            border: 1px solid rgba(0, 255, 249, 0.1);
            border-radius: 16px;
            padding: 2rem;
            transition: all 0.4s ease;
            position: relative;
            overflow: hidden;
        }
        
        .publication-card::before {
            content: '';
            position: absolute;
            left: 0;
            top: 0;
            width: 4px;
            height: 100%;
            background: var(--gradient-cyber);
        }
        
        .publication-card:hover {
            border-color: var(--neon-cyan);
            transform: translateX(10px);
            box-shadow: 0 20px 40px rgba(0, 255, 249, 0.1);
        }
        
        .publication-type {
            display: inline-block;
            font-family: var(--font-mono);
            font-size: 0.75rem;
            padding: 0.4rem 0.8rem;
            border-radius: 4px;
            margin-bottom: 1rem;
            text-transform: uppercase;
            letter-spacing: 1px;
        }
        
        .publication-type.book {
            background: rgba(0, 255, 249, 0.15);
            color: var(--neon-cyan);
        }
        
        .publication-type.paper {
            background: rgba(0, 255, 136, 0.15);
            color: var(--neon-green);
        }
        
        .publication-type.patent {
            background: rgba(255, 107, 0, 0.15);
            color: var(--neon-orange);
        }
        
        .publication-title {
            font-family: var(--font-heading);
            font-size: 1.2rem;
            font-weight: 700;
            color: var(--text-primary);
            margin-bottom: 1rem;
            line-height: 1.4;
        }
        
        .publication-info {
            font-family: var(--font-mono);
            font-size: 0.85rem;
            color: var(--text-muted);
            margin-bottom: 1rem;
        }
        
        .publication-link {
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            font-family: var(--font-heading);
            font-size: 0.9rem;
            color: var(--neon-cyan);
            text-decoration: none;
            font-weight: 600;
            transition: all 0.3s ease;
        }
        
        .publication-link:hover {
            color: var(--neon-magenta);
            transform: translateX(5px);
        }
        
        /* Certifications Section */
        .certifications {
            background: var(--bg-darker);
        }
        
        .cert-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 1.5rem;
        }
        
        .cert-card {
            background: var(--bg-card);
            border: 1px solid rgba(0, 255, 249, 0.1);
            border-radius: 16px;
            padding: 2rem;
            text-align: center;
            transition: all 0.4s ease;
            position: relative;
            overflow: hidden;
        }
        
        .cert-card:hover {
            border-color: var(--neon-cyan);
            transform: translateY(-10px) rotateY(5deg);
            box-shadow: 0 20px 40px rgba(0, 255, 249, 0.15);
        }
        
        .cert-icon {
            font-size: 2.5rem;
            margin-bottom: 1rem;
            background: var(--gradient-cyber);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        .cert-count {
            font-family: var(--font-display);
            font-size: 2.5rem;
            font-weight: 900;
            background: var(--gradient-aurora);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        .cert-name {
            font-family: var(--font-mono);
            font-size: 0.85rem;
            color: var(--text-muted);
            margin-top: 0.5rem;
        }
        
        /* Contact Section */
        .contact {
            background: var(--bg-dark);
        }
        
        .contact-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
        }
        
        .contact-info h3 {
            font-family: var(--font-display);
            font-size: 2rem;
            font-weight: 700;
            margin-bottom: 1.5rem;
            background: var(--gradient-cyber);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        .contact-info p {
            font-size: 1.1rem;
            color: var(--text-secondary);
            line-height: 1.8;
            margin-bottom: 2rem;
        }
        
        .contact-item {
            display: flex;
            align-items: center;
            gap: 1.5rem;
            padding: 1.25rem;
            background: var(--bg-card);
            border: 1px solid rgba(0, 255, 249, 0.1);
            border-radius: 12px;
            margin-bottom: 1rem;
            transition: all 0.3s ease;
        }
        
        .contact-item:hover {
            border-color: var(--neon-cyan);
            transform: translateX(10px);
            box-shadow: 0 10px 30px rgba(0, 255, 249, 0.1);
        }
        
        .contact-icon {
            width: 55px;
            height: 55px;
            background: linear-gradient(135deg, rgba(0, 255, 249, 0.15), rgba(255, 0, 255, 0.15));
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.25rem;
            color: var(--neon-cyan);
            flex-shrink: 0;
        }
        
        .contact-text strong {
            display: block;
            font-family: var(--font-heading);
            font-weight: 700;
            color: var(--text-primary);
            margin-bottom: 0.25rem;
        }
        
        .contact-text span {
            color: var(--text-secondary);
            font-size: 0.95rem;
        }
        
        .social-links {
            display: flex;
            gap: 1rem;
            margin-top: 2rem;
        }
        
        .social-link {
            width: 55px;
            height: 55px;
            background: var(--bg-card);
            border: 1px solid rgba(0, 255, 249, 0.2);
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.25rem;
            color: var(--text-secondary);
            text-decoration: none;
            transition: all 0.3s ease;
        }
        
        .social-link:hover {
            background: var(--gradient-cyber);
            color: var(--bg-dark);
            border-color: transparent;
            transform: translateY(-5px) rotate(5deg);
            box-shadow: var(--glow-cyan);
        }
        
        /* Contact Form */
        .contact-form {
            background: var(--bg-card);
            border: 1px solid rgba(0, 255, 249, 0.1);
            border-radius: 20px;
            padding: 2.5rem;
        }
        
        .form-group {
            margin-bottom: 1.5rem;
        }
        
        .form-label {
            display: block;
            font-family: var(--font-heading);
            font-weight: 600;
            color: var(--text-primary);
            margin-bottom: 0.5rem;
            font-size: 0.95rem;
        }
        
        .form-control {
            width: 100%;
            padding: 1rem 1.25rem;
            background: rgba(0, 255, 249, 0.03);
            border: 1px solid rgba(0, 255, 249, 0.1);
            border-radius: 8px;
            color: var(--text-primary);
            font-family: var(--font-body);
            font-size: 1rem;
            transition: all 0.3s ease;
        }
        
        .form-control:focus {
            outline: none;
            border-color: var(--neon-cyan);
            box-shadow: 0 0 20px rgba(0, 255, 249, 0.1);
            background: rgba(0, 255, 249, 0.05);
        }
        
        .form-control::placeholder {
            color: var(--text-muted);
        }
        
        textarea.form-control {
            min-height: 120px;
            resize: vertical;
        }
        
        /* Footer */
        .footer {
            background: var(--bg-darker);
            padding: 3rem 2rem;
            border-top: 1px solid rgba(0, 255, 249, 0.1);
        }
        
        .footer-container {
            max-width: 1600px;
            margin: 0 auto;
        }
        
        .footer-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 2rem;
        }
        
        .footer-logo {
            font-family: var(--font-display);
            font-size: 1.5rem;
            font-weight: 900;
            background: var(--gradient-cyber);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        .footer-links {
            display: flex;
            gap: 2rem;
            list-style: none;
        }
        
        .footer-link {
            font-family: var(--font-heading);
            color: var(--text-muted);
            text-decoration: none;
            transition: color 0.3s ease;
        }
        
        .footer-link:hover {
            color: var(--neon-cyan);
        }
        
        .footer-bottom {
            text-align: center;
            margin-top: 2rem;
            padding-top: 2rem;
            border-top: 1px solid rgba(0, 255, 249, 0.1);
        }
        
        .footer-bottom p {
            font-family: var(--font-mono);
            font-size: 0.9rem;
            color: var(--text-muted);
        }
        
        .footer-bottom span {
            color: var(--neon-cyan);
        }
        
        /* Responsive */
        @media (max-width: 1200px) {
            .hero-container {
                grid-template-columns: 1fr;
                text-align: center;
            }
            
            .hero-visual {
                order: -1;
            }
            
            .hero-image-wrapper {
                width: 350px;
                height: 350px;
            }
            
            .hero-stats {
                justify-content: center;
            }
            
            .hero-buttons {
                justify-content: center;
            }
            
            .hero-description {
                margin: 0 auto 2rem;
            }
            
            .about-grid,
            .contact-grid {
                grid-template-columns: 1fr;
            }
        }
        
        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }
            
            .mobile-menu {
                display: block;
            }
            
            .hero-image-wrapper {
                width: 280px;
                height: 280px;
            }
            
            .floating-badge {
                display: none;
            }
            
            .hero-stats {
                grid-template-columns: repeat(2, 1fr);
            }
            
            .timeline::before {
                left: 15px;
            }
            
            .timeline-item .timeline-content {
                margin-left: 50px !important;
                margin-right: 0 !important;
                text-align: left !important;
            }
            
            .timeline-dot {
                left: 15px;
            }
            
            .cursor, .cursor-dot {
                display: none;
            }
            
            body {
                cursor: auto;
            }
        }
        
        @media (max-width: 480px) {
            .section {
                padding: 4rem 1rem;
            }
            
            .hero-stats {
                grid-template-columns: 1fr;
            }
            
            .hero-buttons {
                flex-direction: column;
                width: 100%;
            }
            
            .btn {
                width: 100%;
                justify-content: center;
            }
            
            .projects-grid,
            .publications-grid,
            .skills-grid {
                grid-template-columns: 1fr;
            }
        }
        
        /* Loading Screen */
        .loading-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: var(--bg-dark);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            z-index: 100000;
            transition: opacity 0.5s ease, visibility 0.5s ease;
        }
        
        .loading-screen.hidden {
            opacity: 0;
            visibility: hidden;
        }
        
        .loader-text {
            font-family: var(--font-display);
            font-size: 2rem;
            background: var(--gradient-cyber);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 2rem;
            letter-spacing: 5px;
        }
        
        .loader-bar {
            width: 200px;
            height: 3px;
            background: rgba(0, 255, 249, 0.2);
            border-radius: 2px;
            overflow: hidden;
        }
        
        .loader-progress {
            width: 0%;
            height: 100%;
            background: var(--gradient-cyber);
            animation: loading 1.5s ease forwards;
        }
        
        @keyframes loading {
            0% { width: 0%; }
            100% { width: 100%; }
        }
    </style>
</head>
<body>
    <!-- Loading Screen -->
    <div class="loading-screen" id="loading">
        <div class="loader-text">PRANAY.AI</div>
        <div class="loader-bar">
            <div class="loader-progress"></div>
        </div>
    </div>
    
    <!-- Custom Cursor -->
    <div class="cursor" id="cursor"></div>
    <div class="cursor-dot" id="cursor-dot"></div>
    
    <!-- Background Canvas -->
    <canvas id="bg-canvas"></canvas>
    
    <!-- Overlays -->
    <div class="noise-overlay"></div>
    <div class="grid-overlay"></div>
    <div class="scanlines"></div>

    <!-- Navigation -->
    <nav class="navbar">
        <div class="nav-container">
            <a href="#home" class="logo">PRANAY.AI</a>
            <ul class="nav-links">
                <li><a href="#home" class="nav-link">Home</a></li>
                <li><a href="#about" class="nav-link">About</a></li>
                <li><a href="#experience" class="nav-link">Experience</a></li>
                <li><a href="#skills" class="nav-link">Skills</a></li>
                <li><a href="#projects" class="nav-link">Projects</a></li>
                <li><a href="#publications" class="nav-link">Publications</a></li>
                <li><a href="#contact" class="nav-link">Contact</a></li>
            </ul>
            <button class="mobile-menu" id="mobile-menu">
                <i class="fas fa-bars"></i>
            </button>
        </div>
    </nav>

    <!-- Hero Section -->
    <section id="home" class="hero">
        <div class="hero-container">
            <div class="hero-content">
                <div class="hero-badge">
                    <div class="dot"></div>
                    <span>Available for Opportunities</span>
                </div>
                
                <h1 class="hero-title">
                    <span class="line greeting">Hello, I'm</span>
                    <span class="line name">Pranay M. Mahendrakar</span>
                </h1>
                
                <div class="hero-subtitle">
                    <span class="tag">AI Specialist</span>
                    <span class="tag">Author</span>
                    <span class="tag">Patent Holder</span>
                </div>
                
                <p class="hero-description">
                    Transforming the future with Artificial Intelligence. Expert in LLMs, NLP, and Computer Vision. 
                    Delivered 150+ AI systems for Mercedes-Benz, Indian Army, IIT Bombay & more.
                </p>
                
                <div class="hero-stats">
                    <div class="hero-stat">
                        <span class="hero-stat-number">150+</span>
                        <span class="hero-stat-label">AI Systems</span>
                    </div>
                    <div class="hero-stat">
                        <span class="hero-stat-number">1,425+</span>
                        <span class="hero-stat-label">LeetCode</span>
                    </div>
                    <div class="hero-stat">
                        <span class="hero-stat-number">240+</span>
                        <span class="hero-stat-label">Certifications</span>
                    </div>
                    <div class="hero-stat">
                        <span class="hero-stat-number">7</span>
                        <span class="hero-stat-label">Research Papers</span>
                    </div>
                </div>
                
                <div class="hero-buttons">
                    <a href="#contact" class="btn btn-primary">
                        <i class="fas fa-rocket"></i> Get In Touch
                    </a>
                    <a href="#projects" class="btn btn-outline">
                        <i class="fas fa-folder-open"></i> View Projects
                    </a>
                </div>
            </div>
            
            <div class="hero-visual">
                <div class="hero-image-wrapper" data-tilt data-tilt-max="15" data-tilt-speed="400" data-tilt-glare data-tilt-max-glare="0.2">
                    <!-- Orbit Rings -->
                    <div class="orbit-ring orbit-ring-1">
                        <div class="orbit-particle orbit-particle-1"></div>
                        <div class="orbit-particle orbit-particle-2"></div>
                    </div>
                    <div class="orbit-ring orbit-ring-2"></div>
                    <div class="orbit-ring orbit-ring-3"></div>
                    
                    <!-- Profile Image -->
                    <div class="hero-image-container">
                        <img src="https://sonytech.in/pranay/boss.jpeg" alt="Pranay M. Mahendrakar" />
                    </div>
                    
                    <!-- Floating Badges -->
                    <div class="floating-badge badge-1">
                        <i class="fas fa-award"></i>
                        <span>UK Patent Holder</span>
                    </div>
                    <div class="floating-badge badge-2">
                        <i class="fas fa-book"></i>
                        <span>3 Books Published</span>
                    </div>
                    <div class="floating-badge badge-3">
                        <i class="fas fa-code"></i>
                        <span>Rank #7,222</span>
                    </div>
                    <div class="floating-badge badge-4">
                        <i class="fas fa-robot"></i>
                        <span>Hugging Face Dev</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section id="about" class="section about">
        <div class="section-container">
            <div class="section-header">
                <span class="section-tag">// About Me</span>
                <h2 class="section-title">The Innovator</h2>
            </div>
            
            <div class="about-grid">
                <div class="about-content">
                    <h3>Building the Future with <span>Artificial Intelligence</span></h3>
                    <p>
                        I'm an AI Specialist with proven expertise in Large Language Models (LLMs), Natural Language Processing, 
                        Computer Vision, and Full AI Product Development. My work spans across industries including automotive 
                        (Mercedes-Benz Germany), defence (Indian Army & Police), and education (IIT Bombay & IISc).
                    </p>
                    <p>
                        As a published author of 3 AI books, holder of a UK-registered patent in Blockchain technology, 
                        and creator of the Phoenix Programming Language, I constantly push the boundaries of what's possible. 
                        I'm also a Verified Hugging Face LLM Developer with 7 published research papers.
                    </p>
                    
                    <div class="about-highlights">
                        <div class="highlight-item">
                            <i class="fas fa-brain"></i>
                            <span>LLM & NLP Expert</span>
                        </div>
                        <div class="highlight-item">
                            <i class="fas fa-robot"></i>
                            <span>AI Automation</span>
                        </div>
                        <div class="highlight-item">
                            <i class="fas fa-eye"></i>
                            <span>Computer Vision</span>
                        </div>
                        <div class="highlight-item">
                            <i class="fas fa-code"></i>
                            <span>Full Stack Dev</span>
                        </div>
                        <div class="highlight-item">
                            <i class="fas fa-graduation-cap"></i>
                            <span>MCA (CGPA: 9.1)</span>
                        </div>
                        <div class="highlight-item">
                            <i class="fab fa-github"></i>
                            <span>27 Repositories</span>
                        </div>
                    </div>
                </div>
                
                <div class="stats-grid">
                    <div class="stat-card" data-tilt data-tilt-max="10">
                        <div class="stat-icon"><i class="fas fa-microchip"></i></div>
                        <div class="stat-number">150+</div>
                        <div class="stat-label">AI Systems Delivered</div>
                    </div>
                    <div class="stat-card" data-tilt data-tilt-max="10">
                        <div class="stat-icon"><i class="fas fa-book-open"></i></div>
                        <div class="stat-number">3</div>
                        <div class="stat-label">Published Books</div>
                    </div>
                    <div class="stat-card" data-tilt data-tilt-max="10">
                        <div class="stat-icon"><i class="fas fa-file-alt"></i></div>
                        <div class="stat-number">7</div>
                        <div class="stat-label">Research Papers</div>
                    </div>
                    <div class="stat-card" data-tilt data-tilt-max="10">
                        <div class="stat-icon"><i class="fas fa-certificate"></i></div>
                        <div class="stat-number">240+</div>
                        <div class="stat-label">Certifications</div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Experience Section -->
    <section id="experience" class="section experience">
        <div class="section-container">
            <div class="section-header">
                <span class="section-tag">// Career Path</span>
                <h2 class="section-title">Experience</h2>
            </div>
            
            <div class="timeline">
                <div class="timeline-item">
                    <div class="timeline-dot"></div>
                    <div class="timeline-content">
                        <div class="timeline-date">Jan 2025 - Present</div>
                        <h3 class="timeline-title">Instructor & Author</h3>
                        <div class="timeline-company">Tutorials Point | Edu-Tech</div>
                        <p class="timeline-description">Creating comprehensive AI/ML courses and tutorials. Authoring technical content for global audience on LLMs, NLP, and deep learning.</p>
                    </div>
                </div>
                <div class="timeline-item">
                    <div class="timeline-dot"></div>
                    <div class="timeline-content">
                        <div class="timeline-date">Nov 2024 - Present</div>
                        <h3 class="timeline-title">Nodal Coordinator</h3>
                        <div class="timeline-company">IIRS-ISRO</div>
                        <p class="timeline-description">Coordinating ISRO's Indian Institute of Remote Sensing initiatives. Facilitating space technology and geospatial AI research collaborations.</p>
                    </div>
                </div>
                <div class="timeline-item">
                    <div class="timeline-dot"></div>
                    <div class="timeline-content">
                        <div class="timeline-date">Mar 2020 - Present</div>
                        <h3 class="timeline-title">Managing Director</h3>
                        <div class="timeline-company">SonyTech | Edu Tech Development</div>
                        <p class="timeline-description">Overseeing all aspects of educational technology development. Driving growth and innovation in AI-powered educational solutions.</p>
                    </div>
                </div>
                <div class="timeline-item">
                    <div class="timeline-dot"></div>
                    <div class="timeline-content">
                        <div class="timeline-date">Mar 2021 - Aug 2024</div>
                        <h3 class="timeline-title">Technical Lead</h3>
                        <div class="timeline-company">SonyTech</div>
                        <p class="timeline-description">Led development of 20+ AI systems for Mercedes-Benz Germany, Indian Army, and premier institutions like IIT Bombay and IISc.</p>
                    </div>
                </div>
                <div class="timeline-item">
                    <div class="timeline-dot"></div>
                    <div class="timeline-content">
                        <div class="timeline-date">Oct 2023 - Mar 2024</div>
                        <h3 class="timeline-title">Software Developer Intern</h3>
                        <div class="timeline-company">VTU</div>
                        <p class="timeline-description">Developed software solutions and contributed to research projects. Implemented AI algorithms and enterprise development practices.</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Skills Section -->
    <section id="skills" class="section skills">
        <div class="section-container">
            <div class="section-header">
                <span class="section-tag">// Tech Stack</span>
                <h2 class="section-title">Skills & Expertise</h2>
            </div>
            
            <div class="skills-grid">
                <div class="skill-card" data-tilt data-tilt-max="8">
                    <div class="skill-card-header">
                        <div class="skill-card-icon"><i class="fas fa-brain"></i></div>
                        <h3>AI & Machine Learning</h3>
                    </div>
                    <ul class="skill-list">
                        <li class="skill-item"><i class="fas fa-chevron-right"></i> Large Language Models (LLMs)</li>
                        <li class="skill-item"><i class="fas fa-chevron-right"></i> Natural Language Processing</li>
                        <li class="skill-item"><i class="fas fa-chevron-right"></i> Computer Vision</li>
                        <li class="skill-item"><i class="fas fa-chevron-right"></i> TensorFlow & PyTorch</li>
                        <li class="skill-item"><i class="fas fa-chevron-right"></i> Hugging Face & LangChain</li>
                        <li class="skill-item"><i class="fas fa-chevron-right"></i> Fine-tuning & RAG Systems</li>
                    </ul>
                </div>
                
                <div class="skill-card" data-tilt data-tilt-max="8">
                    <div class="skill-card-header">
                        <div class="skill-card-icon"><i class="fas fa-code"></i></div>
                        <h3>Programming Languages</h3>
                    </div>
                    <ul class="skill-list">
                        <li class="skill-item"><i class="fab fa-python"></i> Python</li>
                        <li class="skill-item"><i class="fab fa-java"></i> Java</li>
                        <li class="skill-item"><i class="fas fa-code"></i> C Programming</li>
                        <li class="skill-item"><i class="fab fa-js"></i> JavaScript</li>
                        <li class="skill-item"><i class="fab fa-php"></i> PHP</li>
                        <li class="skill-item"><i class="fas fa-fire"></i> Phoenix (Creator)</li>
                    </ul>
                </div>
                
                <div class="skill-card" data-tilt data-tilt-max="8">
                    <div class="skill-card-header">
                        <div class="skill-card-icon"><i class="fas fa-cloud"></i></div>
                        <h3>Cloud & DevOps</h3>
                    </div>
                    <ul class="skill-list">
                        <li class="skill-item"><i class="fab fa-aws"></i> AWS Cloud</li>
                        <li class="skill-item"><i class="fab fa-google"></i> Google Cloud Platform</li>
                        <li class="skill-item"><i class="fab fa-microsoft"></i> Microsoft Azure</li>
                        <li class="skill-item"><i class="fab fa-docker"></i> Docker</li>
                        <li class="skill-item"><i class="fab fa-git-alt"></i> Git & Version Control</li>
                        <li class="skill-item"><i class="fab fa-linux"></i> Linux Administration</li>
                    </ul>
                </div>
                
                <div class="skill-card" data-tilt data-tilt-max="8">
                    <div class="skill-card-header">
                        <div class="skill-card-icon"><i class="fas fa-laptop-code"></i></div>
                        <h3>Development & Tools</h3>
                    </div>
                    <ul class="skill-list">
                        <li class="skill-item"><i class="fas fa-chevron-right"></i> Full Stack Development</li>
                        <li class="skill-item"><i class="fas fa-chevron-right"></i> REST API Design</li>
                        <li class="skill-item"><i class="fas fa-chevron-right"></i> Database Management</li>
                        <li class="skill-item"><i class="fas fa-chevron-right"></i> Ollama & Local LLMs</li>
                        <li class="skill-item"><i class="fas fa-chevron-right"></i> Game Development</li>
                        <li class="skill-item"><i class="fas fa-chevron-right"></i> Image Steganography</li>
                    </ul>
                </div>
            </div>
        </div>
    </section>

    <!-- Projects Section -->
    <section id="projects" class="section projects">
        <div class="section-container">
            <div class="section-header">
                <span class="section-tag">// Portfolio</span>
                <h2 class="section-title">Featured Projects</h2>
                <p class="section-subtitle">Innovative AI solutions delivered across industries worldwide</p>
            </div>
            
            <div class="projects-filter">
                <button class="filter-btn active" data-filter="all">All Projects</button>
                <button class="filter-btn" data-filter="enterprise">Enterprise AI</button>
                <button class="filter-btn" data-filter="tools">AI Tools</button>
                <button class="filter-btn" data-filter="research">Research</button>
            </div>
            
            <div class="projects-grid">
                <div class="project-card" data-category="enterprise" data-tilt data-tilt-max="5">
                    <div class="project-icon"><i class="fas fa-car"></i></div>
                    <span class="project-category">Enterprise AI</span>
                    <h3 class="project-title">AI Salesperson - Mercedes-Benz</h3>
                    <p class="project-description">Multilingual offline AI avatar for Mercedes-Benz Germany showrooms. Autonomous customer interactions and sales demonstrations.</p>
                    <div class="project-stats">
                        <div class="project-stat"><strong>+40%</strong> Sales Efficiency</div>
                        <div class="project-stat"><strong>Offline</strong> Capable</div>
                    </div>
                    <div class="project-tech">
                        <span class="tech-tag">LLM</span>
                        <span class="tech-tag">NLP</span>
                        <span class="tech-tag">Avatar AI</span>
                    </div>
                </div>
                
                <div class="project-card" data-category="enterprise" data-tilt data-tilt-max="5">
                    <div class="project-icon"><i class="fas fa-shield-alt"></i></div>
                    <span class="project-category">Enterprise AI</span>
                    <h3 class="project-title">Drone Threat Detection</h3>
                    <p class="project-description">Real-time computer vision system for Indian Army & Police. Detects and tracks aerial threats with high precision.</p>
                    <div class="project-stats">
                        <div class="project-stat"><strong>94%</strong> Precision</div>
                        <div class="project-stat"><strong>Real-time</strong> Processing</div>
                    </div>
                    <div class="project-tech">
                        <span class="tech-tag">Computer Vision</span>
                        <span class="tech-tag">YOLO</span>
                        <span class="tech-tag">Edge AI</span>
                    </div>
                </div>
                
                <div class="project-card" data-category="enterprise" data-tilt data-tilt-max="5">
                    <div class="project-icon"><i class="fas fa-university"></i></div>
                    <span class="project-category">Enterprise AI</span>
                    <h3 class="project-title">AI Research Platforms</h3>
                    <p class="project-description">Research automation platforms for IIT Bombay & IISc. Streamlines literature review and data analysis.</p>
                    <div class="project-stats">
                        <div class="project-stat"><strong>3,000+</strong> Users</div>
                        <div class="project-stat"><strong>60%</strong> Time Saved</div>
                    </div>
                    <div class="project-tech">
                        <span class="tech-tag">NLP</span>
                        <span class="tech-tag">RAG</span>
                        <span class="tech-tag">API</span>
                    </div>
                </div>
                
                <div class="project-card" data-category="tools" data-tilt data-tilt-max="5">
                    <div class="project-icon"><i class="fas fa-microphone"></i></div>
                    <span class="project-category">AI Tools</span>
                    <h3 class="project-title">Offline AI Voice Bot</h3>
                    <p class="project-description">Custom fine-tuned LLM with ultra-low latency. Runs entirely offline for privacy-critical applications.</p>
                    <div class="project-stats">
                        <div class="project-stat"><strong>&lt;300ms</strong> Latency</div>
                        <div class="project-stat"><strong>100%</strong> Offline</div>
                    </div>
                    <div class="project-tech">
                        <span class="tech-tag">Fine-tuned LLM</span>
                        <span class="tech-tag">Whisper</span>
                        <span class="tech-tag">Ollama</span>
                    </div>
                </div>
                
                <div class="project-card" data-category="tools" data-tilt data-tilt-max="5">
                    <div class="project-icon"><i class="fas fa-toolbox"></i></div>
                    <span class="project-category">AI Tools</span>
                    <h3 class="project-title">140+ Ollama AI Tools</h3>
                    <p class="project-description">Comprehensive toolkit for learning, programming, data science, and creative applications.</p>
                    <div class="project-stats">
                        <div class="project-stat"><strong>140+</strong> Tools</div>
                        <div class="project-stat"><strong>10</strong> Categories</div>
                    </div>
                    <div class="project-tech">
                        <span class="tech-tag">Ollama</span>
                        <span class="tech-tag">LangChain</span>
                        <span class="tech-tag">Open Source</span>
                    </div>
                </div>
                
                <div class="project-card" data-category="research" data-tilt data-tilt-max="5">
                    <div class="project-icon"><i class="fas fa-fire-alt"></i></div>
                    <span class="project-category">Research</span>
                    <h3 class="project-title">Phoenix Programming Language</h3>
                    <p class="project-description">Novel programming language with custom syntax and compiler design optimized for AI workloads.</p>
                    <div class="project-stats">
                        <div class="project-stat"><strong>2024</strong> Released</div>
                        <div class="project-stat"><strong>Custom</strong> Compiler</div>
                    </div>
                    <div class="project-tech">
                        <span class="tech-tag">Compiler Design</span>
                        <span class="tech-tag">LLVM</span>
                        <span class="tech-tag">C++</span>
                    </div>
                </div>
                
                <div class="project-card" data-category="research" data-tilt data-tilt-max="5">
                    <div class="project-icon"><i class="fas fa-robot"></i></div>
                    <span class="project-category">Research</span>
                    <h3 class="project-title">Pranay-llama</h3>
                    <p class="project-description">Fine-tuned custom LLM deployed on Ollama. Optimized for specific domain knowledge.</p>
                    <div class="project-stats">
                        <div class="project-stat"><strong>2025</strong> Deployed</div>
                        <div class="project-stat"><strong>Ollama</strong> Ready</div>
                    </div>
                    <div class="project-tech">
                        <span class="tech-tag">LLM Fine-tuning</span>
                        <span class="tech-tag">LoRA</span>
                        <span class="tech-tag">Hugging Face</span>
                    </div>
                </div>
                
                <div class="project-card" data-category="tools" data-tilt data-tilt-max="5">
                    <div class="project-icon"><i class="fas fa-lungs"></i></div>
                    <span class="project-category">AI Tools</span>
                    <h3 class="project-title">Lung Cancer Detection</h3>
                    <p class="project-description">CNN-based medical imaging model for early detection with explainable AI visualizations.</p>
                    <div class="project-stats">
                        <div class="project-stat"><strong>91%</strong> Accuracy</div>
                        <div class="project-stat"><strong>XAI</strong> Enabled</div>
                    </div>
                    <div class="project-tech">
                        <span class="tech-tag">CNN</span>
                        <span class="tech-tag">TensorFlow</span>
                        <span class="tech-tag">Medical AI</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Publications Section -->
    <section id="publications" class="section publications">
        <div class="section-container">
            <div class="section-header">
                <span class="section-tag">// Knowledge Sharing</span>
                <h2 class="section-title">Publications & Patents</h2>
            </div>
            
            <div class="publications-grid">
                <div class="publication-card">
                    <span class="publication-type book">Book</span>
                    <h3 class="publication-title">Just AI With Pranay</h3>
                    <p class="publication-info">ISBN: 978-93-6128-745-9</p>
                    <a href="#" class="publication-link">View Publication <i class="fas fa-arrow-right"></i></a>
                </div>
                
                <div class="publication-card">
                    <span class="publication-type book">Book</span>
                    <h3 class="publication-title">Multiverse of AI</h3>
                    <p class="publication-info">ISBN: 978-93-340-9670-5</p>
                    <a href="#" class="publication-link">View Publication <i class="fas fa-arrow-right"></i></a>
                </div>
                
                <div class="publication-card">
                    <span class="publication-type book">Book</span>
                    <h3 class="publication-title">It's Me LLM</h3>
                    <p class="publication-info">ISBN: 978-93-341-4930-2</p>
                    <a href="#" class="publication-link">View Publication <i class="fas fa-arrow-right"></i></a>
                </div>
                
                <div class="publication-card">
                    <span class="publication-type patent">Patent (UK)</span>
                    <h3 class="publication-title">Blockchain-Enabled Decentralized Cloud Computing</h3>
                    <p class="publication-info">UK Design #6380496 (Registered)</p>
                    <a href="#" class="publication-link">View Patent <i class="fas fa-arrow-right"></i></a>
                </div>
                
                <div class="publication-card">
                    <span class="publication-type patent">Patent (India)</span>
                    <h3 class="publication-title">Clone Profile Detection for Social Networks</h3>
                    <p class="publication-info">India (Pipeline)</p>
                    <a href="#" class="publication-link">View Details <i class="fas fa-arrow-right"></i></a>
                </div>
                
                <div class="publication-card">
                    <span class="publication-type paper">Research Paper</span>
                    <h3 class="publication-title">Sheaf-Theoretic Semantics in LLMs</h3>
                    <p class="publication-info">DOI: 10.5281/zenodo.18074071</p>
                    <a href="https://doi.org/10.5281/zenodo.18074071" class="publication-link" target="_blank">Read Paper <i class="fas fa-arrow-right"></i></a>
                </div>
                
                <div class="publication-card">
                    <span class="publication-type paper">Research Paper</span>
                    <h3 class="publication-title">Emotional Intelligence Paradox in LLMs</h3>
                    <p class="publication-info">DOI: 10.5281/zenodo.14040453</p>
                    <a href="https://doi.org/10.5281/zenodo.14040453" class="publication-link" target="_blank">Read Paper <i class="fas fa-arrow-right"></i></a>
                </div>
                
                <div class="publication-card">
                    <span class="publication-type paper">Research Paper</span>
                    <h3 class="publication-title">AI-Infused Drones for Security</h3>
                    <p class="publication-info">DOI: 10.5281/zenodo.14041518</p>
                    <a href="https://doi.org/10.5281/zenodo.14041518" class="publication-link" target="_blank">Read Paper <i class="fas fa-arrow-right"></i></a>
                </div>
                
                <div class="publication-card">
                    <span class="publication-type paper">Research Paper</span>
                    <h3 class="publication-title">Quantum Mirrors: AI vs. Consciousness</h3>
                    <p class="publication-info">DOI: 10.5281/zenodo.14047259</p>
                    <a href="https://doi.org/10.5281/zenodo.14047259" class="publication-link" target="_blank">Read Paper <i class="fas fa-arrow-right"></i></a>
                </div>
            </div>
        </div>
    </section>

    <!-- Certifications Section -->
    <section id="certifications" class="section certifications">
        <div class="section-container">
            <div class="section-header">
                <span class="section-tag">// Credentials</span>
                <h2 class="section-title">240+ Certifications</h2>
                <p class="section-subtitle">Continuous learning across leading platforms</p>
            </div>
            
            <div class="cert-grid">
                <div class="cert-card" data-tilt data-tilt-max="15">
                    <div class="cert-icon"><i class="fab fa-microsoft"></i></div>
                    <div class="cert-count">45+</div>
                    <div class="cert-name">Microsoft AI</div>
                </div>
                <div class="cert-card" data-tilt data-tilt-max="15">
                    <div class="cert-icon"><i class="fab fa-aws"></i></div>
                    <div class="cert-count">35+</div>
                    <div class="cert-name">AWS Cloud</div>
                </div>
                <div class="cert-card" data-tilt data-tilt-max="15">
                    <div class="cert-icon"><i class="fab fa-google"></i></div>
                    <div class="cert-count">25+</div>
                    <div class="cert-name">Google Cloud</div>
                </div>
                <div class="cert-card" data-tilt data-tilt-max="15">
                    <div class="cert-icon"><i class="fas fa-brain"></i></div>
                    <div class="cert-count">17+</div>
                    <div class="cert-name">Google AI</div>
                </div>
                <div class="cert-card" data-tilt data-tilt-max="15">
                    <div class="cert-icon"><i class="fas fa-microchip"></i></div>
                    <div class="cert-count">12+</div>
                    <div class="cert-name">NVIDIA GenAI</div>
                </div>
                <div class="cert-card" data-tilt data-tilt-max="15">
                    <div class="cert-icon"><i class="fas fa-satellite"></i></div>
                    <div class="cert-count">8+</div>
                    <div class="cert-name">ISRO</div>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="section contact">
        <div class="section-container">
            <div class="section-header">
                <span class="section-tag">// Let's Connect</span>
                <h2 class="section-title">Get In Touch</h2>
            </div>
            
            <div class="contact-grid">
                <div class="contact-info">
                    <h3>Ready to Collaborate?</h3>
                    <p>Whether you have a project in mind, want to explore AI solutions, or just want to connect - I'd love to hear from you!</p>
                    
                    <div class="contact-item">
                        <div class="contact-icon"><i class="fas fa-map-marker-alt"></i></div>
                        <div class="contact-text">
                            <strong>Location</strong>
                            <span>Bengaluru, Karnataka, India</span>
                        </div>
                    </div>
                    
                    <div class="contact-item">
                        <div class="contact-icon"><i class="fas fa-phone"></i></div>
                        <div class="contact-text">
                            <strong>Phone</strong>
                            <span>+91 6361723454</span>
                        </div>
                    </div>
                    
                    <div class="contact-item">
                        <div class="contact-icon"><i class="fas fa-envelope"></i></div>
                        <div class="contact-text">
                            <strong>Email</strong>
                            <span>pranaymahendrakar2001@gmail.com</span>
                        </div>
                    </div>
                    
                    <div class="social-links">
                        <a href="https://linkedin.com/in/pranay-mahendrakar-84bb3b197" class="social-link" target="_blank"><i class="fab fa-linkedin-in"></i></a>
                        <a href="https://github.com/PranayMahendrakar" class="social-link" target="_blank"><i class="fab fa-github"></i></a>
                        <a href="https://leetcode.com/PranayMahendrakar" class="social-link" target="_blank"><i class="fas fa-code"></i></a>
                        <a href="https://huggingface.co/" class="social-link" target="_blank"><i class="fas fa-robot"></i></a>
                        <a href="https://sonytech.in/pranay/" class="social-link" target="_blank"><i class="fas fa-globe"></i></a>
                    </div>
                </div>
                
                <div class="contact-form">
                    <form id="contact-form">
                        <div class="form-group">
                            <label class="form-label">Your Name</label>
                            <input type="text" class="form-control" placeholder="Enter your name" required>
                        </div>
                        <div class="form-group">
                            <label class="form-label">Email Address</label>
                            <input type="email" class="form-control" placeholder="Enter your email" required>
                        </div>
                        <div class="form-group">
                            <label class="form-label">Subject</label>
                            <input type="text" class="form-control" placeholder="What's this about?" required>
                        </div>
                        <div class="form-group">
                            <label class="form-label">Message</label>
                            <textarea class="form-control" placeholder="Tell me about your project..." required></textarea>
                        </div>
                        <button type="submit" class="btn btn-primary" style="width: 100%;">
                            <i class="fas fa-paper-plane"></i> Send Message
                        </button>
                    </form>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
        <div class="footer-container">
            <div class="footer-content">
                <div class="footer-logo">PRANAY.AI</div>
                <ul class="footer-links">
                    <li><a href="#home" class="footer-link">Home</a></li>
                    <li><a href="#about" class="footer-link">About</a></li>
                    <li><a href="#projects" class="footer-link">Projects</a></li>
                    <li><a href="#publications" class="footer-link">Publications</a></li>
                    <li><a href="#contact" class="footer-link">Contact</a></li>
                </ul>
            </div>
            <div class="footer-bottom">
                <p>&copy; 2025 <span>Pranay M. Mahendrakar</span>. All Rights Reserved. | AI Specialist • Author • Innovator</p>
            </div>
        </div>
    </footer>

    <script>
        // Loading Screen
        window.addEventListener('load', () => {
            setTimeout(() => {
                document.getElementById('loading').classList.add('hidden');
            }, 1800);
        });

        // Custom Cursor
        const cursor = document.getElementById('cursor');
        const cursorDot = document.getElementById('cursor-dot');

        document.addEventListener('mousemove', (e) => {
            cursor.style.left = e.clientX + 'px';
            cursor.style.top = e.clientY + 'px';
            cursorDot.style.left = e.clientX + 'px';
            cursorDot.style.top = e.clientY + 'px';
        });

        document.querySelectorAll('a, button, .project-card, .stat-card, .skill-card, .publication-card, .cert-card').forEach(el => {
            el.addEventListener('mouseenter', () => cursor.classList.add('hover'));
            el.addEventListener('mouseleave', () => cursor.classList.remove('hover'));
        });

        // Three.js Background
        const canvas = document.getElementById('bg-canvas');
        const renderer = new THREE.WebGLRenderer({ canvas, alpha: true, antialias: true });
        renderer.setSize(window.innerWidth, window.innerHeight);
        renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));

        const scene = new THREE.Scene();
        const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
        camera.position.z = 30;

        // Particles
        const particlesGeometry = new THREE.BufferGeometry();
        const particlesCount = 2000;
        const posArray = new Float32Array(particlesCount * 3);
        const colorsArray = new Float32Array(particlesCount * 3);

        const colors = [
            [0, 1, 0.98],    // Cyan
            [1, 0, 1],        // Magenta
            [1, 0.42, 0],     // Orange
            [0.62, 0, 1]      // Purple
        ];

        for (let i = 0; i < particlesCount * 3; i += 3) {
            posArray[i] = (Math.random() - 0.5) * 100;
            posArray[i + 1] = (Math.random() - 0.5) * 100;
            posArray[i + 2] = (Math.random() - 0.5) * 100;

            const color = colors[Math.floor(Math.random() * colors.length)];
            colorsArray[i] = color[0];
            colorsArray[i + 1] = color[1];
            colorsArray[i + 2] = color[2];
        }

        particlesGeometry.setAttribute('position', new THREE.BufferAttribute(posArray, 3));
        particlesGeometry.setAttribute('color', new THREE.BufferAttribute(colorsArray, 3));

        const particlesMaterial = new THREE.PointsMaterial({
            size: 0.15,
            vertexColors: true,
            transparent: true,
            opacity: 0.8,
            blending: THREE.AdditiveBlending
        });

        const particlesMesh = new THREE.Points(particlesGeometry, particlesMaterial);
        scene.add(particlesMesh);

        // Wireframe Shapes
        const shapes = [];
        const geometries = [
            new THREE.IcosahedronGeometry(3, 0),
            new THREE.OctahedronGeometry(3, 0),
            new THREE.TorusGeometry(2.5, 0.8, 8, 16)
        ];

        for (let i = 0; i < 6; i++) {
            const geo = geometries[i % geometries.length];
            const material = new THREE.MeshBasicMaterial({
                color: new THREE.Color().setHSL(Math.random(), 1, 0.5),
                wireframe: true,
                transparent: true,
                opacity: 0.15
            });
            const mesh = new THREE.Mesh(geo, material);
            mesh.position.set(
                (Math.random() - 0.5) * 60,
                (Math.random() - 0.5) * 60,
                (Math.random() - 0.5) * 40
            );
            mesh.rotation.set(Math.random() * Math.PI, Math.random() * Math.PI, 0);
            shapes.push(mesh);
            scene.add(mesh);
        }

        // Mouse movement
        let mouseX = 0, mouseY = 0;
        document.addEventListener('mousemove', (e) => {
            mouseX = (e.clientX / window.innerWidth) * 2 - 1;
            mouseY = -(e.clientY / window.innerHeight) * 2 + 1;
        });

        // Animation
        function animate() {
            requestAnimationFrame(animate);

            particlesMesh.rotation.x += 0.0003;
            particlesMesh.rotation.y += 0.0005;

            shapes.forEach((shape, i) => {
                shape.rotation.x += 0.002 * (i % 2 === 0 ? 1 : -1);
                shape.rotation.y += 0.003 * (i % 2 === 0 ? -1 : 1);
                shape.position.y += Math.sin(Date.now() * 0.001 + i) * 0.02;
            });

            camera.position.x += (mouseX * 3 - camera.position.x) * 0.02;
            camera.position.y += (mouseY * 3 - camera.position.y) * 0.02;
            camera.lookAt(scene.position);

            renderer.render(scene, camera);
        }
        animate();

        // Resize
        window.addEventListener('resize', () => {
            camera.aspect = window.innerWidth / window.innerHeight;
            camera.updateProjectionMatrix();
            renderer.setSize(window.innerWidth, window.innerHeight);
        });

        // Initialize Vanilla Tilt
        VanillaTilt.init(document.querySelectorAll("[data-tilt]"), {
            max: 15,
            speed: 400,
            glare: true,
            "max-glare": 0.15
        });

        // Smooth scroll
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({ behavior: 'smooth', block: 'start' });
                }
            });
        });

        // Project filter
        const filterBtns = document.querySelectorAll('.filter-btn');
        const projectCards = document.querySelectorAll('.project-card');

        filterBtns.forEach(btn => {
            btn.addEventListener('click', () => {
                const filter = btn.dataset.filter;
                filterBtns.forEach(b => b.classList.remove('active'));
                btn.classList.add('active');

                projectCards.forEach(card => {
                    if (filter === 'all' || card.dataset.category === filter) {
                        card.style.display = 'block';
                        card.style.animation = 'fadeIn 0.5s ease forwards';
                    } else {
                        card.style.display = 'none';
                    }
                });
            });
        });

        // Form submission
        document.getElementById('contact-form').addEventListener('submit', function(e) {
            e.preventDefault();
            alert('Thank you for your message! I will get back to you soon.');
            this.reset();
        });

        // Scroll animations with GSAP
        gsap.registerPlugin(ScrollTrigger);

        gsap.utils.toArray('.stat-card, .skill-card, .project-card, .publication-card, .cert-card, .timeline-content').forEach((el, i) => {
            gsap.from(el, {
                scrollTrigger: {
                    trigger: el,
                    start: 'top 85%',
                    toggleActions: 'play none none reverse'
                },
                y: 60,
                opacity: 0,
                duration: 0.8,
                delay: i * 0.05,
                ease: 'power3.out'
            });
        });

        // Navbar scroll effect
        window.addEventListener('scroll', () => {
            const navbar = document.querySelector('.navbar');
            if (window.scrollY > 50) {
                navbar.style.background = 'rgba(0, 0, 0, 0.95)';
                navbar.style.boxShadow = '0 0 30px rgba(0, 255, 249, 0.1)';
            } else {
                navbar.style.background = 'rgba(0, 0, 0, 0.8)';
                navbar.style.boxShadow = 'none';
            }
        });

        // Text animation on hero
        gsap.from('.hero-title .line', {
            y: 100,
            opacity: 0,
            duration: 1,
            stagger: 0.2,
            ease: 'power4.out',
            delay: 2
        });

        gsap.from('.hero-subtitle .tag', {
            y: 30,
            opacity: 0,
            duration: 0.8,
            stagger: 0.15,
            ease: 'power3.out',
            delay: 2.5
        });

        gsap.from('.hero-description, .hero-stats, .hero-buttons', {
            y: 30,
            opacity: 0,
            duration: 0.8,
            stagger: 0.2,
            ease: 'power3.out',
            delay: 3
        });

        gsap.from('.hero-image-wrapper', {
            scale: 0.8,
            opacity: 0,
            duration: 1.2,
            ease: 'power3.out',
            delay: 2.2
        });
    </script>
</body>
</html>
