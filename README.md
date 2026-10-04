# Commander APP downloads

Verejné úložisko APK súborov pre interné aplikácie Commander.

## Technici

- Práca Technikov: `https://github.com/commanderservicestechnici-dot/APP_DOWNLOADS/releases/download/technici/Praca-Technikov.apk`
- RAI: `https://github.com/commanderservicestechnici-dot/APP_DOWNLOADS/releases/download/technici/RAI.apk`
- Datacho Technik: `https://github.com/commanderservicestechnici-dot/APP_DOWNLOADS/releases/download/technici/Datacho-Technik.apk`
- Aktivácia SIM: `https://github.com/commanderservicestechnici-dot/APP_DOWNLOADS/releases/download/technici/Aktivacia-SIM.apk`

Release `technici` používa stále rovnaké názvy APK, takže odkazy sa nemenia.

Workflow `Sync technician APKs` každú hodinu vezme APK z posledného úspešného buildu privátnych repozitárov Praca_Technikov, Rai, Datacho a Aktivacia_Sim a nahrá ich do verejného Release `technici`.

## Jednorazové nastavenie

V tomto repozitári musí byť Actions secret `SOURCE_REPOS_TOKEN`. Ideálne použiť fine-grained Personal Access Token s prístupom iba k repozitárom `Praca_Technikov`, `Rai`, `Datacho`, `Aktivacia_Sim` a s oprávnením **Actions: Read** a **Contents: Read**.

Po pridaní secretu spusti Actions -> `Sync technician APKs` -> `Run workflow`. Potom už synchronizácia beží automaticky každú hodinu.
