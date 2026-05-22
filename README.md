<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Smash or Pass</title>
<style>
body {
  margin: 0;
  background: #0f0f0f;
  font-family: Arial, sans-serif;
  color: white;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
}
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.card {
  width: 320px;
  height: 420px;
  border-radius: 20px;
  overflow: hidden;
  background: #222;
  box-shadow: 0 8px 16px rgba(0,0,0,0.5);
}
.card img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.buttons {
  margin-top: 20px;
  display: flex;
  gap: 20px;
}
button {
  padding: 12px 24px;
  border: none;
  border-radius: 10px;
  font-size: 16px;
  font-weight: bold;
  cursor: pointer;
  transition: transform 0.1s;
}
button:active {
  transform: scale(0.95);
}
#smash {
  background: #4dff88;
  color: black;
}
#pass {
  background: #ff4d4d;
  color: white;
}
.popup {
  position: fixed;
  top: 40%;
  font-size: 50px;
  font-weight: bold;
  display: none;
  text-shadow: 2px 2px 4px rgba(0,0,0,0.8);
  z-index: 10;
}
</style>
</head>
<body>

<div class="container">
  <div class="card">
    <img id="img" src="" alt="Loading..." />
  </div>
</div>

<div class="popup" id="popup"></div>

<div class="buttons">
  <button id="pass">Pass 👎</button>
  <button id="smash">Smash 🔥</button>
</div>

<script>
// =====================
// IMAGES (Matches your screenshot)
// =====================
let images = [
  "IMG_2583.jpeg",
  "IMG_2584.jpeg",
  "IMG_2585.jpeg",
  "IMG_2586.jpeg",
  "IMG_2587.jpeg",
  "IMG_2588.jpeg",
  "IMG_2589.jpeg",
  "IMG_2590.jpeg",
  "IMG_2591.jpeg",
  "IMG_2592.jpeg"
];

let index = 0;
const img = document.getElementById("img");
const popup = document.getElementById("popup");
const buttonsDiv = document.querySelector(".buttons");

// =====================
// LOAD IMAGE
// =====================
function load() {
  if (index >= images.length) {
    popup.innerText = "DONE 🎉";
    popup.style.color = "white";
    popup.style.display = "block";
    img.style.display = "none"; // Hide image container when done
    buttonsDiv.style.display = "none"; // Hide buttons when done
    return;
  }
  
  // Using a direct relative path. If index.html and images are in the same folder, 
  // this works perfectly both locally and on GitHub Pages.
  img.src = images[index];
}

// =====================
// NEXT IMAGE
// =====================
function next(text, color) {
  popup.innerText = text;
  popup.style.color = color;
  popup.style.display = "block";
  
  setTimeout(() => {
    popup.style.display = "none";
  }, 500);
  
  index++;
  load();
}

// =====================
// BUTTON EVENTS
// =====================
document.getElementById("smash").onclick = () => next("SMASH 🔥", "#4dff88");
document.getElementById("pass").onclick = () => next("PASS 👎", "#ff4d4d");

// Initial Load
load();
</script>
</body>
</html>