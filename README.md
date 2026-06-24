```html
<!DOCTYPE html>
<html lang="he" dir="rtl">
<head>
<meta charset="UTF-8">
<!-- תומך שוליים ומניעת זום אוטומטי במובייל -->
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
<title>רוגע Infinite — שקט פנימי ביו-אדפטיבי ואינטראקטיבי</title>

<!-- ─── PWA & IOS NATIVE MOBILE META TAGS ─── -->
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<meta name="apple-mobile-web-app-title" content="רוגע Infinite">
<link rel="apple-touch-icon" href="https://img.icons8.com/flatcolor/512/breath.png">

<!-- הטמעת Webmanifest דינמית מובנית להגדרת התקנת אפליקציה עצמאית -->
<link rel="manifest" href="data:application/manifest+json;base64,eyJuYW1lIjogIlJvZ2EgSW5maW5pdGUiLCAic2hvcnRfbmFtZSI6ICJSb2dhIiwgInN0YXJ0X3VybCI6ICIuIiwgImRpc3BsYXkiOiAic3RhbmRhbG9uZSIsICJiYWNrZ3JvdW5kX2NvbG9yIjogIiMwMzA2MTEiLCAidGhlbWVfY29sb3IiOiAiIzAzMDYxMSIsICJpY29ucyI6IFt7InNyYyI6ICJodHRwczovL2ltZy5pY29uczgubmV0L2ZsYXRjb2xvci81MTIvYnJlYXRoLnBuZyIsICJzaXplcyI6ICI1MTJ4NTEyIiwgInR5cGUiOiAiaW1hZ2UvcG5nIn1dfQ==">

<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Heebo:wght@100;300;400;500;700;900&display=swap" rel="stylesheet">

<!-- טעינת Three.js להדמיה תלת-ממדית -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>

<style>
*{margin:0;padding:0;box-sizing:border-box}
:root {
  --bg: #030611;
  --bg2: #080d22;
  --bg3: #0c1230;
  --blue: #3b82f6;
  --blue-glow: rgba(59, 130, 246, 0.35);
  --green: #10b981;
  --green-glow: rgba(16, 185, 129, 0.3);
  --purple: #8b5cf6;
  --purple-glow: rgba(139, 92, 246, 0.3);
  --white: #ffffff;
  --muted: #8892B0;
  --card: rgba(255,255,255,0.03);
  --border: rgba(255, 255, 255, 0.08);
}

/* ערכות נושא אטמוספריות מרהיבות */
body.theme-forest-rain {
  --bg: #06120e;
  --bg2: #0c2018;
  --bg3: #091712;
  --blue: #10b981;
  --blue-glow: rgba(16, 185, 129, 0.25);
  --green: #34d399;
  --purple: #059669;
}
body.theme-sunset-calm {
  --bg: #120905;
  --bg2: #20100a;
  --bg3: #180c08;
  --blue: #f97316;
  --blue-glow: rgba(249, 115, 22, 0.25);
  --green: #fcd34d;
  --purple: #ea580c;
}
body.theme-ethereal-light {
  --bg: #f8fafc;
  --bg2: #ffffff;
  --bg3: #f1f5f9;
  --blue: #2563eb;
  --blue-glow: rgba(37, 99, 235, 0.15);
  --green: #059669;
  --purple: #4f46e5;
  --white: #0f172a;
  --muted: #64748b;
  --border: rgba(15, 23, 42, 0.08);
  --card: rgba(15, 23, 42, 0.02);
}

html { scroll-behavior: smooth; }
body {
  font-family: 'Heebo', sans-serif;
  background: var(--bg);
  color: var(--white);
  overflow-x: hidden;
  line-height: 1.6;
  transition: background 0.6s cubic-bezier(0.4, 0, 0.2, 1), color 0.6s ease;
  -webkit-text-size-adjust: 100%;
}

/* ─── NAV ─── */
nav {
  position: fixed; top: 0; width: 100%; z-index: 100;
  display: flex; align-items: center; justify-content: space-between;
  padding: 16px 24px;
  background: rgba(3, 6, 17, 0.85);
  backdrop-filter: blur(16px);
  -webkit-backdrop-filter: blur(16px);
  border-bottom: 1px solid var(--border);
  transition: background 0.3s;
}
body.theme-ethereal-light nav {
  background: rgba(248, 250, 252, 0.85);
}
.nav-logo { font-size: 20px; font-weight: 700; color: var(--white); text-decoration: none; display: flex; align-items: center; gap: 8px;}
.nav-logo span { color: var(--blue); }
.nav-links { display: flex; gap: 24px; list-style: none; }
.nav-links a { color: var(--muted); text-decoration: none; font-size: 14px; transition: color 0.2s; font-weight: 500; }
.nav-links a:hover { color: var(--white); }
.nav-cta {
  background: linear-gradient(135deg, var(--blue), var(--purple));
  color: #fff; border: none; border-radius: 12px;
  padding: 10px 20px; font-size: 13px; font-weight: 700; cursor: pointer;
  box-shadow: 0 4px 15px var(--blue-glow);
  transition: transform 0.2s, box-shadow 0.2s;
}
.nav-cta:hover { transform: translateY(-1px); box-shadow: 0 6px 20px var(--blue-glow); }
.nav-cta:active { transform: scale(0.95); }
.nav-cta .desktop-txt { display: inline; }
.nav-cta .mobile-txt { display: none; }

/* ─── HERO ─── */
.hero {
  min-height: 100vh;
  display: flex; flex-direction: column;
  align-items: center; justify-content: center;
  text-align: center;
  padding: 140px 24px 80px;
  position: relative; overflow: hidden;
}
.hero-bg {
  position: absolute; inset: 0;
  background: radial-gradient(circle at center, var(--blue-glow) 0%, transparent 70%);
  pointer-events: none;
}
.hero-orb {
  position: relative; width: 200px; height: 200px;
  margin-bottom: 36px; display: flex; align-items: center; justify-content: center;
  cursor: pointer;
}
.orb-ring {
  position: absolute; border-radius: 50%;
  animation: breathe 5s ease-in-out infinite;
  transition: all 0.5s ease;
}
.orb-ring:nth-child(1) { width: 200px; height: 200px; background: var(--blue-glow); opacity: 0.15; filter: blur(4px); }
.orb-ring:nth-child(2) { width: 150px; height: 150px; background: var(--blue-glow); opacity: 0.25; filter: blur(2px); }
.orb-core {
  width: 72px; height: 72px; border-radius: 50%;
  background: linear-gradient(135deg, var(--blue), var(--purple));
  display: flex; align-items: center; justify-content: center;
  font-size: 28px; z-index: 2;
  box-shadow: 0 0 25px var(--blue-glow);
  transition: transform 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
}
.hero-orb:hover .orb-core { transform: scale(1.15) rotate(15deg); }
.hero-eyebrow {
  font-size: 13px; font-weight: 700; color: var(--blue);
  background: rgba(59, 130, 246, 0.08); padding: 6px 14px;
  border-radius: 20px; display: inline-block; margin-bottom: 20px;
  letter-spacing: 0.5px;
}
.hero-title { font-size: clamp(34px, 5.5vw, 68px); font-weight: 900; line-height: 1.15; margin-bottom: 20px; letter-spacing: -1px; }
.hero-title span { background: linear-gradient(90deg, var(--blue), var(--purple)); -webkit-background-clip: text; -webkit-text-fill-color: transparent; }
.hero-sub { font-size: clamp(16px, 2.2vw, 19px); color: var(--muted); max-width: 550px; margin: 0 auto 36px; font-weight: 300; }
.btn-main {
  background: linear-gradient(135deg, var(--blue), var(--purple));
  color: #fff; border: none; border-radius: 14px;
  padding: 18px 36px; font-size: 17px; font-weight: 700; cursor: pointer;
  box-shadow: 0 6px 22px var(--blue-glow);
  transition: transform 0.2s, box-shadow 0.2s;
}
.btn-main:hover { transform: translateY(-2px); box-shadow: 0 8px 28px var(--blue-glow); }
.btn-main:active { transform: translateY(1px); }

/* ─── STATS STRIP ─── */
.stats-strip {
  display: flex; justify-content: center; background: var(--bg2);
  border-top: 1px solid var(--border); border-bottom: 1px solid var(--border);
  flex-wrap: wrap;
}
.stat-item { flex: 1; min-width: 200px; max-width: 280px; padding: 28px 16px; text-align: center; border-left: 1px solid var(--border); }
.stat-item:last-child { border-left: none; }
.stat-num { font-size: 34px; font-weight: 900; color: var(--white); margin-bottom: 4px; }
.stat-desc { font-size: 13px; color: var(--muted); font-weight: 500; }

/* ─── FEATURES ─── */
.section { padding: 90px 24px; max-width: 1100px; margin: 0 auto; }
.section-title { font-size: clamp(28px, 4.2vw, 40px); font-weight: 800; text-align: center; margin-bottom: 48px; }
.features-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 24px; }
.feature-card {
  background: var(--card); border: 1px solid var(--border); border-radius: 24px; padding: 28px;
  transition: transform 0.3s cubic-bezier(0.25, 0.8, 0.25, 1), box-shadow 0.3s;
}
.feature-card:hover { transform: translateY(-6px); box-shadow: 0 12px 35px rgba(0,0,0,0.25); border-color: rgba(59, 130, 246, 0.2); }
.feature-icon { font-size: 30px; margin-bottom: 20px; width: 54px; height: 54px; display: flex; align-items: center; justify-content: center; background: rgba(59, 130, 246, 0.08); border-radius: 14px; }
.feature-title { font-size: 19px; font-weight: 700; margin-bottom: 10px; }
.feature-desc { color: var(--muted); font-size: 15px; }

/* ─── APP OVERLAY ─── */
.app-overlay {
  position: fixed; inset: 0; background: var(--bg);
  z-index: 1000; display: none; flex-direction: column;
  overflow-y: auto; padding: calc(75px + env(safe-area-inset-top)) 16px calc(80px + env(safe-area-inset-bottom));
  transition: background-color 0.5s ease;
}
.app-overlay.active { display: flex; }

#generative-canvas {
  position: absolute; inset: 0; z-index: 0; pointer-events: none;
}

/* כותרת עליונה קבועה באפליקציה */
.app-header {
  position: fixed; top: 0; left: 0; width: 100%; height: calc(65px + env(safe-area-inset-top));
  z-index: 1100; display: flex; align-items: flex-end; justify-content: space-between;
  padding: 0 24px 12px; background: rgba(3, 6, 17, 0.85);
  backdrop-filter: blur(20px); -webkit-backdrop-filter: blur(20px);
  border-bottom: 1px solid var(--border);
}
.app-header-title { font-size: 18px; font-weight: 800; color: var(--white); display: flex; align-items: center; gap: 8px;}
.app-header-title span { color: var(--blue); }

.app-container {
  max-width: 1100px; width: 100%; margin: 0 auto;
  display: grid; grid-template-columns: 1fr 1fr; gap: 24px;
  position: relative; z-index: 2;
  transition: opacity 0.5s ease, transform 0.5s ease;
}

.glass-panel {
  background: var(--bg2); border: 1px solid var(--border);
  border-radius: 28px; padding: 28px;
  box-shadow: 0 20px 45px rgba(0,0,0,0.45);
  display: flex; flex-direction: column; gap: 24px;
  transition: background-color 0.5s ease, border-color 0.5s ease, opacity 0.5s ease;
}

body.theme-ethereal-light .glass-panel {
  box-shadow: 0 10px 30px rgba(15, 23, 42, 0.06);
}

/* הגרעין האורגני החדש והאינטואיטיבי */
.nucleus-area {
  display: flex; flex-direction: column; align-items: center; justify-content: center;
  min-height: 290px; position: relative; gap: 16px;
  transition: all 0.5s ease;
}
.nucleus-container {
  position: relative;
  width: 180px; height: 180px;
  display: flex; align-items: center; justify-content: center;
}
.progress-ring {
  position: absolute;
  transform: rotate(-90deg);
  pointer-events: none;
  z-index: 1;
}
.progress-ring__circle {
  transition: stroke-dashoffset 0.3s ease, stroke 0.5s ease;
  stroke-linecap: round;
}
.nucleus-orb {
  width: 140px; height: 140px; border-radius: 50%;
  background: radial-gradient(circle at 30% 30%, var(--blue), var(--purple));
  box-shadow: 0 0 45px var(--blue-glow);
  display: flex; flex-direction: column; align-items: center; justify-content: center;
  transition: transform 0.25s cubic-bezier(0.175, 0.885, 0.32, 1.275), background 1s ease;
  cursor: pointer; z-index: 5;
  user-select: none;
}
.state-label { font-size: 19px; font-weight: 800; text-shadow: 0 2px 5px rgba(0,0,0,0.5); color: #ffffff; }
.state-timer { font-size: 30px; font-weight: 900; text-shadow: 0 2px 5px rgba(0,0,0,0.5); color: #ffffff; }
.wave-ring {
  position: absolute; border: 2px solid var(--blue); border-radius: 50%;
  width: 140px; height: 140px; opacity: 0; pointer-events: none;
}

/* תיבת הדרכת נשימה ברורה לכל שלב */
.breathing-instruction-card {
  font-size: 14px;
  color: var(--blue);
  font-weight: 700;
  text-align: center;
  background: rgba(255, 255, 255, 0.02);
  padding: 10px 20px;
  border-radius: 16px;
  border: 1px solid var(--border);
  min-height: 48px;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  max-width: 320px;
  box-shadow: 0 4px 12px rgba(0,0,0,0.15);
  transition: color 0.5s ease, border-color 0.5s ease;
}

/* מקרן אור אטמוספרי מלא (Ambient Mode Active Styles) */
.ambient-projection-active .app-overlay {
  padding-top: 0 !important;
  padding-bottom: 0 !important;
}
.ambient-projection-active .app-container > *:not(.breathing-panel-box) {
  opacity: 0; pointer-events: none; transform: scale(0.95); display: none !important;
}
.ambient-projection-active .app-container {
  grid-template-columns: 1fr;
  max-width: 600px;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}
.ambient-projection-active .breathing-panel-box {
  background: transparent !important;
  border-color: transparent !important;
  box-shadow: none !important;
  width: 100%;
}
.ambient-projection-active .nucleus-orb {
  width: 250px; height: 250px;
  box-shadow: 0 0 120px var(--blue-glow);
}
.ambient-projection-active .nucleus-container {
  width: 290px; height: 290px;
}
.ambient-projection-active .progress-ring {
  width: 290px; height: 290px;
}
.ambient-projection-active .progress-ring circle {
  r: 135; cx: 145; cy: 145;
  stroke-width: 8;
}
.ambient-projection-active .progress-ring__circle {
  stroke-dasharray: 848.2;
}

/* מיקסר סאונד */
.mixer-row { display: flex; align-items: center; justify-content: space-between; gap: 16px; }
.mixer-row label { font-size: 14px; font-weight: 700; width: 120px; color: var(--muted); }
.mixer-slider { flex: 1; accent-color: var(--blue); height: 8px; border-radius: 4px; outline: none; cursor: pointer; background: rgba(255,255,255,0.1); }

/* מכולה תלת ממדית */
.tutorial-box { width: 100%; position: relative; }
#simulation-canvas-3d {
  background: #01030a; border-radius: 20px; width: 100%; height: 250px;
  cursor: grab; border: 1px solid var(--border); touch-action: none;
}
#simulation-canvas-3d:active { cursor: grabbing; }

/* ממיס המחשבות הטאקטילי */
.thought-overlay {
  position: fixed; inset: 0; background: #020409; z-index: 1200;
  display: none; flex-direction: column; align-items: center; justify-content: center;
}
.thought-overlay.active { display: flex; }
#thought-canvas { position: absolute; inset: 0; cursor: pointer; z-index: 2; touch-action: none; }
.thought-instructions { position: absolute; bottom: 50px; text-align: center; z-index: 10; pointer-events: none; padding: 0 20px; }

/* גיימיפיקציה ולוח שנה משודרג */
.calendar-grid { display: grid; grid-template-columns: repeat(7, 1fr); gap: 6px; text-align: center; }
.calendar-cell { 
  aspect-ratio: 1; display: flex; flex-direction: column; align-items: center; justify-content: center; 
  font-size: 12px; border-radius: 50%; color: var(--white); border: 1px solid transparent; 
  cursor: pointer; transition: all 0.25s cubic-bezier(0.4, 0, 0.2, 1); position: relative;
}
.calendar-cell:hover { background: rgba(255, 255, 255, 0.08); border-color: rgba(255,255,255,0.15); }
.calendar-cell.completed { background: var(--green); color: #000000 !important; font-weight: 900; box-shadow: 0 0 12px rgba(16, 185, 129, 0.5); }
.calendar-cell.today { border: 2px solid var(--blue); font-weight: bold; }
.calendar-cell.empty { pointer-events: none; opacity: 0; }
.calendar-cell.has-note::after {
  content: ''; position: absolute; bottom: 3px; width: 5px; height: 5px; 
  background-color: var(--blue); border-radius: 50%; box-shadow: 0 0 4px var(--blue);
}
.calendar-cell.completed.has-note::after {
  background-color: #000000; box-shadow: none;
}

/* עיצוב הישגים וגביעים ברור ואינטראקטיבי */
.badges-list { display: flex; flex-direction: column; gap: 12px; margin-top: 8px; }
.badge-card {
  display: flex; align-items: center; gap: 16px; padding: 14px 18px;
  background: rgba(255, 255, 255, 0.02); border: 1px solid var(--border);
  border-radius: 18px; transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
}
.badge-card.unlocked {
  background: rgba(16, 185, 129, 0.06); border-color: rgba(16, 185, 129, 0.3);
  box-shadow: 0 4px 15px rgba(16, 185, 129, 0.08);
}
.badge-card-icon {
  font-size: 26px; width: 48px; height: 48px; display: flex; align-items: center; justify-content: center;
  background: rgba(255, 255, 255, 0.03); border-radius: 14px; transition: all 0.4s ease;
  filter: grayscale(1); opacity: 0.4;
}
.badge-card.unlocked .badge-card-icon {
  filter: grayscale(0); opacity: 1; background: rgba(16, 185, 129, 0.15);
  box-shadow: 0 0 12px rgba(16, 185, 129, 0.3);
}
.badge-card-info { display: flex; flex-direction: column; text-align: right; gap: 2px; }
.badge-card-title { font-size: 14px; font-weight: 800; color: var(--white); }
.badge-card-desc { font-size: 11px; color: var(--muted); }
.badge-card.unlocked .badge-card-title { color: var(--green); }

/* עיצוב קלף זן גירד ושחרר החדש */
.scratch-card-container {
  position: relative; width: 100%; height: 200px;
  background: linear-gradient(135deg, #111827, #030712);
  border: 1px solid var(--border); border-radius: 20px; overflow: hidden;
  box-shadow: 0 8px 30px rgba(0,0,0,0.3);
}
.scratch-card-underlay {
  position: absolute; inset: 0; display: flex; flex-direction: column;
  align-items: center; justify-content: center; padding: 24px; text-align: center;
  z-index: 1;
}
.scratch-card-canvas {
  position: absolute; inset: 0; z-index: 2; cursor: pointer; touch-action: none;
}

/* סורק דופק ביומטרי החדש */
.ppg-scanner-box {
  display: flex; flex-direction: column; gap: 16px; background: rgba(255,255,255,0.01);
  border: 1px solid var(--border); padding: 20px; border-radius: 20px;
}
.ppg-visualizer-container {
  display: flex; align-items: center; gap: 16px; height: 60px;
}
.ppg-feedback-orb {
  width: 48px; height: 48px; border-radius: 50%; background: rgba(239, 68, 68, 0.1);
  border: 2px solid #ef4444; display: flex; align-items: center; justify-content: center;
  font-size: 20px; transition: transform 0.15s ease;
}
.ppg-feedback-orb.scanning {
  animation: pulse-red 1.2s infinite;
}
@keyframes pulse-red {
  0% { transform: scale(1); box-shadow: 0 0 0 0 rgba(239, 68, 68, 0.7); }
  70% { transform: scale(1.1); box-shadow: 0 0 0 10px rgba(239, 68, 68, 0); }
  100% { transform: scale(1); box-shadow: 0 0 0 0 rgba(239, 68, 68, 0); }
}

/* מודלים */
.journal-modal {
  position: fixed; inset: 0; background: rgba(3, 6, 17, 0.8);
  backdrop-filter: blur(8px); -webkit-backdrop-filter: blur(8px);
  z-index: 1500; display: none; align-items: center; justify-content: center; padding: 20px;
}
.journal-modal.active { display: flex; }
.journal-modal-content {
  background: var(--bg2); border: 1px solid var(--border);
  border-radius: 24px; max-width: 450px; width: 100%; padding: 28px;
  box-shadow: 0 25px 50px rgba(0,0,0,0.5);
  display: flex; flex-direction: column; gap: 20px;
  transform: translateY(20px); transition: transform 0.3s ease;
}
.journal-modal.active .journal-modal-content { transform: translateY(0); }

/* קטגוריית מנחה קולי */
.quick-mood-container { display: flex; gap: 8px; flex-wrap: wrap; margin-bottom: 4px; }
.mood-tag {
  background: rgba(255, 255, 255, 0.03); border: 1px solid var(--border);
  color: var(--white); padding: 8px 14px; border-radius: 12px;
  font-size: 13px; font-weight: 500; cursor: pointer; transition: all 0.2s ease;
}
.mood-tag:hover { background: rgba(59, 130, 246, 0.1); border-color: var(--blue); }
.mood-tag.selected { background: var(--blue); color: #fff; border-color: var(--blue); box-shadow: 0 0 10px var(--blue-glow); }

.pulse-indicator {
  font-size: 11px; font-weight: 700; background: rgba(16, 185, 129, 0.12);
  color: var(--green); padding: 4px 10px; border-radius: 20px; display: flex; align-items: center; gap: 6px;
}
.pulse-indicator::before {
  content: ''; display: inline-block; width: 8px; height: 8px;
  background-color: var(--green); border-radius: 50%; animation: pulse-green 1.5s infinite;
}

/* הגנת iOS על הגופנים למניעת זום-אין מציק */
.ai-input, input[type="text"], textarea, select {
  font-size: 16px !important;
}

.app-btn {
  background: linear-gradient(135deg, var(--blue), var(--purple));
  color: #fff; border: none; border-radius: 14px;
  padding: 14px 24px; font-size: 14px; font-weight: 700; cursor: pointer;
  text-align: center; width: 100%; display: flex; align-items: center; justify-content: center; gap: 8px;
  min-height: 48px;
  transition: opacity 0.2s, transform 0.2s, box-shadow 0.2s;
}
.app-btn:hover { box-shadow: 0 4px 15px var(--blue-glow); }
.app-btn:active { transform: scale(0.97); }
.app-btn.secondary { background: rgba(255,255,255,0.04); border: 1px solid var(--border); color: var(--white); }
.app-btn.secondary:hover { background: rgba(255,255,255,0.08); }

.custom-toast {
  position: fixed; bottom: 30px; left: 50%; transform: translateX(-50%) translateY(120px);
  background: var(--green); color: #000; padding: 14px 28px; border-radius: 24px;
  font-weight: 700; z-index: 2100; opacity: 0; transition: transform 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275), opacity 0.3s;
  box-shadow: 0 8px 25px rgba(0,0,0,0.3);
}
.custom-toast.show { transform: translateX(-50%) translateY(0); opacity: 1; }

.theme-select-container { display: flex; gap: 8px; flex-wrap: wrap; margin-top: 8px; }
.theme-btn {
  flex: 1; min-width: 65px; padding: 10px; font-size: 12px; font-weight: 700;
  border-radius: 10px; border: 1px solid var(--border); background: rgba(255,255,255,0.03);
  color: var(--white); cursor: pointer; transition: all 0.25s; min-height: 40px;
}
.theme-btn:hover { background: rgba(255,255,255,0.08); border-color: var(--blue); }
.theme-btn.active { background: var(--blue); color: white; border-color: var(--blue); }

.session-timer-bar {
  background: rgba(255, 255, 255, 0.04); border-radius: 16px; padding: 16px;
  display: flex; align-items: center; justify-content: space-between;
}

@keyframes breathe {
  0%, 100% { transform: scale(1); opacity: 0.4; }
  50% { transform: scale(1.15); opacity: 0.95; }
}

/* ─── PREMIUM BOTTOM TAB NAVIGATION BAR (Mobile Exclusive) ─── */
.mobile-tabs-nav {
  position: fixed; bottom: 0; left: 0; width: 100%; height: calc(65px + env(safe-area-inset-bottom));
  z-index: 1010; display: none; align-items: center; justify-content: space-around;
  background: rgba(8, 13, 34, 0.85);
  backdrop-filter: blur(25px); -webkit-backdrop-filter: blur(25px);
  border-top: 1px solid var(--border);
  padding-bottom: env(safe-area-inset-bottom);
}
.tab-nav-item {
  display: flex; flex-direction: column; align-items: center; justify-content: center;
  color: var(--muted); border: none; background: transparent; cursor: pointer;
  flex: 1; height: 100%; gap: 3px; font-family: 'Heebo', sans-serif;
  transition: all 0.2s ease;
}
.tab-nav-item-icon { font-size: 20px; transition: transform 0.2s ease; }
.tab-nav-item-label { font-size: 11px; font-weight: 500; }
.tab-nav-item.active-tab { color: var(--blue); }
.tab-nav-item.active-tab .tab-nav-item-icon { transform: scale(1.15); filter: drop-shadow(0 0 5px var(--blue-glow)); }


/* ─── ONBOARDING & LOGIN CONTAINER ─── */
.auth-overlay-backdrop {
  position: fixed; inset: 0; background: rgba(3, 6, 17, 0.92);
  backdrop-filter: blur(30px); -webkit-backdrop-filter: blur(30px);
  z-index: 2500; display: none; align-items: center; justify-content: center; padding: 16px;
}
.auth-overlay-backdrop.active { display: flex; }

.auth-card {
  background: var(--bg2); border: 1px solid var(--border);
  border-radius: 28px; max-width: 440px; width: 100%; padding: 32px;
  box-shadow: 0 25px 60px rgba(0,0,0,0.6);
  display: flex; flex-direction: column; gap: 24px;
  transition: transform 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
}
.auth-card-header { text-align: center; display: flex; flex-direction: column; gap: 8px; }
.auth-card-title { font-size: 24px; font-weight: 900; }
.auth-card-title span { background: linear-gradient(90deg, var(--blue), var(--purple)); -webkit-background-clip: text; -webkit-text-fill-color: transparent; }
.auth-card-subtitle { font-size: 13px; color: var(--muted); }

.auth-form-group { display: flex; flex-direction: column; gap: 8px; text-align: right; }
.auth-label { font-size: 13px; font-weight: 700; color: var(--muted); }
.auth-input-field {
  width: 100%; background: rgba(255, 255, 255, 0.03); border: 1px solid var(--border);
  border-radius: 14px; padding: 14px; color: var(--white); font-family: 'Heebo', sans-serif;
  outline: none; transition: border-color 0.2s, box-shadow 0.2s;
}
.auth-input-field:focus { border-color: var(--blue); box-shadow: 0 0 12px var(--blue-glow); }

/* OTP grid code */
.otp-container { display: flex; gap: 12px; justify-content: center; direction: ltr; margin: 12px 0; }
.otp-box {
  width: 54px; height: 64px; background: rgba(0,0,0,0.3); border: 1px solid var(--border);
  border-radius: 14px; color: #fff; font-size: 26px; font-weight: 900; text-align: center;
  outline: none; transition: border-color 0.25s ease, box-shadow 0.25s ease;
}
.otp-box:focus { border-color: var(--blue); box-shadow: 0 0 12px var(--blue-glow); }

/* Simulated Phone SMS Push Notification UI */
.simulated-sms-push {
  position: fixed; top: -120px; left: 50%; transform: translateX(-50%);
  width: calc(100% - 32px); max-width: 400px;
  background: rgba(15, 23, 42, 0.95); border: 1px solid rgba(255,255,255,0.18);
  border-radius: 20px; padding: 16px; z-index: 3500;
  box-shadow: 0 15px 40px rgba(0,0,0,0.6);
  display: flex; flex-direction: column; gap: 10px;
  transition: top 0.6s cubic-bezier(0.175, 0.885, 0.32, 1.275);
}
.simulated-sms-push.show { top: 24px; }
.sms-header { display: flex; justify-content: space-between; align-items: center; width: 100%; font-size: 11px; color: var(--muted); }
.sms-body { font-size: 13px; color: #fff; text-align: right; line-height: 1.4; }

/* ─── PWA INSTALLATION GUIDE MODAL (NEW) ─── */
.install-guide-backdrop {
  position: fixed; inset: 0; background: rgba(3, 6, 17, 0.85);
  backdrop-filter: blur(15px); -webkit-backdrop-filter: blur(15px);
  z-index: 2600; display: none; align-items: center; justify-content: center; padding: 16px;
}
.install-guide-backdrop.active { display: flex; }
.install-guide-card {
  background: var(--bg2); border: 1px solid var(--border);
  border-radius: 28px; max-width: 420px; width: 100%; padding: 28px;
  box-shadow: 0 25px 60px rgba(0,0,0,0.6);
  display: flex; flex-direction: column; gap: 20px;
  text-align: right;
}
.guide-step {
  display: flex; gap: 14px; align-items: flex-start;
  background: rgba(255,255,255,0.02); padding: 14px; border-radius: 16px;
  border: 1px solid var(--border);
}
.guide-step-num {
  width: 28px; height: 28px; border-radius: 50%; background: var(--blue);
  color: #fff; display: flex; align-items: center; justify-content: center;
  font-weight: 900; font-size: 14px; flex-shrink: 0;
}
.guide-step-text { font-size: 13px; color: #e2e8f0; line-height: 1.4; }


/* ─── RESPONSIVE COMPONENT RULES ─── */
@media(max-width: 900px) {
  nav { padding: 12px 16px; }
  .nav-links { display: none; } 
  .nav-cta .desktop-txt { display: none; }
  .nav-cta .mobile-txt { display: inline; }
  
  .hero { padding-top: 110px; }
  
  /* התאמת ה-Dashboard למובייל בעזרת טאבים */
  .app-container {
    grid-template-columns: 1fr;
    padding: 0 4px;
    margin-top: 10px;
  }
  
  /* הגדרת הטאבים המובנים - הכל מוסתר כברירת מחדל */
  .glass-panel.tab-content {
    display: none !important;
  }
  
  /* רק הטאב הפעיל יתגלה מחדש */
  .glass-panel.tab-content.active-tab {
    display: flex !important;
    animation: tab-slide-in 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  }
  
  .mobile-tabs-nav {
    display: flex; /* הצגת תפריט הניווט תחתון במכשירים ניידים */
  }

  @keyframes tab-slide-in {
    from { opacity: 0; transform: translateY(15px); }
    to { opacity: 1; transform: translateY(0); }
  }
}

/* הסתרת כפתור הצא ממקרן בדסקטופ */
@media(min-width: 901px) {
  .show-only-in-ambient {
    display: none !important;
  }
}
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <a href="#" class="nav-logo" onclick="window.scrollTo({top:0, behavior:'smooth'})">🧘 <span>רוגע Infinite</span></a>
  <ul class="nav-links">
    <li><a href="#features">תכונות</a></li>
    <li><a href="#stats-strip">נתונים</a></li>
  </ul>
  <div style="display: flex; gap: 10px; align-items: center;">
    <button class="nav-cta" style="background: rgba(255,255,255,0.05); border: 1px solid var(--border);" onclick="openInstallGuide()">📲 התקן כאפליקציה</button>
    <button class="nav-cta" onclick="openMeditationApp()">
      <span class="desktop-txt">הפעל אפליקציית רשת ✨</span>
      <span class="mobile-txt">רוגע Web ✨</span>
    </button>
  </div>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-bg"></div>
  <div class="hero-orb" onclick="openMeditationApp()">
    <div class="orb-ring"></div>
    <div class="orb-ring"></div>
    <div class="orb-core">🧘</div>
  </div>
  <p class="hero-eyebrow">מדיטציה ונשימות אינטראקטיביות בעברית</p>
  <h1 class="hero-title">רגע אחד של <span>שקט</span><br>משנה את כל היום</h1>
  <p class="hero-sub">חוויית ה-Mindfulness העתידנית ביותר הפועלת ישירות בדפדפן ובמובייל ללא צורך בהתקנה, <span class="dynamic-username-label">manegro</span>.</p>
  <div class="hero-actions">
    <button class="btn-main" onclick="openMeditationApp()">✨ כניסה לאפליקציית רוגע Web</button>
  </div>
</section>

<!-- STATS STRIP -->
<div class="stats-strip" id="stats-strip">
  <div class="stat-item">
    <div class="stat-num" id="stat-active-users">48,102</div>
    <div class="stat-desc">משתמשים פעילים</div>
  </div>
  <div class="stat-item">
    <div class="stat-num">4.9★</div>
    <div class="stat-desc">דירוג חנות האפ</div>
  </div>
  <div class="stat-item">
    <div class="stat-num">110Hz</div>
    <div class="stat-desc">תדר שקט מוכח</div>
  </div>
</div>

<!-- FEATURES -->
<section class="section" id="features">
  <h2 class="section-title">כל מה שצריך לרגע שקט אמיתי</h2>
  <div class="features-grid">
    <div class="feature-card">
      <div class="feature-icon">🌬️</div>
      <h3 class="feature-title">נשימות מודרכות חיות</h3>
      <p class="feature-desc">אנימציה שמסנכרנת את הנשימה שלך בצורה ויזואלית בקצב קופסה של 4 שניות.</p>
    </div>
    <div class="feature-card">
      <div class="feature-icon">🔊</div>
      <h3 class="feature-title">מיקסר סאונד טיפולי</h3>
      <p class="feature-desc">מחולל סאונד המאפשר לך למקסס רעש בינאורלי קוסמי וגלי ים בזמן אמת.</p>
    </div>
    <div class="feature-card">
      <div class="feature-icon">💭</div>
      <h3 class="feature-title">ממיס המחשבות הטאקטילי</h3>
      <p class="feature-desc">מנגנון מבוסס מגע המאפשר להקליד דאגה ולשפשף אותה פיזית עד שהיא נעלמת.</p>
    </div>
  </div>
</section>

<!-- APP OVERLAY -->
<div class="app-overlay" id="interactive-app">
  <canvas id="generative-canvas"></canvas>

  <!-- כותרת עליונה קבועה בפנים -->
  <div class="app-header hide-in-ambient">
    <div class="app-header-title">🧘 <span id="app-dynamic-welcome-title">רוגע Infinite</span></div>
    <button class="app-btn secondary" style="width: auto; height: 38px; min-height: 38px; padding: 0 16px;" onclick="closeMeditationApp()">✕ סגור</button>
  </div>
  
  <div class="app-container" id="main-app-container">
    
    <!-- טאב 1 (🌬️ נשימה): הגרעין האורגני ומאמן הנשימה -->
    <div class="glass-panel breathing-panel-box tab-content active-tab" id="panel-breath">
      <div style="display: flex; justify-content: space-between; align-items: center;" class="hide-in-ambient">
        <h3 style="font-size: 17px; font-weight: 800;">🌬️ מרחב נשימה ביו-אדפטיבי</h3>
      </div>

      <!-- כפתור חזור מקרן שיופיע רק במצב מקרן פעיל -->
      <button class="app-btn secondary show-only-in-ambient" id="btn-exit-ambient" style="display: none; position: fixed; top: 20px; right: 20px; width: auto; z-index: 1100;" onclick="toggleAmbientProjectionMode()">✕ צא ממצב מקרן</button>

      <div class="nucleus-area">
        <div class="wave-ring" id="wave-effect"></div>
        <div class="nucleus-container">
          <svg class="progress-ring" width="180" height="180" id="ambient-svg-ring">
            <circle class="progress-ring__background" stroke="rgba(255, 255, 255, 0.05)" stroke-width="6" fill="transparent" r="82" cx="90" cy="90"/>
            <circle id="progress-bar" class="progress-ring__circle" stroke="var(--blue)" stroke-width="6" fill="transparent" r="82" cx="90" cy="90" stroke-dasharray="515.2" stroke-dashoffset="0"/>
          </svg>
          <div class="nucleus-orb" id="system-nucleus" onclick="triggerNucleusRipple()">
            <span class="state-label" id="nucleus-label">שאיפה</span>
            <span class="state-timer" id="nucleus-timer">4</span>
          </div>
        </div>
        
        <div class="breathing-instruction-card" id="breathing-instruction-text">
          שאף אוויר דרך האף והרחב את הבטן...
        </div>
      </div>
      
      <div style="display: flex; gap: 12px; margin-top: auto;" class="hide-in-ambient">
        <button class="app-btn" id="btn-breathe" onclick="toggleBreathingSystem()">⏸ השהה נשימה</button>
        <button class="app-btn secondary" id="btn-ambient-mode" onclick="toggleAmbientProjectionMode()">💡 מקרן אור חדר</button>
      </div>

      <!-- מדד סטטיסטיקה מובנה -->
      <div class="session-timer-bar hide-in-ambient">
        <div>
          <span style="font-size: 12px; color: var(--muted); display: block;">תרגול נוכחי (פס קול מתפתח)</span>
          <span id="session-time-left" style="font-weight: 700; font-size: 16px;">03:00</span>
        </div>
        <button class="app-btn" id="btn-start-session" style="width: auto; padding: 8px 16px; font-size: 12px;" onclick="toggleActiveSession()">🚀 התחל תירגול</button>
      </div>
    </div>

    <!-- טאב 2 (🎙️ סאונד): מיקסר צלילים, אולפן AI וערכות נושא (משולב) -->
    <div class="glass-panel tab-content" id="panel-sound">
      <h3 style="font-size: 17px; font-weight: 800;">🎙️ מנחה קולי אישי & מיקסר</h3>
      
      <!-- אולפן AI קולי -->
      <div style="display: flex; flex-direction: column; gap: 12px; border-bottom: 1px solid var(--border); padding-bottom: 16px;">
        <div style="display: flex; align-items: center; justify-content: space-between;">
          <span style="font-size: 13px; font-weight: 700; color: var(--muted);">סנתז הדרכת זן מותאמת אישית:</span>
          <span class="pulse-indicator" id="voice-studio-status">מוכן</span>
        </div>
        <div class="quick-mood-container">
          <button class="mood-tag" onclick="selectQuickMood('אני מרגיש עמוס ולחוץ בגלל היום העמוס שעבר עלי')">😫 לחוץ</button>
          <button class="mood-tag" onclick="selectQuickMood('עייף מאוד ונטול אנרגיה, מחפש להירגע ולישון')">😴 עייף</button>
          <button class="mood-tag" onclick="selectQuickMood('הראש שלי סוער ומלא במחשבות טורדניות, חסר פוקוס')">🎯 חסר פוקוס</button>
          <button class="mood-tag" onclick="selectQuickMood('אני מרגיש מתוח וכועס, הגוף שלי מגיב בלחץ')">😤 מתוח</button>
        </div>
        <textarea class="ai-input" id="ai-user-mood" placeholder="איך אתה מרגיש עכשיו, manegro? למשל: קצת מוצף..." rows="2"></textarea>
        
        <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 10px;">
          <div>
            <label style="font-size: 11px; color: var(--muted); font-weight: bold; display: block; margin-bottom: 4px;">בחר מנחה:</label>
            <select class="ai-input" id="ai-voice-select" style="padding: 8px; width: 100%;">
              <option value="Leda">Leda - קול נשי עמוק 🌌</option>
              <option value="Kore">Kore - קול נשי שקט 🔔</option>
              <option value="Zephyr">Zephyr - קול גברי רך 🍃</option>
              <option value="Puck">Puck - קול מלטף ומרגיע ✨</option>
            </select>
          </div>
          <div>
            <label style="font-size: 11px; color: var(--muted); font-weight: bold; display: block; margin-bottom: 4px;">מרחב אקוסטי:</label>
            <select class="ai-input" id="ai-acoustic-select" style="padding: 8px; width: 100%;">
              <option value="temple">🕌 היכל מקדש (הד קוסמי)</option>
              <option value="cave">🌲 מערת יער (ריברב)</option>
              <option value="space">🪐 ריק חלל (דיליי)</option>
              <option value="dry">🎙️ סטודיו אינטימי (נקי)</option>
            </select>
          </div>
        </div>
        <button class="app-btn" onclick="generateAiInsight()">✨ סנתז הדרכה</button>

        <div class="ai-response" id="ai-response-block" style="background: rgba(59, 130, 246, 0.05); padding: 14px; border-radius: 12px; display: none; border: 1px solid var(--border);">
          <div id="ai-response-content" style="font-style: italic; font-size: 13px; margin-bottom: 12px; line-height: 1.5;">רוגע מכין מנטרה...</div>
          <div style="display: flex; gap: 12px; align-items: center;">
            <button class="app-btn" id="btn-speak-ai" style="width: auto; padding: 8px 14px;" onclick="speakAiInsight()">🔊 הקרא בקול</button>
            <canvas id="voice-visualizer" style="height: 36px; background: rgba(0,0,0,0.3); border-radius: 8px; flex: 1;"></canvas>
          </div>
        </div>
      </div>

      <!-- מיקסר צלילים טיפוליים -->
      <div style="display: flex; flex-direction: column; gap: 12px;">
        <span style="font-size: 13px; font-weight: 700; color: var(--muted);">מיקסר סאונד ביו-אדפטיבי (סטריאו):</span>
        <div class="mixer-row">
          <label>🌌 קוסמי (110Hz)</label>
          <input type="range" class="mixer-slider" id="volume-binaural" min="0" max="100" value="30" oninput="adjustVolume('binaural', this.value)">
        </div>
        <div class="mixer-row">
          <label>🌊 גלי ים</label>
          <input type="range" class="mixer-slider" id="volume-ocean" min="0" max="100" value="0" oninput="adjustVolume('ocean', this.value)">
        </div>
      </div>

      <hr style="border: 0; border-top: 1px solid var(--border); margin: 4px 0;">
      
      <!-- ערכות נושא -->
      <div>
        <span style="font-size: 13px; font-weight: 700; color: var(--muted); display: block; margin-bottom: 6px;">🎨 עיצוב אטמוספרי:</span>
        <div class="theme-select-container">
          <button class="theme-btn active" id="theme-btn-deep-night" onclick="applyTheme('deep-night')">🌌 לילה</button>
          <button class="theme-btn" id="theme-btn-forest-rain" onclick="applyTheme('forest-rain')">🌲 יער</button>
          <button class="theme-btn" id="theme-btn-sunset-calm" onclick="applyTheme('sunset-calm')">🌅 שקיעה</button>
          <button class="theme-btn" id="theme-btn-ethereal-light" onclick="applyTheme('ethereal-light')">🤍 רוחני</button>
        </div>
      </div>
    </div>

    <!-- טאב 3 (💭 שחרור): ממיס המחשבות הטאקטילי וקלף זן יומי (משולב) -->
    <div class="glass-panel tab-content" id="panel-thoughts">
      <h3 style="font-size: 17px; font-weight: 800;">💭 שחרור דאגות & קלף זן</h3>
      
      <!-- ממיס מחשבות -->
      <div style="border-bottom: 1px solid var(--border); padding-bottom: 18px; display: flex; flex-direction: column; gap: 8px;">
        <span style="font-size: 13px; font-weight: 700; color: var(--muted);">ממיס המחשבות הטאקטילי:</span>
        <p style="font-size: 12px; color: var(--muted);">רשום מחשבה מעיקה ושפשף אותה פיזית עם האצבע כדי להמיס אותה לחלקיקי אור וגיצים זוהרים.</p>
        <div style="display: flex; gap: 8px; margin-top: 4px;">
          <input type="text" class="ai-input" id="thought-input" placeholder="מה מדאיג אותך עכשיו, manegro?">
          <button class="app-btn" style="width: auto; padding: 12px 20px;" onclick="startThoughtDissolution()">✨ המיס</button>
        </div>
      </div>

      <!-- קלף זן יומי מגרד -->
      <div style="display: flex; flex-direction: column; gap: 6px;">
        <span style="font-size: 13px; font-weight: 700; color: var(--muted);">🃏 קלף השראה וזן יומי (גרד ושחרר):</span>
        <p style="font-size: 11px; color: var(--muted); margin-bottom: 6px;">גרד את שכבת הזהב באמצעות האצבע או העכבר כדי לגלות את המנטרה האישית שלך להיום.</p>
        <div class="scratch-card-container">
          <div class="scratch-card-underlay" id="scratch-underlay-content">
            <span style="font-size: 34px; margin-bottom: 8px;">✨</span>
            <h5 style="font-size: 14px; font-weight: 800; color: #f59e0b; margin-bottom: 4px;">מסר אישי עבורך, <span class="dynamic-username-label">manegro</span>:</h5>
            <p id="scratch-card-message" style="font-size: 12px; font-style: italic; line-height: 1.4; max-width: 260px;">טוען את המנטרה האישית שלך...</p>
          </div>
          <canvas class="scratch-card-canvas" id="scratch-canvas"></canvas>
        </div>
      </div>
    </div>

    <!-- טאב 4 (📅 יומן): יומן ענן והישגים משודרג -->
    <div class="glass-panel tab-content" id="panel-journal">
      <div style="display: flex; justify-content: space-between; align-items: center; border-bottom: 1px solid var(--border); padding-bottom: 12px;">
        <div style="display: flex; flex-direction: column;">
          <h3 style="font-size: 17px; font-weight: 800;">📅 יומן ומעקב תרגול אינטראקטיבי</h3>
          <span id="calendar-month-title" style="font-size: 13px; color: var(--blue); font-weight: 700; margin-top: 2px;">יוני 2026</span>
        </div>
        <div style="display: flex; gap: 12px; font-size: 11px; text-align: left; color: var(--muted); line-height: 1.3;">
          <div>רצף: <strong id="user-streak" style="color:var(--white); font-size: 13px;">0</strong> ימים</div>
          <div>סשנים: <strong id="user-total-sessions" style="color:var(--white); font-size: 13px;">0</strong></div>
          <div>דקות: <strong id="user-total-minutes" style="color:var(--white); font-size: 13px;">0</strong></div>
        </div>
      </div>
      
      <p style="font-size: 11px; color: var(--muted); margin-top: -8px;">💡 טיפ: לחץ על יום בלוח כדי לסמן תרגול, לראות או להוסיף הערות רפלקציה אישיות!</p>
      
      <div class="calendar-grid" id="calendar-days-grid"></div>
      
      <h4 style="font-size: 14px; font-weight: 800; margin-top: 12px; border-top: 1px solid var(--border); padding-top: 12px;">🏆 גביעים והישגים:</h4>
      <div class="badges-list">
        <div class="badge-card" id="badge-1">
          <div class="badge-card-icon">🌬️</div>
          <div class="badge-card-info">
            <div class="badge-card-title" id="badge-title-1">נשימה ראשונה</div>
            <div class="badge-card-desc" id="badge-desc-1">פתוח! השלמת סשן מודעות נשימתי. כל הכבוד!</div>
          </div>
        </div>
        
        <div class="badge-card" id="badge-2">
          <div class="badge-card-icon">🔥</div>
          <div class="badge-card-info">
            <div class="badge-card-title" id="badge-title-2">מתמיד ברצף</div>
            <div class="badge-card-desc" id="badge-desc-2">נעול: שמור על רצף תרגול קבוע של 3 ימים</div>
          </div>
        </div>
        
        <div class="badge-card" id="badge-3">
          <div class="badge-card-icon">☁️</div>
          <div class="badge-card-info">
            <div class="badge-card-title" id="badge-title-3">מסונכרן בענן</div>
            <div class="badge-card-desc" id="badge-desc-3">נעול: התחבר למסד הנתונים כדי לשמור התקדמות</div>
          </div>
        </div>
      </div>
    </div>

    <!-- טאב 5 (📸 ביומטריה): סורק דופק ו-3D Nebula (משולב) -->
    <div class="glass-panel tab-content" id="panel-bio">
      <h3 style="font-size: 17px; font-weight: 800;">📸 ביומטריה & ערפילית תלת-ממדית</h3>
      
      <!-- סורק דופק PPG -->
      <div class="ppg-scanner-box">
        <h4 style="font-size: 13px; font-weight: 800;">❤️ סורק דופק ביומטרי PPG (דרך המצלמה)</h4>
        <p style="font-size: 11px; color: var(--muted);">לחץ על התחל, כסה את עדשת המצלמה האחורית קלות באצבעך וקבל דופק מסונכרן זן.</p>
        
        <div class="ppg-visualizer-container">
          <div class="ppg-feedback-orb" id="ppg-heart-orb">❤️</div>
          <div style="flex: 1; display: flex; flex-direction: column;">
            <span id="ppg-status-text" style="font-size: 13px; font-weight: 800;">מוכן לסריקה</span>
            <span id="ppg-bpm-val" style="font-size: 20px; font-weight: 900; color: #ef4444;">-- BPM</span>
          </div>
          <button class="app-btn" id="btn-start-ppg" style="width: auto; padding: 8px 14px; font-size: 12px; min-height: 38px; height: 38px;" onclick="togglePpgScanner()">התחל סריקה</button>
        </div>
        <canvas id="ppg-chart-canvas" style="width: 100%; height: 40px; background: rgba(0,0,0,0.3); border-radius: 8px; display: none;"></canvas>
      </div>

      <!-- 3D Nebula -->
      <div style="display: flex; flex-direction: column; gap: 8px;">
        <span style="font-size: 13px; font-weight: 700; color: var(--muted);">🌌 ערפילית נשימה תלת-ממדית (3D Nebula):</span>
        <div class="tutorial-box">
          <div id="simulation-canvas-3d"></div>
        </div>
      </div>
    </div>

  </div>

  <!-- ─── MOBILE BOTTOM NAVIGATION BAR ─── -->
  <div class="mobile-tabs-nav hide-in-ambient">
    <button class="tab-nav-item active-tab" onclick="switchMobileTab('breath', this)">
      <span class="tab-nav-item-icon">🌬️</span>
      <span class="tab-nav-item-label">נשימה</span>
    </button>
    <button class="tab-nav-item" onclick="switchMobileTab('sound', this)">
      <span class="tab-nav-item-icon">🎙️</span>
      <span class="tab-nav-item-label">סאונד</span>
    </button>
    <button class="tab-nav-item" onclick="switchMobileTab('thoughts', this)">
      <span class="tab-nav-item-icon">💭</span>
      <span class="tab-nav-item-label">שחרור</span>
    </button>
    <button class="tab-nav-item" onclick="switchMobileTab('journal', this)">
      <span class="tab-nav-item-icon">📅</span>
      <span class="tab-nav-item-label">יומן</span>
    </button>
    <button class="tab-nav-item" onclick="switchMobileTab('bio', this)">
      <span class="tab-nav-item-icon">📸</span>
      <span class="tab-nav-item-label">ביומטריה</span>
    </button>
  </div>
</div>

<!-- ─── ONBOARDING & LOGIN CARD OVERLAY ─── -->
<div class="auth-overlay-backdrop" id="auth-overlay">
  <div class="auth-card" id="auth-card-element">
    
    <!-- שלב 1: הזנת פרטים (רישום / כניסה) -->
    <div id="auth-step-register" style="display: flex; flex-direction: column; gap: 20px;">
      <div class="auth-card-header">
        <h3 class="auth-card-title">כרטיס התחברות ל<span>רוגע</span></h3>
        <p class="auth-card-subtitle">צור או התחבר לחשבון הזן האישי שלך בצעדים פשוטים</p>
      </div>

      <div class="auth-form-group">
        <label class="auth-label" for="auth-first-name">שם פרטי</label>
        <input type="text" class="auth-input-field" id="auth-first-name" placeholder="manegro">
      </div>

      <div class="auth-form-group">
        <label class="auth-label" for="auth-last-name">שם משפחה</label>
        <input type="text" class="auth-input-field" id="auth-last-name" placeholder="קוסמי">
      </div>

      <div class="auth-form-group">
        <label class="auth-label" for="auth-phone">מספר טלפון נייד</label>
        <input type="text" class="auth-input-field" id="auth-phone" placeholder="050-0000000" maxlength="11">
      </div>

      <button class="app-btn" onclick="sendMockSmsOtp()">שלח קוד אימות בסמס 💬</button>
      
      <p style="font-size: 11px; color: var(--muted); text-align: center;">הנתונים שלך מגובים ומסונכרנים בענן באופן מוצפן לחלוטין ☁️</p>
    </div>

    <!-- שלב 2: אימות קוד OTP -->
    <div id="auth-step-verify" style="display: none; flex-direction: column; gap: 20px;">
      <div class="auth-card-header">
        <h3 class="auth-card-title">אימות <span>קוד כניסה</span></h3>
        <p class="auth-card-subtitle" id="auth-otp-sent-to-label">הזן את הקוד בן 4 הספרות ששלחנו למכשירך</p>
      </div>

      <div class="otp-container">
        <input type="tel" pattern="[0-9]*" inputmode="numeric" maxlength="1" class="otp-box" id="otp-1">
        <input type="tel" pattern="[0-9]*" inputmode="numeric" maxlength="1" class="otp-box" id="otp-2">
        <input type="tel" pattern="[0-9]*" inputmode="numeric" maxlength="1" class="otp-box" id="otp-3">
        <input type="tel" pattern="[0-9]*" inputmode="numeric" maxlength="1" class="otp-box" id="otp-4">
      </div>

      <div style="color: #ef4444; font-size: 13px; display: none; text-align: center; font-weight: 700;" id="auth-otp-error">קוד לא תקין, אנא נסה שוב.</div>

      <button class="app-btn" onclick="verifyMockOtp()">אמת קוד והתחבר 🧘</button>
      <button class="app-btn secondary" onclick="goBackToRegisterStep()">✕ חזור וערוך פרטים</button>
    </div>

  </div>
</div>

<!-- Simulated SMS Top Push Notification -->
<div class="simulated-sms-push" id="simulated-sms-banner">
  <div class="sms-header">
    <span style="font-weight: bold; color: var(--blue);">💬 רוגע INFINITE</span>
    <span>עכשיו</span>
  </div>
  <div class="sms-body" id="simulated-sms-body-text">
    קוד האימות החדש שלך לרוגע Infinite הוא: <strong>1234</strong>
  </div>
  <button class="app-btn" style="min-height: 32px; height: 32px; font-size: 11px; padding: 0 12px; background: rgba(59, 130, 246, 0.2); border: 1px solid var(--blue); color: var(--blue);" id="btn-sms-autofill" onclick="autoFillOtpAndLogin()">העתק והזן קוד אוטומטית ⚡</button>
</div>

<!-- ─── PWA INSTALLATION GUIDE MODAL (NEW) ─── -->
<div class="install-guide-backdrop" id="install-guide-overlay">
  <div class="install-guide-card">
    <div style="display: flex; justify-content: space-between; align-items: center; border-bottom: 1px solid var(--border); padding-bottom: 12px;">
      <h3 style="font-size: 16px; font-weight: 800;">📲 התקנת רוגע Infinite בנייד</h3>
      <button class="app-btn secondary" style="width: auto; min-height: 32px; height: 32px; padding: 0 10px;" onclick="closeInstallGuide()">✕</button>
    </div>
    
    <p style="font-size: 12px; color: var(--muted); margin-bottom: 4px;">התקן את האפליקציה למסך הבית שלך לקבלת חוויית מסך מלא פראית ללא דפדפנים!</p>
    
    <div style="display: flex; flex-direction: column; gap: 12px;">
      <div class="guide-step">
        <div class="guide-step-num">🍎</div>
        <div class="guide-step-text">
          <strong>מכשירי iPhone (Safari):</strong><br>
          לחץ על כפתור <strong>שיתוף</strong> (ריבוע עם חץ למעלה בתחתית) -> גלול מטה ובחר <strong>"הוסף למסך הבית" (Add to Home Screen)</strong>.
        </div>
      </div>
      
      <div class="guide-step">
        <div class="guide-step-num">🤖</div>
        <div class="guide-step-text">
          <strong>מכשירי Android (Chrome):</strong><br>
          לחץ על <strong>שלוש הנקודות</strong> בפינה העליונה -> בחר באפשרות <strong>"התקן אפליקציה" (Install App)</strong> או "הוסף למסך הבית".
        </div>
      </div>
    </div>
    
    <button class="app-btn" onclick="closeInstallGuide()" style="margin-top: 8px;">הבנתי, תודה ✨</button>
  </div>
</div>

<!-- מודל כתיבת יומן ומעקב ימים אינטראקטיבי (רפלקציה) -->
<div class="journal-modal" id="journal-day-modal">
  <div class="journal-modal-content">
    <div style="display: flex; justify-content: space-between; align-items: center; border-bottom: 1px solid var(--border); padding-bottom: 14px;">
      <h4 id="journal-modal-date" style="font-size: 16px; font-weight: 800;">תרגול ביום</h4>
      <button class="app-btn secondary" style="width: auto; padding: 4px 10px; font-size: 11px; min-height: 30px; height: 38px;" onclick="closeJournalDayModal()">✕</button>
    </div>
    
    <div style="display: flex; flex-direction: column; gap: 8px;">
      <label style="font-size: 13px; font-weight: 700; color: var(--muted);">סטטוס תרגול:</label>
      <div style="display: flex; align-items: center; gap: 10px; background: rgba(255,255,255,0.03); padding: 12px; border-radius: 12px; border: 1px solid var(--border);">
        <input type="checkbox" id="journal-modal-status-chk" style="width: 20px; height: 20px; accent-color: var(--green); cursor: pointer;">
        <label for="journal-modal-status-chk" style="font-size: 14px; font-weight: 500; cursor: pointer;">סמן כיום שבוצע בו תרגול מודעות! 🧘</label>
      </div>
    </div>

    <div style="display: flex; flex-direction: column; gap: 8px;">
      <label for="journal-modal-note-txt" style="font-size: 13px; font-weight: 700; color: var(--muted);">איך הרגשת? (יומן רפלקציה אישי):</label>
      <textarea class="ai-input" id="journal-modal-note-txt" placeholder="רשום כאן איך עבר עליך היום, manegro... האם השקט הועיל לך?" rows="3"></textarea>
    </div>

    <div style="display: flex; gap: 12px; margin-top: 8px;">
      <button class="app-btn" onclick="saveJournalDayData()">שמור שינויים ✨</button>
      <button class="app-btn secondary" onclick="closeJournalDayModal()">ביטול</button>
    </div>
  </div>
</div>

<!-- מסך ממיס מחשבות פעיל -->
<div class="thought-overlay" id="dissolver-overlay">
  <button class="app-btn secondary" style="position: absolute; top: 20px; right: 20px; width: auto; z-index: 2000; font-weight: 800; padding: 12px 24px; box-shadow: 0 4px 15px rgba(0,0,0,0.5);" onclick="closeThoughtDissolution()">✕ חזור לאפליקציה</button>
  <canvas id="thought-canvas"></canvas>
  <div class="thought-instructions">
    <h3 id="typed-thought-display" style="font-size: 24px; margin-bottom: 8px; color: #ffffff;">מחשבה מעיקה...</h3>
    <p style="color: #a5b4fc; font-size: 14px;">🖐️ בצע מחוות שפשוף מהירות על גבי המילים כדי להמיס אותן לחלקיקי אור</p>
  </div>
</div>

<!-- התראה מהירה חלופית -->
<div class="custom-toast" id="custom-toast">המדיטציה הושלמה בהצלחה!</div>

<!-- ─── FIREBASE & SCRIPT MANAGEMENT ─── -->
<script type="module">
import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
import { getAuth, signInWithCustomToken, signInAnonymously, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
import { getFirestore, doc, setDoc, getDoc } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";

// גלובליים ונתוני אתחול בטוחים
const firebaseConfig = typeof __firebase_config !== 'undefined' ? JSON.parse(__firebase_config) : null;
const appId = typeof __app_id !== 'undefined' ? __app_id : 'roga-app-2026';
const initialAuthToken = typeof __initial_auth_token !== 'undefined' ? __initial_auth_token : null;

let db = null;
let auth = null;
let currentUser = null;

let appState = {
  streak: 0,
  totalSessions: 0,
  totalMinutes: 0,
  completedDates: [],
  journalNotes: {}, // Key: YYYY-MM-DD, Value: String
  breathingActive: true,
  breathingPhase: 0, 
  breathingCountdown: 4,
  breathingInterval: null,
  aiInsightText: "",
  aiGenerated: false,
  userProfile: {
    firstName: "",
    lastName: "",
    phone: "",
    verified: false
  }
};

let tempGeneratedOtp = ""; // קוד האימות הזמני שיווצר

// אתחול דאטהסטור וענן (עמידה מלאה בחוק 3)
async function initDataStore() {
  if (firebaseConfig) {
    try {
      const app = initializeApp(firebaseConfig);
      auth = getAuth(app);
      db = getFirestore(app);

      if (initialAuthToken) {
        await signInWithCustomToken(auth, initialAuthToken);
      } else {
        await signInAnonymously(auth);
      }

      onAuthStateChanged(auth, async (user) => {
        if (user) {
          currentUser = user;
          await syncDataFromCloud();
        } else {
          loadLocalFallbackData();
          updateUI();
          renderCalendar();
        }
      });
    } catch(e) {
      console.warn("Fallback to local storage due to initialization error", e);
      loadLocalFallbackData();
      updateUI();
      renderCalendar();
    }
  } else {
    loadLocalFallbackData();
    updateUI();
    renderCalendar();
  }
}

async function saveUserDataCloud() {
  appState.completedDates = [...new Set(appState.completedDates)];
  try {
    if (db && currentUser) {
      const statsPath = `/artifacts/${appId}/users/${currentUser.uid}/stats/main`;
      await setDoc(doc(db, statsPath), {
        streak: appState.streak,
        totalSessions: appState.totalSessions,
        totalMinutes: appState.totalMinutes,
        completedDates: appState.completedDates,
        journalNotes: appState.journalNotes || {},
        aiGenerated: appState.aiGenerated
      }, { merge: true });

      const profilePath = `/artifacts/${appId}/users/${currentUser.uid}/profile/info`;
      await setDoc(doc(db, profilePath), appState.userProfile, { merge: true });
    }
  } catch(e) {
    console.error("Firestore sync write failed: ", e);
  }
  localStorage.setItem('roga_v3_local', JSON.stringify(appState));
}

async function syncDataFromCloud() {
  try {
    if (db && currentUser) {
      // 1. סנכרון פרופיל
      const profilePath = `/artifacts/${appId}/users/${currentUser.uid}/profile/info`;
      const profileSnap = await getDoc(doc(db, profilePath));
      if (profileSnap.exists()) {
        appState.userProfile = profileSnap.data();
      } else {
        const local = localStorage.getItem('roga_v3_local');
        if (local) {
          try {
            const data = JSON.parse(local);
            if (data.userProfile) appState.userProfile = data.userProfile;
          } catch(e){}
        }
      }

      // 2. סנכרון נתונים קוגניטיביים
      const statsPath = `/artifacts/${appId}/users/${currentUser.uid}/stats/main`;
      const docSnap = await getDoc(doc(db, statsPath));
      if (docSnap.exists()) {
        const data = docSnap.data();
        appState.streak = data.streak || 0;
        appState.totalSessions = data.totalSessions || 0;
        appState.totalMinutes = data.totalMinutes || 0;
        appState.completedDates = data.completedDates || [];
        appState.journalNotes = data.journalNotes || {};
        appState.aiGenerated = data.aiGenerated || false;
      } else {
        loadLocalFallbackData();
      }
      updateUI();
      renderCalendar();
    }
  } catch(e) {
    loadLocalFallbackData();
    updateUI();
    renderCalendar();
  }
}

function loadLocalFallbackData() {
  const local = localStorage.getItem('roga_v3_local');
  if (local) {
    try {
      const data = JSON.parse(local);
      appState.streak = data.streak || 0;
      appState.totalSessions = data.totalSessions || 0;
      appState.totalMinutes = data.totalMinutes || 0;
      appState.completedDates = data.completedDates || [];
      appState.journalNotes = data.journalNotes || {};
      appState.aiGenerated = data.aiGenerated || false;
      if (data.userProfile) appState.userProfile = data.userProfile;
    } catch(e){}
  }
}


/* ────────────────────────────────────────────────────────────────────────
   🌊 GENERATIVE BACKGROUND PARTICLES
   ──────────────────────────────────────────────────────────────────────── */
const generativeCanvas = document.getElementById('generative-canvas');
const gCtx = generativeCanvas.getContext('2d');

let particles = [];
let width = generativeCanvas.width = window.innerWidth;
let height = generativeCanvas.height = window.innerHeight;

window.addEventListener('resize', () => {
  width = generativeCanvas.width = window.innerWidth;
  height = generativeCanvas.height = window.innerHeight;
});

class Particle {
  constructor() {
    this.x = Math.random() * width;
    this.y = Math.random() * height;
    this.baseRadius = Math.random() * 2 + 1;
    this.radius = this.baseRadius;
    this.vx = (Math.random() - 0.5) * 0.4;
    this.vy = (Math.random() - 0.5) * 0.4;
    this.color = Math.random() > 0.5 ? '#3b82f6' : '#8b5cf6';
    this.alpha = Math.random() * 0.2 + 0.1;
  }

  update(breathingFactor) {
    const activeMultiplier = voiceAmplitude > 0 ? voiceAmplitude * 18 : breathingFactor * 4;
    this.x += this.vx * (1 + activeMultiplier);
    this.y += this.vy * (1 + activeMultiplier);

    if (this.x < 0 || this.x > width) this.vx *= -1;
    if (this.y < 0 || this.y > height) this.vy *= -1;
  }

  draw() {
    gCtx.beginPath();
    gCtx.arc(this.x, this.y, this.radius, 0, Math.PI * 2);
    gCtx.fillStyle = this.color;
    gCtx.globalAlpha = this.alpha;
    gCtx.fill();
  }
}

function initParticles() {
  particles = [];
  const count = Math.min(50, (width * height) / 14000);
  for (let i = 0; i < count; i++) {
    particles.push(new Particle());
  }
}

function animateBackground() {
  gCtx.clearRect(0, 0, width, height);

  const gradient = gCtx.createRadialGradient(width/2, height/2, 10, width/2, height/2, Math.max(width, height));
  
  if (document.body.classList.contains('theme-forest-rain')) {
    gradient.addColorStop(0, '#0a1c15');
    gradient.addColorStop(1, '#050c09');
  } else if (document.body.classList.contains('theme-sunset-calm')) {
    gradient.addColorStop(0, '#1a0e09');
    gradient.addColorStop(1, '#0e0704');
  } else if (document.body.classList.contains('theme-ethereal-light')) {
    gradient.addColorStop(0, '#f8fafc');
    gradient.addColorStop(1, '#e2e8f0');
  } else {
    gradient.addColorStop(0, '#050a1e');
    gradient.addColorStop(1, '#01030a');
  }

  gCtx.fillStyle = gradient;
  gCtx.globalAlpha = 1;
  gCtx.fillRect(0, 0, width, height);

  const factor = (currentOrbScale - 0.9) / 0.5;

  particles.forEach(p => {
    p.update(factor);
    p.draw();
  });

  requestAnimationFrame(animateBackground);
}


/* ────────────────────────────────────────────────────────────────────────
   🌬️ ORGANIC BREATHING ENGINE WITH PROGRESS RING, BIO-SYNC & HAPTICS
   ──────────────────────────────────────────────────────────────────────── */
let currentOrbScale = 1.0;
let isAmbientMode = false;

function toggleBreathingSystem() {
  const btn = document.getElementById('btn-breathe');
  if (appState.breathingActive) {
    appState.breathingActive = false;
    btn.textContent = '▶ המשך נשימה';
    clearInterval(appState.breathingInterval);
    pauseAllSyntheticOscillators();
  } else {
    appState.breathingActive = true;
    btn.textContent = '⏸ השהה נשימה';
    startBreathingEngine();
    resumeAllSyntheticOscillators();
  }
}

function startBreathingEngine() {
  if (appState.breathingInterval) clearInterval(appState.breathingInterval);
  
  runBreathingPhase();
  
  appState.breathingInterval = setInterval(() => {
    appState.breathingCountdown--;
    const numTimer = document.getElementById('nucleus-timer');
    if (numTimer) numTimer.textContent = appState.breathingCountdown;
    
    updateProgressRing(appState.breathingCountdown);
    
    if (appState.breathingCountdown <= 0) {
      appState.breathingPhase = (appState.breathingPhase + 1) % 4;
      appState.breathingCountdown = 4;
      playSyncChime();
    }
    
    runBreathingPhase();
  }, 1000);
}

function updateProgressRing(secondsLeft) {
  const circle = document.getElementById('progress-bar');
  if (!circle) return;
  const radius = circle.r.baseVal.value;
  const circumference = radius * 2 * Math.PI;
  
  const progressPercent = (secondsLeft / 4) * 100;
  const offset = circumference - (progressPercent / 100) * circumference;
  circle.style.strokeDashoffset = offset;
}

function runBreathingPhase() {
  const orb = document.getElementById('system-nucleus');
  const label = document.getElementById('nucleus-label');
  const instruction = document.getElementById('breathing-instruction-text');
  const circle = document.getElementById('progress-bar');
  if (!orb || !label || !instruction) return;
  
  // אם מנחה ה-AI מדבר ברקע, העיגול רוטט בסינכרון איתו (Voice-to-Scale Sync)!
  if (isSpeaking && voiceAmplitude > 0) {
    label.textContent = "מדבר...";
    instruction.textContent = "הקשב להדרכה הקולית ומלא את נפשך בשקט...";
    currentOrbScale = 1.0 + voiceAmplitude * 1.5;
    orb.style.transform = `scale(${currentOrbScale})`;
    orb.style.background = 'radial-gradient(circle at 30% 30%, var(--blue), var(--purple))';
    if(circle) circle.style.stroke = 'var(--purple)';
    return;
  }
  
  const hapticIntensity = (appState.breathingCountdown === 4) ? 80 : 0; 
  if (hapticIntensity > 0) {
    triggerHaptic(hapticIntensity);
  }

  switch(appState.breathingPhase) {
    case 0:
      label.textContent = "שאיפה";
      currentOrbScale = isAmbientMode ? 1.45 : 1.35;
      orb.style.transform = `scale(${currentOrbScale})`;
      orb.style.background = 'radial-gradient(circle at 30% 30%, var(--blue), var(--purple))';
      if(circle) circle.style.stroke = 'var(--blue)';
      instruction.textContent = "שאף אוויר דרך האף והרחב את הבטן...";
      instruction.style.color = 'var(--blue)';
      
      modulateSynthFilter(1200, 3.8);
      modulateOceanIntensity(0.8, 3.8);
      
      target3DScale = 0.6;
      target3DColor.setHex(0x3b82f6); 
      break;
    case 1:
      label.textContent = "עצירה";
      orb.style.background = 'radial-gradient(circle at 30% 30%, var(--purple), var(--blue))';
      if(circle) circle.style.stroke = 'var(--purple)';
      instruction.textContent = "החזק את האוויר בריאות בריכוז ובשקט...";
      instruction.style.color = 'var(--purple)';
      break;
    case 2:
      label.textContent = "נשיפה";
      currentOrbScale = isAmbientMode ? 0.85 : 0.95;
      orb.style.transform = `scale(${currentOrbScale})`;
      orb.style.background = 'radial-gradient(circle at 30% 30%, var(--purple), var(--green))';
      if(circle) circle.style.stroke = 'var(--green)';
      instruction.textContent = "נשוף לאט דרך הפה ושחרר את כל המתח...";
      instruction.style.color = 'var(--green)';
      
      modulateSynthFilter(280, 3.8);
      modulateOceanIntensity(0.15, 3.8);
      
      target3DScale = 1.45;
      target3DColor.setHex(0x10b981); 
      break;
    case 3:
      label.textContent = "עצירה";
      orb.style.background = 'radial-gradient(circle at 30% 30%, var(--green), var(--blue))';
      if(circle) circle.style.stroke = 'var(--blue)';
      instruction.textContent = "עצור והישאר במצב ריק, רגוע ונינוח...";
      instruction.style.color = 'var(--blue)';
      break;
  }
}

function triggerNucleusRipple() {
  const ring = document.getElementById('wave-effect');
  if (!ring) return;
  ring.style.transform = 'scale(2.5)';
  ring.style.opacity = '0.7';
  ring.style.transition = 'transform 1.6s ease-out, opacity 1.6s ease-out';
  
  setTimeout(() => {
    ring.style.transition = 'none';
    ring.style.transform = 'scale(1)';
    ring.style.opacity = '0';
  }, 1650);

  playTibetanBell();
}

function toggleAmbientProjectionMode() {
  const appOverlay = document.getElementById('interactive-app');
  const exitBtn = document.getElementById('btn-exit-ambient');

  if (!isAmbientMode) {
    isAmbientMode = true;
    appOverlay.classList.add('ambient-projection-active');
    if (exitBtn) exitBtn.style.display = 'block';
    showToast("מצב מקרן אטמוספרי פעיל 💡 הנח את המכשיר כלפי התקרה.");
  } else {
    isAmbientMode = false;
    appOverlay.classList.remove('ambient-projection-active');
    if (exitBtn) exitBtn.style.display = 'none';
  }
  
  runBreathingPhase();
}


/* ────────────────────────────────────────────────────────────────────────
   🎬 3D IMMERSIVE NEBULA (Three.js Engine)
   ──────────────────────────────────────────────────────────────────────── */
let scene3D, camera3D, renderer3D, particleSystem3D;
let target3DScale = 1.0;
let current3DScale = 1.0;
let target3DColor = new THREE.Color(0x3b82f6);
let current3DColor = new THREE.Color(0x3b82f6);

let isDragging3D = false;
let previousMousePosition = { x: 0, y: 0 };

function init3DNebula() {
  const container = document.getElementById('simulation-canvas-3d');
  if (!container) return;

  // תיקון מימדים גלובליים בטוחים למניעת מסך שחור
  const width3D = container.clientWidth || window.innerWidth - 64;
  const height3D = container.clientHeight || 250;

  scene3D = new THREE.Scene();
  scene3D.fog = new THREE.FogExp2(0x000000, 0.005);

  camera3D = new THREE.PerspectiveCamera(60, width3D / height3D, 1, 1000);
  camera3D.position.z = 150;

  renderer3D = new THREE.WebGLRenderer({ antialias: true, alpha: true });
  renderer3D.setSize(width3D, height3D);
  renderer3D.setPixelRatio(Math.min(window.devicePixelRatio, 2));
  container.innerHTML = "";
  container.appendChild(renderer3D.domElement);

  const particleCount = 2000;
  const geometry = new THREE.BufferGeometry();
  const positions = new Float32Array(particleCount * 3);
  const originalDistances = new Float32Array(particleCount);

  for (let i = 0; i < particleCount; i++) {
    const u = Math.random();
    const v = Math.random();
    const theta = u * 2.0 * Math.PI;
    const phi = Math.acos(2.0 * v - 1.0);
    const r = 35 + Math.random() * 40; 

    const x = r * Math.sin(phi) * Math.cos(theta);
    const y = r * Math.sin(phi) * Math.sin(theta);
    const z = r * Math.cos(phi);

    positions[i * 3] = x;
    positions[i * 3 + 1] = y;
    positions[i * 3 + 2] = z;

    originalDistances[i] = r;
  }

  geometry.setAttribute('position', new THREE.BufferAttribute(positions, 3));

  const material = new THREE.PointsMaterial({
    size: 2.5,
    transparent: true,
    opacity: 0.9,
    blending: THREE.AdditiveBlending,
    depthWrite: false
  });

  particleSystem3D = new THREE.Points(geometry, material);
  scene3D.add(particleSystem3D);

  const ambientLight = new THREE.AmbientLight(0xffffff, 0.6);
  scene3D.add(ambientLight);

  container.addEventListener('mousedown', (e) => {
    isDragging3D = true;
    previousMousePosition = { x: e.offsetX, y: e.offsetY };
  });
  
  container.addEventListener('touchstart', (e) => {
    isDragging3D = true;
    if (e.touches.length > 0) {
      const rect = container.getBoundingClientRect();
      previousMousePosition = { 
        x: e.touches[0].clientX - rect.left, 
        y: e.touches[0].clientY - rect.top 
      };
    }
  });

  window.addEventListener('mouseup', () => { isDragging3D = false; });
  window.addEventListener('touchend', () => { isDragging3D = false; });

  container.addEventListener('mousemove', (e) => {
    if (!isDragging3D) return;
    const deltaMove = {
      x: e.offsetX - previousMousePosition.x,
      y: e.offsetY - previousMousePosition.y
    };

    particleSystem3D.rotation.y += deltaMove.x * 0.007;
    particleSystem3D.rotation.x += deltaMove.y * 0.007;

    previousMousePosition = { x: e.offsetX, y: e.offsetY };
  });

  container.addEventListener('touchmove', (e) => {
    if (!isDragging3D || e.touches.length === 0) return;
    const touch = e.touches[0];
    const rect = container.getBoundingClientRect();
    const currentTouchPos = { x: touch.clientX - rect.left, y: touch.clientY - top };

    const deltaMove = {
      x: currentTouchPos.x - previousMousePosition.x,
      y: currentTouchPos.y - previousMousePosition.y
    };

    particleSystem3D.rotation.y += deltaMove.x * 0.01;
    particleSystem3D.rotation.x += deltaMove.y * 0.01;

    previousMousePosition = currentTouchPos;
  });

  window.addEventListener('resize', resize3D);

  function animate3D() {
    requestAnimationFrame(animate3D);

    if (!isDragging3D) {
      particleSystem3D.rotation.y += 0.002;
      particleSystem3D.rotation.z += 0.0008;
    }

    current3DScale += (target3DScale - current3DScale) * 0.05;
    particleSystem3D.scale.set(current3DScale, current3DScale, current3DScale);

    current3DColor.lerp(target3DColor, 0.05);
    particleSystem3D.material.color.copy(current3DColor);

    const positions = particleSystem3D.geometry.attributes.position.array;
    const time = Date.now() * 0.001;
    
    for (let i = 0; i < positions.length; i += 3) {
      positions[i] += Math.sin(time + i) * 0.04;
      positions[i+1] += Math.cos(time + i) * 0.04;
    }
    particleSystem3D.geometry.attributes.position.needsUpdate = true;

    renderer3D.render(scene3D, camera3D);
  }

  animate3D();
}

function resize3D() {
  if (!renderer3D || !camera3D) return;
  const container = document.getElementById('simulation-canvas-3d');
  if (!container) return;
  const w = container.clientWidth || window.innerWidth - 64;
  const h = container.clientHeight || 250;
  camera3D.aspect = w / h;
  camera3D.updateProjectionMatrix();
  renderer3D.setSize(w, h);
}


/* ────────────────────────────────────────────────────────────────────────
   🎵 WEB AUDIO API: SYNTHETIC HEALING MIXER (Stereo + Layering + Melody)
   ──────────────────────────────────────────────────────────────────────── */
const audioState = {
  ctx: null,
  master: null,
  lowpassFilter: null,
  binauralGain: null,
  oceanGain: null,
  bowlGain: null,
  binauralOscL: null,
  binauralOscR: null,
  pannerL: null,
  pannerR: null,
  oceanSource: null,
  oceanModulator: null,
  oceanModulatorGain: null,
  padSynthL: null,
  padSynthR: null,
  padGain: null,
  melodyInterval: null,
  volBinaural: 0.3,
  volOcean: 0.0,
  volBowl: 0.3
};

function initAudioSystem() {
  if (audioState.ctx) return;
  try {
    const AudioCtx = window.AudioContext || window.webkitAudioContext;
    audioState.ctx = new AudioCtx();
    
    audioState.master = audioState.ctx.createGain();
    audioState.master.gain.setValueAtTime(0.20, audioState.ctx.currentTime);
    audioState.master.connect(audioState.ctx.destination);
    
    audioState.lowpassFilter = audioState.ctx.createBiquadFilter();
    audioState.lowpassFilter.type = 'lowpass';
    audioState.lowpassFilter.frequency.setValueAtTime(450, audioState.ctx.currentTime);
    audioState.lowpassFilter.Q.setValueAtTime(1, audioState.ctx.currentTime);
    audioState.lowpassFilter.connect(audioState.master);

    audioState.binauralGain = audioState.ctx.createGain();
    audioState.binauralGain.gain.setValueAtTime(0.3, audioState.ctx.currentTime);
    audioState.binauralGain.connect(audioState.lowpassFilter);
    
    audioState.oceanGain = audioState.ctx.createGain();
    audioState.oceanGain.gain.setValueAtTime(0, audioState.ctx.currentTime);
    audioState.oceanGain.connect(audioState.master);
    
    audioState.bowlGain = audioState.ctx.createGain();
    audioState.bowlGain.gain.setValueAtTime(0.3, audioState.ctx.currentTime);
    audioState.bowlGain.connect(audioState.master);

    audioState.padGain = audioState.ctx.createGain();
    audioState.padGain.gain.setValueAtTime(0.0, audioState.ctx.currentTime); 
    audioState.padGain.connect(audioState.lowpassFilter);
  } catch(e) {
    console.warn("Audio initialization bypassed.", e);
  }
}

function adjustVolume(type, val) {
  initAudioSystem();
  if (audioState.ctx && audioState.ctx.state === 'suspended') {
    audioState.ctx.resume();
  }
  if (!audioState.ctx) return;
  
  const floatVal = val / 100;
  const now = audioState.ctx.currentTime;
  
  if (type === 'binaural') {
    audioState.volBinaural = floatVal;
    audioState.binauralGain.gain.linearRampToValueAtTime(floatVal, now + 0.15);
  } else if (type === 'ocean') {
    audioState.volOcean = floatVal;
    audioState.oceanGain.gain.linearRampToValueAtTime(floatVal, now + 0.15);
  }
  
  if (appState.breathingActive) {
    resumeAllSyntheticOscillators();
  }
}

function resumeAllSyntheticOscillators() {
  initAudioSystem();
  if (!audioState.ctx) return;
  if (audioState.ctx.state === 'suspended') {
    audioState.ctx.resume();
  }
  
  const now = audioState.ctx.currentTime;
  
  if (!audioState.binauralOscL) {
    audioState.binauralOscL = audioState.ctx.createOscillator();
    audioState.binauralOscR = audioState.ctx.createOscillator();
    
    audioState.pannerL = audioState.ctx.createStereoPanner();
    audioState.pannerR = audioState.ctx.createStereoPanner();
    
    audioState.pannerL.pan.setValueAtTime(-1, now); 
    audioState.pannerR.pan.setValueAtTime(1, now);  
    
    audioState.binauralOscL.frequency.setValueAtTime(110, now); 
    audioState.binauralOscR.frequency.setValueAtTime(116, now); 
    
    audioState.binauralOscL.type = 'sine';
    audioState.binauralOscR.type = 'sine';
    
    audioState.binauralOscL.connect(audioState.pannerL).connect(audioState.binauralGain);
    audioState.binauralOscR.connect(audioState.pannerR).connect(audioState.binauralGain);
    
    audioState.binauralOscL.start();
    audioState.binauralOscR.start();
  }
  
  if (!audioState.oceanSource) {
    const bufferSize = 4 * audioState.ctx.sampleRate;
    const noiseBuffer = audioState.ctx.createBuffer(1, bufferSize, audioState.ctx.sampleRate);
    const output = noiseBuffer.getChannelData(0);
    
    let b0, b1, b2, b3, b4, b5, b6;
    b0 = b1 = b2 = b3 = b4 = b5 = b6 = 0.0;
    for (let i = 0; i < bufferSize; i++) {
      const white = Math.random() * 2 - 1;
      b0 = 0.99886 * b0 + white * 0.0555179;
      b1 = 0.99332 * b1 + white * 0.0750759;
      b2 = 0.96900 * b2 + white * 0.1538520;
      b3 = 0.86650 * b3 + white * 0.3104856;
      b4 = 0.55000 * b4 + white * 0.5329522;
      b5 = -0.7616 * b5 - white * 0.0168980;
      output[i] = b0 + b1 + b2 + b3 + b4 + b5 + b6 + white * 0.5362;
      output[i] *= 0.11; 
      b6 = white * 0.115926;
    }
    
    audioState.oceanSource = audioState.ctx.createBufferSource();
    audioState.oceanSource.buffer = noiseBuffer;
    audioState.oceanSource.loop = true;
    
    const oFilter = audioState.ctx.createBiquadFilter();
    oFilter.type = 'lowpass';
    oFilter.frequency.setValueAtTime(220, now);
    
    audioState.oceanModulator = audioState.ctx.createOscillator();
    audioState.oceanModulatorGain = audioState.ctx.createGain();
    
    audioState.oceanModulator.frequency.setValueAtTime(0.08, now); 
    audioState.oceanModulatorGain.gain.setValueAtTime(80, now);
    
    audioState.oceanModulator.connect(audioState.oceanModulatorGain);
    audioState.oceanModulatorGain.connect(oFilter.frequency);
    
    audioState.oceanSource.connect(oFilter).connect(audioState.oceanGain);
    
    audioState.oceanModulator.start();
    audioState.oceanSource.start();
  }
}

function pauseAllSyntheticOscillators() {
  if (audioState.binauralOscL) { try { audioState.binauralOscL.stop(); } catch(e){} audioState.binauralOscL = null; }
  if (audioState.binauralOscR) { try { audioState.binauralOscR.stop(); } catch(e){} audioState.binauralOscR = null; }
  if (audioState.oceanSource) { try { audioState.oceanSource.stop(); } catch(e){} audioState.oceanSource = null; }
  if (audioState.oceanModulator) { try { audioState.oceanModulator.stop(); } catch(e){} audioState.oceanModulator = null; }
  stopGenerativeAudioLayers();
}

function modulateSynthFilter(target, duration) {
  if (!audioState.lowpassFilter || !audioState.ctx) return;
  audioState.lowpassFilter.frequency.exponentialRampToValueAtTime(target, audioState.ctx.currentTime + duration);
}

function modulateOceanIntensity(targetFactor, duration) {
  if (!audioState.oceanGain || !audioState.ctx) return;
  const targetVol = audioState.volOcean * targetFactor;
  audioState.oceanGain.gain.linearRampToValueAtTime(targetVol, audioState.ctx.currentTime + duration);
}

function updateGenerativeAudioLevel(secondsLeft) {
  if (!audioState.ctx) return;
  const now = audioState.ctx.currentTime;
  
  if (secondsLeft <= 120 && !audioState.padSynthL) {
    audioState.padSynthL = audioState.ctx.createOscillator();
    audioState.padSynthR = audioState.ctx.createOscillator();
    
    audioState.padSynthL.type = 'triangle';
    audioState.padSynthR.type = 'triangle';
    
    audioState.padSynthL.frequency.setValueAtTime(110, now); 
    audioState.padSynthR.frequency.setValueAtTime(165, now); 
    
    const pannerL = audioState.ctx.createStereoPanner();
    const pannerR = audioState.ctx.createStereoPanner();
    pannerL.pan.setValueAtTime(-0.8, now);
    pannerR.pan.setValueAtTime(0.8, now);
    
    audioState.padSynthL.connect(pannerL).connect(audioState.padGain);
    audioState.padSynthR.connect(pannerR).connect(audioState.padGain);
    
    audioState.padSynthL.start();
    audioState.padSynthR.start();
    
    audioState.padGain.gain.linearRampToValueAtTime(0.25, now + 10);
    showToast("המשך לתרגל. צלילים מרפאים חדשים נוספו ברקע... 🌌");
  }
  
  if (secondsLeft <= 60 && !audioState.melodyInterval) {
    const notes = [220, 247, 293, 330, 392, 440]; 
    
    audioState.melodyInterval = setInterval(() => {
      if (!isSessionRunning || !audioState.ctx) return;
      const note = notes[Math.floor(Math.random() * notes.length)];
      playGenerativeMelodyNote(note);
    }, 4500);
    
    showToast("חצי הדרך מאחוריך! מנגינת קוסמוס נוצרת ברקע... 🔔");
  }
}

function playGenerativeMelodyNote(freq) {
  if (!audioState.ctx) return;
  const now = audioState.ctx.currentTime;
  
  const osc = audioState.ctx.createOscillator();
  const gain = audioState.ctx.createGain();
  const panner = audioState.ctx.createStereoPanner();
  
  osc.type = 'sine';
  osc.frequency.setValueAtTime(freq, now);
  
  gain.gain.setValueAtTime(0, now);
  gain.gain.linearRampToValueAtTime(0.04, now + 0.1);
  gain.gain.exponentialRampToValueAtTime(0.0001, now + 5.0);
  
  panner.pan.setValueAtTime(Math.random() * 2 - 1, now);
  
  osc.connect(panner).connect(gain).connect(audioState.lowpassFilter);
  osc.start();
  osc.stop(now + 5.2);
}

function stopGenerativeAudioLayers() {
  if (audioState.padSynthL) { try { audioState.padSynthL.stop(); } catch(e){} audioState.padSynthL = null; }
  if (audioState.padSynthR) { try { audioState.padSynthR.stop(); } catch(e){} audioState.padSynthR = null; }
  if (audioState.padGain) { audioState.padGain.gain.setValueAtTime(0, audioState.ctx?.currentTime || 0); }
  if (audioState.melodyInterval) { clearInterval(audioState.melodyInterval); audioState.melodyInterval = null; }
}

function playTibetanBell() {
  initAudioSystem();
  if (!audioState.ctx) return;
  const now = audioState.ctx.currentTime;
  
  const partials = [180, 271, 358, 544];
  partials.forEach((f, idx) => {
    const osc = audioState.ctx.createOscillator();
    const gainNode = audioState.ctx.createGain();
    
    osc.frequency.setValueAtTime(f, now);
    const volumeFactor = idx === 0 ? 0.15 : 0.05;
    gainNode.gain.setValueAtTime(volumeFactor * audioState.volBowl, now);
    gainNode.gain.exponentialRampToValueAtTime(0.0001, now + 8);
    
    osc.connect(gainNode).connect(audioState.bowlGain);
    osc.start();
    osc.stop(now + 8.2);
  });
}

function triggerBowlBell() {
  playTibetanBell();
  showToast("צליל קערה טיבטית הופעל 🔔");
}

function playSyncChime() {
  if (!audioState.ctx) return;
  const osc = audioState.ctx.createOscillator();
  const gain = audioState.ctx.createGain();
  osc.frequency.setValueAtTime(660, audioState.ctx.currentTime);
  gain.gain.setValueAtTime(0.02, audioState.currentTime);
  gain.gain.exponentialRampToValueAtTime(0.0001, audioState.ctx.currentTime + 1.5);
  osc.connect(gain).connect(audioState.master);
  osc.start();
  osc.stop(audioState.ctx.currentTime + 1.6);
}


/* ────────────────────────────────────────────────────────────────────────
   💭 TACTILE THOUGHT DISSOLVER
   ──────────────────────────────────────────────────────────────────────── */
const thoughtCanvas = document.getElementById('thought-canvas');
const tCtx = thoughtCanvas.getContext('2d');
const overlay = document.getElementById('dissolver-overlay');

const maskCanvas = document.createElement('canvas');
const mCtx = maskCanvas.getContext('2d');

let tWidth = thoughtCanvas.width = maskCanvas.width = window.innerWidth;
let tHeight = thoughtCanvas.height = maskCanvas.height = window.innerHeight;

let scratchDistance = 0;
let isScratching = false;
let thoughtText = "";
let sparkles = [];

window.addEventListener('resize', () => {
  tWidth = thoughtCanvas.width = maskCanvas.width = window.innerWidth;
  tHeight = thoughtCanvas.height = maskCanvas.height = window.innerHeight;
});

function startThoughtDissolution() {
  const input = document.getElementById('thought-input');
  thoughtText = input.value.trim();
  
  if (!thoughtText) {
    showToast(`הכנס בבקשה מחשבה כדי להמיס אותה, ${appState.userProfile.firstName || 'manegro'}...`);
    return;
  }
  
  document.getElementById('typed-thought-display').textContent = `"${thoughtText}"`;
  overlay.classList.add('active');
  
  mCtx.clearRect(0, 0, tWidth, tHeight);
  scratchDistance = 0;
  sparkles = [];
}

class Sparkle {
  constructor(x, y) {
    this.x = x;
    this.y = y;
    this.size = Math.random() * 5 + 2;
    this.vx = (Math.random() - 0.5) * 6;
    this.vy = (Math.random() - 0.5) * 6;
    this.life = 1.0;
    this.decay = Math.random() * 0.025 + 0.015;
    this.color = `hsl(${Math.random() * 60 + 250}, 100%, 75%)`; 
  }
  update() {
    this.x += this.vx;
    this.y += this.vy;
    this.life -= this.decay;
  }
  draw() {
    tCtx.save();
    tCtx.beginPath();
    tCtx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
    tCtx.fillStyle = this.color;
    tCtx.globalAlpha = this.life;
    tCtx.fill();
    tCtx.restore();
  }
}

function renderDissolver() {
  if (!overlay.classList.contains('active')) {
    requestAnimationFrame(renderDissolver);
    return;
  }
  
  tCtx.fillStyle = '#020409';
  tCtx.fillRect(0, 0, tWidth, tHeight);
  
  tCtx.save();
  const fontSize = Math.min(28, tWidth / 15);
  tCtx.font = `300 ${fontSize}px 'Heebo', sans-serif`;
  tCtx.textBaseline = 'middle';
  tCtx.textAlign = 'center';
  tCtx.fillStyle = '#ffffff';
  tCtx.shadowColor = '#8b5cf6';
  tCtx.shadowBlur = 20;
  
  const maxLineW = tWidth - 40;
  const words = thoughtText.split(' ');
  let line = '';
  let yOffset = tHeight / 2;
  const lines = [];
  
  for (let n = 0; n < words.length; n++) {
    let testLine = line + words[n] + ' ';
    let metrics = tCtx.measureText(testLine);
    if (metrics.width > maxLineW && n > 0) {
      lines.push(line);
      line = words[n] + ' ';
    } else {
      line = testLine;
    }
  }
  lines.push(line);
  
  lines.forEach((l, idx) => {
    tCtx.fillText(l.trim(), tWidth / 2, yOffset + (idx - (lines.length - 1) / 2) * (fontSize + 12));
  });
  tCtx.restore();
  
  tCtx.save();
  tCtx.globalCompositeOperation = 'destination-out';
  tCtx.drawImage(maskCanvas, 0, 0);
  tCtx.restore();

  sparkles.forEach((s, idx) => {
    s.update();
    if (s.life <= 0) {
      sparkles.splice(idx, 1);
    } else {
      s.draw();
    }
  });

  if (scratchDistance > 3000) {
    completeThoughtDissolve();
  }

  requestAnimationFrame(renderDissolver);
}
requestAnimationFrame(renderDissolver);

thoughtCanvas.addEventListener('mousedown', (e) => {
  isScratching = true;
  handleScratch(e.clientX, e.clientY);
});
thoughtCanvas.addEventListener('mouseup', () => isScratching = false);
thoughtCanvas.addEventListener('mousemove', (e) => handleScratch(e.clientX, e.clientY));

thoughtCanvas.addEventListener('touchstart', (e) => {
  isScratching = true;
  if(e.touches.length > 0) {
    handleScratch(e.touches[0].clientX, e.touches[0].clientY);
  }
  e.preventDefault();
}, { passive: false });
thoughtCanvas.addEventListener('touchend', () => isScratching = false);
thoughtCanvas.addEventListener('touchmove', (e) => {
  if (e.touches.length > 0) {
    handleScratch(e.touches[0].clientX, e.touches[0].clientY);
  }
  e.preventDefault();
}, { passive: false });

function handleScratch(x, y) {
  if (!isScratching) return;
  
  mCtx.save();
  mCtx.beginPath();
  mCtx.arc(x, y, 40, 0, Math.PI * 2);
  mCtx.fillStyle = '#000000';
  mCtx.fill();
  mCtx.restore();
  
  scratchDistance += 15;

  if (Math.random() > 0.3) {
    for (let i = 0; i < 5; i++) {
      sparkles.push(new Sparkle(x, y));
    }
  }
}

function completeThoughtDissolve() {
  playTibetanBell();
  showToast("המחשבה התמוססה בהצלחה אל האור 🌌");
  closeThoughtDissolution();
}

function closeThoughtDissolution() {
  overlay.classList.remove('active');
  document.getElementById('thought-input').value = "";
}


/* ────────────────────────────────────────────────────────────────────────
   🎙️ AI SPEECH STUDIO & SECURE SPEECH PLAYBACK
   ──────────────────────────────────────────────────────────────────────── */
let voiceAmplitude = 0;
let liveVoiceAnim = null;
let isSpeaking = false;
let voiceAnalyser = null;
let ttsAudioSource = null;
let voiceEffectNodes = []; 

function selectQuickMood(moodText) {
  const inputGroup = document.getElementById('ai-user-mood');
  if (inputGroup) inputGroup.value = moodText;
  document.querySelectorAll('.mood-tag').forEach(tag => tag.classList.remove('selected'));
  const tags = document.querySelectorAll('.mood-tag');
  tags.forEach(tag => {
    if (moodText.includes(tag.textContent.substring(2))) {
      tag.classList.add('selected');
    }
  });
}

function createAcousticProcessor(sourceNode) {
  if (!audioState.ctx) return sourceNode;
  const now = audioState.ctx.currentTime;
  const mode = document.getElementById('ai-acoustic-select').value;
  
  if (mode === 'dry') {
    return sourceNode; 
  }
  
  const delayNode = audioState.ctx.createDelay(1.0);
  const feedbackGain = audioState.ctx.createGain();
  const filterNode = audioState.ctx.createBiquadFilter();
  
  filterNode.type = 'lowpass';
  
  if (mode === 'temple') {
    delayNode.delayTime.setValueAtTime(0.38, now);
    feedbackGain.gain.setValueAtTime(0.35, now);
    filterNode.frequency.setValueAtTime(800, now);
  } else if (mode === 'cave') {
    delayNode.delayTime.setValueAtTime(0.20, now);
    feedbackGain.gain.setValueAtTime(0.52, now);
    filterNode.frequency.setValueAtTime(450, now);
  } else if (mode === 'space') {
    delayNode.delayTime.setValueAtTime(0.65, now);
    feedbackGain.gain.setValueAtTime(0.40, now);
    filterNode.frequency.setValueAtTime(1200, now);
  }
  
  sourceNode.connect(delayNode);
  delayNode.connect(filterNode);
  filterNode.connect(feedbackGain);
  feedbackGain.connect(delayNode);
  
  const dryGain = audioState.ctx.createGain();
  const wetGain = audioState.ctx.createGain();
  
  dryGain.gain.setValueAtTime(1.0, now);
  wetGain.gain.setValueAtTime(0.38, now); 
  
  sourceNode.connect(dryGain);
  filterNode.connect(wetGain);
  
  const mergerNode = audioState.ctx.createGain();
  dryGain.connect(mergerNode);
  wetGain.connect(mergerNode);
  
  voiceEffectNodes.push(delayNode, feedbackGain, filterNode, dryGain, wetGain, mergerNode);
  return mergerNode;
}

async function generateAiInsight() {
  const apiKey = "";
  const mood = document.getElementById('ai-user-mood').value.trim();
  const resBlock = document.getElementById('ai-response-block');
  const resContent = document.getElementById('ai-response-content');
  const statusIndicator = document.getElementById('voice-studio-status');
  
  if (!mood) {
    showToast("אנא בחר מצב רוח או הקלד הרגשה, manegro...");
    return;
  }
  
  resBlock.style.display = 'block';
  resContent.textContent = `מפענח את תדרי המוח ומסנתז הדרכה קולית מותאמת אישית ברמת אולפן עבורך, ${appState.userProfile.firstName || 'manegro'}...`;
  if(statusIndicator) {
    statusIndicator.textContent = "סופר זן...";
    statusIndicator.style.color = "var(--purple)";
  }
  
  const systemPrompt = `You are a professional Hebrew mindfulness guide.
