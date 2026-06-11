# obyvvat.github.io

<!DOCTYPE html>
<html lang="pl">
<head>
  <meta charset="UTF-8" />
  <title>mDokument – Demo</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />

  <!-- Prosty, "aplikacyjny" styl -->
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
    }

    body {
      background: #0f172a;        /* ciemne tło */
      color: #0f172a;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      padding: 16px;
    }

    .app-frame {
      width: 360px;
      max-width: 100%;
      background: #020617;
      border-radius: 28px;
      border: 1px solid #1f2937;
      box-shadow:
        0 0 0 4px #020617,
        0 24px 60px rgba(0, 0, 0, 0.65);
      overflow: hidden;
      color: #e5e7eb;
    }

    /* Górny pasek "aplikacji" */
    .status-bar {
      height: 32px;
      padding: 0 12px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      font-size: 11px;
      color: #9ca3af;
      background: linear-gradient(to bottom, #020617, #020617);
    }

    .status-left,
    .status-right {
      display: flex;
      align-items: center;
      gap: 6px;
    }

    .status-dot {
      width: 6px;
      height: 6px;
      border-radius: 999px;
      background: #22c55e;
    }

    .battery {
      width: 18px;
      height: 10px;
      border-radius: 3px;
      border: 1px solid #9ca3af;
      position: relative;
    }

    .battery::after {
      content: "";
      position: absolute;
      right: -3px;
      top: 2px;
      width: 2px;
      height: 6px;
      border-radius: 1px;
      background: #9ca3af;
    }

    .battery-level {
      height: 100%;
      width: 70%;
      background: #22c55e;
    }

    /* Pasek nagłówka dokumentu */
    .header {
      padding: 12px 16px 8px 16px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      border-bottom: 1px solid #1f2937;
      background: linear-gradient(135deg, #020617 0%, #111827 60%, #1f2937 100%);
    }

    .header-left {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .app-logo {
      width: 26px;
      height: 26px;
      border-radius: 7px;
      background: radial-gradient(circle at 30% 30%, #38bdf8, #0369a1);
      display: flex;
      align-items: center;
      justify-content: center;
      font-weight: 700;
      font-size: 14px;
      color: #e5e7eb;
    }

    .header-title {
      display: flex;
      flex-direction: column;
      gap: 2px;
    }

    .header-title-main {
      font-size: 13px;
      font-weight: 600;
      letter-spacing: 0.03em;
      text-transform: uppercase;
      color: #f9fafb;
    }

    .header-title-sub {
      font-size: 11px;
      color: #9ca3af;
    }

    .header-pill {
      padding: 4px 10px;
      border-radius: 999px;
      background: rgba(15, 23, 42, 0.85);
      border: 1px solid rgba(148, 163, 184, 0.35);
      font-size: 11px;
      color: #e5e7eb;
    }

    /* Główna karta dokumentu */
    .card-wrapper {
      padding: 14px 14px 18px 14px;
      background: radial-gradient(circle at top, #1f2937, #020617 55%);
    }

    .card {
      background: linear-gradient(145deg, #f9fafb 0%, #e5e7eb 40%, #d1d5db 100%);
      border-radius: 22px;
      padding: 14px 14px 12px 14px;
      box-shadow: 0 18px 40px rgba(15, 23, 42, 0.75);
      color: #111827;
      position: relative;
      overflow: hidden;
    }

    .card::before {
      content: "";
      position: absolute;
      inset: 0;
      background:
        radial-gradient(circle at -10% -10%, rgba(56, 189, 248, 0.22), transparent 55%),
        radial-gradient(circle at 110% 110%, rgba(59, 130, 246, 0.2), transparent 60%);
      opacity: 0.9;
      pointer-events: none;
    }

    .card-inner {
      position: relative;
      z-index: 1;
    }

    .card-top {
      display: flex;
      justify-content: space-between;
      align-items: flex-start;
      margin-bottom: 10px;
    }

    .card-top-left {
      display: flex;
      flex-direction: column;
      gap: 4px;
    }

    .doc-name {
      font-size: 11px;
      text-transform: uppercase;
      letter-spacing: 0.12em;
      color: #6b7280;
      font-weight: 600;
    }

    .doc-type {
      font-size: 15px;
      font-weight: 700;
      letter-spacing: 0.04em;
      text-transform: uppercase;
      color: #111827;
    }

    .badge {
      margin-top: 4px;
      display: inline-flex;
      align-items: center;
      gap: 6px;
      padding: 2px 8px;
      border-radius: 999px;
      border: 1px solid rgba(31, 41, 55, 0.18);
      background: rgba(249, 250, 251, 0.8);
      font-size: 10px;
      color: #374151;
    }

    .badge-dot {
      width: 6px;
      height: 6px;
      border-radius: 999px;
      background: #22c55e;
    }

    .coat {
      width: 32px;
      height: 40px;
      border-radius: 10px;
      border: 1px solid rgba(31, 41, 55, 0.25);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 9px;
      font-weight: 700;
      text-align: center;
      background: rgba(248, 250, 252, 0.8);
      color: #111827;
    }

    /* Sekcja z danymi */
    .card-content {
      display: flex;
      gap: 10px;
    }

    .photo {
      width: 80px;
      height: 96px;
      border-radius: 14px;
      overflow: hidden;
      border: 1px solid rgba(31, 41, 55, 0.35);
      background: #e5e7eb;
      flex-shrink: 0;
    }

    .photo img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .fields {
      flex: 1;
      display: flex;
      flex-direction: column;
      gap: 6px;
    }

    .field {
      display: flex;
      flex-direction: column;
      gap: 1px;
    }

    .field-label {
      font-size: 9px;
      text-transform: uppercase;
      letter-spacing: 0.15em;
      color: #6b7280;
      font-weight: 600;
    }

    .field-value {
      font-size: 13px;
      font-weight: 600;
      color: #111827;
      line-height: 1.2;
    }

    .field-row {
      display: flex;
      gap: 10px;
    }

    .field-row .field {
      flex: 1;
    }

    /* Dół karty: PESEL, ważność, kod QR */
    .card-bottom {
      margin-top: 10px;
      padding-top: 8px;
      border-top: 1px dashed rgba(148, 163, 184, 0.7);
      display: flex;
      align-items: flex-end;
      justify-content: space-between;
      gap: 8px;
    }

    .bottom-left {
      display: flex;
      flex-direction: column;
      gap: 6px;
    }

    .chip {
      width: 46px;
      height: 30px;
      border-radius: 8px;
      background: linear-gradient(135deg, #e5e7eb, #9ca3af);
      border: 1px solid rgba(31, 41, 55, 0.35);
      display: flex;
      align-items: center;
      justify-content: center;
      position: relative;
      overflow: hidden;
    }

    .chip-lines {
      width: 80%;
      height: 60%;
      border-radius: 6px;
      border: 1px solid rgba(75, 85, 99, 0.7);
      position: relative;
    }

    .chip-lines::before,
    .chip-lines::after {
      content: "";
      position: absolute;
      inset: 45% 0;
      border-top: 1px solid rgba(75, 85, 99, 0.7);
    }

    .doc-meta {
      display: flex;
      gap: 16px;
      margin-top: 2px;
    }

    .doc-meta-block {
      display: flex;
      flex-direction: column;
      gap: 1px;
    }

    .doc-meta-label {
      font-size: 8px;
      text-transform: uppercase;
      letter-spacing: 0.15em;
      color: #6b7280;
      font-weight: 600;
    }

    .doc-meta-value {
      font-size: 11px;
      font-weight: 600;
      color: #111827;
    }

    .qr {
      width: 64px;
      height: 64px;
      border-radius: 10px;
      border: 1px solid rgba(31, 41, 55, 0.4);
      background: repeating-linear-gradient(
        45deg,
        #020617,
        #020617 3px,
        #111827 3px,
        #111827 6px
      );
      display: flex;
      align-items: center;
      justify-content: center;
      position: relative;
      overflow: hidden;
    }

    .qr-inner {
      width: 48px;
      height: 48px;
      background:
        radial-gradient(circle at 10% 10%, #f9fafb 0, #f9fafb 3px, transparent 3px),
        radial-gradient(circle at 90% 10%, #f9fafb 0, #f9fafb 3px, transparent 3px),
        radial-gradient(circle at 10% 90%, #f9fafb 0, #f9fafb 3px, transparent 3px),
        radial-gradient(circle at 90% 90%, #f9fafb 0, #f9fafb 3px, transparent 3px),
        repeating-linear-gradient(0deg, transparent, transparent 3px, #f9fafb 3px, #f9fafb 4px),
        repeating-linear-gradient(90deg, transparent, transparent 3px, #f9fafb 3px, #f9fafb 4px);
      mix-blend-mode: screen;
      opacity: 0.95;
    }

    /* Dolny pasek aplikacji */
    .footer {
      padding: 8px 18px 14px 18px;
      border-top: 1px solid #1f2937;
      display: flex;
      align-items: center;
      justify-content: space-between;
      background: radial-gradient(circle at top, #0f172a, #020617 60%);
      font-size: 11px;
      color: #9ca3af;
    }

    .footer-left {
      display: flex;
      flex-direction: column;
      gap: 2px;
    }

    .footer-label {
      text-transform: uppercase;
      letter-spacing: 0.14em;
      font-size: 9px;
      color: #6b7280;
    }

    .footer-value {
      font-weight: 500;
      color: #e5e7eb;
    }

    .footer-button {
      padding: 6px 12px;
      border-radius: 999px;
      border: 1px solid rgba(148, 163, 184, 0.4);
      background: radial-gradient(circle at 30% 0, #1d4ed8, #0b1120);
      color: #e5e7eb;
      font-size: 11px;
      font-weight: 500;
      display: flex;
      align-items: center;
      gap: 6px;
      cursor: default;
      user-select: none;
    }

    .footer-dot {
      width: 6px;
      height: 6px;
      border-radius: 999px;
      background: #22c55e;
      box-shadow: 0 0 8px rgba(34, 197, 94, 0.9);
    }

    @media (max-width: 400px) {
      body {
        padding: 8px;
      }

      .app-frame {
        width: 100%;
        border-radius: 24px;
      }
    }
  </style>
</head>
<body>
  <div class="app-frame">
    <!-- Pasek statusu (czas, sieć, bateria) -->
    <div class="status-bar">
      <div class="status-left">
        <span>9:41</span>
      </div>
      <div class="status-right">
        <div class="status-dot"></div>
        <span>LTE</span>
        <div class="battery">
          <div class="battery-level"></div>
        </div>
      </div>
    </div>

    <!-- Górny nagłówek aplikacji -->
    <div class="header">
      <div class="header-left">
        <div class="app-logo">m</div>
        <div class="header-title">
          <span class="header-title-main">mDokument</span>
          <span class="header-title-sub">Twoje dane w jednym miejscu</span>
        </div>
      </div>
      <div class="header-pill">
        Dokument aktywny
      </div>
    </div>

    <!-- Główna karta -->
    <div class="card-wrapper">
      <div class="card">
        <div class="card-inner">
          <div class="card-top">
            <div class="card-top-left">
              <span class="doc-name">Rzeczpospolita Polska</span>
              <span class="doc-type">Dokument tożsamości</span>
              <div class="badge">
                <span class="badge-dot"></span>
                <span>Potwierdzenie danych</span>
              </div>
            </div>
            <div class="coat">
              RP<br />PL
            </div>
          </div>

          <div class="card-content">
            <!-- TWOJE ZDJĘCIE -->
            <div class="photo">
              <!-- Podmień src na swoją fotkę -->
              <img src="img/profile.jpg" alt="Zdjęcie posiadacza dokumentu" />
            </div>

            <!-- DANE OSOBOWE -->
            <div class="fields">
              <div class="field">
                <span class="field-label">Imię (imiona)</span>
                <span class="field-value">Anna Maria</span>
              </div>

              <div class="field">
                <span class="field-label">Nazwisko</span>
                <span class="field-value">Kowalska</span>
              </div>

              <div class="field-row">
                <div class="field">
                  <span class="field-label">Data urodzenia</span>
                  <span class="field-value">15.04.2002</span>
                </div>
                <div class="field">
                  <span class="field-label">Obywatelstwo</span>
                  <span class="field-value">POL</span>
                </div>
              </div>

              <div class="field-row">
                <div class="field">
                  <span class="field-label">Seria i nr</span>
                  <span class="field-value">ABC123456</span>
                </div>
                <div class="field">
                  <span class="field-label">Data wydania</span>
                  <span class="field-value">01.06.2024</span>
                </div>
              </div>
            </div>
          </div>

          <!-- Dół karty: PESEL, ważność, "chip", QR -->
          <div class="card-bottom">
            <div class="bottom-left">
              <div class="chip">
                <div class="chip-lines"></div>
              </div>

              <div class="doc-meta">
                <div class="doc-meta-block">
                  <span class="doc-meta-label">PESEL</span>
                  <span class="doc-meta-value">02041512345</span>
                </div>
                <div class="doc-meta-block">
                  <span class="doc-meta-label">Ważny do</span>
                  <span class="doc-meta-value">15.04.2032</span>
                </div>
              </div>
            </div>

            <div class="qr">
              <div class="qr-inner"></div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Dolny pasek aplikacji -->
    <div class="footer">
      <div class="footer-left">
        <span class="footer-label">Tryb prezentacji</span>
        <span class="footer-value">Dane do potwierdzenia tożsamości</span>
      </div>
      <div class="footer-button">
        <span class="footer-dot"></span>
        <span>Aktywny dokument</span>
      </div>
    </div>
  </div>
</body>
</html>
