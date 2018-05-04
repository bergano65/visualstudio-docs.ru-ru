---
title: Размер файла журнала для нагрузочных тестов в Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, logging
ms.assetid: 417059bf-37ae-4e7a-b9b0-29bd71f1414f
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 7faf5402f495eefe64000c67048bcb85c9197388
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-specify-the-maximum-size-for-the-log-file-for-load-tests"></a>Практическое руководство. Указание максимального размера файла журнала для нагрузочных тестов

По умолчанию максимальный размер файла журнала, используемого для нагрузочных тестов, установлен равным 20 МБ. Это значение можно изменить с помощью файла конфигурации, связанного со службой контроллера.

## <a name="specify-the-maximum-log-file-size-for-load-test"></a>Указание максимального размера файла журнала для нагрузочного теста

1.  Откройте XML-файл конфигурации *QTCcontroller.exe.config*, расположенный в %ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTCcontroller.exe.config.

2.  Найдите параметр `<add key="LogSizeLimitInMegs" value="20"/>` в теге `<appSettings>`.

    ```xml
    <appSettings>
        <add key="LogSizeLimitInMegs" value="20"/>
        <add key="AgentConnectionTimeoutInSeconds" value="120"/>
        <add key="AgentSyncTimeoutInSeconds" value="300"/>
        <add key="ControllerServicePort" value="6901"/>
        <add key="ControllerUsersGroup" value="TeamTestControllerUsers"/>
        <add key="ControllerAdminsGroup" value="TeamTestControllerAdmins"/>
        <add key="CreateTraceListener" value="no"/>
      </appSettings>
    ```

3.  Измените `value ="20"` на требуемый максимально разрешенный размер файла журнала.

    > [!NOTE]
    > Введите значение "0", чтобы размер файла журнала ограничивался только объемом свободного места на диске.

## <a name="see-also"></a>См. также

- [Изменение параметров ведения журнала нагрузочного теста](../test/modify-load-test-logging-settings.md)
- [Настройка портов для контроллеров и агентов тестирования](../test/configure-ports-for-test-controllers-and-test-agents.md)