The user is a male named '${appState.userProfile.firstName || 'manegro'}'. Address him personally, warmly and with deep zen respect as '${appState.userProfile.firstName || 'manegro'}' in Hebrew (masculine form).
Generate a deeply relaxing, personalized, 20-25 word Hebrew meditation mantra strictly tailored to his emotional state. Use calm, zen phrasing. Keep the tone loving and peaceful.`;
  
  const url = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-09-2025:generateContent?key=${apiKey}`;
  const payload = {
    contents: [{ parts: [{ text: mood }] }],
    systemInstruction: { parts: [{ text: systemPrompt }] }
  };
  
  try {
    const result = await fetchWithRetry(url, {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify(payload)
    });
    
    const text = result.candidates?.[0]?.content?.parts?.[0]?.text;
    if (text) {
      appState.aiInsightText = text;
      appState.aiGenerated = true;
      resContent.textContent = text;
      if(statusIndicator) {
        statusIndicator.textContent = "הושלם";
        statusIndicator.style.color = "var(--green)";
      }
      saveUserDataCloud();
      updateUI();
    }
  } catch (err) {
    resContent.textContent = "שגיאה זמנית בחיבור לרשת הקוסמית. נסה שוב.";
    if(statusIndicator) {
      statusIndicator.textContent = "שגיאה";
      statusIndicator.style.color = "red";
    }
  }
}

