<!DOCTYPE html>
<html>
<head>
<title>Secret Code</title>
</head>
<body style="font-family:sans-serif;text-align:center;overflow:hidden;">

<h1>💻 Click the button to get the secret code! 💻</h1>

<button id="btn" style="
position:absolute;
font-size:24px;
padding:15px 30px;
left:45%;
top:50%;
">
GET CODE
</button>

<script>
const btn = document.getElementById("btn");

btn.addEventListener("mouseover", () => {
  btn.style.left =
    Math.random() * (window.innerWidth - btn.offsetWidth) + "px";
  btn.style.top =
    Math.random() * (window.innerHeight - btn.offsetHeight) + "px";

  btn.innerText = [
    "Almost!",
    "Too Slow!",
    "Catch Me!",
    "Try Again!",
    "Nope!"
  ][Math.floor(Math.random() * 5)];
});

btn.addEventListener("click", () => {
  document.body.innerHTML = `
    <div style="padding-top:100px;">
      <h1>😂 Just prank Aksh!</h1>
      <h2>Main terko kabhi code nahi dunga! 😜</h2>
    </div>
  `;
});
</script>

</body>
</html>
