---
title: Периоды ожидания для контроллеров тестирования и агентов тестирования
description: Узнайте, как изменить значения времени ожидания для контроллера тестирования и агента тестирования, изменив соответствующие XML-файлы конфигурации.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- agents, configuring
- agetns, timeouts
- controllers, configuring
- controllers, timeouts
ms.assetid: 777d0db5-0073-458a-a2a3-58b1c1f24c60
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 3cca59fc165871e24269723635a1393d2f859178
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879570"
---
# <a name="how-to-specify-timeout-periods-for-test-controllers-and-test-agents"></a>Практическое руководство. Задание периодов ожидания для контроллеров тестирования и агентов тестирования

Для контроллеров и агентов тестирования предусмотрено несколько параметров времени ожидания, которые определяют период времени, в течение которого они должны ожидать ответа друг от друга или от источника данных, прежде чем завершить работу с ошибкой. В некоторых случаях может потребоваться изменить значения времени ожидания в соответствии с потребностями топологии или другими характеристиками среды. Для изменения значений времени ожидания необходимо изменить XML-файл конфигурации, связанный с контроллером или агентом тестирования, как описано в следующих процедурах.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Чтобы изменить различные параметры времени ожидания контроллера или агента тестирования, изменить следующие файлы конфигурации, используя имена и значения разделов, указанные в представленных ниже таблицах.

- Контроллер тестирования: *QTController.exe.config*

    |Имя ключа|Описание|Значение|
    |-|-----------------|-|
    |AgentConnectionTimeoutInSeconds|Период времени (в секундах), в течение которого агент прослушивает запрос, прежде чем подключение считается разорванным.|"n" секунд.|
    |AgentSyncTimeoutInSeconds|Период времени (в секундах) после начала тестового запуска синхронизации, в течение которого все агенты должны ожидать синхронизации, прежде чем прервать запуск.|"n" секунд.|
    |AgentInitializeTimeout|Период времени (в секундах), в течение которого все агенты и их сборщики данных должны ожидать инициализации в начале тестового запуска, прежде чем прервать запуск. Если используются сборщики данных, данное значение должно быть достаточно большим.|"n" секунд. Значение по умолчанию — 120 (две минуты).|
    |AgentCleanupTimeout|Период времени (в секундах), в течение которого все агенты и их сборщики данных должны ожидать очистки, прежде чем завершить тестовый запуск. Если используются сборщики данных, данное значение должно быть достаточно большим.|"n" секунд. Значение по умолчанию — 120 (две минуты).|

- Агент тестирования: *QTAgentService.exe.config*

    |Имя ключа|Описание|Значение|
    |-|-----------------|-|
    |ControllerConnectionPeriodInSeconds|Количество секунд между попытками подключения к контроллеру.|"n" секунд. Значение по умолчанию — 30 (тридцать секунд).|
    |RemotingTimeoutSeconds|Максимальная продолжительность (в секундах) вызова удаленного взаимодействия.|"n" секунд. Значение по умолчанию — 600 (десять минут).|
    |StopTestRunCallTimeoutInSeconds|Период времени (в секундах), в течение которого вызов должен ожидать остановки тестового запуска.|"n" секунд. Значение по умолчанию — 120 (две минуты).|
    |GetCollectorDataTimeout|Период ожидания сборщика данных (в секундах).|"n" секунд. Значение по умолчанию — 300 (пять минут).|

## <a name="to-specify-agent-timeout-options-for-a-test-controller"></a>Задание периодов ожидания агента для контроллера тестирования

1. Откройте XML-файл конфигурации *QTCcontroller.exe.config*, расположенный в папке *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

2. Найдите тег `<appSettings>`.

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

3. Измените существующее значение для одного из разделов периода ожидания контроллера тестирования. Например, можно изменить значение по умолчанию для раздела `AgentConnectionTimeoutInSeconds` с двух до трех минут.

    ```xml
    <add key="AgentConnectionTimeoutInSeconds" value="180"/>
    ```

    -или-

    Добавьте дополнительный раздел и укажите значение периода ожидания. Например, можно добавить раздел `AgentInitializeTimeout` в раздел `<appSettings>` и указать значение пять минут:

    ```xml
    <appSettings>
            <add key="AgentInitializeTimeout" value="300"/>
    </appSettings>
    ```

## <a name="to-specify-agent-timeout-options-for-a-test-agent"></a>Задание параметров периода ожидания агента для агента тестирования

1. Откройте XML-файл конфигурации *QTAgentService.exe.config*, расположенный в папке *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

2. Найдите тег `<appSettings>`.

    ```xml
    <appSettings>
      <appSettings>
      <add key="LogSizeLimitInMegs" value="20"/>
      <add key="AgentServicePort" value="6910"/>
      <add key="ControllerConnectionPeriodInSeconds" value="30"/>
      <add key="StopTestRunCallTimeoutInSeconds" value="120"/>
      <add key="CreateTraceListener" value="no"/>
      <add key="GetCollectorDataTimeout" value="300"/>
    </appSettings>  </appSettings>
    ```

3. Измените существующее значение для одного из разделов периода ожидания агента тестирования. Например, можно изменить значение по умолчанию для раздела `ControllerConnectionPeriodInSeconds` с тридцати секунд до одной минуты.

    ```xml
    <add key="ControllerConnectionPeriodInSeconds" value="60"/>
    ```

    -или-

    Добавьте дополнительный раздел и укажите значение периода ожидания. Например, можно добавить раздел `RemotingTimeoutSeconds` в раздел `<appSettings>` и указать значение пятнадцать минут:

    ```xml
    <appSettings>
            <add key=" RemotingTimeoutSeconds " value="900"/>
    </appSettings>
    ```

## <a name="see-also"></a>См. также раздел

- [Установка и настройка агентов тестирования](../test/lab-management/install-configure-test-agents.md)
- [Изменение параметров ведения журнала для нагрузочного теста](../test/modify-load-test-logging-settings.md)
- [Настройка портов для контроллеров и агентов тестирования](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [Практическое руководство. Привязка контроллера тестирования или агента тестирования к сетевому адаптеру](../test/how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter.md)
