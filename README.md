<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Aditya's Portfolio</title>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500&family=Poppins:wght@300;500;700&display=swap" rel="stylesheet" />
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(to right, #0f2027, #203a43, #2c5364);
      color: #fff;
      overflow-x: hidden;
    }

    header {
      background: rgba(0, 0, 0, 0.7);
      padding: 1rem 2rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
      position: sticky;
      top: 0;
      z-index: 1000;
      box-shadow: 0 2px 10px rgba(0, 0, 0, 0.8);
    }

    .logo {
      font-family: 'Orbitron', sans-serif;
      font-size: 1.5rem;
      color: #00fff7;
    }

    header nav a {
      color: #00fff7;
      margin-left: 1.5rem;
      text-decoration: none;
      font-weight: 500;
      transition: color 0.3s;
    }

    header nav a:hover {
      color: #ff00ff;
    }

    .hero {
      text-align: center;
      padding: 5rem 2rem 3rem;
      position: relative;
    }

    .hero h1 {
      font-size: 3.5rem;
      font-family: 'Orbitron', sans-serif;
      color: #00fff7;
      animation: pulse 2s infinite;
    }

    .typing {
      color: #ffffff;
      font-size: 1.5rem;
      margin-top: 1rem;
      white-space: nowrap;
      overflow: hidden;
      border-right: 3px solid #fff;
      width: 0;
      animation: typing 4s steps(40, end) forwards, blink 0.7s infinite;
      display: inline-block;
      max-width: 100%;
    }

    section {
      padding: 4rem 2rem;
      max-width: 1100px;
      margin: auto;
      opacity: 0;
      transform: translateY(40px);
      transition: all 1s ease-in-out;
    }

    section.visible {
      opacity: 1;
      transform: translateY(0);
    }

    /* About Me Section */

    #about h2 {
      text-align: center;
      margin-bottom: 2rem;
      color: #00fff7;
      font-family: 'Orbitron', sans-serif;
      letter-spacing: 1.5px;
      font-size: 2.5rem;
    }

    .about-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 2rem;
    }

    .about-card {
      background: rgba(255, 255, 255, 0.07);
      padding: 1.8rem 2rem;
      border-radius: 20px;
      box-shadow: 0 0 15px rgba(0, 255, 255, 0.2);
      color: #ddd;
      font-size: 1.1rem;
      transition: transform 0.4s ease, box-shadow 0.4s ease;
      opacity: 0;
      transform: translateY(40px);
      cursor: default;
    }

    /* Different shapes */
    .about-card.intro {
      border-radius: 50% / 30%;
      background: rgba(0, 255, 255, 0.15);
      box-shadow: 0 0 30px #00fff7;
    }

    .about-card.skills {
      clip-path: polygon(10% 0%, 90% 0%, 100% 50%, 90% 100%, 10% 100%, 0% 50%);
      background: rgba(255, 0, 255, 0.15);
      box-shadow: 0 0 30px #ff00ff;
    }

    .about-card.hobbies {
      border-radius: 40px 0 40px 0;
      background: rgba(255, 255, 0, 0.15);
      box-shadow: 0 0 30px #ffff00;
      color: #222;
    }

    .about-card.role {
      clip-path: circle(55% at 50% 50%);
      background: rgba(0, 255, 128, 0.15);
      box-shadow: 0 0 30px #00ff80;
    }

    .about-card.goals {
      transform: skew(-10deg);
      background: rgba(255, 0, 128, 0.15);
      box-shadow: 0 0 30px #ff0080;
    }

    /* Headings style */
    .about-card h3 {
      margin-bottom: 1rem;
      color: #00fff7;
      font-family: 'Orbitron', sans-serif;
      font-size: 1.5rem;
      letter-spacing: 1.2px;
    }

    /* Hover effects */
    .about-card:hover {
      transform: scale(1.05);
      box-shadow: 0 0 50px #ff00ff;
    }

    /* Animate in with different directions */
    .about-card.visible.intro {
      opacity: 1;
      transform: translateY(0);
      transition-delay: 0.1s;
    }

    .about-card.visible.skills {
      opacity: 1;
      transform: translateX(0);
      transition-delay: 0.3s;
    }

    .about-card.visible.hobbies {
      opacity: 1;
      transform: translateX(0);
      transition-delay: 0.5s;
    }

    .about-card.visible.role {
      opacity: 1;
      transform: translateY(0);
      transition-delay: 0.7s;
    }

    .about-card.visible.goals {
      opacity: 1;
      transform: skew(0deg);
      transition-delay: 0.9s;
    }

    /* Projects Section */
    .projects {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 2rem;
      margin-top: 2rem;
    }

    .project-card {
      background: rgba(255, 255, 255, 0.05);
      padding: 1.5rem;
      border-radius: 12px;
      box-shadow: 0 0 20px rgba(0, 255, 255, 0.1);
      backdrop-filter: blur(10px);
      transition: transform 0.3s;
      cursor: default;
    }

    .project-card:hover {
      transform: scale(1.05);
      box-shadow: 0 0 25px rgba(255, 0, 255, 0.4);
    }

    .project-card h3 {
      color: #00fff7;
      margin-bottom: 0.5rem;
    }

    /* Contact Section */
    #contact h2 {
      color: #00fff7;
      font-family: 'Orbitron', sans-serif;
      letter-spacing: 1.5px;
      text-align: center;
      margin-bottom: 2rem;
    }

    .contact {
      text-align: center;
      font-size: 1.2rem;
      line-height: 2rem;
    }

    .contact a {
      color: #00fff7;
      text-decoration: none;
      font-weight: 500;
      transition: color 0.3s;
    }

    .contact a:hover {
      color: #ff00ff;
    }

    footer {
      text-align: center;
      padding: 2rem;
      font-size: 0.9rem;
      color: #bbb;
    }

    @keyframes typing {
      to {
        width: 100%;
      }
    }

    @keyframes blink {
      50% {
        border-color: transparent;
      }
    }

    @keyframes pulse {
      0%,
      100% {
        transform: scale(1);
      }
      50% {
        transform: scale(1.05);
      }
    }
  </style>
