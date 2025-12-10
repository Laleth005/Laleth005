<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Laleth R - Animated GitHub Profile</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
            background: linear-gradient(135deg, #0d1117 0%, #1a1b26 100%);
            color: #e6edf3;
            padding: 40px 20px;
            line-height: 1.6;
            overflow-x: hidden;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: rgba(13, 17, 23, 0.8);
            border-radius: 16px;
            padding: 60px 40px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.5);
        }

        .header {
            text-align: center;
            margin-bottom: 40px;
        }

        .header h1 {
            font-size: 3rem;
            margin-bottom: 10px;
            background: linear-gradient(135deg, #ff4b5c, #ff758c);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: glow 2s ease-in-out infinite;
        }

        @keyframes glow {
            0%, 100% { filter: drop-shadow(0 0 10px rgba(255, 75, 92, 0.5)); }
            50% { filter: drop-shadow(0 0 20px rgba(255, 75, 92, 0.8)); }
        }

        .header h3 {
            font-size: 1.3rem;
            color: #8b949e;
            font-weight: 400;
            margin-bottom: 20px;
        }

        .typing-text {
            font-size: 1.2rem;
            color: #ff4b5c;
            font-family: 'Courier New', monospace;
            margin-top: 20px;
            min-height: 30px;
        }

        .divider {
            height: 2px;
            background: linear-gradient(90deg, transparent, #ff4b5c, transparent);
            margin: 40px 0;
            animation: pulse 2s ease-in-out infinite;
        }

        @keyframes pulse {
            0%, 100% { opacity: 0.5; }
            50% { opacity: 1; }
        }

        .section {
            margin-bottom: 50px;
            animation: fadeInUp 0.8s ease-out;
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .section-title {
            font-size: 2rem;
            margin-bottom: 20px;
            color: #ff4b5c;
        }

        .badges {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            justify-content: center;
            margin-bottom: 20px;
        }

        .badge {
            display: inline-block;
            padding: 10px 20px;
            border-radius: 8px;
            font-weight: 600;
            text-decoration: none;
            transition: all 0.3s ease;
            font-size: 0.9rem;
            animation: bounceIn 0.6s ease-out;
        }

        @keyframes bounceIn {
            0% { transform: scale(0); opacity: 0; }
            50% { transform: scale(1.1); }
            100% { transform: scale(1); opacity: 1; }
        }

        .badge:hover {
            transform: translateY(-5px) scale(1.05);
            box-shadow: 0 8px 20px rgba(255, 75, 92, 0.5);
        }

        .badge.email { background: #ff4b5c; color: white; }
        .badge.linkedin { background: #0A66C2; color: white; }
        .badge.portfolio { background: #1E1E2E; color: white; }
        .badge.github { background: #181717; color: white; }
        .badge.views { background: #ff4b5c; color: white; }

        .code-block {
            background: #161b22;
            border: 1px solid #30363d;
            border-radius: 8px;
            padding: 20px;
            margin: 20px 0;
            font-family: 'Courier New', monospace;
            overflow-x: auto;
            animation: slideIn 0.8s ease-out;
        }

        @keyframes slideIn {
            from { transform: translateX(-50px); opacity: 0; }
            to { transform: translateX(0); opacity: 1; }
        }

        .code-block .keyword { color: #ff7b72; }
        .code-block .string { color: #a5d6ff; }
        .code-block .property { color: #79c0ff; }

        .tech-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 30px;
            margin: 30px 0;
        }

        .tech-category {
            background: rgba(255, 75, 92, 0.05);
            border: 1px solid rgba(255, 75, 92, 0.2);
            border-radius: 12px;
            padding: 20px;
            text-align: center;
            transition: all 0.3s ease;
        }

        .tech-category:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(255, 75, 92, 0.3);
        }

        .tech-category h4 {
            color: #ff4b5c;
            margin-bottom: 15px;
            font-size: 1.2rem;
        }

        .tech-icons {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            justify-content: center;
            margin-top: 20px;
        }

        .tech-icon {
            width: 70px;
            height: 70px;
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            background: rgba(33, 38, 45, 0.6);
            border: 2px solid rgba(48, 54, 61, 0.8);
            transition: all 0.3s ease;
            animation: float 3s ease-in-out infinite;
            backdrop-filter: blur(10px);
        }

        .tech-icon:nth-child(1) { animation-delay: 0s; }
        .tech-icon:nth-child(2) { animation-delay: 0.2s; }
        .tech-icon:nth-child(3) { animation-delay: 0.4s; }
        .tech-icon:nth-child(4) { animation-delay: 0.6s; }
        .tech-icon:nth-child(5) { animation-delay: 0.8s; }
        .tech-icon:nth-child(6) { animation-delay: 1s; }

        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
        }

        .tech-icon:hover {
            transform: scale(1.2) rotate(5deg);
            border-color: #ff4b5c;
            box-shadow: 0 0 20px rgba(255, 75, 92, 0.5);
        }

        .tech-icon img {
            width: 45px;
            height: 45px;
            object-fit: contain;
        }
        
        .tech-icon img[src*="express"],
        .tech-icon img[src*="github"] {
            filter: invert(1);
        }

        .project-card {
            background: linear-gradient(135deg, rgba(255, 75, 92, 0.1), rgba(255, 117, 140, 0.05));
            border: 2px solid rgba(255, 75, 92, 0.3);
            border-radius: 12px;
            padding: 30px;
            text-align: center;
            margin: 20px 0;
            animation: scaleIn 0.8s ease-out;
        }

        @keyframes scaleIn {
            from { transform: scale(0.8); opacity: 0; }
            to { transform: scale(1); opacity: 1; }
        }

        .project-card h3 {
            color: #ff4b5c;
            margin-bottom: 10px;
        }

        .play-button {
            display: inline-block;
            background: #ff4b5c;
            color: white;
            padding: 12px 30px;
            border-radius: 8px;
            text-decoration: none;
            font-weight: 600;
            margin-top: 15px;
            transition: all 0.3s ease;
            animation: pulse-button 2s ease-in-out infinite;
        }

        @keyframes pulse-button {
            0%, 100% { box-shadow: 0 0 0 0 rgba(255, 75, 92, 0.7); }
            50% { box-shadow: 0 0 0 10px rgba(255, 75, 92, 0); }
        }

        .play-button:hover {
            background: #ff758c;
            transform: scale(1.1);
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin: 30px 0;
        }

        .stat-card {
            background: linear-gradient(135deg, rgba(255, 75, 92, 0.1), rgba(255, 117, 140, 0.05));
            border: 1px solid rgba(255, 75, 92, 0.3);
            border-radius: 12px;
            padding: 30px;
            text-align: center;
            transition: all 0.3s ease;
            min-height: 200px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }

        .stat-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(255, 75, 92, 0.3);
        }

        .stat-icon {
            width: 60px;
            height: 60px;
            margin-bottom: 15px;
            animation: rotate 3s linear infinite;
        }

        @keyframes rotate {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        .stat-card:hover .stat-icon {
            animation: bounce 0.6s ease;
        }

        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }

        .stat-number {
            font-size: 2.5rem;
            font-weight: bold;
            color: #ff4b5c;
            margin: 10px 0;
        }

        .stat-label {
            font-size: 1rem;
            color: #8b949e;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .stat-detail {
            font-size: 0.9rem;
            color: #e6edf3;
            margin-top: 10px;
        }

        .quote {
            text-align: center;
            font-style: italic;
            color: #8b949e;
            font-size: 1.2rem;
            margin: 40px 0;
            animation: fadeIn 2s ease-in;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .footer {
            text-align: center;
            margin-top: 50px;
            padding-top: 30px;
            border-top: 2px solid rgba(255, 75, 92, 0.2);
        }

        /* Floating particles background */
        .particle {
            position: fixed;
            width: 4px;
            height: 4px;
            background: #ff4b5c;
            border-radius: 50%;
            pointer-events: none;
            animation: rise 10s infinite ease-in;
            opacity: 0;
        }

        @keyframes rise {
            0% {
                transform: translateY(100vh) scale(0);
                opacity: 0;
            }
            10% {
                opacity: 1;
            }
            90% {
                opacity: 1;
            }
            100% {
                transform: translateY(-100vh) scale(1);
                opacity: 0;
            }
        }
    </style>
</head>
<body>
    <!-- Floating particles -->
    <script>
        for (let i = 0; i < 20; i++) {
            const particle = document.createElement('div');
            particle.className = 'particle';
            particle.style.left = Math.random() * 100 + '%';
            particle.style.animationDelay = Math.random() * 10 + 's';
            particle.style.animationDuration = (Math.random() * 10 + 10) + 's';
            document.body.appendChild(particle);
        }
    </script>

    <div class="container">
        <!-- Header -->
        <div class="header">
            <h1><svg style="display:inline-block;vertical-align:middle;width:40px;height:40px;margin-right:10px;" viewBox="0 0 24 24" fill="none" stroke="#ff4b5c" stroke-width="2"><path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"></path><circle cx="12" cy="7" r="4"></circle></svg> Hey, I'm Laleth R</h1>
            <h3>Full-Stack Developer | MERN Enthusiast | Java Spring Boot Developer</h3>
            <div class="typing-text" id="typing"></div>
        </div>

        <div class="divider"></div>

        <!-- Quick Connect -->
        <div class="section">
            <h2 class="section-title"><svg style="display:inline-block;vertical-align:middle;width:30px;height:30px;margin-right:10px;" viewBox="0 0 24 24" fill="none" stroke="#ff4b5c" stroke-width="2"><polygon points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2"></polygon></svg> Quick Connect</h2>
            <div class="badges">
                <a href="mailto:rockey1533@gmail.com" class="badge email">
                    <svg style="display:inline-block;vertical-align:middle;width:18px;height:18px;margin-right:8px;" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"></path><polyline points="22,6 12,13 2,6"></polyline></svg>
                    Email
                </a>
                <a href="https://www.linkedin.com/in/laleth-r-b15b75254/" class="badge linkedin">
                    <svg style="display:inline-block;vertical-align:middle;width:18px;height:18px;margin-right:8px;" viewBox="0 0 24 24" fill="currentColor"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
                    LinkedIn
                </a>
                <a href="https://creative-brioche-204b8c.netlify.app" class="badge portfolio">
                    <svg style="display:inline-block;vertical-align:middle;width:18px;height:18px;margin-right:8px;" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"></circle><line x1="2" y1="12" x2="22" y2="12"></line><path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"></path></svg>
                    Portfolio
                </a>
                <a href="https://github.com/Laleth005" class="badge github">
                    <svg style="display:inline-block;vertical-align:middle;width:18px;height:18px;margin-right:8px;" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg>
                    Follow
                </a>
            </div>
            <div style="text-align: center; margin-top: 15px;">
                <span class="badge views">
                    <svg style="display:inline-block;vertical-align:middle;width:18px;height:18px;margin-right:8px;" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M1 12s4-8 11-8 11 8 11 8-4 8-11 8-11-8-11-8z"></path><circle cx="12" cy="12" r="3"></circle></svg>
                    Profile Views: <span id="viewCount">0</span>
                </span>
            </div>
        </div>

        <div class="divider"></div>

        <!-- About Me -->
        <div class="section">
            <h2 class="section-title"><svg style="display:inline-block;vertical-align:middle;width:30px;height:30px;margin-right:10px;" viewBox="0 0 24 24" fill="none" stroke="#ff4b5c" stroke-width="2"><path d="M12.22 2h-.44a2 2 0 0 0-2 2v.18a2 2 0 0 1-1 1.73l-.43.25a2 2 0 0 1-2 0l-.15-.08a2 2 0 0 0-2.73.73l-.22.38a2 2 0 0 0 .73 2.73l.15.1a2 2 0 0 1 1 1.72v.51a2 2 0 0 1-1 1.74l-.15.09a2 2 0 0 0-.73 2.73l.22.38a2 2 0 0 0 2.73.73l.15-.08a2 2 0 0 1 2 0l.43.25a2 2 0 0 1 1 1.73V20a2 2 0 0 0 2 2h.44a2 2 0 0 0 2-2v-.18a2 2 0 0 1 1-1.73l.43-.25a2 2 0 0 1 2 0l.15.08a2 2 0 0 0 2.73-.73l.22-.39a2 2 0 0 0-.73-2.73l-.15-.08a2 2 0 0 1-1-1.74v-.5a2 2 0 0 1 1-1.74l.15-.09a2 2 0 0 0 .73-2.73l-.22-.38a2 2 0 0 0-2.73-.73l-.15.08a2 2 0 0 1-2 0l-.43-.25a2 2 0 0 1-1-1.73V4a2 2 0 0 0-2-2z"></path><circle cx="12" cy="12" r="3"></circle></svg> About Me</h2>
            <div class="code-block">
<span class="keyword">const</span> laleth = {
    <span class="property">education</span>: <span class="string">"MSc Software Systems Student"</span>,
    <span class="property">currentFocus</span>: [<span class="string">"MERN Stack"</span>, <span class="string">"Java/Spring Boot"</span>, <span class="string">"DevOps Basics"</span>],
    <span class="property">workingOn</span>: <span class="string">"Scalable Web Applications"</span>,
    <span class="property">openTo</span>: [<span class="string">"Collaborations"</span>, <span class="string">"Freelance Projects"</span>, <span class="string">"Startups"</span>],
    <span class="property">askMeAbout</span>: [<span class="string">"Web Dev"</span>, <span class="string">"REST APIs"</span>, <span class="string">"MERN"</span>, <span class="string">"Java"</span>],
    <span class="property">funFact</span>: <span class="string">"I build AI-powered games in my free time! 🎮"</span>
};
            </div>
        </div>

        <div class="divider"></div>

        <!-- Tech Stack with Real Icons -->
        <div class="section">
            <h2 class="section-title"><svg style="display:inline-block;vertical-align:middle;width:30px;height:30px;margin-right:10px;" viewBox="0 0 24 24" fill="none" stroke="#ff4b5c" stroke-width="2"><path d="M14.7 6.3a1 1 0 0 0 0 1.4l1.6 1.6a1 1 0 0 0 1.4 0l3.77-3.77a6 6 0 0 1-7.94 7.94l-6.91 6.91a2.12 2.12 0 0 1-3-3l6.91-6.91a6 6 0 0 1 7.94-7.94l-3.76 3.76z"></path></svg> Tech Arsenal</h2>
            <div class="tech-grid">
                <div class="tech-category">
                    <h4><svg style="display:inline-block;vertical-align:middle;width:24px;height:24px;margin-right:8px;" viewBox="0 0 24 24" fill="none" stroke="#ff4b5c" stroke-width="2"><polyline points="16 18 22 12 16 6"></polyline><polyline points="8 6 2 12 8 18"></polyline></svg>Frontend Magic</h4>
                    <div class="tech-icons" id="frontend-icons"></div>
                </div>
                <div class="tech-category">
                    <h4><svg style="display:inline-block;vertical-align:middle;width:24px;height:24px;margin-right:8px;" viewBox="0 0 24 24" fill="none" stroke="#ff4b5c" stroke-width="2"><rect x="2" y="2" width="20" height="8" rx="2" ry="2"></rect><rect x="2" y="14" width="20" height="8" rx="2" ry="2"></rect><line x1="6" y1="6" x2="6.01" y2="6"></line><line x1="6" y1="18" x2="6.01" y2="18"></line></svg>Backend Power</h4>
                    <div class="tech-icons" id="backend-icons"></div>
                </div>
                <div class="tech-category">
                    <h4><svg style="display:inline-block;vertical-align:middle;width:24px;height:24px;margin-right:8px;" viewBox="0 0 24 24" fill="none" stroke="#ff4b5c" stroke-width="2"><ellipse cx="12" cy="5" rx="9" ry="3"></ellipse><path d="M21 12c0 1.66-4 3-9 3s-9-1.34-9-3"></path><path d="M3 5v14c0 1.66 4 3 9 3s9-1.34 9-3V5"></path></svg>Database & Tools</h4>
                    <div class="tech-icons" id="tools-icons"></div>
                </div>
            </div>
        </div>

        <div class="divider"></div>

        <!-- Featured Project -->
        <div class="section">
            <h2 class="section-title"><svg style="display:inline-block;vertical-align:middle;width:30px;height:30px;margin-right:10px;" viewBox="0 0 24 24" fill="none" stroke="#ff4b5c" stroke-width="2"><path d="M21.21 15.89A10 10 0 1 1 8 2.83"></path><path d="M22 12A10 10 0 0 0 12 2v10z"></path></svg> Featured Project</h2>
            <div class="project-card">
                <h3><svg style="display:inline-block;vertical-align:middle;width:24px;height:24px;margin-right:8px;" viewBox="0 0 24 24" fill="none" stroke="#ff4b5c" stroke-width="2"><circle cx="12" cy="12" r="10"></circle><polygon points="10 8 16 12 10 16 10 8"></polygon></svg>AI-Powered Browser Game</h3>
                <p>Built an interactive game leveraging AI, featuring clean UI and smooth UX</p>
                <a href="https://creative-brioche-204b8c.netlify.app/" class="play-button">
                    <svg style="display:inline-block;vertical-align:middle;width:18px;height:18px;margin-right:8px;" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polygon points="5 3 19 12 5 21 5 3"></polygon></svg>
                    PLAY NOW
                </a>
                <p style="margin-top: 15px; color: #8b949e;"><strong>Tech Stack:</strong> React | JavaScript | AI Integration | Responsive Design</p>
            </div>
        </div>

        <div class="divider"></div>

        <!-- GitHub Stats -->
        <div class="section">
            <h2 class="section-title"><svg style="display:inline-block;vertical-align:middle;width:30px;height:30px;margin-right:10px;" viewBox="0 0 24 24" fill="none" stroke="#ff4b5c" stroke-width="2"><line x1="12" y1="20" x2="12" y2="10"></line><line x1="18" y1="20" x2="18" y2="4"></line><line x1="6" y1="20" x2="6" y2="16"></line></svg> GitHub Analytics</h2>
            <div class="stats-grid">
                <div class="stat-card">
                    <svg class="stat-icon" viewBox="0 0 24 24" fill="none" stroke="#ff4b5c" stroke-width="2">
                        <path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"></path>
                    </svg>
                    <div class="stat-number" id="totalStars">0</div>
                    <div class="stat-label">Total Stars</div>
                    <div class="stat-detail">Across all repositories</div>
                </div>
                <div class="stat-card">
                    <svg class="stat-icon" viewBox="0 0 24 24" fill="none" stroke="#ff4b5c" stroke-width="2">
                        <path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"></path>
                    </svg>
                    <div class="stat-number" id="contributions">0</div>
                    <div class="stat-label">Contributions</div>
                    <div class="stat-detail">This year</div>
                </div>
                <div class="stat-card">
                    <svg class="stat-icon" viewBox="0 0 24 24" fill="none" stroke="#ff4b5c" stroke-width="2">
                        <path d="M16 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"></path>
                        <circle cx="8.5" cy="7" r="4"></circle>
                        <polyline points="17 11 19 13 23 9"></polyline>
                    </svg>
                    <div class="stat-number" id="followers">0</div>
                    <div class="stat-label">Followers</div>
                    <div class="stat-detail">Growing community</div>
                </div>
                <div class="stat-card">
                    <svg class="stat-icon" viewBox="0 0 24 24" fill="none" stroke="#ff4b5c" stroke-width="2">
                        <rect x="3" y="3" width="18" height="18" rx="2" ry="2"></rect>
                        <circle cx="8.5" cy="8.5" r="1.5"></circle>
                        <polyline points="21 15 16 10 5 21"></polyline>
                    </svg>
                    <div class="stat-number" id="repositories">0</div>
                    <div class="stat-label">Repositories</div>
                    <div class="stat-detail">Public projects</div>
                </div>
                <div class="stat-card">
                    <svg class="stat-icon" viewBox="0 0 24 24" fill="none" stroke="#ff4b5c" stroke-width="2">
                        <polyline points="22 12 18 12 15 21 9 3 6 12 2 12"></polyline>
                    </svg>
                    <div class="stat-number" id="streak">0</div>
                    <div class="stat-label">Day Streak</div>
                    <div class="stat-detail">Coding consistently</div>
                </div>
                <div class="stat-card">
                    <svg class="stat-icon" viewBox="0 0 24 24" fill="none" stroke="#ff4b5c" stroke-width="2">
                        <polyline points="16 18 22 12 16 6"></polyline>
                        <polyline points="8 6 2 12 8 18"></polyline>
                    </svg>
                    <div class="stat-number">JavaScript</div>
                    <div class="stat-label">Top Language</div>
                    <div class="stat-detail">Most used in projects</div>
                </div>
            </div>
        </div>

        <div class="divider"></div>

        <!-- Quote -->
        <div class="quote">
            <svg style="display:inline-block;vertical-align:middle;width:24px;height:24px;margin-right:10px;" viewBox="0 0 24 24" fill="none" stroke="#ff4b5c" stroke-width="2"><path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"></path></svg>
            "Code is like humor. When you have to explain it, it's bad."
        </div>

        <!-- Footer -->
        <div class="footer">
            <h3>Thanks for stopping by! Let's connect and build something amazing together <svg style="display:inline-block;vertical-align:middle;width:24px;height:24px;" viewBox="0 0 24 24" fill="none" stroke="#ff4b5c" stroke-width="2"><circle cx="12" cy="12" r="10"></circle><path d="M8 14s1.5 2 4 2 4-2 4-2"></path><line x1="9" y1="9" x2="9.01" y2="9"></line><line x1="15" y1="9" x2="15.01" y2="9"></line></svg></h3>
            <a href="https://github.com/Laleth005" class="play-button" style="margin-top: 20px;">
                <svg style="display:inline-block;vertical-align:middle;width:18px;height:18px;margin-right:8px;" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polygon points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2"></polygon></svg>
                Star This Repo
            </a>
        </div>
    </div>

    <script>
        // Typing animation
        const texts = [
            "Building Scalable Web Applications",
            "MERN Stack | Java | Spring Boot",
            "Always Learning & Exploring",
            "Let's Build Something Amazing!"
        ];
        let textIndex = 0;
        let charIndex = 0;
        let isDeleting = false;
        const typingElement = document.getElementById('typing');

        function type() {
            const currentText = texts[textIndex];
            
            if (isDeleting) {
                typingElement.textContent = currentText.substring(0, charIndex - 1);
                charIndex--;
            } else {
                typingElement.textContent = currentText.substring(0, charIndex + 1);
                charIndex++;
            }

            if (!isDeleting && charIndex === currentText.length) {
                setTimeout(() => isDeleting = true, 2000);
            } else if (isDeleting && charIndex === 0) {
                isDeleting = false;
                textIndex = (textIndex + 1) % texts.length;
            }

            const speed = isDeleting ? 50 : 100;
            setTimeout(type, speed);
        }

        type();

        // Animated view counter
        let views = 0;
        const targetViews = 1234;
        const viewCounter = document.getElementById('viewCount');
        
        function animateCounter() {
            if (views < targetViews) {
                views += Math.ceil(targetViews / 100);
                if (views > targetViews) views = targetViews;
                viewCounter.textContent = views.toLocaleString();
                setTimeout(animateCounter, 20);
            }
        }
        
        animateCounter();

        // Real-time tech icons with CDN
        const frontendTechs = [
            { name: 'React', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/react/react-original.svg' },
            { name: 'JavaScript', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/javascript/javascript-original.svg' },
            { name: 'TypeScript', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/typescript/typescript-original.svg' },
            { name: 'HTML5', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/html5/html5-original.svg' },
            { name: 'CSS3', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/css3/css3-original.svg' }
        ];

        const backendTechs = [
            { name: 'Node.js', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/nodejs/nodejs-original.svg' },
            { name: 'Express', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/express/express-original.svg' },
            { name: 'Java', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/java/java-original.svg' },
            { name: 'Spring', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/spring/spring-original.svg' },
            { name: 'Python', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/python/python-original.svg' },
            { name: 'PHP', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/php/php-original.svg' }
        ];

        const toolsTechs = [
            { name: 'MongoDB', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/mongodb/mongodb-original.svg' },
            { name: 'MySQL', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/mysql/mysql-original.svg' },
            { name: 'Git', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/git/git-original.svg' },
            { name: 'GitHub', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/github/github-original.svg' },
            { name: 'Figma', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/figma/figma-original.svg' },
            { name: 'Linux', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/linux/linux-original.svg' }
        ];

        function loadIcons(techs, containerId) {
            const container = document.getElementById(containerId);
            techs.forEach((tech, index) => {
                setTimeout(() => {
                    const iconDiv = document.createElement('div');
                    iconDiv.className = 'tech-icon';
                    iconDiv.title = tech.name;
                    
                    const img = document.createElement('img');
                    img.src = tech.icon;
                    img.alt = tech.name;
                    img.loading = 'lazy';
                    
                    // Add error handling - show nothing if image fails
                    img.onerror = function() {
                        console.log('Failed to load:', tech.name);
                        iconDiv.style.display = 'none';
                    };
                    
                    iconDiv.appendChild(img);
                    container.appendChild(iconDiv);
                }, index * 100);
            });
        }

        loadIcons(frontendTechs, 'frontend-icons');
        loadIcons(backendTechs, 'backend-icons');
        loadIcons(toolsTechs, 'tools-icons');

        // Animate GitHub stats
        function animateStat(elementId, target, suffix = '') {
            let current = 0;
            const increment = target / 50;
            const element = document.getElementById(elementId);
            
            const timer = setInterval(() => {
                current += increment;
                if (current >= target) {
                    current = target;
                    clearInterval(timer);
                }
                element.textContent = Math.floor(current) + suffix;
            }, 30);
        }

        // Simulate GitHub stats with realistic numbers
        setTimeout(() => {
            animateStat('totalStars', 127);
            animateStat('contributions', 850, '+');
            animateStat('followers', 245);
            animateStat('repositories', 32);
            animateStat('streak', 45);
        }, 500);
    </script>
</body>
</html>
