# Research findings

Condensed so it never has to be re-researched. Add new findings at the end with a source link.

## Existing checking software (as of 2026-10)
- **Vaad Mishmeres STaM** built the first computer check in the 1980s: scan, compare against the correct text, report missing/extra/unrecognized letters. Needs a flatbed scanner. [HaSOFER](https://store.hasofer.com/halacha/computer-check-stam/)
- When it launched, gedolim set three conditions: only for extra/missing/swapped letters; only in addition to a qualified sofer; only run by an organization expert in hilchos STaM. [Ami Magazine](https://amimagazine.org/2024/08/13/the-questionable-kashrus-of-countless-sifrei-torah/)
- A **second-generation program** also judges letter shapes and touching letters; sold to ~1,500–2,000 people; ~80% of STaM over 30 years checked with it. (same source)
- **Known failure mode:** a missing letter gets flagged as "touching letters"; the reviewer clears it and misses the pesul. Our UI must never let a "touching" flag hide a text-check failure. (same source)
- Scanner dirt or bad optics can create false cracks/touching flags; most structural letter flaws are missed by the older software. [HaSOFER](https://store.hasofer.com/halacha/computer-check-stam/)
- **OU/STAMP mezuzah program:** two checkers, rabbonim, checkers again, then an AI-powered scan. [Jewish Link](https://jewishlink.news/ou-kosher-kicks-off-initiative-to-oversee-kashrut-and-authenticity-of-mezuzahs/)

## Consumer apps
- **Mezuzah Guide App** (2013): sends a photo to human sofrim at Machon Stam; no automatic check. [Jewish Press](https://jewishpress.com/indepth/columns/america-rabbi-shmuley-boteach/the-art-of-the-scribe/2013/10/22/2)
- **Kidron** (iOS, for sofrim): reads the parsha aloud for manual letter-by-letter checking. [App Store](https://apps.apple.com/br/app/id1620707865)
- **No free, automatic, on-phone STaM checker found.** Hebrew-only Israeli apps are less indexed; recheck before launch.

## Market facts
- Checking costs ~$10 per mezuzah and ~$100 per pair of tefillin in the US; 10 shekels per mezuzah in an Ashdod campaign. Barrier is hassle and access more than price. [Torah Chaim Dallas](https://www.toraschaimdallas.org/expert-sofer-visiting-dallas/), [Arutz Sheva](https://www.israelnationalnews.com/news/433253)
- Ashdod campaign found many home mezuzos with erased words and letters peeled off from heat and moisture — damage a photo check catches well. (Arutz Sheva)
- Folding a mezuzah causes cracks in letters — capture guidance must warn users. [Chabad.org](https://www.chabad.org/225742)

## What a photo can't show
- Lishma (OU: impossible to see) [OU Kosher](https://oukosher.org/mezuzah/); kashrus of klaf and ink; writing in order (corrections out of order make a mezuzah pasul). [Chabad.org](https://www.chabad.org/225742)

## Ksav styles
- Four styles in standard use, all fully kosher: Beis Yosef, Arizal, Vellish (Sephardi), Alter Rebbe (Chabad). [HaSOFER](https://store.hasofer.com/halacha/styles-of-ktav-in-stam/)
- Beis Yosef vs Arizal differ mainly in alef, vav, ayin, tzadi and shin: reversed yud of the tzadi; vav-shaped left part of shin, tes and ayin; protruding left foot of the alef. [Shulchan Aruch Harav](https://shulchanaruchharav.com/?p=19758), [EPHE thesis](https://www.ephe.psl.eu/avis-de-soutenance-doctorat-mark-farnadi-jerusalmi)
- Tagin: three on ג ז ט נ ע צ ש; one on ב ד ה ח י ק. [Wikipedia](https://en.wikipedia.org/wiki/Ktav_Stam)

## Data and models
- No public dataset of STaM letters with pesulim labeled was found. Must build our own.
- Related: Torah-scroll letter-decoration dataset (KIT, 2025, ~90% recognition) [SciTePress](https://scitepress.org/PublishedPapers/2025/131738); modern handwritten Hebrew letters, ~5k samples (HHD) [Hugging Face](https://hf.co/datasets/sivan22/hhd).
- High letter accuracy on a Jewish printed script (~99.8%) took >3M labeled letters — indicates the data scale for fine letter-shape judgments. [Papers with Code](https://cs.paperswithcode.com/paper/auto-ml-deep-learning-for-rashi-scripts-ocr)
- Text check, touching/broken detection and hiddur uniformity need far less labeled data: letter recognition + fixed reference text + image geometry + comparing the klaf against itself.

## Licensing notes
- Ultralytics YOLO is AGPL-3.0 — avoid. Permissive options: YOLOX (Apache-2.0), OpenCV (Apache-2.0), ONNX Runtime (MIT), Expo and react-native-vision-camera (MIT). Verify each before adding.
