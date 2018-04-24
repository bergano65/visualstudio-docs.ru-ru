---
title: Свойства отладчика Android (C++) | Документы Майкрософт
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
author: corob
ms.author: mblome
manager: douge
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 7d18125c6666a8eb68becd828da36ecdab077507
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
