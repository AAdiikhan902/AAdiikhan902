/* ==========================================================================
   The Blue Carpet — visual identity
   Palette: paper #F4F7FB, ink #10203A, accent #1D5FD6,
            wire-blue #3A7CA5, meta-gray #5C6B7A
   Display: Fraunces (editorial serif, used at large sizes only)
   Body: Source Serif 4
   Utility/mono: IBM Plex Mono (datelines, timestamps, ticker, meta)
   ========================================================================== */

@import url('https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,300;9..144,500;9..144,600;9..144,700&family=Source+Serif+4:ital,wght@0,400;0,600;1,400&family=IBM+Plex+Mono:wght@400;500&display=swap');

:root {
  --paper: #f4f7fb;
  --paper-dim: #e8eef4;
  --ink: #10203a;
  --accent: #1d5fd6;
  --wire-blue: #3a7ca5;
  --meta: #5c6b7a;
  --rule: #d3dde6;
  --max-width: 1180px;
}

* { box-sizing: border-box; }

html { scroll-behavior: smooth; }

@media (prefers-reduced-motion: reduce) {
  html { scroll-behavior: auto; }
  * { animation-duration: 0.01ms !important; animation-iteration-count: 1 !important; }
}

body {
  margin: 0;
  background: var(--paper);
  color: var(--ink);
  font-family: 'Source Serif 4', Georgia, serif;
  line-height: 1.55;
  -webkit-font-smoothing: antialiased;
}

a { color: var(--wire-blue); text-decoration: none; }
a:hover { text-decoration: underline; }
a:focus-visible, button:focus-visible {
  outline: 2px solid var(--accent);
  outline-offset: 2px;
}

.wrap { max-width: var(--max-width); margin: 0 auto; padding: 0 24px; }

/* ---- Wire ticker (signature element) ---- */
.ticker {
  background: var(--ink);
  color: var(--paper);
  font-family: 'IBM Plex Mono', monospace;
  font-size: 12.5px;
  letter-spacing: 0.02em;
  overflow: hidden;
  white-space: nowrap;
  padding: 7px 0;
}
.ticker__track {
  display: inline-block;
  padding-left: 100%;
  animation: ticker-scroll 45s linear infinite;
}
.ticker__track span { margin-right: 3em; }
.ticker__track span::before { content: "● "; color: var(--accent); }
@keyframes ticker-scroll {
  0% { transform: translateX(0); }
  100% { transform: translateX(-100%); }
}
.ticker__cursor {
  display: inline-block;
  width: 7px; height: 13px;
  background: var(--accent);
  margin-left: 2px;
  vertical-align: -2px;
  animation: blink 1s step-end infinite;
}
@keyframes blink { 50% { opacity: 0; } }

/* ---- Masthead ---- */
.masthead {
  border-bottom: 3px solid var(--ink);
  padding: 22px 0 14px;
}
.masthead__row {
  display: flex;
  justify-content: space-between;
  align-items: baseline;
  flex-wrap: wrap;
  gap: 8px;
}
.masthead__title {
  font-family: 'Fraunces', Georgia, serif;
  font-weight: 700;
  font-optical-sizing: auto;
  font-size: clamp(34px, 6vw, 54px);
  letter-spacing: -0.01em;
  margin: 0;
  line-height: 1;
}
.masthead__title a { color: var(--ink); }
.masthead__title a:hover { text-decoration: none; }
.masthead__dateline {
  font-family: 'IBM Plex Mono', monospace;
  font-size: 12px;
  color: var(--meta);
  text-transform: uppercase;
  letter-spacing: 0.06em;
  text-align: right;
}
.masthead__tagline {
  font-style: italic;
  color: var(--meta);
  font-size: 15px;
  margin-top: 4px;
}

/* ---- Nav ---- */
.nav {
  border-bottom: 1px solid var(--rule);
  background: var(--paper-dim);
}
.nav__list {
  display: flex;
  flex-wrap: wrap;
  gap: 22px;
  list-style: none;
  margin: 0;
  padding: 10px 0;
  font-family: 'IBM Plex Mono', monospace;
  font-size: 12.5px;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}
.nav__list a { color: var(--ink); }
.nav__list a:hover { color: var(--accent); text-decoration: none; }

