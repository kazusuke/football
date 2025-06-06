# football
<!-- ...既存のhead・style・PLAYERSなど全てそのまま... -->
<body>
  <div class="main" id="main1">
    <div class="field-area">
      <div class="field" id="field1">
        <div class="half-line"></div>
        <div class="center-semicircle"></div>
        <div class="goal-area"></div>
        <div class="penalty-area"></div>
        <div class="goal-line"></div>
        <div class="goal"></div>
        <!-- 選手はJSで描画 -->
      </div>
    </div>
    <div class="bench-area">
      <button class="reset-btn" onclick="movePlayersToFormation(1)">ピッチ内選手を初期配置に戻す</button>
      <div class="bench-title">控え選手</div>
      <div class="bench-list" id="bench1"></div>
      <div class="suspension-title">出場停止</div>
      <div class="suspension-list" id="suspension1"></div>
    </div>
  </div>
  <!-- ↓ここから下にもう1セット複製＋コピー用ボタン -->
  <div class="main" id="main2">
    <div class="field-area">
      <div class="field" id="field2">
        <div class="half-line"></div>
        <div class="center-semicircle"></div>
        <div class="goal-area"></div>
        <div class="penalty-area"></div>
        <div class="goal-line"></div>
        <div class="goal"></div>
      </div>
    </div>
    <div class="bench-area">
      <button class="reset-btn" onclick="movePlayersToFormation(2)">ピッチ内選手を初期配置に戻す</button>
      <button class="reset-btn" style="background:#2ecc71;margin-top:8px;" onclick="copyFromUpper()">↑上の状態をコピー</button>
      <div class="bench-title">控え選手</div>
      <div class="bench-list" id="bench2"></div>
      <div class="suspension-title">出場停止</div>
      <div class="suspension-list" id="suspension2"></div>
    </div>
  </div>
  <!-- 編集用モーダルは1つでOK -->
  <div id="edit-modal">
    <!-- ...既存のモーダル内容... -->
  </div>
<script>
// --- 2面分の状態を持つ ---
const PLAYERS = [
  // ...既存のPLAYERS配列...
];
const DEFAULT_SUSPENSIONS = [23, 18,20,17];
const FORMATION_4231 = [
  // ...既存のFORMATION_4231配列...
];

// 2面分の状態
let states = [
  {
    playersOnField: [...FORMATION_4231.map(p=>p.id)],
    playerPositions: (()=>{let o={};FORMATION_4231.forEach(p=>o[p.id]={x:p.x,y:p.y});return o;})(),
    suspensionPlayers: [...DEFAULT_SUSPENSIONS]
  },
  {
    playersOnField: [...FORMATION_4231.map(p=>p.id)],
    playerPositions: (()=>{let o={};FORMATION_4231.forEach(p=>o[p.id]={x:p.x,y:p.y});return o;})(),
    suspensionPlayers: [...DEFAULT_SUSPENSIONS]
  }
];

// 編集モーダル関連（1面目のみ編集可）
function openEditModal(pid) {
  const p = PLAYERS.find(x => x.id === pid);
  document.getElementById('edit-id').value = p.id;
  document.getElementById('edit-name').value = p.name;
  document.getElementById('edit-number').value = p.number;
  document.getElementById('edit-positions').value = p.positions.join(',');
  document.getElementById('edit-modal').style.display = 'flex';
}
function closeEditModal() {
  document.getElementById('edit-modal').style.display = 'none';
}
document.getElementById('edit-form').onsubmit = function(e) {
  e.preventDefault();
  const pid = +document.getElementById('edit-id').value;
  const p = PLAYERS.find(x => x.id === pid);
  p.name = document.getElementById('edit-name').value;
  p.number = +document.getElementById('edit-number').value;
  p.positions = document.getElementById('edit-positions').value.split(',').map(s => s.trim()).filter(Boolean);
  closeEditModal();
  renderAll();
};

