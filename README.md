<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fatima Zahra Khouya - Portfolio</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #333;
            background: linear-gradient(135deg, #6366f1 0%, #8b5cf6 100%);
            scroll-behavior: smooth;
            min-height: 100vh;
        }

        /* Navigation */
        .navbar {
            position: fixed;
            top: 0;
            width: 100%;
            background: rgba(30, 41, 59, 0.95);
            backdrop-filter: blur(10px);
            z-index: 1000;
            padding: 15px 0;
            transition: all 0.3s ease;
        }

        .navbar.scrolled {
            background: rgba(30, 41, 59, 0.98);
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
        }

        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 20px;
        }

        .logo {
            color: white;
            font-size: 1.5rem;
            font-weight: bold;
        }

        .nav-menu {
            display: flex;
            list-style: none;
            gap: 30px;
        }

        .nav-menu a {
            color: white;
            text-decoration: none;
            transition: color 0.3s ease;
            position: relative;
        }

        .nav-menu a:hover {
            color: #6366f1;
        }

        .nav-menu a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: #6366f1;
            transition: width 0.3s ease;
        }

        .nav-menu a:hover::after {
            width: 100%;
        }

        .mobile-menu-btn {
            display: none;
            background: none;
            border: none;
            color: white;
            font-size: 1.5rem;
            cursor: pointer;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: white;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
            border-radius: 20px;
            overflow: hidden;
            margin-top: 80px;
            margin-bottom: 20px;
            animation: fadeInUp 1s ease forwards;
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(50px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .header {
            background: linear-gradient(135deg, #1e293b 0%, #334155 100%);
            color: white;
            padding: 80px 40px 60px;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .header::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(255,255,255,0.1) 0%, transparent 70%);
            animation: float 6s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translate(-50%, -50%) rotate(0deg); }
            50% { transform: translate(-50%, -50%) rotate(180deg); }
        }

        .profile-img {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            border: 5px solid rgba(255,255,255,0.3);
            margin: 0 auto 20px;
            background: #4a5568;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 48px;
            color: white;
            position: relative;
            z-index: 2;
            transition: transform 0.3s ease;
        }

        .profile-img:hover {
            transform: scale(1.05);
        }

        .header h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
            position: relative;
            z-index: 2;
        }

        .header p {
            font-size: 1.2rem;
            opacity: 0.9;
            position: relative;
            z-index: 2;
        }

        .contact-info {
            margin-top: 20px;
            position: relative;
            z-index: 2;
        }

        .contact-info span {
            display: inline-block;
            margin: 0 15px;
            opacity: 0.8;
            transition: opacity 0.3s ease;
            cursor: pointer;
        }

        .contact-info span:hover {
            opacity: 1;
        }

        .main-content {
            padding: 40px;
        }

        .section {
            margin-bottom: 40px;
        }

        .section h2 {
            color: #1e293b;
            border-bottom: 3px solid #6366f1;
            padding-bottom: 10px;
            margin-bottom: 25px;
            font-size: 1.8rem;
            position: relative;
        }

        .section h2::after {
            content: '';
            position: absolute;
            bottom: -3px;
            left: 0;
            width: 50px;
            height: 3px;
            background: #8b5cf6;
            border-radius: 2px;
        }

        .experience-item, .education-item {
            background: white;
            padding: 25px;
            margin-bottom: 20px;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.08);
            border-left: 4px solid #6366f1;
            transition: all 0.3s ease;
        }

        .experience-item:hover, .education-item:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0,0,0,0.15);
        }

        .item-header {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            margin-bottom: 15px;
        }

        .item-title {
            font-weight: bold;
            color: #1e293b;
            font-size: 1.1rem;
        }

        .item-date {
            background: #6366f1;
            color: white;
            padding: 5px 12px;
            border-radius: 15px;
            font-size: 0.9rem;
            white-space: nowrap;
        }

        .item-company {
            color: #7f8c8d;
            font-style: italic;
            margin-bottom: 10px;
        }

        /* Skills with animation */
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
        }

        .skill-category {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 3px 10px rgba(0,0,0,0.05);
            transition: transform 0.3s ease;
        }

        .skill-category:hover {
            transform: translateY(-5px);
        }

        .skill-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
        }

        .skill-dots {
            display: flex;
            gap: 3px;
        }

        .dot {
            width: 8px;
            height: 8px;
            border-radius: 50%;
            background: #ecf0f1;
            transition: all 0.3s ease;
        }

        .dot.filled {
            background: #6366f1;
        }

        /* Certifications */
        .certification {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 20px;
            margin: 15px 0;
            border-radius: 12px;
            box-shadow: 0 8px 25px rgba(0,0,0,0.15);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .certification::before {
            content: '';
            position: absolute;
            top: 0;
            right: -50px;
            width: 100px;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.1));
            transform: skewX(-20deg);
        }

        .certification:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 35px rgba(0,0,0,0.2);
        }

        .certification h4 {
            color: #fff;
            font-size: 22px;
            margin-bottom: 10px;
            font-weight: bold;
            position: relative;
            z-index: 2;
        }

        .certification p {
            color: rgba(255,255,255,0.9);
            font-size: 16px;
            line-height: 1.6;
            margin: 0;
            position: relative;
            z-index: 2;
        }

        .academic-certification {
            background: linear-gradient(135deg, #f39c12 0%, #e67e22 100%);
        }

        .web-certification {
            background: linear-gradient(135deg, #2ecc71 0%, #27ae60 100%);
        }

        .certification-badge {
            position: absolute;
            top: 15px;
            right: 15px;
            background: rgba(255,255,255,0.2);
            color: white;
            padding: 5px 12px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: bold;
            text-transform: uppercase;
        }

        /* Contact Section */
        .contact-section {
            background: linear-gradient(135deg, #1e293b 0%, #334155 100%);
            color: white;
            padding: 60px 40px;
            margin: 40px 0 0 0;
            border-radius: 0 0 20px 20px;
        }

        .contact-form {
            max-width: 600px;
            margin: 0 auto;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
        }

        .form-group input,
        .form-group textarea {
            width: 100%;
            padding: 12px;
            border: none;
            border-radius: 8px;
            background: rgba(255,255,255,0.1);
            color: white;
            border: 2px solid transparent;
            transition: all 0.3s ease;
        }

        .form-group input::placeholder,
        .form-group textarea::placeholder {
            color: rgba(255,255,255,0.7);
        }

        .form-group input:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: #6366f1;
            background: rgba(255,255,255,0.15);
        }

        .btn-submit {
            background: linear-gradient(135deg, #6366f1 0%, #8b5cf6 100%);
            color: white;
            padding: 15px 40px;
            border: none;
            border-radius: 25px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            width: 100%;
        }

        .btn-submit:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 25px rgba(99, 102, 241, 0.3);
        }

        .contact-info-section {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 30px;
            margin-bottom: 40px;
        }

        .contact-item {
            text-align: center;
            padding: 20px;
            background: rgba(255,255,255,0.1);
            border-radius: 10px;
            transition: transform 0.3s ease;
        }

        .contact-item:hover {
            transform: translateY(-5px);
        }

        .contact-item i {
            font-size: 2rem;
            margin-bottom: 15px;
            color: #6366f1;
        }

        /* Progress bar for page loading */
        .progress-bar {
            position: fixed;
            top: 0;
            left: 0;
            width: 0%;
            height: 3px;
            background: linear-gradient(90deg, #6366f1, #8b5cf6);
            z-index: 9999;
            transition: width 0.3s ease;
        }

        /* Scroll to top button */
        .scroll-to-top {
            position: fixed;
            bottom: 30px;
            right: 30px;
            background: linear-gradient(135deg, #6366f1 0%, #8b5cf6 100%);
            color: white;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            border: none;
            cursor: pointer;
            font-size: 1.2rem;
            opacity: 0;
            transform: translateY(100px);
            transition: all 0.3s ease;
            z-index: 1000;
        }

        .scroll-to-top.show {
            opacity: 1;
            transform: translateY(0);
        }

        .scroll-to-top:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(99, 102, 241, 0.3);
        }

        /* Success message */
        .success-message {
            background: #2ecc71;
            color: white;
            padding: 15px;
            border-radius: 8px;
            margin-top: 20px;
            display: none;
            animation: slideIn 0.5s ease;
        }

        @keyframes slideIn {
            from { opacity: 0; transform: translateY(-20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Mobile Responsive */
        @media (max-width: 768px) {
            .nav-menu {
                position: fixed;
                top: 70px;
                left: -100%;
                width: 100%;
                height: calc(100vh - 70px);
                background: rgba(30, 41, 59, 0.98);
                flex-direction: column;
                justify-content: start;
                align-items: center;
                padding-top: 50px;
                transition: left 0.3s ease;
            }

            .nav-menu.active {
                left: 0;
            }

            .mobile-menu-btn {
                display: block;
            }

            .container {
                margin-top: 70px;
            }

            .header {
                padding: 60px 20px 40px;
            }

            .header h1 {
                font-size: 2rem;
            }

            .contact-info span {
                display: block;
                margin: 5px 0;
            }

            .main-content {
                padding: 20px;
            }

            .contact-section {
                padding: 40px 20px;
            }
        }

        .languages, .interests {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 3px 10px rgba(0,0,0,0.05);
            margin-bottom: 20px;
        }

        .interests ul {
            list-style: none;
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
        }

        .interests li {
            background: #3498db;
            color: white;
            padding: 8px 15px;
            border-radius: 20px;
            font-size: 0.9rem;
            transition: transform 0.3s ease;
        }

        .interests li:hover {
            transform: scale(1.05);
        }
    </style>
</head>
<body>
    <!-- Progress Bar -->
    <div class="progress-bar"></div>

    <!-- Navigation -->
    <nav class="navbar">
        <div class="nav-container">
            <div class="logo">FZ Portfolio</div>
            <ul class="nav-menu">
                <li><a href="#profil">Profil</a></li>
                <li><a href="#competences">Compétences</a></li>
                <li><a href="#experience">Expérience</a></li>
                <li><a href="#education">Éducation</a></li>
                <li><a href="#certifications">Certifications</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
            <button class="mobile-menu-btn">☰</button>
        </div>
    </nav>

    <div class="container">
        <header class="header">
            <div class="profile-img">FZ</div>
            <h1>Fatima Zahra Khouya</h1>
            <p>Professionnelle en Formation Bureautique & Technologies</p>
            <div class="contact-info">
                <span onclick="copyEmail()">📧 khouya99fat@gmail.com</span>
                <span onclick="copyPhone()">📱 0698179349</span>
            </div>
        </header>

        <div class="main-content">
            <section id="profil" class="section">
                <h2>Profil Professionnel</h2>
                <p>Diplômée de la Faculté Pluridisciplinaire de Errachidia en spécialité littérature arabe, je suis passionnée par les nouvelles technologies, notamment dans le domaine de la formation bureautique. Fort d'un certificat en formation bureautique de l'Institut de Studyrama leader de formation professionnelle Errachidia, j'ai acquis une solide expérience dans le secteur. Mes compétences clés incluent une maîtrise avancée des outils de bureautique, une capacité d'adaptation rapide aux nouvelles technologies et une forte motivation à relever de nouveaux défis.</p>
            </section>

            <section id="competences" class="section">
                <h2>Compétences</h2>
                <div class="skills-grid">
                    <div class="skill-category">
                        <h3>Bureautique</h3>
                        <div class="skill-item">
                            <span>Microsoft Word</span>
                            <div class="skill-dots">
                                <span class="dot filled"></span>
                                <span class="dot filled"></span>
                                <span class="dot filled"></span>
                                <span class="dot filled"></span>
                                <span class="dot"></span>
                            </div>
                        </div>
                        <div class="skill-item">
                            <span>Microsoft Excel</span>
                            <div class="skill-dots">
                                <span class="dot filled"></span>
                                <span class="dot filled"></span>
                                <span class="dot filled"></span>
                                <span class="dot filled"></span>
                                <span class="dot"></span>
                            </div>
                        </div>
                        <div class="skill-item">
                            <span>PowerPoint</span>
                            <div class="skill-dots">
                                <span class="dot filled"></span>
                                <span class="dot filled"></span>
                                <span class="dot filled"></span>
                                <span class="dot filled"></span>
                                <span class="dot"></span>
                            </div>
                        </div>
                    </div>
                    
                    <div class="skill-category">
                        <h3>Travail d'équipe</h3>
                        <div class="skill-item">
                            <span>Collaboration</span>
                            <div class="skill-dots">
                                <span class="dot filled"></span>
                                <span class="dot filled"></span>
                                <span class="dot filled"></span>
                                <span class="dot filled"></span>
                                <span class="dot filled"></span>
                            </div>
                        </div>
                    </div>
                </div>
            </section>

            <section id="experience" class="section">
                <h2>Expériences Professionnelles</h2>
                
                <div class="experience-item">
                    <div class="item-header">
                        <div>
                            <div class="item-title">Attestation de formation bureautique</div>
                            <div class="item-company">Studyrama leader de formation professionnelle Errachidia</div>
                        </div>
                        <div class="item-date">2021</div>
                    </div>
                </div>

                <div class="experience-item">
                    <div class="item-header">
                        <div>
                            <div class="item-title">Attestation de formation des sauviteurs par le croisement rouge</div>
                            <div class="item-company">Errachidia</div>
                        </div>
                        <div class="item-date">2022</div>
                    </div>
                </div>

                <div class="experience-item">
                    <div class="item-header">
                        <div>
                            <div class="item-title">Formation sur la gestion administrative et financière des associations</div>
                            <div class="item-company">Association taymat m'ssici - Certificat de participation</div>
                        </div>
                        <div class="item-date">2023</div>
                    </div>
                    <p>Techniques de réalisation de projet et la recherche de sources de financement.</p>
                </div>

                <div class="experience-item">
                    <div class="item-header">
                        <div>
                            <div class="item-title">Stage pédagogique de l'enseignement de la langue arabe au cycle primaire</div>
                            <div class="item-company">TINGHIR</div>
                        </div>
                        <div class="item-date">2024/2025</div>
                    </div>
                    <p>Du 11/02/2025 au 12/05/2025</p>
                </div>

                <div class="experience-item">
                    <div class="item-header">
                        <div>
                            <div class="item-title">Travail dans le cadre du programme gouvernemental (AWRASC 2)</div>
                            <div class="item-company">TINGHIR</div>
                        </div>
                        <div class="item-date">Actuel</div>
                    </div>
                    <p>Ateliers de l'accueil et d'orientation sanitaire dans les différents centres du 01/12/2023 au 31/03/2024</p>
                </div>
            </section>

            <section id="education" class="section">
                <h2>Éducation</h2>
                
                <div class="education-item">
                    <div class="item-header">
                        <div>
                            <div class="item-title">Baccalauréat en lettres et sciences humaines</div>
                            <div class="item-company">Lycée Mohamed VI Alnif</div>
                        </div>
                        <div class="item-date">2010</div>
                    </div>
                </div>

                <div class="education-item">
                    <div class="item-header">
                        <div>
                            <div class="item-title">Licence fondamentale option littérature arabe</div>
                            <div class="item-company">Faculté Polydisciplinaire Errachidia</div>
                        </div>
                        <div class="item-date">2022</div>
                    </div>
                </div>
            </section>

            <section id="certifications" class="section">
                <h2>🎓 Certifications</h2>
                
                <div class="certification academic-certification">
                    <div class="certification-badge">Académique</div>
                    <h4>🎓 Baccalauréat</h4>
                    <p>Diplôme d'études secondaires - Certificat de réussite aux examens nationaux</p>
                </div>

                <div class="certification academic-certification">
                    <div class="certification-badge">Universitaire</div>
                    <h4>📚 Licence Fondamentale - Option Littérature Arabe</h4>
                    <p>Diplôme universitaire en littérature arabe - Maîtrise des œuvres classiques et contemporaines de la littérature arabe</p>
                </div>

                <div class="certification web-certification">
                    <div class="certification-badge">Professionnel</div>
                    <h4>💻 Certification Responsive Web Design</h4>
                    <p>WEBJOBS - Formation spécialisée en conception web responsive, maîtrise des techniques modernes de développement web adaptatif</p>
                </div>
            </section>

            <section class="section">
                <h2>Langues</h2>
                <div class="languages">
                    <div class="skill-item">
                        <span>Tamazight</span>
                        <div class="skill-dots">
                            <span class="dot filled"></span>
                            <span class="dot filled"></span>
                            <span class="dot filled"></span>
                            <span class="dot filled"></span>
                            <span class="dot filled"></span>
                        </div>
                    </div>
                    <div class="skill-item">
                        <span>Français</span>
                        <div class="skill-dots">
                            <span class="dot filled"></span>
                            <span class="dot filled"></span>
                            <span class="dot filled"></span>
                            <span class="dot filled"></span>
                            <span class="dot"></span>
                        </div>
                    </div>
                    <div class="skill-item">
                        <span>Arabe</span>
                        <div class="skill-dots">
                            <span class="dot filled"></span>
                            <span class="dot filled"></span>
                            <span class="dot filled"></span>
                            <span class="dot filled"></span>
                            <span class="dot"></span>
                        </div>
                    </div>
                    <div class="skill-item">
                        <span>English</span>
                        <div class="skill-dots">
                            <span class="dot filled"></span>
                            <span class="dot filled"></span>
                            <span class="dot filled"></span>
                            <span class="dot"></span>
                            <span class="dot"></span>
                        </div>
                    </div>
                </div>
            </section>

            <section class="section">
                <h2>Centres d'Intérêt</h2>
                <div class="interests">
                    <ul>
                        <li>🎵 Musique</li>
                        <li>✈️ Voyage</li>
                        <li>⚽ Sports</li>
                    </ul>
                </div>
            </section>
        </div>

        <!-- Contact Section -->
        <section id="contact" class="contact-section">
            <h2 style="text-align: center; margin-bottom: 40px; color: white;">Contactez-moi</h2>
            
            <div class="contact-info-section">
                <div class="contact-item">
                    <div style="font-size: 2rem; margin-bottom: 15px;">📧</div>
                    <h3>Email</h3>
                    <p>khouya99fat@gmail.com</p>
                </div>
                <div class="contact-item">
                    <div style="font-size: 2rem; margin-bottom: 15px;">📱</div>
                    <h3>Téléphone</h3>
                    <p>0698179349</p>
                </div>
                <div class="contact-item">
                    <div style="font-size: 2rem; margin-bottom: 15px;">📍</div>
                    <h3>Localisation</h3>
                    <p>Errachidia, Maroc</p>
                </div>
            </div>

            <div class="contact-form">
                <form id="contactForm">
                    <div class="form-group">
                        <label for="name">Nom complet</label>
                        <input type="text" id="name" name="name" placeholder="Votre nom complet" required>
                    </div>
                    <div class="form-group">
                        <label for="email">Email</label>
                        <input type="email" id="email" name="email" placeholder="votre.email@exemple.com" required>
                    </div>
                    <div class="form-group">
                        <label for="subject">Sujet</label>
                        <input type="text" id="subject" name="subject" placeholder="Sujet de votre message" required>
                    </div>
                    <div class="form-group">
                        <label for="message">Message</label>
                        <textarea id="message" name="message" rows="5" placeholder="Votre message..." required></textarea>
                    </div>
                    <button type
