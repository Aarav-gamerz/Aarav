bash

cat > /mnt/user-data/outputs/BattleZone3D.html << 'EOF'
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Battle Zone 3D</title>
<style>
*{margin:0;padding:0;box-sizing:border-box;user-select:none}
body{background:#000;overflow:hidden;font-family:monospace}
#wrap{position:relative;width:100vw;height:100vh;overflow:hidden}
#c{position:absolute;top:0;left:0;width:100%;height:100%;cursor:crosshair}
#hud{position:absolute;top:0;left:0;width:100%;height:100%;pointer-events:none;z-index:2}
#hp-wrap{position:absolute;top:10px;left:12px}
#hp-label{color:#fff;font-size:11px;letter-spacing:1px;margin-bottom:3px;text-shadow:0 1px 3px #000}
#hp-track{width:140px;height:10px;background:rgba(0,0,0,0.55);border:1px solid rgba(255,255,255,0.3);border-radius:3px;overflow:hidden}
#hp-fill{height:100%;width:100%;background:#44ee66;border-radius:2px}
#hp-num{color:#fff;font-size:12px;margin-top:3px;text-shadow:0 1px 3px #000}
#shield-wrap{position:absolute;top:46px;left:12px}
#shield-track{width:110px;height:7px;background:rgba(0,0,0,0.5);border:1px solid rgba(100,200,255,0.3);border-radius:2px;overflow:hidden}
#shield-fill{height:100%;width:60%;background:#55aaff}
#shield-num{color:#88ccff;font-size:10px;margin-top:2px;text-shadow:0 1px 3px #000}
#ammo-wrap{position:absolute;bottom:140px;right:12px;text-align:right}
#gun-name{color:#ffd700;font-size:13px;letter-spacing:2px;text-shadow:0 1px 4px #000;margin-bottom:2px}
#ammo-num{color:#fff;font-size:24px;font-weight:700;text-shadow:0 1px 4px #000}
#ammo-res{color:#aaa;font-size:12px}
#kills-wrap{position:absolute;top:10px;right:12px;color:#ffd700;font-size:13px;text-shadow:0 1px 4px #000}
#pname-hud{position:absolute;top:30px;right:12px;color:#fff;font-size:11px;text-shadow:0 1px 3px #000}
#crosshair{position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);width:20px;height:20px}
#crosshair::before,#crosshair::after{content:'';position:absolute;background:rgba(255,255,255,0.9)}
#crosshair::before{width:2px;height:20px;left:9px;top:0}
#crosshair::after{width:20px;height:2px;top:9px;left:0}
#msg{position:absolute;top:38%;left:50%;transform:translateX(-50%);color:#ffd700;font-size:15px;font-weight:700;text-shadow:0 2px 6px #000;letter-spacing:2px;text-align:center;min-height:22px}
#look-hint{position:absolute;top:52%;left:50%;transform:translate(-50%,20px);color:rgba(255,255,255,0.65);font-size:12px;background:rgba(0,0,0,0.45);padding:4px 12px;border-radius:4px}
#joystick-zone{position:absolute;bottom:20px;left:20px;width:120px;height:120px;background:rgba(255,255,255,0.07);border:2px solid rgba(255,255,255,0.2);border-radius:50%;pointer-events:all;touch-action:none;z-index:3}
#joystick-knob{position:absolute;width:44px;height:44px;background:rgba(255,255,255,0.3);border:2px solid rgba(255,255,255,0.6);border-radius:50%;top:38px;left:38px}
#look-zone{position:absolute;top:0;right:0;width:55%;height:75%;pointer-events:all;touch-action:none;z-index:3}
#fire-btn{position:absolute;bottom:30px;right:140px;width:70px;height:70px;background:rgba(220,50,50,0.88);border:2px solid rgba(255,100,100,0.9);border-radius:50%;pointer-events:all;touch-action:none;display:flex;align-items:center;justify-content:center;color:#fff;font-size:13px;font-weight:700;cursor:pointer;z-index:3}
#jump-btn{position:absolute;bottom:108px;right:72px;width:50px;height:50px;background:rgba(80,180,255,0.85);border:2px solid rgba(120,200,255,0.9);border-radius:50%;pointer-events:all;touch-action:none;display:flex;align-items:center;justify-content:center;color:#fff;font-size:11px;font-weight:700;cursor:pointer;z-index:3}
#sprint-btn{position:absolute;bottom:108px;right:130px;width:50px;height:50px;background:rgba(255,180,40,0.85);border:2px solid rgba(255,210,80,0.9);border-radius:50%;pointer-events:all;touch-action:none;display:flex;align-items:center;justify-content:center;color:#fff;font-size:11px;font-weight:700;cursor:pointer;transition:background 0.15s;z-index:3}
#sprint-btn.on{background:rgba(255,100,0,0.95);border-color:#ff8800}
#sit-btn{position:absolute;bottom:166px;right:72px;width:44px;height:44px;background:rgba(120,80,200,0.85);border:2px solid rgba(160,120,255,0.9);border-radius:50%;pointer-events:all;touch-action:none;display:flex;align-items:center;justify-content:center;color:#fff;font-size:10px;font-weight:700;cursor:pointer;transition:background 0.15s;z-index:3}
#sit-btn.on{background:rgba(80,0,180,0.95)}
#gloo-btn{position:absolute;bottom:166px;right:124px;width:44px;height:44px;background:rgba(0,200,150,0.85);border:2px solid rgba(0,255,180,0.9);border-radius:50%;pointer-events:all;touch-action:none;display:flex;align-items:center;justify-content:center;color:#fff;font-size:9px;font-weight:700;text-align:center;line-height:1.2;cursor:pointer;z-index:3}
#emote-btn{position:absolute;bottom:166px;right:22px;width:44px;height:44px;background:rgba(255,100,180,0.8);border:2px solid rgba(255,150,200,0.9);border-radius:50%;pointer-events:all;touch-action:none;display:flex;align-items:center;justify-content:center;font-size:18px;cursor:pointer;z-index:3}
#weapon-bar{position:absolute;bottom:12px;left:50%;transform:translateX(-50%);display:flex;gap:5px;pointer-events:all;z-index:3}
.wslot{background:rgba(0,0,0,0.65);border:1px solid rgba(255,255,255,0.2);border-radius:5px;padding:4px 8px;color:#aaa;font-size:9px;cursor:pointer;text-align:center;min-width:46px}
.wslot.active{border-color:#ffd700;color:#ffd700}
#sprint-ind{position:absolute;top:68px;left:12px;color:#ffaa00;font-size:11px;font-weight:700;display:none;text-shadow:0 1px 3px #000}
#sit-ind{position:absolute;top:84px;left:12px;color:#bb88ff;font-size:11px;font-weight:700;display:none;text-shadow:0 1px 3px #000}
#emote-popup{position:absolute;bottom:220px;right:22px;background:rgba(0,0,0,0.92);border:1px solid rgba(255,150,200,0.45);border-radius:8px;padding:9px;display:none;pointer-events:all;z-index:10}
.ep-title{color:#ff88cc;font-size:10px;margin-bottom:6px;letter-spacing:1px}
.ep-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:5px}
.ep-item{font-size:22px;cursor:pointer;text-align:center;padding:4px;border-radius:4px;background:rgba(255,255,255,0.06)}
#emote-disp{position:absolute;top:18%;left:50%;transform:translateX(-50%);font-size:50px}
#pet-disp{position:absolute;bottom:185px;left:155px;font-size:24px}
#lobby{position:absolute;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,0.97);display:flex;flex-direction:column;align-items:center;overflow-y:auto;pointer-events:all;z-index:5;padding:14px 12px 30px}
#lobby h1{color:#ffd700;font-size:22px;letter-spacing:3px;margin-bottom:4px;flex-shrink:0}
.lsub{color:#aaa;font-size:10px;margin-bottom:9px;letter-spacing:1px;flex-shrink:0}
.lsec{width:100%;max-width:680px;margin-bottom:9px;flex-shrink:0}
.lsec h3{color:#ffd700;font-size:11px;letter-spacing:2px;margin-bottom:5px;border-bottom:1px solid rgba(255,215,0,0.2);padding-bottom:3px}
.bgrid{display:grid;grid-template-columns:repeat(4,1fr);gap:6px}
.bcard{background:rgba(255,255,255,0.05);border:1px solid rgba(255,255,255,0.12);border-radius:6px;padding:8px 4px;text-align:center;cursor:pointer}
.bcard.owned{border-color:#ffd700}.bcard.equipped{border-color:#00ffaa;background:rgba(0,255,170,0.08)}
.ggrid{display:grid;grid-template-columns:repeat(3,1fr);gap:6px}
.gcard{background:rgba(255,255,255,0.05);border:1px solid rgba(255,255,255,0.1);border-radius:6px;padding:6px 4px;text-align:center;cursor:pointer}
.gcard.equipped{border-color:#00ffaa}
.pgrid{display:grid;grid-template-columns:repeat(4,1fr);gap:6px}
.pcard{background:rgba(255,255,255,0.05);border:1px solid rgba(255,255,255,0.1);border-radius:6px;padding:6px 4px;text-align:center;cursor:pointer}
.pcard.equipped{border-color:#ff88cc}
.egrid{display:grid;grid-template-columns:repeat(5,1fr);gap:5px}
.ecard{background:rgba(255,255,255,0.05);border:1px solid rgba(255,255,255,0.1);border-radius:6px;padding:5px 2px;text-align:center;cursor:pointer;font-size:18px}
.ecard.on{border-color:#ff88cc}
.nrow{display:flex;gap:7px;align-items:center;margin-bottom:8px;flex-wrap:wrap}
.nrow input{background:rgba(255,255,255,0.09);border:1px solid rgba(255,255,255,0.22);border-radius:4px;color:#fff;font-size:13px;padding:6px 9px;width:160px;font-family:monospace}
.nbtn{background:#ffd700;color:#000;border:none;border-radius:4px;padding:6px 12px;font-size:11px;font-weight:700;cursor:pointer;font-family:monospace}
.coins{color:#ffd700;font-size:12px}
#play-btn{background:#ffd700;color:#000;border:none;border-radius:8px;padding:16px 70px;font-size:20px;font-weight:900;cursor:pointer;font-family:monospace;letter-spacing:3px;margin:14px auto 0;display:block;flex-shrink:0;box-shadow:0 0 24px rgba(255,215,0,0.6)}
#play-btn:hover{background:#ffe033}
.lopen{position:absolute;top:10px;left:50%;transform:translateX(-50%);background:rgba(0,0,0,0.65);border:1px solid rgba(255,215,0,0.45);color:#ffd700;font-size:11px;padding:5px 15px;border-radius:4px;cursor:pointer;pointer-events:all;font-family:monospace;z-index:3}
</style>
</head>
<body>
<div id="wrap">
<canvas id="c"></canvas>
<div id="hud">
  <div id="hp-wrap"><div id="hp-label">HP</div><div id="hp-track"><div id="hp-fill"></div></div><div id="hp-num">100/100</div></div>
  <div id="shield-wrap"><div id="shield-track"><div id="shield-fill"></div></div><div id="shield-num">SHIELD: 60</div></div>
  <div id="sprint-ind">⚡ SPRINT</div><div id="sit-ind">🧎 SIT</div>
  <div id="kills-wrap">KILLS: <span id="kills">0</span></div>
  <div id="pname-hud">PLAYER</div>
  <div id="crosshair"></div>
  <div id="ammo-wrap"><div id="gun-name">STORM-47</div><div id="ammo-num">30</div><div id="ammo-res">/120</div></div>
  <div id="msg"></div>
  <div id="look-hint">DRAG HERE to look around →</div>
  <div id="emote-disp"></div><div id="pet-disp"></div>
  <div id="look-zone"></div>
  <div id="joystick-zone"><div id="joystick-knob"></div></div>
  <div id="fire-btn">FIRE</div>
  <div id="jump-btn">JUMP</div>
  <div id="sprint-btn">RUN</div>
  <div id="sit-btn">SIT</div>
  <div id="gloo-btn">GLOO<br>WALL</div>
  <div id="emote-btn">😄</div>
  <div id="emote-popup"><div class="ep-title">EMOTES</div><div class="ep-grid" id="ep-grid"></div></div>
  <div id="weapon-bar"></div>
  <button class="lopen" id="lopen-btn">☰ LOBBY</button>
</div>
<div id="lobby">
  <h1>BATTLE ZONE</h1>
  <div class="lsub">SEASON 1 — DIAMOND EDITION</div>
  <div class="lsec"><div class="nrow"><input id="name-in" placeholder="Your name..." maxlength="16" value="Player1"/><button class="nbtn" id="name-btn">SET NAME</button><span class="coins">COINS: <span id="coins-n">1200</span></span></div></div>
  <div class="lsec"><h3>BUNDLES</h3><div class="bgrid" id="bungrid"></div></div>
  <div class="lsec"><h3>WEAPON SKINS</h3><div class="ggrid" id="gungrid"></div></div>
  <div class="lsec"><h3>PETS</h3><div class="pgrid" id="petgrid"></div></div>
  <div class="lsec"><h3>EMOTES</h3><div class="egrid" id="emgrid"></div></div>
  <button id="play-btn">▶ PLAY NOW</button>
</div>
</div>
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<script>
const canvas=document.getElementById('c');
const renderer=new THREE.WebGLRenderer({canvas,antialias:true});
renderer.shadowMap.enabled=true;
function resize(){renderer.setSize(window.innerWidth,window.innerHeight);cam.aspect=window.innerWidth/window.innerHeight;cam.updateProjectionMatrix();}
window.addEventListener('resize',resize);

function makeChar(sc,uc,hc,gun){
  const g=new THREE.Group();
  const sm=new THREE.MeshLambertMaterial({color:sc});
  const um=new THREE.MeshLambertMaterial({color:uc});
  const hm=new THREE.MeshLambertMaterial({color:hc});
  const bm=new THREE.MeshLambertMaterial({color:0x111111});
  const dk=new THREE.MeshLambertMaterial({color:0x222222});
  function add(geo,mat,x,y,z){const m=new THREE.Mesh(geo,mat);m.position.set(x,y,z);m.castShadow=true;g.add(m);return m;}
  add(new THREE.BoxGeometry(0.7,0.75,0.38),um,0,0.95,0);
  add(new THREE.BoxGeometry(0.45,0.45,0.42),sm,0,1.6,0);
  add(new THREE.BoxGeometry(0.5,0.28,0.47),hm,0,1.78,0);
  add(new THREE.BoxGeometry(0.55,0.06,0.52),hm,0,1.63,0);
  add(new THREE.CylinderGeometry(0.1,0.1,0.12,8),sm,0,1.39,0);
  add(new THREE.BoxGeometry(0.72,0.4,0.12),dk,0,1.05,0.2);
  add(new THREE.BoxGeometry(0.09,0.07,0.05),new THREE.MeshBasicMaterial({color:0x111111}),-0.11,1.62,0.22);
  add(new THREE.BoxGeometry(0.09,0.07,0.05),new THREE.MeshBasicMaterial({color:0x111111}),0.11,1.62,0.22);
  const lS=add(new THREE.BoxGeometry(0.22,0.38,0.22),um,-0.46,1.03,0);
  const lF=add(new THREE.BoxGeometry(0.18,0.34,0.18),sm,-0.46,0.68,0);
  add(new THREE.BoxGeometry(0.17,0.15,0.17),sm,-0.46,0.48,0);
  const rS=add(new THREE.BoxGeometry(0.22,0.38,0.22),um,0.46,1.03,0);
  const rF=add(new THREE.BoxGeometry(0.18,0.34,0.18),sm,0.46,0.68,0.08);
  add(new THREE.BoxGeometry(0.17,0.15,0.17),sm,0.46,0.48,0.1);
  add(new THREE.BoxGeometry(0.68,0.22,0.36),um,0,0.59,0);
  const lT=add(new THREE.BoxGeometry(0.28,0.38,0.28),um,-0.19,0.3,0);
  const lSh=add(new THREE.BoxGeometry(0.24,0.35,0.24),um,-0.19,-0.04,0);
  add(new THREE.BoxGeometry(0.26,0.16,0.3),bm,-0.19,-0.27,0.03);
  const rT=add(new THREE.BoxGeometry(0.28,0.38,0.28),um,0.19,0.3,0);
  const rSh=add(new THREE.BoxGeometry(0.24,0.35,0.24),um,0.19,-0.04,0);
  add(new THREE.BoxGeometry(0.26,0.16,0.3),bm,0.19,-0.27,0.03);
  if(gun){const gg=new THREE.Group();const gb=new THREE.Mesh(new THREE.BoxGeometry(0.07,0.1,0.55),dk);gb.position.z=-0.28;const bar=new THREE.Mesh(new THREE.CylinderGeometry(0.018,0.018,0.55,8),dk);bar.rotation.x=Math.PI/2;bar.position.set(0,0.04,-0.28);gg.add(gb,bar);gg.position.set(0.55,0.5,0.15);gg.rotation.y=-Math.PI/2;g.add(gg);}
  const hpBg=new THREE.Mesh(new THREE.PlaneGeometry(0.9,0.1),new THREE.MeshBasicMaterial({color:0x333333,depthTest:false}));
  const hpFl=new THREE.Mesh(new THREE.PlaneGeometry(0.9,0.1),new THREE.MeshBasicMaterial({color:0x44ee44,depthTest:false}));hpFl.position.z=0.01;hpFl.name='fill';
  const hpBar=new THREE.Group();hpBar.add(hpBg,hpFl);hpBar.position.set(0,2.15,0);g.add(hpBar);
  g.hpBar=hpBar;g.lS=lS;g.rS=rS;g.lT=lT;g.rT=rT;g.lSh=lSh;g.rSh=rSh;
  return g;
}
function animChar(c,t,mv){
  if(!mv){c.lS.rotation.x=Math.sin(t*0.03)*0.06;c.rS.rotation.x=-Math.sin(t*0.03)*0.06;c.lT.rotation.x=0;c.rT.rotation.x=0;return;}
  const s=Math.sin(t*0.18)*0.55;
  c.lS.rotation.x=-s;c.rS.rotation.x=s;c.lT.rotation.x=s*0.8;c.rT.rotation.x=-s*0.8;
  c.lSh.rotation.x=Math.max(0,s)*0.5;c.rSh.rotation.x=Math.max(0,-s)*0.5;
}

const BUNDLES=[{id:'diamond',name:'Diamond',icon:'💎',price:0,owned:true},{id:'gold',name:'Gold Rush',icon:'🏆',price:300,owned:false},{id:'phantom',name:'Phantom',icon:'👻',price:500,owned:false},{id:'inferno',name:'Inferno',icon:'🔥',price:400,owned:false},{id:'arctic',name:'Arctic',icon:'❄️',price:350,owned:false},{id:'shadow',name:'Shadow',icon:'🌑',price:450,owned:false},{id:'cyber',name:'Cyber',icon:'🤖',price:550,owned:false},{id:'royale',name:'Royale',icon:'👑',price:600,owned:false}];
const SKINS=[{id:'s47',wname:'Storm-47',label:'DEFAULT',color:0x4a3728,price:0,owned:true},{id:'b40',wname:'Blitz-40',label:'DEFAULT',color:0x555555,price:0,owned:true},{id:'vip',wname:'Viper SMG',label:'DEFAULT',color:0x336633,price:0,owned:true},{id:'s47g',wname:'Storm-47',label:'GOLD',color:0xffd700,price:200,owned:false},{id:'b40d',wname:'Blitz-40',label:'DIAMOND',color:0x44aaff,price:250,owned:false},{id:'vipp',wname:'Viper',label:'PHANTOM',color:0xaa88ff,price:220,owned:false}];
const PETS=[{id:'robo',name:'Robo Pup',icon:'🤖',price:0,owned:true},{id:'panda',name:'Panda',icon:'🐼',price:150,owned:false},{id:'dragon',name:'Dragon',icon:'🐲',price:300,owned:false},{id:'bunny',name:'Bunny',icon:'🐰',price:100,owned:false},{id:'none',name:'None',icon:'✖',price:0,owned:true}];
const ALL_EMOTES=['👋','😄','💃','🕺','🤣','🎉','😎','🔥','👍','🫡'];
const WDEFS=[{id:'s47',name:'STORM-47',ammo:30,max:30,res:120,fr:7,dmg:35,auto:true,rt:2000,sp:0.022,melee:false,bl:0.9},{id:'b40',name:'BLITZ-40',ammo:32,max:32,res:160,fr:4,dmg:22,auto:true,rt:1700,sp:0.032,melee:false,bl:0.7},{id:'vip',name:'VIPER SMG',ammo:25,max:25,res:100,fr:3,dmg:18,auto:true,rt:1500,sp:0.04,melee:false,bl:0.6},{id:'gloo',name:'GLOO GUN',ammo:5,max:5,res:15,fr:20,dmg:0,auto:false,rt:2500,sp:0,melee:false,bl:0.6},{id:'blade',name:'BLADE',ammo:1,max:1,res:999,fr:18,dmg:90,auto:false,rt:400,sp:0,melee:true,bl:0.3}];

let pname='Player1',eSkin='s47',ePet='robo',eEmotes=['👋','😄','💃','🕺','🔥','🎉'],coins=1200;

const scene=new THREE.Scene();
scene.background=new THREE.Color(0x5588bb);
scene.fog=new THREE.Fog(0x5588bb,25,90);
const cam=new THREE.PerspectiveCamera(75,window.innerWidth/window.innerHeight,0.1,200);
cam.position.set(0,1.7,0);
scene.add(new THREE.AmbientLight(0xffffff,0.6));
const sun=new THREE.DirectionalLight(0xfff0cc,1.3);
sun.position.set(15,30,10);sun.castShadow=true;sun.shadow.mapSize.width=1024;sun.shadow.mapSize.height=1024;scene.add(sun);
const fl=new THREE.Mesh(new THREE.PlaneGeometry(100,100),new THREE.MeshLambertMaterial({color:0x3a6a30}));fl.rotation.x=-Math.PI/2;fl.receiveShadow=true;scene.add(fl);
scene.add(new THREE.Mesh(new THREE.BoxGeometry(190,90,190),new THREE.MeshBasicMaterial({color:0x4a88cc,side:THREE.BackSide})));
for(let i=0;i<6;i++){const c=new THREE.Mesh(new THREE.BoxGeometry(5+Math.random()*4,1,3),new THREE.MeshBasicMaterial({color:0xffffff,transparent:true,opacity:0.75}));c.position.set(-40+Math.random()*80,18+Math.random()*8,-40+Math.random()*80);scene.add(c);}

const walls=[];
function mkBox(x,z,w,d,h,c){const m=new THREE.Mesh(new THREE.BoxGeometry(w,h,d),new THREE.MeshLambertMaterial({color:c}));m.position.set(x,h/2,z);m.castShadow=true;m.receiveShadow=true;scene.add(m);const rf=new THREE.Mesh(new THREE.BoxGeometry(w+0.3,0.2,d+0.3),new THREE.MeshLambertMaterial({color:0x553322}));rf.position.set(x,h+0.1,z);scene.add(rf);walls.push({x,z,w,d,h,mesh:m,gloo:false});}
mkBox(-8,5,4,3,4,0x8b7355);mkBox(8,-4,3,5,3,0x7a6248);mkBox(0,12,6,2,3.5,0x8a7260);mkBox(-14,-8,2,6,4,0x6b5a40);mkBox(14,6,3,3,4,0x9a8460);mkBox(3,-14,5,2,3,0x7a6840);
function mkTree(x,z){const tr=new THREE.Mesh(new THREE.CylinderGeometry(0.18,0.22,1.8,8),new THREE.MeshLambertMaterial({color:0x5a3a1a}));tr.position.set(x,0.9,z);tr.castShadow=true;scene.add(tr);const lv=new THREE.Mesh(new THREE.ConeGeometry(1.2,2.5,8),new THREE.MeshLambertMaterial({color:0x226622}));lv.position.set(x,2.8,z);scene.add(lv);walls.push({x,z,w:0.5,d:0.5,h:4,mesh:tr,gloo:false});}
[-18,-12,18,16,-5,7].forEach((x,i)=>mkTree(x,[12,-15,-10,14,18,-16][i]));

let enemies=[],bullets=[],pickups=[],gloows=[];
let gs={hp:100,maxHp:100,sh:60,maxSh:100,kills:0,run:false,tick:0,sprint:false,sit:false,jump:false,jumpV:0,ground:true};
let wi=0,wAmmo=30,wRes=120,isReload=false,fcd=0,sanim=0,wgrp=null;
let yaw=0,pitch=0,locked=false,keys={};
let jActive=false,jDX=0,jDY=0,autoFire=false,mDown=false;
let lookDrag=false,lookLX=0,lookLY=0,lookTid=null,lookTX=0,lookTY=0;
let msgTO=null,emTO=null;

function showMsg(t,d=70){document.getElementById('msg').textContent=t;clearTimeout(msgTO);msgTO=setTimeout(()=>document.getElementById('msg').textContent='',d*16);}
function setSprint(v){gs.sprint=v;document.getElementById('sprint-btn').classList.toggle('on',v);document.getElementById('sprint-ind').style.display=v?'block':'none';}
function setSit(v){gs.sit=v;document.getElementById('sit-btn').classList.toggle('on',v);document.getElementById('sit-ind').style.display=v?'block':'none';}

function buildWep(i){
  if(wgrp)cam.remove(wgrp);wgrp=new THREE.Group();
  const def=WDEFS[i];const sk=SKINS.find(s=>s.id===eSkin)||SKINS[0];
  const mat=new THREE.MeshLambertMaterial({color:sk.color});const dk=new THREE.MeshLambertMaterial({color:0x1a1a1a});const wd=new THREE.MeshLambertMaterial({color:0x5a3820});
  if(def.melee){const bl=new THREE.Mesh(new THREE.BoxGeometry(0.04,0.02,0.48),new THREE.MeshLambertMaterial({color:0xddddcc}));bl.position.z=-0.24;const h=new THREE.Mesh(new THREE.BoxGeometry(0.08,0.08,0.16),wd);h.position.z=0.05;wgrp.add(bl,h);}
  else if(def.id==='gloo'){const b=new THREE.Mesh(new THREE.CylinderGeometry(0.07,0.07,0.6,8),new THREE.MeshLambertMaterial({color:0x00cc88}));b.rotation.x=Math.PI/2;b.position.z=-0.3;const t=new THREE.Mesh(new THREE.ConeGeometry(0.1,0.2,8),new THREE.MeshLambertMaterial({color:0x00ffaa}));t.rotation.x=-Math.PI/2;t.position.z=-0.65;wgrp.add(b,t);}
  else{const body=new THREE.Mesh(new THREE.BoxGeometry(0.07,0.11,def.bl),mat);body.position.z=-def.bl/2;const bar=new THREE.Mesh(new THREE.CylinderGeometry(0.016,0.016,def.bl*0.95,8),dk);bar.rotation.x=Math.PI/2;bar.position.set(0,0.045,-def.bl*0.46);const st=new THREE.Mesh(new THREE.BoxGeometry(0.055,0.08,0.24),wd);st.position.set(0,-0.02,0.06);const mg=new THREE.Mesh(new THREE.BoxGeometry(0.045,0.14,0.055),dk);mg.position.set(0,-0.12,-def.bl*0.28);const gr=new THREE.Mesh(new THREE.BoxGeometry(0.048,0.09,0.048),wd);gr.position.set(0,-0.1,-def.bl*0.08);gr.rotation.x=0.35;wgrp.add(body,bar,st,mg,gr);}
  wgrp.position.set(0.2,-0.27,-0.42);cam.add(wgrp);scene.add(cam);
}

const ETYPES=[{sc:0xcc7755,uc:0x883322,hc:0x553311,hp:85,spd:3.0},{sc:0xaa6644,uc:0x334488,hc:0x223366,hp:150,spd:2.1},{sc:0x996644,uc:0x222222,hc:0x111111,hp:240,spd:1.4}];

function spawnEnemy(){const a=Math.random()*Math.PI*2,d=16+Math.random()*14;const lv=Math.min(Math.floor(gs.tick/450),2);const et=ETYPES[lv];const ch=makeChar(et.sc,et.uc,et.hc,true);ch.position.set(Math.cos(a)*d,0,Math.sin(a)*d);scene.add(ch);enemies.push({mesh:ch,hp:et.hp,maxHp:et.hp,speed:et.spd,hpBar:ch.hpBar,st:100+Math.floor(Math.random()*80),tick:0});}
function updEHP(bar,r){const f=bar.getObjectByName('fill');if(f){f.scale.x=Math.max(0.001,r);f.position.x=(r-1)*0.45;f.material.color.setHex(r>0.5?0x44ee44:r>0.25?0xeeaa22:0xee3333);}}
function spawnPick(){const a=Math.random()*Math.PI*2,d=4+Math.random()*12,t=Math.random()<0.6?'ammo':'hp';const m=new THREE.Mesh(new THREE.BoxGeometry(0.45,0.45,0.45),new THREE.MeshLambertMaterial({color:t==='ammo'?0xffcc00:0x44ee88}));m.position.set(Math.cos(a)*d,0.3,Math.sin(a)*d);scene.add(m);pickups.push({mesh:m,type:t,age:0});}
function placeGloo(){const dir=new THREE.Vector3(0,0,-1).applyQuaternion(cam.quaternion);const pos=cam.position.clone().addScaledVector(dir,2.5);pos.y=0;const m=new THREE.Mesh(new THREE.BoxGeometry(2,2.8,0.3),new THREE.MeshLambertMaterial({color:0x00ffaa,transparent:true,opacity:0.7}));m.position.set(pos.x,1.4,pos.z);m.rotation.y=yaw;scene.add(m);gloows.push({mesh:m,life:420});walls.push({x:pos.x,z:pos.z,w:2,d:0.4,h:2.8,mesh:m,gloo:true});showMsg('GLOO WALL!');}
function shoot(){
  if(!gs.run||isReload||fcd>0)return;
  const def=WDEFS[wi];if(wAmmo<=0){startReload();return;}
  if(def.id==='gloo'){placeGloo();wAmmo--;updAmmo();if(wAmmo===0)startReload();return;}
  wAmmo--;fcd=def.fr;sanim=8;updAmmo();
  if(def.melee){for(let j=enemies.length-1;j>=0;j--){const e=enemies[j];if(e.mesh.position.distanceTo(cam.position)<2.6){e.hp-=def.dmg;updEHP(e.hpBar,e.hp/e.maxHp);if(e.hp<=0){scene.remove(e.mesh);enemies.splice(j,1);gs.kills++;document.getElementById('kills').textContent=gs.kills;showMsg('SLICED!');}}}return;}
  const dir=new THREE.Vector3(0,0,-1).applyQuaternion(cam.quaternion);
  if(def.sp>0){dir.x+=(Math.random()-0.5)*def.sp;dir.y+=(Math.random()-0.5)*def.sp;dir.normalize();}
  const bm=new THREE.Mesh(new THREE.SphereGeometry(0.055,6,6),new THREE.MeshBasicMaterial({color:0xffff44}));
  bm.position.copy(cam.position).addScaledVector(dir,0.5);scene.add(bm);
  const fl2=new THREE.PointLight(0xffaa00,3,3);fl2.position.copy(bm.position);scene.add(fl2);setTimeout(()=>scene.remove(fl2),60);
  bullets.push({mesh:bm,dir:dir.clone(),speed:1.4,life:55,dmg:def.dmg,owner:'player'});
  if(wAmmo===0)startReload();
}
function startReload(){if(wRes<=0){showMsg('NO AMMO');return;}isReload=true;showMsg('RELOADING...',150);setTimeout(()=>{const n=WDEFS[wi].max-wAmmo,t=Math.min(n,wRes);wAmmo+=t;wRes-=t;isReload=false;showMsg('RELOADED!');updAmmo();},WDEFS[wi].rt);}
function updAmmo(){document.getElementById('gun-name').textContent=WDEFS[wi].name;document.getElementById('ammo-num').textContent=wAmmo;document.getElementById('ammo-res').textContent='/'+wRes;}
function updHP(){const r=gs.hp/gs.maxHp;document.getElementById('hp-fill').style.width=(r*100)+'%';document.getElementById('hp-fill').style.background=r>0.5?'#44ee66':r>0.25?'#eeaa22':'#ee3333';document.getElementById('hp-num').textContent=Math.max(0,gs.hp)+'/'+gs.maxHp;const sr=gs.sh/gs.maxSh;document.getElementById('shield-fill').style.width=(sr*100)+'%';document.getElementById('shield-num').textContent='SHIELD: '+Math.max(0,gs.sh);}
function initWep(i){wi=i;wAmmo=WDEFS[i].max;wRes=WDEFS[i].res;isReload=false;buildWep(i);updAmmo();document.querySelectorAll('.wslot').forEach((b,j)=>b.classList.toggle('active',j===i));}
function buildWBar(){const bar=document.getElementById('weapon-bar');bar.innerHTML='';WDEFS.forEach((w,i)=>{const d=document.createElement('div');d.className='wslot'+(i===0?' active':'');d.textContent=(i+1)+' '+w.name;d.onclick=()=>{if(!isReload)initWep(i);};bar.appendChild(d);});}

let spT=0,pkT=0;
function loop(){
  requestAnimationFrame(loop);
  if(!gs.run){renderer.render(scene,cam);return;}
  gs.tick++;spT--;pkT--;
  if(spT<=0){spawnEnemy();spT=Math.max(45,110-Math.floor(gs.tick/300)*7);}
  if(pkT<=0){spawnPick();pkT=180;}
  if(fcd>0)fcd--;
  if((mDown||autoFire)&&locked&&WDEFS[wi].auto&&fcd===0)shoot();
  const spd=gs.sprint?0.115:0.058;
  const fwd=new THREE.Vector3(-Math.sin(yaw),0,-Math.cos(yaw));
  const rgt=new THREE.Vector3(Math.cos(yaw),0,-Math.sin(yaw));
  const mv=new THREE.Vector3();
  if(keys['KeyW']||keys['ArrowUp'])mv.addScaledVector(fwd,spd);
  if(keys['KeyS']||keys['ArrowDown'])mv.addScaledVector(fwd,-spd);
  if(keys['KeyA']||keys['ArrowLeft'])mv.addScaledVector(rgt,-spd);
  if(keys['KeyD']||keys['ArrowRight'])mv.addScaledVector(rgt,spd);
  if(jActive&&(Math.abs(jDX)>0.05||Math.abs(jDY)>0.05)){mv.addScaledVector(fwd,-jDY*spd*0.9);mv.addScaledVector(rgt,jDX*spd*0.9);}
  const nx=cam.position.x+mv.x,nz=cam.position.z+mv.z;
  let blk=false;for(const w of walls){if(Math.abs(nx-w.x)<w.w/2+0.6&&Math.abs(nz-w.z)<w.d/2+0.6){blk=true;break;}}
  if(!blk){cam.position.x=nx;cam.position.z=nz;}
  if(gs.jump){gs.jumpV-=0.018;cam.position.y+=gs.jumpV;if(cam.position.y<=1.7){cam.position.y=1.7;gs.jump=false;gs.ground=true;gs.jumpV=0;}}else cam.position.y=gs.sit?1.05:1.7;
  if(sanim>0){if(wgrp)wgrp.position.z=-0.42+Math.sin((8-sanim)/8*Math.PI)*0.055;sanim--;}else if(wgrp)wgrp.position.z=-0.42;
  if(mv.length()>0&&wgrp)wgrp.position.y=-0.27+Math.sin(gs.tick*0.1)*0.013;
  for(let i=enemies.length-1;i>=0;i--){
    const e=enemies[i];e.tick++;
    const dp=new THREE.Vector3().subVectors(cam.position,e.mesh.position);dp.y=0;const dist=dp.length();
    animChar(e.mesh,e.tick,dist>1.5);
    if(dist>0.1){dp.normalize();e.mesh.position.addScaledVector(dp,e.speed*0.016);}
    e.mesh.lookAt(new THREE.Vector3(cam.position.x,e.mesh.position.y,cam.position.z));e.hpBar.lookAt(cam.position);
    if(dist<1.5&&gs.tick%28===0){let d=8;if(gs.sh>0){const s=Math.min(d,gs.sh);gs.sh-=s;d-=s;}gs.hp-=d;updHP();if(gs.hp<=0){endGame();return;}}
    e.st--;if(e.st<=0&&dist<28){const sd=new THREE.Vector3().subVectors(cam.position,e.mesh.position).normalize();const bm2=new THREE.Mesh(new THREE.SphereGeometry(0.065,6,6),new THREE.MeshBasicMaterial({color:0xff3300}));bm2.position.copy(e.mesh.position);bm2.position.y=1.4;bm2.position.addScaledVector(sd,0.8);scene.add(bm2);bullets.push({mesh:bm2,dir:sd,speed:0.9,life:55,dmg:0,owner:'enemy'});e.st=80+Math.floor(Math.random()*70);}
  }
  for(let i=bullets.length-1;i>=0;i--){
    const b=bullets[i];b.mesh.position.addScaledVector(b.dir,b.speed);b.life--;
    if(b.life<=0){scene.remove(b.mesh);bullets.splice(i,1);continue;}
    let hit=false;
    if(b.owner==='player'){for(let j=enemies.length-1;j>=0;j--){const e=enemies[j];if(b.mesh.position.distanceTo(e.mesh.position)<1.2){e.hp-=b.dmg;updEHP(e.hpBar,e.hp/e.maxHp);scene.remove(b.mesh);bullets.splice(i,1);if(e.hp<=0){scene.remove(e.mesh);enemies.splice(j,1);gs.kills++;document.getElementById('kills').textContent=gs.kills;showMsg(['ELIMINATED!','HEADSHOT!','FIRE!','NICE!'][Math.floor(Math.random()*4)]);}hit=true;break;}}}
    else{if(b.mesh.position.distanceTo(cam.position)<0.7){let d=12;if(gs.sh>0){const s=Math.min(d,gs.sh);gs.sh-=s;d-=s;}gs.hp-=d;updHP();scene.remove(b.mesh);bullets.splice(i,1);if(gs.hp<=0){endGame();return;}hit=true;}}
    if(!hit){for(const w of walls){if(b.mesh.position.y<w.h+0.1&&Math.abs(b.mesh.position.x-w.x)<w.w/2+0.2&&Math.abs(b.mesh.position.z-w.z)<w.d/2+0.2){scene.remove(b.mesh);bullets.splice(i,1);break;}}}
  }
  for(let i=pickups.length-1;i>=0;i--){const p=pickups[i];p.age++;p.mesh.rotation.y+=0.04;p.mesh.position.y=0.3+Math.sin(p.age*0.05)*0.12;if(p.mesh.position.distanceTo(cam.position)<1.4){if(p.type==='ammo'){wRes=Math.min(wRes+30,WDEFS[wi].res);showMsg('AMMO +30');updAmmo();}else{gs.hp=Math.min(gs.maxHp,gs.hp+40);showMsg('HP +40');updHP();}scene.remove(p.mesh);pickups.splice(i,1);}if(p.age>700){scene.remove(p.mesh);pickups.splice(i,1);}}
  for(let i=gloows.length-1;i>=0;i--){gloows[i].life--;if(gloows[i].life<=0){scene.remove(gloows[i].mesh);const wi2=walls.findIndex(w=>w.mesh===gloows[i].mesh);if(wi2>=0)walls.splice(wi2,1);gloows.splice(i,1);}}
  renderer.render(scene,cam);
}

function endGame(){
  gs.run=false;document.exitPointerLock();setSprint(false);setSit(false);
  const ov=document.createElement('div');
  ov.style.cssText='position:absolute;inset:0;background:rgba(0,0,0,0.92);display:flex;flex-direction:column;align-items:center;justify-content:center;pointer-events:all;font-family:monospace;z-index:20';
  ov.innerHTML='<div style="color:#ff4455;font-size:26px;letter-spacing:3px;margin-bottom:8px">ELIMINATED</div><div style="color:#ffd700;font-size:18px;margin-bottom:6px">Kills: '+gs.kills+'</div><div style="color:#888;font-size:12px;margin-bottom:20px">Survived '+Math.floor(gs.tick/60)+'s</div><button id="ragain" style="background:#ffd700;color:#000;border:none;border-radius:6px;padding:12px 36px;font-size:16px;font-weight:700;cursor:pointer;font-family:monospace">PLAY AGAIN</button>';
  document.getElementById('wrap').appendChild(ov);
  document.getElementById('ragain').onclick=function(){ov.remove();startGame();};
}
function clearSc(){enemies.forEach(e=>scene.remove(e.mesh));pickups.forEach(p=>scene.remove(p.mesh));bullets.forEach(b=>scene.remove(b.mesh));gloows.forEach(g=>scene.remove(g.mesh));enemies=[];pickups=[];bullets=[];gloows=[];for(let i=walls.length-1;i>=0;i--){if(walls[i].gloo){scene.remove(walls[i].mesh);walls.splice(i,1);}}}

function startGame(){
  clearSc();
  gs={hp:100,maxHp:100,sh:60,maxSh:100,kills:0,run:true,tick:0,sprint:false,sit:false,jump:false,jumpV:0,ground:true};
  cam.position.set(0,1.7,0);yaw=0;pitch=0;cam.rotation.order='YXZ';cam.rotation.set(0,0,0);
  fcd=0;spT=0;pkT=0;setSprint(false);setSit(false);
  document.getElementById('kills').textContent='0';
  document.getElementById('pname-hud').textContent=pname;
  updHP();initWep(0);
  for(let i=0;i<5;i++)spawnPick();
  document.getElementById('lobby').style.display='none';
  showMsg('GAME START! Click screen to aim');
}

document.addEventListener('keydown',e=>{keys[e.code]=true;if(!gs.run)return;if(e.code==='KeyR'&&!isReload&&wAmmo<WDEFS[wi].max)startReload();if(e.code==='Digit1')initWep(0);if(e.code==='Digit2')initWep(1);if(e.code==='Digit3')initWep(2);if(e.code==='Digit4')initWep(3);if(e.code==='Digit5')initWep(4);if(e.code==='ShiftLeft')setSprint(true);if(e.code==='Space'&&gs.ground){gs.jump=true;gs.ground=false;gs.jumpV=0.22;}if(e.code==='KeyC')setSit(!gs.sit);e.preventDefault();});
document.addEventListener('keyup',e=>{keys[e.code]=false;if(e.code==='ShiftLeft')setSprint(false);});
document.addEventListener('mousemove',e=>{if(!locked||!gs.run)return;yaw-=e.movementX*0.002;pitch-=e.movementY*0.002;pitch=Math.max(-1.2,Math.min(1.2,pitch));cam.rotation.order='YXZ';cam.rotation.y=yaw;cam.rotation.x=pitch;});
document.addEventListener('mousedown',e=>{if(e.button===0)mDown=true;});
document.addEventListener('mouseup',e=>{if(e.button===0)mDown=false;});
document.addEventListener('pointerlockchange',()=>{locked=document.pointerLockElement===canvas;document.getElementById('look-hint').style.display=locked?'none':'block';});
canvas.addEventListener('click',()=>{if(gs.run&&!locked)canvas.requestPointerLock();else if(gs.run&&locked)shoot();});
const lookZone=document.getElementById('look-zone');
lookZone.addEventListener('mousedown',e=>{if(locked)return;lookDrag=true;lookLX=e.clientX;lookLY=e.clientY;e.preventDefault();});
document.addEventListener('mousemove',e=>{if(!lookDrag||locked||!gs.run)return;yaw-=(e.clientX-lookLX)*0.004;pitch-=(e.clientY-lookLY)*0.004;pitch=Math.max(-1.2,Math.min(1.2,pitch));cam.rotation.order='YXZ';cam.rotation.y=yaw;cam.rotation.x=pitch;lookLX=e.clientX;lookLY=e.clientY;});
document.addEventListener('mouseup',()=>{lookDrag=false;});
lookZone.addEventListener('touchstart',e=>{e.preventDefault();lookTid=e.changedTouches[0].identifier;lookTX=e.changedTouches[0].clientX;lookTY=e.changedTouches[0].clientY;},{passive:false});
lookZone.addEventListener('touchmove',e=>{e.preventDefault();for(const t of e.changedTouches){if(t.identifier===lookTid){yaw-=(t.clientX-lookTX)*0.005;pitch-=(t.clientY-lookTY)*0.005;pitch=Math.max(-1.2,Math.min(1.2,pitch));cam.rotation.order='YXZ';cam.rotation.y=yaw;cam.rotation.x=pitch;lookTX=t.clientX;lookTY=t.clientY;}}},{passive:false});
lookZone.addEventListener('touchend',e=>{for(const t of e.changedTouches)if(t.identifier===lookTid)lookTid=null;});
const jZone=document.getElementById('joystick-zone'),jKnob=document.getElementById('joystick-knob');let jTid=null;
function updJoy(t){const r=jZone.getBoundingClientRect(),dx=t.clientX-r.left-60,dy=t.clientY-r.top-60;const dist=Math.min(Math.hypot(dx,dy),38),a=Math.atan2(dy,dx);jDX=Math.cos(a)*dist/38;jDY=Math.sin(a)*dist/38;jKnob.style.left=(60+Math.cos(a)*dist-22)+'px';jKnob.style.top=(60+Math.sin(a)*dist-22)+'px';}
jZone.addEventListener('touchstart',e=>{e.preventDefault();jTid=e.changedTouches[0].identifier;jActive=true;updJoy(e.changedTouches[0]);},{passive:false});
jZone.addEventListener('touchmove',e=>{e.preventDefault();for(const t of e.changedTouches)if(t.identifier===jTid)updJoy(t);},{passive:false});
jZone.addEventListener('touchend',()=>{jActive=false;jDX=0;jDY=0;jKnob.style.left='38px';jKnob.style.top='38px';jTid=null;});
jZone.addEventListener('mousedown',e=>{jActive=true;updJoy(e);e.stopPropagation();});
document.addEventListener('mousemove',e=>{if(jActive)updJoy(e);});
document.addEventListener('mouseup',()=>{if(jActive){jActive=false;jDX=0;jDY=0;jKnob.style.left='38px';jKnob.style.top='38px';}});
const fireBtn=document.getElementById('fire-btn');
fireBtn.addEventListener('mousedown',e=>{e.stopPropagation();autoFire=true;shoot();});fireBtn.addEventListener('mouseup',e=>{e.stopPropagation();autoFire=false;});
fireBtn.addEventListener('touchstart',e=>{e.preventDefault();autoFire=true;shoot();},{passive:false});fireBtn.addEventListener('touchend',e=>{e.preventDefault();autoFire=false;},{passive:false});
document.getElementById('jump-btn').addEventListener('click',e=>{e.stopPropagation();if(gs.ground&&gs.run){gs.jump=true;gs.ground=false;gs.jumpV=0.22;}});
document.getElementById('jump-btn').addEventListener('touchstart',e=>{e.preventDefault();e.stopPropagation();if(gs.ground&&gs.run){gs.jump=true;gs.ground=false;gs.jumpV=0.22;}},{passive:false});
document.getElementById('sprint-btn').addEventListener('click',e=>{e.stopPropagation();if(!gs.run)return;setSprint(!gs.sprint);showMsg(gs.sprint?'SPRINTING!':'WALK');});
document.getElementById('sprint-btn').addEventListener('touchstart',e=>{e.preventDefault();e.stopPropagation();if(!gs.run)return;setSprint(!gs.sprint);},{passive:false});
document.getElementById('sit-btn').addEventListener('click',e=>{e.stopPropagation();if(!gs.run)return;setSit(!gs.sit);});
document.getElementById('sit-btn').addEventListener('touchstart',e=>{e.preventDefault();e.stopPropagation();if(!gs.run)return;setSit(!gs.sit);},{passive:false});
document.getElementById('gloo-btn').addEventListener('click',e=>{e.stopPropagation();if(gs.run)initWep(3);});
document.getElementById('gloo-btn').addEventListener('touchstart',e=>{e.preventDefault();e.stopPropagation();if(gs.run)initWep(3);},{passive:false});
let epOpen=false;
document.getElementById('emote-btn').addEventListener('click',e=>{e.stopPropagation();epOpen=!epOpen;document.getElementById('emote-popup').style.display=epOpen?'block':'none';});
function buildEP(){const g=document.getElementById('ep-grid');g.innerHTML='';eEmotes.forEach(em=>{const d=document.createElement('div');d.className='ep-item';d.textContent=em;d.onclick=e=>{e.stopPropagation();const ed=document.getElementById('emote-disp');ed.textContent=em;clearTimeout(emTO);emTO=setTimeout(()=>ed.textContent='',2200);epOpen=false;document.getElementById('emote-popup').style.display='none';};g.appendChild(d);});}
document.getElementById('lopen-btn').addEventListener('click',e=>{e.stopPropagation();gs.run=false;setSprint(false);setSit(false);document.getElementById('lobby').style.display='flex';document.exitPointerLock();});
function buildLobby(){
  const bg=document.getElementById('bungrid');bg.innerHTML='';BUNDLES.forEach(b=>{const d=document.createElement('div');d.className='bcard'+(b.owned?' owned':'');d.innerHTML='<div style="font-size:22px">'+b.icon+'</div><div style="color:#ddd;font-size:9px;margin-top:3px">'+b.name+'</div><div style="color:#ffd700;font-size:9px">'+(b.owned?'OWNED':b.price+' coins')+'</div>';d.onclick=()=>{if(!b.owned){if(coins>=b.price){coins-=b.price;b.owned=true;document.getElementById('coins-n').textContent=coins;}else{alert('Need more coins!');return;}}buildLobby();};bg.appendChild(d);});
  const gg=document.getElementById('gungrid');gg.innerHTML='';SKINS.forEach(s=>{const d=document.createElement('div');d.className='gcard'+(eSkin===s.id?' equipped':'');const c='#'+s.color.toString(16).padStart(6,'0');d.innerHTML='<div style="width:40px;height:10px;background:'+c+';margin:2px auto 4px;border-radius:2px"></div><div style="color:#ddd;font-size:9px">'+s.wname+'</div><div style="color:'+c+';font-size:9px">'+s.label+'</div><div style="color:#ffd700;font-size:8px">'+(s.owned?(eSkin===s.id?'✔ ON':'OWNED'):s.price+' coins')+'</div>';d.onclick=()=>{if(!s.owned){if(coins>=s.price){coins-=s.price;s.owned=true;document.getElementById('coins-n').textContent=coins;}else{alert('Need more coins!');return;}}eSkin=s.id;buildLobby();};gg.appendChild(d);});
  const pg=document.getElementById('petgrid');pg.innerHTML='';PETS.forEach(p=>{const d=document.createElement('div');d.className='pcard'+(ePet===p.id?' equipped':'');d.innerHTML='<div style="font-size:24px">'+p.icon+'</div><div style="color:#ddd;font-size:9px">'+p.name+'</div><div style="color:#ffd700;font-size:9px">'+(p.owned?(ePet===p.id?'✔ ON':'OWNED'):p.price+' coins')+'</div>';d.onclick=()=>{if(!p.owned){if(coins>=p.price){coins-=p.price;p.owned=true;document.getElementById('coins-n').textContent=coins;}else{alert('Need more coins!');return;}}ePet=p.id;const pt=PETS.find(x=>x.id===ePet);document.getElementById('pet-disp').textContent=pt&&pt.id!=='none'?pt.icon:'';buildLobby();};pg.appendChild(d);});
  const eg=document.getElementById('emgrid');eg.innerHTML='';ALL_EMOTES.forEach(em=>{const d=document.createElement('div');d.className='ecard'+(eEmotes.includes(em)?' on':'');d.textContent=em;d.onclick=()=>{if(eEmotes.includes(em))eEmotes=eEmotes.filter(x=>x!==em);else if(eEmotes.length<6)eEmotes.push(em);buildLobby();buildEP();};eg.appendChild(d);});
}
document.getElementById('name-btn').onclick=function(){const v=document.getElementById('name-in').value.trim();if(v){pname=v;document.getElementById('pname-hud').textContent=pname;}};
document.getElementById('play-btn').onclick=function(){startGame();};
buildLobby();buildWBar();buildEP();
const ip=PETS.find(x=>x.id===ePet);if(ip&&ip.id!=='none')document.getElementById('pet-disp').textContent=ip.icon;
resize();loop();
</script>
</body>
</html>
EOF
echo "File created"
Output

File created
