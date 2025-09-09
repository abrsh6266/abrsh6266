<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Abrham Belayineh - Fullstack Developer</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #0f0f23 0%, #1a1a2e 50%, #16213e 100%);
            color: #ffffff;
            line-height: 1.6;
            min-height: 100vh;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Header Section */
        .header {
            text-align: center;
            padding: 60px 0;
            position: relative;
            overflow: hidden;
        }

        .header::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(45deg, rgba(139, 69, 255, 0.1), rgba(59, 130, 246, 0.1));
            z-index: -1;
        }

        .profile-avatar {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            background: linear-gradient(45deg, #8b5cf6, #3b82f6);
            padding: 4px;
            margin: 0 auto 30px;
            position: relative;
            animation: float 3s ease-in-out infinite;
        }

        .profile-avatar::before {
            content: 'AB';
            position: absolute;
            top: 4px;
            left: 4px;
            right: 4px;
            bottom: 4px;
            background: #1a1a2e;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2.5rem;
            font-weight: bold;
            color: #8b5cf6;
        }

        .status-indicator {
            position: absolute;
            top: 10px;
            right: 10px;
            width: 25px;
            height: 25px;
            background: #10b981;
            border-radius: 50%;
            border: 3px solid #1a1a2e;
            animation: pulse 2s infinite;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
        }

        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.5; }
        }

        .typing-effect {
            height: 40px;
            overflow: hidden;
        }

        .typing-text {
            animation: typing 4s steps(20) infinite;
            color: #8b5cf6;
            font-size: 1.2rem;
        }

        @keyframes typing {
            0% { width: 0; }
            25% { width: 100%; }
            75% { width: 100%; }
            100% { width: 0; }
        }

        .main-title {
            font-size: 3.5rem;
            font-weight: bold;
            background: linear-gradient(45deg, #8b5cf6, #3b82f6);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 20px;
        }

        .subtitle {
            font-size: 1.5rem;
            color: #9ca3af;
            margin-bottom: 30px;
        }

        /* Social Links */
        .social-links {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin: 30px 0;
        }

        .social-link {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.1);
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s ease;
            text-decoration: none;
            backdrop-filter: blur(10px);
        }

        .social-link:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(139, 69, 255, 0.3);
        }

        .social-link.linkedin:hover { background: #0077b5; }
        .social-link.github:hover { background: #333; }
        .social-link.instagram:hover { background: linear-gradient(45deg, #f09433, #e6683c, #dc2743, #cc2366, #bc1888); }
        .social-link.email:hover { background: #ea4335; }

        /* Stats Section */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin: 60px 0;
        }

        .stat-card {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            padding: 30px;
            text-align: center;
            backdrop-filter: blur(10px);
            transition: transform 0.3s ease;
        }

        .stat-card:hover {
            transform: translateY(-5px);
        }

        .stat-number {
            font-size: 2.5rem;
            font-weight: bold;
            color: #8b5cf6;
            margin-bottom: 10px;
        }

        /* Skills Section */
        .section-title {
            text-align: center;
            font-size: 2.5rem;
            margin-bottom: 40px;
            color: #8b5cf6;
        }

        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-bottom: 60px;
        }

        .skill-card {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            padding: 25px;
            backdrop-filter: blur(10px);
        }

        .skill-header {
            display: flex;
            justify-content: between;
            align-items: center;
            margin-bottom: 15px;
        }

        .skill-name {
            font-weight: bold;
            font-size: 1.1rem;
        }

        .skill-level {
            color: #9ca3af;
            font-size: 0.9rem;
        }

        .progress-bar {
            width: 100%;
            height: 8px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 4px;
            overflow: hidden;
        }

        .progress-fill {
            height: 100%;
            border-radius: 4px;
            transition: width 2s ease;
        }

        .progress-react { background: linear-gradient(90deg, #61dafb, #21d4fd); width: 95%; }
        .progress-vue { background: linear-gradient(90deg, #4fc08d, #42b883); width: 90%; }
        .progress-laravel { background: linear-gradient(90deg, #ff2d20, #f56565); width: 88%; }
        .progress-node { background: linear-gradient(90deg, #68a063, #8cc84b); width: 92%; }
        .progress-go { background: linear-gradient(90deg, #00add8, #5dc9e2); width: 85%; }
        .progress-dotnet { background: linear-gradient(90deg, #512bd4, #7c3aed); width: 87%; }

        /* Technologies Section */
        .tech-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 20px;
            margin-bottom: 60px;
        }

        .tech-card {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            padding: 25px;
            backdrop-filter: blur(10px);
        }

        .tech-category {
            font-size: 1.3rem;
            font-weight: bold;
            color: #3b82f6;
            margin-bottom: 15px;
        }

        .tech-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
        }

        .tech-tag {
            background: rgba(255, 255, 255, 0.1);
            padding: 5px 12px;
            border-radius: 20px;
            font-size: 0.9rem;
            transition: all 0.3s ease;
        }

        .tech-tag:hover {
            background: #8b5cf6;
            transform: translateY(-2px);
        }

        /* Current Focus */
        .focus-section {
            background: linear-gradient(45deg, rgba(139, 69, 255, 0.2), rgba(59, 130, 246, 0.2));
            border: 1px solid rgba(139, 69, 255, 0.3);
            border-radius: 20px;
            padding: 40px;
            text-align: center;
            margin: 60px 0;
        }

        .focus-icon {
            font-size: 3rem;
            margin-bottom: 20px;
        }

        /* Footer */
        .footer {
            text-align: center;
            padding: 40px 0;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            margin-top: 60px;
        }

        .quote {
            font-style: italic;
            color: #9ca3af;
            margin-bottom: 10px;
        }

        /* Animations */
        .fade-in {
            animation: fadeIn 1s ease-in;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Responsive */
        @media (max-width: 768px) {
            .main-title { font-size: 2.5rem; }
            .stats-grid { grid-template-columns: repeat(2, 1fr); }
            .skills-grid, .tech-grid { grid-template-columns: 1fr; }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Header Section -->
        <header class="header fade-in">
            <div class="profile-avatar">
                <div class="status-indicator"></div>
            </div>
            
            <h1 class="main-title">Abrham Belayineh</h1>
            
            <div class="typing-effect">
                <div class="typing-text" id="typingText">Fullstack Developer</div>
            </div>
            
            <p class="subtitle">🚀 Passionate Developer from Ethiopia | ☕ Fueled by Coffee</p>
            
            <div class="social-links">
                <a href="mailto:abrsh6266@gmail.com" class="social-link email">📧</a>
                <a href="https://linkedin.com/in/abrham-belayineh-190658258" class="social-link linkedin">💼</a>
                <a href="https://github.com/abrsh6266" class="social-link github">🐱</a>
                <a href="https://instagram.com/umabrshxovll" class="social-link instagram">📷</a>
            </div>
        </header>

        <!-- Stats Section -->
        <section class="stats-grid fade-in">
            <div class="stat-card">
                <div class="stat-number">3+</div>
                <div>Years Experience</div>
            </div>
            <div class="stat-card">
                <div class="stat-number">50+</div>
                <div>Projects Completed</div>
            </div>
            <div class="stat-card">
                <div class="stat-number">25+</div>
                <div>Technologies</div>
            </div>
            <div class="stat-card">
                <div class="stat-number">40+</div>
                <div>GitHub Repos</div>
            </div>
        </section>

        <!-- About Section -->
        <section class="fade-in" style="text-align: center; margin: 60px 0;">
            <h2 class="section-title">About Me</h2>
            <p style="font-size: 1.2rem; color: #d1d5db; max-width: 800px; margin: 0 auto;">
                I'm a passionate fullstack developer from Ethiopia with a love for creating innovative solutions. 
                Currently working on exciting projects that push the boundaries of web development. 
                I enjoy solving complex problems and turning ideas into reality through clean, efficient code.
            </p>
        </section>

        <!-- Skills Section -->
        <section class="fade-in">
            <h2 class="section-title">Skills & Expertise</h2>
            <div class="skills-grid">
                <div class="skill-card">
                    <div class="skill-header">
                        <span class="skill-name">React</span>
                        <span class="skill-level">95%</span>
                    </div>
                    <div class="progress-bar">
                        <div class="progress-fill progress-react"></div>
                    </div>
                </div>
                <div class="skill-card">
                    <div class="skill-header">
                        <span class="skill-name">Vue.js</span>
                        <span class="skill-level">90%</span>
                    </div>
                    <div class="progress-bar">
                        <div class="progress-fill progress-vue"></div>
                    </div>
                </div>
                <div class="skill-card">
                    <div class="skill-header">
                        <span class="skill-name">Laravel</span>
                        <span class="skill-level">88%</span>
                    </div>
                    <div class="progress-bar">
                        <div class="progress-fill progress-laravel"></div>
                    </div>
                </div>
                <div class="skill-card">
                    <div class="skill-header">
                        <span class="skill-name">Node.js</span>
                        <span class="skill-level">92%</span>
                    </div>
                    <div class="progress-bar">
                        <div class="progress-fill progress-node"></div>
                    </div>
                </div>
                <div class="skill-card">
                    <div class="skill-header">
                        <span class="skill-name">Go</span>
                        <span class="skill-level">85%</span>
                    </div>
                    <div class="progress-bar">
                        <div class="progress-fill progress-go"></div>
                    </div>
                </div>
                <div class="skill-card">
                    <div class="skill-header">
                        <span class="skill-name">.NET</span>
                        <span class="skill-level">87%</span>
                    </div>
                    <div class="progress-bar">
                        <div class="progress-fill progress-dotnet"></div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Technologies Section -->
        <section class="fade-in">
            <h2 class="section-title">Technologies & Tools</h2>
            <div class="tech-grid">
                <div class="tech-card">
                    <h3 class="tech-category">Frontend</h3>
                    <div class="tech-tags">
                        <span class="tech-tag">React</span>
                        <span class="tech-tag">Vue.js</span>
                        <span class="tech-tag">Angular</span>
                        <span class="tech-tag">Next.js</span>
                        <span class="tech-tag">Nuxt.js</span>
                        <span class="tech-tag">TypeScript</span>
                    </div>
                </div>
                <div class="tech-card">
                    <h3 class="tech-category">Backend</h3>
                    <div class="tech-tags">
                        <span class="tech-tag">Node.js</span>
                        <span class="tech-tag">Laravel</span>
                        <span class="tech-tag">Go</span>
                        <span class="tech-tag">.NET</span>
                        <span class="tech-tag">Express.js</span>
                        <span class="tech-tag">NestJS</span>
                    </div>
                </div>
                <div class="tech-card">
                    <h3 class="tech-category">Mobile</h3>
                    <div class="tech-tags">
                        <span class="tech-tag">React Native</span>
                        <span class="tech-tag">Flutter</span>
                    </div>
                </div>
                <div class="tech-card">
                    <h3 class="tech-category">Database</h3>
                    <div class="tech-tags">
                        <span class="tech-tag">MongoDB</span>
                        <span class="tech-tag">PostgreSQL</span>
                        <span class="tech-tag">MySQL</span>
                        <span class="tech-tag">SQL Server</span>
                    </div>
                </div>
                <div class="tech-card">
                    <h3 class="tech-category">Tools & Others</h3>
                    <div class="tech-tags">
                        <span class="tech-tag">Docker</span>
                        <span class="tech-tag">Git</span>
                        <span class="tech-tag">Figma</span>
                        <span class="tech-tag">Postman</span>
                        <span class="tech-tag">Firebase</span>
                        <span class="tech-tag">GraphQL</span>
                    </div>
                </div>
            </div>
        </section>

        <!-- Current Focus -->
        <section class="focus-section fade-in">
            <div class="focus-icon">⚡</div>
            <h2 style="color: #8b5cf6; margin-bottom: 20px;">Currently Working On</h2>
            <p style="font-size: 1.2rem; color: #d1d5db;">
                Building innovative fullstack applications and exploring new technologies to create amazing user experiences.
            </p>
        </section>

        <!-- GitHub Stats -->
        <section class="fade-in" style="text-align: center; margin: 60px 0;">
            <h2 class="section-title">GitHub Statistics</h2>
            <div style="display: flex; flex-wrap: wrap; justify-content: center; gap: 20px; align-items: center;">
                <img src="https://github-readme-stats.vercel.app/api/top-langs?username=abrsh6266&show_icons=true&locale=en&layout=compact&theme=radical" alt="Top Languages" style="border-radius: 10px;" />
                <img src="https://github-readme-stats.vercel.app/api?username=abrsh6266&show_icons=true&locale=en&theme=radical" alt="GitHub Stats" style="border-radius: 10px;" />
                <img src="https://github-readme-streak-stats.herokuapp.com/?user=abrsh6266&theme=radical" alt="GitHub Streak" style="border-radius: 10px;" />
            </div>
        </section>

        <!-- Footer -->
        <footer class="footer fade-in">
            <p class="quote">💻 "Code is like humor. When you have to explain it, it's bad." - Cory House</p>
            <p style="color: #6b7280;">Let's connect and build something amazing together! 🚀</p>
        </footer>
    </div>

    <script>
        // Typing animation
        const texts = ['Fullstack Developer', 'Problem Solver', 'Tech Enthusiast', 'Code Architect'];
        let textIndex = 0;
        let charIndex = 0;
        let isDeleting = false;
        const typingElement = document.getElementById('typingText');

        function typeWriter() {
            const currentText = texts[textIndex];
            
            if (isDeleting) {
                typingElement.textContent = currentText.substring(0, charIndex - 1);
                charIndex--;
            } else {
                typingElement.textContent = currentText.substring(0, charIndex + 1);
                charIndex++;
            }

            let typeSpeed = isDeleting ? 50 : 100;

            if (!isDeleting && charIndex === currentText.length) {
                typeSpeed = 2000;
                isDeleting = true;
            } else if (isDeleting && charIndex === 0) {
                isDeleting = false;
                textIndex = (textIndex + 1) % texts.length;
                typeSpeed = 500;
            }

            setTimeout(typeWriter, typeSpeed);
        }

        // Start typing animation
        typeWriter();

        // Fade in animation on scroll
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = '1';
                    entry.target.style.transform = 'translateY(0)';
                }
            });
        }, observerOptions);

        document.querySelectorAll('.fade-in').forEach(el => {
            el.style.opacity = '0';
            el.style.transform = 'translateY(30px)';
            el.style.transition = 'opacity 0.6s ease, transform 0.6s ease';
            observer.observe(el);
        });
    </script>
</body>
</html>
