<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jatin Joshi - Portfolio</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #0a0e27 0%, #1a1a2e 50%, #16213e 100%);
            color: #e0e0e0;
            overflow-x: hidden;
        }

        .cursor-dot {
            width: 8px;
            height: 8px;
            background: #00d4ff;
            border-radius: 50%;
            position: fixed;
            pointer-events: none;
            z-index: 10000;
            transition: transform 0.15s ease;
        }

        .cursor-outline {
            width: 30px;
            height: 30px;
            border: 2px solid rgba(0, 212, 255, 0.4);
            border-radius: 50%;
            position: fixed;
            pointer-events: none;
            z-index: 9999;
            transition: all 0.15s ease;
        }

        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
        }

        .particles {
            position: absolute;
            width: 100%;
            height: 100%;
            overflow: hidden;
        }

        .particle {
            position: absolute;
            background: rgba(0, 212, 255, 0.5);
            border-radius: 50%;
            animation: float 20s infinite;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0) translateX(0); opacity: 0; }
            10% { opacity: 0.5; }
            90% { opacity: 0.5; }
            100% { transform: translateY(-100vh) translateX(50px); opacity: 0; }
        }

        .hero-content {
            text-align: center;
            z-index: 2;
            padding: 2rem;
        }

        .glitch {
            font-size: 4rem;
            font-weight: 900;
            text-transform: uppercase;
            position: relative;
            text-shadow: 0.05em 0 0 #00fffc, -0.03em -0.04em 0 #fc00ff,
                         0.025em 0.04em 0 #fffc00;
            animation: glitch 725ms infinite;
        }

        @keyframes glitch {
            0% {
                text-shadow: 0.05em 0 0 #00fffc, -0.03em -0.04em 0 #fc00ff,
                             0.025em 0.04em 0 #fffc00;
            }
            15% {
                text-shadow: 0.05em 0 0 #00fffc, -0.03em -0.04em 0 #fc00ff,
                             0.025em 0.04em 0 #fffc00;
            }
            16% {
                text-shadow: -0.05em -0.025em 0 #00fffc, 0.025em 0.035em 0 #fc00ff,
                             -0.05em -0.05em 0 #fffc00;
            }
            49% {
                text-shadow: -0.05em -0.025em 0 #00fffc, 0.025em 0.035em 0 #fc00ff,
                             -0.05em -0.05em 0 #fffc00;
            }
            50% {
                text-shadow: 0.05em 0.035em 0 #00fffc, 0.03em 0 0 #fc00ff,
                             0 -0.04em 0 #fffc00;
            }
            99% {
                text-shadow: 0.05em 0.035em 0 #00fffc, 0.03em 0 0 #fc00ff,
                             0 -0.04em 0 #fffc00;
            }
            100% {
                text-shadow: -0.05em 0 0 #00fffc, -0.025em -0.04em 0 #fc00ff,
                             -0.04em -0.025em 0 #fffc00;
            }
        }

        .subtitle {
            font-size: 1.5rem;
            margin: 1rem 0;
            color: #00d4ff;
            opacity: 0;
            animation: fadeInUp 1s ease forwards 0.5s;
        }

        @keyframes fadeInUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
            from {
                opacity: 0;
                transform: translateY(20px);
            }
        }

        .cta-buttons {
            margin-top: 2rem;
            display: flex;
            gap: 1rem;
            justify-content: center;
            flex-wrap: wrap;
        }

        .btn {
            padding: 1rem 2rem;
            border: none;
            border-radius: 50px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
            text-decoration: none;
            display: inline-block;
        }

        .btn-primary {
            background: linear-gradient(135deg, #00d4ff 0%, #0099ff 100%);
            color: #0a0e27;
        }

        .btn-secondary {
            background: transparent;
            border: 2px solid #00d4ff;
            color: #00d4ff;
        }

        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 30px rgba(0, 212, 255, 0.4);
        }

        .btn::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 0;
            height: 0;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.3);
            transform: translate(-50%, -50%);
            transition: width 0.6s, height 0.6s;
        }

        .btn:hover::before {
            width: 300px;
            height: 300px;
        }

        .section {
            padding: 5rem 2rem;
            max-width: 1400px;
            margin: 0 auto;
        }

        .section-title {
            font-size: 2.5rem;
            text-align: center;
            margin-bottom: 3rem;
            position: relative;
            color: #00d4ff;
        }

        .section-title::after {
            content: '';
            display: block;
            width: 100px;
            height: 4px;
            background: linear-gradient(90deg, transparent, #00d4ff, transparent);
            margin: 1rem auto;
        }

        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }

        .skill-card {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 20px;
            padding: 2rem;
            border: 1px solid rgba(0, 212, 255, 0.2);
            transition: all 0.3s ease;
            backdrop-filter: blur(10px);
            cursor: pointer;
        }

        .skill-card:hover {
            transform: translateY(-10px);
            border-color: #00d4ff;
            box-shadow: 0 20px 40px rgba(0, 212, 255, 0.2);
            background: rgba(255, 255, 255, 0.08);
        }

        .skill-icon {
            font-size: 3rem;
            margin-bottom: 1rem;
            display: block;
        }

        .skill-name {
            font-size: 1.3rem;
            font-weight: 600;
            margin-bottom: 0.5rem;
            color: #fff;
        }

        .skill-items {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
            margin-top: 1rem;
        }

        .skill-tag {
            background: rgba(0, 212, 255, 0.2);
            padding: 0.3rem 0.8rem;
            border-radius: 20px;
            font-size: 0.85rem;
            border: 1px solid rgba(0, 212, 255, 0.3);
        }

        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }

        .project-card {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 20px;
            overflow: hidden;
            border: 1px solid rgba(0, 212, 255, 0.2);
            transition: all 0.3s ease;
            position: relative;
        }

        .project-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(0, 212, 255, 0.1), transparent);
            transition: left 0.5s ease;
        }

        .project-card:hover::before {
            left: 100%;
        }

        .project-card:hover {
            transform: translateY(-10px);
            border-color: #00d4ff;
            box-shadow: 0 20px 50px rgba(0, 212, 255, 0.3);
        }

        .project-image {
            width: 100%;
            height: 200px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 4rem;
            position: relative;
            overflow: hidden;
        }

        .project-card:nth-child(2) .project-image {
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
        }

        .project-card:nth-child(3) .project-image {
            background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
        }

        .project-card:nth-child(4) .project-image {
            background: linear-gradient(135deg, #43e97b 0%, #38f9d7 100%);
        }

        .project-card:nth-child(5) .project-image {
            background: linear-gradient(135deg, #fa709a 0%, #fee140 100%);
        }

        .project-card:nth-child(6) .project-image {
            background: linear-gradient(135deg, #30cfd0 0%, #330867 100%);
        }

        .project-content {
            padding: 1.5rem;
        }

        .project-title {
            font-size: 1.4rem;
            font-weight: 700;
            margin-bottom: 0.5rem;
            color: #fff;
        }

        .project-desc {
            color: #b0b0b0;
            margin-bottom: 1rem;
            line-height: 1.6;
        }

        .project-tech {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
            margin-bottom: 1rem;
        }

        .tech-tag {
            background: rgba(0, 212, 255, 0.15);
            padding: 0.3rem 0.7rem;
            border-radius: 15px;
            font-size: 0.8rem;
            color: #00d4ff;
        }

        .project-links {
            display: flex;
            gap: 1rem;
        }

        .project-link {
            color: #00d4ff;
            text-decoration: none;
            font-weight: 600;
            transition: all 0.3s ease;
        }

        .project-link:hover {
            color: #fff;
            transform: translateX(5px);
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 2rem;
            margin: 3rem 0;
        }

        .stat-card {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 20px;
            padding: 2rem;
            text-align: center;
            border: 1px solid rgba(0, 212, 255, 0.2);
            transition: all 0.3s ease;
        }

        .stat-card:hover {
            transform: scale(1.05);
            border-color: #00d4ff;
        }

        .stat-number {
            font-size: 3rem;
            font-weight: 900;
            color: #00d4ff;
            display: block;
        }

        .stat-label {
            font-size: 1rem;
            color: #b0b0b0;
            margin-top: 0.5rem;
        }

        .timeline {
            position: relative;
            max-width: 800px;
            margin: 3rem auto;
        }

        .timeline::before {
            content: '';
            position: absolute;
            left: 50%;
            transform: translateX(-50%);
            width: 2px;
            height: 100%;
            background: linear-gradient(180deg, transparent, #00d4ff, transparent);
        }

        .timeline-item {
            margin-bottom: 3rem;
            position: relative;
        }

        .timeline-item:nth-child(odd) {
            padding-right: calc(50% + 2rem);
        }

        .timeline-item:nth-child(even) {
            padding-left: calc(50% + 2rem);
        }

        .timeline-content {
            background: rgba(255, 255, 255, 0.05);
            padding: 1.5rem;
            border-radius: 15px;
            border: 1px solid rgba(0, 212, 255, 0.2);
            position: relative;
        }

        .timeline-year {
            font-size: 1.5rem;
            font-weight: 700;
            color: #00d4ff;
            margin-bottom: 0.5rem;
        }

        .timeline-dot {
            width: 20px;
            height: 20px;
            background: #00d4ff;
            border-radius: 50%;
            position: absolute;
            left: 50%;
            top: 0;
            transform: translateX(-50%);
            box-shadow: 0 0 20px rgba(0, 212, 255, 0.8);
        }

        .contact-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1.5rem;
            margin-top: 2rem;
        }

        .contact-card {
            background: rgba(255, 255, 255, 0.05);
            padding: 2rem;
            border-radius: 20px;
            text-align: center;
            border: 1px solid rgba(0, 212, 255, 0.2);
            transition: all 0.3s ease;
            cursor: pointer;
            text-decoration: none;
            color: inherit;
            display: block;
        }

        .contact-card:hover {
            transform: translateY(-5px);
            border-color: #00d4ff;
            box-shadow: 0 15px 30px rgba(0, 212, 255, 0.3);
        }

        .contact-icon {
            font-size: 3rem;
            margin-bottom: 1rem;
            color: #00d4ff;
        }

        .scroll-indicator {
            position: fixed;
            bottom: 2rem;
            left: 50%;
            transform: translateX(-50%);
            font-size: 2rem;
            color: #00d4ff;
            animation: bounce 2s infinite;
            z-index: 10;
        }

        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% {
                transform: translateX(-50%) translateY(0);
            }
            40% {
                transform: translateX(-50%) translateY(-20px);
            }
            60% {
                transform: translateX(-50%) translateY(-10px);
            }
        }

        .wave {
            display: inline-block;
            animation: wave-animation 2.5s infinite;
            transform-origin: 70% 70%;
        }

        @keyframes wave-animation {
            0% { transform: rotate(0deg); }
            10% { transform: rotate(14deg); }
            20% { transform: rotate(-8deg); }
            30% { transform: rotate(14deg); }
            40% { transform: rotate(-4deg); }
            50% { transform: rotate(10deg); }
            60% { transform: rotate(0deg); }
            100% { transform: rotate(0deg); }
        }

        @media (max-width: 768px) {
            .glitch {
                font-size: 2.5rem;
            }

            .subtitle {
                font-size: 1.2rem;
            }

            .section {
                padding: 3rem 1rem;
            }

            .section-title {
                font-size: 2rem;
            }

            .timeline::before {
                left: 0;
            }

            .timeline-item:nth-child(odd),
            .timeline-item:nth-child(even) {
                padding-left: 2rem;
                padding-right: 0;
            }

            .timeline-dot {
                left: 0;
                transform: translateX(-50%);
            }

            .projects-grid {
                grid-template-columns: 1fr;
            }
        }

        .footer {
            text-align: center;
            padding: 2rem;
            background: rgba(0, 0, 0, 0.3);
            margin-top: 3rem;
        }

        .footer-text {
            color: #b0b0b0;
        }

        .footer-heart {
            color: #ff006e;
            display: inline-block;
            animation: heartbeat 1.5s infinite;
        }

        @keyframes heartbeat {
            0%, 100% { transform: scale(1); }
            10%, 30% { transform: scale(1.1); }
            20%, 40% { transform: scale(1.05); }
        }
    </style>
</head>
<body>
    <div class="cursor-dot"></div>
    <div class="cursor-outline"></div>

    <section class="hero">
        <div class="particles" id="particles"></div>
        <div class="hero-content">
            <h1 class="glitch">JATIN JOSHI</h1>
            <p class="subtitle">Full-Stack Developer | Tech Innovator | Problem Solver <span class="wave">👋</span></p>
            <p style="color: #b0b0b0; margin: 1rem 0;">Transforming ideas into digital reality through innovation 🚀</p>
            <div class="cta-buttons">
                <a href="#projects" class="btn btn-primary">View Projects</a>
                <a href="#contact" class="btn btn-secondary">Get In Touch</a>
            </div>
        </div>
        <div class="scroll-indicator">↓</div>
    </section>

    <section class="section">
        <div class="stats-grid">
            <div class="stat-card">
                <span class="stat-number" data-target="50">0</span>
                <span class="stat-label">Projects Completed</span>
            </div>
            <div class="stat-card">
                <span class="stat-number" data-target="1000">0</span>
                <span class="stat-label">GitHub Stars</span>
            </div>
            <div class="stat-card">
                <span class="stat-number" data-target="15">0</span>
                <span class="stat-label">Technologies Mastered</span>
            </div>
            <div class="stat-card">
                <span class="stat-number" data-target="98">0</span>
                <span class="stat-label">Client Satisfaction %</span>
            </div>
        </div>
    </section>

    <section class="section" id="skills">
        <h2 class="section-title">⚡ Tech Stack & Skills</h2>
        <div class="skills-grid">
            <div class="skill-card">
                <span class="skill-icon">💻</span>
                <h3 class="skill-name">Frontend Development</h3>
                <div class="skill-items">
                    <span class="skill-tag">React</span>
                    <span class="skill-tag">Next.js</span>
                    <span class="skill-tag">Angular</span>
                    <span class="skill-tag">Vue</span>
                    <span class="skill-tag">Tailwind</span>
                </div>
            </div>
            <div class="skill-card">
                <span class="skill-icon">⚙️</span>
                <h3 class="skill-name">Backend Development</h3>
                <div class="skill-items">
                    <span class="skill-tag">Node.js</span>
                    <span class="skill-tag">Django</span>
                    <span class="skill-tag">Spring Boot</span>
                    <span class="skill-tag">FastAPI</span>
                </div>
            </div>
            <div class="skill-card">
                <span class="skill-icon">📱</span>
                <h3 class="skill-name">Mobile Development</h3>
                <div class="skill-items">
                    <span class="skill-tag">Flutter</span>
                    <span class="skill-tag">React Native</span>
                    <span class="skill-tag">Kotlin</span>
                </div>
            </div>
            <div class="skill-card">
                <span class="skill-icon">🗄️</span>
                <h3 class="skill-name">Databases</h3>
                <div class="skill-items">
                    <span class="skill-tag">MongoDB</span>
                    <span class="skill-tag">PostgreSQL</span>
                    <span class="skill-tag">MySQL</span>
                    <span class="skill-tag">Redis</span>
                </div>
            </div>
            <div class="skill-card">
                <span class="skill-icon">☁️</span>
                <h3 class="skill-name">Cloud & DevOps</h3>
                <div class="skill-items">
                    <span class="skill-tag">AWS</span>
                    <span class="skill-tag">Docker</span>
                    <span class="skill-tag">Kubernetes</span>
                    <span class="skill-tag">CI/CD</span>
                </div>
            </div>
            <div class="skill-card">
                <span class="skill-icon">🤖</span>
                <h3 class="skill-name">AI/ML & Data</h3>
                <div class="skill-items">
                    <span class="skill-tag">Python</span>
                    <span class="skill-tag">TensorFlow</span>
                    <span class="skill-tag">PyTorch</span>
                    <span class="skill-tag">Scikit-learn</span>
                </div>
            </div>
        </div>
    </section>

    <section class="section" id="projects">
        <h2 class="section-title">🚀 Featured Projects</h2>
        <div class="projects-grid">
            <div class="project-card">
                <div class="project-image">🛒</div>
                <div class="project-content">
                    <h3 class="project-title">Smart E-Commerce Platform</h3>
                    <p class="project-desc">A full-featured e-commerce solution with real-time inventory, AI recommendations, and seamless payments.</p>
                    <div class="project-tech">
                        <span class="tech-tag">React</span>
                        <span class="tech-tag">Node.js</span>
                        <span class="tech-tag">MongoDB</span>
                        <span class="tech-tag">Redis</span>
                    </div>
                    <div class="project-links">
                        <a href="#" class="project-link">View Project →</a>
                        <a href="#" class="project-link">GitHub →</a>
                    </div>
                </div>
            </div>
            <div class="project-card">
                <div class="project-image">🧠</div>
                <div class="project-content">
                    <h3 class="project-title">AI Health Assistant</h3>
                    <p class="project-desc">Intelligent healthcare app with symptom analysis, appointments, and personalized health insights.</p>
                    <div class="project-tech">
                        <span class="tech-tag">Python</span>
                        <span class="tech-tag">TensorFlow</span>
                        <span class="tech-tag">Flutter</span>
                        <span class="tech-tag">FastAPI</span>
                    </div>
                    <div class="project-links">
                        <a href="#" class="project-link">View Project →</a>
                        <a href="#" class="project-link">GitHub →</a>
                    </div>
                </div>
            </div>
            <div class="project-card">
                <div class="project-image">📊</div>
                <div class="project-content">
                    <h3 class="project-title">FinTech Analytics Dashboard</h3>
                    <p class="project-desc">Real-time financial analytics with advanced visualizations and portfolio management.</p>
                    <div class="project-tech">
                        <span class="tech-tag">Vue.js</span>
                        <span class="tech-tag">Spring Boot</span>
                        <span class="tech-tag">PostgreSQL</span>
                        <span class="tech-tag">WebSocket</span>
                    </div>
                    <div class="project-links">
                        <a href="#" class="project-link">View Project →</a>
                        <a href="#" class="project-link">GitHub →</a>
                    </div>
                </div>
            </div>
            <div class="project-card">
                <div class="project-image">🏠</div>
                <div class="project-content">
                    <h3 class="project-title">IoT Home Automation</h3>
                    <p class="project-desc">Complete smart home solution with mobile control and voice-activated automation.</p>
                    <div class="project-tech">
                        <span class="tech-tag">Flutter</span>
                        <span class="tech-tag">Firebase</span>
                        <span class="tech-tag">MQTT</span>
                        <span class="tech-tag">Arduino</span>
                    </div>
                    <div class="project-links">
                        <a href="#" class="project-link">View Project →</a>
                        <a href="#" class="project-link">GitHub →</a>
                    </div>
                </div>
            </div>
            <div class="project-card">
                <div class="project-image">🌐</div>
                <div class="project-content">
                    <h3 class="project-title">Developer Portfolio 3.0</h3>
                    <p class="project-desc">Modern portfolio with smooth animations, dark mode, and dynamic CMS integration.</p>
                    <div class="project-tech">
                        <span class="tech-tag">Next.js</span>
                        <span class="tech-tag">Tailwind</span>
                        <span class="tech-tag">Framer Motion</span>
                        <span class="tech-tag">Contentful</span>
                    </div>
                    <div class="project-links">
                        <a href="#" class="project-link">View Project →</a>
                        <a href="#" class="project-link">GitHub →</a>
                    </div>
                </div>
            </div>
            <div class="project-card">
                <div class="project-image">🎮</div>
                <div class="project-content">
                    <h3 class="project-title">Multiplayer Game Engine</h3>
                    <p class="project-desc">Real-time multiplayer framework with lobby system and matchmaking.</p>
                    <div class="project-tech">
                        <span class="tech-tag">Node.js</span>
                        <span class="tech-tag">Socket.io</span>
                        <span class="tech-tag">Canvas API</span>
                        <span class="tech-tag">WebRTC</span>
                    </div>
                    <div class="project-links">
                        <a href="#" class="project-link">View Project →</a>
                        <a href="#" class="project-link">GitHub →</a>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <section class="section">
        <h2 class="section-title">📚 Learning Journey</h2>
        <div class="timeline">
            <div class="timeline-item">
                <div class="timeline-dot"></div>
                <div class="timeline-content">
                    <div class="timeline-year">2022</div>
                    <p>🎯 Programming Foundations - Mastered Java & Python, built first web applications</p>
                </div>
            </div>
            <div class="timeline-item">
                <div class="timeline-dot"></div>
                <div class="timeline-content">
                    <div class="timeline-year">2023</div>
                    <p><function_calls>
<invoke name="artifacts">
<parameter name="command">update</parameter>
<parameter name="id">jatin_portfolio_readme</parameter>
<parameter name="old_str">                    <p></parameter>
<parameter name="new_str">                    <p>🚀 Full-Stack Development - React, Node.js & databases, deployed 10+ production apps</p>
</div>
</div>
<div class="timeline-item">
<div class="timeline-dot"></div>
<div class="timeline-content">
<div class="timeline-year">2024</div>
<p>📱 Mobile & DevOps - Flutter, React Native, Docker, Kubernetes & AWS</p>
</div>
</div>
<div class="timeline-item">
<div class="timeline-dot"></div>
<div class="timeline-content">
<div class="timeline-year">2025</div>
<p>🤖 Advanced Technologies - AI/ML Engineering, Blockchain & System Architecture</p>
</div>
</div>
</div>
</section>
<section class="section" id="contact">
    <h2 class="section-title">🌐 Let's Connect</h2>
    <div class="contact-grid">
        <a href="https://linkedin.com/in/jatinjoshi" class="contact-card">
            <div class="contact-icon">💼</div>
            <h3>LinkedIn</h3>
            <p>Connect professionally</p>
        </a>
        <a href="https://github.com/jatinjoshi" class="contact-card">
            <div class="contact-icon">🐙</div>
            <h3>GitHub</h3>
            <p>View my code</p>
        </a>
        <a href="https://twitter.com/jatinjoshi" class="contact-card">
            <div class="contact-icon">🐦</div>
            <h3>Twitter</h3>
            <p>Follow updates</p>
        </a>
        <a href="mailto:jatin@example.com" class="contact-card">
            <div class="contact-icon">✉️</div>
            <h3>Email</h3>
            <p>Get in touch</p>
        </a>
    </div>
</section>

<footer class="footer">
    <p class="footer-text">Built with <span class="footer-heart">❤️</span> by Jatin Joshi</p>
    <p class="footer-text" style="margin-top: 0.5rem; font-size: 0.9rem;">© 2025 All rights reserved</p>
</footer>

<script>
    // Custom cursor
    const cursorDot = document.querySelector('.cursor-dot');
    const cursorOutline = document.querySelector('.cursor-outline');

    document.addEventListener('mousemove', (e) => {
        cursorDot.style.left = e.clientX + 'px';
        cursorDot.style.top = e.clientY + 'px';
        
        cursorOutline.style.left = e.clientX + 'px';
        cursorOutline.style.top = e.clientY + 'px';
    });

    document.querySelectorAll('a, .btn, .skill-card, .project-card, .contact-card').forEach(el => {
        el.addEventListener('mouseenter', () => {
            cursorOutline.style.transform = 'scale(1.5)';
            cursorDot.style.transform = 'scale(1.5)';
        });
        el.addEventListener('mouseleave', () => {
            cursorOutline.style.transform = 'scale(1)';
            cursorDot.style.transform = 'scale(1)';
        });
    });

    // Particles
    const particlesContainer = document.getElementById('particles');
    for (let i = 0; i < 50; i++) {
        const particle = document.createElement('div');
        particle.className = 'particle';
        particle.style.width = Math.random() * 5 + 2 + 'px';
        particle.style.height = particle.style.width;
        particle.style.left = Math.random() * 100 + '%';
        particle.style.animationDelay = Math.random() * 20 + 's';
        particle.style.animationDuration = (Math.random() * 10 + 15) + 's';
        particlesContainer.appendChild(particle);
    }

    // Stats counter animation
    const animateCounter = (el) => {
        const target = parseInt(el.getAttribute('data-target'));
        const duration = 2000;
        const increment = target / (duration / 16);
        let current = 0;

        const updateCounter = () => {
            current += increment;
            if (current < target) {
                el.textContent = Math.ceil(current);
                requestAnimationFrame(updateCounter);
            } else {
                el.textContent = target;
            }
        };

        updateCounter();
    };

    // Intersection Observer for animations
    const observerOptions = {
        threshold: 0.2,
        rootMargin: '0px'
    };

    const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                entry.target.style.opacity = '1';
                entry.target.style.transform = 'translateY(0)';
                
                // Animate stats
                if (entry.target.classList.contains('stat-card')) {
                    const counter = entry.target.querySelector('.stat-number');
                    animateCounter(counter);
                }
            }
        });
    }, observerOptions);

    // Observe elements
    document.querySelectorAll('.skill-card, .project-card, .stat-card, .timeline-item, .contact-card').forEach(el => {
        el.style.opacity = '0';
        el.style.transform = 'translateY(30px)';
        el.style.transition = 'all 0.6s ease';
        observer.observe(el);
    });

    // GSAP ScrollTrigger animations
    gsap.registerPlugin(ScrollTrigger);

    gsap.utils.toArray('.section-title').forEach(title => {
        gsap.from(title, {
            scrollTrigger: {
                trigger: title,
                start: 'top 80%',
                end: 'top 50%',
                scrub: 1
            },
            y: 50,
            opacity: 0
        });
    });

    // Smooth scroll
    document.querySelectorAll('a[href^="#"]').forEach(anchor => {
        anchor.addEventListener('click', function(e) {
            e.preventDefault();
            const target = document.querySelector(this.getAttribute('href'));
            if (target) {
                target.scrollIntoView({
                    behavior: 'smooth',
                    block: 'start'
                });
            }
        });
    });

    // Hide scroll indicator on scroll
    window.addEventListener('scroll', () => {
        const scrollIndicator = document.querySelector('.scroll-indicator');
        if (window.scrollY > 100) {
            scrollIndicator.style.opacity = '0';
        } else {
            scrollIndicator.style.opacity = '1';
        }
    });

    // Parallax effect for hero
    window.addEventListener('scroll', () => {
        const scrolled = window.pageYOffset;
        const hero = document.querySelector('.hero-content');
        hero.style.transform = `translateY(${scrolled * 0.5}px)`;
        hero.style.opacity = 1 - scrolled / 500;
    });

    // Add ripple effect to buttons
    document.querySelectorAll('.btn').forEach(button => {
        button.addEventListener('click', function(e) {
            const x = e.clientX - e.target.offsetLeft;
            const y = e.clientY - e.target.offsetTop;
            
            const ripple = document.createElement('span');
            ripple.style.left = x + 'px';
            ripple.style.top = y + 'px';
            
            this.appendChild(ripple);
            
            setTimeout(() => {
                ripple.remove();
            }, 600);
        });
    });
</script>
</body>
</html></parameter>Claude is AI and can make mistakes. Please double-check responses.