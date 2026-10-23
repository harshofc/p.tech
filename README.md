# p.tech 




<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Attendance Management</title>
  <style>
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: #f1f5f9;
      color: #1e293b;
    }

    header {
      background: #2563eb;
      color: white;
      text-align: center;
      padding: 25px 15px;
    }

    header h1 {
      margin: 0 0 8px;
    }

    .container {
      max-width: 850px;
      margin: 25px auto;
      padding: 0 15px;
    }

    .stats {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 12px;
      margin-bottom: 20px;
    }

    .stat {
      background: white;
      padding: 18px 8px;
      text-align: center;
      border-radius: 12px;
      box-shadow: 0 2px 8px #0000000d;
    }

    .stat h2 {
      margin: 0 0 8px;
      font-size: 26px;
    }

    .present-color { color: #16a34a; }
    .absent-color { color: #dc2626; }

    .panel {
      background: white;
      border-radius: 12px;
      padding: 20px;
      box-shadow: 0 2px 8px #0000000d;
    }

    .add-box {
      display: flex;
      gap: 10px;
      margin-bottom: 18px;
    }

    input {
      flex: 1;
      min-width: 0;
      padding: 12px;
      border: 1px solid #cbd5e1;
      border-radius: 8px;
      font-size: 16px;
    }

    button {
      border: 0;
      padding: 10px 13px;
      border-radius: 7px;
      color: white;
      cursor: pointer;
      font-size: 14px;
    }

    .add-btn { background: #2563eb; }

    .student {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 12px;
      padding: 14px 0;
      border-bottom: 1px solid #e2e8f0;
    }

    .student-name {
      font-weight: bold;
      overflow-wrap: anywhere;
    }

    .actions {
      display: flex;
      gap: 6px;
      flex-shrink: 0;
    }

    .p-btn { background: #16a34a; }
    .a-btn { background: #dc2626; }
    .delete-btn { background: #64748b; }

    .status {
      display: block;
      font-size: 12px;
      margin-top: 5px;
      color: #64748b;
    }

    .empty {
      text-align: center;
      color: #64748b;
      padding: 20px 0;
    }

    @media (max-width: 480px) {
      .student {
        align-items: flex-start;
      }
      .actions {
        flex-wrap: wrap;
        justify-content: flex-end;
      }
      button {
        padding: 9px;
      }
    }
  </style>
</head>
<body>

<header>
  <h1>📋 Attendance System</h1>
  <div>Student Present / Absent Management</div>
</header>

<div class="container">
  <div class="stats">
    <div class="stat">
      <h2 id="total">3</h2>
      Total Students
    </div>
    <div class="stat">
      <h2 id="present" class="present-color">0</h2>
      Present
    </div>
    <div class="stat">
      <h2 id="absent" class="absent-color">0</h2>
      Absent
    </div>
  </div>

  <div class="panel">
    <h2>Manage Attendance</h2>
    <p id="today"></p>

    <div class="add-box">
      <input id="nameInput" placeholder="Enter student name">
      <button class="add-btn" onclick="addStudent()">+ Add</button>
    </div>

    <div id="studentList"></div>
  </div>
</div>

<script>
  let students = [
    { name: "Rahul", status: "Not Marked" },
    { name: "Aman", status: "Not Marked" },
    { name: "Priya", status: "Not Marked" }
  ];

  document.getElementById("today").textContent =
    "Date: " + new Date().toLocaleDateString("en-IN");

  function render() {
    const list = document.getElementById("studentList");
    list.innerHTML = "";

    students.forEach((student, index) => {
      const row = document.createElement("div");
      row.className = "student";

      const info = document.createElement("div");
      const name = document.createElement("div");
      name.className = "student-name";
      name.textContent = (index + 1) + ". " + student.name;

      const status = document.createElement("span");
      status.className = "status";
      status.textContent = "Status: " + student.status;

      if (student.status === "Present") {
        status.style.color = "#16a34a";
      } else if (student.status === "Absent") {
        status.style.color = "#dc2626";
      }

      info.append(name, status);

      const actions = document.createElement("div");
      actions.className = "actions";

      const presentBtn = document.createElement("button");
      presentBtn.className = "p-btn";
      presentBtn.textContent = "Present";
      presentBtn.onclick = () => mark(index, "Present");

      const absentBtn = document.createElement("button");
      absentBtn.className = "a-btn";
      absentBtn.textContent = "Absent";
      absentBtn.onclick = () => mark(index, "Absent");

      const deleteBtn = document.createElement("button");
      deleteBtn.className = "delete-btn";
      deleteBtn.textContent = "Delete";
      deleteBtn.onclick = () => {
        students.splice(index, 1);
        render();
      };

      actions.append(presentBtn, absentBtn, deleteBtn);
      row.append(info, actions);
      list.appendChild(row);
    });

    if (students.length === 0) {
      list.innerHTML = '<div class="empty">No students added yet.</div>';
    }

    document.getElementById("total").textContent = students.length;
    document.getElementById("present").textContent =
      students.filter(s => s.status === "Present").length;
    document.getElementById("absent").textContent =
      students.filter(s => s.status === "Absent").length;
  }

  function mark(index, status) {
    students[index].status = status;
    render();
  }

  function addStudent() {
    const input = document.getElementById("nameInput");
    const name = input.value.trim();

    if (!name) {
      alert("Please enter student name!");
      return;
    }

    students.push({ name: name, status: "Not Marked" });
    input.value = "";
    render();
  }

  document.getElementById("nameInput").addEventListener("keydown", e => {
    if (e.key === "Enter") addStudent();
  });

  render();
</script>

</body>
</html>
