<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>FINANZAS IA — App</title>
  <link rel="stylesheet" href="style.css" />
  <!-- libs -->
  <script src="https://cdn.jsdelivr.net/npm/papaparse@5.4.1/papaparse.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf-autotable/3.5.28/jspdf.plugin.autotable.min.js"></script>
</head>
<body>
  <header class="site-header">
    <div class="brand">
      <!-- LOGO placeholder: reemplaza por <img src="assets/logo.png"> cuando tengas el logo -->
      <div id="logo-placeholder">FINANZAS IA</div>
      <div class="tag">Tecnología + Análisis Financiero + IA</div>
    </div>
    <nav class="main-nav">
      <a href="#services">Servicios</a>
      <a href="#plans">Planes</a>
      <a href="#app">App</a>
      <a href="#contact">Contacto</a>
    </nav>
  </header>

  <main>
    <section class="hero" id="app">
      <div class="hero-inner">
        <h1>Automatización contable con IA</h1>
        <p>Subí tus transacciones (.csv) — mapeá columnas — generá asientos y exportá en segundos.</p>
        <div class="cta-row">
          <button id="btn-login" class="btn outline">Login / Register</button>
          <a class="btn primary" href="#contact">Contratar</a>
        </div>
      </div>
    </section>

    <section class="section card" id="uploader">
      <h2>1 · Cargar CSV</h2>
      <input id="file-input" type="file" accept=".csv" />
      <div id="sample-help" class="muted">Ej: date, description, amount, currency, type</div>

      <div id="preview-controls" class="cols hidden">
        <div>
          <label>Columna Monto</label>
          <select id="col-amount"></select>
        </div>
        <div>
          <label>Columna Descripción</label>
          <select id="col-desc"></select>
        </div>
        <div>
          <label>Columna Moneda</label>
          <select id="col-curr"></select>
        </div>
        <div>
          <label>Columna Tipo</label>
          <select id="col-type"></select>
        </div>
      </div>

      <div id="table-wrap" class="table-wrap hidden"></div>
      <div class="actions hidden" id="generate-row">
        <button id="generate-entries" class="btn primary">Generar Asientos</button>
      </div>
    </section>

    <section class="section card hidden" id="entries-section">
      <h2>2 · Asientos generados</h2>
      <div id="entries-wrap"></div>
      <div class="actions">
        <button id="export-csv" class="btn">Exportar CSV</button>
        <button id="export-xlsx" class="btn">Exportar Excel</button>
        <button id="export-pdf" class="btn">Exportar PDF</button>
        <button id="download-original" class="btn outline">Descargar CSV original</button>
      </div>
    </section>

    <section class="section card" id="services">
      <h2>Servicios</h2>
      <ul class="services-list">
        <li>Automatización contable con IA generativa</li>
        <li>Modelos de clasificación y detección de anomalías</li>
        <li>Sistemas multimoneda y reportes automáticos</li>
        <li>Dashboards financieros</li>
        <li>Integraciones API / Backend</li>
        <li>Desarrollo web y consultoría</li>
      </ul>
    </section>

    <section class="section card" id="plans">
      <h2>Planes</h2>
      <div class="plans">
        <div class="plan">
          <h3>Plan Básico</h3>
          <p>USD 300 / mes</p>
          <button class="btn">Contratar</button>
        </div>
        <div class="plan highlighted">
          <h3>Plan Pro</h3>
          <p>USD 900 / mes</p>
          <button class="btn">Contratar</button>
        </div>
        <div class="plan">
          <h3>Plan Empresa</h3>
          <p>USD 2000 / mes</p>
          <button class="btn">Contratar</button>
        </div>
      </div>
    </section>

    <section class="section card" id="contact">
      <h2>Contacto y Cobro</h2>
      <p>WhatsApp: <a href="https://wa.me/5492613991663" target="_blank">+54 9 261 399 1663</a></p>
      <p>Email: <a href="mailto:priluskyezequielsamuel@gmail.com">priluskyezequielsamuel@gmail.com</a></p>

      <div class="payment-row">
        <div class="payment">
          <h4>Mercado Pago</h4>
          <p>Link de pago (placeholder): <a id="mp-link" href="#" target="_blank">https://mpago.la/finanzasIA</a></p>
          <button id="mp-pay" class="btn">Pagar con Mercado Pago</button>
        </div>
        <div class="payment">
          <h4>Transferencia Bancaria</h4>
          <p>Alias (temporal): <strong>finanzas.ia.prilusky.mp</strong></p>
          <p>Indica referencia: <em>Pago - Servicio</em></p>
        </div>
      </div>

    </section>

  </main>

  <footer class="footer">
    <div>© 2025 FINANZAS IA — Ezequiel S. Prilusky</div>
    <div>www.finanazas.com.ar</div>
  </footer>

  <!-- Auth modal (demo) -->
  <div id="auth-modal" class="modal hidden">
    <div class="modal-body">
      <h3>Login / Register</h3>
      <input id="auth-email" placeholder="Email" />
      <input id="auth-name" placeholder="Nombre (solo register)" />
      <input id="auth-pass" placeholder="Password" type="password" />
      <div class="modal-actions">
        <button id="btn-register" class="btn outline">Register</button>
        <button id="btn-login-modal" class="btn primary">Login</button>
        <button id="btn-close-modal" class="btn">Cerrar</button>
      </div>
      <small class="muted">Si no hay backend, el modo demo guardará token local.</small>
    </div>
  </div>

  <script src="app.js"></script>
