<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PulseAI — Next-Gen SaaS Platform</title>
    <!-- Google Fonts for Modern Typography -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&display=swap" rel="stylesheet">
    
    <style>
        /* ==========================================
           1. CSS CUSTOM PROPERTIES & CONSTANTS
           ========================================== */
        :root {
            --clr-primary: #6366f1;
            --clr-primary-hover: #4f46e5;
            --clr-primary-light: #e0e7ff;
            --clr-accent: #06b6d4;
            --clr-dark: #0f172a;
            --clr-muted: #475569;
            --clr-light-bg: #f8fafc;
            --clr-white: #ffffff;
            --clr-border: #e2e8f0;
            
            --font-main: 'Plus Jakarta Sans', -apple-system, BlinkMacSystemFont, sans-serif;
            
            --shadow-sm: 0 1px 2px 0 rgba(0, 0, 0, 0.05);
            --shadow-md: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
            --shadow-lg: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
            --shadow-glow: 0 0 50px rgba(99, 102, 241, 0.25);
            
            --radius-sm: 8px;
            --radius-md: 12px;
            --radius-lg: 20px;
            --radius-full: 9999px;
            
            --transition-fast: 0.2s ease;
            --transition-normal: 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }

        /* ==========================================
           2. BASE & RESET STYLES
           ========================================== */
        *, *::before, *::after {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            font-family: var(--font-main);
            background-color: var(--clr-light-bg);
            color: var(--clr-dark);
            line-height: 1.6;
            overflow-x: hidden;
            display: flex;
            flex-direction: column;
            min-height: 100vh;
        }

        a {
            text-decoration: none;
            color: inherit;
        }

        button {
            cursor: pointer;
            border: none;
            outline: none;
            font-family: inherit;
        }

        /* Container helper */
        .container {
            width: 100%;
            max-width: 1240px;
            margin: 0 auto;
            padding: 0 1.5rem;
        }

        /* ==========================================
           3. STICKY HEADER & NAVIGATION
           ========================================== */
        .header {
            position: sticky;
            top: 0;
            z-index: 1000;
            background-color: rgba(255, 255, 255, 0.85);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border-bottom: 1px solid rgba(226, 232, 240, 0.8);
            transition: var(--transition-normal);
        }

        .navbar {
            display: flex;
            align-items: center;
            justify-content: space-between;
            height: 80px;
        }

        /* Brand Logo */
        .logo {
            display: flex;
            align-items: center;
            gap: 10px;
            font-weight: 800;
            font-size: 1.4rem;
            color: var(--clr-dark);
            letter-spacing: -0.5px;
        }

        .logo-icon {
            width: 38px;
            height: 38px;
            background: linear-gradient(135deg, var(--clr-primary), var(--clr-accent));
            border-radius: var(--radius-sm);
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--clr-white);
            box-shadow: 0 4px 12px rgba(99, 102, 241, 0.3);
        }

        /* Navigation Links */
        .nav-menu {
            display: flex;
            align-items: center;
            gap: 2.2rem;
            list-style: none;
        }

        .nav-link {
            font-size: 0.95rem;
            font-weight: 600;
            color: var(--clr-muted);
            transition: var(--transition-fast);
            position: relative;
            padding: 0.5rem 0;
        }

        .nav-link:hover {
            color: var(--clr-primary);
        }

        .nav-link::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0%;
            height: 2px;
            background-color: var(--clr-primary);
            border-radius: 2px;
            transition: var(--transition-fast);
        }

        .nav-link:hover::after {
            width: 100%;
        }

        /* CTA Buttons */
        .btn {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            padding: 0.75rem 1.6rem;
            font-size: 0.95rem;
            font-weight: 600;
            border-radius: var(--radius-full);
            transition: var(--transition-normal);
            text-align: center;
        }

        .btn-primary {
            background-color: var(--clr-primary);
            color: var(--clr-white);
            box-shadow: 0 4px 14px rgba(99, 102, 241, 0.35);
        }

        .btn-primary:hover {
            background-color: var(--clr-primary-hover);
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(99, 102, 241, 0.45);
        }

        .btn-secondary {
            background-color: var(--clr-white);
            color: var(--clr-dark);
            border: 1px solid var(--clr-border);
            box-shadow: var(--shadow-sm);
        }

        .btn-secondary:hover {
            background-color: var(--clr-light-bg);
            border-color: #cbd5e1;
            transform: translateY(-2px);
        }

        .btn-lg {
            padding: 0.95rem 2rem;
            font-size: 1rem;
        }

        /* Hamburger Toggle Button */
        .mobile-toggle {
            display: none;
            background: none;
            font-size: 1.5rem;
            color: var(--clr-dark);
            padding: 0.5rem;
        }

        /* ==========================================
           4. HERO SECTION (FLEXBOX LAYOUT)
           ========================================== */
        .hero-section {
            padding: 5rem 0 6rem;
            position: relative;
            background: radial-gradient(circle at 80% 20%, rgba(99, 102, 241, 0.08) 0%, transparent 40%),
                        radial-gradient(circle at 20% 80%, rgba(6, 182, 212, 0.08) 0%, transparent 40%);
        }

        .hero-container {
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 4rem;
        }

        /* Hero Text Content Left Column */
        .hero-content {
            flex: 1;
            max-width: 580px;
        }

        .badge {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            padding: 0.35rem 1rem;
            background-color: var(--clr-primary-light);
            color: var(--clr-primary);
            border-radius: var(--radius-full);
            font-size: 0.85rem;
            font-weight: 700;
            margin-bottom: 1.5rem;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .badge-dot {
            width: 8px;
            height: 8px;
            background-color: var(--clr-primary);
            border-radius: 50%;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0% { transform: scale(0.95); box-shadow: 0 0 0 0 rgba(99, 102, 241, 0.7); }
            70% { transform: scale(1); box-shadow: 0 0 0 8px rgba(99, 102, 241, 0); }
            100% { transform: scale(0.95); box-shadow: 0 0 0 0 rgba(99, 102, 241, 0); }
        }

        .hero-title {
            font-size: 3.5rem;
            line-height: 1.15;
            font-weight: 800;
            letter-spacing: -1.5px;
            color: var(--clr-dark);
            margin-bottom: 1.25rem;
        }

        .hero-title span {
            background: linear-gradient(135deg, var(--clr-primary) 0%, var(--clr-accent) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .hero-description {
            font-size: 1.15rem;
            color: var(--clr-muted);
            margin-bottom: 2.25rem;
            line-height: 1.7;
        }

        .hero-actions {
            display: flex;
            align-items: center;
            gap: 1rem;
            flex-wrap: wrap;
        }

        .hero-meta {
            margin-top: 2rem;
            display: flex;
            align-items: center;
            gap: 1.5rem;
            font-size: 0.875rem;
            color: var(--clr-muted);
        }

        .hero-meta-item {
            display: flex;
            align-items: center;
            gap: 6px;
        }

        .hero-meta-item svg {
            color: var(--clr-primary);
        }

        /* Hero Graphic Right Column */
        .hero-image-wrapper {
            flex: 1;
            position: relative;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        /* Styled Interactive SaaS Graphics Representation */
        .hero-graphic {
            width: 100%;
            max-width: 520px;
            height: auto;
            border-radius: var(--radius-lg);
            background: var(--clr-white);
            box-shadow: var(--shadow-lg), var(--shadow-glow);
            border: 1px solid rgba(226, 232, 240, 0.9);
            padding: 1rem;
            position: relative;
            transition: var(--transition-normal);
        }

        .hero-graphic:hover {
            transform: translateY(-5px);
        }

        /* ==========================================
           5. FOOTER & STICKY BOTTOM BAR
           ========================================== */
        .footer {
            margin-top: auto;
            background-color: var(--clr-dark);
            color: var(--clr-white);
            padding: 2.5rem 0;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
        }

        .footer-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 1.5rem;
        }

        .footer-logo {
            font-weight: 700;
            font-size: 1.2rem;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .footer-links {
            display: flex;
            gap: 1.5rem;
            list-style: none;
            font-size: 0.9rem;
            color: #94a3b8;
        }

        .footer-links a:hover {
            color: var(--clr-white);
        }

        .copyright {
            color: #64748b;
            font-size: 0.875rem;
            width: 100%;
            text-align: center;
            margin-top: 1.5rem;
            padding-top: 1.5rem;
            border-top: 1px solid rgba(255, 255, 255, 0.05);
        }

        /* ==========================================
           6. RESPONSIVE DESIGN & MEDIA QUERIES
           ========================================== */
        @media (max-width: 992px) {
            .hero-title {
                font-size: 2.75rem;
            }
            .hero-container {
                gap: 2.5rem;
            }
        }

        @media (max-width: 768px) {
            /* Navbar Mobile View */
            .mobile-toggle {
                display: block;
            }

            .nav-menu {
                position: absolute;
                top: 80px;
                left: 0;
                width: 100%;
                background-color: var(--clr-white);
                flex-direction: column;
                align-items: stretch;
                padding: 1.5rem 2rem;
                gap: 1.25rem;
                box-shadow: var(--shadow-lg);
                border-bottom: 1px solid var(--clr-border);
                display: none; /* Toggled by JS */
            }

            .nav-menu.active {
                display: flex;
            }

            .header-cta {
                display: none; /* Hide header CTA on mobile, moved to nav drawer */
            }

            /* Stack Hero Section vertically */
            .hero-container {
                flex-direction: column;
                text-align: center;
                gap: 3.5rem;
            }

            .hero-content {
                max-width: 100%;
            }

            .hero-actions {
                justify-content: center;
            }

            .hero-meta {
                justify-content: center;
            }

            .hero-image-wrapper {
                width: 100%;
            }

            .footer-content {
                flex-direction: column;
                text-align: center;
            }
        }

        @media (max-width: 480px) {
            .hero-title {
                font-size: 2.2rem;
            }
            .hero-actions {
                flex-direction: column;
                width: 100%;
            }
            .btn {
                width: 100%;
            }
        }
    </style>
</head>
<body>

    <!-- ==========================================
       HEADER & NAVIGATION SECTION
       ========================================== -->
    <header class="header">
        <div class="container">
            <nav class="navbar">
                <!-- Brand Logo -->
                <a href="#" class="logo">
                    <div class="logo-icon">
                        <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
                            <polyline points="22 12 18 12 15 21 9 3 6 12 2 12"></polyline>
                        </svg>
                    </div>
                    <span>PulseAI</span>
                </a>

                <!-- Desktop Navigation Items -->
                <ul class="nav-menu" id="navMenu">
                    <li><a href="#features" class="nav-link">Features</a></li>
                    <li><a href="#solutions" class="nav-link">Solutions</a></li>
                    <li><a href="#pricing" class="nav-link">Pricing</a></li>
                    <li><a href="#about" class="nav-link">About</a></li>
                </ul>

                <!-- Primary Call To Action Button -->
                <div class="header-cta">
                    <a href="#signup" class="btn btn-primary">Get Started</a>
                </div>

                <!-- Mobile Hamburger Toggle -->
                <button class="mobile-toggle" id="mobileToggle" aria-label="Toggle Navigation Menu">
                    <svg width="24" height="24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                        <line x1="3" y1="12" x2="21" y2="12"></line>
                        <line x1="3" y1="6" x2="21" y2="6"></line>
                        <line x1="3" y1="18" x2="21" y2="18"></line>
                    </svg>
                </button>
            </nav>
        </div>
    </header>

    <!-- ==========================================
       HERO SECTION (Flexbox Container)
       ========================================== -->
    <main>
        <section class="hero-section">
            <div class="container hero-container">
                
                <!-- Left Column: Hero Text Content -->
                <div class="hero-content">
                    <div class="badge">
                        <span class="badge-dot"></span>
                        Next-Gen Intelligence 2.0
                    </div>

                    <h1 class="hero-title">
                        Automate your workflow with <span>smart AI</span>.
                    </h1>

                    <p class="hero-description">
                        Empower your team with cutting-edge automated insights, real-time analytics, and seamless tool integrations. Built for scale, security, and velocity.
                    </p>

                    <!-- Hero Call-To-Action Buttons -->
                    <div class="hero-actions">
                        <a href="#trial" class="btn btn-primary btn-lg">
                            Start Free Trial
                            <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="5" y1="12" x2="19" y2="12"></line><polyline points="12 5 19 12 12 19"></polyline></svg>
                        </a>
                        <a href="#demo" class="btn btn-secondary btn-lg">
                            <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M8 5v14l11-7z"/></svg>
                            Watch Demo
                        </a>
                    </div>

                    <!-- Trust indicators -->
                    <div class="hero-meta">
                        <div class="hero-meta-item">
                            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"><polyline points="20 6 9 17 4 12"></polyline></svg>
                            <span>No credit card required</span>
                        </div>
                        <div class="hero-meta-item">
                            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"><polyline points="20 6 9 17 4 12"></polyline></svg>
                            <span>14-day free trial</span>
                        </div>
                    </div>
                </div>

                <!-- Right Column: Interactive Vector SVG SaaS Graphic -->
                <div class="hero-image-wrapper">
                    <div class="hero-graphic">
                        <svg viewBox="0 0 500 360" width="100%" height="100%" xmlns="http://www.w3.org/2000/svg" style="background:#ffffff; border-radius:12px;">
                            <!-- Mock Application Window Header -->
                            <rect width="500" height="35" rx="8" fill="#f1f5f9"/>
                            <circle cx="20" cy="18" r="5" fill="#ef4444"/>
                            <circle cx="36" cy="18" r="5" fill="#eab308"/>
                            <circle cx="52" cy="18" r="5" fill="#22c55e"/>
                            <rect x="180" y="10" width="140" height="15" rx="4" fill="#e2e8f0"/>

                            <!-- Sidebar Graphics -->
                            <rect x="15" y="50" width="100" height="295" rx="6" fill="#f8fafc"/>
                            <rect x="25" y="65" width="80" height="10" rx="3" fill="#cbd5e1"/>
                            <rect x="25" y="90" width="65" height="8" rx="3" fill="#6366f1" opacity="0.8"/>
                            <rect x="25" y="110" width="70" height="8" rx="3" fill="#cbd5e1"/>
                            <rect x="25" y="130" width="55" height="8" rx="3" fill="#cbd5e1"/>

                            <!-- Main Dashboard Content Cards -->
                            <rect x="130" y="50" width="170" height="90" rx="8" fill="#EEF2FF"/>
                            <rect x="145" y="65" width="80" height="10" rx="3" fill="#6366f1"/>
                            <text x="145" y="110" font-family="sans-serif" font-weight="bold" font-size="20" fill="#1e1b4b">+148%</text>

                            <rect x="315" y="50" width="170" height="90" rx="8" fill="#ECFEFF"/>
                            <rect x="330" y="65" width="80" height="10" rx="3" fill="#06b6d4"/>
                            <text x="330" y="110" font-family="sans-serif" font-weight="bold" font-size="20" fill="#164e63">99.9%</text>

                            <!-- Analytic Chart Simulation -->
                            <rect x="130" y="155" width="355" height="185" rx="8" fill="#ffffff" stroke="#f1f5f9" stroke-width="2"/>
                            
                            <!-- Grid Lines -->
                            <line x1="150" y1="180" x2="465" y2="180" stroke="#f1f5f9" stroke-width="1"/>
                            <line x1="150" y1="220" x2="465" y2="220" stroke="#f1f5f9" stroke-width="1"/>
                            <line x1="150" y1="260" x2="465" y2="260" stroke="#f1f5f9" stroke-width="1"/>
                            <line x1="150" y1="300" x2="465" y2="300" stroke="#f1f5f9" stroke-width="1"/>

                            <!-- Chart Wave Path -->
                            <path d="M 150 280 Q 210 210, 270 240 T 390 190 T 465 210 L 465 310 L 150 310 Z" fill="url(#gradientChart)" opacity="0.3"/>
                            <path d="M 150 280 Q 210 210, 270 240 T 390 190 T 465 210" fill="none" stroke="#6366f1" stroke-width="3.5" stroke-linecap="round"/>

                            <!-- Active Data Points -->
                            <circle cx="390" cy="190" r="5" fill="#6366f1" stroke="#ffffff" stroke-width="2"/>

                            <!-- Gradients Definition -->
                            <defs>
                                <linearGradient id="gradientChart" x1="0%" y1="0%" x2="0%" y2="100%">
                                    <stop offset="0%" stop-color="#6366f1" />
                                    <stop offset="100%" stop-color="#ffffff" stop-opacity="0"/>
                                </linearGradient>
                            </defs>
                        </svg>
                    </div>
                </div>

            </div>
        </section>
    </main>

    <!-- ==========================================
       FOOTER / STICKY BOTTOM SECTION
       ========================================== -->
    <footer class="footer">
        <div class="container">
            <div class="footer-content">
                <div class="footer-logo">
                    <div class="logo-icon" style="width:28px; height:28px;">
                        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"></polyline></svg>
                    </div>
                    <span>PulseAI</span>
                </div>

                <ul class="footer-links">
                    <li><a href="#privacy">Privacy Policy</a></li>
                    <li><a href="#terms">Terms of Service</a></li>
                    <li><a href="#security">Security</a></li>
                    <li><a href="#contact">Contact Us</a></li>
                </ul>
            </div>
            
            <div class="copyright">
                &copy; 2026 PulseAI Technologies Inc. All rights reserved. Assignment 7.4 Completed.
            </div>
        </div>
    </footer>

    <!-- ==========================================
       7. JAVASCRIPT FOR MOBILE NAV TOGGLE
       ========================================== -->
    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const mobileToggle = document.getElementById('mobileToggle');
            const navMenu = document.getElementById('navMenu');

            // Mobile menu drawer toggle logic
            mobileToggle.addEventListener('click', () => {
                navMenu.classList.toggle('active');
            });

            // Close mobile menu when clicking outside
            document.addEventListener('click', (event) => {
                if (!mobileToggle.contains(event.target) && !navMenu.contains(event.target)) {
                    navMenu.classList.remove('active');
                }
            });
        });
    </script>
</body>
</html>