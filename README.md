Lista minimale di debloat per Samsung Galaxy A52S 5G con One UI 4.1 (versione italiana).

Quasi tutti i produttori di smartphone preinstallano sui dispositivi delle app, spesso inutili, che non possono essere disinstallate come le normali app. Inoltre, alcune di queste hanno dei permessi molto "larghi" (ad esempio la possibilità di ottenere la lista delle app installate sul dispositivo) e scambiano periodicamente dei dati in background, all'insaputa dell'utente, ponendo un potenziale rischio per la privacy. Fortunatamente è possibile rimuovere la maggior parte di queste app con l'ausilio di un PC e senza la necessità di fare il root del dispositivo. Gli step necessari sono illustrati nella sezione sottostante.

Tramite l'app gratuita e open source [PCAPdroid](https://play.google.com/store/apps/details?id=com.emanuelef.remote_capture) è possibile monitorare le connessioni effettuate dalle varie app per rilevare le connessioni effettuate in background, quando l'app non è in uso.

<a href="https://f-droid.org/packages/com.emanuelef.remote_capture">
    <img src="https://fdroid.gitlab.io/artwork/badge/get-it-on.png"
    alt="Get it on F-Droid"
    height="80">
</a> <a href='https://play.google.com/store/apps/details?id=com.emanuelef.remote_capture'><img height="80" alt='Get it on Google Play' src='https://play.google.com/intl/en_us/badges/static/images/badges/en_badge_web_generic.png'/></a>


## Dati in background

Le seguenti app stock scambiano dati in background, ovvero quando l'app non è utilizzata dall'utente.

Con qualche eccezione, non è possibile determinare con sicurezza quali app inviano dati personali e quali dati interni. Per preservare la privacy, una buona strategia è di analizzare i permessi dell'app (è possibile far questo [comodamente da PCAPdroid](https://emanuele-f.github.io/PCAPdroid/images/app_details.jpg)) ed eliminare tutto ciò che non è strettamente necessario, con ulteriori piccoli benefici su prestazioni, batteria e memoria.

```
Nome app             - Nome package                               - Domini contattati
---------------------------------------------------------------------------------------------------------------------------
Aggiornamento config - com.samsung.android.sdm.config             - poll.gras.samsungdm.com
AppCloud             - com.aura.oobe.samsung.gl                   - crashlyticsreports*, *gogoleapis.com, *isappcloud.com
Archivio             - com.sec.android.app.myfiles                - vas.samsungapps.com
Camera               - com.sec.android.app.camera                 - vas.samsungapps.com
Complemento de Il t..- com.microsoft.appmanager                   - *microsoft.com
Drive                - com.google.android.apps.docs               - *googleapis.com
Duo                  - com.google.android.apps.tachyon            - instantmessaging-pa.googleapis.com
Galleria             - com.sec.android.gallery3d                  - vas.samsungapps.com, clients4.google.com
Game Booster         - com.samsung.android.game.gametools         - vas.samsungapps.com
Google               - com.google.android.googlequicksearchbox    - geller-pa.googleaps.com, www.google.com
Google TV            - com.google.android.videos                  - *googleapis.com
Impostaz. utente     - com.android.systemui                       - vas.samsungapps.com
Messaggi             - com.google.android.apps.messaging          - www.gstatic.com, growth-pa.gogoleapis.com
Pannelli Tag Edge    - com.samsung.android.app.cocktailbarservice - vas.samsungapps.com
Quick Share          - com.samsung.android.app.sharelive          - capi.samsungcloud.com
Samsung Notes        - com.samsung.android.app.notes              - api.samsungcloud.com
Samung O             - com.samsung.android.app.spage              - sdk.pushmessage.samsung.com
SmartThings          - com.samsung.android.oneconnect             - api.smartthings.com, api.launchdarkly.com
Tastiera Samsung     - com.samsung.android.honeyboard             - *spotify.com
Telefono             - com.samsung.android.dialer                 - vas.samsungapps.com
```