</body>
</html>
            
                 /* style.css - Azul tech theme */
:root{
  --bg:#0a1a33; --card:#0f2345; --accent:#3a5ed7; --muted:#9fb0df;
  --radius:12px; --pad:18px;
}
*{box-sizing:border-box;font-family:Inter,Arial,sans-serif}
body{margin:0;background:var(--bg);color:#fff}
.site-header{display:flex;justify-content:space-between;align-items:center;padding:18px 28px;border-bottom:1px solid #14243b}
.brand{display:flex;flex-direction:column}
#logo-placeholder{font-size:18px;font-weight:700;font-style:italic}
.tag{font-size:12px;color:var(--muted)}
.main-nav a{color:#cfe1ff;margin-left:12px;text-decoration:none}
.hero{padding:60px 20px;text-align:center}
.hero-inner{max-width:900px;margin:auto}
.hero h1{font-size:36px;margin:0 0 8px;font-style:italic}
.hero p{color:var(--muted);margin:0 0 16px}
.cta-row{display:flex;gap:10px;justify-content:center;margin-top:12px}
.btn{background:var(--accent);color:white;padding:10px 16px;border-radius:8px;border:0;cursor:pointer;text-decoration:none}
.btn.outline{background:transparent;border:1px solid rgba(255,255,255,0.08)}
.btn.primary{background:#2853d6}
.section{max-width:980px;margin:22px auto;padding:0 16px}
.card{background:var(--card);padding:var(--pad);border-radius:12px;margin-bottom:18px;box-shadow:0 8px 24px rgba(0,0,0,0.3)}
.table-wrap{overflow:auto}
.cols{display:grid;grid-template-columns:repeat(4,1fr);gap:12px;margin-top:12px}
.table-wrap table{width:100%;border-collapse:collapse;color:#dfefff}
.table-wrap th, .table-wrap td{padding:8px;border-bottom:1px solid rgba(255,255,255,0.03)}
.actions{margin-top:12px;display:flex;gap:8px;flex-wrap:wrap}
.hidden{display:none}
.services-list{list-style:disc;margin-left:18px}
.plans{display:flex;gap:12px;flex-wrap:wrap}
.plan{flex:1;background:#102444;padding:18px;border-radius:10px;text-align:center}
.plan.highlighted{border:2px solid var(--accent);transform:scale(1.03)}
.payment-row{display:flex;gap:18px;flex-wrap:wrap;margin-top:12px}
.payment{background:#0e2848;padding:12px;border-radius:10px}
.footer{text-align:center;padding:20px;color:var(--muted);border-top:1px solid #14243b;margin-top:30px}
.modal{position:fixed;left:0;top:0;width:100%;height:100%;display:flex;align-items:center;justify-content:center;background:rgba(0,0,0,0.6)}
.modal-body{background:#07122a;padding:20px;border-radius:10px;width:320px}
.modal-body input{width:100%;padding:8px;margin:6px 0;border-radius:6px;border:1px solid rgba(255,255,255,0.06);background:#09172e;color:white}
.modal-actions{display:flex;gap:8px;justify-content:flex-end;margin-top:8px}
.muted{color:var(--muted);font-size:12px}
@media(max-width:880px){.cols{grid-template-columns:repeat(2,1fr)}.plans{flex-direction:column}}.                               // app.js - frontend behavior (no backend required)
let originalData = null;
let headers = [];

const fileInput = document.getElementById('file-input');
const previewControls = document.getElementById('preview-controls');
const tableWrap = document.getElementById('table-wrap');
const entriesWrap = document.getElementById('entries-wrap');
const previewControlsEl = document.getElementById('preview-controls');
const entriesSection = document.getElementById('entries-section');

const selAmount = document.getElementById('col-amount');
const selDesc = document.getElementById('col-desc');
const selCurr = document.getElementById('col-curr');
const selType = document.getElementById('col-type');

const authModal = document.getElementById('auth-modal');
const btnLogin = document.getElementById('btn-login');
const btnCloseModal = document.getElementById('btn-close-modal');
const btnRegister = document.getElementById('btn-register');
const btnLoginModal = document.getElementById('btn-login-modal');

btnLogin && btnLogin.addEventListener('click', ()=> authModal.classList.remove('hidden'));
btnCloseModal && btnCloseModal.addEventListener('click', ()=> authModal.classList.add('hidden'));

fileInput && fileInput.addEventListener('change', e=>{
  const file = e.target.files[0];
  if(!file) return;
  Papa.parse(file, { header:true, skipEmptyLines:true, complete: (res)=>{
    originalData = res.data;
    headers = res.meta.fields || [];
    if(!headers.length) return alert('CSV sin encabezados. Asegurate que la primera fila tenga nombres.');
    populateSelectors(headers);
    renderTable(originalData, headers);
    previewControlsEl.classList.remove('hidden');
    document.getElementById('generate-row').classList.remove('hidden');
  }});
});

function populateSelectors(hdrs){
  [selAmount, selDesc, selCurr, selType].forEach(sel=>{
    sel.innerHTML = '<option value="">-- Ninguno --</option>';
    hdrs.forEach(h=>{
      const opt = document.createElement('option'); opt.value = h; opt.textContent = h; sel.appendChild(opt);
    });
  });
  tryAutoSelect(selAmount, ['amount','monto','importe','total']);
  tryAutoSelect(selDesc, ['description','desc','detalle','concepto']);
  tryAutoSelect(selCurr, ['currency','moneda','curr']);
  tryAutoSelect(selType, ['type','tipo','transaction_type']);
}

function tryAutoSelect(sel, candidates){
  for(let i=0;i<sel.options.length;i++){
    const v = sel.options[i].value.toLowerCase();
    if(candidates.includes(v)){ sel.value = sel.options[i].value; break; }
  }
}

function renderTable(data, hdrs){
  document.getElementById('table-wrap').classList.remove('hidden');
  const table = document.createElement('table');
  const thead = document.createElement('thead'); const tr = document.createElement('tr');
  hdrs.forEach(h=>{ const th = document.createElement('th'); th.textContent = h; tr.appendChild(th); });
  thead.appendChild(tr); table.appendChild(thead);
  const tbody = document.createElement('tbody');
  data.slice(0,200).forEach(row=>{
    const r = document.createElement('tr');
    hdrs.forEach(h=> { const td = document.createElement('td'); td.textContent = row[h] ?? ''; r.appendChild(td); });
    tbody.appendChild(r);
  });
  table.appendChild(tbody);
  tableWrap.innerHTML=''; tableWrap.appendChild(table);
}

document.getElementById('generate-entries') && document.getElementById('generate-entries').addEventListener('click', ()=>{
  if(!originalData) return alert('Subí un CSV primero.');
  const A = selAmount.value; const D = selDesc.value; const C = selCurr.value; const T = selType.value;
  const entries = [];
  originalData.forEach(r=>{
    const raw = A ? r[A] : (r['amount']||r['monto']||r['importe']||0);
    let v = String(raw).replace(/[^0-9\-\.,]/g,'').replace(',','.');
    const amount = parseFloat(v) || 0;
    const desc = D ? r[D] : (r['description']||r['detalle']||'');
    const curr = C ? r[C] : (r['currency']||r['moneda']||'');
    let tipo = T ? String(r[T]||'').toLowerCase() : (amount < 0 ? 'compra' : 'venta');
    if(/comp|buy|purchase/i.test(tipo)) tipo='compra';
    else if(/ven|sale|ingr|invoice|venta/i.test(tipo)) tipo='venta';
    else tipo = amount < 0 ? 'compra' : 'venta';
    if(amount === 0) return;
    if(tipo === 'venta'){
      entries.push({ fecha: r['date']||r['fecha']||'', descripcion: desc, moneda: curr, debe: 'Clientes / Cta cte', haber: 'Ingresos / Ventas', monto: Math.abs(amount) });
    } else {
      entries.push({ fecha: r['date']||r['fecha']||'', descripcion: desc, moneda: curr, debe: 'Gastos / Compras', haber: 'Proveedores / Ctas x pagar', monto: Math.abs(amount) });
    }
  });
  window._generatedEntries = entries;
  renderEntries(entries);
  entriesSection.classList.remove('hidden');
});

function renderEntries(entries){
  entriesWrap.innerHTML = '';
  if(!entries.length){ entriesWrap.innerHTML = '<small>No se generaron asientos.</small>'; return; }
  entries.forEach((e,i)=>{
    const div = document.createElement('div'); div.className='entry card';
    div.innerHTML = `<strong>#${i+1}</strong> <small>${e.fecha} ${e.moneda ? ' — '+e.moneda : ''}</small>
      <div><em>${e.descripcion}</em></div>
      <div>DEBE: ${e.debe} — ${e.monto}</div>
      <div>HABER: ${e.haber} — ${e.monto}</div>
    `;
    entriesWrap.appendChild(div);
  });
}

// exports
document.getElementById('export-csv') && document.getElementById('export-csv').addEventListener('click', ()=>{
  const entries = window._generatedEntries || []; if(!entries.length) return alert('No hay asientos.');
  const hdrs = ['fecha','descripcion','moneda','debe','haber','monto'];
  const csv = [hdrs.join(',')].concat(entries.map(e=> hdrs.map(h=> `"${String(e[h] ?? '').replace(/"/g,'""')}"`).join(',') )).join('\n');
  downloadFile('asientos.csv', csv, 'text/csv');
});
document.getElementById('export-xlsx') && document.getElementById('export-xlsx').addEventListener('click', ()=>{
  const entries = window._generatedEntries || []; if(!entries.length) return alert('No hay asientos.');
  const ws = XLSX.utils.json_to_sheet(entries); const wb = XLSX.utils.book_new(); XLSX.utils.book_append_sheet(wb, ws, 'Asientos'); XLSX.writeFile(wb, 'asientos.xlsx');
});
document.getElementById('export-pdf') && document.getElementById('export-pdf').addEventListener('click', ()=>{
  const entries = window._generatedEntries || []; if(!entries.length) return alert('No hay asientos.');
  const { jsPDF } = window.jspdf; const doc = new jsPDF({unit:'pt',format:'a4'});
  const cols = ['#','fecha','descripcion','moneda','debe','haber','monto'];
  const rows = entries.map((e,i)=>[i+1,e.fecha,e.descripcion,e.moneda,e.debe,e.haber,e.monto]);
  doc.text('Asientos generados — Finanzas IA', 40, 40); doc.autoTable({ startY: 60, head:[cols], body: rows, styles:{fontSize:9} }); doc.save('asientos_generados.pdf');
});
document.getElementById('download-original') && document.getElementById('download-original').addEventListener('click', ()=>{
  const f = fileInput.files[0]; if(!f) return alert('Subí el CSV primero.'); const url = URL.createObjectURL(f); const a = document.createElement('a'); a.href = url; a.download = f.name; a.click(); URL.revokeObjectURL(url);
});
function downloadFile(name,data,type){ const blob = new Blob([data],{type}); const url = URL.createObjectURL(blob); const a = document.createElement('a'); a.href = url; a.download = name; a.click(); URL.revokeObjectURL(url); }

// demo IA local (cuando no hay backend)
document.getElementById('mp-pay') && document.getElementById('mp-pay').addEventListener('click', ()=>{
  alert('Placeholder Mercado Pago — reemplaza con tu link real cuando lo tengas.');
});

// auth demo (frontend-only if no backend)
async function registerDemo(email, pass, name){
  // try backend
  try {
    const res = await fetch('/auth/register', {method:'POST', headers:{'Content-Type':'application/json'}, body:JSON.stringify({email, password:pass, full_name:name})});
    if(res.ok){ const j=await res.json(); localStorage.setItem('fa_token', j.access_token); alert('Registrado y logueado'); authModal.classList.add('hidden'); return; }
  } catch(e){ /* no backend */ }
  // fallback demo token
  const token = btoa(JSON.stringify({email, name, iat:Date.now()}));
  localStorage.setItem('fa_token', token); alert('Modo demo: registrado localmente'); authModal.classList.add('hidden');
}
async function loginDemo(email, pass){
  try {
    const res = await fetch('/auth/token', {method:'POST', headers:{'Content-Type':'application/json'}, body:JSON.stringify({email, password:pass})});
    if(res.ok){ const j=await res.json(); localStorage.setItem('fa_token', j.access_token); alert('Logueado'); authModal.classList.add('hidden'); return; }
  } catch(e){}
  // fallback: accept anything in demo
  const token = btoa(JSON.stringify({email, iat:Date.now()}));
  localStorage.setItem('fa_token', token); alert('Modo demo: logueado localmente'); authModal.classList.add('hidden');
}
document.getElementById('btn-register') && document.getElementById('btn-register').addEventListener('click', ()=>{
  const email=document.getElementById('auth-email').value; const pass=document.getElementById('auth-pass').value; const name=document.getElementById('auth-name').value;
  if(!email||!pass) return alert('Email y password requeridos');
  registerDemo(email,pass,name);
});
document.getElementById('btn-login-modal') && document.getElementById('btn-login-modal').addEventListener('click', ()=>{
  const email=document.getElementById('auth-email').value; const pass=document.getElementById('auth-pass').value;
  if(!email||!pass) return alert('Email y password requeridos');
  loginDemo(email,pass);
});                               # Finanzas IA — Web App (GitHub Pages)

Archivos que deben estar en la raíz del repo:
- index.html
- style.css
- app.js

## Cómo publicar
1. Subir los archivos al repo público `Contabilidad-de-datos-`.
2. Settings -> Pages -> Branch = main, Folder = / (root). Save.
3. Esperar ~30-60s y abrir:
   https://ezequiel199899.github.io/Contabilidad-de-datos-/

## Reemplazos importantes
- Reemplazar placeholder Mercado Pago por tu link real en index.html (id=mp-link y en app.js).
- Agregar logo en `assets/logo.png` y reemplazar el placeholder en index.html.
- Si querés backend (auth / modelo), subir en `backend/` y ajustar fetch URLs.

## Notas de seguridad
- No subir archivos con DNI/CUIT ni información sensible.
- Mantener el repo público solo con código y documentación.               