</head>
<body>
  <header>
    <div class="logo">Aditya</div>
    <nav>
      <a href="#home">Home</a>
      <a href="#about">About</a>
      <a href="#projects">Projects</a>
      <a href="#contact">Contact</a>
    </nav>
  </header>

  <section class="hero" id="home">
    <h1>Hi, I'm Aditya</h1>
    <div class="typing">Web Developer</div>
  </section>

  <section id="about">
    <h2>About Me</h2>
    <div class="about-grid">
      <div class="about-card intro">
        <h3>Introduction</h3>
        <p>
          I am Aditya, a passionate web developer and animation designer currently interning at Examirror.
          My work is a blend of creativity and technical skills, combining coding with visual storytelling.
        </p>
      </div>

      <div class="about-card skills">
        <h3>Skills</h3>
        <ul>
          <li>HTML, CSS, JavaScript</li>
          <li>Python (Manim)</li>
          <li>Animation Design</li>
        </ul>
      </div>

      <div class="about-card hobbies">
        <h3>Hobbies</h3>
        <ul>
          <li>Gaming</li>
          <li>Coding</li>
          <li>Sketching</li>
          <li>Cooking</li>
        </ul>
      </div>

      <div class="about-card role">
        <h3>Current Role</h3>
        <p>Animation Design Intern at Examirror.</p>
      </div>

      <div class="about-card goals">
        <h3>Future Goals</h3>
        <p>To innovate in the intersection of web development and animation technologies.</p>
      </div>
    </div>
  </section>

  <section id="projects">
    <h2>Projects</h2>
    <div class="projects">
      <div class="project-card">
        <h3>Manim Animation Demo</h3>
        <p>Created an educational video animation using Manim in Python to visualize mathematical concepts.</p>
      </div>
      <div class="project-card">
        <h3>Portfolio Website</h3>
        <p>This responsive personal portfolio site built using HTML, CSS, and JS showcases my skills and projects.</p>
      </div>
      <div class="project-card">
        <h3>Todo App with Dark Mode</h3>
        <p>Built a JavaScript-based Todo app featuring localStorage persistence and dark/light theme toggling.</p>
      </div>
    </div>
  </section>

  <section id="contact">
    <h2>Contact Me</h2>
    <div class="contact">
      <p>Email: <a href="mailto:aditya535600@gmail.com">aditya535600@gmail.com</a></p>
      <p>GitHub: <a href="https://github.com/TechyAditya" target="_blank" rel="noopener noreferrer">github.com/TechyAditya</a></p>
      <p>LinkedIn: <a href="https://linkedin.com/in/aditya-kumar-jha" target="_blank" rel="noopener noreferrer">linkedin.com/in/aditya-kumar-jha</a></p>
    </div>
  </section>

  <footer>
    &copy; 2025 Aditya Kumar Jha. All Rights Reserved.
  </footer>

  <script>
    // Intersection Observer for fade-in animation
    const sections = document.querySelectorAll('section');
    const aboutCards = document.querySelectorAll('.about-card');

    const observer = new IntersectionObserver(entries => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('visible');
        }
      });
    }, { threshold: 0.15 });

    sections.forEach(section => observer.observe(section));
    aboutCards.forEach(card => observer.observe(card));
  </script>
</body>
</html>
