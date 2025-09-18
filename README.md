[index.html](https://github.com/user-attachments/files/22400936/index.html)
<!doctype html>
<html lang="zh-Hans">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>DSR 在线计算器</title>
  <style>
    body{font-family:sans-serif;background:#f9fafb;color:#111;padding:20px}
    .card{max-width:600px;margin:0 auto;background:#fff;padding:20px;border-radius:10px;box-shadow:0 4px 12px rgba(0,0,0,0.05)}
    h1{font-size:20px;margin-bottom:10px}
    label{display:block;font-size:14px;margin-top:10px;margin-bottom:4px}
    input{width:100%;padding:8px;border:1px solid #ddd;border-radius:6px}
    button{margin-top:14px;padding:10px 14px;border:none;border-radius:6px;background:#0366d6;color:#fff;cursor:pointer}
    .result{margin-top:16px;padding:12px;background:#f1f5f9;border-radius:8px}
    .big{font-size:22px;font-weight:bold}
  </style>
</head>
<body>
  <div class="card">
    <h1>DSR 在线计算器</h1>
    <label for="income">月收入 (RM)</label>
    <input id="income" type="number" value="9900">

    <label for="mortgage">房贷月供 (RM)</label>
    <input id="mortgage" type="number" value="1548">

    <label for="car">车贷月供 (RM)</label>
    <input id="car" type="number" value="0">

    <label for="cc">信用卡还款 (RM)</label>
    <input id="cc" type="number" value="0">

    <label for="personal">个人贷款月供 (RM)</label>
    <input id="personal" type="number" value="0">

    <button id="calc">计算 DSR</button>

    <div class="result" id="result">
      <div>每月总债务：<span class="big" id="total">RM 0.00</span></div>
      <div>DSR：<span class="big" id="dsr">0%</span></div>
    </div>
  </div>

  <script>
    function money(v){return Number(v).toLocaleString(undefined,{minimumFractionDigits:2,maximumFractionDigits:2});}
    function pct(v){return v.toFixed(2)+'%';}

    function compute(){
      const i = parseFloat(document.getElementById('income').value)||0;
      const m = parseFloat(document.getElementById('mortgage').value)||0;
      const c = parseFloat(document.getElementById('car').value)||0;
      const cc = parseFloat(document.getElementById('cc').value)||0;
      const p = parseFloat(document.getElementById('personal').value)||0;
      const total = m+c+cc+p;
      const ratio = i===0?0:(total/i*100);
      document.getElementById('total').textContent = 'RM '+money(total);
      document.getElementById('dsr').textContent = pct(ratio);
    }

    document.getElementById('calc').addEventListener('click', compute);
    compute();
  </script>
</body>
</html>
