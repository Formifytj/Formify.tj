<!DOCTYPE html>
<html lang="tg">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Formify PDF – Анкетаи донишҷӯ</title>
  <link href="https://fonts.googleapis.com/css2?family=Rubik:wght@400;600&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'Rubik', sans-serif;
      background: #f4f6f9;
      margin: 0;
      padding: 0;
    }
    .container {
      max-width: 720px;
      margin: 40px auto;
      background: #fff;
      padding: 30px;
      border-radius: 10px;
      box-shadow: 0 5px 15px rgba(0,0,0,0.1);
    }
    .logo {
      text-align: center;
      margin-bottom: 20px;
    }
    .logo h1 {
      color: #0057D8;
      font-size: 28px;
    }
    .form input, .form textarea {
      display: block;
      width: 100%;
      margin: 12px 0;
      padding: 12px;
      border: 1px solid #ccc;
      border-radius: 6px;
      font-size: 15px;
    }
    button {
      background: #0057D8;
      color: white;
      border: none;
      padding: 12px 24px;
      font-size: 16px;
      border-radius: 6px;
      cursor: pointer;
      margin-top: 10px;
    }
    button:hover {
      background: #0041a8;
    }
    .preview {
      display: none;
      background: #fafafa;
      margin-top: 30px;
      padding: 20px;
      border: 1px solid #ccc;
      border-radius: 6px;
    }
    .preview h2 {
      color: #333;
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="logo">
      <h1>Formify PDF</h1>
      <p><em>Анкетаи донишҷӯ</em></p>
    </div>

    <div class="form">
      <input id="fullname" placeholder="Ном ва насаб" />
      <input id="dob" type="date" placeholder="Санаи таваллуд" />
      <input id="email" placeholder="Email" />
      <input id="phone" placeholder="Рақами телефон" />
      <input id="field" placeholder="Факултет ё ихтисос" />
      <textarea id="goals" placeholder="Чаро мехоҳед таҳсил кунед?"></textarea>
      <button onclick="generatePDF()">Download PDF</button>
    </div>

    <div id="preview" class="preview">
      <h2>Анкетаи донишҷӯ</h2>
      <p><strong>Ном:</strong> <span id="p-name"></span></p>
      <p><strong>Санаи таваллуд:</strong> <span id="p-dob"></span></p>
      <p><strong>Email:</strong> <span id="p-email"></span></p>
      <p><strong>Телефон:</strong> <span id="p-phone"></span></p>
      <p><strong>Факултет/ихтисос:</strong> <span id="p-field"></span></p>
      <p><strong>Мақсад:</strong></p>
      <p id="p-goals"></p>
    </div>
  </div>

  <script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script>
  <script>
    function generatePDF() {
      document.getElementById("p-name").innerText = document.getElementById("fullname").value;
      document.getElementById("p-dob").innerText = document.getElementById("dob").value;
      document.getElementById("p-email").innerText = document.getElementById("email").value;
      document.getElementById("p-phone").innerText = document.getElementById("phone").value;
      document.getElementById("p-field").innerText = document.getElementById("field").value;
      document.getElementById("p-goals").innerText = document.getElementById("goals").value;

      const preview = document.getElementById("preview");
      preview.style.display = "block";

      html2pdf().from(preview).save("anketai-donishju.pdf");
    }
  </script>
</body>
</html>
