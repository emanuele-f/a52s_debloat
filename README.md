Lista minimale di debloat per Samsung Galaxy A52S 5G con One UI 4.1 (versione italiana). Rimuovi le app inutili, alcune delle quali scambiano dati in background, aumentando la tua privacy.

E' possibile monitorare lo scambio dati in background tramite l'app gratuita e open source [PCAPdroid](https://play.google.com/store/apps/details?id=com.emanuelef.remote_capture).


<a href="https://f-droid.org/packages/com.emanuelef.remote_capture">
    <img src="https://fdroid.gitlab.io/artwork/badge/get-it-on.png"
    alt="Get it on F-Droid"
    height="80">
</a> <a href='https://play.google.com/store/apps/details?id=com.emanuelef.remote_capture'><img height="80" alt='Get it on Google Play' src='https://play.google.com/intl/en_us/badges/static/images/badges/en_badge_web_generic.png'/></a>


## App non rimosse

- Galaxy wearable
- Smart switch - passaggio dati su nuovo cell
- Samsung pay
- SCPM Client (`com.samsung.android.sm.policy`) - servizio di ottimizzazione batteria
- Galaxy themes

## Rimuovere bloatware

Per fare il debloat su Windows seguire i seguenti passaggi:

1. Scaricare e scompattare i [command line tools](https://developer.android.com/studio#command-tools) per Android
2. Sul cell, abilitare la modalità sviluppatore (fare tap più volte su versione build in informazioni software)
3. In opzioni sviluppatore, abilitare il debug USB
4. Collegare il cell al pc tramite cavo USB
5. Aprire un terminale e dalla cartella dei command line tools precedentemente scaricata eseguire `adb shell` e lanciare i comandi sotto

```bash
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

# upday (news)
drop de.axelspringer.yana.zeropage

# altro
drop com.samsung.android.server.wifi.mobilewips
```

Per reinstallare un pacchetto precedentemente disinstallato è sufficiente eseguire `restore` seguito dal nome del pacchetto (e.g. `restore com.sec.android.app.sbrowser`)
