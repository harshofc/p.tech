<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Parinda Study Management</title>

<style>
*{box-sizing:border-box}
body{
 margin:0;
 font-family:Arial,sans-serif;
 background:#f1f5f9;
 color:#172554;
}
header{
 background:linear-gradient(120deg,#1d4ed8,#6366f1);
 color:white;padding:25px 7%;
}
header h1{margin:0 0 8px}
.container{max-width:1150px;margin:25px auto;padding:0 18px}
.panel,.card{
 background:white;padding:20px;border-radius:12px;
 border:1px solid #e5e7eb;margin-bottom:18px;
}
.stats{
 display:grid;grid-template-columns:repeat(4,1fr);gap:12px;
}
.card p{color:#64748b;font-size:14px}
.card h2{margin:5px 0}
input,select{
 padding:11px;border:1px solid #cbd5e1;
 border-radius:7px;margin:5px;font-size:14px;
}
button{
 border:0;padding:10px 14px;border-radius:7px;
 color:white;cursor:pointer;margin:3px;
}
button:hover{opacity:.85}
.blue{background:#2563eb}
.green{background:#16a34a}
.red{background:#dc2626}
.purple{background:#7c3aed}
.gray{background:#64748b}
.tabs{margin:20px 0}
.tabs button{background:#334155}
.tabs button.active{background:#2563eb}
.table-wrap{overflow-x:auto}
table{width:100%;border-collapse:collapse;min-width:650px}
th,td{
 padding:14px;text-align:left;border-bottom:1px solid #e5e7eb;
}
th{background:#f8fafc;color:#64748b;font-size:12px}
.status{font-weight:bold}
.paid{color:#16a34a}
.partial{color:#d97706}
.unpaid{color:#dc2626}
.footer{text-align:center;padding:25px;color:#64748b}
@media(max-width:700px){
 .stats{grid-template-columns:repeat(2,1fr)}
 header{padding:20px}
 .panel,.card{padding:14px}
}
</style>
</head>

<body>

<header>
<h1>📚 Parinda Study</h1>
<p>Student Attendance & Monthly Fees Management</p>
</header>

<div class="container">

<div class="tabs">
<button class="active" onclick="showPage('attendance',this)">Attendance</button>
<button onclick="showPage('fees',this)">Monthly Fees</button>
</div>

<!-- ATTENDANCE -->

<section id="attendance">

<h2>Attendance Dashboard</h2>

<div class="stats">
<div class="card"><p>Total Students</p><h2 id="total">0</h2></div>
<div class="card"><p>Present</p><h2 id="present">0</h2></div>
<div class="card"><p>Absent</p><h2 id="absent">0</h2></div>
<div class="card"><p>Attendance Rate</p><h2 id="rate">0%</h2></div>
</div>

<div class="panel">
<h2>Student Management</h2>

<input id="studentName" placeholder="Student Name">
<button class="blue" onclick="addStudent()">+ Add Student</button>

<br>
<input id="search" placeholder="Search student..." oninput="render()">
<input type="date" id="date">

<div class="table-wrap">
<table>
<thead>
<tr>
<th>No.</th>
<th>Student Name</th>
<th>Status</th>
<th>Action</th>
</tr>
</thead>
<tbody id="studentList"></tbody>
</table>
</div>
</div>
</section>

<!-- MONTHLY FEES -->

<section id="fees" style="display:none">

<h2>Monthly Fees Dashboard</h2>

<div class="panel">
<label>Select Month:</label>
<select id="month" onchange="renderFees()">
</select>
</div>

<div class="stats">
<div class="card"><p>Total Fees</p><h2 id="totalFees">₹0</h2></div>
<div class="card"><p>Collected Fees</p><h2 id="collected">₹0</h2></div>
<div class="card"><p>Pending Fees</p><h2 id="pending">₹0</h2></div>
<div class="card"><p>Total Students</p><h2 id="feeStudents">0</h2></div>
</div>

<div class="panel">
<h2>Monthly Student Fees</h2>

<input id="feeSearch" placeholder="Search student..." oninput="renderFees()">

<div class="table-wrap">
<table>
<thead>
<tr>
<th>Student</th>
<th>Monthly Fees</th>
<th>Paid</th>
<th>Remaining</th>
<th>Status</th>
<th>Action</th>
</tr>
</thead>
<tbody id="feeList"></tbody>
</table>
</div>
</div>

<div class="panel">
<h2>Payment History</h2>
<div class="table-wrap">
<table>
<thead>
<tr>
<th>Student</th>
<th>Month</th>
<th>Amount</th>
<th>Payment Date</th>
</tr>
</thead>
<tbody id="history"></tbody>
</table>
</div>
</div>

</section>

</div>

<div class="footer">
© 2026 Parinda Study | Learn • Grow • Succeed
</div>

<script>

let students=JSON.parse(localStorage.getItem("ps_students"))||[];
let attendance=JSON.parse(localStorage.getItem("ps_attendance"))||{};
let fees=JSON.parse(localStorage.getItem("ps_fees"))||{};

let nextId=Math.max(0,...students.map(s=>s.id))+1;

let months=[
"January","February","March","April",
"May","June","July","August",
"September","October","November","December"
];

let month=document.getElementById("month");

months.forEach((m,i)=>{
let option=document.createElement("option");
option.value=new Date().getFullYear()+"-"+String(i+1).padStart(2,"0");
option.textContent=m+" "+new Date().getFullYear();
month.appendChild(option);
});

month.value=new Date().getFullYear()+"-"+String(new Date().getMonth()+1).padStart(2,"0");

let date=document.getElementById("date");
date.value=new Date().toLocaleDateString("en-CA");

function save(){
localStorage.setItem("ps_students",JSON.stringify(students));
localStorage.setItem("ps_attendance",JSON.stringify(attendance));
localStorage.setItem("ps_fees",JSON.stringify(fees));
}

function showPage(page,btn){
document.getElementById("attendance").style.display=
page==="attendance"?"block":"none";

document.getElementById("fees").style.display=
page==="fees"?"block":"none";

document.querySelectorAll(".tabs button").forEach(b=>b.classList.remove("active"));
btn.classList.add("active");

render();
renderFees();
}

function addStudent(){
let name=document.getElementById("studentName").value.trim();

if(!name)return alert("Enter student name");

if(students.some(s=>s.name.toLowerCase()===name.toLowerCase()))
return alert("Student already exists!");

students.push({id:nextId++,name:name});
document.getElementById("studentName").value="";

save();
render();
renderFees();
}

function deleteStudent(id){
let s=students.find(x=>x.id===id);
if(!s || !confirm("Delete "+s.name+"?"))return;

students=students.filter(x=>x.id!==id);

Object.values(attendance).forEach(r=>delete r[id]);
delete fees[id];

save();
render();
renderFees();
}

function render(){

let list=document.getElementById("studentList");
list.innerHTML="";

let record=attendance[date.value]||{};
let query=document.getElementById("search").value.toLowerCase();

students.filter(s=>s.name.toLowerCase().includes(query))
.forEach((s,i)=>{

let status=record[s.id]||"Not Marked";
let tr=document.createElement("tr");

tr.innerHTML=`
<td>${i+1}</td>
<td></td>
<td>${status}</td>
<td>
<button class="green" onclick="mark(${s.id},'Present')">Present</button>
<button class="red" onclick="mark(${s.id},'Absent')">Absent</button>
<button class="gray" onclick="deleteStudent(${s.id})">Delete</button>
</td>`;

tr.children[1].textContent=s.name;
list.appendChild(tr);
});

let values=students.map(s=>record[s.id]);
let p=values.filter(v=>v==="Present").length;
let a=values.filter(v=>v==="Absent").length;
let marked=p+a;

document.getElementById("total").textContent=students.length;
document.getElementById("present").textContent=p;
document.getElementById("absent").textContent=a;
document.getElementById("rate").textContent=
(marked?Math.round(p/marked*100):0)+"%";
}

function mark(id,status){
if(!attendance[date.value])attendance[date.value]={};
attendance[date.value][id]=status;
save();
render();
}

date.addEventListener("change",render);

function getFee(id){
if(!fees[id])fees[id]={monthly:0,records:{}};
if(!fees[id].records)fees[id].records={};
return fees[id];
}

function renderFees(){

let list=document.getElementById("feeList");
let history=document.getElementById("history");

list.innerHTML="";
history.innerHTML="";

let total=0,collected=0;
let selectedMonth=month.value;
let query=document.getElementById("feeSearch").value.toLowerCase();

students.filter(s=>s.name.toLowerCase().includes(query))
.forEach(s=>{

let f=getFee(s.id);
let r=f.records[selectedMonth]||{paid:0,payments:[]};

let remaining=Math.max(0,f.monthly-r.paid);

let status=f.monthly===0?"Not Set":
r.paid>=f.monthly?"Paid":
r.paid>0?"Partial":"Unpaid";

total+=f.monthly;
collected+=r.paid;

let tr=document.createElement("tr");

let cells=[
s.name,"₹"+f.monthly,"₹"+r.paid,
"₹"+remaining,status
];

cells.forEach((value,i)=>{
let td=document.createElement("td");
td.textContent=value;
if(i===4){
td.className=status==="Paid"?"paid":
status==="Partial"?"partial":"unpaid";
}
tr.appendChild(td);
});

let action=document.createElement("td");

let set=document.createElement("button");
set.className="purple";
set.textContent="Set Fees";

set.onclick=()=>{
let amount=prompt("Enter monthly fees:",f.monthly);
if(amount===null)return;

amount=Number(amount);

if(!Number.isFinite(amount)||amount<0)
return alert("Enter valid fees");

if(amount<r.paid)
return alert("Fees cannot be less than already paid amount");

f.monthly=amount;
save();
renderFees();
};

let pay=document.createElement("button");
pay.className="green";
pay.textContent="Add Payment";

pay.onclick=()=>{
if(f.monthly<=0)return alert("First set monthly fees");

let amount=prompt("Enter payment amount:",remaining);
if(amount===null)return;

amount=Number(amount);

if(!Number.isFinite(amount)||amount<=0)
return alert("Enter valid payment");

if(r.paid+amount>f.monthly)
return alert("Payment is greater than remaining fees");

r.paid+=amount;

r.payments.push({
amount:amount,
date:new Date().toLocaleDateString("en-IN")
});

f.records[selectedMonth]=r;

save();
renderFees();
};

action.append(set,pay);
tr.appendChild(action);
list.appendChild(tr);

});

// Payment History

students.forEach(s=>{
let f=getFee(s.id);

Object.entries(f.records).forEach(([m,r])=>{
(r.payments||[]).forEach(payment=>{

let tr=document.createElement("tr");

[s.name,formatMonth(m),"₹"+payment.amount,payment.date]
.forEach(value=>{
let td=document.createElement("td");
td.textContent=value;
tr.appendChild(td);
});

history.appendChild(tr);

});
});
});

document.getElementById("totalFees").textContent="₹"+total;
document.getElementById("collected").textContent="₹"+collected;
document.getElementById("pending").textContent="₹"+(total-collected);
document.getElementById("feeStudents").textContent=students.length;

}

function formatMonth(value){
let [year,m]=value.split("-");
return months[Number(m)-1]+" "+year;
}

render();
renderFees();

</script>
</body>
</html>
