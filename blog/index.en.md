---
title: "JetPrinter Interface: a Qt control UI for ink printing"
description: "A Qt desktop application for operating an ink printing station, coordinating printer and PLC views, configuring production programs, and reviewing reports."
date: 2026-11-19
lang: en
tags:
  - Qt
  - C++
  - JetPrinter
  - LEIBINGER JET3
  - PLC
  - manufacturing
repo: CodElecCz/jet-printer-interface
featured: true
---

# Project overview

JetPrinterUI is a Qt Widgets desktop application designed for a marking station equipped with a LEIBINGER JET3 industrial continuous inkjet (CIJ) printer. It brings the printer controls and production-station workflow into one interface, with dedicated views for printer operation, PLC state, production programs, settings, and reports. The project is written in C++ and the Qt project file enables the Core, Gui, Widgets, SQL, Network, and XML modules.

The main window builds its tabs from configuration, allowing the installation to expose the views needed by its operators. Printer and PLC communication are handled by the project libraries under `Lib/`; the UI provides a working view of station activity rather than requiring operators to work directly with those protocol interfaces.

# Printer and station workflow

The printer view presents machine and print states and provides controls for power, starting or stopping a print, and opening or closing the nozzle. On the LEIBINGER JET3, these nozzle controls correspond to its automated nozzle seal system, which helps prevent ink from drying during idle states. The PLC view monitors the station sequence, including loading a part, checking sensors, preparing the print, waiting for the operator, and completing the cycle. Statuses such as a sensor error or a request to remove the part are shown in the interface.

Production programs are configured with a job file and options for inserts, sensors, and the start button. The sample `settings.ini` contains six short- and long-part program variants, each linked to a job under `LJ3/Jobs/`. This keeps the selected job and station setup together for each product variant.

# Reports and configuration

The reports view queries the configured production history and lets an operator browse results by date and label. Application and station settings are stored in INI files, while PLC configuration is supplied in `plc.xml`. The repository includes sample configuration, job files, and prebuilt Windows binaries; adapt the machine-specific settings before using it on a production station.

# Screenshots

The following screenshots show the application interface included in the repository.

![JetPrinterUI screenshot 1](../screenshots/JetPrinter01.png)

![JetPrinterUI screenshot 2](../screenshots/JetPrinter02.png)

![JetPrinterUI screenshot 3](../screenshots/JetPrinter03.png)

![JetPrinterUI screenshot 4](../screenshots/JetPrinter04.png)

![JetPrinterUI screenshot 5](../screenshots/JetPrinter05.png)

![JetPrinterUI screenshot 6](../screenshots/JetPrinter06.png)

# Project structure

- `jetprinterview.*` contains the ink-printer controls and status display.
- `plcview.*` and `plcviewmodel.*` provide the PLC station view.
- `programview.*` handles product-specific jobs and station options.
- `reportview.*` displays production history.
- `Lib/` contains the printer, OMC8000, and shared-node libraries.
- `LJ3/Jobs/` contains the sample printer job files.

Source code: [CodElecCz/jet-printer-interface](https://github.com/CodElecCz/jet-printer-interface).
