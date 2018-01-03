---
title: "Свойства отладчика Android (C++) | Документы Майкрософт"
ms.custom: 
ms.date: 10/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
author: corob
ms.author: mblome
manager: ghogen
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.workload: xplat-cplusplus
ms.openlocfilehash: d8caf579aa73a77f3c20162ae775411df551f373
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="android-debugger-properties"></a>Свойства отладчика Android

Свойство. | Описание: | Варианты
--- | ---| ---
Тип отладчика | Указывает тип кода для отладки. | **Только машинный код**<br>**Только Java**<br>
Целевой объект отладки | Указывает эмулятор или устройство для использования при отладке. Если эмуляторы не запущены, используйте "Диспетчер виртуальных устройств Android (AVD)" для запуска устройства.
Пакет для запуска | Указывает расположение APK-файла, подлежащего отладке. Выберите этот параметр, чтобы указать, что при отладке приложения следует запускать определенный пакет (APK).
Действие запуска | Действие Android для запуска приложения должно соответствовать использованному в манифесте. Нажмите кнопку "Применить", чтобы извлечь список из файла AndroidManifest.xml и динамически заполнить его.
Дополнительные пути поиска символов | Дополнительный путь поиска для символов отладки.
Дополнительные пути поиска исходных файлов Java | Дополнительные пути поиска для исходных файлов Java (применяется исключительно для типа отладчика "Только Java").
