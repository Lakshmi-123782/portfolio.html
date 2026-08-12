# portfolio.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My portfolio</title>

    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
        }

        header {
            background-color: navy;
            color: rgb(72, 22, 100);
            padding: 20px 0;

        }

        nav {
            background-color: #28cce9;
            color: rgb(224, 209, 209);
            padding: 10px 0;
        }

        nav a {
            color: white;
            text-decoration: none;
            margin: 0 15px;
        }
        nav a:hover {
            text-decoration: underline;
        }
        main {
            padding: 20px;
        }
        section {
            margin-bottom: 40px;
        }
        footer {
            background-color: #0e81c4;
            color: white;
            text-align: center;
            padding: 10px 0;
        }
        </style>
</head>

<body>
    <header style="background-color:rgb(30, 139, 88); color: rgb(50, 201, 221); font-size: 30px; text-align: center; border-radius: 10px; padding: 30px;">
        <h4><u>My Portfolio</u></h4>

        <figure style="text-align: center;">
            <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcT-JyRFAKSmCZSwGepLGMxADMcUE7mMphiyBZpPnKW0Ew&s" alt="Profile Image" width="300" height="200">
            <figcaption style="text-align: center; color: rgb(212, 221, 228);">portfolio</figcaption>
        </figure>

        <div style="background-color: pink; color: rgb(255, 0, 98); font-size: 30px; text-align: center; border-radius: 1px; display: inline-block; padding: 5px 15px;">
            <h3><u>Lakshmi</u></h3>
        </div>
        <p style="text-align: center; color: rgb(138, 165, 42);">
            BCA student aspiring developer
        </p>
        <nav>
            <ol type="1" style="list-style-type: none; display: flex; justify-content: center; gap: 20px;">
                <li><a href="#About.html"><u>About me</u></a></li>
                <li><a href="#skills.html"><u>Skills</u></a></li>
                <li><a href="#projects.html"><u>projects</u></a></li>
                <li><a href="#contact.html"><u>Contact</u></a></li>
            </ol>
        </nav>
    </header>
    <main>
        <section id="About.html">
        <h2>Welcome to my portfolio</h2>  
        <h3 style="color: rgb(106, 162, 235); text-align: center; border-radius: 1px;"><u>About Me</u></h3>  
        <p>Hi, I'm Lakshmi, a passionate BCA student aspiring to become a skilled developer.<br> <br>This portfolio showcases my journey, skills, and projects that reflect my dedication to the world of technology.</p>
        </section>

        
<hr>
    <section id="skills.html">
        <h3 style="color: rgb(85, 172, 63); text-align: center; border-radius: 1px;"><u>Skills</u></h3>
        <ul>
            <li>HTML</li>
            <li>CSS</li>
            <li>JavaScript</li>
            <li>Python</li>
            <li>Database Management</li>
        </ul>
</section>
<hr>
    <section id="projects.html" >
        <h3 style="color: rgb(219, 127, 140); text-align: center; border-radius: 1px;"><u>Projects</u></h3>
        <p style="color: rgb(19, 223, 145); font-weight: bold;"><u>Student Registration System:</u></p>
        <p style="background-color: rgb(142, 193, 209); padding: 10px; border-radius: 5px;">A web application that allows students to register for courses, view their schedules, and manage their academic profiles.</p>
        <p style="color: rgb(255, 185, 93); font-weight: bold;"><u>E-commerce Website:</u></p>
        <p style="background-color: rgb(172, 202, 226); padding: 10px; border-radius: 5px;">A fully functional e-commerce platform for buying and selling products online.</p>
    </section>
<hr>
    <section id="contact.html">
        <h3 style="color: rgb(120, 63, 196); text-align: center; border-radius: 1px;"><u>Contact Me</u></h3>
        <form>
            <label for="name">Name:</label>
            <input type="text" id="name" name="name" required><br><br>
            <label for="email">Email:</label>
            <input type="email" id="email" name="email" required><br><br>
            <label for="message">Message:</label><br>
            <textarea id="message" name="message" rows="4" cols="50" required></textarea><br><br>
            <button type="submit">Submit</button> <br><br>
            <button type="reset">Reset</button>
        </form>
    </section>
     <footer>
            <p>&copy; 2023 Lakshmi. All rights reserved.</p>
        </footer>
    </main>
</body>
</html>
