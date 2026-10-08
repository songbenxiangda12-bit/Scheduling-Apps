<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>就活スケジュール</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Shippori+Mincho:wght@500;700&family=Zen+Kaku+Gothic+New:wght@400;500;700&display=swap" rel="stylesheet">
<style>
  :root{
    --bg: #EDECE6;
    --surface: #FFFFFF;
    --ink: #1B2027;
    --ink-soft: #5B5F66;
    --navy: #16213E;
    --navy-soft: #2C3A5E;
    --gold: #B8862E;
    --gold-soft: #E9D9B0;
    --line: #D8D6CC;
    --danger: #B03A2E;

    --cat-info: #3B6EA5;
    --cat-es: #B03A2E;
    --cat-interview: #16213E;
    --cat-ob: #4A7856;
    --cat-other: #7A776B;
  }

  *{ box-sizing: border-box; }

  body{
    margin:0;
    background: var(--bg);
    color: var(--ink);
    font-family: 'Zen Kaku Gothic New', sans-serif;
    -webkit-font-smoothing: antialiased;
  }

  .app{
    max-width: 620px;
    margin: 0 auto;
    padding: 28px 18px 80px;
  }

  header.top{
    display:flex;
    align-items:center;
    justify-content:space-between;
    margin-bottom: 22px;
  }

  header.top h1{
    font-family:'Shippori Mincho', serif;
    font-weight: 700;
    font-size: 24px;
    letter-spacing: 0.04em;
    margin:0;
    color: var(--navy);
  }

  header.top .sub{
    font-size: 11px;
    color: var(--ink-soft);
    margin-top: 4px;
    letter-spacing: 0.05em;
  }

  .header-actions{
    display:flex;
    gap: 8px;
    align-items:center;
  }

  .add-btn{
    background: var(--navy);
    color: #fff;
    border:none;
    border-radius: 3px;
    padding: 12px 16px;
    min-height: 44px;
    font-family:'Zen Kaku Gothic New', sans-serif;
    font-weight: 700;
    font-size: 13px;
    cursor:pointer;
    transition: background .15s ease;
    white-space: nowrap;
    touch-action: manipulation;
    -webkit-tap-highlight-color: rgba(255,255,255,0.2);
  }
  .add-btn:hover{ background: var(--navy-soft); }
  .add-btn:active{ background: var(--navy-soft); }
  .add-btn:focus-visible{ outline: 2px solid var(--gold); outline-offset: 2px; }

  .bell-btn{
    background: #fff;
    border: 1px solid var(--line);
    color: var(--navy);
    border-radius: 3px;
    width: 44px;
    height: 44px;
    font-size: 17px;
    cursor:pointer;
    flex-shrink:0;
    position: relative;
    touch-action: manipulation;
    -webkit-tap-highlight-color: rgba(22,33,62,0.12);
  }
  .bell-btn:hover{ background: #F5F5F1; }
  .bell-btn:active{ background: #EDEDE8; }
  .bell-btn:focus-visible{ outline: 2px solid var(--gold); outline-offset: 2px; }
  .bell-btn.on::after{
    content:"";
    position:absolute;
    top:6px; right:7px;
    width:6px; height:6px;
    border-radius:50%;
    background: var(--gold);
  }

  .checkbox-row{
    display:flex;
    align-items:center;
    gap: 10px;
    padding: 12px 0;
    border-bottom: 1px solid var(--line);
  }
  .checkbox-row:last-child{ border-bottom:none; }
  .checkbox-row label{
    font-size: 14px;
    color: var(--ink);
    cursor:pointer;
    padding: 4px 0;
  }
  .checkbox-row input[type="checkbox"]{
    width: 20px; height: 20px;
    accent-color: var(--navy);
    cursor:pointer;
    flex-shrink:0;
  }

  .settings-note{
    font-size: 12px;
    color: var(--ink-soft);
    line-height: 1.6;
    background: #FAFAF7;
    border: 1px solid var(--line);
    border-radius: 4px;
    padding: 10px 12px;
    margin-top: 4px;
  }

  .perm-status{
    font-size: 12px;
    margin-top: 10px;
    padding: 8px 10px;
    border-radius: 3px;
  }
  .perm-status.granted{ background: #EEF4EC; color: var(--cat-ob); }
  .perm-status.denied{ background: #F7E9E7; color: var(--danger); }
  .perm-status.default{ background: #F1F1EC; color: var(--ink-soft); }

  /* Hero: next event */
  .hero{
    background: var(--navy);
    border-radius: 4px;
    padding: 20px 20px 18px;
    margin-bottom: 22px;
    position: relative;
    overflow: hidden;
  }
  .hero::before{
    content:"";
    position:absolute;
    left:0; top:0; bottom:0;
    width: 5px;
    background: var(--gold);
  }
  .hero .label{
    color: var(--gold-soft);
    font-size: 11px;
    letter-spacing: 0.12em;
    margin-bottom: 10px;
  }
  .hero .row{
    display:flex;
    align-items: baseline;
    gap: 14px;
    flex-wrap: wrap;
  }
  .hero .days{
    font-family:'Shippori Mincho', serif;
    font-size: 44px;
    font-weight: 700;
    color: #fff;
    line-height: 1;
  }
  .hero .days span{
    font-size: 15px;
    margin-left: 4px;
    font-family:'Zen Kaku Gothic New', sans-serif;
    font-weight: 500;
    color: var(--gold-soft);
  }
  .hero .info{
    color: #EDEDED;
    font-size: 14px;
    line-height: 1.5;
  }
  .hero .info .company{ font-weight: 700; }
  .hero .info .meta{ color: #B9BFCF; font-size: 12.5px; }
  .hero.empty{
    background: var(--surface);
    border: 1px dashed var(--line);
  }
  .hero.empty::before{ display:none; }
  .hero.empty .msg{
    color: var(--ink-soft);
    font-size: 14px;
  }

  /* Filters */
  .filters{
    display:flex;
    gap: 6px;
    margin-bottom: 16px;
    border-bottom: 1px solid var(--line);
  }
  .filters button{
    background: none;
    border: none;
    padding: 12px 10px;
    min-height: 44px;
    font-family:'Zen Kaku Gothic New', sans-serif;
    font-size: 13px;
    color: var(--ink-soft);
    cursor: pointer;
    border-bottom: 2px solid transparent;
    margin-bottom: -1px;
    touch-action: manipulation;
    -webkit-tap-highlight-color: transparent;
  }
  .filters button.active{
    color: var(--navy);
    font-weight: 700;
    border-bottom-color: var(--gold);
  }

  .month-heading{
    font-size: 12px;
    color: var(--ink-soft);
    letter-spacing: 0.08em;
    margin: 18px 2px 8px;
  }

  .card{
    display:flex;
    background: var(--surface);
    border: 1px solid var(--line);
    border-radius: 4px;
    margin-bottom: 10px;
    overflow: hidden;
  }
  .card.done{ opacity: 0.55; }

  .card .datebox{
    width: 62px;
    flex-shrink:0;
    display:flex;
    flex-direction:column;
    align-items:center;
    justify-content:center;
    padding: 10px 4px;
    border-right: 1px dashed var(--line);
    background: #FAFAF7;
    position:relative;
  }
  .card .datebox .dow{
    font-size: 10px;
    color: var(--ink-soft);
  }
  .card .datebox .dnum{
    font-family:'Shippori Mincho', serif;
    font-size: 22px;
    font-weight: 700;
    line-height:1.1;
    color: var(--navy);
  }
  .card .datebox .mon{
    font-size: 10px;
    color: var(--ink-soft);
  }

  .card .body{
    flex:1;
    padding: 10px 12px;
    min-width:0;
  }
  .card .toprow{
    display:flex;
    align-items:center;
    gap: 8px;
    margin-bottom: 3px;
  }
  .dot{
    width: 8px; height: 8px;
    border-radius: 50%;
    flex-shrink:0;
  }
  .cat-label{
    font-size: 11px;
    color: var(--ink-soft);
  }
  .card .company{
    font-weight: 700;
    font-size: 15px;
    margin: 2px 0 2px;
    word-break: break-word;
  }
  .card .memo{
    font-size: 12.5px;
    color: var(--ink-soft);
    white-space: pre-wrap;
    word-break: break-word;
  }
  .card .time{
    font-size: 12px;
    color: var(--ink-soft);
  }
  .card .remain{
    font-size: 11px;
    font-weight: 700;
    margin-top: 4px;
    display:inline-block;
  }
  .remain.urgent{ color: var(--danger); }
  .remain.soon{ color: var(--gold); }
  .remain.later{ color: var(--ink-soft); }
  .remain.past{ color: var(--ink-soft); font-weight:400; }

  .card .actions{
    display:flex;
    flex-direction:column;
    gap: 4px;
    padding: 6px 4px;
    border-left: 1px dashed var(--line);
    justify-content:center;
  }
  .icon-btn{
    background:none;
    border:none;
    cursor:pointer;
    color: var(--ink-soft);
    font-size: 17px;
    line-height:1;
    width: 40px;
    height: 40px;
    display:flex;
    align-items:center;
    justify-content:center;
    border-radius: 4px;
    touch-action: manipulation;
    -webkit-tap-highlight-color: rgba(22,33,62,0.12);
  }
  .icon-btn:hover{ color: var(--navy); background: #F2F2EE; }
  .icon-btn:active{ background: #E9E9E3; }
  .icon-btn:focus-visible{ outline: 2px solid var(--gold); outline-offset:1px; }

  .empty-state{
    text-align:center;
    padding: 50px 10px;
    color: var(--ink-soft);
    font-size: 13.5px;
  }

  /* Modal */
  .overlay{
    position: fixed;
    inset:0;
    background: rgba(20,24,34,0.45);
    display:flex;
    align-items:flex-end;
    justify-content:center;
    z-index: 50;
  }
  @media (min-width: 640px){
    .overlay{ align-items:center; }
  }
  .modal{
    background: var(--surface);
    width: 100%;
    max-width: 460px;
    border-radius: 8px 8px 0 0;
    padding: 22px 20px 24px;
    max-height: 88vh;
    overflow-y:auto;
  }
  @media (min-width: 640px){
    .modal{ border-radius: 8px; }
  }
  .modal h2{
    font-family:'Shippori Mincho', serif;
    font-size: 18px;
    margin: 0 0 16px;
    color: var(--navy);
  }
  .field{ margin-bottom: 14px; }
  .field label{
    display:block;
    font-size: 12px;
    color: var(--ink-soft);
    margin-bottom: 5px;
  }
  .field input, .field select, .field textarea{
    width:100%;
    border: 1px solid var(--line);
    border-radius: 3px;
    padding: 11px 10px;
    font-family:'Zen Kaku Gothic New', sans-serif;
    font-size: 16px;
    color: var(--ink);
    background: #fff;
  }
  .field textarea{ resize: vertical; min-height: 54px; }
  .field-row{ display:flex; gap: 10px; }
  .field-row .field{ flex:1; }

  .cat-select{
    display:flex;
    flex-wrap:wrap;
    gap:6px;
  }
  .cat-option{
    border:1px solid var(--line);
    border-radius: 20px;
    padding: 10px 14px;
    min-height: 40px;
    font-size: 13px;
    cursor:pointer;
    display:flex;
    align-items:center;
    gap:6px;
    background:#fff;
    touch-action: manipulation;
    -webkit-tap-highlight-color: rgba(22,33,62,0.1);
  }
  .cat-option.selected{
    border-color: var(--navy);
    background: #F3F4F8;
    font-weight:700;
  }

  .modal-actions{
    display:flex;
    gap: 10px;
    margin-top: 18px;
  }
  .btn{
    flex:1;
    padding: 13px;
    min-height: 46px;
    border-radius: 3px;
    border:none;
    font-family:'Zen Kaku Gothic New', sans-serif;
    font-weight:700;
    font-size: 14px;
    cursor:pointer;
    touch-action: manipulation;
  }
  .btn.primary{ background: var(--navy); color:#fff; }
  .btn.primary:hover, .btn.primary:active{ background: var(--navy-soft); }
  .btn.ghost{ background:#fff; color: var(--ink-soft); border:1px solid var(--line); }
  .btn.ghost:hover, .btn.ghost:active{ background:#F5F5F1; }
  .btn.danger{ background: var(--danger); color:#fff; }
  .btn.danger:active{ background: #973026; }

  .err{
    color: var(--danger);
    font-size: 12px;
    margin-top: -8px;
    margin-bottom: 12px;
  }

  .status-note{
    text-align:center;
    font-size: 11.5px;
    color: var(--ink-soft);
    margin-top: 26px;
  }

  @media (prefers-reduced-motion: no-preference){
    .card, .add-btn{ transition: transform .12s ease; }
  }
</style>
</head>
<body>

<div class="app" id="app">
  <header class="top">
    <div>
      <h1>就活スケジュール</h1>
      <div class="sub">予定だけを、シンプルに管理する</div>
    </div>
    <div class="header-actions">
      <button class="bell-btn" id="openNotifyBtn" title="通知設定">🔔</button>
      <button class="add-btn" id="openAddBtn">＋ 予定を追加</button>
    </div>
  </header>

  <div id="heroSlot"></div>

  <div class="filters" id="filters">
    <button data-filter="upcoming" class="active">今後の予定</button>
    <button data-filter="all">すべて</button>
    <button data-filter="done">終了済み</button>
  </div>

  <div id="listSlot"></div>

  <div class="status-note" id="statusNote"></div>
</div>

<div id="modalSlot"></div>

<script>
(function(){

  const CATEGORIES = {
    info:       { label: '説明会',   color: 'var(--cat-info)' },
    es:         { label: 'ES締切',   color: 'var(--cat-es)' },
    interview:  { label: '面接',     color: 'var(--cat-interview)' },
    ob:         { label: 'OB/OG訪問', color: 'var(--cat-ob)' },
    other:      { label: 'その他',   color: 'var(--cat-other)' }
  };

  const DOW = ['日','月','火','水','木','金','土'];

  let events = [];
  let filter = 'upcoming';
  let editingId = null;
  let loaded = false;
  let settings = { enabled: false, notifyDays: [3,1,0] };
  let notifyTimer = null;

  const heroSlot = document.getElementById('heroSlot');
  const listSlot = document.getElementById('listSlot');
  const modalSlot = document.getElementById('modalSlot');
  const statusNote = document.getElementById('statusNote');
  const filtersEl = document.getElementById('filters');

  function uid(){
    return 'ev_' + Date.now() + '_' + Math.random().toString(36).slice(2,8);
  }

  function todayMidnight(){
    const d = new Date();
    d.setHours(0,0,0,0);
    return d;
  }

  function parseEventDate(ev){
    // date: "YYYY-MM-DD", time optional "HH:MM"
    const [y,m,d] = ev.date.split('-').map(Number);
    if(ev.time){
      const [hh,mm] = ev.time.split(':').map(Number);
      return new Date(y, m-1, d, hh, mm);
    }
    return new Date(y, m-1, d);
  }

  function dayDiff(ev){
    const dt = parseEventDate(ev);
    const dtMid = new Date(dt.getFullYear(), dt.getMonth(), dt.getDate());
    const t = todayMidnight();
    return Math.round((dtMid - t) / 86400000);
  }

  function isPast(ev){
    return dayDiff(ev) < 0;
  }

  function remainLabel(ev){
    const diff = dayDiff(ev);
    if(diff < 0) return { text: '終了', cls: 'past' };
    if(diff === 0) return { text: '本日', cls: 'urgent' };
    if(diff <= 3) return { text: `あと${diff}日`, cls: 'urgent' };
    if(diff <= 7) return { text: `あと${diff}日`, cls: 'soon' };
    return { text: `あと${diff}日`, cls: 'later' };
  }

  async function loadEvents(){
    try{
      const res = await window.storage.get('schedule:events');
      events = res && res.value ? JSON.parse(res.value) : [];
    }catch(e){
      events = [];
    }
    loaded = true;
  }

  async function saveEvents(){
    try{
      const res = await window.storage.set('schedule:events', JSON.stringify(events));
      if(!res){
        statusNote.textContent = '保存に失敗しました。もう一度お試しください。';
      } else {
        statusNote.textContent = '';
      }
    }catch(e){
      statusNote.textContent = '保存に失敗しました。もう一度お試しください。';
    }
  }

  async function loadSettings(){
    try{
      const res = await window.storage.get('schedule:settings');
      if(res && res.value){
        const parsed = JSON.parse(res.value);
        settings = { enabled: !!parsed.enabled, notifyDays: parsed.notifyDays || [3,1,0] };
      }
    }catch(e){
      // no settings saved yet, keep defaults
    }
  }

  async function saveSettings(){
    try{
      await window.storage.set('schedule:settings', JSON.stringify(settings));
    }catch(e){
      // ignore; will just fall back to defaults next load
    }
  }

  function updateBellIndicator(){
    const btn = document.getElementById('openNotifyBtn');
    if(!btn) return;
    const active = settings.enabled && typeof Notification !== 'undefined' && Notification.permission === 'granted';
    btn.classList.toggle('on', active);
  }

  async function wasAlreadyNotified(key){
    try{
      const res = await window.storage.get(key);
      return !!(res && res.value);
    }catch(e){
      return false;
    }
  }

  async function markNotified(key){
    try{ await window.storage.set(key, '1'); }catch(e){ /* ignore */ }
  }

  async function checkAndNotify(){
    if(!settings.enabled) return;
    if(typeof Notification === 'undefined' || Notification.permission !== 'granted') return;

    for(const ev of events){
      if(ev.done) continue;
      const diff = dayDiff(ev);
      if(diff < 0) continue;
      if(!settings.notifyDays.includes(diff)) continue;

      const key = `notified:${ev.id}:${diff}`;
      const already = await wasAlreadyNotified(key);
      if(already) continue;

      const cat = CATEGORIES[ev.category] || CATEGORIES.other;
      const bodyText = diff === 0
        ? `本日が予定日です（${cat.label}）`
        : `あと${diff}日です（${cat.label}）`;

      try{
        new Notification(ev.company, { body: bodyText });
      }catch(e){ /* ignore notification errors */ }

      await markNotified(key);
    }
  }

  function startNotifyLoop(){
    if(notifyTimer) clearInterval(notifyTimer);
    checkAndNotify();
    notifyTimer = setInterval(checkAndNotify, 30 * 60 * 1000);
  }

  function permStatusHtml(){
    if(typeof Notification === 'undefined'){
      return `<div class="perm-status denied">お使いの環境では通知がサポートされていません。</div>`;
    }
    const p = Notification.permission;
    if(p === 'granted') return `<div class="perm-status granted">通知が許可されています。</div>`;
    if(p === 'denied') return `<div class="perm-status denied">通知がブロックされています。ブラウザの設定から許可してください。</div>`;
    return `<div class="perm-status default">まだ通知が許可されていません。</div>`;
  }

  function openNotifySettings(){
    const dayOptions = [
      { v: 7, label: '1週間前' },
      { v: 3, label: '3日前' },
      { v: 1, label: '前日' },
      { v: 0, label: '当日' }
    ];

    modalSlot.innerHTML = `
      <div class="overlay" id="overlay">
        <div class="modal">
          <h2>通知設定</h2>
          <div class="checkbox-row">
            <input type="checkbox" id="enableToggle" ${settings.enabled ? 'checked' : ''}>
            <label for="enableToggle">締切が近づいたら通知する</label>
          </div>
          <div class="field" style="margin-top:14px;">
            <label>通知するタイミング</label>
            ${dayOptions.map(o => `
              <div class="checkbox-row">
                <input type="checkbox" class="dayCheck" value="${o.v}" ${settings.notifyDays.includes(o.v) ? 'checked' : ''}>
                <label>${o.label}</label>
              </div>
            `).join('')}
          </div>
          ${permStatusHtml()}
          <div class="settings-note">
            この通知はブラウザの通知機能を使っています。このページを開いているタブがある間だけ届きます。アプリを完全に閉じている間や、スマホでバックグラウンドにある間は届かないのでご注意ください。
          </div>
          <div class="modal-actions">
            <button class="btn ghost" id="cancelBtn">閉じる</button>
            <button class="btn primary" id="saveNotifyBtn">保存する</button>
          </div>
        </div>
      </div>`;

    document.getElementById('overlay').addEventListener('click', (e) => {
      if(e.target.id === 'overlay') closeModal();
    });
    document.getElementById('cancelBtn').addEventListener('click', closeModal);

    document.getElementById('saveNotifyBtn').addEventListener('click', async () => {
      const enable = document.getElementById('enableToggle').checked;
      const days = Array.from(document.querySelectorAll('.dayCheck:checked')).map(el => Number(el.value));

      if(enable && typeof Notification !== 'undefined' && Notification.permission === 'default'){
        try{
          const perm = await Notification.requestPermission();
          if(perm !== 'granted'){
            settings.enabled = false;
            await saveSettings();
            updateBellIndicator();
            openNotifySettings();
            return;
          }
        }catch(e){
          settings.enabled = false;
        }
      }

      settings.enabled = enable && typeof Notification !== 'undefined' && Notification.permission === 'granted';
      settings.notifyDays = days.length ? days : [3,1,0];
      await saveSettings();
      updateBellIndicator();
      if(settings.enabled) startNotifyLoop();
      else if(notifyTimer) clearInterval(notifyTimer);
      closeModal();
    });
  }

  function sortedEvents(){
    return [...events].sort((a,b) => parseEventDate(a) - parseEventDate(b));
  }

  function visibleEvents(){
    const sorted = sortedEvents();
    if(filter === 'upcoming') return sorted.filter(ev => !ev.done && !isPast(ev));
    if(filter === 'done') return sorted.filter(ev => ev.done || isPast(ev));
    return sorted;
  }

  function nextEvent(){
    return sortedEvents().find(ev => !ev.done && !isPast(ev));
  }

  function renderHero(){
    const ev = nextEvent();
    if(!ev){
      heroSlot.innerHTML = `
        <div class="hero empty">
          <div class="msg">直近の予定はありません。右上から予定を追加しましょう。</div>
        </div>`;
      return;
    }
    const diff = dayDiff(ev);
    const diffText = diff === 0 ? '本日' : (diff > 0 ? diff : 0);
    const diffUnit = diff === 0 ? '' : '日後';
    const cat = CATEGORIES[ev.category];
    const dateStr = formatDateLong(ev);

    heroSlot.innerHTML = `
      <div class="hero">
        <div class="label">次の予定まで</div>
        <div class="row">
          <div class="days">${diffText}<span>${diffUnit}</span></div>
          <div class="info">
            <div class="company">${escapeHtml(ev.company)}　<span style="color:var(--gold-soft); font-weight:400;">${cat.label}</span></div>
            <div class="meta">${dateStr}${ev.time ? '　' + ev.time : ''}</div>
          </div>
        </div>
      </div>`;
  }

  function formatDateLong(ev){
    const d = parseEventDate(ev);
    return `${d.getMonth()+1}月${d.getDate()}日（${DOW[d.getDay()]}）`;
  }

  function escapeHtml(str){
    const div = document.createElement('div');
    div.textContent = str || '';
    return div.innerHTML;
  }

  function renderList(){
    const list = visibleEvents();

    if(!loaded){
      listSlot.innerHTML = `<div class="empty-state">読み込み中…</div>`;
      return;
    }

    if(list.length === 0){
      const msg = filter === 'done'
        ? '終了した予定はまだありません。'
        : filter === 'all'
          ? '予定がまだ登録されていません。'
          : '今後の予定はありません。';
      listSlot.innerHTML = `<div class="empty-state">${msg}</div>`;
      return;
    }

    let html = '';
    let currentMonth = null;

    list.forEach(ev => {
      const d = parseEventDate(ev);
      const monthKey = `${d.getFullYear()}-${d.getMonth()}`;
      if(monthKey !== currentMonth){
        currentMonth = monthKey;
        html += `<div class="month-heading">${d.getFullYear()}年 ${d.getMonth()+1}月</div>`;
      }
      const cat = CATEGORIES[ev.category] || CATEGORIES.other;
      const remain = remainLabel(ev);
      const doneClass = (ev.done || isPast(ev)) ? 'done' : '';

      html += `
        <div class="card ${doneClass}" data-id="${ev.id}">
          <div class="datebox">
            <div class="dow">${DOW[d.getDay()]}曜</div>
            <div class="dnum">${d.getDate()}</div>
            <div class="mon">${d.getMonth()+1}月</div>
          </div>
          <div class="body">
            <div class="toprow">
              <span class="dot" style="background:${cat.color}"></span>
              <span class="cat-label">${cat.label}</span>
            </div>
            <div class="company">${escapeHtml(ev.company)}</div>
            ${ev.time ? `<div class="time">${ev.time}〜</div>` : ''}
            ${ev.memo ? `<div class="memo">${escapeHtml(ev.memo)}</div>` : ''}
            <div class="remain ${remain.cls}">${remain.text}</div>
          </div>
          <div class="actions">
            <button class="icon-btn" data-action="edit" title="編集">✎</button>
            <button class="icon-btn" data-action="toggle" title="${ev.done ? '未完了に戻す' : '完了にする'}">${ev.done ? '↺' : '✓'}</button>
            <button class="icon-btn" data-action="delete" title="削除">✕</button>
          </div>
        </div>`;
    });

    listSlot.innerHTML = html;
  }

  function render(){
    renderHero();
    renderList();
  }

  function openModal(existing){
    editingId = existing ? existing.id : null;
    const ev = existing || { category: 'info', date: toInputDate(new Date()), time:'', company:'', memo:'' };

    modalSlot.innerHTML = `
      <div class="overlay" id="overlay">
        <div class="modal">
          <h2>${existing ? '予定を編集' : '予定を追加'}</h2>
          <div class="field">
            <label>種類</label>
            <div class="cat-select" id="catSelect">
              ${Object.entries(CATEGORIES).map(([key, c]) => `
                <div class="cat-option ${key === ev.category ? 'selected' : ''}" data-cat="${key}">
                  <span class="dot" style="background:${c.color}"></span>${c.label}
                </div>
              `).join('')}
            </div>
          </div>
          <div class="field">
            <label>企業名・団体名</label>
            <input type="text" id="companyInput" value="${escapeHtml(ev.company)}" placeholder="例）〇〇株式会社">
          </div>
          <div class="field-row">
            <div class="field">
              <label>日付</label>
              <input type="date" id="dateInput" value="${ev.date}">
            </div>
            <div class="field">
              <label>時刻（任意）</label>
              <input type="time" id="timeInput" value="${ev.time || ''}">
            </div>
          </div>
          <div class="field">
            <label>メモ（任意）</label>
            <textarea id="memoInput" placeholder="持ち物、場所、URLなど">${escapeHtml(ev.memo)}</textarea>
          </div>
          <div class="err" id="formErr" style="display:none;"></div>
          <div class="modal-actions">
            <button class="btn ghost" id="cancelBtn">キャンセル</button>
            ${existing ? '<button class="btn danger" id="deleteBtn">削除</button>' : ''}
            <button class="btn primary" id="saveBtn">${existing ? '更新する' : '追加する'}</button>
          </div>
        </div>
      </div>`;

    let selectedCat = ev.category;

    document.getElementById('catSelect').addEventListener('click', (e) => {
      const opt = e.target.closest('.cat-option');
      if(!opt) return;
      selectedCat = opt.dataset.cat;
      document.querySelectorAll('.cat-option').forEach(o => o.classList.toggle('selected', o === opt));
    });

    document.getElementById('overlay').addEventListener('click', (e) => {
      if(e.target.id === 'overlay') closeModal();
    });
    document.getElementById('cancelBtn').addEventListener('click', closeModal);

    if(existing){
      document.getElementById('deleteBtn').addEventListener('click', async () => {
        events = events.filter(x => x.id !== existing.id);
        await saveEvents();
        closeModal();
        render();
      });
    }

    document.getElementById('saveBtn').addEventListener('click', async () => {
      const company = document.getElementById('companyInput').value.trim();
      const date = document.getElementById('dateInput').value;
      const time = document.getElementById('timeInput').value;
      const memo = document.getElementById('memoInput').value.trim();
      const errEl = document.getElementById('formErr');

      if(!company){
        errEl.textContent = '企業名・団体名を入力してください。';
        errEl.style.display = 'block';
        return;
      }
      if(!date){
        errEl.textContent = '日付を選択してください。';
        errEl.style.display = 'block';
        return;
      }

      if(existing){
        const target = events.find(x => x.id === existing.id);
        Object.assign(target, { category: selectedCat, company, date, time, memo });
      } else {
        events.push({
          id: uid(),
          category: selectedCat,
          company, date, time, memo,
          done: false
        });
      }
      await saveEvents();
      closeModal();
      render();
    });
  }

  function closeModal(){
    modalSlot.innerHTML = '';
    editingId = null;
  }

  function toInputDate(d){
    const y = d.getFullYear();
    const m = String(d.getMonth()+1).padStart(2,'0');
    const day = String(d.getDate()).padStart(2,'0');
    return `${y}-${m}-${day}`;
  }

  document.getElementById('openAddBtn').addEventListener('click', () => openModal(null));
  document.getElementById('openNotifyBtn').addEventListener('click', () => openNotifySettings());

  filtersEl.addEventListener('click', (e) => {
    const btn = e.target.closest('button[data-filter]');
    if(!btn) return;
    filter = btn.dataset.filter;
    document.querySelectorAll('#filters button').forEach(b => b.classList.toggle('active', b === btn));
    renderList();
  });

  listSlot.addEventListener('click', async (e) => {
    const card = e.target.closest('.card');
    if(!card) return;
    const id = card.dataset.id;
    const action = e.target.closest('[data-action]')?.dataset.action;
    const ev = events.find(x => x.id === id);
    if(!ev) return;

    if(action === 'edit'){
      openModal(ev);
    } else if(action === 'toggle'){
      ev.done = !ev.done;
      await saveEvents();
      render();
    } else if(action === 'delete'){
      events = events.filter(x => x.id !== id);
      await saveEvents();
      render();
    }
  });

  (async function init(){
    await loadEvents();
    await loadSettings();
    render();
    updateBellIndicator();
    if(settings.enabled && typeof Notification !== 'undefined' && Notification.permission === 'granted'){
      startNotifyLoop();
    }
  })();

})();
</script>

</body>
</html>
