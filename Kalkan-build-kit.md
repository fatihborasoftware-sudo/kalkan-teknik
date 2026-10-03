# Kalkan Teknik — build kit for FB AI Engine – Claude Connector

One-page technical service website (electrical, CCTV, fire and burglar alarms, network, Wi-Fi) on a **fresh WordPress**, built through FB AI Engine – Claude Connector 1.2.1+. Approved mockup: `mockup/index.html` in https://github.com/fatihborasoftware-sudo/kalkan-teknik

Placeholders:
- `{{site}}` → the site address without a trailing slash (e.g. `https://example.com/test`).
- `{{img:KEY}}` → the url media_upload returned for that key (section 2).
- `{{form_shortcode}}` → the shortcode form_create returned (section 5).
- Business details in square brackets — `[0 5XX XXX XX XX]`, `tel:+90XXXXXXXXXX`, `https://wa.me/90XXXXXXXXXX`, `[ornek@firma.com]`, `[Şehir]`, `[İlçe 1]`…, `[Açık adres]`, opening hours — and the name **Kalkan Teknik** are replaced with the owner's details when the build prompt gives them. Details not given stay as placeholders.

Use every block exactly as written. Do not add `<style>` or `<script>` tags (styles live in section 4; the recording timer on the camera tiles is pure CSS). The camera videos load from jsDelivr (GitHub); their poster images go into the media library.

## 1. Build plan (build_plan_submit arguments)
Find the ids of "Hello world!" and "Sample Page" with content_list first and put them in `trash`.
```json
{
 "title": "Kalkan Teknik — tek sayfalık teknik servis sitesi",
 "summary": "Fresh-site build from the approved Kalkan Teknik mockup: one long homepage (hero with live security-camera panel, trust strip, six services, process, call-to-action, service area with map, contact form), Kadence header and footer, menu with in-page links, contact form, floating WhatsApp button and mobile call bar.",
 "pages": [
  {
   "title": "Anasayfa",
   "type": "page"
  }
 ],
 "menu": true,
 "settings": true,
 "theme": true,
 "plugins": [
  "wpvivid-backuprestore",
  "contact-form-7"
 ],
 "themes": [
  "kadence"
 ],
 "trash": [
  "<id of \"Hello world!\">",
  "<id of \"Sample Page\">"
 ],
 "launch": "auto",
 "reason": "Owner approved the Kalkan Teknik mockup in chat; one plan for the whole fresh-site build."
}
```

## 2. Images (media_upload: url + alt; keep key → id + url)
| key | url | alt | used on |
|---|---|---|---|
| logo | https://raw.githubusercontent.com/fatihborasoftware-sudo/kalkan-teknik/main/assets/img/logo.png | Kalkan Teknik logosu | Header logo + footer |
| cam01 | https://raw.githubusercontent.com/fatihborasoftware-sudo/kalkan-teknik/main/assets/video/cam01.jpg | (empty) | Poster of CAM 01 video (decorative, empty alt) |
| cam02 | https://raw.githubusercontent.com/fatihborasoftware-sudo/kalkan-teknik/main/assets/video/cam02.jpg | (empty) | Poster of CAM 02 video (decorative, empty alt) |
| cam03 | https://raw.githubusercontent.com/fatihborasoftware-sudo/kalkan-teknik/main/assets/video/cam03.jpg | (empty) | Poster of CAM 03 video (decorative, empty alt) |
| cam04 | https://raw.githubusercontent.com/fatihborasoftware-sudo/kalkan-teknik/main/assets/video/cam04.jpg | (empty) | Poster of CAM 04 video (decorative, empty alt) |

If the owner's business is **not** Kalkan Teknik, skip the `logo` image: leave the Kadence logo empty and show the site title instead, and use the site title in the footer instead of the logo image.

## 3. Theme, header, footer, settings
```json
{
 "theme": "kadence (WordPress.org)",
 "note": "Read the current shapes with theme_settings_get first and keep Kadence's exact structure; only change the values below.",
 "kadence_global_palette": {
  "palette1": "#F5A524",
  "palette2": "#D98E0B",
  "palette3": "#E8EDF5",
  "palette4": "#C6D0DE",
  "palette5": "#AEBBCD",
  "palette6": "#7F8DA3",
  "palette7": "#22304A",
  "palette8": "#111A2C",
  "palette9": "#0B1220"
 },
 "fonts": {
  "heading_font": "Bricolage Grotesque (Google), weight 700",
  "base_font": "Figtree (Google), weight 400, size 17px, line-height 1.6",
  "buttons": "Figtree 700"
 },
 "pages": {
  "page_title": false,
  "page_layout": "fullwidth",
  "page_content_style": "unboxed",
  "page_vertical_padding": "hide",
  "note": "The homepage has its own H1 and full-width sections."
 },
 "logo": "custom_logo = the media id of image \"logo\"; logo width 175px desktop, 150px mobile. Hide the site title text next to the logo (the logo already has the name).",
 "header": {
  "main_row": "Background #0B1220, bottom border 1px #1C2840, height about 80px. Left: logo. Center: primary navigation (Figtree 500, 15px, colour #C6D0DE, hover #F5A524). Right: header button.",
  "header_button_label": "[0 5XX XXX XX XX]",
  "header_button_link": "tel:+90XXXXXXXXXX",
  "header_button_style": "background #F5A524, text #0B1220, radius 12px, bold",
  "sticky": "Make the main row sticky on desktop and mobile if Kadence allows it through settings.",
  "mobile": "Logo left, hamburger right (mobile navigation = primary menu)."
 },
 "footer": {
  "layout": "Middle row with 4 columns = widget areas footer1..footer4 (blocks in section 6), background #070C16, text #9AA8BD. Bottom row: HTML \"© 2026 Kalkan Teknik. Tüm hakları saklıdır.\" left, text #7F8DA3, top border 1px #1C2840."
 },
 "site_settings": {
  "title": "Kalkan Teknik",
  "tagline": "Elektrik, güvenlik ve network teknik servisi",
  "front_page": "the page \"Anasayfa\""
 },
 "custom_css": "Section 4 (whole file, mode replace)"
}
```

