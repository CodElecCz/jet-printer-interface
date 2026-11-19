---
title: "JetPrinter Interface: Qt rozhraní pro inkoustový tisk"
description: "Desktopová aplikace v Qt pro obsluhu inkoustové tiskové stanice, propojení pohledů tiskárny a PLC, nastavení výrobních programů a zobrazení reportů."
date: 2026-11-19
lang: cs
tags:
  - Qt
  - C++
  - JetPrinter
  - LEIBINGER JET3
  - PLC
  - výroba
repo: CodElecCz/jet-printer-interface
featured: true
---

# Přehled projektu

JetPrinterUI je desktopová aplikace v Qt Widgets navržená pro značicí stanici vybavenou průmyslovou kontinuální inkoustovou tiskárnou (CIJ) LEIBINGER JET3. Spojuje ovládání tiskárny a výrobní postup v jednom rozhraní s oddělenými pohledy pro obsluhu tiskárny, stav PLC, výrobní programy, nastavení a reporty. Projekt je napsaný v C++ a soubor Qt projektu zapíná moduly Core, Gui, Widgets, SQL, Network a XML.

Hlavní okno vytváří záložky podle konfigurace, takže instalace může obsluze zpřístupnit potřebné pohledy. Komunikaci s tiskárnou a PLC zajišťují knihovny ve složce `Lib/`; uživatelské rozhraní poskytuje přehled činnosti stanice bez nutnosti pracovat přímo s komunikačními rozhraními.

# Tiskárna a postup stanice

Pohled tiskárny zobrazuje stav zařízení a tisku a nabízí ovládání napájení, spuštění a zastavení tisku i otevření a zavření trysky. U tiskárny LEIBINGER JET3 tato tlačítka ovládají automatický systém těsnění trysky, který v době nečinnosti pomáhá zabránit zasychání inkoustu. Pohled PLC sleduje postup stanice: založení dílu, kontrolu senzorů, přípravu tisku, čekání na obsluhu a dokončení cyklu. Rozhraní zobrazuje také chybový stav senzorů nebo požadavek na odebrání dílu.

Výrobní programy se nastavují pomocí souboru zakázky a voleb pro vložky, senzory a startovací tlačítko. Ukázkový soubor `settings.ini` obsahuje šest variant pro krátké a dlouhé díly; každá je propojena se souborem zakázky ve složce `LJ3/Jobs/`. Nastavení stanice a vybraná zakázka jsou tak uloženy společně pro každou variantu výrobku.

# Reporty a konfigurace

Pohled reportů načítá nakonfigurovanou historii výroby a umožňuje procházet výsledky podle data a označení. Nastavení aplikace a stanice jsou uložena v souborech INI, konfigurace PLC je v `plc.xml`. Repozitář obsahuje ukázkovou konfiguraci, soubory zakázek a předkompilované binární soubory pro Windows; před použitím na výrobní stanici je potřeba upravit nastavení podle konkrétního zařízení.

# Snímky obrazovky

Následující snímky ukazují rozhraní aplikace obsažené v repozitáři.

![Snímek JetPrinterUI 1](../screenshots/JetPrinter01.png)

![Snímek JetPrinterUI 2](../screenshots/JetPrinter02.png)

![Snímek JetPrinterUI 3](../screenshots/JetPrinter03.png)

![Snímek JetPrinterUI 4](../screenshots/JetPrinter04.png)

![Snímek JetPrinterUI 5](../screenshots/JetPrinter05.png)

![Snímek JetPrinterUI 6](../screenshots/JetPrinter06.png)

# Struktura projektu

- `jetprinterview.*` obsahuje ovládání tiskárny a zobrazení jejího stavu.
- `plcview.*` a `plcviewmodel.*` zajišťují pohled na PLC stanice.
- `programview.*` spravuje zakázky a nastavení jednotlivých výrobků.
- `reportview.*` zobrazuje výrobní historii.
- `Lib/` obsahuje knihovny tiskárny, OMC8000 a sdílených uzlů.
- `LJ3/Jobs/` obsahuje ukázkové soubory tiskových zakázek.

Zdrojový kód: [CodElecCz/jet-printer-interface](https://github.com/CodElecCz/jet-printer-interface).
