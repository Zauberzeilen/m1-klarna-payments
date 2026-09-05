# Klarna M2 4.15.0 Referenz

Dieser Ordner ist die Ablage für die offiziellen Quellen von `klarna/m2-klarna:4.15.0` von https://commercemarketplace.adobe.com/klarna-m2-klarna.html

## Status
- Branch: `modernisierung/magento-2-port` (Basis M1 v4.4.5)
- Ziel: Diff M1 (`app/code/community/Klarna/`) vs. M2 4.15.0 für Modernisierungs-Plan

## Befüllung (nach Adobe Login)

### Variante A: via Composer (empfohlen, benötigt repo.magento.com Keys)
```bash
# auth.json aus Marketplace Keys erzeugen:
composer config --global http-basic.repo.magento.com <public_key> <private_key>

# In temp dir laden:
composer require klarna/m2-klarna:4.15.0 --no-install --working-dir=C:\Temp\klarna-src
# oder wenn schon M2 Projekt vorhanden:
composer show klarna/m2-klarna --all
```

Danach Inhalt von `C:\Temp\klarna-src\vendor\klarna\` hierher kopieren:
```powershell
Copy-Item -Recurse -Force C:\Temp\klarna-src\vendor\klarna\* D:\Firma\REGAflex\klarna-m1\reference\klarna-m2-4.15.0\
```

### Variante B: Direkt aus bestehendem Shop
```powershell
Copy-Item -Recurse -Force <magento-root>\vendor\klarna\* .\reference\klarna-m2-4.15.0\
```

## Erwartete Struktur nach Befüllung
```
klarna-m2-4.15.0/
  m2-klarna/              # Metapackage
  module-core/
  module-kp/
  module-kp-graph-ql/
  module-onsitemessaging/
  module-ordermanagement/
  ...
```

## Hinweise
- Nicht zu verwechseln mit `D:\Firma\REGAflex\klarna-m2` (= mage2pro/klarna 0.5.2, proprietär)
- Lizenz M2 4.15.0: Apache-2.0 (lt. Marketplace)
- Nach Befüllung: `git add reference/klarna-m2-4.15.0` oder `.gitignore` anpassen falls vendor groß

## Nächster Schritt
Sobald Ordner befüllt ist, Bescheid geben -> dann erstelle ich Struktur-Diff + Migrations-Plan M1->M2 API.
