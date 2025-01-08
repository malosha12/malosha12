<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MaloshaApp Poll - Complete Features</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 0;
        }

        /* Three Dots Icon */
        #menuIcon {
            font-size: 30px;
            position: absolute;
            top: 20px;
            left: 20px;
            cursor: pointer;
            color: #333;
        }

        /* Dropdown Menu Styling */
        #menu {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 250px;
            height: 100%;
            background-color: #333;
            color: white;
            z-index: 1000;
            box-shadow: 2px 0 5px rgba(0, 0, 0, 0.2);
        }

        #menuHeader {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px 20px;
            background-color: #444;
        }

        #menuHeader h3 {
            margin: 0;
            color: white;
        }

        #closeMenu {
            font-size: 25px;
            cursor: pointer;
        }

        #menu a {
            display: flex;
            align-items: center;
            padding: 15px 20px;
            text-decoration: none;
            color: white;
            font-size: 18px;
        }

        #menu a:hover {
            background-color: #575757;
        }

        #menu a span {
            margin-right: 10px;
            font-size: 20px;
        }

        .poll-container {
            margin: 50px auto;
            padding: 20px;
            max-width: 600px;
            background-color: #fff;
            border-radius: 8px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        }

        h1 {
            text-align: center;
        }

        .poll-options {
            margin-top: 20px;
        }

        .poll-options label {
            display: block;
            margin-bottom: 10px;
        }

        .voter-name {
            margin-top: 10px;
        }

        button {
            background-color: #007bff;
            color: white;
            padding: 10px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            width: 100%;
            margin-top: 20px;
        }

        button:hover {
            background-color: #0056b3;
        }

        .results {
            display: none;
            margin-top: 30px;
        }

        .comment-section {
            margin-top: 20px;
            text-align: center;
        }

        .comment-section input {
            padding: 10px;
            margin-top: 10px;
            border-radius: 5px;
            border: 1px solid #ddd;
            font-size: 16px;
            width: 80%;
        }

        .comment-section button {
            padding: 10px 20px;
            background-color: #28a745;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        .comment-section button:hover {
            background-color: #218838;
        }

        #shareButton {
            background-color: #28a745;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            width: 100%;
        }

        #shareButton:hover {
            background-color: #218838;
        }
    </style>
</head>
<body>

    <!-- Menu Icon -->
    <div id="menuIcon" onclick="toggleMenu()">&#9776;</div>

    <!-- Side Menu -->
    <div id="menu">
        <div id="menuHeader">
            <h3>Menu</h3>
            <div id="closeMenu" onclick="toggleMenu()">×</div>
        </div>
        <a href="#" onclick="showPage('home')"><span>🏠</span>Home</a>
        <a href="#" onclick="showPage('maloshaPrivateBox')"><span>📦</span>Malosha Private Box</a>
        <a href="#" onclick="showPage('settings')"><span>⚙️</span>Settings</a>
        <a href="#" onclick="showPage('participatedMembers')"><span>👥</span>Participated Members</a>
        <a href="#" onclick="showPage('help')"><span>❓</span>Help</a>
    </div>

    <!-- Polling Container -->
    <div class="poll-container" id="pollPage">
        <h1>Welcome to MaloshaApp Poll</h1>
        <h2>Select Poll Type:</h2>
        <select id="pollType" onchange="updatePollOptions()">
            <option value="standard">Standard Poll</option>
            <option value="star">Star Rating Poll</option>
            <option value="meeting">Meeting Poll</option>
            <option value="ranking">Ranking Poll</option>
            <option value="image">Image Poll</option>
        </select>
        <h2>Please enter your question below:</h2>
        <input type="text" id="questionInput" placeholder="Enter your custom question here..." oninput="updateQuestion()">
        <div id="pollOptions" class="poll-options"></div>
        <input type="text" id="voterName" class="voter-name" placeholder="Enter your name">
        <button onclick="submitVote()">Vote</button>

        <!-- Results Section -->
        <div class="results" id="results">
            <h3>Poll Results</h3>
            <p id="resultDetails"></p>
        </div>

        <!-- Comment Section -->
        <div class="comment-section">
            <h3>Your Comments</h3>
            <input type="text" id="smsCommentInput" placeholder="Enter your comments here...">
            <button onclick="submitSMSComment()">Submit Comment</button>
        </div>

        <!-- Share Button -->
        <button id="shareButton" onclick="sharePoll()">Share Poll</button>
    </div>

    <script>
        let pollData = {
            question: "",
            options: {},
            voters: [],
            comments: []
        };

        function toggleMenu() {
            const menu = document.getElementById("menu");
            menu.style.display = menu.style.display === "block" ? "none" : "block";
        }

        function showPage(page) {
            alert(`Navigating to: ${page}`);
            toggleMenu();
        }

        function updatePollOptions() {
            const pollType = document.getElementById("pollType").value;
            const pollOptionsDiv = document.getElementById("pollOptions");
            if (pollType === "standard") {
                pollOptionsDiv.innerHTML = `
                    <label><input type="radio" name="vote" value="Option 1"> Option 1</label>
                    <label><input type="radio" name="vote" value="Option 2"> Option 2</label>
                `;
            }
        }

        function submitVote() {
            alert("Vote submitted!");
        }

        function submitSMSComment() {
            const comment = document.getElementById("smsCommentInput").value;
            alert(`Comment submitted: ${comment}`);
        }

        function sharePoll() {
            alert("Poll shared!");
        }
    </script>
</body>
</html>