// 2面分描画
function renderAll() {
  render(1);
  render(2);
}
function render(idx) {
  // idx: 1 or 2
  const state = states[idx-1];
  // フィールド側
  const field = document.getElementById('field'+idx);
  field.querySelectorAll('.player').forEach(e=>e.remove());
  const fw = field.clientWidth, fh = field.clientHeight;
  state.playersOnField.forEach(pid=>{
    const p = PLAYERS.find(x=>x.id===pid);
    const pos = state.playerPositions[pid];
    const div = document.createElement('div');
    div.className = 'player';
    div.setAttribute('draggable', true);
    div.setAttribute('data-id', pid);
    div.style.left = (pos.x/100*fw-35)+'px';
    div.style.top = (pos.y/100*fh-40)+'px';
    div.innerHTML = `<div class="player-circle">${p.number}</div><div class="player-name">${p.name}</div>`;
    div.addEventListener('dragstart', e=>onDragStartPlayer(e, idx));
    div.addEventListener('dragend', e=>onDragEndPlayer(e, idx));
    div.addEventListener('touchstart', e=>onTouchStartPlayer(e, idx), {passive:false});
    // 編集は1面目のみ
    if(idx===1) {
      div.querySelector('.player-name').style.cursor = "pointer";
      div.querySelector('.player-name').style.textDecoration = "underline dotted";
      div.querySelector('.player-name').onclick = ()=>openEditModal(pid);
    }
    field.appendChild(div);
  });

  // 控え側
  const bench = document.getElementById('bench'+idx);
  bench.innerHTML = '';
  PLAYERS.filter(p=>!state.playersOnField.includes(p.id) && !state.suspensionPlayers.includes(p.id)).forEach(p=>{
    const div = document.createElement('div');
    div.className = 'bench-player';
    div.setAttribute('draggable', true);
    div.setAttribute('data-id', p.id);
    div.innerHTML = `<div class="player-circle">${p.number}</div>
      <div class="player-name"${idx===1?' style="cursor:pointer; text-decoration:underline dotted;"':''}${idx===1?` onclick="openEditModal(${p.id})"`:""}>${p.name}</div>`;
    div.addEventListener('dragstart', e=>onDragStartBench(e, idx));
    div.addEventListener('dragend', e=>onDragEndBench(e, idx));
    div.addEventListener('touchstart', e=>onTouchStartBench(e, idx), {passive:false});
    // 右クリックで出場停止
    div.addEventListener('contextmenu', e=>{
      e.preventDefault();
      moveToSuspension(p.id, idx);
    });
    bench.appendChild(div);
  });

  // 出場停止
  const suspension = document.getElementById('suspension'+idx);
  suspension.innerHTML = '';
  PLAYERS.filter(p=>state.suspensionPlayers.includes(p.id)).forEach(p=>{
    const div = document.createElement('div');
    div.className = 'suspension-player';
    div.setAttribute('draggable', true);
    div.setAttribute('data-id', p.id);
    div.innerHTML = `<div class="player-circle">${p.number}</div>
      <div class="player-name"${idx===1?' style="cursor:pointer; text-decoration:underline dotted;"':''}${idx===1?` onclick="openEditModal(${p.id})"`:""}>${p.name}</div>`;
    div.addEventListener('dragstart', e=>onDragStartSuspension(e, idx));
    div.addEventListener('dragend', e=>onDragEndSuspension(e, idx));
    div.addEventListener('touchstart', e=>onTouchStartSuspension(e, idx), {passive:false});
    // 右クリックで控えに戻す
    div.addEventListener('contextmenu', e=>{
      e.preventDefault();
      moveToBench(p.id, idx);
    });
    suspension.appendChild(div);
  });
}

// ドラッグデータ
let dragPlayerId = null;
let dragFrom = null;

// フィールド上の選手ドラッグ
function onDragStartPlayer(e, idx) {
  dragPlayerId = +e.target.getAttribute('data-id');
  dragFrom = 'field';
  e.target.classList.add('dragging');
  document.getElementById('field'+idx).addEventListener('dragover', ev=>onDragOverField(ev, idx));
  document.getElementById('field'+idx).addEventListener('drop', ev=>onDropField(ev, idx));
  document.getElementById('bench'+idx).addEventListener('dragover', ev=>onDragOverBench(ev, idx));
  document.getElementById('bench'+idx).addEventListener('drop', ev=>onDropBench(ev, idx));
  document.getElementById('suspension'+idx).addEventListener('dragover', ev=>onDragOverSuspension(ev, idx));
  document.getElementById('suspension'+idx).addEventListener('drop', ev=>onDropSuspension(ev, idx));
}
function onDragEndPlayer(e, idx) {
  e.target.classList.remove('dragging');
  document.getElementById('field'+idx).removeEventListener('dragover', ev=>onDragOverField(ev, idx));
  document.getElementById('field'+idx).removeEventListener('drop', ev=>onDropField(ev, idx));
  document.getElementById('bench'+idx).removeEventListener('dragover', ev=>onDragOverBench(ev, idx));
  document.getElementById('bench'+idx).removeEventListener('drop', ev=>onDropBench(ev, idx));
  document.getElementById('suspension'+idx).removeEventListener('dragover', ev=>onDragOverSuspension(ev, idx));
  document.getElementById('suspension'+idx).removeEventListener('drop', ev=>onDropSuspension(ev, idx));
  dragPlayerId = null;
  dragFrom = null;
}

