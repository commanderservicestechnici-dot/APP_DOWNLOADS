# HANDOFF — APP_DOWNLOADS

Aktualizované: 2026-10-07

## Účel
Verejný distribučný repozitár pre interné Commander APK. Zdrojové aplikácie môžu zostať privátne; telefóny sťahujú APK z verejného release `technici`.

## Kľúčové workflow
- `.github/workflows/sync-technici.yml` — synchronizácia APK.
- `.github/workflows/cleanup-actions.yml` — centrálne čistenie GitHub Actions runov.

## Synchronizácia APK
`Sync technician APKs`:
- automaticky približne každých 5 minút,
- okamžite cez `repository_dispatch` event `sync-technici` zo zdrojových repozitárov,
- dá sa spustiť ručne,
- pri jednej chybnej/neprístupnej aplikácii ostatné pokračujú,
- prepíše asset s rovnakým názvom, takže URL zostáva stabilná.

## Stabilné verejné linky
- Práca Technikov: `https://github.com/commanderservicestechnici-dot/APP_DOWNLOADS/releases/download/technici/Praca-Technikov.apk`
- RAI: `https://github.com/commanderservicestechnici-dot/APP_DOWNLOADS/releases/download/technici/RAI.apk`
- Datacho Technik: `https://github.com/commanderservicestechnici-dot/APP_DOWNLOADS/releases/download/technici/Datacho-Technik.apk`
- Aktivácia SIM: `https://github.com/commanderservicestechnici-dot/APP_DOWNLOADS/releases/download/technici/Aktivacia-SIM.apk`
- CMD Obchod: `https://github.com/commanderservicestechnici-dot/APP_DOWNLOADS/releases/download/technici/CMD-Obchod.apk`
- Commander Apps: `https://github.com/commanderservicestechnici-dot/APP_DOWNLOADS/releases/download/technici/Commander-Apps.apk`
- Bungi Darts: `https://github.com/commanderservicestechnici-dot/APP_DOWNLOADS/releases/download/technici/Bungi-Darts.apk`
- Nezabudni: `https://github.com/commanderservicestechnici-dot/APP_DOWNLOADS/releases/download/technici/Nezabudni.apk`

## Zdrojové repozitáre
Synchronizované:
- Praca_Technikov
- Rai
- Datacho
- Aktivacia_Sim
- Podporovane_vozidla
- ALL_APP
- Bungi-Darts-Android
- Nezabudni-Zoznam

Zámerne mimo distribučnej synchronizácie:
- Bungi-Darts-OLD_Android
- Py-aplikacie

## Secrets
Hodnoty tajomstiev nikdy nepísať do repo ani HANDOFF.
- `SOURCE_REPOS_TOKEN` — čítanie privátnych source repo.
- `ACTIONS_CLEANUP_TOKEN` — Actions Read/Write pre centrálne čistenie.

## Cleanup Actions
Používateľ nasadil `cleanup-actions.yml` a prvé čistenie úspešne prešlo.
Pravidlo:
- v každom nastavenom repozitári ponechať 3 najnovšie úspešné runy,
- ostatné ukončené runy odstrániť,
- queued/in_progress nemažú sa,
- automaticky raz denne podľa cron vo workflow,
- ručne cez Actions → Cleanup old Actions runs → Run workflow.

## Dôležité pravidlá
- Release tag `technici` a stabilné názvy APK nemeníť bez úpravy Google Sheetu/aplikácií.
- Ručne nahraté cudzie utility v release nemaž pri bežnej sync úprave.
- Jedna nedostupná app nesmie zablokovať ostatné.
- Pri pridaní novej app doplniť source repo, output názov, release upload a README/HANDOFF.


## Priame spustenie zo source repo
Workflow `sync-technici.yml` prijíma `repository_dispatch` s typom `sync-technici`.
Zdrojová aplikácia môže po úspešnom release poslať dispatch a tým spustiť verejnú synchronizáciu hneď; 5-minútový cron zostáva ako záloha.

## Aktualizácie aplikácie Práca Technikov 1.10.9
- Workflow synchronizuje `Praca-Technikov.apk` aj `Praca-Technikov-version.txt` do verejného release `technici`.
- Súbor verzie vzniká iba po úspešnom stiahnutí APK a obsahuje hodnotu z názvu vydaného source release `latest`.
- Aplikácia kontroluje verziu z verejného súboru po spustení/obnovení; prípadne používa `ALL_APP` ako zálohu.
