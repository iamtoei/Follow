<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no">
<title>ระบบติดตามลูกค้า</title>

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.9.4/leaflet.min.css">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Sans+Thai:wght@400;500;600;700&family=Noto+Sans+Thai:wght@400;500;700&display=swap" rel="stylesheet">

<style>
  :root{
    --ink:#0d1b2a;
    --panel:#12263a;
    --panel-2:#1b3650;
    --line:#e2e8ed;
    --surface:#ffffff;
    --muted:#64748b;
    --text:#0f2235;
    --accent:#0e7c66;       /* การกระทำหลัก */
    --accent-press:#0a6253;
    --gold:#b45309;          /* ยอดค้าง / เงิน */
    --owe:#dc2626;
    --clear:#16a34a;
    --unknown:#94a3b8;
    --shadow:0 10px 30px rgba(13,27,42,.18);
    --shadow-sm:0 4px 14px rgba(13,27,42,.14);
    --r:16px;
    font-family:"IBM Plex Sans Thai","Noto Sans Thai",system-ui,sans-serif;
  }
  *{box-sizing:border-box}
  html,body{margin:0;height:100%;background:var(--ink);color:var(--text);
    -webkit-tap-highlight-color:transparent;overscroll-behavior:none}
  #map{position:fixed;inset:0;z-index:0}
  .num{font-variant-numeric:tabular-nums}

  /* ---------- แถบค้นหาด้านบน ---------- */
  .searchwrap{position:fixed;top:14px;left:50%;transform:translateX(-50%);
    z-index:600;width:min(560px,calc(100% - 28px))}
  .searchbar{display:flex;align-items:center;gap:10px;background:var(--surface);
    border-radius:999px;box-shadow:var(--shadow);padding:8px 8px 8px 16px}
  .searchbar svg{flex:0 0 auto;color:var(--muted)}
  .searchbar input{flex:1;border:0;outline:0;font:inherit;font-size:16px;
    background:transparent;color:var(--text);min-width:0}
  .searchbar input::placeholder{color:#9aa7b4}
  .searchbar .go{flex:0 0 auto;border:0;background:var(--accent);color:#fff;
    width:38px;height:38px;border-radius:999px;cursor:pointer;font-size:15px;
    display:grid;place-items:center}
  .searchbar .go:active{background:var(--accent-press)}
  .suggest{margin-top:8px;background:var(--surface);border-radius:14px;
    box-shadow:var(--shadow);overflow:hidden;display:none}
  .suggest.open{display:block}
  .suggest button{display:flex;gap:10px;align-items:center;width:100%;border:0;
    background:none;text-align:left;padding:11px 16px;cursor:pointer;font:inherit;
    font-size:14.5px;color:var(--text);border-top:1px solid var(--line)}
  .suggest button:first-child{border-top:0}
  .suggest button:hover{background:#f4f7f9}
  .suggest .pin{color:var(--accent);flex:0 0 auto}
  .suggest .t2{display:block;font-size:12px;color:var(--muted);margin-top:1px}

  /* ---------- แถบสรุปบน ---------- */
  .stats{position:fixed;top:70px;left:14px;z-index:550;display:flex;gap:8px;
    flex-wrap:wrap;max-width:calc(100% - 28px)}
  .chip{background:var(--surface);border-radius:999px;box-shadow:var(--shadow-sm);
    padding:7px 13px;font-size:13px;display:flex;gap:7px;align-items:center;white-space:nowrap}
  .chip b{font-size:14px}
  .chip .dot{width:8px;height:8px;border-radius:50%}

  /* ---------- ปุ่มลอยขวาล่าง ---------- */
  .fabs{position:fixed;right:16px;bottom:18px;z-index:600;display:flex;
    flex-direction:column;gap:12px;align-items:flex-end}
  .fab{width:58px;height:58px;border-radius:50%;border:0;cursor:pointer;
    box-shadow:var(--shadow);display:grid;place-items:center;font-size:24px;
    color:#fff;transition:transform .15s,background .15s}
  .fab:active{transform:scale(.94)}
  .fab.add{background:var(--accent)}
  .fab.add.on{background:var(--owe);transform:rotate(45deg)}
  .fab.mini{width:46px;height:46px;font-size:18px;background:var(--panel)}
  .fab.list{background:var(--panel)}

  /* ---------- โหมดปักหมุด ฮินต์ ---------- */
  .hint{position:fixed;left:50%;bottom:24px;transform:translateX(-50%) translateY(20px);
    z-index:590;background:var(--ink);color:#fff;padding:11px 18px;border-radius:999px;
    font-size:14.5px;box-shadow:var(--shadow);opacity:0;pointer-events:none;
    transition:.25s;display:flex;gap:8px;align-items:center}
  .hint.on{opacity:1;transform:translateX(-50%) translateY(0)}

  /* ---------- แผ่นฟอร์ม / การ์ด ---------- */
  .scrim{position:fixed;inset:0;background:rgba(13,27,42,.45);z-index:900;
    opacity:0;pointer-events:none;transition:.2s}
  .scrim.on{opacity:1;pointer-events:auto}
  .sheet{position:fixed;z-index:950;background:var(--surface);box-shadow:var(--shadow);
    left:50%;bottom:0;transform:translateX(-50%) translateY(110%);
    width:min(460px,100%);border-radius:22px 22px 0 0;transition:transform .28s cubic-bezier(.2,.8,.2,1);
    max-height:92vh;display:flex;flex-direction:column}
  .sheet.on{transform:translateX(-50%) translateY(0)}
  .sheet .grab{width:40px;height:4px;border-radius:99px;background:#cdd7df;
    margin:10px auto 2px}
  .sheet h2{margin:6px 22px 2px;font-size:19px;font-weight:700}
  .sheet .sub{margin:0 22px 4px;color:var(--muted);font-size:13px}
  .sheet form{overflow:auto;padding:8px 22px 0}
  .field{margin-top:12px}
  .field label{display:block;font-size:13px;color:var(--muted);margin-bottom:5px;font-weight:500}
  .field input{width:100%;border:1.5px solid var(--line);border-radius:11px;
    padding:12px 13px;font:inherit;font-size:16px;outline:0;background:#fbfcfd;color:var(--text)}
  .field input:focus{border-color:var(--accent);background:#fff}
  .row{display:flex;gap:10px}
  .row .field{flex:1}
  .money input{text-align:right}
  .owebox{margin-top:14px;background:#fff8f1;border:1.5px solid #f3d8b8;
    border-radius:13px;padding:13px 15px;display:flex;justify-content:space-between;align-items:center}
  .owebox span{font-size:13px;color:var(--gold);font-weight:600}
  .owebox b{font-size:23px;color:var(--gold);font-weight:700}
  .teamline{display:flex;gap:8px;flex-wrap:wrap;margin-top:8px}
  .teamline button{border:1.5px solid var(--line);background:#fff;border-radius:999px;
    padding:7px 14px;font:inherit;font-size:14px;cursor:pointer;color:var(--text)}
  .teamline button.sel{border-color:var(--accent);background:#e7f4f0;color:var(--accent-press);font-weight:600}
  .actions{position:sticky;bottom:0;background:var(--surface);padding:14px 0 calc(16px + env(safe-area-inset-bottom));
    display:flex;gap:10px;margin-top:8px}
  .btn{flex:1;border:0;border-radius:13px;padding:15px;font:inherit;font-size:16px;
    font-weight:600;cursor:pointer}
  .btn.primary{background:var(--accent);color:#fff}
  .btn.primary:active{background:var(--accent-press)}
  .btn.ghost{flex:0 0 auto;background:#eef2f5;color:var(--text);padding-left:22px;padding-right:22px}
  .btn.danger{background:#fdeaea;color:var(--owe)}

  /* ---------- การ์ดดูข้อมูลลูกค้า ---------- */
  .view .vline{display:flex;justify-content:space-between;padding:11px 0;
    border-top:1px solid var(--line);font-size:15px}
  .view .vline:first-of-type{border-top:0}
  .view .vline span{color:var(--muted)}
  .view .vbig{font-size:18px;font-weight:700;margin:2px 0 2px}
  .tag{display:inline-flex;align-items:center;gap:6px;font-size:13px;font-weight:600;
    padding:4px 11px;border-radius:999px}
  .tag .dot{width:8px;height:8px;border-radius:50%}
  .tag.owe{background:#fdecec;color:var(--owe)}
  .tag.clear{background:#e8f6ec;color:var(--clear)}

  /* ---------- พาเนลรายชื่อ ---------- */
  .listpanel{position:fixed;top:0;right:0;bottom:0;width:min(380px,100%);z-index:800;
    background:var(--surface);box-shadow:var(--shadow);transform:translateX(105%);
    transition:transform .26s cubic-bezier(.2,.8,.2,1);display:flex;flex-direction:column}
  .listpanel.on{transform:translateX(0)}
  .lphead{padding:18px 18px 12px;border-bottom:1px solid var(--line);display:flex;
    align-items:center;justify-content:space-between}
  .lphead h2{margin:0;font-size:18px;font-weight:700}
  .lphead .x{border:0;background:#eef2f5;width:34px;height:34px;border-radius:50%;
    cursor:pointer;font-size:17px}
  .lpfilter{display:flex;gap:7px;overflow:auto;padding:11px 18px;border-bottom:1px solid var(--line)}
  .lpfilter button{border:1.5px solid var(--line);background:#fff;border-radius:999px;
    padding:6px 13px;font:inherit;font-size:13.5px;cursor:pointer;white-space:nowrap;color:var(--text)}
  .lpfilter button.sel{border-color:var(--accent);background:#e7f4f0;color:var(--accent-press);font-weight:600}
  .lplist{overflow:auto;flex:1;padding:8px 0}
  .cust{display:flex;align-items:center;gap:12px;padding:12px 18px;cursor:pointer}
  .cust:hover{background:#f6f9fa}
  .cust .av{width:40px;height:40px;border-radius:12px;flex:0 0 auto;display:grid;
    place-items:center;color:#fff;font-weight:700;font-size:16px}
  .cust .info{flex:1;min-width:0}
  .cust .nm{font-weight:600;font-size:15px;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
  .cust .meta{font-size:12.5px;color:var(--muted);white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
  .cust .amt{text-align:right;font-size:14px;font-weight:700}
  .empty{text-align:center;color:var(--muted);padding:50px 24px;font-size:14.5px;line-height:1.7}

  /* ---------- ตั้งค่า Google Sheet ---------- */
  .sync{margin-top:6px;font-size:13px}
  .sync ol{margin:8px 0 0;padding-left:20px;line-height:1.75;color:var(--text)}
  .sync code{background:#f1f5f8;padding:1px 6px;border-radius:6px;font-size:12.5px}
  .sync textarea{width:100%;margin-top:10px;border:1.5px solid var(--line);border-radius:10px;
    padding:11px;font:13px/1.6 ui-monospace,monospace;height:150px;resize:vertical;background:#fbfcfd}
  .codebox{position:relative;margin-top:8px}
  .codebox pre{background:#0d1b2a;color:#d6e4f0;border-radius:12px;padding:14px;
    overflow:auto;font:12px/1.6 ui-monospace,monospace;max-height:210px;margin:0}
  .copybtn{position:absolute;top:8px;right:8px;border:0;background:#1b3650;color:#fff;
    border-radius:8px;padding:6px 11px;font:inherit;font-size:12px;cursor:pointer}
  .syncrow{display:flex;gap:8px;align-items:center;margin-top:10px}
  .syncrow input{flex:1;border:1.5px solid var(--line);border-radius:10px;padding:11px;font:inherit;font-size:14px}

  /* ---------- toast ---------- */
  .toast{position:fixed;left:50%;bottom:96px;transform:translateX(-50%) translateY(20px);
    z-index:1100;background:var(--ink);color:#fff;padding:12px 20px;border-radius:999px;
    font-size:14.5px;box-shadow:var(--shadow);opacity:0;pointer-events:none;transition:.25s;
    display:flex;gap:9px;align-items:center;max-width:90%}
  .toast.on{opacity:1;transform:translateX(-50%) translateY(0)}
  .toast.err{background:#7f1d1d}

  /* ---------- หมุดบนแผนที่ ---------- */
  .pin-ico{position:relative}
  .pin-ico .pin-body{width:30px;height:30px;border-radius:50% 50% 50% 0;transform:rotate(-45deg);
    box-shadow:0 3px 8px rgba(0,0,0,.35);border:2.5px solid #fff;display:grid;place-items:center}
  .pin-ico .pin-body b{transform:rotate(45deg);color:#fff;font-size:11px;font-weight:700}
  .leaflet-popup-content-wrapper{border-radius:13px}
  .leaflet-popup-content{margin:12px 15px;font-family:inherit}

  .loader{position:fixed;inset:0;z-index:2000;background:var(--ink);color:#cfe;
    display:grid;place-items:center;font-size:15px;transition:.3s}
  .loader.gone{opacity:0;pointer-events:none}

  @media(max-width:520px){
    .stats{top:66px}
    .sheet{width:100%}
  }
  @media(prefers-reduced-motion:reduce){*{transition:none!important}}
</style>

<div id="map"></div>

<!-- ค้นหา -->
<div class="searchwrap">
  <div class="searchbar">
    <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="11" cy="11" r="7"/><path d="M21 21l-4-4"/></svg>
    <input id="search" placeholder="ค้นหาจังหวัด/อำเภอ หรือวางลิงก์ Google Maps" autocomplete="off">
    <button class="go" id="goBtn" aria-label="ค้นหา">➜</button>
  </div>
  <div class="suggest" id="suggest"></div>
</div>

<!-- สรุป -->
<div class="stats" id="stats"></div>

<!-- ปุ่มลอย -->
<div class="fabs">
  <button class="fab mini" id="syncBtn" title="ตั้งค่า Google Sheet">⚙️</button>
  <button class="fab list" id="listBtn" title="รายชื่อลูกค้า">☰</button>
  <button class="fab add" id="addBtn" title="เพิ่มลูกค้า">📍</button>
</div>

<div class="hint" id="hint">👆 แตะตำแหน่งลูกค้าบนแผนที่</div>

<!-- scrim + sheet -->
<div class="scrim" id="scrim"></div>
<div class="sheet" id="sheet"></div>

<!-- พาเนลรายชื่อ -->
<div class="listpanel" id="listpanel">
  <div class="lphead"><h2>รายชื่อลูกค้า</h2><button class="x" id="lpClose">✕</button></div>
  <div class="lpfilter" id="lpfilter"></div>
  <div class="lplist" id="lplist"></div>
</div>

<div class="toast" id="toast"></div>
<div class="loader" id="loader">กำลังเปิดแผนที่…</div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.9.4/leaflet.min.js"></script>
<script>
(function(){
'use strict';

/* ============ สถานะ ============ */
var STORE_KEY='customers', CFG_KEY='cfg';
var customers=[];           // {id,name,phone,model,total,down,paid,outstanding,team,area,lat,lng,ts}
var cfg={sheetUrl:''};
var markers={};             // id -> leaflet marker
var map, addMode=false, tempMarker=null, editingId=null, filterTeam='ทั้งหมด';
var TEAMS=['ทีม A','ทีม B','ทีม C'];   // ปรับได้ในฟอร์ม

var $=function(s){return document.querySelector(s)};
var baht=function(n){n=Number(n)||0;return '฿'+n.toLocaleString('th-TH')};
var esc=function(s){return String(s==null?'':s).replace(/[&<>"]/g,function(c){return{'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;'}[c]})};

/* ============ storage (คงข้อมูลข้ามครั้งเปิด) ============
   เปิดใน Claude -> ใช้ window.storage / เปิดนอก Claude -> ใช้ localStorage ของเครื่อง */
var hasWS = (typeof window!=='undefined' && window.storage && typeof window.storage.get==='function');
async function dbGet(k){
  if(hasWS){ try{var r=await window.storage.get(k); return (r&&r.value!=null)?r.value:null;}catch(e){return null;} }
  try{ return localStorage.getItem(k); }catch(e){ return null; }
}
async function dbSet(k,v){
  if(hasWS){ try{ await window.storage.set(k,v); return true; }catch(e){} }
  try{ localStorage.setItem(k,v); return true; }catch(e){ return false; }
}
async function loadStore(){
  try{var r=await dbGet(STORE_KEY); if(r) customers=JSON.parse(r);}catch(e){customers=[];}
  try{var c=await dbGet(CFG_KEY); if(c) cfg=Object.assign(cfg,JSON.parse(c));}catch(e){}
}
async function saveStore(){
  var ok=await dbSet(STORE_KEY,JSON.stringify(customers));
  if(!ok) toast('เก็บข้อมูลในเครื่องไม่ได้',true);
}
async function saveCfg(){ await dbSet(CFG_KEY,JSON.stringify(cfg)); }

/* ============ แผนที่ ============ */
function initMap(){
  map=L.map('map',{zoomControl:false,attributionControl:false}).setView([13.736,100.523],6);
  L.control.zoom({position:'bottomleft'}).addTo(map);
  L.tileLayer('https://{s}.basemaps.cartocdn.com/rastertiles/voyager/{z}/{x}/{y}{r}.png',
    {maxZoom:19,subdomains:'abcd'}).addTo(map);
  map.on('click',function(e){ if(addMode) onDrop(e.latlng); });
}

function statusOf(c){
  var t=Number(c.total)||0, owe=Number(c.outstanding);
  if(!t && !c.down && !c.paid) return 'unknown';
  return owe>0 ? 'owe' : 'clear';
}
function colorOf(c){return {owe:'#dc2626',clear:'#16a34a',unknown:'#94a3b8'}[statusOf(c)];}

function makeIcon(c){
  var col=colorOf(c), initial=(c.name||'?').trim().charAt(0)||'?';
  return L.divIcon({className:'',iconSize:[30,40],iconAnchor:[15,38],popupAnchor:[0,-36],
    html:'<div class="pin-ico"><div class="pin-body" style="background:'+col+'"><b>'+esc(initial)+'</b></div></div>'});
}
function addMarker(c){
  var m=L.marker([c.lat,c.lng],{icon:makeIcon(c)}).addTo(map);
  m.on('click',function(){ openView(c.id); });
  markers[c.id]=m;
}
function refreshMarker(c){ if(markers[c.id]){markers[c.id].setIcon(makeIcon(c));} }
function renderAllMarkers(){ Object.values(markers).forEach(function(m){map.removeLayer(m)}); markers={};
  customers.forEach(addMarker); }

/* ============ ค้นหาสถานที่ (Nominatim) ============ */
var searchTimer=null;
function onSearchInput(){
  var q=$('#search').value.trim();
  clearTimeout(searchTimer);
  $('#suggest').classList.remove('open');
  if(isMapUrl(q)) return;            // เป็นลิงก์ Maps -> รอกด Enter/ปุ่ม
  if(q.length<2) return;
  searchTimer=setTimeout(function(){ doGeocode(q,true); },350);
}
function onSearchSubmit(){
  var q=$('#search').value.trim();
  if(!q) return;
  if(isMapUrl(q)) handleMapLink(q);
  else doGeocode(q,false);
}
function doGeocode(q,suggest){
  var url='https://nominatim.openstreetmap.org/search?format=json&addressdetails=1&limit=6&countrycodes=th&accept-language=th&q='+encodeURIComponent(q);
  fetch(url,{headers:{'Accept':'application/json'}}).then(function(r){return r.json()}).then(function(list){
    if(!list||!list.length){ if(!suggest) toast('ไม่พบสถานที่นี้',true); $('#suggest').classList.remove('open'); return; }
    if(suggest){ renderSuggest(list); }
    else{ flyTo(list[0]); $('#suggest').classList.remove('open'); }
  }).catch(function(){ toast('ค้นหาไม่สำเร็จ ลองใหม่',true); });
}
function renderSuggest(list){
  var box=$('#suggest'); box.innerHTML='';
  list.forEach(function(it){
    var b=document.createElement('button');
    var name=it.display_name.split(',')[0];
    var rest=it.display_name.split(',').slice(1,4).join(',').trim();
    b.innerHTML='<span class="pin">📍</span><span>'+esc(name)+'<span class="t2">'+esc(rest)+'</span></span>';
    b.onclick=function(){ flyTo(it); box.classList.remove('open'); $('#search').value=name; };
    box.appendChild(b);
  });
  box.classList.add('open');
}
function flyTo(it){
  var z= it.type&&/state|province/.test(it.type)?10:13;
  map.flyTo([+it.lat,+it.lon],z,{duration:.9});
}

/* ============ ลิงก์ Google Maps ============ */
function isMapUrl(q){ return /^https?:\/\//i.test(q) && /(google\.[^/]+\/maps|maps\.app\.goo\.gl|goo\.gl\/maps|maps\.google)/i.test(q); }
function parseLatLng(s){
  if(!s) return null; s=String(s);
  var tries=[s]; try{tries.push(decodeURIComponent(s));}catch(e){}
  for(var i=0;i<tries.length;i++){
    var x=tries[i],m;
    if((m=x.match(/@(-?\d+\.\d+),(-?\d+\.\d+)/)))                                  return {lat:+m[1],lng:+m[2]};
    if((m=x.match(/!3d(-?\d+\.\d+)!4d(-?\d+\.\d+)/)))                              return {lat:+m[1],lng:+m[2]};
    if((m=x.match(/[?&](?:q|query|ll|center|destination|daddr|sll)=(-?\d+\.\d+),(-?\d+\.\d+)/))) return {lat:+m[1],lng:+m[2]};
    if((m=x.match(/\/(-?\d+\.\d+),\+?(-?\d+\.\d+)/)))                              return {lat:+m[1],lng:+m[2]};
  }
  return null;
}
function goToMapPoint(lat,lng){
  var latlng=L.latLng(lat,lng);
  $('#search').value='';
  map.flyTo(latlng,16,{duration:.8});
  setTimeout(function(){ onDrop(latlng); },850);
}
function handleMapLink(q){
  $('#suggest').classList.remove('open');
  var ll=parseLatLng(q);
  if(ll){ toast('กำลังไปยังพิกัด…'); goToMapPoint(ll.lat,ll.lng); return; }
  if(/goo\.gl|maps\.app/i.test(q)){           // ลิงก์สั้น -> ให้ Apps Script คลี่
    if(!cfg.sheetUrl){ toast('ลิงก์สั้นต้องตั้งค่า ⚙️ ก่อน',true); return; }
    toast('กำลังคลี่ลิงก์สั้น…');
    resolveShortLink(q,function(res){
      if(res) goToMapPoint(res.lat,res.lng);
      else toast('คลี่ลิงก์ไม่สำเร็จ — ลองเปิดลิงก์แล้วก็อปลิงก์ยาวมาวาง',true);
    });
    return;
  }
  toast('อ่านพิกัดจากลิงก์นี้ไม่ได้',true);
}
function resolveShortLink(url,cb){
  var name='__mapcb'+Date.now()+Math.floor(Math.random()*999);
  var s=document.createElement('script');
  var to=setTimeout(function(){ cleanup(); cb(null); },13000);
  function cleanup(){ try{delete window[name]}catch(e){window[name]=undefined} if(s.parentNode)s.parentNode.removeChild(s); clearTimeout(to); }
  window[name]=function(d){ cleanup(); cb(d&&d.ok&&d.lat!=null?{lat:+d.lat,lng:+d.lng}:null); };
  s.onerror=function(){ cleanup(); cb(null); };
  s.src=cfg.sheetUrl+(cfg.sheetUrl.indexOf('?')>-1?'&':'?')+'resolve='+encodeURIComponent(url)+'&callback='+name;
  document.body.appendChild(s);
}

/* ============ ปักหมุด + ฟอร์ม ============ */
function toggleAdd(force){
  addMode=(force!=null)?force:!addMode;
  $('#addBtn').classList.toggle('on',addMode);
  $('#hint').classList.toggle('on',addMode);
  map.getContainer().style.cursor=addMode?'crosshair':'';
}
function onDrop(latlng){
  toggleAdd(false);
  if(tempMarker) map.removeLayer(tempMarker);
  tempMarker=L.marker(latlng,{icon:makeIcon({name:'+',total:0})}).addTo(map);
  editingId=null;
  openForm({lat:latlng.lat,lng:latlng.lng});
  reverseGeo(latlng,function(area){ var f=$('#f_area'); if(f && !f.value) f.value=area; });
}
function reverseGeo(latlng,cb){
  var url='https://nominatim.openstreetmap.org/reverse?format=json&zoom=12&accept-language=th&lat='+latlng.lat+'&lon='+latlng.lng;
  fetch(url).then(function(r){return r.json()}).then(function(d){
    var a=d.address||{}; var parts=[a.suburb||a.village||a.town||a.city_district||a.county, a.state||a.province].filter(Boolean);
    cb(parts.join(' · '));
  }).catch(function(){});
}

function openForm(rec){
  rec=rec||{};
  var teams=TEAMS.slice(); if(rec.team && teams.indexOf(rec.team)<0) teams.unshift(rec.team);
  var teamBtns=teams.map(function(t){return '<button type="button" data-team="'+esc(t)+'"'+(rec.team===t?' class="sel"':'')+'>'+esc(t)+'</button>'}).join('');
  $('#sheet').innerHTML=
   '<div class="grab"></div>'+
   '<h2>'+(editingId?'แก้ไขข้อมูลลูกค้า':'ลูกค้าใหม่')+'</h2>'+
   '<p class="sub">ยอดค้างจะคำนวณให้อัตโนมัติ</p>'+
   '<form id="custForm">'+
     '<div class="field"><label>ชื่อลูกค้า</label><input id="f_name" value="'+esc(rec.name||'')+'" placeholder="เช่น สมชาย ใจดี"></div>'+
     '<div class="row">'+
       '<div class="field"><label>เบอร์โทร</label><input id="f_phone" inputmode="tel" value="'+esc(rec.phone||'')+'" placeholder="08x-xxx-xxxx"></div>'+
       '<div class="field"><label>รุ่น</label><input id="f_model" value="'+esc(rec.model||'')+'" placeholder="รุ่นสินค้า"></div>'+
     '</div>'+
     '<div class="field money"><label>ราคาเต็ม</label><input id="f_total" inputmode="numeric" value="'+(rec.total||'')+'" placeholder="0"></div>'+
     '<div class="row money">'+
       '<div class="field"><label>ดาวน์</label><input id="f_down" inputmode="numeric" value="'+(rec.down||'')+'" placeholder="0"></div>'+
       '<div class="field"><label>จ่ายแล้ว (เพิ่ม)</label><input id="f_paid" inputmode="numeric" value="'+(rec.paid||'')+'" placeholder="0"></div>'+
     '</div>'+
     '<div class="owebox"><span>ยอดค้าง</span><b id="f_owe">฿0</b></div>'+
     '<div class="field"><label>ทีมที่ดูแล (เว้นได้)</label><div class="teamline" id="f_teams">'+teamBtns+'</div>'+
       '<input id="f_team" style="margin-top:8px" value="'+esc(rec.team||'')+'" placeholder="หรือพิมพ์ชื่อทีมเอง"></div>'+
     '<div class="field"><label>พื้นที่ (เติมอัตโนมัติ)</label><input id="f_area" value="'+esc(rec.area||'')+'" placeholder="อำเภอ · จังหวัด"></div>'+
     '<div class="actions">'+
       (editingId?'<button type="button" class="btn danger" id="delBtn">ลบ</button>':'<button type="button" class="btn ghost" id="cancelBtn">ยกเลิก</button>')+
       '<button type="submit" class="btn primary">บันทึก</button>'+
     '</div>'+
   '</form>';
  // events
  ['f_total','f_down','f_paid'].forEach(function(id){ $('#'+id).addEventListener('input',calcOwe); });
  $('#f_teams').addEventListener('click',function(e){
    var b=e.target.closest('button[data-team]'); if(!b)return;
    [].forEach.call(this.children,function(x){x.classList.remove('sel')});
    b.classList.add('sel'); $('#f_team').value=b.dataset.team;
  });
  $('#f_team').addEventListener('input',function(){
    [].forEach.call($('#f_teams').children,function(x){x.classList.toggle('sel',x.dataset.team===this.value)},this);
  });
  $('#custForm').addEventListener('submit',function(e){e.preventDefault();onSave(rec);});
  if($('#cancelBtn')) $('#cancelBtn').onclick=closeSheet;
  if($('#delBtn')) $('#delBtn').onclick=function(){ onDelete(editingId); };
  calcOwe();
  openSheet();
}
function calcOwe(){
  var t=+($('#f_total').value||0), d=+($('#f_down').value||0), p=+($('#f_paid').value||0);
  var owe=Math.max(0,t-d-p);
  $('#f_owe').textContent=baht(owe);
}

async function onSave(rec){
  var t=+($('#f_total').value||0), d=+($('#f_down').value||0), p=+($('#f_paid').value||0);
  var c={
    id: editingId || ('c'+Date.now()+Math.floor(Math.random()*900)),
    name:$('#f_name').value.trim()||'(ไม่ระบุชื่อ)',
    phone:$('#f_phone').value.trim(), model:$('#f_model').value.trim(),
    total:t, down:d, paid:p, outstanding:Math.max(0,t-d-p),
    team:$('#f_team').value.trim(), area:$('#f_area').value.trim(),
    lat:rec.lat, lng:rec.lng, ts: editingId? (rec.ts||Date.now()) : Date.now()
  };
  if(tempMarker){ map.removeLayer(tempMarker); tempMarker=null; }
  if(editingId){
    var i=customers.findIndex(function(x){return x.id===editingId});
    if(i>-1){ c.lat=customers[i].lat;c.lng=customers[i].lng; customers[i]=c; }
    refreshMarker(c);
  }else{
    customers.push(c); addMarker(c);
  }
  await saveStore();
  closeSheet(); renderStats(); renderList();
  pushToSheet(c);     // ส่งเข้า Google Sheet (ถ้าตั้งค่าไว้)
}
async function onDelete(id){
  customers=customers.filter(function(x){return x.id!==id});
  if(markers[id]){ map.removeLayer(markers[id]); delete markers[id]; }
  await saveStore(); closeSheet(); renderStats(); renderList();
  toast('ลบแล้ว');
}

/* ============ การ์ดดูข้อมูล ============ */
function openView(id){
  var c=customers.find(function(x){return x.id===id}); if(!c)return;
  var st=statusOf(c);
  var tag= st==='owe' ? '<span class="tag owe"><span class="dot" style="background:var(--owe)"></span>ค้างชำระ</span>'
        : st==='clear' ? '<span class="tag clear"><span class="dot" style="background:var(--clear)"></span>ปิดยอดแล้ว</span>'
        : '';
  $('#sheet').innerHTML=
   '<div class="grab"></div>'+
   '<div style="display:flex;justify-content:space-between;align-items:center;margin:6px 22px 0">'+
     '<h2 style="margin:0">'+esc(c.name)+'</h2>'+tag+'</div>'+
   '<p class="sub">'+(c.area?esc(c.area)+' · ':'')+(c.team?esc(c.team):'ยังไม่ระบุทีม')+'</p>'+
   '<div class="view" style="padding:8px 22px 0">'+
     (c.phone?'<div class="vline"><span>เบอร์โทร</span><a href="tel:'+esc(c.phone)+'" style="color:var(--accent);font-weight:600;text-decoration:none">'+esc(c.phone)+'</a></div>':'')+
     (c.model?'<div class="vline"><span>รุ่น</span><b>'+esc(c.model)+'</b></div>':'')+
     '<div class="vline"><span>ราคาเต็ม</span><b class="num">'+baht(c.total)+'</b></div>'+
     '<div class="vline"><span>ดาวน์</span><b class="num">'+baht(c.down)+'</b></div>'+
     '<div class="vline"><span>จ่ายเพิ่ม</span><b class="num">'+baht(c.paid)+'</b></div>'+
     '<div class="vline"><span>ยอดค้าง</span><b class="num" style="color:'+(c.outstanding>0?'var(--owe)':'var(--clear)')+'">'+baht(c.outstanding)+'</b></div>'+
   '</div>'+
   '<div class="actions" style="padding-left:22px;padding-right:22px">'+
     '<button class="btn ghost" id="vClose">ปิด</button>'+
     '<button class="btn primary" id="vEdit">แก้ไข</button>'+
   '</div>';
  $('#vClose').onclick=closeSheet;
  $('#vEdit').onclick=function(){ editingId=c.id; openForm(c); };
  openSheet();
  map.panTo([c.lat,c.lng]);
}

/* ============ พาเนลรายชื่อ ============ */
function renderFilters(){
  var teams=['ทั้งหมด'].concat(Array.from(new Set(customers.map(function(c){return c.team}).filter(Boolean))));
  $('#lpfilter').innerHTML=teams.map(function(t){return '<button data-f="'+esc(t)+'"'+(t===filterTeam?' class="sel"':'')+'>'+esc(t)+'</button>'}).join('');
}
function renderList(){
  renderFilters();
  var arr=customers.slice().sort(function(a,b){return b.ts-a.ts});
  if(filterTeam!=='ทั้งหมด') arr=arr.filter(function(c){return c.team===filterTeam});
  var box=$('#lplist');
  if(!arr.length){ box.innerHTML='<div class="empty">ยังไม่มีลูกค้าในรายการนี้<br>กดปุ่ม 📍 เพื่อปักหมุดลูกค้าใหม่</div>'; return; }
  box.innerHTML=arr.map(function(c){
    return '<div class="cust" data-id="'+c.id+'">'+
      '<div class="av" style="background:'+colorOf(c)+'">'+esc((c.name||'?').charAt(0))+'</div>'+
      '<div class="info"><div class="nm">'+esc(c.name)+'</div>'+
        '<div class="meta">'+[c.model,c.phone,c.area].filter(Boolean).map(esc).join(' · ')+'</div></div>'+
      '<div class="amt" style="color:'+(c.outstanding>0?'var(--owe)':'var(--clear)')+'">'+baht(c.outstanding)+'</div>'+
    '</div>';
  }).join('');
  [].forEach.call(box.querySelectorAll('.cust'),function(el){
    el.onclick=function(){ var c=customers.find(function(x){return x.id===el.dataset.id});
      if(c){ closeList(); map.flyTo([c.lat,c.lng],14,{duration:.7}); setTimeout(function(){openView(c.id)},650); } };
  });
}
$('#lpfilter').addEventListener?0:0;

function renderStats(){
  var n=customers.length;
  var owe=customers.reduce(function(s,c){return s+(Number(c.outstanding)||0)},0);
  var oweN=customers.filter(function(c){return c.outstanding>0}).length;
  $('#stats').innerHTML=
    '<div class="chip">ลูกค้า <b class="num">'+n+'</b></div>'+
    '<div class="chip"><span class="dot" style="background:var(--owe)"></span>ค้างชำระ <b class="num">'+oweN+'</b></div>'+
    '<div class="chip"><span class="dot" style="background:var(--gold)"></span>ยอดค้างรวม <b class="num">'+baht(owe)+'</b></div>';
}

/* ============ Google Sheet ============ */
var APPS_SCRIPT=
'function doPost(e){\n'+
'  var ss = SpreadsheetApp.getActiveSpreadsheet();\n'+
'  var sh = ss.getSheetByName("ลูกค้า") || ss.getSheets()[0];\n'+
'  if(sh.getLastRow()===0){\n'+
'    sh.appendRow(["เวลา","ชื่อ","เบอร์","รุ่น","ราคาเต็ม","ดาวน์","จ่ายแล้ว","ยอดค้าง","ทีม","พื้นที่","lat","lng","id"]);\n'+
'  }\n'+
'  var d = JSON.parse(e.postData.contents);\n'+
'  var rng = sh.getRange(2,13,Math.max(sh.getLastRow()-1,1),1).getValues();\n'+
'  var row = -1;\n'+
'  for(var i=0;i<rng.length;i++){ if(rng[i][0]==d.id){ row=i+2; break; } }\n'+
'  var vals=[new Date(),d.name,d.phone,d.model,d.total,d.down,d.paid,d.outstanding,d.team,d.area,d.lat,d.lng,d.id];\n'+
'  if(row>0){ sh.getRange(row,1,1,vals.length).setValues([vals]); }\n'+
'  else { sh.appendRow(vals); }\n'+
'  return ContentService.createTextOutput("ok");\n'+
'}';

function openSync(){
  $('#sheet').innerHTML=
   '<div class="grab"></div>'+
   '<h2>เชื่อมต่อ Google Sheet</h2>'+
   '<p class="sub">ทำครั้งเดียว แล้วทุกการบันทึกจะเด้งเข้าชีตอัตโนมัติ</p>'+
   '<form id="syncForm" onsubmit="return false"><div class="sync">'+
     '<ol>'+
       '<li>เปิด Google Sheet ใหม่ → เมนู <b>ส่วนขยาย → Apps Script</b></li>'+
       '<li>ลบโค้ดเดิม วางโค้ดนี้แล้วบันทึก:</li>'+
     '</ol>'+
     '<div class="codebox"><pre id="codePre">'+esc(APPS_SCRIPT)+'</pre><button type="button" class="copybtn" id="copyCode">คัดลอก</button></div>'+
     '<ol start="3">'+
       '<li>กด <b>ทำให้ใช้งานได้ (Deploy) → การทำให้ใช้งานได้ใหม่</b></li>'+
       '<li>ประเภท: <code>เว็บแอป</code> · ผู้ที่เข้าถึง: <code>ทุกคน</code> → Deploy</li>'+
       '<li>คัดลอก <b>URL เว็บแอป</b> มาวางด้านล่าง</li>'+
     '</ol>'+
     '<div class="syncrow"><input id="f_url" placeholder="https://script.google.com/macros/s/…/exec" value="'+esc(cfg.sheetUrl||'')+'"></div>'+
   '</div>'+
   '<div class="actions"><button type="button" class="btn ghost" id="syncClose">ปิด</button>'+
     '<button type="button" class="btn primary" id="syncSave">บันทึกการเชื่อมต่อ</button></div></form>';
  $('#copyCode').onclick=function(){ navigator.clipboard.writeText(APPS_SCRIPT).then(function(){toast('คัดลอกโค้ดแล้ว')}); };
  $('#syncClose').onclick=closeSheet;
  $('#syncSave').onclick=async function(){
    cfg.sheetUrl=$('#f_url').value.trim(); await saveCfg();
    closeSheet(); toast(cfg.sheetUrl?'เชื่อมต่อแล้ว':'ล้างการเชื่อมต่อแล้ว');
  };
  openSheet();
}
function pushToSheet(c){
  if(!cfg.sheetUrl){ toast('บันทึกในเครื่องแล้ว · ยังไม่เชื่อม Sheet'); return; }
  fetch(cfg.sheetUrl,{method:'POST',mode:'no-cors',headers:{'Content-Type':'text/plain;charset=utf-8'},body:JSON.stringify(c)})
    .then(function(){ toast('✓ บันทึก + ส่งเข้า Sheet แล้ว'); })
    .catch(function(){ toast('บันทึกในเครื่องแล้ว · ส่ง Sheet ไม่สำเร็จ',true); });
}

/* ============ sheet ควบคุม ============ */
function openSheet(){ $('#scrim').classList.add('on'); $('#sheet').classList.add('on'); }
function closeSheet(){
  $('#scrim').classList.remove('on'); $('#sheet').classList.remove('on');
  if(tempMarker){ map.removeLayer(tempMarker); tempMarker=null; }
  editingId=null;
}
function openList(){ renderList(); $('#listpanel').classList.add('on'); }
function closeList(){ $('#listpanel').classList.remove('on'); }

var toastTimer=null;
function toast(msg,err){
  var t=$('#toast'); t.textContent=msg; t.classList.toggle('err',!!err); t.classList.add('on');
  clearTimeout(toastTimer); toastTimer=setTimeout(function(){t.classList.remove('on')},2600);
}

/* ============ bind ============ */
function bind(){
  $('#search').addEventListener('input',onSearchInput);
  $('#search').addEventListener('keydown',function(e){ if(e.key==='Enter'){e.preventDefault();onSearchSubmit();} });
  $('#goBtn').onclick=onSearchSubmit;
  $('#addBtn').onclick=function(){ closeList(); toggleAdd(); };
  $('#listBtn').onclick=openList;
  $('#lpClose').onclick=closeList;
  $('#syncBtn').onclick=openSync;
  $('#scrim').onclick=closeSheet;
  $('#lpfilter').addEventListener('click',function(e){
    var b=e.target.closest('button[data-f]'); if(!b)return; filterTeam=b.dataset.f; renderList();
  });
  document.addEventListener('keydown',function(e){ if(e.key==='Escape'){closeSheet();closeList();toggleAdd(false);} });
}

/* ============ start ============ */
(async function(){
  initMap();
  bind();
  await loadStore();
  renderAllMarkers(); renderStats(); renderList();
  if(customers.length){
    var g=L.featureGroup(Object.values(markers));
    try{ map.fitBounds(g.getBounds().pad(.25),{maxZoom:12}); }catch(e){}
  }
  setTimeout(function(){ $('#loader').classList.add('gone'); },300);
})();
})();
</script>
