# Decisions log

Settled decisions. Append new ones; don't reopen without Sven.

## 2026-10-05
- App name **Stam**; owner **Computer Rabbis LLC**; private, proprietary code.
- **Free** to users; development to be funded later by donors and sponsorships.
- **Rabbinic backing** is in place.
- **Scope:** any STaM the user can access — mezuzos, megillos, open sefer Torah sections, and tefillin parshiyos when already open.
- **All ksav styles** supported; the app identifies the style from the image and shows it to the user.
- **Results** cover pasul issues in the writing and klaf, plus a hiddur/quality assessment (uniformity, symmetry, proportions, etc.).
- **Rules** are compiled from published sources (OU, OK, sofer guides, poskim) rather than written from scratch.
- **Training images:** gathered online, plus own samples as needed.
- **Languages:** English, Hebrew and Yiddish, user-selectable.
- **Sofer referral:** deferred.
- **Repo:** private GitHub repo `Wbbdlr/stam`.
- **Order:** analysis first, tested in alpha builds of the app installed on our own iPhones and Androids. Must ship to the App Store and Google Play; users are not tech-savvy.

## Proposed, awaiting confirmation
- Three-tier result wording (pasul / shailah / no visible problems found) — rav to approve.
- Stack: Expo + ONNX Runtime; Python for analysis R&D (see PLAN.md).
