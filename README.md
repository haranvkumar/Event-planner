# Event-planner


<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Resilio — Personal Health & Activity</title>
<style>
:root{--ink:#172b35;--muted:#71838a;--bg:#f4f7f6;--panel:#fff;--line:#e4ece9;--teal:#167d76;--teal2:#e5f4f1;--blue:#eaf1fb;--amber:#fff4df;--red:#fff0ed;--shadow:0 8px 28px rgba(24,52,58,.06)}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--ink);font:15px/1.5 system-ui,sans-serif}
button,input,select,textarea{font:inherit}
button{cursor:pointer;border:0}
.app{display:flex;min-height:100vh}
.sidebar{width:245px;background:#fff;border-right:1px solid var(--line);padding:28px 18px;display:flex;flex-direction:column;gap:28px}
.brand{display:flex;align-items:center;gap:10px;padding:0 10px}
.logo{width:36px;height:36px;border-radius:12px;background:var(--teal);color:white;display:grid;place-items:center;font-weight:800}
.brand strong{font-size:20px;letter-spacing:1.6px}
.brand small{display:block;color:var(--muted);font-size:11px}
.nav{display:grid;gap:6px}
.nav button{background:transparent;color:#62747b;text-align:left;padding:12px 14px;border-radius:10px;display:flex;gap:12px;align-items:center}
.nav button.active,.nav button:hover{background:var(--teal2);color:var(--teal);font-weight:650}
.nav .ico{width:20px;text-align:center}
.side-note{margin-top:auto;background:#f1f7f5;padding:15px;border-radius:13px;color:#52666c;font-size:12px}
.main{flex:1;min-width:0;padding:30px clamp(18px,4vw,52px);max-width:1600px;margin:auto}
.top{display:flex;justify-content:space-between;align-items:center;gap:16px;margin-bottom:28px}
.eyebrow{color:var(--teal);font-size:11px;font-weight:750;letter-spacing:1.4px;text-transform:uppercase}
.top h1{margin:4px 0 0;font-size:29px}
.date{color:var(--muted);font-size:13px}
.profile{display:flex;align-items:center;gap:10px;background:white;border:1px solid var(--line);border-radius:30px;padding:7px 12px;font-size:13px}
.avatar{width:30px;height:30px;border-radius:50%;background:#dcefeb;color:var(--teal);display:grid;place-items:center;font-weight:700}
.view{display:none}
.view.active{display:block}
.grid{display:grid;grid-template-columns:repeat(12,minmax(0,1fr));gap:17px}
.card{background:var(--panel);border:1px solid var(--line);border-radius:16px;padding:20px;box-shadow:var(--shadow);min-width:0}
.span-3{grid-column:span 3}.span-4{grid-column:span 4}.span-5{grid-column:span 5}.span-6{grid-column:span 6}.span-7{grid-column:span 7}.span-8{grid-column:span 8}.span-12{grid-column:span 12}
.card-head{display:flex;justify-content:space-between;align-items:center;gap:10px;margin-bottom:15px}
.card h3{margin:0;font-size:15px}
.muted{color:var(--muted)}.small{font-size:12px}
.metric{font-size:30px;font-weight:750;margin:6px 0}
.pill{display:inline-flex;align-items:center;padding:4px 9px;border-radius:20px;background:var(--teal2);color:var(--teal);font-size:11px;font-weight:650}
.pill.amber{background:var(--amber);color:#93620e}
.pill.blue{background:var(--blue);color:#416b9c}
.pill.red{background:var(--red);color:#a34b3d}
.metric-row{display:flex;justify-content:space-between;align-items:end}
.bar{height:7px;background:#edf2f0;border-radius:10px;overflow:hidden;margin-top:12px}
.bar i{display:block;height:100%;background:var(--teal);border-radius:10px}
.btn{background:var(--teal);color:#fff;border-radius:10px;padding:10px 14px;font-weight:650;font-size:13px}
.btn.secondary{background:#edf5f3;color:var(--teal)}
.btn.ghost{background:#f3f6f5;color:#53676d}
.btn-row{display:flex;gap:8px;flex-wrap:wrap}
.notice{padding:13px 14px;border-radius:12px;background:#f0f6fb;color:#4c6575;font-size:12px;margin-top:14px}
.notice.warn{background:var(--amber);color:#75551d}
.notice.danger{background:var(--red);color:#874a40}
.chart{width:100%;height:160px;display:block}
.chart text{font-size:10px;fill:#87969b}
.legend{display:flex;gap:15px;font-size:11px;color:var(--muted)}
.dot{display:inline-block;width:8px;height:8px;border-radius:50%;background:var(--teal);margin-right:5px}
.list{display:grid;gap:11px}
.list-item{display:flex;justify-content:space-between;gap:12px;align-items:center;padding:10px 0;border-bottom:1px solid #eef2f0}
.list-item:last-child{border:0}
.tag{font-size:11px;color:#60757b;background:#f1f5f4;padding:4px 8px;border-radius:7px}
.form-grid{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:14px}
.field{display:grid;gap:6px}
.field.full{grid-column:1/-1}
.field label{font-size:12px;color:#5c7077;font-weight:650}
.field input,.field select,.field textarea{width:100%;border:1px solid #dce6e2;border-radius:9px;padding:10px 11px;background:white;color:var(--ink)}
.field textarea{min-height:80px;resize:vertical}
.range-row{display:flex;align-items:center;gap:12px}
.range-row input{flex:1;accent-color:var(--teal)}
.range-value{min-width:24px;font-weight:700;color:var(--teal)}
.section-title{font-size:18px;margin:0 0 4px}
.section-sub{color:var(--muted);font-size:13px;margin:0 0 18px}
.calendar{display:grid;grid-template-columns:repeat(7,1fr);gap:7px}
.day{border:1px solid var(--line);border-radius:10px;min-height:86px;padding:8px;font-size:11px;background:#fff}
.day strong{display:block;font-size:12px;margin-bottom:8px}
.day.event{background:#eff8f5;border-color:#cde8df}
.day.rest{background:#f5f7fb}
.event-label{font-size:10px;color:var(--teal);line-height:1.25}
.table{width:100%;border-collapse:collapse;font-size:12px}
.table th,.table td{text-align:left;padding:11px 8px;border-bottom:1px solid var(--line)}
.table th{color:var(--muted);font-weight:650}
.empty{padding:25px;text-align:center;color:var(--muted);font-size:13px}
.toast{position:fixed;right:22px;bottom:22px;background:#183b3c;color:white;padding:12px 16px;border-radius:10px;display:none;z-index:5}
.toast.show{display:block}
.footer-note{font-size:11px;color:var(--muted);margin-top:18px}
.mobile-nav{display:none}
@media(max-width:900px){.sidebar{width:205px}.span-3,.span-4{grid-column:span 6}.span-5,.span-7,.span-8{grid-column:span 12}}
@media(max-width:640px){
.app{display:block}.sidebar{display:none}.main{padding:20px 14px 90px}
.top{align-items:flex-start}.top h1{font-size:24px}.profile{font-size:0}
.profile .avatar{font-size:13px}.grid{gap:12px}
.span-3,.span-4,.span-5,.span-6,.span-7,.span-8{grid-column:span 12}
.card{padding:16px}
.mobile-nav{position:fixed;display:flex;bottom:0;left:0;right:0;background:white;border-top:1px solid var(--line);justify-content:space-around;padding:8px 3px;z-index:4}
.mobile-nav button{background:transparent;color:#64777d;font-size:10px;display:grid;gap:2px;justify-items:center}
.mobile-nav button.active{color:var(--teal);font-weight:700}
.mobile-nav span{font-size:18px}.form-grid{grid-template-columns:1fr}
.field.full{grid-column:auto}.day{min-height:70px;padding:5px}
}
</style>
</head>
<body>
<div class="app">
<aside class="sidebar">
<div class="brand"><div class="logo">R</div><div><strong>RESILIO</strong><small>YOUR HEALTH, YOUR PACE</small></div></div>
<nav class="nav">
<button class="active" data-view="dashboard">⌂ Overview</button>
<button data-view="checkin">＋ Daily check-in</button>
<button data-view="activity">◷ Activity & workouts</button>
<button data-view="trends">⌁ Health trends</button>
<button data-view="profile">⚙ Health profile</button>
</nav>
<div class="side-note"><strong>Built around your baseline</strong><br><br>Resilio helps you record patterns and prepare useful information to discuss with your healthcare team. It does not diagnose or prescribe exercise.</div>
</aside>
<main class="main">
<header class="top">
<div><div class="eyebrow">Personal health & activity</div><h1 id="pageTitle">Your overview</h1><div class="date" id="todayDate"></div></div>
<div class="profile"><div class="avatar">U</div><span id="profileName">Your profile</span></div>
</header>


<section class="view active" id="dashboard">
<div class="grid">
<article class="card span-3"><div class="card-head"><h3>Today's energy</h3><span class="pill">Self-reported</span></div><div class="metric" id="energyMetric">— / 10</div><div class="small muted">Your latest check-in</div><div class="bar"><i id="energyBar" style="width:0%"></i></div></article>
<article class="card span-3"><div class="card-head"><h3>Symptoms</h3><span class="pill blue">Latest entry</span></div><div class="metric" id="symptomMetric">—</div><div class="small muted" id="symptomSub">No symptom entry yet</div></article>
<article class="card span-3"><div class="card-head"><h3>Sleep</h3><span class="pill">Hours</span></div><div class="metric" id="sleepMetric">—</div><div class="small muted">Last recorded night</div></article>
<article class="card span-3"><div class="card-head"><h3>Activity</h3><span class="pill amber">Logged</span></div><div class="metric" id="activityMetric">—</div><div class="small muted">Minutes recorded today</div></article>
<article class="card span-7"><div class="card-head"><div><h3>Energy over the last 7 days</h3><div class="small muted">Based on your check-ins</div></div><button class="btn secondary" onclick="showView('trends')">View trends</button></div><svg class="chart" id="energyChart" viewBox="0 0 600 170"></svg><div class="legend"><span><i class="dot"></i>Energy (out of 10)</span></div></article>
<article class="card span-5"><div class="card-head"><h3>Today's plan</h3><span class="pill blue">Your calendar</span></div><div id="todayPlan" class="list"><div class="empty">No activities planned yet.</div></div><button class="btn secondary" onclick="showView('activity')">Open activity planner</button></article>
<article class="card span-6"><div class="card-head"><h3>Recent check-ins</h3><button class="btn secondary" onclick="showView('checkin')">Add check-in</button></div><div id="recentCheckins" class="list"></div></article>
<article class="card span-6"><div class="card-head"><h3>Pattern notes</h3><span class="pill amber">For reflection</span></div><p class="small muted">As you add entries, look for patterns worth discussing with your healthcare professional.</p><div class="notice">A change in symptoms is not automatically caused by exercise. Resilio displays your recorded information; it cannot determine the cause.</div></article>
</div>
</section>


<section class="view" id="checkin">
<h2 class="section-title">Daily check-in</h2>
<p class="section-sub">Record how you are feeling today.</p>
<div class="grid">
<article class="card span-7">
<form id="checkinForm">
<div class="form-grid">
<div class="field"><label>Date</label><input id="checkDate" type="date" required></div>
<div class="field"><label>Sleep last night (hours)</label><input id="sleepInput" type="number" min="0" max="24" step=".25"></div>
<div class="field full"><label>Energy level (0 = very low, 10 = very high)</label><div class="range-row"><input id="energyInput" type="range" min="0" max="10" value="5"><span id="energyValue" class="range-value">5</span></div></div>
<div class="field"><label>Mood</label><select id="moodInput"><option value="">Choose</option><option>Very low</option><option>Low</option><option>Okay</option><option>Good</option><option>Very good</option></select></div>
<div class="field"><label>Main symptom</label><select id="symptomInput"><option value="">No symptom selected</option><option>Fatigue</option><option>Dizziness</option><option>Pain</option><option>Headache</option><option>Breathlessness</option><option>Brain fog</option><option>Joint instability</option><option>Other</option></select></div>
<div class="field"><label>Where is the pain?</label><select id="painLocationInput"><option value="">Not applicable / not sure</option><option>Back</option><option>Neck</option><option>Shoulder</option><option>Arm / elbow</option><option>Wrist / hand</option><option>Hip</option><option>Knee</option><option>Ankle / foot</option><option>Other</option></select></div>
<div class="field"><label>Symptom severity (0–10)</label><div class="range-row"><input id="severityInput" type="range" min="0" max="10" value="0"><span id="severityValue" class="range-value">0</span></div></div>
<div class="field"><label>Symptom duration</label><select id="durationInput"><option value="">Not specified</option><option>Less than an hour</option><option>1–3 hours</option><option>Most of the day</option><option>More than a day</option></select></div>
<div class="field full"><label>Notes</label><textarea id="notesInput" placeholder="Anything you want to record…"></textarea></div>
</div>
<button class="btn" style="margin-top:16px">Save check-in</button>
</form>
</article>
<article class="card span-5"><h3>Why check in?</h3><p class="small muted">A consistent record can help you notice changes and explain your experience to a healthcare professional.</p><div class="notice warn">Do not use an app score to decide whether it is safe to exercise. Follow the care plan provided by your healthcare team.</div></article>
</div>
</section>


<section class="view" id="activity">
<h2 class="section-title">Activity & workout planning</h2>
<p class="section-sub">Enter your planned workout and review it alongside your symptoms for that date.</p>
<div class="grid">
<article class="card span-12">
<div class="card-head"><div><h3>Workout safety review</h3><div class="small muted">Add your exercises individually to receive symptom-related caution flags.</div></div><span class="pill blue">Symptom-aware</span></div>
<form id="workoutForm">
<div class="form-grid">
<div class="field"><label>Workout date</label><input id="workoutDate" type="date" required></div>
<div class="field"><label>Workout name</label><input id="workoutName" placeholder="e.g. Upper body session" required></div>
<div class="field full"><label>Planned exercises (one per line)</label><textarea id="workoutExercises" rows="5" required placeholder="Bicep curls — 3 sets of 10&#10;Hammer curls — 3 sets of 10&#10;Kettlebell ab rotations — 3 sets of 12"></textarea><div class="small muted">Include sets, reps and equipment if useful.</div></div>
</div>
<div class="btn-row" style="margin-top:14px"><button class="btn" type="submit">Review my workout</button><button class="btn secondary" type="button" onclick="showView('checkin')">Complete check-in</button></div>
</form>
<div id="workoutReview" style="margin-top:18px"><div class="notice">Your review will appear here. Complete a check-in for the same date to add context.</div></div>
</article>


<article class="card span-5">
<h3 style="margin-bottom:15px">Add an activity</h3>
<form id="activityForm">
<div class="form-grid">
<div class="field full"><label>Activity</label><input id="activityName" required placeholder="e.g. Team training, school, walk"></div>
<div class="field"><label>Date</label><input id="activityDate" type="date" required></div>
<div class="field"><label>Duration (minutes)</label><input id="activityMinutes" type="number" min="1" max="1440" required></div>
<div class="field"><label>Category</label><select id="activityType"><option>Sport / exercise</option><option>School / work</option><option>Social</option><option>Daily living</option><option>Rest</option><option>Other</option></select></div>
<div class="field"><label>Status</label><select id="activityStatus"><option>Planned</option><option>Completed</option><option>Rest / recovery</option></select></div>
<div class="field full"><label>Notes</label><textarea id="activityNotes"></textarea></div>
</div>
<button class="btn" style="margin-top:16px">Add to calendar</button>
</form>
</article>
<article class="card span-7"><div class="card-head"><h3>Upcoming activities</h3><button class="btn secondary" onclick="exportCSV('activities')">Export CSV</button></div><div id="activityList" class="list"></div></article>
<article class="card span-12"><div class="card-head"><h3>Weekly planner</h3><span class="small muted">Next 7 days</span></div><div class="calendar" id="calendar"></div></article>
</div>
</section>


<section class="view" id="trends">
<h2 class="section-title">Health trends</h2>
<p class="section-sub">Review your recorded information over time. Trends are descriptive, not diagnoses.</p>
<div class="grid">
<article class="card span-6"><h3>Energy check-ins</h3><svg class="chart" id="trendEnergyChart" viewBox="0 0 600 190"></svg></article>
<article class="card span-6"><h3>Symptom severity</h3><svg class="chart" id="symptomChart" viewBox="0 0 600 190"></svg></article>
<article class="card span-12"><div class="card-head"><h3>Check-in history</h3><button class="btn secondary" onclick="exportCSV('checkins')">Export check-ins CSV</button></div><div style="overflow-x:auto"><table class="table"><thead><tr><th>Date</th><th>Energy</th><th>Sleep</th><th>Symptom</th><th>Severity</th><th>Mood</th></tr></thead><tbody id="checkinTable"></tbody></table></div></article>
</div>
</section>


<section class="view" id="profile">
<h2 class="section-title">Health profile</h2>
<p class="section-sub">Personalise the tracker. This information stays in this browser in this demo.</p>
<div class="grid">
<article class="card span-7">
<form id="profileForm">
<div class="form-grid">
<div class="field"><label>Display name</label><input id="nameInput" placeholder="Your name"></div>
<div class="field"><label>Condition(s) you want to track</label><select id="conditionInput"><option value="">Not specified</option><option>POTS</option><option>ME/CFS</option><option>Long COVID</option><option>Asthma</option><option>Type 1 diabetes</option><option>Ehlers-Danlos Syndrome (EDS)</option><option>Chronic migraine</option><option>Other / multiple conditions</option></select></div>
<div class="field full"><label>Personal notes or tracking preferences</label><textarea id="baselineInput"></textarea></div>
</div>
<button class="btn" style="margin-top:16px">Save profile</button>
</form>
</article>
<article class="card span-5"><h3>Wearable connection</h3><p class="small muted">Wearable connections are not active in this prototype.</p><div class="list"><div class="list-item">Garmin <span class="pill amber">Not connected</span></div><div class="list-item">Apple Health <span class="pill amber">Not connected</span></div><div class="list-item">Google Health Connect <span class="pill amber">Not connected</span></div></div></article>
<article class="card span-12"><h3>Privacy & safety</h3><ul class="small muted"><li>This demo stores entries in your browser's local storage; it does not send them to a server.</li><li>Do not use this prototype for emergencies, diagnosis, treatment decisions, or exercise clearance.</li><li>A production app requires encryption, access controls, consent and clinical review.</li></ul><div class="btn-row"><button class="btn secondary" onclick="exportCSV('all')">Export all my data</button><button class="btn ghost" onclick="clearData()">Delete local demo data</button></div></article>
</div>
</section>
<p class="footer-note">Resilio prototype · Not a medical device or substitute for professional care.</p>
</main>
</div>
<nav class="mobile-nav">
<button class="active" data-view="dashboard"><span>⌂</span>Home</button><button data-view="checkin"><span>＋</span>Check-in</button><button data-view="activity"><span>◷</span>Activity</button><button data-view="trends"><span>⌁</span>Trends</button><button data-view="profile"><span>⚙</span>Profile</button>
</nav>
<div class="toast" id="toast"></div>


<script>
const $=id=>document.getElementById(id);
const today=()=>new Date().toISOString().slice(0,10);
const load=(key,fallback=[])=>{
const storageKey='resilio_'+key;
let stored=localStorage.getItem(storageKey);
if(stored===null){
stored=localStorage.getItem('recover_'+key);
}
try{return stored?JSON.parse(stored)||fallback:fallback}catch{return fallback}
};
const save=(key,val)=>localStorage.setItem('resilio_'+key,JSON.stringify(val));
let checkins=load('checkins'),activities=load('activities'),workouts=load('workouts');
let profile=load('profile',{});


const titles={dashboard:'Your overview',checkin:'Daily check-in',activity:'Activity & workout planning',trends:'Health trends',profile:'Health profile'};
function toast(msg){const t=$('toast');t.textContent=msg;t.classList.add('show');setTimeout(()=>t.classList.remove('show'),2400)}
function esc(s){return String(s??'').replace(/[&<>"']/g,c=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c]))}
function fmtDate(d){return new Date(d+'T12:00:00').toLocaleDateString(undefined,{day:'numeric',month:'short'})}


function showView(id){
document.querySelectorAll('.view').forEach(v=>v.classList.toggle('active',v.id===id));
document.querySelectorAll('[data-view]').forEach(b=>b.classList.toggle('active',b.dataset.view===id));
$('pageTitle').textContent=titles[id];
if(id==='dashboard')renderDashboard();
if(id==='activity')renderActivities();
if(id==='trends')renderTrends();
window.scrollTo({top:0,behavior:'smooth'});
}
document.querySelectorAll('[data-view]').forEach(b=>b.addEventListener('click',()=>showView(b.dataset.view)));


$('todayDate').textContent=new Date().toLocaleDateString(undefined,{weekday:'long',day:'numeric',month:'long',year:'numeric'});
$('checkDate').value=today();
$('activityDate').value=today();
$('workoutDate').value=today();


$('profileName').textContent=profile.name||'Your profile';
$('nameInput').value=profile.name||'';
$('conditionInput').value=profile.condition||'';
$('baselineInput').value=profile.notes||'';


$('energyInput').addEventListener('input',e=>$('energyValue').textContent=e.target.value);
$('severityInput').addEventListener('input',e=>$('severityValue').textContent=e.target.value);


$('checkinForm').addEventListener('submit',e=>{
e.preventDefault();
const entry={
date:$('checkDate').value,
energy:Number($('energyInput').value),
sleep:$('sleepInput').value===''?null:Number($('sleepInput').value),
mood:$('moodInput').value,
symptom:$('symptomInput').value,
painLocation:$('painLocationInput').value,
severity:Number($('severityInput').value),
duration:$('durationInput').value,
notes:$('notesInput').value
};
checkins=checkins.filter(x=>x.date!==entry.date);
checkins.push(entry);
checkins.sort((a,b)=>a.date.localeCompare(b.date));
save('checkins',checkins);
e.target.reset();
$('checkDate').value=today();
$('energyInput').value=5;
$('energyValue').textContent='5';
$('severityInput').value=0;
$('severityValue').textContent='0';
toast('Check-in saved');
renderDashboard();
});


$('activityForm').addEventListener('submit',e=>{
e.preventDefault();
activities.push({
id:Date.now(),
name:$('activityName').value,
date:$('activityDate').value,
minutes:Number($('activityMinutes').value),
type:$('activityType').value,
status:$('activityStatus').value,
notes:$('activityNotes').value
});
save('activities',activities);
e.target.reset();
$('activityDate').value=today();
renderActivities();
renderDashboard();
toast('Activity added');
});


$('workoutForm').addEventListener('submit',e=>{
e.preventDefault();
const plan={
id:Date.now(),
date:$('workoutDate').value,
name:$('workoutName').value.trim(),
exercises:$('workoutExercises').value.split('\n').map(x=>x.trim()).filter(Boolean)
};
workouts=workouts.filter(w=>w.date!==plan.date);
workouts.push(plan);
save('workouts',workouts);
reviewWorkout(plan);
toast('Workout reviewed and saved');
});


function reviewWorkout(plan){
const check=checkins.find(c=>c.date===plan.date);
const pain=check&&((check.symptom||'').toLowerCase()==='pain'||check.painLocation);
const backPain=!!(check&&((check.painLocation||'').toLowerCase()==='back'||((check.symptom||'').toLowerCase()==='pain'&&/back/i.test(check.notes||''))));
const severity=check?Number(check.severity||0):null;
let html='';


if(!check){
html='<div class="notice warn">No check-in was found for '+fmtDate(plan.date)+'. This review is limited. Record your symptoms for this date. The absence of a check-in does not mean an exercise is safe.</div>';
}else if(backPain){
html='<div class="notice danger"><strong>Back pain recorded ('+severity+'/10).</strong> Resilio cannot determine the cause or assess whether this workout is safe. Consider postponing exercises involving loaded twisting or repeated trunk rotation, including rotational kettlebell movements, until you have checked with a qualified health professional.</div>';
}else if(pain){
html='<div class="notice warn"><strong>Pain recorded ('+severity+'/10).</strong> The location or cause may need more detail. This app cannot clear exercises as safe. Avoid movements that increase symptoms and consider professional advice if pain is new, worsening or persistent.</div>';
}else{
html='<div class="notice">Your check-in does not show a pain location for this date. This is not medical clearance. Follow advice from your healthcare professional.</div>';
}


html+='<h4 style="margin:16px 0 8px">Exercise-by-exercise review</h4><div class="list">';


plan.exercises.forEach(ex=>{
const t=ex.toLowerCase();
let status='General caution';
let cls='amber';
let why='Resilio does not have enough information to judge this movement. Follow your clinician’s advice and stop if it worsens symptoms.';


if(backPain&&/(rotation|rotat|twist|russian|wood.?chop|windmill|kettlebell.*(abs|core)|abs.*kettlebell|core.*kettlebell)/i.test(t)){
status='Avoid for now';
cls='red';
why='This appears to involve loaded trunk rotation. With back pain recorded, Resilio flags it for caution. Pause it until a qualified health professional has advised whether it is appropriate.';
}else if(backPain&&/(deadlift|bent.?over|good.?morning|sit.?up|back extension|hyperextension|heavy row)/i.test(t)){
status='Needs professional review';
cls='amber';
why='This may place demand on the back or trunk. Resilio cannot assess your technique, injury or capacity. Ask your clinician or physiotherapist before doing it while you have back pain.';
}else if(backPain){
status='Not cleared as safe';
cls='amber';
why='Back pain is recorded. This exercise is not automatically safe just because it was not matched to a caution rule. Follow your healthcare professional’s advice.';
}


html+='<div class="list-item" style="align-items:flex-start"><div style="min-width:0"><strong>'+esc(ex)+'</strong><div class="small muted" style="margin-top:4px">'+why+'</div></div><span class="pill '+cls+'">'+status+'</span></div>';
});


html+='</div><div class="notice warn"><strong>Important:</strong> This is a basic keyword-based safety prompt, not a clinical assessment. It may miss risky movements or flag movements that are appropriate for some people. If pain is severe, worsening, follows an injury, or comes with concerning symptoms, seek prompt medical advice. Do not use this review to diagnose yourself or push through pain.</div>';


$('workoutReview').innerHTML=html;
}


$('profileForm').addEventListener('submit',e=>{
e.preventDefault();
profile={name:$('nameInput').value.trim(),condition:$('conditionInput').value,notes:$('baselineInput').value};
save('profile',profile);
$('profileName').textContent=profile.name||'Your profile';
toast('Profile saved');
});


function drawChart(el,data,max=10){
const svg=$(el);
if(!data.length){svg.innerHTML='<text x="300" y="85" text-anchor="middle">Add check-ins to see your trend</text>';return}
const w=600,h=170,p=28,usable=h-2*p;
const points=data.map((v,i)=>`${p+(data.length===1?0:i*(w-2*p)/(data.length-1))},${h-p-(v.value/max)*usable}`).join(' ');
const circles=data.map((v,i)=>{
const x=p+(data.length===1?0:i*(w-2*p)/(data.length-1));
const y=h-p-(v.value/max)*usable;
return `<circle cx="${x}" cy="${y}" r="4" fill="#167d76"/><text x="${x}" y="${h-5}" text-anchor="middle">${v.label}</text>`;
}).join('');
const grid=[0,2,4,6,8,10].map(n=>{
const y=h-p-(n/max)*usable;
return `<line x1="${p}" y1="${y}" x2="${w-p}" y2="${y}" stroke="#edf2f0"/><text x="4" y="${y+3}">${n}</text>`;
}).join('');
svg.innerHTML=grid+`<polyline points="${points}" fill="none" stroke="#167d76" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"/>`+circles;
}


function renderDashboard(){
const latest=[...checkins].sort((a,b)=>b.date.localeCompare(a.date))[0];
$('energyMetric').textContent=latest?latest.energy+' / 10':'—';
$('energyBar').style.width=latest?latest.energy*10+'%':'0%';
$('symptomMetric').textContent=latest?(latest.symptom||'None selected'):'—';
$('symptomSub').textContent=latest?(latest.symptom?'Severity '+latest.severity+'/10 · '+fmtDate(latest.date):'No symptom selected'):'No symptom entry yet';
$('sleepMetric').textContent=latest&&latest.sleep!==null?latest.sleep+'h':'—';
$('activityMetric').textContent=activities.filter(a=>a.date===today()&&a.status==='Completed').reduce((s,a)=>s+a.minutes,0);


const recent=[...checkins].sort((a,b)=>b.date.localeCompare(a.date)).slice(0,4);
$('recentCheckins').innerHTML=recent.length?recent.map(c=>`<div class="list-item"><div><strong>${fmtDate(c.date)}</strong><div class="small muted">${esc(c.symptom||'No symptom selected')}</div></div><span class="tag">Energy ${c.energy}/10</span></div>`).join(''):'<div class="empty">Your check-ins will appear here.</div>';


const todays=activities.filter(a=>a.date===today());
$('todayPlan').innerHTML=todays.length?todays.map(a=>`<div class="list-item"><div><strong>${esc(a.name)}</strong><div class="small muted">${esc(a.type)} · ${a.minutes} min</div></div><span class="tag">${esc(a.status)}</span></div>`).join(''):'<div class="empty">No activities planned for today.</div>';


drawChart('energyChart',checkins.slice(-7).map(c=>({value:c.energy,label:fmtDate(c.date)})));
}


function renderActivities(){
const sorted=[...activities].sort((a,b)=>a.date.localeCompare(b.date));
$('activityList').innerHTML=sorted.length?sorted.map(a=>`<div class="list-item"><div><strong>${esc(a.name)}</strong><div class="small muted">${fmtDate(a.date)} · ${esc(a.type)} · ${a.minutes} min</div></div><div class="btn-row"><span class="tag">${esc(a.status)}</span><button class="btn ghost" onclick="removeActivity(${a.id})">Remove</button></div></div>`).join(''):'<div class="empty">No activities added yet.</div>';


const days=Array.from({length:7},(_,i)=>{const d=new Date();d.setDate(d.getDate()+i);return d.toISOString().slice(0,10)});
$('calendar').innerHTML=days.map(d=>{
const entries=activities.filter(a=>a.date===d);
return `<div class="day ${entries.some(a=>a.status==='Rest / recovery')?'rest':entries.length?'event':''}"><strong>${new Date(d+'T12:00:00').toLocaleDateString(undefined,{weekday:'short',day:'numeric'})}</strong>${entries.map(a=>`<div class="event-label">${esc(a.name)}</div>`).join('')}</div>`;
}).join('');
}


function removeActivity(id){
activities=activities.filter(a=>a.id!==id);
save('activities',activities);
renderActivities();
renderDashboard();
toast('Activity removed');
}


function renderTrends(){
const recent=[...checkins].sort((a,b)=>a.date.localeCompare(b.date)).slice(-14);
drawChart('trendEnergyChart',recent.map(c=>({value:c.energy,label:fmtDate(c.date)})));
const symptoms=recent.filter(c=>c.symptom);
drawChart('symptomChart',symptoms.map(c=>({value:c.severity,label:fmtDate(c.date)})));
$('checkinTable').innerHTML=recent.length?recent.slice().reverse().map(c=>`<tr><td>${fmtDate(c.date)}</td><td>${c.energy}/10</td><td>${c.sleep===null?'—':c.sleep+'h'}</td><td>${esc(c.symptom||'—')}</td><td>${c.symptom?c.severity+'/10':'—'}</td><td>${esc(c.mood||'—')}</td></tr>`).join(''):'<tr><td colspan="6" class="empty">No data yet.</td></tr>';
}


function exportCSV(which){
let rows,filename;
if(which==='activities'||which==='all'){
rows=[['Date','Activity','Minutes','Category','Status','Notes'],...activities.map(a=>[a.date,a.name,a.minutes,a.type,a.status,a.notes])];
filename='resilio-activities.csv';
if(which==='all')downloadCSV(rows,filename);
if(which==='all'){
const c=[['Date','Energy','Sleep hours','Mood','Symptom','Severity','Duration','Notes'],...checkins.map(x=>[x.date,x.energy,x.sleep,x.mood,x.symptom,x.severity,x.duration,x.notes])];
downloadCSV(c,'resilio-checkins.csv');
return;
}
}else{
rows=[['Date','Energy','Sleep hours','Mood','Symptom','Severity','Duration','Notes'],...checkins.map(x=>[x.date,x.energy,x.sleep,x.mood,x.symptom,x.severity,x.duration,x.notes])];
filename='resilio-checkins.csv';
}
downloadCSV(rows,filename);
}
function downloadCSV(rows,name){
const csv=rows.map(r=>r.map(v=>'"'+String(v??'').replace(/"/g,'""')+'"').join(',')).join('\n');
const blob=new Blob([csv],{type:'text/csv;charset=utf-8;'});
const url=URL.createObjectURL(blob);
const a=document.createElement('a');a.href=url;a.download=name;a.click();
URL.revokeObjectURL(url);
toast('Export prepared');
}


function clearData(){
if(confirm('Delete all Resilio demo entries saved in this browser? This cannot be undone.')){
['checkins','activities','workouts','profile'].forEach(k=>{
localStorage.removeItem('resilio_'+k);
localStorage.removeItem('recover_'+k);
});
checkins=[];activities=[];workouts=[];profile={};
$('profileName').textContent='Your profile';
$('nameInput').value='';$('conditionInput').value='';$('baselineInput').value='';
renderDashboard();renderActivities();renderTrends();
toast('Local demo data deleted');
}
}


renderDashboard();
</script>
</body>
</html>