## 4. Site CSS (custom_css_set, mode "replace")
```css
/* Kalkan Teknik — site styles (Appearance → Customize → Additional CSS, via custom_css_set) */
:root{--kt-bg:#0B1220;--kt-bg2:#0D1526;--kt-card:#111A2C;--kt-line:#22304A;--kt-line2:#2A3A58;--kt-text:#E8EDF5;--kt-soft:#C6D0DE;--kt-muted:#AEBBCD;--kt-dim:#9AA8BD;--kt-amber:#F5A524;--kt-amber-d:#9A5B00;--kt-green:#25D366;--kt-ok:#3DDC84;--kt-rec:#FF6B5E;--kt-light:#F4F2ED;--kt-ink:#0B1220;--kt-ink2:#46526A;--kt-cardline:#E3DED3;--kt-display:"Bricolage Grotesque",system-ui,sans-serif}
body{background:var(--kt-bg);color:var(--kt-text)}
html{scroll-behavior:smooth}
[id]{scroll-margin-top:90px}
.entry-content>.alignfull{margin-top:0;margin-bottom:0}
.kt-wrap{max-width:1200px;margin-left:auto !important;margin-right:auto !important;padding:112px 32px;box-sizing:border-box}
.kt-light{background:var(--kt-light);color:var(--kt-ink)}
.kt-light h1,.kt-light h2,.kt-light h3,.kt-light strong{color:var(--kt-ink)}
.kt-deep{background:var(--kt-bg2);border-top:1px solid #1C2840;border-bottom:1px solid #1C2840}
.kt-eyebrow{font-size:13px !important;font-weight:700;letter-spacing:2px;text-transform:uppercase;color:var(--kt-amber) !important;margin:0 0 14px !important}
.kt-light .kt-eyebrow{color:var(--kt-amber-d) !important}
.kt-h1{font-family:var(--kt-display);font-weight:700;font-size:clamp(38px,4.6vw,62px) !important;line-height:1.04;letter-spacing:-1.5px;margin:0 0 24px;color:var(--kt-text)}
.kt-h2{font-family:var(--kt-display);font-weight:700;font-size:clamp(30px,3.4vw,46px) !important;line-height:1.1;letter-spacing:-1px;margin:0 0 16px}
.kt-amber{color:var(--kt-amber)}
.kt-lead{font-size:19px;line-height:1.65;color:var(--kt-muted);max-width:34em}
.kt-light .kt-lead{color:var(--kt-ink2)}
.kt-head{max-width:720px;margin-bottom:52px !important}
/* pill */
.kt-pill{display:inline-flex !important;align-items:center;gap:10px;border:1px solid var(--kt-line2);border-radius:999px;padding:8px 16px !important;font-size:13px !important;font-weight:600;color:var(--kt-soft);margin:0 0 26px !important}
.kt-pill:before{content:"";width:8px;height:8px;border-radius:50%;background:var(--kt-ok)}
/* buttons */
.wp-block-button[class*=kt-btn] .wp-block-button__link{border-radius:14px !important;padding:16px 24px !important;font-weight:700;font-size:16px;min-height:52px;display:inline-flex;align-items:center;gap:10px;box-sizing:border-box}
.kt-btn .wp-block-button__link{background:var(--kt-amber) !important;color:var(--kt-ink) !important}
.kt-btn-wa .wp-block-button__link{background:var(--kt-green) !important;color:#06210F !important}
.kt-btn-line .wp-block-button__link{background:transparent !important;color:var(--kt-text) !important;border:1px solid var(--kt-line2) !important}
.kt-btn-dark .wp-block-button__link{background:var(--kt-ink) !important;color:#fff !important}
.kt-btn-ink-line .wp-block-button__link{background:transparent !important;color:var(--kt-ink) !important;border:2px solid var(--kt-ink) !important}
.kt-btn-wa .wp-block-button__link:before{content:"";width:20px;height:20px;background:currentColor;-webkit-mask:var(--kt-i-chat) center/contain no-repeat;mask:var(--kt-i-chat) center/contain no-repeat}
/* icons (masks) */
:root{
--kt-i-bolt:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='%23000' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'%3E%3Cpath d='M13 2 4 14h7l-1 8 9-12h-7l1-8z'/%3E%3C/svg%3E");
--kt-i-cam:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='%23000' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'%3E%3Crect x='2' y='6' width='14' height='8' rx='2'/%3E%3Cpath d='m16 9 5-2v8l-5-2'/%3E%3Cpath d='M6 14v4H3'/%3E%3C/svg%3E");
--kt-i-fire:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='%23000' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'%3E%3Cpath d='M12 3c1 3 5 5 5 10a5 5 0 0 1-10 0c0-2.5 1.2-4 2.5-5 0 2 1 3.5 2.5 3.5 0-3.5-1-6 0-8.5z'/%3E%3C/svg%3E");
--kt-i-lock:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='%23000' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'%3E%3Cpath d='M12 3 4 6v6c0 5 3.5 8 8 9 4.5-1 8-4 8-9V6z'/%3E%3Crect x='9' y='11' width='6' height='5' rx='1'/%3E%3Cpath d='M10 11V9a2 2 0 0 1 4 0v2'/%3E%3C/svg%3E");
--kt-i-net:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='%23000' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'%3E%3Crect x='9' y='3' width='6' height='5' rx='1'/%3E%3Crect x='3' y='16' width='6' height='5' rx='1'/%3E%3Crect x='15' y='16' width='6' height='5' rx='1'/%3E%3Cpath d='M12 8v4M6 16v-4h12v4'/%3E%3C/svg%3E");
--kt-i-wifi:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='%23000' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'%3E%3Cpath d='M2 9a15 15 0 0 1 20 0'/%3E%3Cpath d='M5 12.5a10 10 0 0 1 14 0'/%3E%3Cpath d='M8.5 16a5 5 0 0 1 7 0'/%3E%3Ccircle cx='12' cy='19.5' r='1'/%3E%3C/svg%3E");
--kt-i-search:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='%23000' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'%3E%3Ccircle cx='11' cy='11' r='7'/%3E%3Cpath d='m20 20-3.5-3.5'/%3E%3C/svg%3E");
--kt-i-doc:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='%23000' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'%3E%3Cpath d='M7 3h10v18l-5-3-5 3z'/%3E%3C/svg%3E");
--kt-i-check:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='%23000' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'%3E%3Cpath d='m4 12 5 5L20 6'/%3E%3C/svg%3E");
--kt-i-clock:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='%23000' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'%3E%3Ccircle cx='12' cy='12' r='9'/%3E%3Cpath d='M12 7v5l3 2'/%3E%3C/svg%3E");
--kt-i-pin:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='%23000' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'%3E%3Cpath d='M12 21s7-6.2 7-12a7 7 0 0 0-14 0c0 5.8 7 12 7 12z'/%3E%3Ccircle cx='12' cy='9' r='2.5'/%3E%3C/svg%3E");
--kt-i-phone:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='%23000' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'%3E%3Cpath d='M5 4h4l2 5-2.5 1.5a11 11 0 0 0 5 5L15 13l5 2v4a2 2 0 0 1-2 2A16 16 0 0 1 3 6a2 2 0 0 1 2-2'/%3E%3C/svg%3E");
--kt-i-chat:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='%23000' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'%3E%3Cpath d='M21 12a9 9 0 0 1-13.5 7.8L3 21l1.2-4.5A9 9 0 1 1 21 12z'/%3E%3Cpath d='M9 10.5c.5 2 2 3.5 4.5 4.5l1.2-1.2 1.8.8'/%3E%3C/svg%3E");
--kt-i-mail:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='%23000' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'%3E%3Crect x='3' y='5' width='18' height='14' rx='2'/%3E%3Cpath d='m3 7 9 6 9-6'/%3E%3C/svg%3E")}
.kt-i-bolt{--i:var(--kt-i-bolt)}.kt-i-cam{--i:var(--kt-i-cam)}.kt-i-fire{--i:var(--kt-i-fire)}.kt-i-lock{--i:var(--kt-i-lock)}.kt-i-net{--i:var(--kt-i-net)}.kt-i-wifi{--i:var(--kt-i-wifi)}
.kt-i-search{--i:var(--kt-i-search)}.kt-i-doc{--i:var(--kt-i-doc)}.kt-i-check{--i:var(--kt-i-check)}.kt-i-clock{--i:var(--kt-i-clock)}.kt-i-pin{--i:var(--kt-i-pin)}.kt-i-phone{--i:var(--kt-i-phone)}.kt-i-chat{--i:var(--kt-i-chat)}.kt-i-mail{--i:var(--kt-i-mail)}
/* hero + security panel */
.kt-hero{align-items:center !important;gap:56px !important}
.kt-panel{background:var(--kt-card);border:1px solid var(--kt-line);border-radius:28px;padding:20px;box-shadow:0 40px 80px -40px rgba(0,0,0,.7)}
.kt-panel-top{display:flex;justify-content:space-between;align-items:center;padding:4px 6px 16px;font-weight:700;font-size:15px}
.kt-live{display:inline-flex;align-items:center;gap:8px;font-size:13px;color:var(--kt-ok);font-weight:600}
.kt-live:before{content:"";width:8px;height:8px;border-radius:50%;background:var(--kt-ok);animation:kt-blink 2s infinite}
@keyframes kt-blink{50%{opacity:.35}}
.kt-cams{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:10px}
.kt-cam{position:relative;aspect-ratio:16/10;border-radius:14px;overflow:hidden;background:var(--kt-bg2);border:1px solid var(--kt-line)}
.kt-cam video{position:absolute;top:0;left:0;width:100%;height:100%;object-fit:cover;display:block}
.kt-cam:after{content:"";position:absolute;inset:0;pointer-events:none;background:linear-gradient(rgba(5,10,20,.55),transparent 38%,transparent 70%,rgba(5,10,20,.5)),repeating-linear-gradient(0deg,rgba(0,0,0,.16) 0 1px,transparent 1px 3px)}
.kt-cam span{position:absolute;z-index:2;font-size:11px;font-weight:700;letter-spacing:1px;color:#fff;text-shadow:0 1px 3px rgba(0,0,0,.9)}
.kt-cam .kt-cam-l{left:12px;top:10px}
.kt-cam .kt-cam-l span{position:static;font-size:inherit}
.kt-cam .kt-rec{right:12px;top:10px;color:var(--kt-rec)}
.kt-cam .kt-time{left:12px;bottom:10px;font-family:ui-monospace,Menlo,Consolas,monospace;font-weight:600;letter-spacing:.5px}
/* elapsed recording time, CSS only (no scripts in WordPress content) */
@property --kt-h{syntax:"<integer>";initial-value:0;inherits:false}
@property --kt-m{syntax:"<integer>";initial-value:0;inherits:false}
@property --kt-s{syntax:"<integer>";initial-value:0;inherits:false}
@keyframes kt-h{to{--kt-h:24}}@keyframes kt-m{to{--kt-m:60}}@keyframes kt-s{to{--kt-s:60}}
.kt-time{animation:kt-h 86400s steps(24) infinite,kt-m 3600s steps(60) infinite,kt-s 60s steps(60) infinite;counter-reset:h var(--kt-h) m var(--kt-m) s var(--kt-s)}
.kt-time:after{content:"KAYIT " counter(h,decimal-leading-zero) ":" counter(m,decimal-leading-zero) ":" counter(s,decimal-leading-zero)}
.kt-stats{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:10px;margin-top:10px}
.kt-stats div{background:var(--kt-bg2);border:1px solid var(--kt-line);border-radius:14px;padding:14px}
.kt-stats span{display:block;font-size:12px;color:var(--kt-dim);font-weight:600}
.kt-stats strong{display:block;margin-top:6px;font-size:15px;color:var(--kt-text)}
.kt-stats .kt-ok{color:var(--kt-ok)}
/* trust strip */
.kt-trust{padding:32px !important;max-width:1200px;margin:0 auto !important;gap:24px !important}
.kt-ti{position:relative;padding-left:42px !important;margin:0 !important;font-size:14px;color:var(--kt-dim);line-height:1.45}
.kt-ti strong{color:var(--kt-text);font-size:16px}
.kt-ti:before,.kt-ci:before{content:"";position:absolute;left:0;top:50%;transform:translateY(-50%);width:26px;height:26px;background:var(--kt-amber);-webkit-mask:var(--i) center/contain no-repeat;mask:var(--i) center/contain no-repeat}
/* service cards */
.kt-grid{gap:20px !important}
.kt-card{background:#fff;border:1px solid var(--kt-cardline);border-radius:22px;padding:30px !important;height:100%;box-sizing:border-box;transition:transform .25s,box-shadow .25s}
.kt-card:hover{transform:translateY(-4px);box-shadow:0 24px 48px -28px rgba(11,18,32,.35)}
.kt-card h3{position:relative;font-family:var(--kt-display);font-size:23px !important;font-weight:600;padding-top:70px;margin:0 0 12px !important}
.kt-card h3:before{content:"";position:absolute;left:0;top:0;width:52px;height:52px;border-radius:14px;background:var(--kt-ink)}
.kt-card h3:after{content:"";position:absolute;left:13px;top:13px;width:26px;height:26px;background:var(--kt-amber);-webkit-mask:var(--i) center/contain no-repeat;mask:var(--i) center/contain no-repeat}
.kt-card p{color:var(--kt-ink2);line-height:1.6;margin:0 0 14px}
.kt-card ul{list-style:none;padding:0 !important;margin:0;display:grid;gap:8px;font-size:15px;color:#2A3448}
.kt-card li:before{content:"— "}
/* process */
.kt-steps{gap:20px !important}
.kt-step{border-top:2px solid var(--kt-line2);padding-top:22px !important}
.kt-step:first-child{border-top-color:var(--kt-amber)}
.kt-step .kt-num{font-family:var(--kt-display);font-weight:600;font-size:15px;color:var(--kt-amber);margin:0 0 8px}
.kt-step h3{font-family:var(--kt-display);font-size:23px !important;font-weight:600;margin:0 0 8px}
.kt-step p{color:var(--kt-muted);line-height:1.6;margin:0}
/* cta band */
.kt-band{background:var(--kt-amber);color:var(--kt-ink);border-radius:28px;padding:44px 48px !important;margin-top:56px !important;gap:24px 32px}
.kt-band h2{font-family:var(--kt-display);font-size:34px !important;font-weight:700;line-height:1.15;margin:0 0 8px;color:var(--kt-ink)}
.kt-band p{margin:0;font-weight:500;font-size:17px;color:var(--kt-ink)}
/* area + map */
.kt-ci{position:relative;padding-left:34px !important;margin:0 0 12px !important;font-size:16px}
.kt-light .kt-ci:before{top:1px;transform:none;background:var(--kt-amber-d);width:22px;height:22px}
.kt-map{position:relative;border-radius:28px;overflow:hidden;border:1px solid var(--kt-cardline);aspect-ratio:4/3;background-color:#E9E5DC;background-image:repeating-linear-gradient(0deg,transparent 0 46px,#DDD7CB 46px 48px),repeating-linear-gradient(90deg,transparent 0 46px,#DDD7CB 46px 48px)}
.kt-map .kt-road1{position:absolute;left:-10%;top:46%;width:120%;height:18px;background:#fff;transform:rotate(-12deg)}
.kt-map .kt-road2{position:absolute;left:58%;top:-10%;width:14px;height:120%;background:#fff;transform:rotate(8deg)}
.kt-map .kt-pin{position:absolute;left:50%;top:44%;transform:translate(-50%,-100%);display:flex;flex-direction:column;align-items:center;gap:8px}
.kt-map .kt-pin b{background:var(--kt-ink);color:#fff;font-size:13px;padding:8px 14px;border-radius:10px;white-space:nowrap}
.kt-map .kt-note{position:absolute;left:16px;bottom:16px;background:rgba(255,255,255,.92);color:var(--kt-ink2);font-size:12px;font-weight:600;padding:6px 10px;border-radius:8px}
.kt-map .kt-go{position:absolute;right:16px;bottom:16px;background:var(--kt-ink);color:#fff !important;font-size:14px;font-weight:700;padding:12px 16px;border-radius:12px;text-decoration:none}
.kt-map-embed iframe{width:100%;aspect-ratio:4/3;height:auto;border:0;border-radius:28px;display:block}
/* contact */
.kt-two{gap:48px !important}
.kt-cc{position:relative;padding-left:84px !important;background:var(--kt-card);border:1px solid var(--kt-line);border-radius:18px;padding-top:18px !important;padding-bottom:18px !important;padding-right:20px !important;margin:0 0 14px !important;font-size:20px;font-weight:700;line-height:1.3}
.kt-cc small{font-size:13px;color:var(--kt-dim);font-weight:600}
.kt-cc a{color:var(--kt-text);text-decoration:none}
.kt-cc:before{content:"";position:absolute;left:20px;top:50%;transform:translateY(-50%);width:48px;height:48px;border-radius:12px;background:var(--kt-amber) var(--i) center/22px no-repeat}
.kt-cc.kt-i-chat:before{background-color:var(--kt-green)}
.kt-form{background:var(--kt-card);border:1px solid var(--kt-line);border-radius:28px;padding:36px !important}
.kt-form h3{font-family:var(--kt-display);font-size:26px !important;font-weight:700;margin:0 0 18px}
.kt-form .wpcf7 p{margin:0 0 16px;font-size:14px;font-weight:600;color:var(--kt-soft)}
.kt-form .wpcf7 input:not([type=checkbox]):not([type=submit]),.kt-form .wpcf7 select,.kt-form .wpcf7 textarea{width:100%;background:var(--kt-bg);border:1px solid var(--kt-line2);border-radius:12px;padding:14px;color:var(--kt-text);font-size:16px;margin-top:8px;box-sizing:border-box}
.kt-form .wpcf7 .wpcf7-acceptance{font-weight:400;color:var(--kt-muted)}
.kt-form .wpcf7 input[type=checkbox]{accent-color:var(--kt-amber);width:20px;height:20px;vertical-align:middle}
.kt-form .wpcf7 input[type=submit]{width:100%;background:var(--kt-amber);color:var(--kt-ink);border:0;border-radius:14px;padding:16px;font-weight:700;font-size:16px;cursor:pointer;min-height:52px}
/* header + footer (Kadence) */
.site-header .header-button{background:var(--kt-amber) !important;color:var(--kt-ink) !important;border-radius:12px !important;font-weight:700}
#masthead,.site-main-header-wrap .site-header-row-container-inner{background:rgba(11,18,32,.95)}
.site-main-header-wrap{border-bottom:1px solid #1C2840}
.site-footer,.site-footer .site-middle-footer-wrap .site-footer-row-container-inner{background:#070C16}
.site-footer,.site-footer a{color:var(--kt-dim)}
.site-footer a:hover{color:#fff}
.site-footer .widget-title{color:#fff;font-size:16px;font-weight:700;text-transform:none;letter-spacing:0}
.kt-flinks{list-style:none;padding:0 !important}.kt-flinks li{margin:0 0 10px}
/* floating WhatsApp + mobile call bar (footer widget) */
.kt-wa{position:fixed;right:24px;bottom:24px;z-index:99;width:60px;height:60px;border-radius:50%;background:var(--kt-green);display:flex;align-items:center;justify-content:center;box-shadow:0 14px 30px -8px rgba(37,211,102,.55)}
.kt-wa:before{content:"";width:28px;height:28px;background:#06210F;-webkit-mask:var(--kt-i-chat) center/contain no-repeat;mask:var(--kt-i-chat) center/contain no-repeat}
.kt-bar{display:none}
@media (max-width:767px){
.kt-wrap{padding:72px 20px}
.kt-band{padding:28px !important}
.kt-wa{display:none}
.kt-bar{display:grid;grid-template-columns:1fr 1fr;gap:10px;position:fixed;left:0;right:0;bottom:0;z-index:99;padding:12px 16px 20px;background:rgba(7,12,22,.96);border-top:1px solid #1C2840}
.kt-bar a{display:flex;align-items:center;justify-content:center;gap:8px;min-height:50px;border-radius:14px;font-weight:700;text-decoration:none}
.kt-bar .kt-bar-call{border:1px solid var(--kt-line2);color:var(--kt-text)}
.kt-bar .kt-bar-wa{background:var(--kt-green);color:#06210F}
body{padding-bottom:84px}
.kt-cam .kt-cam-l span{display:none}
.kt-cam span{font-size:9px}
.kt-stats strong{font-size:14px}
}
```

