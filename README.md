<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Portfolio</title>
    <style>
        body {
            font-family: sans-serif;
            margin: 0;
            background-color: #f4f4f4;
            color: #333;
            overflow-x: hidden;
        }

        .sidebar {
            background-color: #222;
            color: #fff;
            width: 250px;
            height: 100vh;
            position: fixed;
            top: 0;
            left: 0;
            padding: 20px;
            box-sizing: border-box;
            display: flex;
            flex-direction: column;
            align-items: center;
            z-index: 10;
            overflow-y: auto; /* Enable scrolling for long sidebars */
        }

        .profile-image-container {
            width: 120px;
            height: 120px;
            border-radius: 50%;
            overflow: hidden;
            margin-bottom: 15px;
            border: 3px solid #eee;
            opacity: 0;
            transform: translateY(-20px);
            animation: slideIn 0.8s ease-out 0.3s forwards;
        }

        .profile-image-container img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .name-container {
            position: relative;
            margin-bottom: 5px;
            text-align: center;
            opacity: 0;
            transform: translateY(-10px);
            animation: fadeIn 0.5s ease-out 0.6s forwards;
        }

        .name {
            font-size: 1.5em;
            font-weight: bold;
            color: #fff; /* Default text color */
            padding: 5px 10px;
            border-radius: 5px; /* Optional rounded corners */
            display: inline-block; /* To contain the background */
        }

        .name-background {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: url('name_background.jpg'); /* Replace with your image path */
            background-size: cover;
            background-position: center;
            z-index: -1; /* Place behind the text */
            border-radius: 5px; /* Match text container */
        }

        .title {
            font-size: 0.9em;
            color: #ccc;
            margin-bottom: 20px;
            text-align: center;
            opacity: 0;
            transform: translateY(-10px);
            animation: fadeIn 0.5s ease-out 0.8s forwards;
            <bg></bg>
        }

        .nav-links {
            list-style: none;
            padding: 0;
            width: 100%;
            opacity: 0;
            animation: fadeIn 0.5s ease-out 1s forwards;
        }

        .nav-links li {
            margin-bottom: 10px;
        }

        .nav-links a {
            display: block;
            color: #fff;
            text-decoration: none;
            padding: 10px 15px;
            border-radius: 5px;
            transition: background-color 0.3s ease, transform 0.3s ease;
            transform: translateX(-10px);
        }

        .nav-links a:hover {
            background-color: #444;
            transform: translateX(5px);
        }

        .content {
            margin-left: 250px;
            padding: 20px;
            box-sizing: border-box;
            transition: margin-left 0.5s ease-in-out;
        }

        .hero {
            background-color: #fff;
            padding: 40px;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
            margin-bottom: 20px;
            text-align: center;
            opacity: 0;
            transform: translateY(20px);
            animation: slideUp 0.8s ease-out 0.2s forwards;
        }

        .hero h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
            animation: pulse 1.5s infinite alternate;
        }

        .hero p {
            font-size: 1.1em;
            color: #666;
            margin-bottom: 20px;
            animation: fadeIn 1s ease-out 0.5s forwards;
            opacity: 0;
        }

        .hero img {
            max-width: 100%;
            height: auto;
            border-radius: 8px;
            margin-top: 20px;
            animation: zoomIn 1s ease-out 0.8s forwards;
            opacity: 0;
        }

        .section {
            background-color: #c0c0c0;
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
            margin-bottom: 20px;
            opacity: 0;
            transform: translateX(-20px);
            animation: slideInLeft 0.7s ease-out forwards;
            margin-left: -20px;
        }

        .section:nth-child(even) {
            transform: translateX(20px);
            animation: slideInRight 0.7s ease-out forwards;
            margin-left: 0;
            margin-right: -20px;
        }

        .section h2 {
            font-size: 2em;
            margin-bottom: 15px;
            border-bottom: 2px solid #c2c2c2;
            padding-bottom: 10px;
            animation: scaleUp 0.6s ease-out 0.3s forwards;
            transform: scale(0);
            opacity: 0;
        }

        .project {
            margin-bottom: 20px;
            padding: 15px;
            border: 1px solid #ddd;
            border-radius: 5px;
            opacity: 0;
            transform: scale(0.9);
            animation: fadeInUp 0.5s ease-out forwards;
        }

        .project:nth-child(odd) {
            animation-delay: 0.2s;
        }

        .project:nth-child(even) {
            animation-delay: 0.4s;
        }

        .project h3 {
            margin-top: 0;
        }

        .certificate-section {
            background-color: #c0c0c0;
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
            margin-bottom: 20px;
            opacity: 0;
            transform: translateY(20px);
            animation: fadeInUp 0.7s ease-out forwards;
        }

        .certificate-section h2 {
            font-size: 2em;
            margin-bottom: 15px;
            border-bottom: 2px solid #eee;
            padding-bottom: 10px;
        }

        .certificate-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
        }

        .certificate-item {
            border: 1px solid #ddd;
            border-radius: 5px;
            padding: 15px;
            text-align: center;
        }

        .certificate-item img {
            max-width: 100%;
            height: auto;
            border-radius: 5px;
            margin-bottom: 10px;
        }

        .certificate-item h4 {
            margin-top: 0;
            font-size: 1.1em;
        }

        .certificate-item p {
            font-size: 0.9em;
            color: #666;
        }

        /* Animations */
        @keyframes slideIn {
            from { transform: translateY(-20px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @keyframes slideUp {
            from { transform: translateY(20px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        @keyframes slideInLeft {
            from { transform: translateX(-20px); opacity: 0; }
            to { transform: translateX(0); opacity: 1; }
        }

        @keyframes slideInRight {
            from { transform: translateX(20px); opacity: 0; }
            to { transform: translateX(0); opacity: 1; }
        }

        @keyframes scaleUp {
            from { transform: scale(0); opacity: 0; }
            to { transform: scale(1); opacity: 1; }
        }

        @keyframes fadeInUp {
            from { transform: translateY(20px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        @keyframes zoomIn {
            from { transform: scale(0.8); opacity: 0; }
            to { transform: scale(1); opacity: 1; }
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            100% { transform: scale(1.05); }
        }

        /* Responsive adjustments */
        @media (max-width: 768px) {
            .sidebar {
                width: 100%;
                height: auto;
                position: static;
                left: 0;
                flex-direction: row;
                justify-content: space-around;
                padding: 10px;
                align-items: center;
                z-index: 10;
                overflow-y: visible; /* Allow full height on smaller screens */
            }

            .profile-image-container {
                width: 60px;
                height: 60px;
                margin-bottom: 0;
            }

            .name-container, .title {
                display: none;
            }

            .nav-links {
                display: flex;
                width: auto;
            }

            .nav-links li {
                margin-bottom: 0;
                margin-left: 5px;
                margin-right: 5px;
            }

            .nav-links a {
                padding: 8px 12px;
                font-size: 0.9em;
            }

            .content {
                margin-left: 0;
                padding: 15px;
                transition: margin-left 0.5s ease-in-out;
            }

            .certificate-grid {
                grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
                gap: 10px;
            }

            .certificate-item {
                padding: 10px;
            }

            .certificate-item h4 {
                font-size: 1em;
                margin-bottom: 5px;
            }
        }
    </style>
</head>
<body>
    <div class="sidebar">
        <div class="profile-image-container">
            <img src="C:\Users\lenovo\Downloads\portfolio_profile.jpg" alt="chaitrali Ghodekar">
        </div>
        <div class="name-container">
            <h1 class="name">Chaitrali Ghodekar</h1>
            <div class="name-background"></div>
        </div>
        <p class="title">Mechanical Engineering Student</p>
        <ul class="nav-links">
            <li><a href="#home">Home</a></li>
            <li><a href="#about">About</a></li>
            <li><a href="#skills">Education</a></li>
            <li><a href="#skills">Skills</a></li>
            <li><a href="#achievements">Achievements</a></li>
            <li><a href="#certificates">Certificates</a></li> <li><a href="#contact">Contact</a></li>
        </ul>
    </div>

    <div class="content">
        <section id="home" class="hero">
            <h1>Chaitrali Ghodekar</h1>
            <p><b>A passionate Mechanical Engineering student dedicated to innovation and learning</b></p></p>
            
        </section>

        <section id="about" class="section">
            <h2>About Me</h2>
            <p>Hello,I'm Chaitrali Ghodekar, a first-year student embarking on my Mechanical Engineering journey at MIT Academy of Engineering.</p>
            <p> Beyond the world of mechanics, I'm also deeply engaged in fitness and possess a keen eye for design. This portfolio offers a glimpse into my initial engineering projects, coursework, and foundational skills, hinting at the interdisciplinary perspective I bring to problem-solving. I'm eager to explore the principles of mechanical engineering and discover potential connections with my other passions.</p>
        </section>

        <section id="Education" class="section">
            <h2>Education</h2>
            <p><b>Janhit Pratishthan, Baramati</b></p>
            <p>SSC- 94.4%</p>
            <p><b>Shri Siddeshwar Collage</b></p>
            <p>HSC- 72.0%</p>
            <p><b>MIT AOE</b></p>
            <p>B.Tech, Mechanical Engineering</p>
            </section>

        <section id="skills" class="section">
            <h2>Skills</h2>
            <ul>
                <li>HTML</li>
                <li>Python</li>
                <li>AutoCad</li>
                <li>Autodesk Fusion360</li>
            </ul>
        </section>

        
        <section id="achievements" class="section">
            <h2>Achievements</h2>
            <ul>
                <li>Completed an intensive <b>Python</b> programming course through Cisco, earning certification and demonstrating proficiency in the language.</li>
                <li>Completed <b>975 Surya Namaskars in one session</b>, showcasing significant physical endurance and dedication. This accomplishment highlights my capacity to push beyond conventional limits and maintain focus under demanding conditions.</li>
                </ul>
        </section>

        <section id="certificates" class="certificate-section">
            <h2>Certificates of Achievement</h2>
            <div class="certificate-grid">
                <div class="certificate-item">
                    <img src="C:\Users\lenovo\Downloads\ISRO_certificate.jpg" alt="Certificate 1">
                    <h4>Participation in Remote sensing & GIS for Environmental Studies course</h4>
                    <p>Issuing Organization:ISRO</p>
                    <p>06/08/2021</p>
                    </div>
                <div class="certificate-item">
                    <img src="C:\Users\lenovo\OneDrive\Desktop\Sem 2\chess.jpg" alt="Certificate 2">
                    <h4>Chess Certificate</h4>
                    <p>Issuing Organization:MITAOE</p>
                    <p>12/03/2025</p>
                </div>
                </div>
        </section>

        <section id="contact" class="section">
            <h2>Contact Me</h2>
            <p><b>Email:</b> c.ghodekar11@gmail.com</p>
            <p><b>LinkedIn</b>:www.linkedin.com/in/chaitrali-ghodekar</p>
            <p><b>GitHub:</b>https://github.com/cg11</p>
            </section>
    </div>

    <script>22
        // Basic 2smooth scrolling for navigation links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();

                document.querySelector(this.getAttribute('href')).scrollIntoView({
                    behavior: 'smooth'
                });
            });
        });

        // Initial animations on page load
        document.addEventListener('DOMContentLoaded', () => {
            const sections = document.querySelectorAll('.section');
            sections.forEach((section, index) => {
                section.style.animationDelay = `${index * 0.15 + 0.3}s`;
            });

            // Add animation to the certificate section
            const certificateSection = document.getElementById('certificates');
            if (certificateSection) {
                certificateSection.style.animationDelay = `calc(0.3s + ${sections.length * 0.15}s)`; // Appear after other sections
            }
        });
    </script>
</body>
</html># portfolio
