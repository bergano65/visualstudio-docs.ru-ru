---
title: Размер файла журнала для нагрузочных тестов
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, logging
ms.assetid: 417059bf-37ae-4e7a-b9b0-29bd71f1414f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.openlocfilehash: 5b685681444e501ef05b76bea22d2152c3296908
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54973685"
---
# <a name="how-to-specify-the-maximum-size-for-the-log-file-for-load-tests"></a>Как выполнить Указание максимального размера файла журнала для нагрузочных тестов

По умолчанию максимальный размер файла журнала, используемого для нагрузочных тестов, установлен равным 20 МБ. Это значение можно изменить с помощью файла конфигурации, связанного со службой контроллера.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-maximum-log-file-size-for-load-test"></a>Указание максимального размера файла журнала для нагрузочного теста

1.  Откройте XML-файл конфигурации *QTCcontroller.exe.config*, расположенный в *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTCcontroller.exe.config*.

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

- [Изменение параметров ведения журнала для нагрузочного теста](../test/modify-load-test-logging-settings.md)
- [Настройка портов для контроллеров и агентов тестирования](../test/configure-ports-for-test-controllers-and-test-agents.md)