## 5. Contact form (form_create)
```json
{
 "title": "Keşif talebi",
 "submit": "Talebi gönder",
 "subject": "Yeni keşif talebi — Kalkan Teknik",
 "fields": [
  {
   "name": "ad-soyad",
   "label": "Ad soyad",
   "type": "text",
   "required": true
  },
  {
   "name": "telefon",
   "label": "Telefon",
   "type": "tel",
   "required": true
  },
  {
   "name": "hizmet",
   "label": "Hizmet",
   "type": "select",
   "options": [
    "Elektrik tesisatı",
    "Güvenlik kamerası",
    "Yangın alarm sistemi",
    "Hırsız alarm sistemi",
    "Network ve kablolama",
    "Wi-Fi çözümleri",
    "Diğer"
   ]
  },
  {
   "name": "mesaj",
   "label": "Mesajınız",
   "type": "textarea"
  },
  {
   "name": "kvkk",
   "label": "Bilgilerimin bu talebi yanıtlamak için kullanılmasını kabul ediyorum (KVKK).",
   "type": "acceptance",
   "required": true
  }
 ],
 "recipient": "(leave empty = site admin email)"
}
```

## 6. Footer widgets (widgets_set, one call per area)
footer4 also carries the floating WhatsApp button and the mobile call bar (fixed position, shown on every page).
```json
{
 "footer1": [
  "<!-- wp:image {\"width\":\"175px\",\"sizeSlug\":\"full\",\"linkDestination\":\"custom\"} -->\n<figure class=\"wp-block-image size-full is-resized\"><a href=\"{{site}}/\"><img src=\"{{img:logo}}\" alt=\"Kalkan Teknik\" style=\"width:175px\"/></a></figure>\n<!-- /wp:image -->",
  "<!-- wp:paragraph -->\n<p>Elektrik, güvenlik ve ağ sistemlerinde keşif, kurulum ve bakım.</p>\n<!-- /wp:paragraph -->"
 ],
 "footer2": [
  "<!-- wp:heading {\"className\": \"widget-title\"} -->\n<h2 class=\"wp-block-heading widget-title\">Hizmetler</h2>\n<!-- /wp:heading -->",
  "<!-- wp:list {\"className\": \"kt-flinks\"} -->\n<ul class=\"wp-block-list kt-flinks\"><!-- wp:list-item -->\n<li><a href=\"{{site}}/#hizmetler\">Elektrik tesisatı</a></li>\n<!-- /wp:list-item -->\n\n<!-- wp:list-item -->\n<li><a href=\"{{site}}/#hizmetler\">Güvenlik kamerası</a></li>\n<!-- /wp:list-item -->\n\n<!-- wp:list-item -->\n<li><a href=\"{{site}}/#hizmetler\">Yangın ve hırsız alarm</a></li>\n<!-- /wp:list-item -->\n\n<!-- wp:list-item -->\n<li><a href=\"{{site}}/#hizmetler\">Network ve Wi-Fi</a></li>\n<!-- /wp:list-item --></ul>\n<!-- /wp:list -->"
 ],
 "footer3": [
  "<!-- wp:heading {\"className\": \"widget-title\"} -->\n<h2 class=\"wp-block-heading widget-title\">Sayfa</h2>\n<!-- /wp:heading -->",
  "<!-- wp:list {\"className\": \"kt-flinks\"} -->\n<ul class=\"wp-block-list kt-flinks\"><!-- wp:list-item -->\n<li><a href=\"{{site}}/#surec\">Nasıl çalışırız</a></li>\n<!-- /wp:list-item -->\n\n<!-- wp:list-item -->\n<li><a href=\"{{site}}/#bolge\">Hizmet bölgesi</a></li>\n<!-- /wp:list-item -->\n\n<!-- wp:list-item -->\n<li><a href=\"{{site}}/#iletisim\">İletişim</a></li>\n<!-- /wp:list-item --></ul>\n<!-- /wp:list -->"
 ],
 "footer4": [
  "<!-- wp:heading {\"className\": \"widget-title\"} -->\n<h2 class=\"wp-block-heading widget-title\">İletişim</h2>\n<!-- /wp:heading -->",
  "<!-- wp:paragraph -->\n<p><a href=\"tel:+90XXXXXXXXXX\">[0 5XX XXX XX XX]</a><br>[ornek@firma.com]<br>[Açık adres]</p>\n<!-- /wp:paragraph -->",
  "<!-- wp:html -->\n<a class=\"kt-wa\" href=\"https://wa.me/90XXXXXXXXXX\" aria-label=\"WhatsApp'tan yazın\"></a><div class=\"kt-bar\"><a class=\"kt-bar-call\" href=\"tel:+90XXXXXXXXXX\">Ara</a><a class=\"kt-bar-wa\" href=\"https://wa.me/90XXXXXXXXXX\">WhatsApp</a></div>\n<!-- /wp:html -->"
 ]
}
```

