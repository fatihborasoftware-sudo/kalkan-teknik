# 3 — Build prompt

Start a **new chat** in Claude, attach [`../Kalkan-build-kit.md`](../Kalkan-build-kit.md), fill in your details below and send. Claude builds the whole site through the connector; you approve the plan once and watch on **Watch Me Live**.

Yeni bir sohbet aç, [`Kalkan-build-kit.md`](../Kalkan-build-kit.md) dosyasını ekle, aşağıdaki bilgileri doldur ve gönder.

```
Build the one-page website in the attached file Kalkan-build-kit.md on my WordPress site through my connector (FB AI Engine – Claude Connector). The kit has everything: the build plan, images, theme settings, CSS, form, footer, menu and the page as ready block markup. I already approved the mockup.

My site address: [SITE ADDRESS, e.g. https://example.com]

My business details (replace the kit's placeholders and the name "Kalkan Teknik" with these; leave anything I left empty as a placeholder):
- Business name: [Kalkan Teknik]
- Phone: [0 5XX XXX XX XX]
- WhatsApp number (with country code, digits only): [905XXXXXXXXX]
- E-mail: [ornek@firma.com]
- City: [Şehir]
- Districts we serve: [İlçe 1, İlçe 2, İlçe 3]
- Address: [Açık adres]
- Opening hours: [Hafta içi 09:00–19:00 · Cumartesi 09:00–17:00]

The site is fresh: only the connector is installed. Work in this order and keep me posted live:

0. task_status at the start with all steps below (and a short spoken "brief"), at every step, and with done=true at the end.
1. content_list to find the ids of "Hello world!" and "Sample Page", then build_plan_submit with kit section 1 (those ids in "trash"). Tell me it is waiting, wait until I approve it, then check build_plan_status.
2. plugins_install wpvivid-backuprestore → backup_create → wait until backup_status shows a fresh backup.
3. theme_install kadence.
4. plugins_install contact-form-7.
5. content_trash the two ids from step 1.
6. media_upload every image in kit section 2 (url + alt). Keep a list of key → id + url. (Skip "logo" if my business name is not Kalkan Teknik.)
7. custom_css_set with kit section 4 (mode replace). Then theme_settings_get, and set the Kadence palette, fonts, page layout, logo, header, header button and footer with theme_settings_set (kit section 3), keeping Kadence's exact structures. If a header or footer part cannot be set through theme settings, link your browser first (the connector tells you how) and use the Customizer.
8. form_create with kit section 5 and keep the shortcode.
9. The page: content_create_draft (post_type page, title "Anasayfa", content exactly as kit section 8, with {{site}}, {{img:KEY}}, {{form_shortcode}} and my business details filled in), then content_publish.
10. menu_set (kit section 7, primary + mobile). site_settings: front page = Anasayfa, title = my business name, tagline "Elektrik, güvenlik ve network teknik servisi". widgets_set footer1–footer4 (kit section 6, same replacements).
11. site_check. Fix every problem it finds, then run it again.
12. Finish with task_status done=true and a brief: what was built, the link, and what is left for me: the Google map (kit section 9) and any placeholder I did not fill in.

Rules: follow the kit's markup and texts exactly. Don't add <style> or <script> tags. Ask me before anything outside the plan. If a step fails, tell me the exact error and the step number before trying something else.
```
