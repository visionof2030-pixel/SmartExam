<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<title>المنصة الذكية للاختبارات والتلخيص</title>
<style>
body{font-family:Tajawal;background:#0A3D62;color:white;padding:20px}
.container{max-width:900px;margin:auto;background:#1A5F7A;padding:25px;border-radius:15px}
.option{border:1px solid #ccc;padding:12px;margin:8px 0;cursor:pointer;border-radius:6px}
.option.correct{background:#4CAF50}
.option.incorrect{background:#dc2626}
.feedback{background:#0f766e;padding:10px;margin-top:5px;border-radius:6px}
.hidden{display:none}
</style>
</head>
<body>

<div class="container">

<select id="mode">
<option value="manual">اختبار يدوي</option>
<option value="file">اختبار من ملف</option>
<option value="summary">تلخيص ملف</option>
</select>

<div id="manual">
<textarea id="topic" placeholder="اكتب موضوع الاختبار"></textarea>
<select id="lang"><option value="ar">عربي</option><option value="en">English</option></select>
<button onclick="manual()">ابدأ</button>
</div>

<div id="file" class="hidden">
<input type="file" id="fileInput">
<select id="fileLang"><option value="ar">عربي</option><option value="en">English</option></select>
<button onclick="fileQuiz()">ابدأ</button>
</div>

<div id="summary" class="hidden">
<input type="file" id="sumFile">
<select id="sumLang"><option value="ar">عربي</option><option value="en">English</option></select>
<button onclick="summarize()">تلخيص</button>
</div>

<div id="result"></div>
<button id="nextBtn" class="hidden" onclick="next()">التالي</button>
</div>

<script>
const BACKEND="https://smarttest-0ycc.onrender.com"
let questions=[],answers=[],i=0

document.getElementById("mode").onchange=e=>{
["manual","file","summary"].forEach(x=>document.getElementById(x).classList.add("hidden"))
document.getElementById(e.target.value).classList.remove("hidden")
document.getElementById("result").innerHTML=""
}

function parse(t){return JSON.parse(t.replace(/```json|```/g,""))}

async function manual(){
const res=await fetch(BACKEND+"/ask",{method:"POST",headers:{"Content-Type":"application/json"},
body:JSON.stringify({prompt:topic.value,language:lang.value})})
const d=await res.json()
questions=parse(d.result).questions
answers=new Array(questions.length).fill(null)
i=0
nextBtn.classList.remove("hidden")
render()
}

async function fileQuiz(){
const fd=new FormData()
fd.append("file",fileInput.files[0])
fd.append("mode","questions")
fd.append("language",fileLang.value)
const r=await fetch(BACKEND+"/ask-file",{method:"POST",body:fd})
const d=await r.json()
questions=parse(d.result).questions
answers=new Array(questions.length).fill(null)
i=0
nextBtn.classList.remove("hidden")
render()
}

async function summarize(){
const fd=new FormData()
fd.append("file",sumFile.files[0])
fd.append("mode","summary")
fd.append("language",sumLang.value)
const r=await fetch(BACKEND+"/ask-file",{method:"POST",body:fd})
const d=await r.json()
result.innerHTML=`<pre>${d.result}</pre>`
}

function render(){
const q=questions[i]
let h=`<h3>${q.q}</h3>`
q.options.forEach((o,idx)=>{
let c="option"
if(answers[i]!==null){
if(idx===q.answer)c+=" correct"
else c+=" incorrect"
}
h+=`<div class="${c}" onclick="choose(${idx})">${o}
${answers[i]!==null?`<div class="feedback">${q.explanations[idx]}</div>`:""}
</div>`
})
result.innerHTML=h
}

function choose(x){
if(answers[i]!==null)return
answers[i]=x
render()
}

function next(){
if(i<questions.length-1){i++;render()}
else{
let c=0
answers.forEach((a,j)=>{if(a===questions[j].answer)c++})
result.innerHTML=`<h2>النتيجة: ${c}/${questions.length}</h2>`
nextBtn.classList.add("hidden")
}
}
</script>
</body>
</html>
