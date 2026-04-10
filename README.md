<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Password Guessing Game</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; }
        #confetti { display: none; position: absolute; top: 0; left: 0; width: 100%; height: 100%; pointer-events: none; }
        .hidden { display: none; }
    </style>
</head>
<body>
    <h1>Guess the Password!</h1>
    <input type="text" id="passwordInput" placeholder="Enter your guess">
    <button onclick="checkPassword()">Submit</button>
    <p id="message"></p>
    <p id="hint" class="hidden"></p>
    <div id="confetti"></div>
    <div style="position: fixed; bottom: 10px; right: 10px;">
        <button onclick="adminSignIn()">Admin Sign In</button>
    </div>

    <script>
        const passwords = ["apple", "banana", "cherry", "date", "elderberry"];
        let currentPassword = passwords[Math.floor(Math.random() * passwords.length)];
        let attempts = 0;

        function checkPassword() {
            const userInput = document.getElementById("passwordInput").value;
            attempts++;
            if (userInput === currentPassword) {
                document.getElementById("message").innerText = "Congratulations! 🎉";
                showConfetti();
            } else {
                document.getElementById("message").innerText = "Try again!";
                if (attempts % 10 === 0) {
                    document.getElementById("hint").innerText = "Hint: The password is a fruit.";
                    document.getElementById("hint").classList.remove("hidden");
                }
            }
        }

        function showConfetti() {
            const confetti = document.getElementById("confetti");
            confetti.style.display = "block";
            setTimeout(() => { confetti.style.display = "none"; }, 10000);
        }

        function adminSignIn() {
            const adminPassword = prompt("Enter admin password:");
            if (adminPassword === "passworda") {
                const newPassword = prompt("Enter new password:");
                currentPassword = newPassword;
                alert("Password changed successfully!");
            } else {
                alert("Incorrect password!");
            }
        }
    </script>
</body>
</html>
