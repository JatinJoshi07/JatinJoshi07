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
            scroll-behavior: smooth;
        }

        body {
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            background: #0a0e27;
            background: linear-gradient(135deg, #0a0e27 0%, #1a1a2e 50%, #16213e 100%);
            color: #e0e0e0;
            overflow-x: hidden;
            line-height: 1.6;
        }

        /* Custom Cursor */
        .cursor-dot, .cursor-outline {
            position: fixed;
            top: 0;
            left: 0;
            transform: translate(-50%, -50%);
            border-radius: 50%;
            z-index: 10000;
            pointer-events: none;
            transition: transform 0.1s ease-out;
        }

        .cursor-dot {
            width: 8px;
            height: 8px;
            background: #00d4ff;
        }

        .cursor-outline {
            width: 40px;
            height: 40px;
            border: 2px solid rgba(0, 212, 255, 0.4);
            transition: all 0.2s ease-out;
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
            text-align: center;
        }

        .particles {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
        }

        .particle {
            position: absolute;
            background: rgba(0, 212, 255, 0.3);
            border-radius: 50%;
            pointer-events: none;
        }

        .hero-content {
            position: relative;
            z-index: 2;
            padding: 2rem;
        }

        .glitch {
            font-size: clamp(3rem, 10vw, 5rem);
            font-weight: 900;
            text-transform: uppercase;
            position: relative;
            text-shadow: 0.05em 0 0 #00fffc, -0.03em -0.04em 0 #fc00ff, 0.025em 0.04em 0 #fffc00;
            animation: glitch 725ms infinite;
        }

        @keyframes glitch {
            0% { text-shadow: 0.05em 0 0 #00fffc, -0.03em -0.04em 0 #fc00ff, 0.025em 0.04em 0 #fffc00; }
            15% { text-shadow: 0.05em 0 0 #00fffc, -0.03em -0.04em 0 #fc00ff, 0.025em 0.04em 0 #fffc00; }
            16% { text-shadow: -0.05em -0.025em 0 #00fffc, 0.025em 0.035em 0 #fc00ff, -0.05em -0.05em 0 #fffc00; }
            49% { text-shadow: -0.05em -0.025em 0 #00fffc, 0.025em 0.035em 0 #fc00ff, -0.05em -0.05em 0 #fffc00; }
            50% { text-shadow: 0.05em 0.035em 0 #00fffc, 0.03em 0 0 #fc00ff, 0 -0.04em 0 #fffc00; }
            99% { text-shadow: 0.05em 0.035em 0 #00fffc, 0.03em 0 0 #fc00ff, 0 -0.04em 0 #fffc00; }
            100% { text-shadow: -0.05em 0 0 #00fffc, -0.025em -0.04em 0 #fc00ff, -0.04em -0.025em 0 #fffc00; }
        }

        .subtitle {
            font-size: clamp(1rem, 4vw, 1.5rem);
            margin: 1rem 0;
            color: #00d4ff;
        }

        .btn {
            padding: 0.8rem 2rem;
            border-radius: 50px;
            text-decoration: none;
            font-weight: 600;
            display: inline-block;
            margin: 0.5rem;
            transition: 0.3s;
            border: 2px solid #00d4ff;
        }

        .btn-primary {
            background: #00d4ff;
            color: #0a0e27;
        }

        .btn-secondary {
            color: #00d4ff;
            background: transparent;
        }

        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(0, 212, 255, 0.3);
        }

        /* Sections */
        .section {
            padding: 80px 20px;
            max-width: 1200px;
            margin: 0 auto;
        }

        .section-title {
            font-size: 2.5rem;
            text-align: center;
            margin-bottom: 3rem;
            color: #00d4ff;
        }

        /* Stats */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
        }

        .stat-card {
            background: rgba(255, 255, 255, 0.05);
            padding: 2rem;
            border-radius: 15px;
            text-align: center;
            border: 1px solid rgba(0, 212, 255, 0.1);
        }

        .stat-number {
            font-size: 2.5rem;
            font-weight: bold;
            color: #00d4ff;
            display: block;
        }

        /* Skills */
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 20px;
        }

        .skill-card {
            background: rgba(255, 255, 255, 0.03);
            padding: 1.5rem;
            border-radius: 15px;
            border: 1px solid rgba(0, 212, 255, 0.1);
            transition: 0.3s;
        }

        .skill-card:hover {
            background: rgba(255, 255, 255, 0.07);
            border-color: #00d4ff;
        }

        .skill-tag {
            display: inline-block;
            background: rgba(0, 212, 255, 0.1);
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 0.8rem;
            margin: 4px;
            border: 1px solid rgba(0, 212, 255, 0.2);
        }

        /* Projects */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 30px;
        }

        .project-card {
            background: rgba(255, 255, 255, 0.03);
            border-radius: 20px;
            overflow: hidden;
            border: 1px solid rgba(255, 255, 255, 0.1);
            transition: 0.4s;
        }

        .project-card:hover {
            transform: translateY(-10px);
            border-color: #00d4ff;
        }

        .project-image {
            height: 180px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
            background: #16213e;
        }

        .project-content { padding: 1.5rem; }

        /* Timeline */
        .timeline {
            position: relative;
            max-width: 800px;
            margin: 0 auto;
            padding: 40px 0;
        }

        .timeline::before {
            content: '';
            position: absolute;
            left: 50%;
            width: 2px;
            height: 100%;
            background: #00d4ff;
            transform: translateX(-50%);
        }

        .timeline-item {
            margin-bottom: 40px;
            width: 100%;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .timeline-content {
            width: 45%;
            padding: 20px;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 10px;
            border: 1px solid rgba(0, 212, 255, 0.2);
        }

        .timeline-item:nth-child(even) { flex-direction: row-reverse; }

        /* Contact */
        .contact-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
        }

        .contact-card {
            text-align: center;
            padding: 2rem;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 15px;
            text-decoration: none;
            color: white;
            transition: 0.3s;
        }

        .contact-card:hover {
            background: #00d4ff;
            color: #0a0e27;
        }

        .scroll-indicator {
            position: absolute;
            bottom: 30px;
            left: 50%;
            transform: translateX(-50%);
            animation: bounce 2s infinite;
            font-size: 2rem;
            color: #00d4ff;
        }

        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% {transform: translateY(0) translateX(-50%);}
            40% {transform: translateY(-10px) translateX(-50%);}
            60% {transform: translateY(-5px) translateX(-50%);}
        }

        @media (max-width: 768px) {
            .timeline::before { left: 20px; }
            .timeline-item { flex-direction: row !important; }
            .timeline-content { width: 85%; margin-left: 40px; }
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
            <p class="subtitle">Full-Stack Developer | Tech Innovator</p>
            <div class="cta-buttons">
                <a href="#projects" class="btn btn-primary">View Projects</a>
                <a href="#contact" class="btn btn-secondary">Contact Me</a>
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
                <span class="stat-label">Tech Stack</span>
            </div>
        </div>
    </section>

    <section class="section" id="skills">
        <h2 class="section-title">Skills</h2>
        <div class="skills-grid">
            <div class="skill-card">
                <h3>Frontend</h3>
                <div class="skill-tag">React</div><div class="skill-tag">Next.js</div><div class="skill-tag">Tailwind</div>
            </div>
            <div class="skill-card">
                <h3>Backend</h3>
                <div class="skill-tag">Node.js</div><div class="skill-tag">Python</div><div class="skill-tag">PostgreSQL</div>
            </div>
            <div class="skill-card">
                <h3>DevOps</h3>
                <div class="skill-tag">AWS</div><div class="skill-tag">Docker</div><div class="skill-tag">CI/CD</div>
            </div>
        </div>
    </section>

    <section class="section" id="projects">
        <h2 class="section-title">Projects</h2>
        <div class="projects-grid">
            <div class="project-card">
                <div class="project-image">🚀</div>
                <div class="project-content">
                    <h3>AI Platform</h3>
                    <p>Next-gen AI integration tool.</p>
                </div>
            </div>
            <div class="project-card">
                <div class="project-image">🛡️</div>
                <div class="project-content">
                    <h3>Fintech App</h3>
                    <p>Secure banking architecture.</p>
                </div>
            </div>
        </div>
    </section>

    <section class="section">
        <h2 class="section-title">Journey</h2>
        <div class="timeline">
            <div class="timeline-item">
                <div class="timeline-content">
                    <h4>2023</h4>
                    <p>Started Full-Stack Mastery</p>
                </div>
            </div>
            <div class="timeline-item">
                <div class="timeline-content">
                    <h4>2024</h4>
                    <p>Cloud Architecture Specialization</p>
                </div>
            </div>
            <div class="timeline-item">
                <div class="timeline-content">
                    <h4>2025</h4>
                    <p>Lead AI Developer</p>
                </div>
            </div>
        </div>
    </section>

    <section class="section" id="contact">
        <h2 class="section-title">Connect</h2>
        <div class="contact-grid">
            <a href="#" class="contact-card">GitHub</a>
            <a href="#" class="contact-card">LinkedIn</a>
            <a href="mailto:jatin@example.com" class="contact-card">Email</a>
        </div>
    </section>

    <script>
        // Custom Cursor Logic
        const dot = document.querySelector('.cursor-dot');
        const outline = document.querySelector('.cursor-outline');

        window.addEventListener('mousemove', (e) => {
            dot.style.transform = `translate(${e.clientX}px, ${e.clientY}px)`;
            outline.style.transform = `translate(${e.clientX}px, ${e.clientY}px)`;
        });

        // Particle System
        const container = document.getElementById('particles');
        for (let i = 0; i < 50; i++) {
            const p = document.createElement('div');
            p.className = 'particle';
            const size = Math.random() * 3 + 2;
            p.style.width = size + 'px';
            p.style.height = size + 'px';
            p.style.left = Math.random() * 100 + '%';
            p.style.top = Math.random() * 100 + '%';
            p.style.opacity = Math.random();
            container.appendChild(p);
            
            gsap.to(p, {
                y: "-=100",
                x: `+=${Math.random() * 50 - 25}`,
                duration: Math.random() * 3 + 2,
                repeat: -1,
                yoyo: true,
                ease: "sine.inOut"
            });
        }

        // Counter Animation
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting && entry.target.classList.contains('stat-card')) {
                    const numEl = entry.target.querySelector('.stat-number');
                    const target = parseInt(numEl.getAttribute('data-target'));
                    gsap.to(numEl, {
                        innerText: target,
                        duration: 2,
                        snap: { innerText: 1 }
                    });
                }
            });
        }, { threshold: 0.5 });

        document.querySelectorAll('.stat-card').forEach(card => observer.observe(card));

        // GSAP Scroll Animations
        gsap.registerPlugin(ScrollTrigger);
        gsap.from(".project-card", {
            scrollTrigger: {
                trigger: ".projects-grid",
                start: "top 80%"
            },
            y: 50,
            opacity: 0,
            duration: 0.8,
            stagger: 0.2
        });
    </script>
</body>
</html>
