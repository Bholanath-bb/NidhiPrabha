# NidhiPrabha
Nidhi's contact card
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Nidhi Prabha · Sambodhi</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>

<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --ink: #1a1410;
    --sand: #f5f0e8;
    --warm: #c8a96e;
    --muted: #8a7f72;
    --line: rgba(26,20,16,0.12);
  }

  html, body {
    min-height: 100vh;
    background: var(--sand);
    font-family: 'DM Sans', sans-serif;
    color: var(--ink);
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 2rem 1rem;
  }

  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background:
      radial-gradient(ellipse 80% 60% at 20% 10%, rgba(200,169,110,0.13) 0%, transparent 60%),
      radial-gradient(ellipse 60% 80% at 80% 90%, rgba(200,169,110,0.09) 0%, transparent 60%);
    pointer-events: none;
    z-index: 0;
  }

  .card {
    position: relative;
    z-index: 1;
    background: #fffef9;
    border: 1px solid var(--line);
    border-radius: 2px;
    max-width: 420px;
    width: 100%;
    padding: 3rem 2.5rem 2.5rem;
    box-shadow:
      0 1px 2px rgba(0,0,0,0.04),
      0 8px 32px rgba(0,0,0,0.07),
      0 32px 64px rgba(0,0,0,0.05);
    animation: rise 0.7s cubic-bezier(0.22,1,0.36,1) both;
  }

  @keyframes rise {
    from { opacity: 0; transform: translateY(28px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  .top-rule {
    width: 100%;
    height: 3px;
    background: linear-gradient(90deg, var(--warm), #e8d5a8, var(--warm));
    position: absolute;
    top: 0; left: 0;
    border-radius: 2px 2px 0 0;
  }

  .org-tag {
    font-family: 'DM Sans', sans-serif;
    font-size: 0.65rem;
    font-weight: 500;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--warm);
    margin-bottom: 1.6rem;
  }

  .name {
    font-family: 'Cormorant Garamond', serif;
    font-size: 2.4rem;
    font-weight: 300;
    line-height: 1.1;
    letter-spacing: -0.01em;
    color: var(--ink);
    margin-bottom: 0.35rem;
  }

  .name em {
    font-style: italic;
    font-weight: 400;
  }

  .title {
    font-size: 0.78rem;
    font-weight: 400;
    color: var(--muted);
    letter-spacing: 0.04em;
    margin-bottom: 2.2rem;
    line-height: 1.5;
  }

  .divider {
    width: 100%;
    height: 1px;
    background: var(--line);
    margin-bottom: 1.8rem;
  }

  .contacts {
    display: flex;
    flex-direction: column;
    gap: 0.75rem;
    margin-bottom: 2rem;
  }

  .contact-row {
    display: flex;
    align-items: center;
    gap: 0.85rem;
    text-decoration: none;
    color: var(--ink);
    font-size: 0.82rem;
    font-weight: 400;
    transition: color 0.2s;
  }

  .contact-row:hover { color: var(--warm); }

  .contact-row svg {
    width: 14px; height: 14px;
    flex-shrink: 0;
    opacity: 0.45;
  }

  .contact-row:hover svg { opacity: 0.8; }

  .actions {
    display: flex;
    flex-direction: column;
    gap: 0.75rem;
    margin-bottom: 2.2rem;
  }

  .btn {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 0.6rem;
    padding: 0.85rem 1.5rem;
    border-radius: 2px;
    font-family: 'DM Sans', sans-serif;
    font-size: 0.78rem;
    font-weight: 500;
    letter-spacing: 0.06em;
    text-transform: uppercase;
    cursor: pointer;
    text-decoration: none;
    transition: all 0.2s;
    border: none;
  }

  .btn-primary {
    background: var(--ink);
    color: #fff;
  }

  .btn-primary:hover {
    background: #2d2520;
    transform: translateY(-1px);
    box-shadow: 0 4px 16px rgba(0,0,0,0.15);
  }

  .btn-secondary {
    background: transparent;
    color: var(--ink);
    border: 1px solid var(--line);
  }

  .btn-secondary:hover {
    border-color: var(--warm);
    color: var(--warm);
    transform: translateY(-1px);
  }

  .btn svg { width: 16px; height: 16px; flex-shrink: 0; }

  .qr-section {
    border-top: 1px solid var(--line);
    padding-top: 1.6rem;
    display: flex;
    align-items: center;
    gap: 1.2rem;
  }

  .qr-box {
    width: 72px;
    height: 72px;
    flex-shrink: 0;
    border: 1px solid var(--line);
    padding: 4px;
    border-radius: 2px;
    background: #fff;
  }

  .qr-box canvas, .qr-box img { width: 100% !important; height: 100% !important; }

  .qr-label {
    font-size: 0.7rem;
    color: var(--muted);
    line-height: 1.55;
  }

  .qr-label strong {
    display: block;
    font-size: 0.73rem;
    font-weight: 500;
    color: var(--ink);
    margin-bottom: 0.2rem;
  }

  @media (max-width: 480px) {
    .card { padding: 2.4rem 1.75rem 2rem; }
    .name { font-size: 2rem; }
  }
</style>
</head>
<body>

<div class="card">
  <div class="top-rule"></div>

  <div class="org-tag">Sambodhi · Social Sector</div>

  <h1 class="name"><em>Nidhi</em> Prabha</h1>
  <p class="title">Senior Manager, Capacity Building</p>

  <div class="divider"></div>

  <div class="contacts">
    <a class="contact-row" href="mailto:prabha.nidhi@outlook.com">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6">
        <rect x="2" y="4" width="20" height="16" rx="2"/>
        <path d="M2 7l10 7 10-7"/>
      </svg>
      prabha.nidhi@outlook.com
    </a>
    <a class="contact-row" href="tel:+919971650149">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6">
        <path d="M22 16.92v3a2 2 0 01-2.18 2 19.79 19.79 0 01-8.63-3.07A19.5 19.5 0 013.07 9.81 19.79 19.79 0 01.1 1.18 2 2 0 012.1 0h3a2 2 0 012 1.72 12.84 12.84 0 00.7 2.81 2 2 0 01-.45 2.11L6.09 7.91a16 16 0 006 6l1.27-1.27a2 2 0 012.11-.45 12.84 12.84 0 002.81.7A2 2 0 0122 14.92z"/>
      </svg>
      +91 99716 50149
    </a>
    <a class="contact-row" href="https://www.linkedin.com/in/nidhi-prabha" target="_blank">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6">
        <rect x="2" y="2" width="20" height="20" rx="2"/>
        <path d="M7 10v7M7 7v.01M12 10v7M12 13a3 3 0 016 0v4"/>
      </svg>
      linkedin.com/in/nidhi-prabha
    </a>
  </div>

  <div class="actions">
    <button class="btn btn-primary" onclick="downloadVCard()">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
        <path d="M20 21v-2a4 4 0 00-4-4H8a4 4 0 00-4 4v2"/>
        <circle cx="12" cy="7" r="4"/>
      </svg>
      Save Contact
    </button>
    <a class="btn btn-secondary" href="https://www.linkedin.com/in/nidhi-prabha" target="_blank">
      <svg viewBox="0 0 24 24" fill="currentColor" width="16" height="16">
        <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
      </svg>
      Connect on LinkedIn
    </a>
  </div>

  <div class="qr-section">
    <div class="qr-box" id="qrcode"></div>
    <div class="qr-label">
      <strong>Scan to connect</strong>
      Opens this card on any phone. Save contact or connect on LinkedIn directly.
    </div>
  </div>
</div>

<script>
function downloadVCard() {
  const vcard = [
    'BEGIN:VCARD',
    'VERSION:3.0',
    'FN:Nidhi Prabha',
    'N:Prabha;Nidhi;;;',
    'ORG:Sambodhi',
    'TITLE:Senior Manager, Capacity Building',
    'EMAIL;TYPE=INTERNET:prabha.nidhi@outlook.com',
    'TEL;TYPE=CELL:+91-9971650149',
    'URL:https://www.linkedin.com/in/nidhi-prabha',
    'END:VCARD'
  ].join('\r\n');

  const blob = new Blob([vcard], { type: 'text/vcard' });
  const url = URL.createObjectURL(blob);
  const a = document.createElement('a');
  a.href = url;
  a.download = 'Nidhi_Prabha.vcf';
  a.click();
  URL.revokeObjectURL(url);
}

// Generate QR pointing to this page (self-referential via LinkedIn as fallback)
new QRCode(document.getElementById('qrcode'), {
  text: 'https://drive.google.com/uc?export=view&id=1bwaAvKo13_jCRpOrUvm2U0KckKlz4k-h',
  width: 64,
  height: 64,
  colorDark: '#1a1410',
  colorLight: '#ffffff',
  correctLevel: QRCode.CorrectLevel.M
});
</script>
</body>
</html>
