 📁 Structure:

```
portfolio-site/
│
├── index.html         → Home Page
├── about.html         → About Me
├── projects.html      → Projects Page
├── contact.html       → Contact Form Page
└── assets/
    └── resume.pdf     → (Optional resume link)
```

---

##  Let's create it. Ready-to-run pure HTML code:

###  1. `index.html` (Home Page)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>My Portfolio - Home</title>
</head>
<body>
  <header>
    <h1>Welcome to My Portfolio</h1>
    <nav>
      <a href="index.html">Home</a> |
      <a href="about.html">About</a> |
      <a href="projects.html">Projects</a> |
      <a href="contact.html">Contact</a>
    </nav>
  </header>

  <main>
    <section>
      <h2>Introduction</h2>
      <p>Hi! I'm a passionate web developer learning HTML and beyond.</p>
    </section>

    <section>
      <h2>Latest Video Intro</h2>
      <video width="320" controls>
        <source src="https://www.w3schools.com/html/mov_bbb.mp4" type="video/mp4">
        Your browser does not support video.
      </video>
    </section>
  </main>

  <footer>
    <p>&copy; 2025 My Name. All rights reserved.</p>
  </footer>
</body>
</html>
```

---

### ✅ 2. `about.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>About Me</title>
</head>
<body>
  <header>
    <h1>About Me</h1>
    <nav>
      <a href="index.html">Home</a> |
      <a href="about.html">About</a> |
      <a href="projects.html">Projects</a> |
      <a href="contact.html">Contact</a>
    </nav>
  </header>

  <main>
    <section>
      <h2>Who Am I?</h2>
      <p>I am a beginner web developer with a passion for learning HTML, CSS, and JavaScript.</p>
    </section>

    <section>
      <h2>Download My Resume</h2>
      <a href="assets/resume.pdf" download>Click here to download</a>
    </section>
  </main>

  <footer>
    <p>&copy; 2025 My Name</p>
  </footer>
</body>
</html>
```

---

### ✅ 3. `projects.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Projects</title>
</head>
<body>
  <header>
    <h1>My Projects</h1>
    <nav>
      <a href="index.html">Home</a> |
      <a href="about.html">About</a> |
      <a href="projects.html">Projects</a> |
      <a href="contact.html">Contact</a>
    </nav>
  </header>

  <main>
    <article>
      <h2>Project 1: Portfolio Site</h2>
      <p>This current site is my first full HTML-only portfolio project.</p>
      <details>
        <summary>View Details</summary>
        <p>Built using semantic HTML, includes multiple pages, forms, and multimedia.</p>
      </details>
    </article>

    <article>
      <h2>Project 2: HTML Quiz</h2>
      <p>A simple quiz using only HTML radio buttons and details tag.</p>
      <details>
        <summary>View Details</summary>
        <p>No CSS or JS used, but fully functional for basic MCQs.</p>
      </details>
    </article>
  </main>

  <footer>
    <p>&copy; 2025 My Name</p>
  </footer>
</body>
</html>
```

---

### ✅ 4. `contact.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Advanced Contact Form</title>
</head>
<body>
  <h1>Contact Me</h1>

  <form>
    <!-- Personal Info -->
    <fieldset>
      <legend>Personal Details</legend>

      <label for="fullname">Full Name:</label><br>
      <input type="text" id="fullname" name="fullname" placeholder="Your name" required autofocus><br><br>

      <label for="email">Email:</label><br>
      <input type="email" id="email" name="email" required><br><br>

      <label for="phone">Phone Number:</label><br>
      <input type="tel" id="phone" name="phone" pattern="[0-9]{10}" placeholder="10-digit number"><br><br>

      <label for="dob">Date of Birth:</label><br>
      <input type="date" id="dob" name="dob" max="2010-01-01"><br><br>

      <label for="website">Portfolio URL:</label><br>
      <input type="url" id="website" name="website" placeholder="https://example.com"><br><br>

      <label for="country">Country:</label><br>
      <select id="country" name="country">
        <option value="">--Select--</option>
        <option>India</option>
        <option>USA</option>
        <option>UK</option>
        <option>Australia</option>
      </select><br><br>

    </fieldset>

    <!-- Preferences -->
    <fieldset>
      <legend>Preferences</legend>

      <label for="color">Favorite Color:</label><br>
      <input type="color" id="color" name="color"><br><br>

      <label for="experience">Experience Level (Years):</label><br>
      <input type="range" id="experience" name="experience" min="0" max="10"><br><br>

      <label for="skills">Skills (Type & select):</label><br>
      <input list="skills" name="skill">
      <datalist id="skills">
        <option value="HTML">
        <option value="CSS">
        <option value="JavaScript">
        <option value="Python">
      </datalist><br><br>

      <label>Preferred Contact Method:</label><br>
      <input type="radio" name="contact_method" value="email" checked> Email<br>
      <input type="radio" name="contact_method" value="phone"> Phone<br><br>

      <label>Topics of Interest:</label><br>
      <input type="checkbox" name="topics" value="html"> HTML<br>
      <input type="checkbox" name="topics" value="css"> CSS<br>
      <input type="checkbox" name="topics" value="js"> JavaScript<br><br>

    </fieldset>

    <!-- Upload -->
    <fieldset>
      <legend>Upload Resume</legend>
      <input type="file" name="resume" accept=".pdf,.doc,.docx"><br><br>
    </fieldset>

    <!-- Message -->
    <fieldset>
      <legend>Message</legend>
      <label for="message">Your Message:</label><br>
      <textarea id="message" name="message" rows="6" cols="40" required></textarea><br><br>
    </fieldset>

    <!-- Submission -->
    <input type="submit" value="Submit">
    <input type="reset" value="Reset Form">
  </form>

  <footer>
    <p>&copy; 2025 My Portfolio</p>
  </footer>
</body>
</html>
```

---

##

1. Create a folder: `portfolio-site`
2. Inside it, save:

   * The four `.html` files
   * Create a subfolder `assets/` and place your `resume.pdf` (or a placeholder file)


* A **multi-page personal portfolio site**
* Semantic HTML: header, nav, main, footer
* Internal navigation
* Contact form (no JS needed)
* Embedded video
* Expandable project details
* Downloadable resume link

---

