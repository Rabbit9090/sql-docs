---
description: "SQLInstallTranslator Mapping"
title: "SQLInstallTranslator Mapping | Microsoft Docs"
ms.custom: ""
ms.date: "01/19/2017"
ms.service: sql
ms.reviewer: ""
ms.subservice: connectivity
ms.topic: reference
helpviewer_keywords: 
  - "SQLInstallTranslator function [ODBC], mapping"
  - "mapping deprecated functions [ODBC], SQLInstallTranslator"
ms.assetid: bcd9ba4f-7834-4bc4-876e-c7478998e524
author: David-Engel
ms.author: v-davidengel
---
# SQLInstallTranslator Mapping
When an ODBC *2.x* application calls **SQLInstallTranslator** through an ODBC *3.x* driver, the Driver Manager maps the call to **SQLInstallTranslatorEx**.An application should not call **SQLInstallTranslator** in the ODBC *3.x* Driver Manager with the *lpszInfFile* argument set to a value other than NULL. The ODBC.INF file used in ODBC *2.x* is no longer supported in ODBC *3.x*, even for backward compatibility.