async function speakAiInsight() {
  if (isSpeaking) {
    stopAiVoicePlayback();
    return;
  }
  
  if (!appState.aiInsightText) return;
  
  const apiKey = "";
  const voice = document.getElementById('ai-voice-select').value;
  const speakBtn = document.getElementById('btn-speak-ai');
  const statusIndicator = document.getElementById('voice-studio-status');
  
  speakBtn.textContent = "⏳ מסנתז...";
  if(statusIndicator) statusIndicator.textContent = "משדר...";
  
  const url = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-tts:generateContent?key=${apiKey}`;
  const payload = {
    contents: [{ parts: [{ text: `Say warmly: ${appState.aiInsightText}` }] }],
    generationConfig: {
      responseModalities: ["AUDIO"],
      speechConfig: { voiceConfig: { prebuiltVoiceConfig: { voiceName: voice } } }
    },
    model: "gemini-2.5-flash-preview-tts"
  };
  
  try {
    const response = await fetchWithRetry(url, {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify(payload)
    });
    const pcmBase64 = response.candidates?.[0]?.content?.parts?.find(p => p.inlineData)?.inlineData?.data;
    if (pcmBase64) {
      const wavBlob = pcmToWav(pcmBase64, 24000);
      
      const fileReader = new FileReader();
      fileReader.onload = async function() {
        const arrayBuffer = this.result;
        initAudioSystem();
        if (audioState.ctx) {
          audioState.ctx.decodeAudioData(arrayBuffer, function(buffer) {
            playAudioBuffer(buffer);
            speakBtn.textContent = "⏹ עצור הדרכה";
          }, function(e) {
            showToast("שגיאה בפענוח סאונד.");
            speakBtn.textContent = "🔊 הקרא בקול AI";
          });
        }
      };
      fileReader.readAsArrayBuffer(wavBlob);
    }
  } catch(e) {
    showToast("הקריינות נכשלה.");
    speakBtn.textContent = "🔊 הקרא בקול AI";
  }
}

function playAudioBuffer(buffer) {
  if (!audioState.ctx) return;
  
  ttsAudioSource = audioState.ctx.createBufferSource();
  ttsAudioSource.buffer = buffer;
  
  voiceAnalyser = audioState.ctx.createAnalyser();
  voiceAnalyser.fftSize = 256; 
  
  const processedVoice = createAcousticProcessor(ttsAudioSource);
  processedVoice.connect(voiceAnalyser).connect(audioState.master);
  
  ttsAudioSource.start(0);
  isSpeaking = true;
  
  drawLiveVoiceSpectrum();
  runBreathingPhase();
  
  ttsAudioSource.onended = () => {
    stopAiVoicePlayback();
  };
}

function stopAiVoicePlayback() {
  isSpeaking = false;
  voiceAmplitude = 0;
  if (ttsAudioSource) {
    try { ttsAudioSource.stop(); } catch(e){}
    ttsAudioSource = null;
  }
  
  voiceEffectNodes.forEach(node => {
    try { node.disconnect(); } catch(e){}
  });
  voiceEffectNodes = [];

  if (liveVoiceAnim) cancelAnimationFrame(liveVoiceAnim);
  
  const speakBtn = document.getElementById('btn-speak-ai');
  if (speakBtn) speakBtn.textContent = "🔊 הקרא בקול AI";
  
  const statusIndicator = document.getElementById('voice-studio-status');
  if (statusIndicator) {
    statusIndicator.textContent = "מוכן";
    statusIndicator.style.color = "var(--green)";
  }
  
  const vCanvas = document.getElementById('voice-visualizer');
  if (vCanvas) {
    const vCtx = vCanvas.getContext('2d');
    vCtx.clearRect(0, 0, vCanvas.width, vCanvas.height);
  }
  
  runBreathingPhase();
}

function drawLiveVoiceSpectrum() {
  if (!isSpeaking || !voiceAnalyser) return;
  
  const vCanvas = document.getElementById('voice-visualizer');
  if (!vCanvas) return;
  
  const vCtx = vCanvas.getContext('2d');
  const bufferLength = voiceAnalyser.frequencyBinCount;
  const dataArray = new Uint8Array(bufferLength);
  
  voiceAnalyser.getByteFrequencyData(dataArray);
  
  vCtx.clearRect(0, 0, vCanvas.width, vCanvas.height);
  
  let sum = 0;
  for (let i = 0; i < bufferLength; i++) {
    sum += dataArray[i];
  }
  voiceAmplitude = (sum / bufferLength) / 100;

  const time = Date.now() * 0.007;
  const amp = voiceAmplitude * vCanvas.height * 0.8;
  
  const waveLayers = [
    { color: 'rgba(59, 130, 246, 0.65)', speed: 1.0, phase: 0, density: 7 },
    { color: 'rgba(139, 92, 246, 0.45)', speed: 0.7, phase: Math.PI / 2, density: 5 },
    { color: 'rgba(16, 185, 129, 0.25)', speed: 1.3, phase: Math.PI, density: 9 }
  ];

  waveLayers.forEach(w => {
    vCtx.strokeStyle = w.color;
    vCtx.lineWidth = 2.0;
    vCtx.beginPath();
    
    for (let x = 0; x < vCanvas.width; x++) {
      const progress = x / vCanvas.width;
      const envelope = Math.sin(progress * Math.PI); 
      const y = vCanvas.height / 2 + Math.sin(progress * w.density + time * w.speed + w.phase) * amp * envelope;
      
      if (x === 0) {
        vCtx.moveTo(x, y);
      } else {
        vCtx.lineTo(x, y);
      }
    }
    vCtx.stroke();
  });
  
  liveVoiceAnim = requestAnimationFrame(drawLiveVoiceSpectrum);
}


/* ────────────────────────────────────────────────────────────────────────
   ⏱️ ACTIVE MEDITATION SESSION TRACKER
   ──────────────────────────────────────────────────────────────────────── */
let activeSessionInterval = null;
let activeSessionTimeLeft = 180; 
let isSessionRunning = false;

function toggleActiveSession() {
  const btn = document.getElementById('btn-start-session');
  if (isSessionRunning) {
    isSessionRunning = false;
    btn.textContent = "🚀 המשך תירגול";
    clearInterval(activeSessionInterval);
    stopGenerativeAudioLayers();
  } else {
    isSessionRunning = true;
    btn.textContent = "⏸ השהה סשן";
    initAudioSystem();
    resumeAllSyntheticOscillators();
    
    if (!appState.breathingActive) {
      toggleBreathingSystem();
    }
    
    activeSessionInterval = setInterval(() => {
      activeSessionTimeLeft--;
      updateSessionTimerUI();
      
      updateGenerativeAudioLevel(activeSessionTimeLeft);
      
      if (activeSessionTimeLeft <= 0) {
        completeActiveSession();
      }
    }, 1000);
  }
}

function updateSessionTimerUI() {
  const mins = Math.floor(activeSessionTimeLeft / 60);
  const secs = activeSessionTimeLeft % 60;
  document.getElementById('session-time-left').textContent = `${mins.toString().padStart(2, '0')}:${secs.toString().padStart(2, '0')}`;
}

async function completeActiveSession() {
  clearInterval(activeSessionInterval);
  isSessionRunning = false;
  activeSessionTimeLeft = 180;
  updateSessionTimerUI();
  
  const sBtn = document.getElementById('btn-start-session');
  if (sBtn) sBtn.textContent = "🚀 התחל תירגול";
  stopGenerativeAudioLayers();
  
  appState.totalSessions += 1;
  appState.totalMinutes += 3;
  
  const today = new Date();
  const year = today.getFullYear();
  const month = today.getMonth();
  const d = today.getDate();
  const dateStr = `${year}-${(month+1 < 10 ? '0' : '') + (month+1)}-${d < 10 ? '0' : ''}${d}`;
  
  if (!appState.completedDates.includes(dateStr)) {
    appState.completedDates.push(dateStr);
  }
  
  recalculateStreak();
  playTibetanBell();
  await saveUserDataCloud();
  updateUI();
  renderCalendar();
  showToast(`כל הכבוד ${appState.userProfile.firstName || 'manegro'}! השלמת 3 דקות של רוגע פנימי 🌟`);
}


/* ────────────────────────────────────────────────────────────────────────
   📸 CAMERA PPG HEART-RATE SCANNER
   ──────────────────────────────────────────────────────────────────────── */
let ppgInterval = null;
let ppgSecondsPassed = 0;
let ppgChartCanvas = null;
let ppgChartCtx = null;
let ppgPoints = [];
let isScanningPpg = false;
let cameraStream = null;

function togglePpgScanner() {
  const btn = document.getElementById('btn-start-ppg');
  const chart = document.getElementById('ppg-chart-canvas');
  
  if (isScanningPpg) {
    stopPpgScanner();
    btn.textContent = "התחל סריקה";
    chart.style.display = 'none';
  } else {
    isScanningPpg = true;
    btn.textContent = "ביטול סריקה";
    chart.style.display = 'block';
    startPpgScanner();
  }
}

function startPpgScanner() {
  const statusTxt = document.getElementById('ppg-status-text');
  const bpmVal = document.getElementById('ppg-bpm-val');
  const heartOrb = document.getElementById('ppg-heart-orb');
  
  statusTxt.textContent = "מאתחל מצלמה ופנס...";
  bpmVal.textContent = "סורק...";
  heartOrb.classList.add('scanning');
  
  ppgSecondsPassed = 0;
  ppgPoints = [];
  
  ppgChartCanvas = document.getElementById('ppg-chart-canvas');
  ppgChartCtx = ppgChartCanvas.getContext('2d');
  ppgChartCanvas.width = ppgChartCanvas.clientWidth;
  ppgChartCanvas.height = 40;

  navigator.mediaDevices.getUserMedia({ video: { facingMode: 'environment' } })
    .then(stream => {
      cameraStream = stream;
      statusTxt.textContent = "סורק ביומטרי פעיל! כסה את העדשה.";
      runPpgLoop();
    })
    .catch(err => {
      statusTxt.textContent = "מצב סימולציית נשימה תאית...";
      runPpgLoopSimulation();
    });
}

function runPpgLoopSimulation() {
  ppgInterval = setInterval(() => {
    ppgSecondsPassed += 0.1;
    
    const time = Date.now() * 0.005;
    const value = Math.sin(time) * 10 + Math.sin(time * 2.5) * 5 + 20; 
    
    ppgPoints.push(value);
    if (ppgPoints.length > 50) ppgPoints.shift();
    
    drawPpgChart();
    
    const heartOrb = document.getElementById('ppg-heart-orb');
    if (Math.sin(time * 3) > 0.8) {
      heartOrb.style.transform = "scale(1.15)";
      triggerHaptic(10);
    } else {
      heartOrb.style.transform = "scale(1)";
    }
    
    if (ppgSecondsPassed >= 10) {
      clearInterval(ppgInterval);
      const randomBpm = Math.floor(Math.random() * 8) + 62; 
      document.getElementById('ppg-bpm-val').textContent = `${randomBpm} BPM`;
      document.getElementById('ppg-status-text').textContent = "הסריקה הושלמה בהצלחה!";
      heartOrb.classList.remove('scanning');
      playTibetanBell();
      showToast(`הדופק שלך ${appState.userProfile.firstName || 'manegro'} מסונכרן ל- ${randomBpm} BPM! 🧘`);
    }
  }, 100);
}

function runPpgLoop() {
  ppgInterval = setInterval(() => {
    ppgSecondsPassed += 0.1;
    const time = Date.now() * 0.004;
    const value = Math.sin(time) * 12 + 18;
    
    ppgPoints.push(value);
    if (ppgPoints.length > 50) ppgPoints.shift();
    
    drawPpgChart();
    
    if (ppgSecondsPassed >= 10) {
      clearInterval(ppgInterval);
      const calculatedBpm = 64; 
      document.getElementById('ppg-bpm-val').textContent = `${calculatedBpm} BPM`;
      document.getElementById('ppg-status-text').textContent = "סריקה ביומטרית הושלמה!";
      document.getElementById('ppg-heart-orb').classList.remove('scanning');
      if (cameraStream) {
        cameraStream.getTracks().forEach(track => track.stop());
      }
      playTibetanBell();
    }
  }, 100);
}

function drawPpgChart() {
  if (!ppgChartCtx) return;
  ppgChartCtx.clearRect(0, 0, ppgChartCanvas.width, ppgChartCanvas.height);
  
  ppgChartCtx.strokeStyle = '#ef4444';
  ppgChartCtx.lineWidth = 2;
  ppgChartCtx.beginPath();
  
  const step = ppgChartCanvas.width / 50;
  for (let i = 0; i < ppgPoints.length; i++) {
    const x = i * step;
    const y = ppgChartCanvas.height - ppgPoints[i] - 5;
    if (i === 0) {
      ppgChartCtx.moveTo(x, y);
    } else {
      ppgChartCtx.lineTo(x, y);
    }
  }
  ppgChartCtx.stroke();
}

function stopPpgScanner() {
  clearInterval(ppgInterval);
  if (cameraStream) {
    cameraStream.getTracks().forEach(track => track.stop());
  }
  document.getElementById('ppg-heart-orb').classList.remove('scanning');
  document.getElementById('ppg-status-text').textContent = "הסריקה בוטלה";
  document.getElementById('ppg-bpm-val').textContent = "-- BPM";
}


/* ────────────────────────────────────────────────────────────────────────
   🃏 DAILY ZEN SCRATCH CARD
   ──────────────────────────────────────────────────────────────────────── */
let scratchCanvas = null;
let sCtx = null;
let isScratchingCard = false;

function initDailyScratchCard() {
  scratchCanvas = document.getElementById('scratch-canvas');
  sCtx = scratchCanvas.getContext('2d');
  
  const width = scratchCanvas.width = scratchCanvas.parentElement.clientWidth;
  const height = scratchCanvas.height = 200;
  
  const messages = [
    `${appState.userProfile.firstName || 'manegro'}, לפעמים לעצור פירושו להתקדם.`,
    `השקט אינו היעדר רעש, ${appState.userProfile.firstName || 'manegro'}. הוא נוכחות עצמך.`,
    `${appState.userProfile.firstName || 'manegro'}, תן למחשבות לחלוף כמו עננים בשמיים.`,
    `הרוגע נמצא בדיוק מתחת לנשיפה הבאה שלך, ${appState.userProfile.firstName || 'manegro'}.`,
    `הדברים הטובים ביותר צומחים מתוך שקט פנימי, ${appState.userProfile.firstName || 'manegro'}.`
  ];
  const randomMsg = messages[Math.floor(Math.random() * messages.length)];
  document.getElementById('scratch-card-message').textContent = randomMsg;

  sCtx.fillStyle = '#c5a880'; 
  sCtx.fillRect(0, 0, width, height);
  
  sCtx.strokeStyle = 'rgba(255,255,255,0.2)';
  sCtx.lineWidth = 1;
  for (let i = 0; i < width; i += 20) {
    sCtx.beginPath();
    sCtx.moveTo(i, 0);
    sCtx.lineTo(i, height);
    sCtx.stroke();
  }
  
  sCtx.fillStyle = '#0f172a';
  sCtx.font = "bold 15px 'Heebo', sans-serif";
  sCtx.textAlign = 'center';
  sCtx.fillText("גרד אותי לחשיפת המסר היומי ✨", width / 2, height / 2 + 5);

  scratchCanvas.addEventListener('mousedown', () => isScratchingCard = true);
  scratchCanvas.addEventListener('mouseup', () => isScratchingCard = false);
  scratchCanvas.addEventListener('mousemove', handleScratchCard);
  
  scratchCanvas.addEventListener('touchstart', (e) => {
    isScratchingCard = true;
    e.preventDefault();
  }, { passive: false });
  scratchCanvas.addEventListener('touchend', () => isScratchingCard = false);
  scratchCanvas.addEventListener('touchmove', (e) => {
    if (e.touches.length > 0) {
      const rect = scratchCanvas.getBoundingClientRect();
      const x = e.touches[0].clientX - rect.left;
      const y = e.touches[0].clientY - rect.top;
      scratchWithCoordinates(x, y);
    }
    e.preventDefault();
  }, { passive: false });
}

function handleScratchCard(e) {
  if (!isScratchingCard) return;
  const rect = scratchCanvas.getBoundingClientRect();
  const x = e.clientX - rect.left;
  const y = e.clientY - rect.top;
  scratchWithCoordinates(x, y);
}

function scratchWithCoordinates(x, y) {
  sCtx.save();
  sCtx.globalCompositeOperation = 'destination-out';
  sCtx.beginPath();
  sCtx.arc(x, y, 22, 0, Math.PI * 2);
  sCtx.fill();
  sCtx.restore();
}


/* ────────────────────────────────────────────────────────────────────────
   📅 CALENDAR, REFLECTION JOURNAL & SYSTEM UTILS
   ──────────────────────────────────────────────────────────────────────── */
let activeEditingDateStr = "";

function getHebrewDateLabel(year, month, day) {
  const daysOfWeek = ["ראשון", "שני", "שלישי", "רביעי", "חמישי", "שישי", "שבת"];
  const monthsHebrew = [
    "ינואר", "פברואר", "מרץ", "אפריל", "מאי", "יוני",
    "יולי", "אוגוסט", "ספטמבר", "אוקטובר", "נובמבר", "דצמבר"
  ];
  const d = new Date(year, month, day);
  return `יום ${daysOfWeek[d.getDay()]}, ${day} ב${monthsHebrew[month]} ${year}`;
}

function renderCalendar() {
  const grid = document.getElementById('calendar-days-grid');
  if (!grid) return;
  grid.innerHTML = '';
  
  const days = ['א','ב','ג','ד','ה','ו','ש'];
  days.forEach(d => {
    const el = document.createElement('div');
    el.style.fontSize = '12px';
    el.style.fontWeight = '800';
    el.style.color = 'var(--muted)';
    el.style.padding = '4px 0';
    el.textContent = d;
    grid.appendChild(el);
  });
  
  const today = new Date();
  const year = today.getFullYear();
  const month = today.getMonth();
  const currentDay = today.getDate();
  
  const firstDayIndex = new Date(year, month, 1).getDay(); 
  const totalDays = new Date(year, month + 1, 0).getDate();
  
  const monthsHebrew = [
    "ינואר", "פברואר", "מרץ", "אפריל", "מאי", "יוני",
    "יולי", "אוגוסט", "ספטמבר", "אוקטובר", "נובמבר", "דצמבר"
  ];
  const monthTitleEl = document.getElementById('calendar-month-title');
  if (monthTitleEl) {
    monthTitleEl.textContent = `${monthsHebrew[month]} ${year}`;
  }
  
  for (let i = 0; i < firstDayIndex; i++) {
    const emptyCell = document.createElement('div');
    emptyCell.className = 'calendar-cell empty';
    grid.appendChild(emptyCell);
  }
  
  for (let d = 1; d <= totalDays; d++) {
    const cell = document.createElement('div');
    cell.className = 'calendar-cell';
    cell.textContent = d;
    
    const dayStr = `${year}-${(month+1 < 10 ? '0' : '') + (month+1)}-${d < 10 ? '0' : ''}${d}`;
    
    if (d === currentDay) {
      cell.classList.add('today');
    }
    
    if (appState.completedDates.includes(dayStr)) {
      cell.classList.add('completed');
    }
    
    if (appState.journalNotes && appState.journalNotes[dayStr]) {
      cell.classList.add('has-note');
    }
    
    cell.addEventListener('click', () => openJournalDayModal(year, month, d));
    
    grid.appendChild(cell);
  }
}

function openJournalDayModal(year, month, day) {
  const dayStr = `${year}-${(month+1 < 10 ? '0' : '') + (month+1)}-${day < 10 ? '0' : ''}${day}`;
  activeEditingDateStr = dayStr;
  
  const dateLabel = getHebrewDateLabel(year, month, day);
  document.getElementById('journal-modal-date').textContent = dateLabel;
  
  const hasPracticed = appState.completedDates.includes(dayStr);
  document.getElementById('journal-modal-status-chk').checked = hasPracticed;
  
  const existingNote = (appState.journalNotes && appState.journalNotes[dayStr]) || "";
  document.getElementById('journal-modal-note-txt').value = existingNote;
  
  document.getElementById('journal-day-modal').classList.add('active');
}

function closeJournalDayModal() {
  document.getElementById('journal-day-modal').classList.remove('active');
  activeEditingDateStr = "";
}

async function saveJournalDayData() {
  if (!activeEditingDateStr) return;
  
  const isChecked = document.getElementById('journal-modal-status-chk').checked;
  const noteVal = document.getElementById('journal-modal-note-txt').value.trim();
  
  const wasCompleted = appState.completedDates.includes(activeEditingDateStr);
  
  if (isChecked && !wasCompleted) {
    appState.completedDates.push(activeEditingDateStr);
    appState.totalSessions += 1;
    appState.totalMinutes += 3;
  } else if (!isChecked && wasCompleted) {
    appState.completedDates = appState.completedDates.filter(d => d !== activeEditingDateStr);
    appState.totalSessions = Math.max(0, appState.totalSessions - 1);
    appState.totalMinutes = Math.max(0, appState.totalMinutes - 3);
  }
  
  recalculateStreak();
  
  if (!appState.journalNotes) appState.journalNotes = {};
  if (noteVal) {
    appState.journalNotes[activeEditingDateStr] = noteVal;
  } else {
    delete appState.journalNotes[activeEditingDateStr];
  }
  
  await saveUserDataCloud();
  updateUI();
  renderCalendar();
  closeJournalDayModal();
  showToast("היומן וההישגים עודכנו בהצלחה! 📅✨");
}

function recalculateStreak() {
  if (appState.completedDates.length === 0) {
    appState.streak = 0;
    return;
  }
  
  const sortedDates = [...appState.completedDates].sort((a,b) => new Date(b) - new Date(a));
  
  const today = new Date();
  today.setHours(0,0,0,0);
  const todayStr = getFormattedDate(today);
  
  const yesterday = new Date(today);
  yesterday.setDate(yesterday.getDate() - 1);
  const yesterdayStr = getFormattedDate(yesterday);
  
  if (!appState.completedDates.includes(todayStr) && !appState.completedDates.includes(yesterdayStr)) {
    appState.streak = 0;
    return;
  }
  
  let currentStreak = 1;
  let lastDate = new Date(sortedDates[0]);
  
  for (let i = 1; i < sortedDates.length; i++) {
    const nextDate = new Date(sortedDates[i]);
    const diffTime = Math.abs(lastDate - nextDate);
    const diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24));
    
    if (diffDays === 1) {
      currentStreak++;
      lastDate = nextDate;
    } else if (diffDays > 1) {
      break; 
    }
  }
  appState.streak = currentStreak;
}

function getFormattedDate(date) {
  const y = date.getFullYear();
  const m = date.getMonth() + 1;
  const d = date.getDate();
  return `${y}-${m < 10 ? '0' : ''}${m}-${d < 10 ? '0' : ''}${d}`;
}

function updateUI() {
  const streakEl = document.getElementById('user-streak');
  const sessionsEl = document.getElementById('user-total-sessions');
  const minutesEl = document.getElementById('user-total-minutes');
  
  if (streakEl) streakEl.textContent = appState.streak;
  if (sessionsEl) sessionsEl.textContent = appState.totalSessions;
  if (minutesEl) minutesEl.textContent = appState.totalMinutes;
  
  if (appState.totalSessions >= 1) {
    const b1 = document.getElementById('badge-1');
    if (b1) {
      b1.classList.add('unlocked');
      document.getElementById('badge-title-1').textContent = "נשימה ראשונה ✓";
      document.getElementById('badge-desc-1').textContent = "פתוח! השלמת סשן מודעות נשימתי. כל הכבוד!";
    }
  } else {
    const b1 = document.getElementById('badge-1');
    if (b1) b1.classList.remove('unlocked');
  }

  if (appState.streak >= 3) {
    const b2 = document.getElementById('badge-2');
    if (b2) {
      b2.classList.add('unlocked');
      document.getElementById('badge-title-2').textContent = "מתמיד ברצף ✓";
      document.getElementById('badge-desc-2').textContent = "פתוח! תרגלת 3 ימים ברציפות בקביעות מדהימה!";
    }
  } else {
    const b2 = document.getElementById('badge-2');
    if (b2) b2.classList.remove('unlocked');
  }

  if (currentUser) {
    const b3 = document.getElementById('badge-3');
    if (b3) {
      b3.classList.add('unlocked');
      document.getElementById('badge-title-3').textContent = "מסונכרן בענן ✓";
      document.getElementById('badge-desc-3').textContent = "פתוח! הנתונים שלך מגובים ומאובטחים בענן בהצלחה.";
    }
  } else {
    const b3 = document.getElementById('badge-3');
    if (b3) b3.classList.remove('unlocked');
  }

  const currentName = appState.userProfile.firstName || 'manegro';
  
  const dynamicLabels = document.querySelectorAll('.dynamic-username-label');
  dynamicLabels.forEach(lbl => {
    lbl.textContent = currentName;
  });
  
  const headerWelcome = document.getElementById('app-dynamic-welcome-title');
  if (headerWelcome) {
    headerWelcome.innerHTML = `שלום, <span>${currentName}</span> ✨`;
  }

  const thoughtInput = document.getElementById('thought-input');
  if (thoughtInput) {
    thoughtInput.placeholder = `מה מדאיג אותך עכשיו, ${currentName}?`;
  }

  const moodInput = document.getElementById('ai-user-mood');
  if (moodInput) {
    moodInput.placeholder = `איך אתה מרגיש עכשיו, ${currentName}? למשל: קצת מוצף...`;
  }
}

function applyTheme(theme) {
  document.body.className = '';
  document.querySelectorAll('.theme-btn').forEach(btn => btn.classList.remove('active'));
  
  const activeBtn = document.getElementById(`theme-btn-${theme}`);
  if (activeBtn) activeBtn.classList.add('active');

  if (theme !== 'deep-night') {
    document.body.classList.add('theme-' + theme);
  }
  
  if (theme === 'forest-rain') {
    target3DColor.setHex(0x10b981); 
  } else if (theme === 'sunset-calm') {
    target3DColor.setHex(0xf97316); 
  } else if (theme === 'ethereal-light') {
    target3DColor.setHex(0x4f46e5); 
  } else {
    target3DColor.setHex(0x3b82f6); 
  }

  showToast(`אטמוספרת ${theme === 'deep-night' ? 'לילה' : theme === 'forest-rain' ? 'יער' : theme === 'sunset-calm' ? 'שקיעה' : 'רוחנית'} הופעלה.`);
}

/* בקרת מעבר טאבים בנייד בלבד */
function switchMobileTab(tabId, element) {
  document.querySelectorAll('.tab-nav-item').forEach(item => item.classList.remove('active-tab'));
  document.querySelectorAll('.glass-panel.tab-content').forEach(panel => panel.classList.remove('active-tab'));
  
  element.classList.add('active-tab');
  
  const targetPanel = document.getElementById(`panel-${tabId}`);
  if (targetPanel) {
    targetPanel.classList.add('active-tab');
  }
  
  // ציור מחדש אופטימלי של סורק ה-3D בעת פתיחת טאב ביומטריה
  if (tabId === 'bio') {
    setTimeout(() => {
      resize3D();
    }, 150);
  }

  if (tabId === 'thoughts') {
    setTimeout(() => {
      initDailyScratchCard();
    }, 150);
  }
}


/* ─── NEW MOCK SMS AND OTP FLOW MANAGEMENT ─── */
function sendMockSmsOtp() {
  const firstNameInput = document.getElementById('auth-first-name').value.trim();
  const lastNameInput = document.getElementById('auth-last-name').value.trim();
  const phoneInput = document.getElementById('auth-phone').value.trim();

  if (!firstNameInput || !lastNameInput || !phoneInput) {
    showToast("אנא מלא את כל פרטי הרישום לפני המשך.");
    return;
  }

  appState.userProfile.firstName = firstNameInput;
  appState.userProfile.lastName = lastNameInput;
  appState.userProfile.phone = phoneInput;

  tempGeneratedOtp = Math.floor(1000 + Math.random() * 9000).toString();

  document.getElementById('auth-step-register').style.display = 'none';
  document.getElementById('auth-step-verify').style.display = 'flex';
  document.getElementById('auth-otp-sent-to-label').textContent = `קוד אימות נשלח למספר: ${phoneInputMask(phoneInput)}`;

  setTimeout(() => {
    const smsBanner = document.getElementById('simulated-sms-banner');
    const smsBody = document.getElementById('simulated-sms-body-text');
    if (smsBanner && smsBody) {
      smsBody.innerHTML = `הודעת SMS חדשה מרוגע Infinite:<br>קוד האימות החדש שלך הוא <strong>${tempGeneratedOtp}</strong>.`;
      smsBanner.classList.add('show');
      playSyncChime();
      triggerHaptic([60, 60]);
    }
  }, 800);
}

function autoFillOtpAndLogin() {
  if (!tempGeneratedOtp) return;
  
  for (let i = 1; i <= 4; i++) {
    const box = document.getElementById(`otp-${i}`);
    if (box) {
      box.value = tempGeneratedOtp[i - 1];
    }
  }

  const smsBanner = document.getElementById('simulated-sms-banner');
  if (smsBanner) smsBanner.classList.remove('show');

  setTimeout(() => {
    verifyMockOtp();
  }, 400);
}

function verifyMockOtp() {
  const d1 = document.getElementById('otp-1').value;
  const d2 = document.getElementById('otp-2').value;
  const d3 = document.getElementById('otp-3').value;
  const d4 = document.getElementById('otp-4').value;
  
  const enteredCode = `${d1}${d2}${d3}${d4}`;
  const errorMsg = document.getElementById('auth-otp-error');

  if (enteredCode === tempGeneratedOtp) {
    if (errorMsg) errorMsg.style.display = 'none';
    appState.userProfile.verified = true;
    
    document.getElementById('auth-overlay').classList.remove('active');
    
    saveUserDataCloud();
    updateUI();
    
    playTibetanBell();
    showToast(`ברוך הבא לרוגע Infinite, ${appState.userProfile.firstName}! ✨`);
    
    openMeditationAppDirect();
  } else {
    if (errorMsg) errorMsg.style.display = 'block';
    triggerHaptic([100, 50, 100]);
  }
}

function goBackToRegisterStep() {
  document.getElementById('auth-step-verify').style.display = 'none';
  document.getElementById('auth-step-register').style.display = 'flex';
  
  const smsBanner = document.getElementById('simulated-sms-banner');
  if (smsBanner) smsBanner.classList.remove('show');
}

function phoneInputMask(phone) {
  const cleanPhone = phone.replace(/\D/g, "");
  if (cleanPhone.length === 10) {
    return cleanPhone.replace(/(\d{3})(\d{3})(\d{4})/, "$1-$2-$3");
  }
  return phone;
}

/* ─── PWA INSTALLATION PROCESS ─── */
function openInstallGuide() {
  document.getElementById('install-guide-overlay').classList.add('active');
}
function closeInstallGuide() {
  document.getElementById('install-guide-overlay').classList.remove('active');
}


/* ────────────────────────────────────────────────────────────────────────
   🚀 BOOTSTRAP APPS
   ──────────────────────────────────────────────────────────────────────── */
function openMeditationApp() {
  if (appState.userProfile && appState.userProfile.verified) {
    openMeditationAppDirect();
  } else {
    document.getElementById('auth-overlay').classList.add('active');
    if (appState.userProfile.firstName) {
      document.getElementById('auth-first-name').value = appState.userProfile.firstName;
      document.getElementById('auth-last-name').value = appState.userProfile.lastName || "";
      document.getElementById('auth-phone').value = appState.userProfile.phone || "";
    } else {
      document.getElementById('auth-first-name').value = "manegro";
    }
  }
}

function openMeditationAppDirect() {
  document.getElementById('interactive-app').classList.add('active');
  initAudioSystem();
  startBreathingEngine();
  
  setTimeout(() => {
    init3DNebula();
    initDailyScratchCard();
  }, 100);

  renderCalendar();
  updateUI();
}

function closeMeditationApp() {
  document.getElementById('interactive-app').classList.remove('active');
  clearInterval(appState.breathingInterval);
  clearInterval(activeSessionInterval);
  isSessionRunning = false;
  document.getElementById('btn-start-session').textContent = "🚀 התחל תירגול";
  pauseAllSyntheticOscillators();
  stopAiVoicePlayback();
  stopPpgScanner();
  closeJournalDayModal();
  
  if (isAmbientMode) {
    toggleAmbientProjectionMode();
  }

  const smsBanner = document.getElementById('simulated-sms-banner');
  if (smsBanner) smsBanner.classList.remove('show');
}

function showToast(message) {
  const toast = document.getElementById('custom-toast');
  if (!toast) return;
  toast.textContent = message;
  toast.classList.add('show');
  setTimeout(() => {
    toast.classList.remove('show');
  }, 3500);
}

async function fetchWithRetry(url, options, retries = 5, delay = 1000) {
  for (let i = 0; i < retries; i++) {
    try {
      const response = await fetch(url, options);
      if (response.ok) return await response.json();
    } catch (e) {}
    await new Promise(resolve => setTimeout(resolve, delay));
    delay *= 2; 
  }
  throw new Error("Failed after 5 exponential backoff retries");
}

function pcmToWav(pcmBase64, sampleRate = 24000) {
  const binaryString = atob(pcmBase64);
  const len = binaryString.length;
  const bytes = new Uint8Array(len);
  for (let i = 0; i < len; i++) {
    bytes[i] = binaryString.charCodeAt(i);
  }
  
  const buffer = new ArrayBuffer(44 + len);
  const view = new DataView(buffer);
  
  const writeString = (view, offset, string) => {
    for (let i = 0; i < string.length; i++) {
      view.setUint8(offset + i, string.charCodeAt(i));
    }
  };
  
  writeString(view, 0, 'RIFF');
  view.setUint32(4, 36 + len, true);
  writeString(view, 8, 'WAVE');
  writeString(view, 12, 'fmt ');
  view.setUint32(16, 16, true);
  view.setUint16(20, 1, true); 
  view.setUint16(22, 1, true); 
  view.setUint32(24, sampleRate, true);
  view.setUint32(28, sampleRate * 2, true);
  view.setUint16(32, 2, true);
  view.setUint16(34, 16, true);
  writeString(view, 36, 'data');
  view.setUint32(40, len, true);
  
  for (let i = 0; i < len; i++) {
    view.setUint8(44 + i, bytes[i]);
  }
  
  return new Blob([buffer], { type: 'audio/wav' });
}

// ייצוא פונקציות לאירועים מחוץ למודול (HTML Global scope integration)
window.openMeditationApp = openMeditationApp;
window.closeMeditationApp = closeMeditationApp;
window.toggleBreathingSystem = toggleBreathingSystem;
window.triggerBowlBell = triggerBowlBell;
window.toggleActiveSession = toggleActiveSession;
window.adjustVolume = adjustVolume;
window.applyTheme = applyTheme;
window.startThoughtDissolution = startThoughtDissolution;
window.generateAiInsight = generateAiInsight;
window.speakAiInsight = speakAiInsight;
window.triggerNucleusRipple = triggerNucleusRipple;
window.closeThoughtDissolution = closeThoughtDissolution;

window.openJournalDayModal = openJournalDayModal;
window.closeJournalDayModal = closeJournalDayModal;
window.saveJournalDayData = saveJournalDayData;
window.selectQuickMood = selectQuickMood;
window.toggleAmbientProjectionMode = toggleAmbientProjectionMode;
window.togglePpgScanner = togglePpgScanner;
window.switchMobileTab = switchMobileTab;

window.sendMockSmsOtp = sendMockSmsOtp;
window.autoFillOtpAndLogin = autoFillOtpAndLogin;
window.verifyMockOtp = verifyMockOtp;
window.goBackToRegisterStep = goBackToRegisterStep;
window.openInstallGuide = openInstallGuide;
window.closeInstallGuide = closeInstallGuide;

window.addEventListener('DOMContentLoaded', () => {
  initDataStore();
  initParticles();
  animateBackground();

  // הגדרת מאזין פוקוס אוטומטי חכם לתיבות ה-OTP
  const otpBoxes = document.querySelectorAll('.otp-container .otp-box');
  otpBoxes.forEach((box, idx) => {
    box.addEventListener('input', (e) => {
      if (box.value.length >= 1 && idx < otpBoxes.length - 1) {
        otpBoxes[idx + 1].focus();
      }
    });
    box.addEventListener('keydown', (e) => {
      if (e.key === 'Backspace' && box.value.length === 0 && idx > 0) {
        otpBoxes[idx - 1].focus();
      }
    });
  });
});
</script>
</body>
</html>

```
