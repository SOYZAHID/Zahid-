<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Mi IA estilo iOS</title>
  <style>
    body {
      margin: 0;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
      background: linear-gradient(135deg, #dfe9f3, #ffffff);
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .chat-container {
      width: 90%;
      max-width: 400px;
      height: 80vh;
      display: flex;
      flex-direction: column;
      backdrop-filter: blur(20px) saturate(180%);
      background-color: rgba(255, 255, 255, 0.3);
      border-radius: 20px;
      box-shadow: 0 8px 32px rgba(0,0,0,0.2);
      overflow: hidden;
    }

    .messages {
      flex: 1;
      padding: 15px;
      overflow-y: auto;
    }

    .message {
      margin: 10px 0;
      padding: 10px 15px;
      border-radius: 15px;
      max-width: 80%;
      animation: fadeIn 0.3s ease;
    }

    .user {
      background: rgba(0, 122, 255, 0.2);
      align-self: flex-end;
    }

    .bot {
      background: rgba(255, 255, 255, 0.6);
      align-self: flex-start;
    }

    .input-area {
      display: flex;
      padding: 10px;
      background: rgba(255,255,255,0.2);
      backdrop-filter: blur(10px);
    }

    .input-area input {
      flex: 1;
      border: none;
      padding: 10px;
      border-radius: 10px;
      outline: none;
      font-size: 14px;
    }

    .input-area button {
      margin-left: 10px;
      padding: 10px 15px;
      border: none;
      border-radius: 10px;
      background: #007aff;
      color: white;
      font-weight: bold;
      cursor: pointer;
      transition: background 0.3s;
    }

    .input-area button:hover {
      background: #005bb5;
    }

    @keyframes fadeIn {
      from {opacity: 0; transform: translateY(10px);}
      to {opacity: 1; transform: translateY(0);}
    }
  </style>
</head>
<body>
  <div class="chat-container">
    <div class="messages" id="messages"></div>
    <div class="input-area">
      <input type="text" id="userInput" placeholder="Escribe tu mensaje...">
      <button onclick="sendMessage()">Enviar</button>
    </div>
  </div>

  <script>
    function sendMessage() {
      const input = document.getElementById("userInput");
      const text = input.value.trim();
      if (text === "") return;

      addMessage(text, "user");
      input.value = "";

      // Simulación de respuesta de IA
      setTimeout(() => {
        addMessage("Soy tu IA estilo iOS ✨", "bot");
      }, 800);
    }

    function addMessage(text, type) {
      const messages = document.getElementById("messages");
      const msg = document.createElement("div");
      msg.className = "message " + type;
      msg.textContent = text;
      messages.appendChild(msg);
      messages.scrollTop = messages.scrollHeight;
    }
  </script>
</body>
</html>
