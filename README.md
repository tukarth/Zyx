
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Login com Firebase</title>
  <link rel="icon" href="data:,"> <!-- FAVICON REMOVIDO AQUI -->
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;500;700&display=swap" rel="stylesheet">
  <style>
    body {
      background-color: #000;
      color: #fff;
      font-family: 'Poppins', sans-serif;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      min-height: 0vh;
      padding: 0px;
    }

    form {
      background: rgba(255, 255, 255, 0.05);
      padding: 30px;
      border-radius: 15px;
      max-width: 400px;
      width: 100%;
      box-shadow: 0 0 10px rgba(0,0,0,0.5);
    }

    input, button {
      width: 100%;
      margin: 10px 0;
      padding: 12px;
      border-radius: 8px;
      border: 1px solid #333;
      background-color: #1a1a1a;
      color: #fff;
      font-size: 16px;
    }

    button {
      background-color: #1abc9c;
      border: none;
      cursor: pointer;
      transition: background 0.3s ease;
    }

    button:hover {
      background-color: #16a085;
    }

    h2 {
      text-align: center;
      margin-bottom: 10px;
    }

    .message {
      text-align: center;
      margin-top: 15px;
      font-size: 14px;
      color: #1abc9c;
    }
  </style>
</head>
<body>

  <form id="authForm">
    <h3>Entrar na Plataforma</h3>
    <input type="email" id="email" placeholder="E-mail" required />
    <input type="password" id="password" placeholder="Senha" required />
    <button type="button" id="loginBtn">Entrar</button>
    <div id="msg" class="message"></div>
  </form>

  <!-- Firebase SDKs -->
  <script src="https://www.gstatic.com/firebasejs/8.10.1/firebase-app.js"></script>
  <script src="https://www.gstatic.com/firebasejs/8.10.1/firebase-auth.js"></script>

  <script>
    const firebaseConfig = {
      apiKey: "AIzaSyAEtOJtXMIclBzLNNsEXJKqF4Rsqg_AAHs",
      authDomain: "arthur-dba38.firebaseapp.com",
      projectId: "arthur-dba38",
      storageBucket: "arthur-dba38.firebasestorage.app",
      messagingSenderId: "226852614993",
      appId: "1:226852614993:web:5f60769150d33a50e69970",
      measurementId: "G-WSNY5JJS7Q"
    };

    firebase.initializeApp(firebaseConfig);
  </script>

  <script>
    const loginBtn = document.getElementById("loginBtn");
    const msgDiv = document.getElementById("msg");

    loginBtn.addEventListener("click", () => {
      const email = document.getElementById("email").value.trim();
      const password = document.getElementById("password").value;

      firebase.auth().signInWithEmailAndPassword(email, password)
        .then(() => {
          msgDiv.textContent = "✅ Login realizado com sucesso!";
          setTimeout(() => {
            window.location.href = "dashboard.html";
          }, 1500);
        })
        .catch(error => {
          msgDiv.textContent = "❌ Erro no login: " + error.message;
        });
    });
  </script>
</body>
</html>
