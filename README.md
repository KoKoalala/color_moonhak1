# color_moonhak1
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <title>시 색채 시각화</title>
  <style>
    .highlight {
      padding: 2px 4px;
      border-radius: 4px;
      font-weight: bold;
    }
    .red { background-color: #ffcccc; }
    .blue { background-color: #cce5ff; }
    .black { background-color: #d9d9d9; color: #000; }
    .white { background-color: #f9f9f9; }
  </style>
</head>
<body>
  <h2>📜 시 색채 시각화</h2>
  <textarea id="poem" rows="8" cols="50" placeholder="여기에 시를 입력하세요..."></textarea><br>
  <button onclick="analyze()">색채 분석</button>
  <div id="result"></div>

  <script>
    const colors = {
      "붉": "red",
      "빨": "red",
      "푸르": "blue",
      "파랗": "blue",
      "파란": "blue",
      "검": "black",
      "까맣": "black",
      "하얗": "white",
      "희": "white"
    };

    function analyze() {
      const lines = document.getElementById("poem").value.split('\n');
      const resultDiv = document.getElementById("result");
      resultDiv.innerHTML = "";

      lines.forEach(line => {
        let newLine = line;

        for (let key in colors) {
          const colorClass = colors[key];
          // 정규식으로 해당 색채어 포함 단어를 찾아서 <span>으로 감싸기
          const regex = new RegExp(`(${key}\\S*)`, 'g');
          newLine = newLine.replace(regex, `<span class="highlight ${colorClass}">$1</span>`);
        }

        const div = document.createElement("div");
        div.className = "line";
        div.innerHTML = newLine;  // innerText가 아니라 innerHTML로!
        resultDiv.appendChild(div);
      });
    }
  </script>
</body>
</html>
