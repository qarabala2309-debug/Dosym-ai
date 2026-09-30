# Dosym-ai
Менің жеке AI ассистентім -ДОСЫМ 
<!DOCTYPE html>
<html lang="kk">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>ДОСЫМ</title>

  <style>
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      min-height: 100vh;
      background: #090909;
      color: white;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
    }

    .app {
      max-width: 520px;
      min-height: 100vh;
      margin: auto;
      padding: 22px 18px 120px;
    }

    header {
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .logo {
      font-size: 21px;
      font-weight: 800;
      letter-spacing: 3px;
    }

    .online {
      font-size: 11px;
      color: #777;
    }

    .hero {
      text-align: center;
      padding: 65px 0 35px;
    }

    .orb {
      width: 115px;
      height: 115px;
      margin: auto;
      border-radius: 50%;
      display: grid;
      place-items: center;

      background:
        radial-gradient(
          circle at 35% 30%,
          #555,
          #202020 50%,
          #0d0d0d
        );

      box-shadow: 0 0 60px #222;
    }

    .orb span {
      font-size: 42px;
      font-weight: 800;
    }

    h1 {
      margin: 25px 0 7px;
      font-size: 29px;
    }

    #status {
      margin: 0;
      color: #777;
    }

    #chat {
      display: flex;
      flex-direction: column;
      gap: 10px;
    }

    .message {
      max-width: 84%;
      padding: 13px 16px;
      border-radius: 18px;
      line-height: 1.45;
    }

    .user {
      align-self: flex-end;
      background: white;
      color: black;
      border-bottom-right-radius: 5px;
    }

    .dosym {
      align-self: flex-start;
      background: #191919;
      border-bottom-left-radius: 5px;
    }

    .input-area {
      position: fixed;
      bottom: 70px;
      left: 50%;
      transform: translateX(-50%);

      width: min(490px, calc(100% - 25px));

      display: flex;
      gap: 8px;

      padding: 8px;

      background: #151515;
      border: 1px solid #292929;
      border-radius: 22px;
    }

    input {
      flex: 1;
      min-width: 0;

      background: transparent;
      border: none;
      outline: none;

      color: white;
      font-size: 16px;
    }

    button {
      border: none;
      color: white;
      background: #292929;

      width: 42px;
      height: 42px;

      border-radius: 14px;
      font-size: 18px;
    }

    #send {
      background: white;
      color: black;
    }

    nav {
      position: fixed;
      bottom: 0;
      left: 0;
      right: 0;

      height: 60px;

      background: #0d0d0d;
      border-top: 1px solid #222;

      display: flex;
      justify-content: center;
      gap: 30px;

      padding-top: 8px;
    }

    nav div {
      text-align: center;
      color: #777;
      font-size: 17px;
    }

    nav small {
      display: block;
      font-size: 9px;
      margin-top: 2px;
    }
  </style>
</head>

<body>

<div class="app">

  <header>
    <div class="logo">ДОСЫМ</div>
    <div class="online">● ONLINE</div>
  </header>

  <section class="hero">

    <div class="orb">
      <span>Д</span>
    </div>

    <h1>Сәлем, досым.</h1>

    <p id="status">
      Мен сені тыңдап тұрмын.
    </p>

  </section>

  <section id="chat"></section>

</div>

<div class="input-area">

  <button id="mic">🎙️</button>

  <input
    id="input"
    type="text"
    placeholder="ДОСЫМ-ға жаз..."
  >

  <button id="send">➤</button>

</div>

<nav>

  <div>
    💬
    <small>Сөйлесу</small>
  </div>

  <div>
    🧠
    <small>Memory</small>
  </div>

  <div>
    🛠️
    <small>Tools</small>
  </div>

  <div>
    ⚙️
    <small>Settings</small>
  </div>

</nav>

<script>

const input = document.getElementById("input");
const send = document.getElementById("send");
const chat = document.getElementById("chat");
const status = document.getElementById("status");

function addMessage(text, type) {

  const message = document.createElement("div");

  message.className = "message " + type;

  message.textContent = text;

  chat.appendChild(message);

}

function sendMessage() {

  const text = input.value.trim();

  if (!text) return;

  addMessage(text, "user");

  input.value = "";

  status.textContent = "Ойланып жатырмын...";

  setTimeout(() => {

    let answer =
      "Түсіндім, досым. Мен — ДОСЫМ. Бұл менің алғашқы нұсқам.";

    if (/сәлем|салам|привет/i.test(text)) {

      answer = "Сәлем, досым! 👋 Мен дайынмын.";

    }

    if (/атың|кімсің/i.test(text)) {

      answer =
        "Менің атым — ДОСЫМ. Мен сенің жеке AI ассистентің боламын.";

    }

    if (/рахмет|спасибо/i.test(text)) {

      answer =
        "Әрқашан, досым 🤝";

    }

    addMessage(answer, "dosym");

    status.textContent =
      "Мен сені тыңдап тұрмын.";

  }, 500);

}

send.onclick = sendMessage;

input.addEventListener("keydown", function(event) {

  if (event.key === "Enter") {

    sendMessage();

  }

});

</script>

</body>
</html>