## 7. Menu (menu_set)
```json
{
 "name": "Ana menü",
 "location": "primary (also the mobile menu)",
 "items": [
  {
   "title": "Hizmetler",
   "url": "{{site}}/#hizmetler"
  },
  {
   "title": "Nasıl çalışırız",
   "url": "{{site}}/#surec"
  },
  {
   "title": "Hizmet bölgesi",
   "url": "{{site}}/#bolge"
  },
  {
   "title": "İletişim",
   "url": "{{site}}/#iletisim"
  }
 ],
 "note": "All items are custom links to sections of the one-page homepage."
}
```

## 8. Page (content_create_draft, post_type page, then content_publish)

### Page: Anasayfa
```html
<!-- wp:group {"anchor": "top", "align": "full", "className": "kt-hero-band", "layout": {"type": "default"}} -->
<div id="top" class="wp-block-group alignfull kt-hero-band"><!-- wp:columns {"className": "kt-wrap kt-hero"} -->
<div class="wp-block-columns kt-wrap kt-hero"><!-- wp:column -->
<div class="wp-block-column"><!-- wp:paragraph {"className": "kt-pill"} -->
<p class="kt-pill">[Şehir] ve çevresinde teknik servis</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level": 1, "className": "kt-h1"} -->
<h1 class="wp-block-heading kt-h1">Elektrikten güvenliğe, <span class="kt-amber">tek ekip</span> tek numara.</h1>
<!-- /wp:heading -->

<!-- wp:paragraph {"className": "kt-lead"} -->
<p class="kt-lead">Elektrik tesisatı, güvenlik kamerası, yangın ve hırsız alarm sistemleri, network ve Wi-Fi. Ev ve iş yeriniz için keşiften kuruluma, bakıma kadar.</p>
<!-- /wp:paragraph -->

<!-- wp:buttons -->
<div class="wp-block-buttons"><!-- wp:button {"className":"kt-btn-wa"} -->
<div class="wp-block-button kt-btn-wa"><a class="wp-block-button__link wp-element-button" href="https://wa.me/90XXXXXXXXXX">WhatsApp'tan yazın</a></div>
<!-- /wp:button -->

<!-- wp:button {"className":"kt-btn-line"} -->
<div class="wp-block-button kt-btn-line"><a class="wp-block-button__link wp-element-button" href="{{site}}/#hizmetler">Hizmetleri gör →</a></div>
<!-- /wp:button --></div>
<!-- /wp:buttons --></div>
<!-- /wp:column -->

<!-- wp:column -->
<div class="wp-block-column"><!-- wp:html -->
<div class="kt-panel" role="img" aria-label="Güvenlik paneli: dört kameradan canlı görüntü"><div class="kt-panel-top"><span>Güvenlik paneli</span><span class="kt-live">Sistem aktif</span></div><div class="kt-cams"><div class="kt-cam"><video src="https://cdn.jsdelivr.net/gh/fatihborasoftware-sudo/kalkan-teknik@main/assets/video/cam01.mp4" poster="{{img:cam01}}" autoplay muted loop playsinline preload="auto"></video><span class="kt-cam-l">CAM 01<span> · GİRİŞ</span></span><span class="kt-rec">● REC</span><span class="kt-time"></span></div><div class="kt-cam"><video src="https://cdn.jsdelivr.net/gh/fatihborasoftware-sudo/kalkan-teknik@main/assets/video/cam02.mp4" poster="{{img:cam02}}" autoplay muted loop playsinline preload="auto"></video><span class="kt-cam-l">CAM 02<span> · OTOPARK</span></span><span class="kt-rec">● REC</span><span class="kt-time"></span></div><div class="kt-cam"><video src="https://cdn.jsdelivr.net/gh/fatihborasoftware-sudo/kalkan-teknik@main/assets/video/cam03.mp4" poster="{{img:cam03}}" autoplay muted loop playsinline preload="auto"></video><span class="kt-cam-l">CAM 03<span> · DEPO</span></span><span class="kt-rec">● REC</span><span class="kt-time"></span></div><div class="kt-cam"><video src="https://cdn.jsdelivr.net/gh/fatihborasoftware-sudo/kalkan-teknik@main/assets/video/cam04.mp4" poster="{{img:cam04}}" autoplay muted loop playsinline preload="auto"></video><span class="kt-cam-l">CAM 04<span> · BAHÇE</span></span><span class="kt-rec">● REC</span><span class="kt-time"></span></div></div><div class="kt-stats"><div><span>Hırsız alarmı</span><strong class="kt-ok">Devrede</strong></div><div><span>Yangın paneli</span><strong>Normal</strong></div><div><span>Ağ / Wi-Fi</span><strong>Bağlı</strong></div></div></div>
<!-- /wp:html --></div>
<!-- /wp:column --></div>
<!-- /wp:columns --></div>
<!-- /wp:group -->

<!-- wp:group {"align": "full", "className": "kt-deep", "layout": {"type": "default"}} -->
<div class="wp-block-group alignfull kt-deep"><!-- wp:group {"className": "kt-trust", "layout": {"type": "grid", "minimumColumnWidth": "14rem"}} -->
<div class="wp-block-group kt-trust"><!-- wp:paragraph {"className": "kt-ti kt-i-search"} -->
<p class="kt-ti kt-i-search"><strong>Yerinde keşif</strong><br>İhtiyacı görerek planlarız</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph {"className": "kt-ti kt-i-doc"} -->
<p class="kt-ti kt-i-doc"><strong>Yazılı teklif</strong><br>Kalem kalem, sürprizsiz</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph {"className": "kt-ti kt-i-check"} -->
<p class="kt-ti kt-i-check"><strong>Temiz işçilik</strong><br>Kablo düzeni, etiketleme</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph {"className": "kt-ti kt-i-clock"} -->
<p class="kt-ti kt-i-clock"><strong>Bakım ve destek</strong><br>Kurulumdan sonra da yanınızda</p>
<!-- /wp:paragraph --></div>
<!-- /wp:group --></div>
<!-- /wp:group -->

<!-- wp:group {"anchor": "hizmetler", "align": "full", "className": "kt-light", "layout": {"type": "default"}} -->
<div id="hizmetler" class="wp-block-group alignfull kt-light"><!-- wp:group {"className": "kt-wrap", "layout": {"type": "default"}} -->
<div class="wp-block-group kt-wrap"><!-- wp:group {"className": "kt-head", "layout": {"type": "default"}} -->
<div class="wp-block-group kt-head"><!-- wp:paragraph {"className": "kt-eyebrow"} -->
<p class="kt-eyebrow">Hizmetler</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"className": "kt-h2"} -->
<h2 class="wp-block-heading kt-h2">Altı uzmanlık, tek servis</h2>
<!-- /wp:heading -->

<!-- wp:paragraph {"className": "kt-lead"} -->
<p class="kt-lead">Ayrı ayrı usta aramayın. Tesisattan kameraya, alarmdan internete kadar hepsini aynı ekip kurar ve aynı ekip bakımını yapar.</p>
<!-- /wp:paragraph --></div>
<!-- /wp:group -->

<!-- wp:group {"className": "kt-grid", "layout": {"type": "grid", "minimumColumnWidth": "18rem"}} -->
<div class="wp-block-group kt-grid"><!-- wp:group {"className": "kt-card", "layout": {"type": "default"}} -->
<div class="wp-block-group kt-card"><!-- wp:heading {"level": 3, "className": "kt-i-bolt"} -->
<h3 class="wp-block-heading kt-i-bolt">Elektrik tesisatı</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Yeni tesisat, pano yenileme, arıza tespiti ve aydınlatma.</p>
<!-- /wp:paragraph -->

<!-- wp:list -->
<ul class="wp-block-list"><!-- wp:list-item -->
<li>Sigorta ve kaçak akım panosu</li>
<!-- /wp:list-item -->

<!-- wp:list-item -->
<li>Priz, anahtar, hat çekimi</li>
<!-- /wp:list-item -->

<!-- wp:list-item -->
<li>LED ve dış aydınlatma</li>
<!-- /wp:list-item --></ul>
<!-- /wp:list --></div>
<!-- /wp:group -->

<!-- wp:group {"className": "kt-card", "layout": {"type": "default"}} -->
<div class="wp-block-group kt-card"><!-- wp:heading {"level": 3, "className": "kt-i-cam"} -->
<h3 class="wp-block-heading kt-i-cam">Güvenlik kamerası</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>IP ve analog kamera kurulumu, kayıt cihazı, telefondan izleme.</p>
<!-- /wp:paragraph -->

<!-- wp:list -->
<ul class="wp-block-list"><!-- wp:list-item -->
<li>İç ve dış mekân kamera</li>
<!-- /wp:list-item -->

<!-- wp:list-item -->
<li>NVR / DVR kurulumu</li>
<!-- /wp:list-item -->

<!-- wp:list-item -->
<li>Mobil uygulamadan canlı izleme</li>
<!-- /wp:list-item --></ul>
<!-- /wp:list --></div>
<!-- /wp:group -->

<!-- wp:group {"className": "kt-card", "layout": {"type": "default"}} -->
<div class="wp-block-group kt-card"><!-- wp:heading {"level": 3, "className": "kt-i-fire"} -->
<h3 class="wp-block-heading kt-i-fire">Yangın alarm sistemi</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Duman ve ısı dedektörleri, yangın paneli, sesli-ışıklı uyarı.</p>
<!-- /wp:paragraph -->

<!-- wp:list -->
<ul class="wp-block-list"><!-- wp:list-item -->
<li>Konvansiyonel ve adresli panel</li>
<!-- /wp:list-item -->

<!-- wp:list-item -->
<li>Dedektör ve buton montajı</li>
<!-- /wp:list-item -->

<!-- wp:list-item -->
<li>Periyodik test ve bakım</li>
<!-- /wp:list-item --></ul>
<!-- /wp:list --></div>
<!-- /wp:group -->

<!-- wp:group {"className": "kt-card", "layout": {"type": "default"}} -->
<div class="wp-block-group kt-card"><!-- wp:heading {"level": 3, "className": "kt-i-lock"} -->
<h3 class="wp-block-heading kt-i-lock">Hırsız alarm sistemi</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Hareket ve kapı-pencere sensörleri, siren, uzaktan kurma.</p>
<!-- /wp:paragraph -->

<!-- wp:list -->
<ul class="wp-block-list"><!-- wp:list-item -->
<li>Kablolu ve kablosuz sistem</li>
<!-- /wp:list-item -->

<!-- wp:list-item -->
<li>Telefondan kur / devre dışı bırak</li>
<!-- /wp:list-item -->

<!-- wp:list-item -->
<li>Alarm anında bildirim</li>
<!-- /wp:list-item --></ul>
<!-- /wp:list --></div>
<!-- /wp:group -->

<!-- wp:group {"className": "kt-card", "layout": {"type": "default"}} -->
<div class="wp-block-group kt-card"><!-- wp:heading {"level": 3, "className": "kt-i-net"} -->
<h3 class="wp-block-heading kt-i-net">Network ve kablolama</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Ofis ve ev ağı, kabin düzeni, switch ve modem kurulumu.</p>
<!-- /wp:paragraph -->

<!-- wp:list -->
<ul class="wp-block-list"><!-- wp:list-item -->
<li>Cat6 data kablolama</li>
<!-- /wp:list-item -->

<!-- wp:list-item -->
<li>Rack kabin ve patch panel</li>
<!-- /wp:list-item -->

<!-- wp:list-item -->
<li>Ağ arıza tespiti</li>
<!-- /wp:list-item --></ul>
<!-- /wp:list --></div>
<!-- /wp:group -->

<!-- wp:group {"className": "kt-card", "layout": {"type": "default"}} -->
<div class="wp-block-group kt-card"><!-- wp:heading {"level": 3, "className": "kt-i-wifi"} -->
<h3 class="wp-block-heading kt-i-wifi">Wi-Fi çözümleri</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Çekmeyen odalara son. Mesh, erişim noktası ve misafir ağı.</p>
<!-- /wp:paragraph -->

<!-- wp:list -->
<ul class="wp-block-list"><!-- wp:list-item -->
<li>Kapsama ölçümü</li>
<!-- /wp:list-item -->

<!-- wp:list-item -->
<li>Mesh ve access point</li>
<!-- /wp:list-item -->

<!-- wp:list-item -->
<li>Ayrı misafir ağı</li>
<!-- /wp:list-item --></ul>
<!-- /wp:list --></div>
<!-- /wp:group --></div>
<!-- /wp:group --></div>
<!-- /wp:group --></div>
<!-- /wp:group -->

<!-- wp:group {"anchor": "surec", "align": "full", "layout": {"type": "default"}} -->
<div id="surec" class="wp-block-group alignfull"><!-- wp:group {"className": "kt-wrap", "layout": {"type": "default"}} -->
<div class="wp-block-group kt-wrap"><!-- wp:group {"className": "kt-head", "layout": {"type": "default"}} -->
<div class="wp-block-group kt-head"><!-- wp:paragraph {"className": "kt-eyebrow"} -->
<p class="kt-eyebrow">Nasıl çalışırız</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"className": "kt-h2"} -->
<h2 class="wp-block-heading kt-h2">Dört adımda bitmiş iş</h2>
<!-- /wp:heading --></div>
<!-- /wp:group -->

<!-- wp:group {"className": "kt-steps", "layout": {"type": "grid", "minimumColumnWidth": "14rem"}} -->
<div class="wp-block-group kt-steps"><!-- wp:group {"className": "kt-step", "layout": {"type": "default"}} -->
<div class="wp-block-group kt-step"><!-- wp:paragraph {"className": "kt-num"} -->
<p class="kt-num">01</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level": 3} -->
<h3 class="wp-block-heading">Keşif</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Yerinde bakar, ihtiyacınızı ve mevcut tesisatı not alırız.</p>
<!-- /wp:paragraph --></div>
<!-- /wp:group -->

<!-- wp:group {"className": "kt-step", "layout": {"type": "default"}} -->
<div class="wp-block-group kt-step"><!-- wp:paragraph {"className": "kt-num"} -->
<p class="kt-num">02</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level": 3} -->
<h3 class="wp-block-heading">Teklif</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Malzeme ve işçiliği ayrı ayrı yazan net bir teklif.</p>
<!-- /wp:paragraph --></div>
<!-- /wp:group -->

<!-- wp:group {"className": "kt-step", "layout": {"type": "default"}} -->
<div class="wp-block-group kt-step"><!-- wp:paragraph {"className": "kt-num"} -->
<p class="kt-num">03</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level": 3} -->
<h3 class="wp-block-heading">Kurulum</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Söz verilen günde, temiz ve düzenli montaj.</p>
<!-- /wp:paragraph --></div>
<!-- /wp:group -->

<!-- wp:group {"className": "kt-step", "layout": {"type": "default"}} -->
<div class="wp-block-group kt-step"><!-- wp:paragraph {"className": "kt-num"} -->
<p class="kt-num">04</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level": 3} -->
<h3 class="wp-block-heading">Teslim ve destek</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Sistemi gösterir, kullanımı anlatır, bakımı üstleniriz.</p>
<!-- /wp:paragraph --></div>
<!-- /wp:group --></div>
<!-- /wp:group -->

<!-- wp:group {"className": "kt-band", "layout": {"type": "flex", "flexWrap": "wrap", "justifyContent": "space-between", "verticalAlignment": "center"}} -->
<div class="wp-block-group kt-band"><!-- wp:group {"layout": {"type": "default"}} -->
<div class="wp-block-group"><!-- wp:heading -->
<h2 class="wp-block-heading">Arıza mı var, yeni kurulum mu?</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Fotoğrafını WhatsApp'tan gönderin, size hızlıca dönelim.</p>
<!-- /wp:paragraph --></div>
<!-- /wp:group -->

<!-- wp:buttons -->
<div class="wp-block-buttons"><!-- wp:button {"className":"kt-btn-dark"} -->
<div class="wp-block-button kt-btn-dark"><a class="wp-block-button__link wp-element-button" href="https://wa.me/90XXXXXXXXXX">WhatsApp'tan yazın</a></div>
<!-- /wp:button -->

<!-- wp:button {"className":"kt-btn-ink-line"} -->
<div class="wp-block-button kt-btn-ink-line"><a class="wp-block-button__link wp-element-button" href="tel:+90XXXXXXXXXX">Hemen arayın</a></div>
<!-- /wp:button --></div>
<!-- /wp:buttons --></div>
<!-- /wp:group --></div>
<!-- /wp:group --></div>
<!-- /wp:group -->

<!-- wp:group {"anchor": "bolge", "align": "full", "className": "kt-light", "layout": {"type": "default"}} -->
<div id="bolge" class="wp-block-group alignfull kt-light"><!-- wp:columns {"className": "kt-wrap kt-hero"} -->
<div class="wp-block-columns kt-wrap kt-hero"><!-- wp:column -->
<div class="wp-block-column"><!-- wp:paragraph {"className": "kt-eyebrow"} -->
<p class="kt-eyebrow">Hizmet bölgesi</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"className": "kt-h2"} -->
<h2 class="wp-block-heading kt-h2">[Şehir] ve çevresindeyiz</h2>
<!-- /wp:heading -->

<!-- wp:paragraph {"className": "kt-lead"} -->
<p class="kt-lead">[İlçe 1], [İlçe 2], [İlçe 3] ve yakın bölgelere servis veriyoruz. Bölgeniz listede yoksa yine de yazın.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph {"className": "kt-ci kt-i-pin"} -->
<p class="kt-ci kt-i-pin">[Açık adres]</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph {"className": "kt-ci kt-i-clock"} -->
<p class="kt-ci kt-i-clock">Hafta içi [09:00–19:00] · Cumartesi [09:00–17:00]</p>
<!-- /wp:paragraph --></div>
<!-- /wp:column -->

<!-- wp:column {"className": "kt-map-embed"} -->
<div class="wp-block-column kt-map-embed"><!-- wp:html -->
<div class="kt-map" role="img" aria-label="Harita yeri"><span class="kt-road1"></span><span class="kt-road2"></span><span class="kt-pin"><b>Kalkan Teknik</b><svg width="40" height="48" viewBox="0 0 24 28" aria-hidden="true"><path d="M12 27s10-8.6 10-16A10 10 0 0 0 2 11c0 7.4 10 16 10 16z" fill="#F5A524" stroke="#0B1220" stroke-width="1.5"/><circle cx="12" cy="11" r="3.5" fill="#0B1220"/></svg></span><span class="kt-note">Google Haritalar buraya gelecek</span><a class="kt-go" href="https://www.google.com/maps">Yol tarifi al ↗</a></div>
<!-- /wp:html --></div>
<!-- /wp:column --></div>
<!-- /wp:columns --></div>
<!-- /wp:group -->

<!-- wp:group {"anchor": "iletisim", "align": "full", "layout": {"type": "default"}} -->
<div id="iletisim" class="wp-block-group alignfull"><!-- wp:columns {"className": "kt-wrap kt-two"} -->
<div class="wp-block-columns kt-wrap kt-two"><!-- wp:column -->
<div class="wp-block-column"><!-- wp:paragraph {"className": "kt-eyebrow"} -->
<p class="kt-eyebrow">İletişim</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"className": "kt-h2"} -->
<h2 class="wp-block-heading kt-h2">Keşif için bize ulaşın</h2>
<!-- /wp:heading -->

<!-- wp:paragraph {"className": "kt-lead"} -->
<p class="kt-lead">Formu doldurun ya da doğrudan arayın. Ne yaptırmak istediğinizi kısaca yazmanız yeterli.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph {"className": "kt-cc kt-i-phone"} -->
<p class="kt-cc kt-i-phone"><small>Telefon</small><br><a href="tel:+90XXXXXXXXXX">[0 5XX XXX XX XX]</a></p>
<!-- /wp:paragraph -->

<!-- wp:paragraph {"className": "kt-cc kt-i-chat"} -->
<p class="kt-cc kt-i-chat"><small>WhatsApp</small><br><a href="https://wa.me/90XXXXXXXXXX">Mesaj gönderin</a></p>
<!-- /wp:paragraph -->

<!-- wp:paragraph {"className": "kt-cc kt-i-mail"} -->
<p class="kt-cc kt-i-mail"><small>E-posta</small><br><a href="mailto:ornek@firma.com">[ornek@firma.com]</a></p>
<!-- /wp:paragraph --></div>
<!-- /wp:column -->

<!-- wp:column -->
<div class="wp-block-column"><!-- wp:group {"className": "kt-form", "layout": {"type": "default"}} -->
<div class="wp-block-group kt-form"><!-- wp:heading {"level": 3} -->
<h3 class="wp-block-heading">Keşif talebi</h3>
<!-- /wp:heading -->

<!-- wp:shortcode -->
{{form_shortcode}}
<!-- /wp:shortcode --></div>
<!-- /wp:group --></div>
<!-- /wp:column --></div>
<!-- /wp:columns --></div>
<!-- /wp:group -->
```

## 9. After the build — the map (done by the owner, by hand)
WordPress removes `<iframe>` from content written by tools, so the real Google map is pasted by hand:
1. Google Maps → find the business → **Paylaş** → **Harita yerleştir** → **HTML'yi kopyala**.
2. WordPress → Sayfalar → Anasayfa → Düzenle → in "Hizmet bölgesi", select the map card (Özel HTML block) → replace its code with the copied `<iframe …>` → **Güncelle**.
The CSS already gives the iframe rounded corners and a 4:3 shape (`.kt-map-embed iframe`).
