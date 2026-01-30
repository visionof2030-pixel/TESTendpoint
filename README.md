<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <title>أداة مقفلة بكود تفعيل</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      direction: rtl;
      background: #f5f5f5;
      padding: 30px;
    }
    .box {
      background: white;
      padding: 20px;
      max-width: 400px;
      margin: auto;
      border-radius: 8px;
      box-shadow: 0 0 10px rgba(0,0,0,.1);
    }
    input, textarea, button {
      width: 100%;
      margin-top: 10px;
      padding: 10px;
      font-size: 16px;
    }
    button {
      background: #4CAF50;
      color: white;
      border: none;
      cursor: pointer;
    }
    pre {
      background: #eee;
      padding: 10px;
      margin-top: 15px;
      white-space: pre-wrap;
    }
  </style>
</head>
<body>

  <div class="box">
    <h3>أداة مقفلة بكود تفعيل</h3>

    <input
      id="code"
      placeholder="أدخل كود التفعيل"
    />

    <textarea
      id="prompt"
      rows="4"
      placeholder="اكتب سؤالك هنا"
    ></textarea>

    <button onclick="send()">إرسال</button>

    <pre id="result"></pre>
  </div>

  <script>
    function send() {
      const code = document.getElementById("code").value;
      const prompt = document.getElementById("prompt").value;
      const result = document.getElementById("result");

      result.textContent = "جاري الإرسال...";

      fetch("https://deep2-0z0k.onrender.com/activate", {
        method: "POST",
        headers: {
          "Content-Type": "application/json"
        },
        body: JSON.stringify({
          code: code,
          prompt: prompt
        })
      })
      .then(res => res.json())
      .then(data => {
        if (data.answer) {
          result.textContent = data.answer;
        } else {
          result.textContent = JSON.stringify(data, null, 2);
        }
      })
      .catch(err => {
        result.textContent = "خطأ في الاتصال بالسيرفر";
      });
    }
  </script>

</body>
</html>
