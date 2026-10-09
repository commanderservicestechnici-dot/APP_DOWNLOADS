# Commander APP downloads

Verejné úložisko APK súborov pre interné aplikácie Commander.

## Stabilné verejné APK odkazy

Release `technici` používa stále rovnaké názvy súborov. Odkazy sa preto nemenia ani po vydaní novej verzie a môžu byť priamo uložené v Google Sheete `ALL_APP`.

- Práca Technikov: `https://github.com/commanderservicestechnici-dot/APP_DOWNLOADS/releases/download/technici/Praca-Technikov.apk`
- Práca Technikov – číslo poslednej vydanej verzie (`*.txt`, automaticky zo source release): `https://github.com/commanderservicestechnici-dot/APP_DOWNLOADS/releases/download/technici/Praca-Technikov-version.txt`
- RAI: `https://github.com/commanderservicestechnici-dot/APP_DOWNLOADS/releases/download/technici/RAI.apk`
- Datacho Technik: `https://github.com/commanderservicestechnici-dot/APP_DOWNLOADS/releases/download/technici/Datacho-Technik.apk`
- Aktivácia SIM: `https://github.com/commanderservicestechnici-dot/APP_DOWNLOADS/releases/download/technici/Aktivacia-SIM.apk`
- CMD Obchod: `https://github.com/commanderservicestechnici-dot/APP_DOWNLOADS/releases/download/technici/CMD-Obchod.apk`
- Commander Apps: `https://github.com/commanderservicestechnici-dot/APP_DOWNLOADS/releases/download/technici/Commander-Apps.apk`
- Bungi Darts: `https://github.com/commanderservicestechnici-dot/APP_DOWNLOADS/releases/download/technici/Bungi-Darts.apk`
- Nezabudni: `https://github.com/commanderservicestechnici-dot/APP_DOWNLOADS/releases/download/technici/Nezabudni.apk`

## Ako synchronizácia funguje

Workflow `Sync technician APKs` beží každých 5 minút a zároveň sa dá spustiť ručne.

Zdrojové aplikácie zostávajú v privátnych repozitároch. Workflow si z nich vezme posledný úspešný APK a nahrá ho do verejného release `technici` v tomto repozitári.

Používané zdroje:

- `Praca_Technikov` – stabilný release `latest`
- `Podporovane_vozidla` – stabilný release `latest`
- `ALL_APP` – stabilný release `latest`
- `Rai` – posledný úspešný artifact z `android.yml`
- `Datacho` – posledný úspešný artifact z `android.yml`
- `Aktivacia_Sim` – posledný úspešný artifact z `android.yml`
- `Bungi-Darts-Android` – APK z posledného úspešného workflow runu
- `Nezabudni-Zoznam` – APK z posledného úspešného workflow runu

Repozitáre `Bungi-Darts-OLD_Android` a `Py-aplikacie` sa zámerne nesynchronizujú.

## SOURCE_REPOS_TOKEN

V repozitári musí byť Actions secret `SOURCE_REPOS_TOKEN`.

Ak je to fine-grained Personal Access Token, musí mať prístup ku všetkým týmto privátnym repozitárom:

- `Praca_Technikov`
- `Rai`
- `Datacho`
- `Aktivacia_Sim`
- `Podporovane_vozidla`
- `ALL_APP`
- `Bungi-Darts-Android`
- `Nezabudni-Zoznam`

Potrebné oprávnenia sú minimálne **Actions: Read** a **Contents: Read**.

Po rozšírení prístupu tokenu stačí spustiť Actions → `Sync technician APKs` → `Run workflow`. Potom už synchronizácia beží automaticky každých 5 minút.
