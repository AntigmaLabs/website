<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Antigma - Mine Thyself</title>
    <style>
        body {
            background-color: black;
            color: #00FF00; /* Default terminal text color */
            font-family: 'Courier New', Courier, monospace;
            margin: 0;
            padding: 20px;
        }
        .banner {
            color: #00FFFF; /* Cyan color for banner */
            margin-bottom: 40px; /* Increased space below the banner */
            text-align: center;
            font-size: 1.5em; /* Larger font size for the banner */
        }
        .section {
            display: none;
            margin-bottom: 40px;
        }
        .section h2 {
            position: relative;
            margin-bottom: 20px;
            color: #FFD700; /* Gold color for section titles */
        }
        .section h2::after {
            content: '------------------------------------------------------------';
            position: absolute;
            left: 0;
            top: 100%;
            color: #FFD700; /* Matching gold color for separator */
            font-size: 12px;
            line-height: 0.5em;
        }
        a {
            color: #D3D3D3; /* Softer color for readability */
            text-decoration: none;
            cursor: pointer;
            font-weight: bold;
        }
        a:hover {
            text-decoration: underline;
        }
        .command {
            color: #FF00FF;
            font-weight: bold;
            font-size: 1.2em; /* Increased font size for command words */
        }
        #command-line {
            margin-top: 20px;
        }
        #command-prompt {
            display: flex;
            align-items: center;
        }
        #prompt {
            margin-right: 10px;
            font-family: 'Courier New', Courier, monospace;
        }
        #commandInput {
            background-color: black;
            color: #00FFFF; /* Light blue color for user input */
            border: none;
            outline: none;
            flex-grow: 1;
            font-family: 'Courier New', Courier, monospace;
            caret-color: #00FFFF;
            padding-left: 2px;
        }
        .highlight {
            color: #20B2AA; /* Teal color for slogan */
        }
        .project-name {
            color: #FF4500; /* Red-Orange color for project name */
        }
        .cursor {
            display: inline-block;
            background-color: #00FF00;
            margin-left: 2px;
            width: 10px;
            animation: blink 1s steps(1) infinite;
        }
        .unknown-command {
            color: #FF0000; /* Red color for unknown command */
            margin-top: 10px;
        }
        @keyframes blink {
            50% {
                background-color: black;
            }
        }
        /* Softer color for readable content */
        .readable-content {
            color: #D3D3D3;
        }
    </style>
</head>
<body>
    <pre class="banner">
        ___      .__   __. .___________. __    _______ .___  ___.      ___
        /   \     |  \ |  | |           ||  |  /  _____||   \/   |     /   \
       /  ^  \    |   \|  | `---|  |----`|  | |  |  __  |  \  /  |    /  ^  \
      /  /_\  \   |  . `  |     |  |     |  | |  | |_ | |  |\/|  |   /  /_\  \
     /  _____  \  |  |\   |     |  |     |  | |  |__| | |  |  |  |  /  _____  \
    /__/     \__\ |__| \__|     |__|     |__|  \______| |__|  |__| /__/     \__\
                                                                             
    </pre>
    <div id="intro" class="section readable-content">
        <h2>Welcome to <span class="project-name">Antigma</span></h2>
        <p><span class="project-name">Antigma</span> A federated intelligence network supported by model sharding and splitting</p>
        <p><strong class="highlight">Slogan:</strong> Mine Thyself</p>
    </div>
    <div id="articles" class="section readable-content">
        <h2>Articles</h2>
        <ul>
            <li><a href="#" onclick="displayArticle('article1')">Understanding data era</a></li>
            <li><a href="#" onclick="displayArticle('article2')">The Future of AI in edge devices</a></li>
            <li><a href="#" onclick="displayArticle('article3')">How <span class="project-name">Antigma</span> Protects Your Privacy</a></li>
        </ul>
    </div>
    <div id="article1" class="section article-content readable-content">
        <h2>Understanding data era</h2>
        <p>This article explains the concept of personal data mining...</p>
        <p><a class="command" onclick="navigate('articles')">back</a></p>
    </div>
    <div id="article2" class="section article-content readable-content">
        <h2>The Future of AI in edge devices</h2>
        <p>This article discusses the future trends and potential of AI in edge devices...</p>
        <p><a class="command" onclick="navigate('articles')">back</a></p>
    </div>
    <div id="article3" class="section article-content readable-content">
        <h2>How <span class="project-name">Antigma</span> Protects Your Privacy</h2>
        <p>This article describes the measures <span class="project-name">Antigma</span> takes to protect user privacy...</p>
        <p><a class="command" onclick="navigate('articles')">back</a></p>
    </div>
    <div id="team" class="section readable-content">
        <h2>Our Team</h2>
        <ul>
            <li><strong class="highlight">Mohan:</strong> Co-founder, CEO</li>
            <li><strong class="highlight">Mengshi:</strong> Co-founder, Cheif of Coasting</li>
            <li><strong class="highlight">Member 3:</strong> Role</li>
            <li><strong class="highlight">Member 4:</strong> Role</li>
            <li><strong class="highlight">Member 5:</strong> Role</li>
        </ul>
    </div>
    <div id="command-line">
        <p>Type or click <a class="command" onclick="navigate('intro')">intro</a>, <a class="command" onclick="navigate('articles')">articles</a>, or <a class="command" onclick="navigate('team')">team</a> to navigate:</p>
        <div id="command-prompt">
            <span id="prompt">guest@antigma.ai:~$</span>
            <input type="text" id="commandInput" autocomplete="off">
            <span class="cursor"></span>
        </div>
        <div id="command-output" class="unknown-command"></div>
    </div>

    <script>
        // Function to focus the input field
        function focusInput() {
            document.getElementById('commandInput').focus();
        }

        // Focus the input field and display the intro section when the page loads
        window.onload = function() {
            focusInput();
            navigate('intro'); // Display the intro section by default
        };

        // Add event listener for the command input
        document.getElementById('commandInput').addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                const command = e.target.value.toLowerCase();
                e.target.value = '';
                navigate(command);
            }
        });

        // Function to handle navigation
        function navigate(command) {
            document.getElementById('command-output').innerHTML = ''; // Clear previous output
            document.querySelectorAll('.section').forEach(section => section.style.display = 'none');

            if (command === 'intro') {
                document.getElementById('intro').style.display = 'block';
            } else if (command === 'articles') {
                document.getElementById('articles').style.display = 'block';
            } else if (command === 'team') {
                document.getElementById('team').style.display = 'block';
            } else if (command === 'back') {
                document.getElementById('articles').style.display = 'block';
            } else if (document.getElementById(command)) {
                document.getElementById(command).style.display = 'block';
            } else {
                document.getElementById('command-output').innerHTML = 'Unknown command: ' + command;
            }
            focusInput(); // Ensure the input field is focused after navigation
        }

        // Function to display article content
        function displayArticle(articleId) {
            document.getElementById('command-output').innerHTML = ''; // Clear previous output
            document.querySelectorAll('.section').forEach(section => section.style.display = 'none');
            document.getElementById(articleId).style.display = 'block';
            focusInput(); // Ensure the input field is focused after displaying an article
        }
    </script>
</body>
</html>
