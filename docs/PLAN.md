# Stam — product and technical plan

Owner: Computer Rabbis LLC · Status: Phase 0 · Updated 2026-10-05

## Goal
A free app. The user photographs any STaM they can access (mezuzah, megillah, an open sefer Torah column, tefillin parshiyos already opened by a sofer). The phone analyzes it on-device and reports problems and quality. Funded later by donors and sponsorships.

## Result format
1. **Pasul** — definite visible pesulim, each marked on the image.
2. **Shailah** — borderline findings to show a sofer or rav, marked on the image.
3. **No visible problems found** — with a short note that invisible factors (lishma, klaf and ink, written in order) can't be checked from a photo.
4. **Hiddur score (1–100)** with a breakdown (see checks below).

Final wording of all results is approved by the rav.

## What the app detects automatically
- **Item and location:** mezuzah, megillah, or which passage of the Torah is in the photo (searched against the full text).
- **Ksav style:** Beis Yosef, Arizal, Chabad (Alter Rebbe), Sephardi (Vellish).

## Checks
- **Text:** missing, extra or swapped letters; missing or extra words; parsha spacing (pesuchos/stumos); layout conventions where relevant.
- **Letters:** touching letters; broken or cracked letters; faded or flaking ink; malformed letters judged against the rules of the detected ksav.
- **Klaf:** holes, tears or stains that touch or obscure letters.
- **Hiddur:** uniformity of each letter across the klaf; proportions against the ksav's norms; stroke quality and symmetry; spacing and alignment to the ruled lines; tagin present and well formed; one consistent ksav; margins.

Classification of every check (pasul / shailah / hiddur) is compiled from published sources into `docs/halacha/RULES.md`.

## Architecture (all on-device)
capture → quality gate (focus, glare, resolution, full coverage) → flatten/dewarp → line and letter segmentation → letter classification + ksav detection → alignment to reference text → defect detectors → hiddur metrics → report.

- **Reference text:** verified STaM text, including the known Ashkenazi/Sephardi/Teimani spelling variants. Source and license to be chosen; rav approves.
- **Models:** trained in Python, exported to ONNX, run with ONNX Runtime on iOS, Android and web.
- **No server needed** for analysis; this keeps the app free to run and private.

## Proposed stack (pending Sven's OK)
- **App:** Expo (React Native, TypeScript), react-native-vision-camera, onnxruntime-react-native, i18n with RTL. iOS builds through EAS Build, so a Mac isn't required.
- **Analysis R&D:** Python, OpenCV, PyTorch → ONNX.
- **Web (later):** same Expo codebase via React Native Web, with onnxruntime-web.

## Phases
- **P0 — Foundations (now):** repo and rules; compile `RULES.md` from published sources (Shulchan Aruch, Mishnah Berurah, Keses HaSofer, Mishnas Sofrim, OU/OK and sofer guides) for the rav's sign-off; choose the reference text; gather sample images (online plus own scans); define the labeling scheme.
- **P1 — Analysis prototype (desktop, Python):** mezuzah only, Beis Yosef and Arizal. Text check, touching/broken letters, hiddur metrics. Measure against sofer-checked samples. **Gate:** missing/extra letter detection must reach the agreed accuracy before app work starts.
- **P2 — Mobile MVP:** guided capture, on-device models, results screens, three languages.
- **P3 — Expand:** all four ksav styles, megillah, Torah sections, tefillin parshiyos, letter-shape (shailah) model.
- **P4 — Later:** sofer referral, donations and sponsorships, web version, app-store release.

## Open items
- Apple Developer account in the LLC's name (needs a D-U-N-S number); Google Play developer account.
- Rav's sign-off process and result wording.
- Licensing of images gathered online.
- Accuracy targets for the P1 gate.
