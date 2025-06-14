<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Login com Firebase</title>
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
      min-height: 100vh;
      padding: 20px;
    }

    form {
      background: rgba(255, 255, 255, 0.05);
      padding: 30px;
      border-radius: 15px;
      max-width: 400px;
      width: 100%;
      box-shadow: 0 0 10px rgba(0,0,0,0.5);
      margin-bottom: 30px;
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
      margin-bottom: 20px;
    }
  </style>
</head>
<body>

  <!-- Formulário de Login -->
  <form id="loginForm">
    <h2>Login</h2>
    <input type="email" id="email" placeholder="E-mail" required>
    <input type="password" id="password" placeholder="Senha" required>
    <button type="submit">Entrar</button>
  </form>

  <!-- Formulário de Cadastro -->
  <form id="signupForm">
    <h2>Cadastrar Usuário</h2>
    <input type="email" id="newEmail" placeholder="Novo e-mail" required>
    <input type="password" id="newPassword" placeholder="Nova senha" required>
    <button type="submit">Cadastrar</button>
  </form>

  <!-- Firebase SDKs -->
  <script src="https://www.gstatic.com/firebasejs/10.11.1/firebase-app.js"></script>
  <script src="https://www.gstatic.com/firebasejs/10.11.1/firebase-auth.js"></script>
  <script src="https://www.gstatic.com/firebasejs/10.11.1/firebase-analytics.js"></script>

  <!-- Inicialização do Firebase com seus dados -->
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
    firebase.analytics();
  </script>

  <!-- Lógica de Login -->
  <script>
    document.getElementById("loginForm").addEventListener("submit", function(event) {
      event.preventDefault();
      const email = document.getElementById("email").value;
      const password = document.getElementById("password").value;

      firebase.auth().signInWithEmailAndPassword(email, password)
        .then((userCredential) => {
          alert("Login realizado com sucesso!");
          window.location.href = "dashboard.html"; // redireciona após login
        })
        .catch((error) => {
          alert("Erro ao fazer login: " + error.message);
        });
    });
  </script>

  <!-- Lógica de Cadastro -->
  <script>
    document.getElementById("signupForm").addEventListener("submit", function(event) {
      event.preventDefault();
      const email = document.getElementById("newEmail").value;
      const password = document.getElementById("newPassword").value;

      firebase.auth().createUserWithEmailAndPassword(email, password)
        .then((userCredential) => {
          alert("Usuário cadastrado com sucesso!");
        })
        .catch((error) => {
          alert("Erro ao cadastrar: " + error.message);
        });
    });
  </script>

</body>
</html>
