[habit-tracker.html](https://github.com/user-attachments/files/32854888/habit-tracker.html)<!DOCTYPE html>
<html lang="de">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Habits</title>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&family=Space+Grotesk:wght@500;700&display=swap" rel="stylesheet">
<style>
:root{--bg:#fcfbf9;--card:#f0eee8;--ink:#1a1a1a;--mid:#6b6b6b;--soft:#e2dfd7;--line:#d9d6ce;--onink:#fff;--red:#e5261b;
box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#141312;--card:#201f1d;--ink:#f4f2ee;--mid:#9a978f;--soft:#2e2c29;--line:#3a3834;--onink:#141312}}
:root[data-theme="dark"]{--bg:#141312;--card:#201f1d;--ink:#f4f2ee;--mid:#9a978f;--soft:#2e2c29;--line:#3a3834;--onink:#141312}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--ink);font-family:Inter,system-ui,Arial,sans-serif;min-height:100vh}
.app{max-width:900px;margin:0 auto;padding:12px 12px 40px}
.head{background:transparent;color:var(--ink);padding:14px 4px 6px;display:flex;justify-content:space-between;align-items:center}
.head small{display:block;font-size:12px;color:var(--mid);font-weight:500}
.head b{font-size:26px;font-weight:700}
.menu{background:none;border:0;padding:8px;cursor:pointer}
.menu i{display:block;height:2px;background:var(--ink);margin:5px 0;border-radius:2px}
.menu i:first-child{width:22px;margin-left:auto}.menu i:last-child{width:14px;margin-left:auto}
.card{background:var(--card);border-radius:22px;padding:20px;margin-top:12px}
h2{font-size:12px;font-weight:700;margin:0 0 14px;letter-spacing:.02em}
.ringwrap{display:flex;justify-content:center}
.ring{position:relative;width:170px;height:170px}
.ring svg{transform:rotate(-90deg)}
.ring div{position:absolute;inset:0;display:flex;flex-direction:column;align-items:center;justify-content:center}
.ring b{font-size:26px}.ring span{font-size:11px;color:var(--mid)}
.bars{display:flex;align-items:flex-end;justify-content:space-between;height:90px;gap:8px}
.bars div{flex:1;display:flex;flex-direction:column;align-items:center;justify-content:flex-end;height:100%;font-size:10px;color:var(--mid);gap:6px}
.bars u{display:block;width:100%;background:var(--soft);border-radius:4px;text-decoration:none;min-height:6px}
.bars .t u{background:var(--red)}
.row{display:flex;align-items:center;gap:12px;padding:12px 0;border-top:1px solid var(--line);cursor:pointer;font-size:13px;font-weight:600;background:none;border-left:0;border-right:0;border-bottom:0;width:100%;color:var(--ink);text-align:left;font-family:inherit}
.row:first-of-type{border-top:0}
.box{width:22px;height:22px;border-radius:50%;border:2px solid var(--ink);flex:none;display:grid;place-items:center}
.done .box{background:var(--red);border-color:var(--red)}
.done .box:after{content:"";width:6px;height:10px;border:solid #fff;border-width:0 2px 2px 0;transform:rotate(45deg) translate(-1px,-1px)}
.done span{color:var(--mid);text-decoration:line-through}
.add{display:flex;gap:8px;margin-top:10px}
input{flex:1;min-width:0;font-family:inherit;font-size:13px;padding:12px 16px;border-radius:999px;border:1px solid var(--line);background:var(--soft);color:var(--ink);outline:none}
input:focus-visible,button:focus-visible{outline:2px solid var(--ink);outline-offset:2px}
.pill{background:var(--red);color:#fff;border:0;border-radius:999px;padding:13px 22px;font-family:inherit;font-weight:700;font-size:12px;cursor:pointer}
:root[data-theme="dark"] .pill,:root:not([data-theme="light"]) .pill{}
.pill.full{width:100%;margin-top:12px}
.ghost{background:none;border:0;color:var(--mid);font-family:inherit;font-size:12px;cursor:pointer;padding:6px}
.hello{min-height:80vh;display:flex;flex-direction:column;justify-content:center;gap:16px;text-align:center;padding:0 10px}
.hello h1{font-size:34px;margin:0}
.hello input{text-align:center;padding:16px}
.empty{color:var(--mid);font-size:12px;text-align:center;padding:6px 0}
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(min(300px,100%),1fr));gap:12px;margin-top:12px}
.grid .card{margin-top:0}
.seg{display:flex;gap:6px;flex-wrap:wrap;margin-bottom:16px}
.seg button{border:0;border-radius:999px;padding:8px 16px;font-family:inherit;font-weight:600;font-size:12px;cursor:pointer;background:var(--soft);color:var(--mid)}
.seg button.on{background:var(--ink);color:var(--onink)}
.hmw{overflow-x:auto;padding-bottom:4px}
.hm{display:grid;grid-template-rows:repeat(7,auto);grid-auto-flow:column;gap:4px}
.hm.w{grid-template-rows:auto;grid-auto-flow:row;grid-template-columns:repeat(7,1fr);gap:8px}
.hm i{display:block;aspect-ratio:1;border-radius:4px;background:var(--soft)}
.hm.w i{aspect-ratio:auto;height:64px;border-radius:10px}
.hm i.o,.hm i.f{background:none;opacity:.5;outline:1px dashed var(--line);outline-offset:-1px}
.hm i.o{visibility:hidden}
.hm i.l1{background:color-mix(in srgb,var(--ink) 25%,var(--soft))}
.hm i.l2{background:color-mix(in srgb,var(--ink) 50%,var(--soft))}
.hm i.l3{background:color-mix(in srgb,var(--ink) 75%,var(--soft))}
.hm i.l4{background:var(--ink)}
.lab{display:grid;grid-template-columns:repeat(7,1fr);gap:8px;margin-top:6px;font-size:10px;color:var(--mid);text-align:center}
.stats{display:flex;gap:28px;margin-top:16px}
.stats b{display:block;font-size:20px}.stats span{font-size:11px;color:var(--mid)}
.leg{display:flex;align-items:center;gap:4px;margin-left:auto;font-size:10px;color:var(--mid)}
.leg i{width:12px;height:12px;border-radius:3px;display:block;background:var(--soft)}
.leg i.l1{background:color-mix(in srgb,var(--ink) 25%,var(--soft))}.leg i.l2{background:color-mix(in srgb,var(--ink) 50%,var(--soft))}
.leg i.l3{background:color-mix(in srgb,var(--ink) 75%,var(--soft))}.leg i.l4{background:var(--ink)}
.hm i.d,.leg i{box-shadow:inset 0 0 0 1px rgba(128,128,128,.35)}
.nv{display:flex;align-items:center;justify-content:space-between;margin-bottom:16px}
.nv b{font-size:15px}
.ar{width:36px;height:36px;border-radius:50%;border:0;background:var(--soft);color:var(--ink);font-size:20px;line-height:1;cursor:pointer;font-family:inherit}
.ar:disabled{opacity:.3;cursor:default}
.cal{display:grid;grid-template-columns:repeat(7,1fr);gap:5px;max-width:300px;margin:0 auto}
.cal b{text-align:center;font-size:10px;color:var(--mid);font-weight:600;padding-bottom:4px}
.cal u{display:block}
.cal i{aspect-ratio:1;display:grid;place-items:center;border-radius:8px;font-style:normal}
.cal i.d{box-shadow:inset 0 0 0 1px rgba(128,128,128,.35)}
.cal i.f{color:var(--mid);outline:1px dashed var(--line);outline-offset:-1px}
.months{display:flex;flex-wrap:wrap;gap:22px 26px}
.mh{display:flex;align-items:baseline;gap:8px;margin-bottom:8px;font-size:12px}
.mh span{font-size:10px;color:var(--mid)}
.mb .hm{gap:3px}
.head b,.quote,.ring b,.stats b,.nv b{font-family:"Space Grotesk",Inter,system-ui,sans-serif}
.quote{margin:26px auto 22px;max-width:640px;text-align:center;font-size:clamp(28px,6vw,46px);font-weight:700;line-height:1.1;letter-spacing:-.02em}
.quote em{font-style:normal;color:var(--red)}
html{-webkit-text-size-adjust:100%}
body{overflow-x:hidden}
button{touch-action:manipulation;-webkit-tap-highlight-color:transparent}
input{font-size:16px}
.row{min-height:48px}
.pill{min-height:44px}
.seg button{min-height:40px}
.ar{width:44px;height:44px}
.ring svg{width:100%;height:100%}
.hmw{-webkit-overflow-scrolling:touch}
@media (max-width:600px){
.app{padding:10px 10px 32px}
.head{padding:10px 2px 4px}
.head b{font-size:20px}
.card{padding:16px;border-radius:20px}
.ring{width:150px;height:150px}
.hm.w{gap:6px}.hm.w i{height:48px}
.lab{gap:6px}
.months{gap:18px 20px}
.stats{gap:20px;flex-wrap:wrap}
.leg{margin-left:0;width:100%}
.seg{gap:4px}.seg button{padding:8px 13px}
}
@media (min-width:601px) and (max-width:1024px){.app{max-width:760px}}
.hm i,.cal i{transition:background .3s ease}
</style>
</head>
<body>
<div class="app" id="app"></div>
<script>
var K="habit-tracker-v1",S,view="home";
function load(){try{var r=localStorage.getItem(K);if(r)return JSON.parse(r)}catch(e){}return{name:"",cats:[],log:{}}}
function save(){try{localStorage.setItem(K,JSON.stringify(S))}catch(e){}}
S=load();
function day(d){d=d||new Date();return d.getFullYear()+"-"+String(d.getMonth()+1).padStart(2,"0")+"-"+String(d.getDate()).padStart(2,"0")}
function esc(s){return String(s).replace(/[&<>"']/g,function(c){return{"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"}[c]})}
function uid(){return Math.random().toString(36).slice(2,9)}
function all(){var a=[];S.cats.forEach(function(c){c.habits.forEach(function(h){a.push(h.id)})});return a}
function doneOn(k){var ids=all();return(S.log[k]||[]).filter(function(i){return ids.indexOf(i)>-1}).length}
function toggle(id){var k=day(),l=S.log[k]||[],i=l.indexOf(id);if(i>-1)l.splice(i,1);else l.push(id);S.log[k]=l;save();render()}
function addCat(v){v=v.trim();if(!v)return;S.cats.push({id:uid(),name:v,habits:[]});save();render()}
function addHabit(cid,v){v=v.trim();if(!v)return;S.cats.forEach(function(c){if(c.id===cid)c.habits.push({id:uid(),name:v})});save();render()}
function delCat(cid){S.cats=S.cats.filter(function(c){return c.id!==cid});save();render()}
function delHabit(cid,hid){S.cats.forEach(function(c){if(c.id===cid)c.habits=c.habits.filter(function(h){return h.id!==hid})});save();render()}
function header(t,sub){return'<div class="head"><div><small>'+sub+'</small><b>'+t+'</b></div><button class="menu" aria-label="Menü" onclick="go(\''+(view==="home"?"settings":"home")+'\')"><i></i><i></i><i></i></button></div>'}
function go(v){view=v;RS=0;render()}
function ring(p){var r=72,c=2*Math.PI*r;return'<svg width="170" height="170" viewBox="0 0 170 170"><circle cx="85" cy="85" r="'+r+'" fill="none" stroke="var(--soft)" stroke-width="16"/><circle cx="85" cy="85" r="'+r+'" fill="none" stroke="var(--red)" stroke-width="16" stroke-linecap="round" stroke-dasharray="'+(c*p)+' '+c+'"/></svg>'}
var hr="Jahr",hy=new Date().getFullYear(),hm={y:new Date().getFullYear(),m:new Date().getMonth()};
var MN=["Januar","Februar","März","April","Mai","Juni","Juli","August","September","Oktober","November","Dezember"];
var MS=["Jan","Feb","Mär","Apr","Mai","Jun","Jul","Aug","Sep","Okt","Nov","Dez"];
function pad(n){return String(n).padStart(2,"0")}
var ST=["#1a1a1a","#48120e","#8f1a12","#d3241a","#ff3b2e"];
function col(v){if(v>=1)return ST[4];var x=Math.max(0,v)*4,i=Math.floor(x),t=Math.round((x-i)*100);return"color-mix(in oklab,"+ST[i+1]+" "+t+"%,"+ST[i]+")"}
function lg(){return[0,.25,.5,.75,1].map(function(v){return'<i style="background:'+col(v)+'"></i>'}).join("")}
function actKeys(){var o={},n=new Date();o[n.getFullYear()+"-"+pad(n.getMonth()+1)]=1;Object.keys(S.log).forEach(function(k){if(doneOn(k)>0)o[k.slice(0,7)]=1});return Object.keys(o).sort()}
function step(dir){
 if(dir>0){if(hr==="Monat"){var d=new Date(hm.y,hm.m+1,1);return d.getFullYear()+"-"+pad(d.getMonth()+1)}return String(hy+1)}
 var ks=actKeys(),cur=hr==="Monat"?hm.y+"-"+pad(hm.m+1):String(hy);
 if(hr==="Jahr")ks=ks.map(function(k){return k.slice(0,4)}).filter(function(k,i,a){return a.indexOf(k)===i});
 var c=ks.filter(function(k){return dir<0?k<cur:k>cur});
 if(!c.length)return null;
 return dir<0?c[c.length-1]:c[0];
}
function jump(dir){var k=step(dir);if(!k)return;if(hr==="Monat")hm={y:+k.slice(0,4),m:+k.slice(5,7)-1};else hy=+k;render()}
function nav(title){
 var p=step(-1),n=step(1);
 return'<div class="nv"><button class="ar" data-n="-1" aria-label="Zurück"'+(p?'':' disabled')+'>&#8249;</button><b>'+title+'</b><button class="ar" data-n="1" aria-label="Weiter"'+(n?'':' disabled')+'>&#8250;</button></div>';
}
function mcells(y,m,total,t){
 var first=new Date(y,m,1),last=new Date(y,m+1,0),st=new Date(first);st.setDate(1-((first.getDay()+6)%7));
 var h="",cnt=0,act=0,sum=0;
 for(var c=new Date(st);c<=last;c.setDate(c.getDate()+1)){
  var out=c<first,fut=c>t,n=0,v=0,k=day(c);
  if(!out&&!fut){n=doneOn(k);v=total?n/total:0;if(n){act++;sum+=n}}
  h+='<i class="'+(out?"o":fut?"f":"d")+'"'+(out||fut?'':' style="background:'+col(v)+'"')+' title="'+k+': '+n+'"></i>';cnt++;
 }
 return{h:h,cols:Math.ceil(cnt/7),act:act,sum:sum};
}
function cal(y,m,total,t){
 var first=new Date(y,m,1),nd=new Date(y,m+1,0).getDate(),off=(first.getDay()+6)%7,h="",act=0,sum=0;
 ["Mo","Di","Mi","Do","Fr","Sa","So"].forEach(function(d){h+='<b>'+d+'</b>'});
 for(var i=0;i<off;i++)h+='<u></u>';
 for(var d=1;d<=nd;d++){var c=new Date(y,m,d),fut=c>t,n=0,v=0,k=day(c);
  if(!fut){n=doneOn(k);v=total?n/total:0;if(n){act++;sum+=n}}
  h+=fut?'<i class="f"></i>':'<i class="d" style="background:'+col(v)+';color:'+(v>.5?'#1c1c1c':'#fff')+'" title="'+k+': '+n+'"></i>'}
 return{h:'<div class="cal">'+h+'</div>',act:act,sum:sum};
}
function heat(){
 var total=all().length,t=new Date();t.setHours(0,0,0,0);
 var body="",head="",act=0,sum=0,seg='<div class="seg">';
 ["Woche","Monat","Jahr","Gesamt"].forEach(function(x){seg+='<button data-hr="'+x+'" class="'+(x===hr?"on":"")+'">'+x+'</button>'});
 seg+='</div>';
 if(hr==="Woche"){
  var cells="",labs="",dn=["So","Mo","Di","Mi","Do","Fr","Sa"];
  for(var i=6;i>=0;i--){var c=new Date(t);c.setDate(c.getDate()-i);var k=day(c),n=doneOn(k),v=total?n/total:0;if(n){act++;sum+=n}
   cells+='<i class="d" style="background:'+col(v)+'" title="'+k+': '+n+'"></i>';labs+='<span>'+dn[c.getDay()]+'</span>'}
  body='<div class="hm w">'+cells+'</div><div class="lab">'+labs+'</div>';
 }else if(hr==="Monat"){
  var q=cal(hm.y,hm.m,total,t);act=q.act;sum=q.sum;head=nav(MN[hm.m]+" "+hm.y);body=q.h;
 }else{
  var list=[];
  if(hr==="Jahr"){for(var m=0;m<12;m++)list.push([hy,m]);head=nav(String(hy))}
  else{var f=actKeys()[0],y=+f.slice(0,4),m2=+f.slice(5,7)-1;while(y<t.getFullYear()||(y===t.getFullYear()&&m2<=t.getMonth())){list.push([y,m2]);m2++;if(m2>11){m2=0;y++}}}
  body='<div class="months">';
  list.forEach(function(p){var r=mcells(p[0],p[1],total,t);act+=r.act;sum+=r.sum;
   body+='<div class="mb"><div class="mh"><b>'+(hr==="Jahr"?MS[p[1]]:MS[p[1]]+" "+String(p[0]).slice(2))+'</b></div><div class="hm" style="grid-template-columns:repeat('+r.cols+',12px);width:max-content">'+r.h+'</div></div>'});
  body+='</div>';
 }
 return'<div class="card" style="margin-top:12px"><h2>Aktivität</h2>'+seg+head+body+'<div class="stats"><div><b>'+sum+'</b><span>erledigt</span></div><div><b>'+act+'</b><span>aktive Tage</span></div><div class="leg"><span>Weniger</span>'+lg()+'<span>Mehr</span></div></div></div>';
}
var QS=[["Heute entscheidest du,","wer du morgen bist."],["Jeder Haken bringt dich","näher ans Ziel."],["Andere reden.","Du lieferst."],["Dranbleiben schlägt","jedes Talent."],["Kleine Schritte heute,","große Ergebnisse morgen."],["Disziplin ist","dein größter Vorteil."],["Mach den nächsten Haken.","Jetzt."],["Dein Erfolg wächst,","wenn du es tust."],["Heute zählt.","Zeig, was du kannst."],["Bau Gewohnheiten,","die ohne dich laufen."]];
var Q=QS[Math.floor(Math.random()*QS.length)];
var RS=0;
function render(){
 var el=document.getElementById("app");
 if(false){
  el.innerHTML='<div class="hello"><h1>Hi</h1><input id="n" placeholder="Dein Name" maxlength="20" autocomplete="off"><button class="pill" id="go">Start</button></div>';
  var n=document.getElementById("n");
  function st(){var v=n.value.trim();if(v){S.name=v;save();render()}}
  document.getElementById("go").onclick=st;n.onkeydown=function(e){if(e.key==="Enter")st()};return}
 var total=all().length,d=doneOn(day()),p=total?d/total:0,h="";
 if(view==="settings"){
  h=header("Einstellungen",esc(S.name))+'<div class="card"><h2>Name</h2><div class="add"><input id="nm" value="'+esc(S.name)+'" maxlength="20"><button class="pill" id="sn">Ok</button></div></div>';
  h+='<div class="card"><h2>Kategorien</h2>';
  if(!S.cats.length)h+='<div class="empty">Noch nichts da</div>';
  S.cats.forEach(function(c){
   h+='<div class="row" style="cursor:default"><span style="flex:1">'+esc(c.name)+'</span><button class="ghost" data-dc="'+c.id+'">Löschen</button></div>';
   c.habits.forEach(function(x){h+='<div class="row" style="cursor:default;padding-left:14px;font-weight:400"><span style="flex:1">'+esc(x.name)+'</span><button class="ghost" data-dh="'+c.id+'|'+x.id+'">Löschen</button></div>'})
  });
  h+='</div><div class="card"><button class="ghost" id="rs"'+(RS?' style="color:var(--red);font-weight:600"':'')+'>'+["Alles zurücksetzen","Bist du sicher?","Wirklich sicher? Das löscht alles."][RS]+'</button>'+(RS?'<button class="ghost" id="rc">Abbrechen</button>':'')+'</div>';
  el.innerHTML=h;
  document.getElementById("sn").onclick=function(){var v=document.getElementById("nm").value.trim();if(v){S.name=v;save();go("home")}};
  el.querySelectorAll("[data-dc]").forEach(function(b){b.onclick=function(){delCat(b.dataset.dc)}});
  el.querySelectorAll("[data-dh]").forEach(function(b){b.onclick=function(){var a=b.dataset.dh.split("|");delHabit(a[0],a[1])}});
  document.getElementById("rs").onclick=function(){RS++;if(RS>2){RS=0;S={name:"",cats:[],log:{}};save();view="home"}render()};
  var rc=document.getElementById("rc");if(rc)rc.onclick=function(){RS=0;render()};
  return}
 h=header("Habits",S.name?esc(S.name):"Heute")+'<div class="quote">'+Q[0]+' <em>'+Q[1]+'</em></div>';
 h+='<div class="grid"><div class="card"><div class="ringwrap"><div class="ring">'+ring(p)+'<div><b>'+d+'/'+total+'</b><span>erledigt</span></div></div></div></div>';
 var days=["So","Mo","Di","Mi","Do","Fr","Sa"],bars="";
 for(var i=6;i>=0;i--){var dt=new Date();dt.setDate(dt.getDate()-i);var v=total?doneOn(day(dt))/total:0;bars+='<div class="'+(i===0?"t":"")+'"><u style="height:'+Math.max(6,Math.round(v*62))+'px"></u>'+days[dt.getDay()]+'</div>'}
 h+='<div class="card"><h2>Woche</h2><div class="bars">'+bars+'</div></div></div>'+heat();
 var log=S.log[day()]||[];h+='<div class="grid">';
 S.cats.forEach(function(c){
  h+='<div class="card"><h2>'+esc(c.name)+'</h2>';
  if(!c.habits.length)h+='<div class="empty">Füge dein erstes Habit hinzu</div>';
  c.habits.forEach(function(x){h+='<button class="row '+(log.indexOf(x.id)>-1?"done":"")+'" data-t="'+x.id+'"><i class="box"></i><span>'+esc(x.name)+'</span></button>'});
  h+='<div class="add"><input data-hi="'+c.id+'" placeholder="Neues Habit" maxlength="40"><button class="pill" data-ha="'+c.id+'">+</button></div></div>'
 });
 h+='<div class="card"><h2>Neue Kategorie</h2><div class="add" style="margin-top:0"><input id="cn" placeholder="z.B. Content" maxlength="24"><button class="pill" id="ca">+</button></div></div></div>';
 el.innerHTML=h;
 el.querySelectorAll("[data-hr]").forEach(function(b){b.onclick=function(){hr=b.dataset.hr;render()}});
 el.querySelectorAll("[data-n]").forEach(function(b){b.onclick=function(){jump(+b.dataset.n)}});
 el.querySelectorAll("[data-t]").forEach(function(b){b.onclick=function(){toggle(b.dataset.t)}});
 el.querySelectorAll("[data-ha]").forEach(function(b){var i=el.querySelector('[data-hi="'+b.dataset.ha+'"]');b.onclick=function(){addHabit(b.dataset.ha,i.value)};i.onkeydown=function(e){if(e.key==="Enter")addHabit(b.dataset.ha,i.value)}});
 var cn=document.getElementById("cn");document.getElementById("ca").onclick=function(){addCat(cn.value)};cn.onkeydown=function(e){if(e.key==="Enter")addCat(cn.value)};
}
render();
</script>
</body>
</html>
