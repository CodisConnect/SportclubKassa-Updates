# SportclubKassa Updates

Publieke repository voor releasebestanden van SportclubKassa.

Broncode en gevoelige configuratie horen niet in deze repository.

## Update-architectuur

De POS leest altijd het rootbestand `manifest.json`.

De binaire updatepakketten worden gepubliceerd als **GitHub Release assets**, niet als gewone repositorybestanden. Dit vermijdt de uploadlimiet van de webinterface voor grote bestanden.

### Conventie per versie

Voor versie `0.5.1`:

- GitHub Release tag: `v0.5.1`
- Release asset: `SportclubKassa-0.5.1.zip`
- Package URL: `https://github.com/CodisConnect/SportclubKassa-Updates/releases/download/v0.5.1/SportclubKassa-0.5.1.zip`
- Manifest URL voor de POS: `https://raw.githubusercontent.com/CodisConnect/SportclubKassa-Updates/main/manifest.json`

### Publicatievolgorde

1. Bouw de release met `Installer/Build-Release.ps1` in de bronrepository.
2. Maak in deze repository een GitHub Release aan met tag `v<versie>`.
3. Upload `SportclubKassa-<versie>.zip` als release asset.
4. Controleer dat de release-asset bereikbaar is.
5. Vervang pas daarna het rootbestand `manifest.json` door het gegenereerde manifest.

Publiceer het manifest altijd als laatste. Zo krijgt een POS nooit een update aangeboden waarvan het ZIP-bestand nog niet beschikbaar is.