/* ---- Lead story ---- */
.lead {
  padding: 40px 0 20px;
  border-bottom: 1px solid var(--rule);
}
.lead__eyebrow {
  font-family: 'IBM Plex Mono', monospace;
  font-size: 11.5px;
  color: var(--accent);
  text-transform: uppercase;
  letter-spacing: 0.08em;
  margin-bottom: 10px;
}
.lead__headline {
  font-family: 'Fraunces', Georgia, serif;
  font-weight: 600;
  font-size: clamp(28px, 4.5vw, 46px);
  line-height: 1.05;
  margin: 0 0 14px;
}
.lead__headline a { color: var(--ink); }
.lead__headline a:hover { text-decoration: none; }
.lead__dek {
  font-size: 19px;
  color: #3b3833;
  max-width: 70ch;
  margin: 0 0 12px;
}
.byline {
  font-family: 'IBM Plex Mono', monospace;
  font-size: 12px;
  color: var(--meta);
  text-transform: uppercase;
  letter-spacing: 0.04em;
}

/* ---- Content grid ---- */
.content-grid {
  display: grid;
  grid-template-columns: 1fr 320px;
  gap: 48px;
  padding: 36px 0 60px;
}
@media (max-width: 820px) {
  .content-grid { grid-template-columns: 1fr; }
}

.story-list { display: grid; gap: 28px; }
.story {
  padding-bottom: 26px;
  border-bottom: 1px solid var(--rule);
}
.story:last-child { border-bottom: none; }
.story__eyebrow {
  font-family: 'IBM Plex Mono', monospace;
  font-size: 11px;
  color: var(--wire-blue);
  text-transform: uppercase;
  letter-spacing: 0.07em;
  margin-bottom: 6px;
  display: block;
}
.story__headline {
  font-family: 'Fraunces', Georgia, serif;
  font-weight: 600;
  font-size: 23px;
  line-height: 1.15;
  margin: 0 0 8px;
}
.story__headline a { color: var(--ink); }
.story__headline a:hover { text-decoration: none; }
.story__dek { color: #3b3833; margin: 0 0 8px; }

/* ---- Sidebar: wire feed ---- */
.sidebar__title {
  font-family: 'IBM Plex Mono', monospace;
  font-size: 12px;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  border-bottom: 2px solid var(--ink);
  padding-bottom: 8px;
  margin: 0 0 16px;
}
.wire-feed { list-style: none; margin: 0; padding: 0; }
.wire-feed li {
  padding: 12px 0;
  border-bottom: 1px dashed var(--rule);
  font-size: 14.5px;
}
.wire-feed li:first-child { padding-top: 0; }
.wire-feed time {
  display: block;
  font-family: 'IBM Plex Mono', monospace;
  font-size: 11px;
  color: var(--meta);
  margin-bottom: 3px;
}
.wire-feed a { color: var(--ink); font-weight: 600; }
.wire-feed a:hover { color: var(--accent); text-decoration: none; }

/* ---- Article page ---- */
.article { padding: 40px 0 60px; max-width: 72ch; margin: 0 auto; }
.article__headline {
  font-family: 'Fraunces', Georgia, serif;
  font-weight: 700;
  font-size: clamp(30px, 5vw, 44px);
  line-height: 1.08;
  margin: 14px 0;
}
.article__meta {
  display: flex; gap: 16px; flex-wrap: wrap;
  border-top: 1px solid var(--rule);
  border-bottom: 1px solid var(--rule);
  padding: 10px 0;
  margin-bottom: 28px;
}
.article__body { font-size: 19px; }
.article__body p { margin: 0 0 20px; }
.article__body h2 {
  font-family: 'Fraunces', Georgia, serif;
  font-size: 26px;
  margin: 34px 0 12px;
}
.article__body blockquote {
  border-left: 3px solid var(--accent);
  margin: 24px 0;
  padding: 4px 0 4px 20px;
  font-style: italic;
  color: #3b3833;
}

/* ---- Footer ---- */
.footer {
  border-top: 3px solid var(--ink);
  padding: 28px 0;
  font-family: 'IBM Plex Mono', monospace;
  font-size: 12px;
  color: var(--meta);
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 10px;
}
