# toscribexl-build-assets

Geprüfte Bau-Artefakte für [ToScribeXL](https://github.com/machine303/toscribexl).
**Kein Quellcode** — nur unveränderliche Binaries, auf die der Bauvorgang mit
hart gepinnter SHA-256 zugreift.

## Warum es dieses Repo gibt

Der Windows-Bauweg bezog FFmpeg bisher von [BtbN/FFmpeg-Builds](https://github.com/BtbN/FFmpeg-Builds).
Dort hält jeder Autobuild-Release nur ein rollierendes Fenster von rund zehn Tagen —
der gepinnte Release `autobuild-2026-08-09-13-03` war am 28.08.2026 upstream nicht
mehr erreichbar (404 auf Zip **und** `checksums.sha256`), was Bauvorgang und CI zum
Stehen brachte.

Gespiegelt werden deshalb **genau die Bytes, die im abgenommenen Windows-Build
stecken** — kein neuer Bau, keine andere Fassung.

## Releases

### `ffmpeg-btbn-2026-08-09-13-03`

| Datei | Zweck |
|---|---|
| `ffmpeg.exe` | Runtime-Binary, wandert ins App-Bundle |
| `ffprobe.exe` | Runtime-Binary, wandert ins App-Bundle |
| `ffmpeg-n8.1.2-34-g9b6c8969e0-win64-lgpl-shared-8.1.zip` | Header + Import-Libs, gegen die PyAV gelinkt wird |

Der Tag benennt die **Herkunft** (den ursprünglichen BtbN-Release), nicht das
Upload-Datum. Er ist unveränderlich: Ein überschriebener Tag würde jeden Pin wertlos
machen, der auf ihn zeigt.

## Lizenz

Die FFmpeg-Binaries sind **LGPL**-konfiguriert (kein `--enable-gpl`, keine externen
Codec-Bibliotheken). Die Weitergabe ist davon gedeckt; dieselben Binaries liegen
ohnehin in jedem ausgelieferten Installer. Attribution und Lizenztexte stehen in
`THIRD_PARTY_LICENSES.md` im Hauptrepo.

Der Inhalt dieses Repos steht unter den Lizenzen der jeweiligen Artefakte, nicht
unter einer eigenen.

## Geplantes Ende

Dieses Repo wird überflüssig, sobald der Windows-Bauweg FFmpeg **aus Quellen** baut —
so wie der macOS-Weg es längst tut (gepinnter Quell-Tarball von ffmpeg.org, der nicht
verfällt). Bis dahin ist der Spiegel die Brücke.
