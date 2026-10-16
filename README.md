# spotify-premium
<!doctype html>
<html lang="es">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<meta name="theme-color" content="#0b0b0d">
<title>Onda · Tu música</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;700&display=swap" rel="stylesheet">
<style>
:root{--bg:#0b0b0d;--sf:#17181c;--s2:#22242a;--tx:#f2f3f5;--mu:#9a9fab;--ac:#2bff88;--on:#04140a;--r:14px}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--tx);font:400 15px/1.4 "DM Sans",system-ui,sans-serif;-webkit-tap-highlight-color:transparent}
button{font:inherit;color:inherit;background:none;border:0;cursor:pointer;padding:0}
button:focus-visible,input:focus-visible{outline:2px solid var(--ac);outline-offset:2px}
main{max-width:760px;margin:0 auto;padding:calc(16px + env(safe-area-inset-top,0px)) 16px 190px;animation:in .25s ease}
@keyframes in{from{opacity:0;transform:translateY(6px)}}
@media (prefers-reduced-motion:reduce){*{animation:none!important;transition:none!important}}
h2{font-size:24px;margin:4px 0 14px}h3{font-size:18px;margin:22px 0 10px}
.logo{display:flex;align-items:center;gap:8px;font-weight:700;font-size:20px;margin-bottom:10px}
.msg{color:var(--mu);text-align:center;padding:28px 8px}
.sub{color:var(--mu);font-size:12px;margin:-6px 0 10px}
ul{list-style:none;margin:0;padding:0}
.row{display:flex;align-items:center;gap:2px;border-radius:12px;padding:5px}
.row.on{background:var(--sf)}.row.on .tt b{color:var(--ac)}
.go{flex:1;min-width:0;display:flex;align-items:center;gap:12px;text-align:left}
.go img,.av{width:48px;height:48px;border-radius:8px;object-fit:cover;background:var(--s2);flex:none}
.av{display:grid;place-items:center;border-radius:50%;font-weight:700}
.tt{min-width:0}.tt b{display:block;font-weight:500;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.tt span{display:block;color:var(--mu);font-size:13px;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.dur{color:var(--mu);font-size:12px;margin:0 4px}
.ib{width:38px;height:38px;color:var(--mu);font-size:18px;border-radius:50%}
.hb.f{color:var(--ac)}
.hs{display:flex;gap:12px;overflow-x:auto;padding-bottom:6px;scrollbar-width:none}
.card{flex:none;width:132px;text-align:left}
.card img,.card .ph{width:132px;height:132px;border-radius:var(--r);object-fit:cover;background:var(--s2);display:grid;place-items:center;font-size:34px}
.card b{display:block;font-weight:500;margin-top:6px;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.card span{color:var(--mu);font-size:12px;display:block;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(132px,1fr));gap:14px}.grid .card,.grid .card img,.grid .card .ph{width:100%}.grid .card img,.grid .card .ph{height:auto;aspect-ratio:1}
.quick{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.quick button{background:var(--sf);border-radius:var(--r);padding:16px 14px;text-align:left;font-weight:500;transition:background .2s}
.quick button:hover{background:var(--s2)}.quick small{display:block;color:var(--mu);font-weight:400}
.sk{height:132px;border-radius:var(--r);background:linear-gradient(90deg,var(--sf),var(--s2),var(--sf));background-size:200% 100%;animation:sh 1.2s linear infinite}
@keyframes sh{to{background-position:-200% 0}}
#q,.in{width:100%;padding:13px 16px;border-radius:99px;border:1px solid var(--s2);background:var(--sf);color:var(--tx);font:inherit}
.in{border-radius:12px}
.chips{display:flex;gap:8px;overflow-x:auto;margin:12px 0;scrollbar-width:none}
.chips button{flex:none;padding:8px 14px;border-radius:99px;background:var(--sf);color:var(--mu)}
.chips button[aria-pressed=true]{background:var(--ac);color:var(--on);font-weight:500}
.btn{background:var(--ac);color:var(--on);font-weight:700;border-radius:99px;padding:11px 20px}
.btn.g{background:var(--s2);color:var(--tx);font-weight:500}
.hd{display:flex;gap:16px;align-items:flex-end;margin-bottom:12px}.hd img,.hd .ph{width:120px;height:120px;border-radius:var(--r);object-fit:cover;background:var(--s2);display:grid;place-items:center;font-size:44px;flex:none}
.hd h2{margin:0}.acts{display:flex;gap:8px;flex-wrap:wrap;margin:10px 0}
.back{color:var(--mu);margin-bottom:8px}
#pl{position:fixed;left:0;right:0;bottom:calc(58px + env(safe-area-inset-bottom,0px));background:var(--sf);border-top:1px solid var(--s2);padding:8px 14px}
#pl[hidden]{display:none}
.pin{max-width:760px;margin:0 auto}
.pr{display:flex;align-items:center;gap:10px}
.pr img{width:44px;height:44px;border-radius:8px;object-fit:cover;background:var(--s2)}
.pr .tt{flex:1;text-align:left}
.pc{display:flex;gap:2px;align-items:center}
.pc .ib.on{color:var(--ac)}
.pp{background:var(--ac);color:var(--on);width:44px;height:44px;font-size:18px}
.sb2{display:flex;align-items:center;gap:8px;font-size:11px;color:var(--mu)}
input[type=range]{flex:1;accent-color:var(--ac);height:20px}
.vol{display:none;width:90px;flex:none}
nav{position:fixed;left:0;right:0;bottom:0;background:#101114;border-top:1px solid var(--s2);display:flex;padding-bottom:env(safe-area-inset-bottom,0px)}
nav button{flex:1;height:58px;color:var(--mu);font-size:12px;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:2px}
nav button span{font-size:20px}nav button[aria-current=true]{color:var(--ac)}
@media (min-width:900px){.vol{display:block}nav{top:0;right:auto;width:96px;flex-direction:column;justify-content:flex-start;padding-top:20px;border-top:0;border-right:1px solid var(--s2)}nav button{flex:none}main,#pl{margin-left:96px}main{max-width:820px}#pl{left:0}}
#sh{position:fixed;inset:0;z-index:9;display:flex;align-items:flex-end;justify-content:center}#sh[hidden]{display:none}
.sb{position:absolute;inset:0;background:#000a}
.sp{position:relative;background:var(--sf);width:100%;max-width:560px;border-radius:20px 20px 0 0;padding:16px 16px calc(16px + env(safe-area-inset-bottom,0px));max-height:80vh;overflow:auto;animation:up .2s ease}
@keyframes up{from{transform:translateY(30px);opacity:0}}
.sp>button{display:block;width:100%;text-align:left;padding:13px 6px;border-bottom:1px solid var(--s2)}
.sp h3{margin:0 0 8px}
#ts{position:fixed;left:50%;transform:translateX(-50%);bottom:calc(150px + env(safe-area-inset-bottom,0px));background:var(--tx);color:var(--bg);padding:10px 16px;border-radius:12px;z-index:10;max-width:90%;font-size:14px}#ts[hidden]{display:none}
.pf{display:flex;gap:16px;align-items:center;margin-bottom:16px}.pf .av{width:84px;height:84px;font-size:32px;object-fit:cover}
</style>
</head>
<body>
<main id="m"></main>
<div id="pl" hidden><div class="pin">
<div class="sb2"><span id="te">0:00</span><input id="sk" type="range" min="0" max="1000" value="0" aria-label="Posición"><span id="td">0:30</span></div>
<div class="pr"><img id="pi" alt=""><button class="tt" id="pq" data-act="queue" aria-label="Abrir cola"><b id="pt"></b><span id="pa"></span></button>
<div class="pc"><button class="ib" id="sh1" data-act="shuf" aria-label="Aleatorio" aria-pressed="false">⇄</button><button class="ib" data-act="prev" aria-label="Anterior">⏮</button><button class="ib pp" id="pp" data-act="pp" aria-label="Reproducir">▶</button><button class="ib" data-act="next" aria-label="Siguiente">⏭</button><button class="ib" id="rp" data-act="rep" aria-label="Repetir" aria-pressed="false">↻</button><input class="vol" id="vo" type="range" min="0" max="100" value="80" aria-label="Volumen"></div></div>
</div></div>
<nav id="nv"><button data-act="tab" data-v="home"><span>⌂</span>Inicio</button><button data-act="tab" data-v="search"><span>⌕</span>Buscar</button><button data-act="tab" data-v="lib"><span>▤</span>Biblioteca</button><button data-act="tab" data-v="prof"><span>☺</span>Perfil</button></nav>
<div id="sh" hidden></div><div id="ts" hidden role="status"></div>
<script>
const $=s=>document.querySelector(s),API='https://itunes.apple.com/';
const esc=s=>String(s??'').replace(/[&<>"']/g,c=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c]));
const fmt=s=>Math.floor(s/60)+':'+String(Math.floor(s%60)).padStart(2,'0');
let S={fav:[],pls:[],albums:[],arts:[],rec:[],user:{name:'Tú',photo:''}};
try{Object.assign(S,JSON.parse(localStorage.getItem('onda3')||'{}'))}catch(e){}
const save=()=>{try{localStorage.setItem('onda3',JSON.stringify(S))}catch(e){toast('No se ha podido guardar: almacenamiento lleno.')}};
const T=new Map(),reg=t=>(T.set(String(t.id),t),t);
[...S.fav,...S.rec,...S.pls.flatMap(p=>p.tracks)].forEach(reg);
let tm;function toast(m){const t=$('#ts');t.textContent=m;t.hidden=false;clearTimeout(tm);tm=setTimeout(()=>t.hidden=true,2400)}
function jsonp(p){return new Promise((ok,ko)=>{const cb='cb'+Math.random().toString(36).slice(2),s=document.createElement('script'),x=setTimeout(()=>{s.remove();ko()},9000);window[cb]=d=>{clearTimeout(x);delete window[cb];s.remove();ok(d)};s.src=API+p+'&callback='+cb;s.onerror=()=>{clearTimeout(x);s.remove();ko()};document.head.appendChild(s)})}
const api=async p=>{try{const r=await fetch(API+p);if(!r.ok)throw 0;return await r.json()}catch(e){return jsonp(p)}};
const nt=r=>reg({id:r.trackId,t:r.trackName,a:r.artistName,aid:r.artistId,al:r.collectionName,alid:r.collectionId,img:(r.artworkUrl100||'').replace('100x100','400x400'),u:r.previewUrl,d:r.trackTimeMillis,url:r.trackViewUrl});
const songs=d=>d.results.filter(r=>r.wrapperType==='track'&&r.kind==='song'&&r.previewUrl).map(nt);
const isFav=id=>S.fav.some(f=>String(f.id)===String(id));
const heart=t=>`<button class="ib hb${isFav(t.id)?' f':''}" data-act="fav" data-t="${t.id}" aria-label="Favorita" aria-pressed="${isFav(t.id)}">${isFav(t.id)?'♥':'♡'}</button>`;
let L={};
const row=(t,k,o={})=>`<li class="row${Q[qi]&&Q[qi].id===t.id?' on':''}"><button class="go" data-act="play" data-l="${k}" data-t="${t.id}"><img src="${esc(t.img)}" alt="" loading="lazy"><span class="tt"><b>${esc(t.t)}</b><span>${esc(t.a)}${t.al?' · '+esc(t.al):''}</span></span></button>${o.mv?`<button class="ib" data-act="mv" data-t="${t.id}" data-d="-1" aria-label="Subir">▲</button><button class="ib" data-act="mv" data-t="${t.id}" data-d="1" aria-label="Bajar">▼</button>`:''}<span class="dur">${t.d?fmt(t.d/1000):''}</span>${heart(t)}<button class="ib" data-act="menu" data-t="${t.id}" aria-label="Más opciones">⋯</button></li>`;
const list=(a,k,o)=>{L[k]=a;return a.length?`<ul>${a.map(t=>row(t,k,o)).join('')}</ul>`:'<p class="msg">No hay canciones.</p>'};
const card=(img,t,s,act,attrs,ph='♪')=>`<button class="card" data-act="${act}" ${attrs}>${img?`<img src="${esc(img)}" alt="" loading="lazy">`:`<div class="ph">${ph}</div>`}<b>${esc(t)}</b><span>${esc(s||'')}</span></button>`;
const sk=n=>`<div class="hs">${Array(n).fill('<div class="card"><div class="sk" style="width:132px"></div></div>').join('')}</div>`;
const err='<p class="msg">No se ha podido conectar con el catálogo. Comprueba tu conexión e inténtalo de nuevo.</p>';
/* ===== reproductor ===== */
const au=new Audio();let Q=[],qi=-1,shuf=false,rep=0,errs=0;
function play(l,i){Q=l.slice();qi=i;load()}
function load(){const t=Q[qi];if(!t)return;au.src=t.u;au.play().catch(()=>{});S.rec=[t,...S.rec.filter(x=>x.id!==t.id)].slice(0,30);save();ui();ms(t);hl()}
function next(auto){if(!Q.length)return;if(auto&&rep===2){au.currentTime=0;au.play();return}
let n=qi+1;if(shuf&&Q.length>1){do{n=Math.floor(Math.random()*Q.length)}while(n===qi)}
if(n>=Q.length){if(rep===1||!auto)n=0;else{au.pause();return}}qi=n;load()}
function prev(){if(au.currentTime>3||Q.length<2){au.currentTime=0;return}qi=(qi-1+Q.length)%Q.length;load()}
const toggle=()=>{if(qi<0)return;au.paused?au.play():au.pause()};
au.onended=()=>next(true);au.onplay=au.onpause=()=>{ui();if('mediaSession'in navigator)navigator.mediaSession.playbackState=au.paused?'paused':'playing'};
au.onplaying=()=>errs=0;
au.onerror=()=>{if(qi<0)return;toast('Esta canción no está disponible.');if(++errs<3&&Q.length>1)next(false);else au.pause()};
au.ontimeupdate=()=>{const d=au.duration||30;$('#te').textContent=fmt(au.currentTime);$('#td').textContent=fmt(d);$('#sk').value=au.currentTime/d*1000};
$('#sk').oninput=e=>{if(au.duration)au.currentTime=e.target.value/1000*au.duration};
$('#vo').oninput=e=>au.volume=e.target.value/100;
function ui(){const t=Q[qi];$('#pl').hidden=!t;if(!t)return;$('#pi').src=t.img;$('#pt').textContent=t.t;$('#pa').textContent=t.a;
$('#pp').textContent=au.paused?'▶':'⏸';$('#pp').setAttribute('aria-label',au.paused?'Reproducir':'Pausar');
$('#sh1').setAttribute('aria-pressed',shuf);$('#sh1').classList.toggle('on',shuf);$('#rp').setAttribute('aria-pressed',rep>0);$('#rp').classList.toggle('on',rep>0);$('#rp').textContent=rep===2?'↺':'↻'}
function hl(){document.querySelectorAll('.row').forEach(r=>{const b=r.querySelector('.go');r.classList.toggle('on',!!Q[qi]&&b.dataset.t==Q[qi].id)})}
function ms(t){if(!('mediaSession'in navigator))return;navigator.mediaSession.metadata=new MediaMetadata({title:t.t,artist:t.a,album:t.al||'',artwork:[{src:t.img,sizes:'400x400'}]});
[['play',()=>au.play()],['pause',()=>au.pause()],['nexttrack',()=>next(false)],['previoustrack',prev]].forEach(([a,f])=>{try{navigator.mediaSession.setActionHandler(a,f)}catch(e){}})}
/* ===== navegación ===== */
let V={n:'home'},H=[],TAB='home',LT='fav',SQ={q:'',f:'song'},sid=0;
function go(n,a,push=true){if(push)H.push(V);V={n,a};if(['home','search','lib','prof'].includes(n))TAB=n;draw()}
function draw(){const m=$('#m'),tk=V;L={};window.scrollTo(0,0);
document.querySelectorAll('#nv button').forEach(b=>b.toggleAttribute('aria-current',b.dataset.v===TAB));
({home:vHome,search:vSearch,lib:vLib,prof:vProf,art:vArt,alb:vAlb,pl:vPl}[V.n])(m,tk)}
const bk='<button class="back" data-act="back">← Volver</button>';
function vHome(m,tk){const G=[['Pop','pop'],['Rock','rock'],['Reggaeton','reggaeton']];
m.innerHTML=`<div class="logo"><svg width="28" height="28" viewBox="0 0 28 28" fill="none" stroke="#2bff88" stroke-width="2.5" stroke-linecap="round"><path d="M3 14h2M8 9v10M13 4v20M18 9v10M23 12v4"/></svg>Onda</div><h2>Hola, ${esc(S.user.name)}</h2>
<div class="quick"><button data-act="lib" data-s="fav">♥ Favoritos<small>${S.fav.length} canciones</small></button><button data-act="lib" data-s="rec">↺ Recientes<small>${S.rec.length} canciones</small></button></div>
${S.rec.length?`<h3>Seguir escuchando</h3><div class="hs">${(L.r=S.rec.slice(0,10)).map(t=>card(t.img,t.t,t.a,'play',`data-l="r" data-t="${t.id}"`)).join('')}</div>`:''}
${S.pls.length?`<h3>Tus playlists</h3><div class="hs">${S.pls.map(p=>card(p.cover,p.name,p.tracks.length+' canciones','opl',`data-p="${p.id}"`,'♫')).join('')}</div>`:''}
${G.map((g,i)=>`<h3>Explorar: ${g[0]}</h3><div id="g${i}">${sk(4)}</div>`).join('')}<p class="sub">Las secciones “Explorar” son búsquedas por género en el catálogo de iTunes, no listas de éxitos. Vista previa de 30 s por canción.</p>`;
G.forEach(async(g,i)=>{try{const d=await api(`search?term=${encodeURIComponent(g[1])}&media=music&entity=song&limit=14&country=ES`);if(V!==tk)return;const s=songs(d);L['g'+i]=s;$('#g'+i).innerHTML=`<div class="hs">${s.map(t=>card(t.img,t.t,t.a,'play',`data-l="g${i}" data-t="${t.id}"`)).join('')}</div>`}catch(e){if(V===tk)$('#g'+i).innerHTML=err}})}
function vSearch(m){m.innerHTML=`<h2>Buscar</h2><input id="q" type="search" placeholder="Canciones, artistas o álbumes" aria-label="Buscar" autocomplete="off" value="${esc(SQ.q)}"><div id="su" class="chips"></div><div class="chips">${[['song','Canciones'],['art','Artistas'],['alb','Álbumes'],['pl','Playlists']].map(c=>`<button data-act="flt" data-f="${c[0]}" aria-pressed="${SQ.f===c[0]}">${c[1]}</button>`).join('')}</div><div id="res"></div>`;
let t;$('#q').oninput=e=>{SQ.q=e.target.value;clearTimeout(t);t=setTimeout(doSearch,300)};$('#q').onkeydown=e=>{if(e.key==='Enter'){clearTimeout(t);doSearch()}};doSearch()}
async function doSearch(){const q=SQ.q.trim(),r=$('#res');if(!r)return;$('#su').innerHTML='';
if(q.length<2){r.innerHTML='<p class="msg">Escribe al menos dos letras para buscar.</p>';return}
if(SQ.f==='pl'){const p=S.pls.filter(x=>x.name.toLowerCase().includes(q.toLowerCase()));r.innerHTML=p.length?`<div class="grid">${p.map(x=>card(x.cover,x.name,x.tracks.length+' canciones','opl',`data-p="${x.id}"`,'♫')).join('')}</div>`:'<p class="msg">Ninguna de tus playlists coincide. Aquí solo se buscan las que creas tú.</p>';return}
r.innerHTML=sk(4);const my=++sid;
try{const e={song:'song',art:'musicArtist',alb:'album'}[SQ.f],d=await api(`search?term=${encodeURIComponent(q)}&media=music&entity=${e}&limit=40&country=ES`);if(my!==sid)return;
if(SQ.f==='song'){const s=songs(d);if(!s.length){r.innerHTML=`<p class="msg">Sin resultados para “${esc(q)}”.</p>`;return}
$('#su').innerHTML=[...new Set(s.map(t=>t.a))].slice(0,4).map(a=>`<button data-act="sug" data-q="${esc(a)}" class="btn g">${esc(a)}</button>`).join('');r.innerHTML=list(s,'s')}
else if(SQ.f==='art'){const a=d.results.filter(x=>x.artistId);r.innerHTML=a.length?`<ul>${a.map(x=>`<li class="row"><button class="go" data-act="art" data-id="${x.artistId}" data-n="${esc(x.artistName)}"><span class="av">${esc(x.artistName[0])}</span><span class="tt"><b>${esc(x.artistName)}</b><span>${esc(x.primaryGenreName||'Artista')}</span></span></button></li>`).join('')}</ul>`:`<p class="msg">Sin resultados para “${esc(q)}”.</p>`}
else{const a=d.results.filter(x=>x.collectionId);r.innerHTML=a.length?`<div class="grid">${a.map(x=>card(x.artworkUrl100.replace('100x100','400x400'),x.collectionName,x.artistName,'alb',`data-id="${x.collectionId}"`)).join('')}</div>`:`<p class="msg">Sin resultados para “${esc(q)}”.</p>`}}
catch(e){if(my===sid)r.innerHTML=err}}
function vLib(m){const tabs=[['fav','Favoritos'],['pl','Playlists'],['alb','Álbumes'],['art','Artistas'],['rec','Recientes']];let h=`<h2>Tu biblioteca</h2><div class="chips">${tabs.map(t=>`<button data-act="lt" data-s="${t[0]}" aria-pressed="${LT===t[0]}">${t[1]}</button>`).join('')}</div>`;
if(LT==='fav')h+=S.fav.length?`<div class="acts"><button class="btn" data-act="playall" data-l="f">▶ Reproducir</button></div>${list(S.fav,'f')}`:'<p class="msg">Aún no tienes favoritos. Toca ♡ en cualquier canción.</p>';
if(LT==='rec')h+=S.rec.length?list(S.rec,'rc'):'<p class="msg">Todavía no has reproducido nada.</p>';
if(LT==='pl')h+=`<div class="acts"><button class="btn" data-act="plnew" data-t="">＋ Nueva playlist</button></div>`+(S.pls.length?`<div class="grid">${S.pls.map(p=>card(p.cover,p.name,p.tracks.length+' canciones','opl',`data-p="${p.id}"`,'♫')).join('')}</div>`:'<p class="msg">Crea tu primera playlist.</p>');
if(LT==='alb')h+=S.albums.length?`<div class="grid">${S.albums.map(a=>card(a.img,a.name,a.artist,'alb',`data-id="${a.id}"`)).join('')}</div>`:'<p class="msg">Guarda álbumes con ♡ desde su página.</p>';
if(LT==='art')h+=S.arts.length?`<ul>${S.arts.map(a=>`<li class="row"><button class="go" data-act="art" data-id="${a.id}" data-n="${esc(a.name)}"><span class="av">${esc(a.name[0])}</span><span class="tt"><b>${esc(a.name)}</b></span></button></li>`).join('')}</ul>`:'<p class="msg">Guarda artistas con ♡ desde su página.</p>';
m.innerHTML=h}
function vProf(m){m.innerHTML=`<h2>Perfil</h2><div class="pf">${S.user.photo?`<img class="av" src="${S.user.photo}" alt="Tu foto">`:`<div class="av">${esc(S.user.name[0]||'T')}</div>`}<label class="btn g" style="cursor:pointer">Cambiar foto<input type="file" accept="image/*" id="ph" hidden></label></div>
<label for="nm" class="sub">Nombre</label><input class="in" id="nm" maxlength="30" value="${esc(S.user.name)}"><div class="acts"><button class="btn" data-act="sname">Guardar nombre</button></div>
<h3>Tu música</h3><p>${S.fav.length} favoritas · ${S.pls.length} playlists · ${S.albums.length} álbumes · ${S.arts.length} artistas</p>
<p class="sub">Tu biblioteca se guarda en este navegador. Las cuentas con sincronización entre dispositivos necesitan un servidor (por ejemplo Supabase) y aún no están conectadas.</p><div class="acts"><button class="btn g" data-act="wipe">Borrar mis datos</button></div>`;
$('#ph').onchange=e=>{const f=e.target.files[0];if(!f)return;const i=new Image();i.onload=()=>{const c=document.createElement('canvas');c.width=c.height=160;const x=c.getContext('2d'),s=Math.min(i.width,i.height);x.drawImage(i,(i.width-s)/2,(i.height-s)/2,s,s,0,0,160,160);S.user.photo=c.toDataURL('image/jpeg',.8);save();vProf(m)};i.onerror=()=>toast('No se puede leer esa imagen.');i.src=URL.createObjectURL(f)}}
async function vArt(m,tk){const a=V.a;m.innerHTML=`${bk}<div class="hd"><div class="ph">${esc(a.n[0])}</div><div><h2>${esc(a.n)}</h2><button class="btn g" data-act="favart" data-id="${a.id}" data-n="${esc(a.n)}">${S.arts.some(x=>x.id==a.id)?'♥ Guardado':'♡ Guardar artista'}</button></div></div><div id="ab">${sk(4)}</div>`;
try{const[d,e]=await Promise.all([api(`lookup?id=${a.id}&entity=song&limit=40&country=ES`),api(`lookup?id=${a.id}&entity=album&limit=12&country=ES`)]);if(V!==tk)return;const s=songs(d),al=e.results.filter(x=>x.collectionId);
$('#ab').innerHTML=`${s.length?`<div class="acts"><button class="btn" data-act="playall" data-l="a">▶ Reproducir</button></div>${list(s,'a')}`:'<p class="msg">No hay canciones con vista previa para este artista.</p>'}${al.length?`<h3>Álbumes</h3><div class="hs">${al.map(x=>card(x.artworkUrl100.replace('100x100','400x400'),x.collectionName,x.releaseDate?.slice(0,4),'alb',`data-id="${x.collectionId}"`)).join('')}</div>`:''}`}catch(x){if(V===tk)$('#ab').innerHTML=err}}
async function vAlb(m,tk){m.innerHTML=bk+'<div id="ab">'+sk(4)+'</div>';
try{const d=await api(`lookup?id=${V.a}&entity=song&limit=60&country=ES`);if(V!==tk)return;const c=d.results[0],s=songs(d);if(!c){$('#ab').innerHTML='<p class="msg">Álbum no encontrado.</p>';return}
const img=c.artworkUrl100.replace('100x100','400x400');V.al={id:c.collectionId,name:c.collectionName,artist:c.artistName,img};
$('#ab').innerHTML=`<div class="hd"><img src="${esc(img)}" alt=""><div><h2>${esc(c.collectionName)}</h2><p class="sub">${esc(c.artistName)}</p><button class="btn g" data-act="favalb">${S.albums.some(x=>x.id==c.collectionId)?'♥ Guardado':'♡ Guardar álbum'}</button></div></div>${s.length?`<div class="acts"><button class="btn" data-act="playall" data-l="b">▶ Reproducir</button></div>${list(s,'b')}`:'<p class="msg">Este álbum no tiene vistas previas.</p>'}`}catch(e){if(V===tk)$('#ab').innerHTML=err}}
function vPl(m){const p=S.pls.find(x=>x.id===V.a);if(!p){go('lib',0,false);return}
m.innerHTML=`${bk}<div class="hd">${p.cover?`<img src="${esc(p.cover)}" alt="">`:'<div class="ph">♫</div>'}<div><h2>${esc(p.name)}</h2><p class="sub">${p.tracks.length} canciones</p></div></div>
<div class="acts"><button class="btn" data-act="playall" data-l="p">▶ Reproducir</button><button class="btn g" data-act="plren">Renombrar</button><button class="btn g" data-act="plcov">Portada</button><button class="btn g" data-act="plsh">Compartir</button><button class="btn g" data-act="pldel">Eliminar</button></div>${p.tracks.length?list(p.tracks,'p',{mv:1}):'<p class="msg">Playlist vacía. Usa ⋯ en cualquier canción para añadirla.</p>'}`}
/* ===== hojas y acciones ===== */
function sheet(h){const s=$('#sh');s.innerHTML=`<div class="sb" data-act="close"></div><div class="sp" role="dialog">${h}</div>`;s.hidden=false}
const close=()=>$('#sh').hidden=true;
const cur=()=>S.pls.find(x=>x.id===V.a);
function menu(t){sheet(`<h3>${esc(t.t)}</h3><button data-act="fav" data-t="${t.id}">${isFav(t.id)?'Quitar de favoritos':'Añadir a favoritos'}</button><button data-act="addpl" data-t="${t.id}">Añadir a una playlist</button><button data-act="enq" data-t="${t.id}">Añadir a la cola</button>${t.aid?`<button data-act="art" data-id="${t.aid}" data-n="${esc(t.a)}">Ir al artista</button>`:''}${t.alid?`<button data-act="alb" data-id="${t.alid}">Ir al álbum</button>`:''}<button data-act="shr" data-t="${t.id}">Compartir</button>${V.n==='pl'?`<button data-act="rmpl" data-t="${t.id}">Quitar de esta playlist</button>`:''}`)}
function nameSheet(title,act,val,t=''){sheet(`<h3>${title}</h3><input class="in" id="pn" maxlength="40" placeholder="Nombre" value="${esc(val)}" aria-label="Nombre de la playlist"><div class="acts"><button class="btn" data-act="${act}" data-t="${t}">Guardar</button></div>`);setTimeout(()=>$('#pn')?.focus(),50)}
async function share(txt,url){try{if(navigator.share){await navigator.share({title:txt,url:url||undefined,text:url?undefined:txt});return}await navigator.clipboard.writeText(url?txt+' '+url:txt);toast('Enlace copiado')}catch(e){}}
function addTo(p,t){if(p.tracks.some(x=>x.id==t.id)){toast('Ya está en la playlist.');return}p.tracks.push(t);if(!p.cover)p.cover=t.img;save();toast('Añadida a «'+p.name+'»')}
document.addEventListener('keydown',e=>{if(e.key==='Escape')close()});
document.addEventListener('click',e=>{const b=e.target.closest('[data-act]');if(!b)return;const d=b.dataset,t=d.t?T.get(d.t):null;
switch(d.act){
case 'tab':H=[];go(d.v,0,false);break;
case 'back':V=H.pop()||{n:'home'};if(['home','search','lib','prof'].includes(V.n))TAB=V.n;draw();break;
case 'lib':LT=d.s;go('lib',0);break;
case 'lt':LT=d.s;draw();break;
case 'flt':SQ.f=d.f;draw();break;
case 'sug':SQ.q=d.q;$('#q').value=d.q;doSearch();break;
case 'play':{const l=L[d.l]||[],i=l.findIndex(x=>x.id==d.t);if(i>=0)play(l,i);break}
case 'playall':{const l=L[d.l]||[];if(l.length)play(l,0);break}
case 'pp':toggle();break;case 'next':next(false);break;case 'prev':prev();break;
case 'shuf':shuf=!shuf;ui();break;case 'rep':rep=(rep+1)%3;ui();break;
case 'fav':{if(!t)break;const k=S.fav.findIndex(x=>x.id==t.id);k>=0?S.fav.splice(k,1):S.fav.unshift(t);save();document.querySelectorAll(`[data-act=fav][data-t="${t.id}"]`).forEach(h=>{if(h.classList.contains('hb')){h.classList.toggle('f',isFav(t.id));h.textContent=isFav(t.id)?'♥':'♡'}});if(!$('#sh').hidden)close();toast(isFav(t.id)?'Añadida a favoritos':'Quitada de favoritos');if(V.n==='lib'&&LT==='fav')draw();break}
case 'menu':menu(t);break;
case 'close':close();break;
case 'enq':Q.push(t);if(qi<0){qi=0;load()}close();toast('Añadida a la cola');break;
case 'shr':close();share(t.t+' – '+t.a,t.url);break;
case 'art':close();go('art',{id:d.id,n:d.n});break;
case 'alb':close();go('alb',d.id);break;
case 'favart':{const k=S.arts.findIndex(x=>x.id==d.id);k>=0?S.arts.splice(k,1):S.arts.push({id:d.id,name:d.n});save();b.textContent=k>=0?'♡ Guardar artista':'♥ Guardado';break}
case 'favalb':{const a=V.al;if(!a)break;const k=S.albums.findIndex(x=>x.id==a.id);k>=0?S.albums.splice(k,1):S.albums.push(a);save();b.textContent=k>=0?'♡ Guardar álbum':'♥ Guardado';break}
case 'addpl':sheet(`<h3>Añadir a una playlist</h3>${S.pls.map(p=>`<button data-act="pladd" data-p="${p.id}" data-t="${t.id}">${esc(p.name)} <small>(${p.tracks.length})</small></button>`).join('')}<button data-act="plnew" data-t="${t.id}">＋ Nueva playlist</button>`);break;
case 'pladd':{const p=S.pls.find(x=>x.id===d.p);if(p&&t)addTo(p,t);close();break}
case 'plnew':nameSheet('Nueva playlist','plmk','',d.t);break;
case 'plmk':{const n=$('#pn').value.trim();if(!n){toast('Escribe un nombre.');break}const p={id:'p'+Date.now(),name:n,cover:'',tracks:[]};S.pls.push(p);if(t)addTo(p,t);save();close();if(V.n==='lib')draw();else if(!t)toast('Playlist creada');break}
case 'opl':go('pl',d.p);break;
case 'plren':nameSheet('Renombrar playlist','plrn',cur().name);break;
case 'plrn':{const n=$('#pn').value.trim(),p=cur();if(n&&p){p.name=n;save();close();draw()}break}
case 'plcov':{const p=cur();if(!p||!p.tracks.length){toast('Añade canciones para elegir portada.');break}const i=p.tracks.findIndex(x=>x.img===p.cover);p.cover=p.tracks[(i+1)%p.tracks.length].img;save();draw();break}
case 'plsh':{const p=cur();share(p.name+' — '+p.tracks.map(x=>x.t+' ('+x.a+')').join(', '));break}
case 'pldel':if(confirm('¿Eliminar esta playlist?')){S.pls=S.pls.filter(x=>x.id!==V.a);save();V=H.pop()||{n:'lib'};draw()}break;
case 'rmpl':{const p=cur();p.tracks=p.tracks.filter(x=>x.id!=t.id);save();close();draw();break}
case 'mv':{const p=cur(),i=p.tracks.findIndex(x=>x.id==t.id),j=i+ +d.d;if(j<0||j>=p.tracks.length)break;[p.tracks[i],p.tracks[j]]=[p.tracks[j],p.tracks[i]];save();const y=scrollY;draw();scrollTo(0,y);break}
case 'queue':sheet(`<h3>Cola de reproducción</h3>${Q.map((x,i)=>`<button data-act="jump" data-i="${i}" style="${i===qi?'color:var(--ac)':''}">${esc(x.t)} <small>· ${esc(x.a)}</small></button>`).join('')}`);break;
case 'jump':qi=+d.i;load();close();break;
case 'sname':S.user.name=$('#nm').value.trim()||'Tú';save();toast('Nombre guardado');break;
case 'wipe':if(confirm('Se borrarán favoritos, playlists y perfil de este navegador. ¿Continuar?')){S={fav:[],pls:[],albums:[],arts:[],rec:[],user:{name:'Tú',photo:''}};save();draw()}break}});
draw();
</script>
</body>
</html>