// 控え選手ドラッグ
function onDragStartBench(e, idx) {
  dragPlayerId = +e.target.getAttribute('data-id');
  dragFrom = 'bench';
  e.target.classList.add('dragging');
  document.getElementById('field'+idx).addEventListener('dragover', ev=>onDragOverField(ev, idx));
  document.getElementById('field'+idx).addEventListener('drop', ev=>onDropField(ev, idx));
  document.getElementById('bench'+idx).addEventListener('dragover', ev=>onDragOverBench(ev, idx));
  document.getElementById('bench'+idx).addEventListener('drop', ev=>onDropBench(ev, idx));
  document.getElementById('suspension'+idx).addEventListener('dragover', ev=>onDragOverSuspension(ev, idx));
  document.getElementById('suspension'+idx).addEventListener('drop', ev=>onDropSuspension(ev, idx));
}
function onDragEndBench(e, idx) {
  e.target.classList.remove('dragging');
  document.getElementById('field'+idx).removeEventListener('dragover', ev=>onDragOverField(ev, idx));
  document.getElementById('field'+idx).removeEventListener('drop', ev=>onDropField(ev, idx));
  document.getElementById('bench'+idx).removeEventListener('dragover', ev=>onDragOverBench(ev, idx));
  document.getElementById('bench'+idx).removeEventListener('drop', ev=>onDropBench(ev, idx));
  document.getElementById('suspension'+idx).removeEventListener('dragover', ev=>onDragOverSuspension(ev, idx));
  document.getElementById('suspension'+idx).removeEventListener('drop', ev=>onDropSuspension(ev, idx));
  dragPlayerId = null;
  dragFrom = null;
}

// 出場停止選手ドラッグ
function onDragStartSuspension(e, idx) {
  dragPlayerId = +e.target.getAttribute('data-id');
  dragFrom = 'suspension';
  e.target.classList.add('dragging');
  document.getElementById('bench'+idx).addEventListener('dragover', ev=>onDragOverBench(ev, idx));
  document.getElementById('bench'+idx).addEventListener('drop', ev=>onDropBench(ev, idx));
}
function onDragEndSuspension(e, idx) {
  e.target.classList.remove('dragging');
  document.getElementById('bench'+idx).removeEventListener('dragover', ev=>onDragOverBench(ev, idx));
  document.getElementById('bench'+idx).removeEventListener('drop', ev=>onDropBench(ev, idx));
  dragPlayerId = null;
  dragFrom = null;
}

// フィールドへのドロップ
function onDragOverField(e, idx) { e.preventDefault(); }
function onDropField(e, idx) {
  e.preventDefault();
  const field = document.getElementById('field'+idx);
  const fw = field.clientWidth, fh = field.clientHeight;
  const state = states[idx-1];
  if (dragFrom === 'bench' && state.playersOnField.length < 11) {
    state.playersOnField.push(dragPlayerId);
    let x = e.offsetX/fw*100, y = e.offsetY/fh*100;
    // GKは一番下
    const p = PLAYERS.find(x=>x.id===dragPlayerId);
    if (p.positions.includes('GK')) y = 95;
    state.playerPositions[dragPlayerId] = {x, y};
  } else if (dragFrom === 'field') {
    let x = e.offsetX/fw*100, y = e.offsetY/fh*100;
    state.playerPositions[dragPlayerId] = {x, y};
  }
  render(idx);
}

