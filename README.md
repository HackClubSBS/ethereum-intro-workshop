<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Introduction to Ethereum — HackClub SBS</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Fraunces:ital,wght@0,300;0,700;1,300&family=DM+Mono:wght@300;400&family=Outfit:wght@300;400;600&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --ink: #0C0E1A;
    --ink2: #2D3055;
    --muted: #7B82A8;
    --subtle: #B4B9D4;
    --bg: #F7F8FC;
    --surface: #FFFFFF;
    --line: #E2E5F0;
    --eth: #4C56D4;
    --eth-light: #EEF0FF;
    --eth-dark: #2E3699;
    --accent: #7C85E8;
    --green: #1A9E72;
    --green-bg: #E6F7F1;
  }

  html { font-size: 16px; }

  body {
    font-family: 'Outfit', sans-serif;
    background: var(--bg);
    color: var(--ink);
    line-height: 1.7;
    max-width: 860px;
    margin: 0 auto;
    padding: 0 24px 80px;
  }

  /* ── HERO ── */
  .hero {
    padding: 72px 0 56px;
    border-bottom: 1px solid var(--line);
    margin-bottom: 56px;
  }

  .badge-row {
    display: flex;
    gap: 8px;
    flex-wrap: wrap;
    margin-bottom: 32px;
  }

  .badge {
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.1em;
    padding: 5px 12px;
    border-radius: 100px;
    display: inline-flex;
    align-items: center;
    gap: 6px;
  }

  .badge-blue { background: var(--eth-light); color: var(--eth-dark); border: 1px solid #C5C9F5; }
  .badge-green { background: var(--green-bg); color: var(--green); border: 1px solid #A3DFCC; }
  .badge-gray { background: #F0F1F5; color: var(--muted); border: 1px solid var(--line); }

  .badge-dot { width: 6px; height: 6px; border-radius: 50%; background: currentColor; opacity: 0.7; }

  .hero-eyebrow {
    font-family: 'DM Mono', monospace;
    font-size: 12px;
    color: var(--eth);
    letter-spacing: 0.15em;
    text-transform: uppercase;
    margin-bottom: 16px;
  }

  .hero-title {
    font-family: 'Fraunces', serif;
    font-size: clamp(42px, 7vw, 68px);
    font-weight: 700;
    line-height: 1.0;
    color: var(--ink);
    letter-spacing: -0.02em;
    margin-bottom: 12px;
  }

  .hero-title em {
    font-style: italic;
    font-weight: 300;
    color: var(--eth);
  }

  .hero-sub {
    font-size: 18px;
    font-weight: 300;
    color: var(--muted);
    margin-bottom: 36px;
    max-width: 520px;
  }

  .hero-meta {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
    gap: 1px;
    background: var(--line);
    border: 1px solid var(--line);
    border-radius: 12px;
    overflow: hidden;
    max-width: 640px;
  }

  .hero-meta-cell {
    background: var(--surface);
    padding: 16px 20px;
  }

  .hero-meta-label {
    font-family: 'DM Mono', monospace;
    font-size: 9px;
    letter-spacing: 0.2em;
    color: var(--eth);
    text-transform: uppercase;
    margin-bottom: 4px;
  }

  .hero-meta-value {
    font-size: 13px;
    font-weight: 600;
    color: var(--ink);
    line-height: 1.35;
  }

  /* ── ETH DIAMOND ── */
  .eth-logo {
    width: 52px;
    height: 52px;
    margin-bottom: 28px;
  }

  /* ── SECTION ── */
  section {
    margin-bottom: 56px;
  }

  .section-label {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.2em;
    color: var(--subtle);
    text-transform: uppercase;
    margin-bottom: 8px;
  }

  h2 {
    font-family: 'Fraunces', serif;
    font-size: 28px;
    font-weight: 700;
    letter-spacing: -0.01em;
    color: var(--ink);
    margin-bottom: 20px;
    line-height: 1.2;
  }

  p {
    color: var(--ink2);
    font-size: 15px;
    line-height: 1.75;
    margin-bottom: 12px;
  }

  /* ── AGENDA ── */
  .agenda {
    border: 1px solid var(--line);
    border-radius: 12px;
    overflow: hidden;
  }

  .agenda-header {
    display: grid;
    grid-template-columns: 72px 1fr 110px;
    background: var(--ink);
    padding: 10px 20px;
    gap: 16px;
  }

  .agenda-header span {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.15em;
    color: rgba(255,255,255,0.5);
    text-transform: uppercase;
  }

  .agenda-row {
    display: grid;
    grid-template-columns: 72px 1fr 110px;
    padding: 14px 20px;
    gap: 16px;
    border-top: 1px solid var(--line);
    align-items: start;
    transition: background 0.15s;
  }

  .agenda-row:hover { background: var(--eth-light); }

  .agenda-row:nth-child(2) { border-top: none; }

  .agenda-time {
    font-family: 'DM Mono', monospace;
    font-size: 12px;
    color: var(--muted);
    padding-top: 2px;
  }

  .agenda-session {
    font-size: 14px;
    font-weight: 600;
    color: var(--ink);
    margin-bottom: 3px;
  }

  .agenda-desc {
    font-size: 12px;
    color: var(--muted);
    line-height: 1.5;
  }

  .agenda-format {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    color: var(--eth-dark);
    background: var(--eth-light);
    border: 1px solid #C5C9F5;
    padding: 3px 8px;
    border-radius: 100px;
    text-align: center;
    align-self: start;
    white-space: nowrap;
  }

  /* ── BUDGET ── */
  .budget-table {
    width: 100%;
    border-collapse: collapse;
    border: 1px solid var(--line);
    border-radius: 12px;
    overflow: hidden;
    font-size: 14px;
  }

  .budget-table th {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: rgba(255,255,255,0.6);
    background: var(--ink);
    padding: 12px 16px;
    text-align: left;
    font-weight: 400;
  }

  .budget-table td {
    padding: 12px 16px;
    border-top: 1px solid var(--line);
    color: var(--ink2);
    vertical-align: top;
  }

  .budget-table tr:nth-child(even) td { background: #FAFBFF; }

  .budget-table tfoot td {
    background: var(--eth-light);
    font-weight: 600;
    color: var(--eth-dark);
    border-top: 2px solid #C5C9F5;
  }

  .amt {
    font-family: 'DM Mono', monospace;
    font-size: 13px;
    text-align: right;
  }

  /* ── DELIVERABLES ── */
  .deliverables {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 12px;
  }

  .deliverable-card {
    background: var(--surface);
    border: 1px solid var(--line);
    border-radius: 10px;
    padding: 18px 20px;
    display: flex;
    gap: 14px;
    align-items: flex-start;
    transition: border-color 0.15s, box-shadow 0.15s;
  }

  .deliverable-card:hover {
    border-color: var(--accent);
    box-shadow: 0 2px 12px rgba(76,86,212,0.08);
  }

  .deliverable-num {
    font-family: 'Fraunces', serif;
    font-size: 28px;
    font-weight: 700;
    color: var(--eth-light);
    line-height: 1;
    min-width: 32px;
  }

  .deliverable-title {
    font-size: 13px;
    font-weight: 600;
    color: var(--ink);
    margin-bottom: 4px;
  }

  .deliverable-desc {
    font-size: 12px;
    color: var(--muted);
    line-height: 1.5;
  }

  /* ── TIMELINE ── */
  .timeline {
    position: relative;
    padding-left: 28px;
  }

  .timeline::before {
    content: '';
    position: absolute;
    left: 7px;
    top: 8px;
    bottom: 8px;
    width: 1px;
    background: var(--line);
  }

  .timeline-item {
    position: relative;
    margin-bottom: 24px;
  }

  .timeline-item::before {
    content: '';
    position: absolute;
    left: -24px;
    top: 7px;
    width: 8px;
    height: 8px;
    border-radius: 50%;
    background: var(--eth);
    border: 2px solid var(--bg);
    box-shadow: 0 0 0 1px var(--eth);
  }

  .timeline-week {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.15em;
    color: var(--eth);
    text-transform: uppercase;
    margin-bottom: 4px;
  }

  .timeline-text {
    font-size: 14px;
    color: var(--ink2);
    line-height: 1.55;
  }

  .timeline-item.highlight::before { background: var(--green); box-shadow: 0 0 0 1px var(--green); }
  .timeline-item.highlight .timeline-week { color: var(--green); }
  .timeline-item.highlight .timeline-text { font-weight: 600; color: var(--ink); }

  /* ── CONTACT ── */
  .contact-row {
    display: flex;
    gap: 16px;
    flex-wrap: wrap;
    margin-top: 20px;
  }

  .contact-chip {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    background: var(--surface);
    border: 1px solid var(--line);
    border-radius: 100px;
    padding: 8px 16px;
    font-size: 13px;
    color: var(--ink2);
    text-decoration: none;
    transition: border-color 0.15s;
  }

  .contact-chip:hover { border-color: var(--eth); color: var(--eth); }

  .contact-icon {
    width: 16px;
    height: 16px;
    opacity: 0.5;
  }

  /* ── LINKS ── */
  .links-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 10px;
  }

  .link-card {
    background: var(--surface);
    border: 1px solid var(--line);
    border-radius: 10px;
    padding: 16px 18px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    text-decoration: none;
    color: var(--ink);
    transition: border-color 0.15s;
  }

  .link-card:hover { border-color: var(--eth); }

  .link-title { font-size: 13px; font-weight: 600; margin-bottom: 2px; }
  .link-url { font-family: 'DM Mono', monospace; font-size: 10px; color: var(--muted); }

  .link-arrow {
    color: var(--subtle);
    font-size: 18px;
  }

  /* ── FOOTER ── */
  footer {
    border-top: 1px solid var(--line);
    padding-top: 32px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 16px;
    flex-wrap: wrap;
  }

  .footer-text {
    font-size: 12px;
    color: var(--muted);
    font-family: 'DM Mono', monospace;
  }

  hr.divider {
    border: none;
    border-top: 1px solid var(--line);
    margin: 48px 0;
  }

  .highlight-box {
    background: var(--eth-light);
    border: 1px solid #C5C9F5;
    border-left: 3px solid var(--eth);
    border-radius: 0 8px 8px 0;
    padding: 16px 20px;
    margin: 20px 0;
    font-size: 14px;
    color: var(--eth-dark);
    line-height: 1.6;
  }
</style>
</head>
<body>

<!-- HERO -->
<div class="hero">
  <svg class="eth-logo" viewBox="0 0 52 52" fill="none" xmlns="http://www.w3.org/2000/svg">
    <polygon points="26,4 26,20 40,24" fill="#4C56D4" opacity="0.9"/>
    <polygon points="26,4 26,20 12,24" fill="#7C85E8" opacity="0.9"/>
    <polygon points="26,48 26,32 40,28" fill="#4C56D4" opacity="0.55"/>
    <polygon points="26,48 26,32 12,28" fill="#7C85E8" opacity="0.55"/>
    <polygon points="26,20 40,24 26,30" fill="#2E3699"/>
    <polygon points="26,20 12,24 26,30" fill="#4C56D4"/>
  </svg>

  <p class="hero-eyebrow">HackClub SBS · Road to Devcon 8</p>

  <h1 class="hero-title">Introduction to<br><em>Ethereum</em></h1>

  <p class="hero-sub">Campus workshop & networking meetup — open to all students, graduates, and curious minds in Ahmedabad.</p>

  <div class="badge-row">
    <span class="badge badge-blue"><span class="badge-dot"></span>EF University Program</span>
    <span class="badge badge-green"><span class="badge-dot"></span>Grant Applied</span>
    <span class="badge badge-gray">July – August 2026</span>
    <span class="badge badge-gray">Ahmedabad, India</span>
  </div>

  <div class="hero-meta">
    <div class="hero-meta-cell">
      <div class="hero-meta-label">Organised by</div>
      <div class="hero-meta-value">HackClub SBS</div>
    </div>
    <div class="hero-meta-cell">
      <div class="hero-meta-label">Institution</div>
      <div class="hero-meta-value">Shanti Business School</div>
    </div>
    <div class="hero-meta-cell">
      <div class="hero-meta-label">Grant Request</div>
      <div class="hero-meta-value">INR 23,000 · USD ~$276</div>
    </div>
    <div class="hero-meta-cell">
      <div class="hero-meta-label">Submitted to</div>
      <div class="hero-meta-value">Ethereum Foundation ESP</div>
    </div>
  </div>
</div>

<!-- ABOUT -->
<section>
  <p class="section-label">01 · About</p>
  <h2>What is this?</h2>
  <p>This repository documents the proposal and planning for an <strong>introductory Ethereum workshop and networking meetup</strong> organised by HackClub SBS at Shanti Business School, Ahmedabad — submitted as part of the Ethereum Foundation's <strong>Road to Devcon 8 India University Program</strong>.</p>
  <p>The event is open to everyone — students from any college, recent graduates, working professionals. No blockchain background required.</p>

  <div class="highlight-box">
    🗓 Devcon 8 is happening in Mumbai, November 2026 — just hours from Ahmedabad. This workshop is the first step toward getting students there.
  </div>
</section>

<hr class="divider">

<!-- AGENDA -->
<section>
  <p class="section-label">02 · Agenda</p>
  <h2>Event Schedule</h2>
  <p>A focused 2.5 – 3 hour program covering fundamentals, real-world context, and open networking.</p>

  <div class="agenda" style="margin-top: 24px;">
    <div class="agenda-header">
      <span>Time</span>
      <span>Session</span>
      <span>Format</span>
    </div>
    <div class="agenda-row">
      <div class="agenda-time">20 min</div>
      <div>
        <div class="agenda-session">Welcome & Introduction</div>
        <div class="agenda-desc">HackClub SBS intro, overview of Devcon 8 Mumbai, why Ethereum matters</div>
      </div>
      <div><span class="agenda-format">Presentation</span></div>
    </div>
    <div class="agenda-row">
      <div class="agenda-time">30 min</div>
      <div>
        <div class="agenda-session">What is Ethereum?</div>
        <div class="agenda-desc">Blockchain basics, decentralisation, real-world relevance</div>
      </div>
      <div><span class="agenda-format">Lecture + Q&A</span></div>
    </div>
    <div class="agenda-row">
      <div class="agenda-time">40 min</div>
      <div>
        <div class="agenda-session">Guest Speaker Session</div>
        <div class="agenda-desc">Experienced Ethereum developer shares their journey — open AMA</div>
      </div>
      <div><span class="agenda-format">Talk + AMA</span></div>
    </div>
    <div class="agenda-row">
      <div class="agenda-time">30 min</div>
      <div>
        <div class="agenda-session">Ethereum in the Real World</div>
        <div class="agenda-desc">DeFi, DAOs, NFTs, Layer 2s — real use cases and career paths</div>
      </div>
      <div><span class="agenda-format">Discussion</span></div>
    </div>
    <div class="agenda-row">
      <div class="agenda-time">20 min</div>
      <div>
        <div class="agenda-session">Career Paths in Web3</div>
        <div class="agenda-desc">Opportunities for tech and business students in the ecosystem</div>
      </div>
      <div><span class="agenda-format">Discussion</span></div>
    </div>
    <div class="agenda-row">
      <div class="agenda-time">20 min</div>
      <div>
        <div class="agenda-session">Q&A + Networking Meetup</div>
        <div class="agenda-desc">Open discussion, Devcon ticket info, informal 1:1 networking</div>
      </div>
      <div><span class="agenda-format">Open</span></div>
    </div>
  </div>
</section>

<hr class="divider">

<!-- BUDGET -->
<section>
  <p class="section-label">03 · Budget</p>
  <h2>Budget Breakdown</h2>
  <p>Total grant requested from Ethereum Foundation ESP: <strong>INR ~23,000 (~USD $276)</strong> — within the program's $300 ceiling. Venue and AV provided by the college.</p>

  <table class="budget-table" style="margin-top: 20px;">
    <thead>
      <tr>
        <th>Item</th>
        <th>Details</th>
        <th style="text-align:right">Cost (INR)</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><strong>Refreshments</strong></td>
        <td style="color: var(--muted)">Snacks & beverages for 50–100 attendees</td>
        <td class="amt">8,000</td>
      </tr>
      <tr>
        <td><strong>Printed Materials</strong></td>
        <td style="color: var(--muted)">Handouts, banners, Ethereum cheat sheets</td>
        <td class="amt">4,000</td>
      </tr>
      <tr>
        <td><strong>Speaker Logistics</strong></td>
        <td style="color: var(--muted)">Travel reimbursement + token honorarium</td>
        <td class="amt">6,000</td>
      </tr>
      <tr>
        <td><strong>Event Promotion</strong></td>
        <td style="color: var(--muted)">Social media creatives, print posters</td>
        <td class="amt">3,000</td>
      </tr>
      <tr>
        <td><strong>Miscellaneous</strong></td>
        <td style="color: var(--muted)">Last-minute or unforeseen expenses</td>
        <td class="amt">2,000</td>
      </tr>
      <tr>
        <td><strong>Venue / AV</strong></td>
        <td style="color: var(--muted)">Seminar hall + projector (college infrastructure)</td>
        <td class="amt" style="color: var(--muted)">—</td>
      </tr>
    </tbody>
    <tfoot>
      <tr>
        <td colspan="2"><strong>Total</strong></td>
        <td class="amt"><strong>23,000</strong></td>
      </tr>
    </tfoot>
  </table>
</section>

<hr class="divider">

<!-- DELIVERABLES -->
<section>
  <p class="section-label">04 · Deliverables</p>
  <h2>Expected Deliverables</h2>
  <p>Upon completion, HackClub SBS will submit the following to the Ethereum Foundation ESP.</p>

  <div class="deliverables" style="margin-top: 24px;">
    <div class="deliverable-card">
      <div class="deliverable-num">01</div>
      <div>
        <div class="deliverable-title">Post-Event Impact Report</div>
        <div class="deliverable-desc">Full report with overview, outcomes, learnings — submitted within 2 weeks</div>
      </div>
    </div>
    <div class="deliverable-card">
      <div class="deliverable-num">02</div>
      <div>
        <div class="deliverable-title">Attendance Data</div>
        <div class="deliverable-desc">Registration records and final headcount, broken down by institution</div>
      </div>
    </div>
    <div class="deliverable-card">
      <div class="deliverable-num">03</div>
      <div>
        <div class="deliverable-title">Feedback Survey Results</div>
        <div class="deliverable-desc">Anonymised responses with satisfaction scores and qualitative feedback</div>
      </div>
    </div>
    <div class="deliverable-card">
      <div class="deliverable-num">04</div>
      <div>
        <div class="deliverable-title">Event Photos</div>
        <div class="deliverable-desc">High-quality photos from workshop, speaker session, and meetup</div>
      </div>
    </div>
    <div class="deliverable-card">
      <div class="deliverable-num">05</div>
      <div>
        <div class="deliverable-title">Social Media Coverage</div>
        <div class="deliverable-desc">Promotion and post-event coverage with reach and engagement metrics</div>
      </div>
    </div>
    <div class="deliverable-card">
      <div class="deliverable-num">06</div>
      <div>
        <div class="deliverable-title">EF Summary Submission</div>
        <div class="deliverable-desc">Highlights, impact, and next steps submitted to EF ESP within 2 weeks</div>
      </div>
    </div>
  </div>
</section>

<hr class="divider">

<!-- TIMELINE -->
<section>
  <p class="section-label">05 · Timeline</p>
  <h2>Project Timeline</h2>
  <p>Event window: 15 May – 15 October 2026 per EF program requirements.</p>

  <div class="timeline" style="margin-top: 28px;">
    <div class="timeline-item">
      <div class="timeline-week">Week 1 – 2</div>
      <div class="timeline-text">Grant approval received · Confirm venue date with management · Begin speaker outreach</div>
    </div>
    <div class="timeline-item">
      <div class="timeline-week">Week 3</div>
      <div class="timeline-text">Confirm guest speaker · Design event materials, banners, and handouts</div>
    </div>
    <div class="timeline-item">
      <div class="timeline-week">Week 4</div>
      <div class="timeline-text">Open registrations · Promote via college channels and social media</div>
    </div>
    <div class="timeline-item">
      <div class="timeline-week">Week 5</div>
      <div class="timeline-text">Finalise headcount · Purchase refreshments · Print all materials</div>
    </div>
    <div class="timeline-item highlight">
      <div class="timeline-week">Week 6 — Event Day</div>
      <div class="timeline-text">Workshop + Guest Speaker AMA + Networking Meetup</div>
    </div>
    <div class="timeline-item">
      <div class="timeline-week">Week 7</div>
      <div class="timeline-text">Post-event survey · Impact report with photos and data submitted to EF ESP</div>
    </div>
  </div>
</section>

<hr class="divider">

<!-- LINKS -->
<section>
  <p class="section-label">06 · Links</p>
  <h2>Useful Links</h2>

  <div class="links-grid" style="margin-top: 20px;">
    <a href="https://esp.ethereum.foundation" class="link-card" target="_blank">
      <div>
        <div class="link-title">Ethereum Foundation ESP</div>
        <div class="link-url">esp.ethereum.foundation</div>
      </div>
      <span class="link-arrow">↗</span>
    </a>
    <a href="https://esp.ethereum.foundation/applicants/rfp/rtd8_india_academic/apply" class="link-card" target="_blank">
      <div>
        <div class="link-title">Road to Devcon 8 Program</div>
        <div class="link-url">University Program Application</div>
      </div>
      <span class="link-arrow">↗</span>
    </a>
    <a href="https://devcon.org" class="link-card" target="_blank">
      <div>
        <div class="link-title">Devcon 8 — Mumbai</div>
        <div class="link-url">devcon.org · Nov 2026</div>
      </div>
      <span class="link-arrow">↗</span>
    </a>
  </div>
</section>

<hr class="divider">

<!-- CONTACT -->
<section>
  <p class="section-label">07 · Contact</p>
  <h2>Get in Touch</h2>
  <p>HackClub SBS · Shanti Business School, Ahmedabad</p>

  <div class="contact-row">
    <a href="mailto:hetanshsachaniya07@gmail.com" class="contact-chip">
      <svg class="contact-icon" viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="1" y="3" width="14" height="10" rx="2"/><path d="M1 5l7 5 7-5"/></svg>
      hetanshsachaniya07@gmail.com
    </a>
    <a href="https://twitter.com/hetansh2220" class="contact-chip" target="_blank">
      <svg class="contact-icon" viewBox="0 0 16 16" fill="currentColor"><path d="M12.6 1h2.3L9.7 7l5.8 8H10L6.4 9.6 2.3 15H0l5.5-6.3L0 1h5.1l3.3 4.3L12.6 1zM11.8 13.5h1.3L4.3 2.4H2.9l8.9 11.1z"/></svg>
      @hetansh2220
    </a>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <span class="footer-text">HackClub SBS · Shanti Business School, Ahmedabad · 2026</span>
  <span class="footer-text">Road to Devcon 8 · India University Program</span>
</footer>

</body>
</html>