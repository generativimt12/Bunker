# Bunker Conquest

משחק פעולה תלת־ממדי בגוף ראשון, בעברית, המבוסס על קובץ ה־HTML שהועלה לפרויקט. המשחק ארוז כאפליקציית Android עצמאית באמצעות Capacitor; הלוגיקה והגרפיקה רצות מקומית במכשיר, ללא שרת משחק.

## הפעלה בדפדפן

```bash
npm install
npm run dev
```

## בניית Android מקומית

נדרש Node.js 22, Java 21 ו־Android SDK:

```bash
npm install
npm run build
npx cap add android
npx cap sync android
cd android
./gradlew assembleDebug
```

ה־APK יופיע ב־`android/app/build/outputs/apk/debug/app-debug.apk`.

## קבלת APK דרך GitHub Actions

1. פותחים את לשונית **Actions** במאגר.
2. בוחרים **Build Android APK** ולוחצים **Run workflow** (או ממתינים לריצה האוטומטית לאחר שינוי בקוד).
3. לאחר שהריצה מסתיימת בהצלחה, מורידים את `bunker-conquest-android-debug` מתוך **Artifacts**.
4. מחלצים את קובץ ה־ZIP ומתקינים את `app-debug.apk` במכשיר Android.

זהו APK מסוג **debug** להתקנה ולבדיקה, לא חבילת release חתומה להפצה בחנות.

## מבנה

- `index.html` — המשחק המקורי שהועלה, כולל ממשק בעברית והקוד שלו.
- `vite.config.js` — בנייה עם נתיבים יחסיים שמתאימים ל־Android WebView.
- `capacitor.config.json` — מזהה ושם האפליקציה.
- `.github/workflows/android-apk.yml` — בניית APK אוטומטית.

## הערה

הוספת אריזת Android אינה מבטיחה שכל מכשיר יתמוך באותה רמת ביצועים או באותן יכולות גרפיות. יש לבדוק את המשחק בפועל במכשיר היעד.