// 控えエリアへのドロップ
function onDragOverBench(e, idx) { e.preventDefault(); }
function onDropBench(e, idx) {
  e.preventDefault();
  const state = states[idx-1];
  if (dragFrom === 'field') {
    state.playersOnField = state.playersOnField.filter(id=>id!==dragPlayerId);
    delete state.playerPositions[dragPlayerId];
  } else if (dragFrom === 'suspension') {
    state.suspensionPlayers = state.suspensionPlayers.filter(id=>id!==dragPlayerId);
  }
  render(idx);
}

// 出場停止エリアへのドロップ
function onDragOverSuspension(e, idx) { e.preventDefault(); }
function onDropSuspension(e, idx) {
  e.preventDefault();
  const state = states[idx-1];
  if (dragFrom === 'bench') {
    state.suspensionPlayers.push(dragPlayerId);
  }
  render(idx);
}

// タッチ操作
function onTouchStartPlayer(e, idx) {
  e.preventDefault();
  const pid = +e.target.getAttribute('data-id');
  const field = document.getElementById('field'+idx);
  let offsetX = e.touches[0].clientX - e.target.getBoundingClientRect().left;
  let offsetY = e.touches[0].clientY - e.target.getBoundingClientRect().top;
  const move = (ev) => {
    let x = (ev.touches[0].clientX - field.getBoundingClientRect().left - offsetX);
    let y = (ev.touches[0].clientY - field.getBoundingClientRect().top - offsetY);
    e.target.style.left = Math.max(0, Math.min(x, field.clientWidth-70))+'px';
    e.target.style.top = Math.max(0, Math.min(y, field.clientHeight-80))+'px';
  };
  const up = (ev) => {
    let fw = field.clientWidth, fh = field.clientHeight;
    let left = parseInt(e.target.style.left), top = parseInt(e.target.style.top);
    states[idx-1].playerPositions[pid] = {x: (left+35)/fw*100, y: (top+40)/fh*100};
    document.removeEventListener('touchmove', move);
    document.removeEventListener('touchend', up);
    render(idx);
  };
  document.addEventListener('touchmove', move, {passive:false});
  document.addEventListener('touchend', up, {passive:false});
}
function onTouchStartBench(e, idx) {
  e.preventDefault();
  const pid = +e.target.getAttribute('data-id');
  const state = states[idx-1];
  if (state.playersOnField.length >= 11) return;
  state.playersOnField.push(pid);
  state.playerPositions[pid] = {x: 50, y: 50};
  render(idx);
}
function onTouchStartSuspension(e, idx) {
  e.preventDefault();
  // 出場停止→控え
  const pid = +e.target.getAttribute('data-id');
  const state = states[idx-1];
  state.suspensionPlayers = state.suspensionPlayers.filter(id=>id!==pid);
  render(idx);
}

// 右クリックで控え→出場停止
function moveToSuspension(pid, idx) {
  const state = states[idx-1];
  if (!state.suspensionPlayers.includes(pid)) {
    state.suspensionPlayers.push(pid);
    render(idx);
  }
}
// 右クリックで出場停止→控え
function moveToBench(pid, idx) {
  const state = states[idx-1];
  state.suspensionPlayers = state.suspensionPlayers.filter(id=>id!==pid);
  render(idx);
}

// ピッチ内選手を一番近い初期配置へ
function movePlayersToFormation(idx) {
  const state = states[idx-1];
  let remainInit = FORMATION_4231.map(p=>({...p}));
  state.playersOnField.forEach(pid=>{
    let minIdx = 0, minDist = 1e9;
    for(let i=0;i<remainInit.length;i++) {
      let d = Math.abs(remainInit[i].x - (state.playerPositions[pid]?.x??50)) + Math.abs(remainInit[i].y - (state.playerPositions[pid]?.y??50));
      if (d < minDist) { minDist = d; minIdx = i; }
    }
    state.playerPositions[pid] = {x: remainInit[minIdx].x, y: remainInit[minIdx].y};
    remainInit.splice(minIdx,1);
  });
  render(idx);
}

// 上の状態を下にコピー
function copyFromUpper() {
  // 深いコピー
  states[1].playersOnField = [...states[0].playersOnField];
  states[1].playerPositions = JSON.parse(JSON.stringify(states[0].playerPositions));
  states[1].suspensionPlayers = [...states[0].suspensionPlayers];
  render(2);
}

window.addEventListener('resize', renderAll);
renderAll();
</script>
</body>
</html>
