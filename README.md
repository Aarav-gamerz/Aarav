<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>FREE FIRE SECURITY ALERT</title>

<style>
body{
    background:#000;
    color:#00ff00;
    font-family:Consolas, monospace;
    margin:0;
    padding:20px;
    overflow-x:hidden;
}

#screen{
    white-space:pre-line;
    font-size:20px;
    line-height:1.5;
}

.blink{
    animation:blink 1s infinite;
}

@keyframes blink{
    50%{opacity:0;}
}
</style>
</head>
<body>

<div id="screen"></div>

<script>
const lines = [
"⚠ FREE FIRE SECURITY ALERT ⚠",
"",
"Player: LEGEND333",
"",
"Connecting to Garena Servers...",
"██████████ 100%",
"",
"Checking Account...",
"██████████ 100%",
"",
"Scanning Match History...",
"██████████ 100%",
"",
"Analyzing Reports...",
"██████████ 100%",
"",
"🚨 SUSPICIOUS ACTIVITY DETECTED 🚨",
"",
"Reason:",
"Using unauthorized software",
"",
"Risk Level:",
"CRITICAL",
"",
"Account Status:",
"PERMANENT BAN REVIEW",
"",
"Final Decision Loading...",
"",
"[■■□□□□□□□□] 20%",
"[■■■■□□□□□□] 40%",
"[■■■■■■□□□□] 60%",
"[■■■■■■■■□□] 80%",
"[■■■■■■■■■■] 100%",
"",
"Processing...",
"",
"3...",
"2...",
"1...",
"",
"❌ ACCOUNT BANNED",
"",
"Actual Reason:",
"You can't beat Aarav in a 1 vs 1 — only one-tap 😎",
"",
"🏆 Achievement Unlocked:",
"ULTIMATE PRANK VICTIM",
"",
"Reward:",
"🥔 1 Premium Potato",
"🎖️ Button Chaser Pro Max",
"",
"😂😂😂 NOOB! 😂😂😂"
];

const screen = document.getElementById("screen");
let i = 0;

function showLine() {
    if (i < lines.length) {
        screen.innerHTML += lines[i] + "<br>";
        window.scrollTo(0, document.body.scrollHeight);
        i++;
        setTimeout(showLine, 700);
    } else {
        screen.innerHTML += "<br><br><span class='blink'>MISSION COMPLETE 😆</span>";
    }
}

showLine();
</script>

</body>
</html>