## Rimuovere bloatware

**Attenzione**: rimuovere app di sistema potrebbe generare crash e arresti anomali. L'autore non si assume la responsabilità per eventuali malfunzionamenti. In caso di problemi, provare a reinstallare un'app come indicato sotto o in estremis effettuare un factory reset

Per fare il debloat su Windows seguire i seguenti passaggi:

1. Scaricare e scompattare i [command line tools](https://developer.android.com/studio#command-tools) per Android
2. Sul cell, abilitare la modalità sviluppatore (fare tap più volte su versione build in informazioni software)
3. In opzioni sviluppatore, abilitare il debug USB
4. Collegare il cell al pc tramite cavo USB
5. Aprire una [finestra di terminale dentro la cartella](https://www.easypc.altervista.org/guide/come-aprire-il-prompt-dei-comandi-da-una-cartella-specifica) dei command line tools precedentemente scaricata, eseguire `adb shell` e copiare ed incollare i seguenti comandi (è possibili copiare e incollare tutto in una volta, le righe con cancelletto sono commenti e vengono ignorati)

```bash
# creare i seguenti alias per accorciare le operazioni successive
alias drop="pm uninstall -k --user 0"
alias restore="cmd package install-existing"

# bixby
drop com.samsung.android.app.settings.bixby
drop com.samsung.android.bixby.agent
drop com.samsung.systemui.bixby2
drop com.samsung.android.bixbyvision.framework
drop com.samsung.android.bixby.wakeup
drop com.samsung.android.bixby.service

# facebook
drop com.facebook.services
drop com.facebook.system
drop com.facebook.appmanager

# game launcher
drop com.samsung.android.game.gametools
drop com.samsung.android.game.gos
drop com.samsung.android.game.gamehome

# ar emoji
drop com.samsung.android.aremoji
drop com.samsung.android.aremojieditor
drop com.samsung.android.arzone

# health
drop com.samsung.android.service.health
drop com.sec.android.app.shealth

# samsung members
drop com.samsung.android.voc

# app cloud
drop com.aura.oobe.samsung.gl

# app manager
drop com.microsoft.appmanager

# galaxy store
drop com.sec.android.app.samsungapps

# global goals
drop com.samsung.sree

# samsung o
drop com.samsung.android.app.spage

# samsung customization service
drop com.samsung.android.rubin.app

# samsung tips
drop com.samsung.android.app.tips

# pannelli tag edge
drop com.samsung.android.app.cocktailbarservice

# quick share
drop com.samsung.android.app.sharelive

# smart things
drop com.samsung.android.oneconnect

# upday (news)
drop de.axelspringer.yana.zeropage

# google duo
drop com.google.android.apps.tachyon

# altro
drop com.samsung.android.server.wifi.mobilewips
drop com.google.android.videos
```

Dopo aver fatto il debloat, riavviare il cell e testare le varie funzioni di sistema per assicurarsi che non ci siano problemi. In contemporanea, eseguire `adb logcat *:E` per rilevare eventuali crash latenti.

Per reinstallare un pacchetto precedentemente disinstallato è sufficiente eseguire `restore` seguito dal nome del pacchetto (e.g. `restore com.sec.android.app.sbrowser`). Potrebbe non esser possibile reinstallare alcuni pacchetti. In tal caso, un factory reset riporta il cell al suo stato originale.


## App non rimosse

Le seguenti app non sono rimosse per i motivi indicati o, dove non indicato, per preferenze personali.

- App di utilità: Galleria, Archivio, Camera, Messaggi, Tastiera Samsung, Telefono, Samsung Notes
- Galaxy wearable
- Smart switch - passaggio dati su nuovo cell
- Samsung pay
- SCPM Client (`com.samsung.android.sm.policy`) - servizio di ottimizzazione batteria
- Galaxy themes
- Game Booster - l'app non può essere rimossa, in quanto viene immediatamente reinstallata dal sistema
- Drive
