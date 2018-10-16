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
ms.openlocfilehash: be240ed2cea05194d51040fd29a17de9a4472fc9
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232648"
---
# <a name="android-debugger-properties"></a>Свойства отладчика Android

Свойство. | Описание: | Варианты
--- | ---| ---
Тип отладчика | Указывает тип кода для отладки. | **Только машинный код**<br>**Только Java**<br>
Целевой объект отладки | Указывает эмулятор или устройство для использования при отладке. Если эмуляторы не запущены, используйте "Диспетчер виртуальных устройств Android (AVD)" для запуска устройства.
Пакет для запуска | Указывает расположение *APK-файла*, подлежащего отладке. Выберите этот параметр, чтобы указать, что при отладке приложения следует запускать определенный пакет (APK).
Действие запуска | Действие Android для запуска приложения должно соответствовать использованному в манифесте. Нажмите кнопку "Применить", чтобы извлечь список из файла *AndroidManifest.xml* и динамически заполнить его.
Дополнительные пути поиска символов | Дополнительный путь поиска для символов отладки.
Дополнительные пути поиска исходных файлов Java | Дополнительные пути поиска для исходных файлов Java (применяется исключительно для типа отладчика "Только Java").
