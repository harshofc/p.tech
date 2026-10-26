
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Parinda Study | Attendance</title>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #f4f7fc;
  color: #172554;
}

header {
  background: linear-gradient(120deg, #1d4ed8, #6366f1);
  color: white;
  padding: 25px 7%;
}

header h1 {
  margin: 0 0 8px;
  font-size: 30px;
}

header p {
  margin: 0;
  color: #e0e7ff;
}

.container {
  max-width: 1150px;
  margin: 28px auto;
  padding: 0 18px;
}

.topbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 15px;
  flex-wrap: wrap;
  margin-bottom: 22px;
}

.topbar h2 {
  margin: 0 0 6px;
}

.muted {
  color: #64748b;
  font-size: 14px;
}

.stats {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 16px;
  margin-bottom: 24px;
}

.card, .panel {
  background: white;
  border-radius: 15px;
  padding: 22px;
  box-shadow: 0 5px 20px #0f172a0a;
  border: 1px solid #e8edf5;
}

.card p {
  color: #64748b;
  margin: 0 0 12px;
  font-size: 14px;
}

.card h2 {
  font-size: 30px;
  margin: 0;
}

.blue { color: #2563eb; }
.green { color: #16a34a; }
.red { color: #dc2626; }
.purple { color: #7c3aed; }

.toolbar {
  display: flex;
  justify-content: space-between;
  gap: 12px;
  flex-wrap: wrap;
  margin: 20px 0;
}

input {
  padding: 12px 14px;
  border: 1px solid #dbe3ef;
  border-radius: 9px;
  font-size: 15px;
  outline: none;
  background: white;
}

input:focus {
  border-color: #3b82f6;
}

#search {
  flex: 1;
  min-width: 180px;
}

.add-area {
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
}

button {
  border: none;
  border-radius: 8px;
  padding: 11px 14px;
  color: white;
  font-size: 13px;
  font-weight: bold;
  cursor: pointer;
  transition: 0.2s;
}

button:hover {
  filter: brightness(0.93);
  transform: translateY(-1px);
}

.add-btn { background: #2563eb; }
.present-btn { background: #16a34a; }
.absent-btn { background: #dc2626; }
.reset-btn { background: #64748b; }
.save-btn { background: #7c3aed; }

.table-wrap {
  width: 100%;
  overflow-x: auto;
}

table {
  width: 100%;
  border-collapse: collapse;
  min-width: 650px;
}

th {
  text-align: left;
  color: #64748b;
  background: #f8fafc;
  font-size: 12px;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

th, td {
  padding: 16px 12px;
  border-bottom: 1px solid #edf1f7;
}

td {
  font-size: 14px;
}

.student-name {
  font-weight: bold;
}

.status {
  display: inline-block;
  padding: 6px 10px;
  border-radius: 20px;
  font-size: 12px;
  font-weight: bold;
}

.status-present {
  background: #dcfce7;
  color: #166534;
}

.status-absent {
  background: #fee2e2;
  color: #991b1b;
}

.status-pending {
  background: #f1f5f9;
  color: #475569;
}

.actions {
  display: flex;
  gap: 6px;
}

.actions button {
  padding: 9px 10px;
}

.delete-btn {
  background: #e2e8f0;
  color: #334155;
}

.progress-bg {
  height: 8px;
  background: #e2e8f0;
  border-radius: 20px;
  overflow: hidden;
  margin-top: 10px;
}

.progress {
  height: 100%;
  background: #16a34a;
  width: 0%;
  transition: width 0.3s;
}

.footer {
  text-align: center;
  padding: 25px;
  color: #64748b;
  font-size: 13px;
}

.empty {
  text-align: center;
  padding: 30px;
  color: #64748b;
}

@media (max-width: 700px) {
  .stats {
    grid-template-columns: repeat(2, 1fr);
  }

  header {
    padding: 22px 18px;
  }

  header h1 {
    font-size: 24px;
  }

  .card, .panel {
    padding: 16px;
  }
}
</style>
</head>

<body>

<header>
  <h1>📚 Parinda Study</h1>
  <p>Student Attendance Management System</p>
</header>

<div class="container">

  <div class="topbar">
    <div>
      <h2>Dashboard</h2>
      <div class="muted">Manage your students and daily attendance.</div>
    </div>
    <div>
      <input type="date" id="dateInput">
    </div>
  </div>

  <div class="stats">
    <div class="card">
      <p>👨‍🎓 Total Students</p>
      <h2 class="blue" id="total">0</h2>
    </div>

    <div class="card">
      <p>✅ Present Today</p>
      <h2 class="green" id="present">0</h2>
    </div>

    <div class="card">
      <p>❌ Absent Today</p>
      <h2 class="red" id="absent">0</h2>
    </div>

    <div class="card">
      <p>📊 Attendance Rate</p>
      <h2 class="purple" id="rate">0%</h2>
      <div class="progress-bg">
        <div class="progress" id="progress"></div>
      </div>
    </div>
  </div>

  <div class="panel">
    <h2>Student Management</h2>
    <p class="muted">Add students and mark their daily attendance.</p>

    <div class="toolbar">
      <input id="search" placeholder="🔍 Search student name...">

      <div class="add-area">
        <input id="studentName" placeholder="Enter student name">
        <button class="add-btn" onclick="addStudent()">+ Add Student</button>
      </div>
    </div>

    <div class="table-wrap">
      <table>
        <thead>
          <tr>
            <th>No.</th>
            <th>Student Name</th>
            <th>Status</th>
            <th>Mark Attendance</th>
            <th>Delete</th>
          </tr>
        </thead>
        <tbody id="studentList"></tbody>
      </table>
    </div>

    <div id="empty" class="empty" style="display:none">
      No students found. Add a student to get started.
    </div>

    <div class="toolbar" style="margin-bottom:0">
      <button class="save-btn" onclick="saveAttendance()">
        💾 Save Attendance
      </button>
      <button class="reset-btn" onclick="resetAttendance()">
        Reset Today's Attendance
      </button>
    </div>

    <p class="muted" id="message"></p>
  </div>
</div>

<div class="footer">
  © 2026 Parinda Study | Learn • Grow • Succeed
</div>

<script>
let students = JSON.parse(
  localStorage.getItem("parinda_students") || "null"
) || [
  { id: 1, name: "Rahul" },
  { id: 2, name: "Aman" },
  { id: 3, name: "Priya" }
];

let nextId = Math.max(0, ...students.map(s => s.id)) + 1;
let records = JSON.parse(
  localStorage.getItem("parinda_attendance") || "{}"
);

const dateInput = document.getElementById("dateInput");
const search = document.getElementById("search");

function localDate() {
  const d = new Date();
  return d.getFullYear() + "-" +
    String(d.getMonth() + 1).padStart(2, "0") + "-" +
    String(d.getDate()).padStart(2, "0");
}

dateInput.value = localDate();

function currentRecord() {
  const date = dateInput.value;
  if (!records[date]) records[date] = {};
  return records[date];
}

function store() {
  localStorage.setItem("parinda_students", JSON.stringify(students));
  localStorage.setItem("parinda_attendance", JSON.stringify(records));
}

function render() {
  const list = document.getElementById("studentList");
  const record = currentRecord();
  const query = search.value.trim().toLowerCase();

  list.innerHTML = "";

  const filtered = students.filter(s =>
    s.name.toLowerCase().includes(query)
  );

  filtered.forEach((student, index) => {
    const status = record[student.id] || "Not Marked";

    const row = document.createElement("tr");

    const number = document.createElement("td");
    number.textContent = index + 1;

    const nameCell = document.createElement("td");
    nameCell.className = "student-name";
    nameCell.textContent = student.name;

    const statusCell = document.createElement("td");
    const badge = document.createElement("span");
    badge.className = "status " +
      (status === "Present" ? "status-present" :
       status === "Absent" ? "status-absent" : "status-pending");
    badge.textContent = status;
    statusCell.appendChild(badge);

    const actionsCell = document.createElement("td");
    const actions = document.createElement("div");
    actions.className = "actions";

    const p = document.createElement("button");
    p.className = "present-btn";
    p.textContent = "Present";
    p.onclick = () => mark(student.id, "Present");

    const a = document.createElement("button");
    a.className = "absent-btn";
    a.textContent = "Absent";
    a.onclick = () => mark(student.id, "Absent");

    actions.append(p, a);
    actionsCell.appendChild(actions);

    const deleteCell = document.createElement("td");
    const del = document.createElement("button");
    del.className = "delete-btn";
    del.textContent = "Delete";
    del.onclick = () => deleteStudent(student.id);
    deleteCell.appendChild(del);

    row.append(number, nameCell, statusCell, actionsCell, deleteCell);
    list.appendChild(row);
  });

  document.getElementById("empty").style.display =
    filtered.length ? "none" : "block";

  const values = students.map(s => record[s.id] || "Not Marked");
  const presentCount = values.filter(s => s === "Present").length;
  const absentCount = values.filter(s => s === "Absent").length;
  const marked = presentCount + absentCount;
  const rate = marked ? Math.round(presentCount / marked * 100) : 0;

  document.getElementById("total").textContent = students.length;
  document.getElementById("present").textContent = presentCount;
  document.getElementById("absent").textContent = absentCount;
  document.getElementById("rate").textContent = rate + "%";
  document.getElementById("progress").style.width = rate + "%";
}

function mark(id, status) {
  currentRecord()[id] = status;
  store();
  render();
}

function addStudent() {
  const input = document.getElementById("studentName");
  const name = input.value.trim();

  if (!name) {
    alert("Please enter a student name!");
    return;
  }

  if (students.some(s => s.name.toLowerCase() === name.toLowerCase())) {
    alert("This student already exists!");
    return;
  }

  students.push({ id: nextId++, name: name });
  input.value = "";
  store();
  render();
  document.getElementById("message").textContent =
    "Student added successfully.";
}

function deleteStudent(id) {
  const student = students.find(s => s.id === id);
  if (!student) return;

  if (!confirm("Delete " + student.name + "?")) return;

  students = students.filter(s => s.id !== id);
  Object.values(records).forEach(record => delete record[id]);
  store();
  render();
}

function saveAttendance() {
  store();
  document.getElementById("message").textContent =
    "Attendance saved for " + dateInput.value + ".";
}

function resetAttendance() {
  if (!confirm("Reset attendance for " + dateInput.value + "?")) return;

  records[dateInput.value] = {};
  store();
  render();

  document.getElementById("message").textContent =
    "Today's attendance has been reset.";
}

search.addEventListener("input", render);
dateInput.addEventListener("change", render);

document.getElementById("studentName").addEventListener("keydown", e => {
  if (e.key === "Enter") addStudent();
});

render();
</script>

</body>
</html>
