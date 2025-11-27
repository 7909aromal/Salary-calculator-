<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>A - Monthly Hour Calculator</title>
  <style>
    /* --- CSS VARIABLES --- */
    :root {
      /* Light Mode Palette */
      --bg: linear-gradient(135deg, #e0c3fc, #8ec5fc);
      --container-bg: rgba(255, 255, 255, 0.95);
      --text: #333;
      --input-bg: #ffffff;
      --input-border: #ddd;
      --table-border: #eee;
      --button-bg: #6c5ce7;
      --button-hover: #5649c0;
      --danger: #ff7675;
      --shadow: 0px 10px 30px rgba(0,0,0,0.1);
    }

    /* Professional Dark Mode Palette */
    body.dark {
      --bg: linear-gradient(135deg, #0f172a, #1e293b); /* Slate Dark */
      --container-bg: #1e293b;
      --text: #e2e8f0; /* Off-white for readability */
      --input-bg: #334155;
      --input-border: #475569;
      --table-border: #475569;
      --button-bg: #6366f1; /* Indigo */
      --button-hover: #4f46e5;
      --danger: #ef4444;
      --shadow: 0px 10px 30px rgba(0,0,0,0.5);
    }

    body {
      font-family: 'Segoe UI', Poppins, sans-serif;
      background: var(--bg);
      padding: 20px;
      color: var(--text);
      transition: background 0.5s ease, color 0.3s ease;
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .container {
      width: 100%;
      max-width: 600px;
      background: var(--container-bg);
      padding: 30px;
      border-radius: 24px;
      box-shadow: var(--shadow);
      position: relative; /* Needed for toggle positioning */
      backdrop-filter: blur(10px); /* Glassmorphism effect */
    }

    /* --- THEME TOGGLE SWITCH --- */
    .theme-toggle {
      position: absolute;
      top: 25px;
      right: 25px;
      background: transparent;
      border: 1px solid var(--input-border);
      color: var(--text);
      font-size: 1.2rem;
      width: 40px;
      height: 40px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      transition: all 0.3s ease;
    }

    .theme-toggle:hover {
      background: var(--button-bg);
      color: white;
      border-color: var(--button-bg);
      transform: rotate(15deg);
    }

    .logo {
      width: 70px;
      height: 70px;
      background: linear-gradient(135deg, #6c5ce7, #a29bfe);
      border-radius: 18px;
      display: flex;
      justify-content: center;
      align-items: center;
      margin: 0 auto 15px;
      color: white;
      font-size: 32px;
      font-weight: bold;
      box-shadow: 0 4px 15px rgba(108, 92, 231, 0.4);
    }

    h2 {
      text-align: center;
      margin-bottom: 25px;
      font-weight: 700;
    }

    label {
      font-size: 0.9rem;
      font-weight: 600;
      margin-top: 10px;
      display: block;
      color: var(--text);
      opacity: 0.9;
    }

    /* Inputs adapted for Dark Mode */
    input, select {
      width: 100%;
      padding: 12px 15px;
      margin: 5px 0 15px;
      border-radius: 10px;
      border: 1px solid var(--input-border);
      background: var(--input-bg);
      color: var(--text);
      font-size: 15px;
      transition: 0.3s;
      box-sizing: border-box;
    }

    input:focus, select:focus {
      outline: none;
      border-color: var(--button-bg);
      box-shadow: 0 0 0 3px rgba(99, 102, 241, 0.2);
    }

    button.action-btn {
      width: 100%;
      padding: 14px;
      background: var(--button-bg);
      color: white;
      border: none;
      border-radius: 12px;
      font-size: 16px;
      font-weight: 600;
      cursor: pointer;
      margin-top: 5px;
      transition: transform 0.2s, background 0.3s;
    }

    button.action-btn:hover {
      background: var(--button-hover);
      transform: translateY(-2px);
    }

    button.action-btn:active {
      transform: translateY(0);
    }

    /* Table Styling */
    .table-container {
      overflow-x: auto;
      margin-top: 20px;
      border-radius: 12px;
      border: 1px solid var(--table-border);
    }

    table {
      width: 100%;
      border-collapse: collapse;
      font-size: 14px;
    }

    th, td {
      padding: 12px;
      text-align: left;
      border-bottom: 1px solid var(--table-border);
    }

    th {
      background: rgba(0,0,0,0.05);
    }
    
    body.dark th {
      background: rgba(255,255,255,0.05);
    }

    tr:last-child td {
      border-bottom: none;
    }

    .result {
      margin-top: 20px;
      font-size: 1.1rem;
      font-weight: bold;
      text-align: center;
      background: var(--button-bg);
      color: white;
      padding: 15px;
      border-radius: 12px;
      box-shadow: 0 4px 15px rgba(0,0,0,0.1);
    }

    .clearBtn {
      background: transparent;
      border: 1px solid var(--danger);
      color: var(--danger);
      margin-top: 15px;
    }

    .clearBtn:hover {
      background: var(--danger);
      color: white;
    }

    .credits {
      text-align: center;
      margin-top: 20px;
      font-size: 12px;
      opacity: 0.6;
    }

  </style>
</head>
<body>

  <div class="container">
    <button class="theme-toggle" onclick="toggleDarkMode()" id="themeBtn" title="Toggle Dark Mode">
      🌙
    </button>

    <div class="logo">A</div>
    <h2>Monthly Calculator<br><span style="font-size:0.6em; opacity:0.7">Party Time Jones</span></h2>

    <label>Employee Type</label>
    <select id="empType">
      <option value="Chef">Chef</option>
      <option value="Cleaning Staff">Cleaning Staff</option>
      <option value="Visitor">Visitor</option>
      <option value="Kitchen Helper">Kitchen Helper</option>
      <option value="Delivery Boy">Delivery Boy</option>
      <option value="Account Manager">Account Manager</option>
      <option value="Manager">Manager</option>
      <option value="Normal Staff">Normal Staff</option>
    </select>

    <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 15px;">
      <div>
        <label>Login Time</label>
        <input type="time" id="login">
      </div>
      <div>
        <label>Logout Time</label>
        <input type="time" id="logout">
      </div>
    </div>

    <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 15px;">
      <div>
        <label>Break Start</label>
        <input type="time" id="breakStart">
      </div>
      <div>
        <label>Break End</label>
        <input type="time" id="breakEnd">
      </div>
    </div>

    <button class="action-btn" onclick="addDay()">+ Add Day</button>

    <div class="table-container">
      <table id="dayTable">
        <thead>
          <tr>
            <th>Day</th>
            <th>Role</th>
            <th>Total</th>
            <th>Break</th>
            <th>Paid</th>
          </tr>
        </thead>
        <tbody>
          </tbody>
      </table>
    </div>

    <label>Hourly Wage ($)</label>
    <input type="number" id="rate" placeholder="0.00" oninput="autoSaveRate()">

    <button class="action-btn" onclick="calculateMonth()">Calculate Salary</button>

    <div class="result" id="monthResult">Result will appear here...</div>

    <button class="action-btn clearBtn" onclick="clearAll()">Reset Data</button>

    <div class="credits">
      Created by Aromal & AI
    </div>
  </div>

  <script>
    let dayCount = 0;
    let totalMonthlyPaidHours = 0;

    // Load saved data
    window.onload = () => {
      // Load Data
      if (localStorage.getItem("daysData")) {
        const saved = JSON.parse(localStorage.getItem("daysData"));
        saved.forEach(d => addRowFromSave(d));
      }
      if (localStorage.getItem("rate"))
        document.getElementById("rate").value = localStorage.getItem("rate");
      if (localStorage.getItem("totalPaid"))
        totalMonthlyPaidHours = parseFloat(localStorage.getItem("totalPaid"));

      // Load Theme
      const isDark = localStorage.getItem("darkMode") === "true";
      if (isDark) {
        document.body.classList.add("dark");
        document.getElementById("themeBtn").innerText = "☀️";
      }
    };

    function autoSaveRate() {
      localStorage.setItem("rate", document.getElementById("rate").value);
    }

    function addDay() {
      const empType = document.getElementById("empType").value;
      const login = document.getElementById('login').value;
      const logout = document.getElementById('logout').value;
      const breakStart = document.getElementById('breakStart').value;
      const breakEnd = document.getElementById('breakEnd').value;

      if (!login || !logout || !breakStart || !breakEnd) {
        alert("Please fill all time fields.");
        return;
      }

      const data = calculateHours(login, logout, breakStart, breakEnd, empType);
      saveDay(data);
      addRowFromSave(data);
    }

    function calculateHours(login, logout, breakStart, breakEnd, empType) {
      const start = new Date(`2020-01-01T${login}:00`);
      const end = new Date(`2020-01-01T${logout}:00`);
      const bStart = new Date(`2020-01-01T${breakStart}:00`);
      const bEnd = new Date(`2020-01-01T${breakEnd}:00`);

      let totalHours = (end - start) / 3600000;
      let breakHours = (bEnd - bStart) / 3600000;

      if (totalHours < 0) totalHours += 24;
      if (breakHours < 0) breakHours += 24;

      let paidHours = totalHours - breakHours;
      if (paidHours < 0) paidHours = 0;

      totalMonthlyPaidHours += paidHours;
      localStorage.setItem("totalPaid", totalMonthlyPaidHours);

      return { empType, totalHours, breakHours, paidHours };
    }

    function saveDay(data) {
      let list = JSON.parse(localStorage.getItem("daysData") || "[]");
      list.push(data);
      localStorage.setItem("daysData", JSON.stringify(list));
    }

    function addRowFromSave(d) {
      dayCount++;
      const table = document.getElementById('dayTable').getElementsByTagName('tbody')[0];
      const row = table.insertRow();
      
      row.insertCell(0).innerText = dayCount;
      row.insertCell(1).innerText = d.empType;
      row.insertCell(2).innerText = d.totalHours.toFixed(2);
      row.insertCell(3).innerText = d.breakHours.toFixed(2);
      row.insertCell(4).innerText = d.paidHours.toFixed(2);
    }

    function calculateMonth() {
      const rate = parseFloat(document.getElementById('rate').value);
      if (isNaN(rate)) {
        alert("Please enter an hourly wage.");
        return;
      }
      const totalPay = totalMonthlyPaidHours * rate;
      document.getElementById('monthResult').innerText = 
        `Paid Hours: ${totalMonthlyPaidHours.toFixed(2)} hrs | Salary: $${totalPay.toFixed(2)}`;
    }

    function clearAll() {
      if (confirm("Are you sure you want to clear all saved data?")) {
        localStorage.clear();
        location.reload();
      }
    }

    // Professional Dark Mode Toggle Logic
    function toggleDarkMode() {
      const body = document.body;
      const btn = document.getElementById("themeBtn");
      
      body.classList.toggle("dark");
      
      if (body.classList.contains("dark")) {
        btn.innerText = "☀️"; // Sun icon for light mode switch
        localStorage.setItem("darkMode", "true");
      } else {
        btn.innerText = "🌙"; // Moon icon for dark mode switch
        localStorage.setItem("darkMode", "false");
      }
    }
  </script>
</body>
</html>
