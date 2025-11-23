# Separar features y target
X = df_encoded.drop(columns=['Churn_Yes', 'Total.Day', 'phone.PhoneService_Yes', 'phone.MultipleLines_No phone service', 'internet.InternetService_No', 'account.Charges.Total'])
y = df_encoded['Churn_Yes']

# Dividir en entrenamiento y prueba
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.3, random_state=42, stratify=y
)

# Normalizar con StandardScaler
scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)

# Balancear con SMOTE
smote = SMOTE(random_state=42)
X_train_bal, y_train_bal = smote.fit_resample(X_train_scaled, y_train)

# --- Modelo 1: Regresión Logística ---
print("--- Regresión Logística ---")
lr = LogisticRegression(random_state=42, max_iter=1000)
lr.fit(X_train_bal, y_train_bal)

y_pred_lr = lr.predict(X_test_scaled)
y_prob_lr = lr.predict_proba(X_test_scaled)[:, 1]

print("Exactitud:", accuracy_score(y_test, y_pred_lr))
print("ROC AUC:", roc_auc_score(y_test, y_prob_lr))
print("Matriz de Confusión:\n", confusion_matrix(y_test, y_pred_lr))
print(classification_report(y_test, y_pred_lr))

# --- Modelo 2: Random Forest ---
print("\n--- Random Forest ---")
rf = RandomForestClassifier(random_state=42)
rf.fit(X_train_bal, y_train_bal)

y_pred_rf = rf.predict(X_test_scaled)
y_prob_rf = rf.predict_proba(X_test_scaled)[:, 1]

print("Exactitud:", accuracy_score(y_test, y_pred_rf))
print("ROC AUC:", roc_auc_score(y_test, y_prob_rf))
print("Matriz de Confusión:\n", confusion_matrix(y_test, y_pred_rf))
print(classification_report(y_test, y_pred_rf))
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
      <h1>Automatización contable con IA</h1>
      <p>Subí tu archivo CSV, mapeá columnas y generá asientos en segundos.</p>
      <div class="cta-row">
        <button id="btn-login" class="btn outline">Login / Register</button>
        <a class="btn primary" href="#contact">Contratar</a>
      </div>
    </section>

    <section class="section card">
      <h2>Cargar CSV</h2>
      <input id="file-input" type="file" accept=".csv" />
      <div id="preview-controls" class="cols hidden">
        <div><label>Monto</label><select id="col-amount"></select></div>
        <div><label>Descripción</label><select id="col-desc"></select></div>
        <div><label>Moneda</label><select id="col-curr"></select></div>
        <div><label>Tipo</label><select id="col-type"></select></div>
      </div>

      <div id="table-wrap" class="table-wrap hidden"></div>

      <div class="actions hidden" id="generate-row">
        <button id="generate-entries" class="btn primary">Generar Asientos</button>
      </div>
    </section>

    <section class="section card hidden" id="entries-section">
      <h2>Asientos generados</h2>
      <div id="entries-wrap"></div>
      <div class="actions">
        <button id="export-csv" class="btn">Exportar CSV</button>
        <button id="export-xlsx" class="btn">Exportar Excel</button>
        <button id="export-pdf" class="btn">Exportar PDF</button>
        <button id="download-original" class="btn outline">CSV original</button>
      </div>
    </section>

    <section class="section card" id="services">
      <h2>Servicios</h2>
      <ul>
        <li>Automatización contable con IA Generativa</li>
        <li>Modelos de clasificación y anomalías</li>
        <li>Sistemas multimoneda</li>
        <li>Dashboards financieros</li>
        <li>Integraciones API</li>
        <li>Desarrollo web / consultoría</li>
      </ul>
    </section>

    <section class="section card" id="plans">
      <h2>Planes</h2>
      <div class="plans">
        <div class="plan"><h3>Básico</h3><p>USD 300 / mes</p></div>
        <div class="plan highlighted"><h3>Pro</h3><p>USD 900 / mes</p></div>
        <div class="plan"><h3>Empresa</h3><p>USD 2000 / mes</p></div>
      </div>
    </section>

    <section class="section card" id="contact">
      <h2>Contacto</h2>
      <p>WhatsApp: 2613991663</p>
      <p>Email: priluskyezequielsamuel@gmail.com</p>
    </section>
  </main>

  <footer class="footer">© 2025 FINANZAS IA — Ezequiel S. Prilusky</footer>

  <script src="app.js"></script>
</body>
</html>.                  :root{
  --bg:#0a1a33;
  --card:#0f2345;
  --accent:#3a5ed7;
  --muted:#9fb0df;
}

body{
  margin:0;
  background:var(--bg);
  color:white;
  font-family:Arial, sans-serif;
}

.site-header{
  display:flex;
  justify-content:space-between;
  padding:20px;
  border-bottom:1px solid #162b4f;
}

.hero{
  padding:60px 20px;
  text-align:center;
}

.btn{
  padding:10px 18px;
  border-radius:8px;
  background:var(--accent);
  color:white;
  border:0;
  cursor:pointer;
}

.btn.outline{
  background:transparent;
  border:1px solid var(--accent);
}

.section{
  max-width:900px;
  margin:auto;
  padding:20px;
}

.card{
  background:var(--card);
  padding:20px;
  border-radius:12px;
}

.table-wrap{
  margin-top:20px;
  overflow:auto;
}

.cols{
  display:grid;
  grid-template-columns:repeat(4,1fr);
  gap:10px;
  margin-top:12px;
}

.hidden{
  display:none;
}

.plans{
  display:flex;
  gap:20px;
}

.plan{
  flex:1;
  padding:20px;
  background:#102a57;
  border-radius:12px;
  text-align:center;
}

.plan.highlighted{
  border:2px solid var(--accent);
}

.footer{
  text-align:center;
  padding:20px;
  color:var(--muted);
}                            