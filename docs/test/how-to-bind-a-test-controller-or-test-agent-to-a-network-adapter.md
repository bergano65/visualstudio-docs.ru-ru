---
title: Привязка контроллера или агента тестирования к сетевому адаптеру
description: Сведения о том, как связать контроллер тестирования или агент тестирования с помощью IP-адреса в том случае, если он установлен для нескольких сетевых адаптеров.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- controllers, netwrok adapter
- agents, configuring
- agents, network adapter
- controllers, configuring
ms.assetid: 7eb9290a-f9f6-4e41-9caa-796fcfaf0610
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: f35e870e625a0f494692d082494ee0c2511ffd8f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966842"
---
# <a name="how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter"></a>Практическое руководство. Привязка контроллера тестирования или агента тестирования к сетевому адаптеру

Если компьютер, на котором установлено программное обеспечение контроллера или агента тестирования, оснащен несколькими сетевыми адаптерами, то чтобы определить этот контроллер или агент тестирования, необходимо указать не имя компьютера, а IP-адрес.

> [!WARNING]
> При попытке установки агента тестирования может появиться следующее сообщение об ошибке.
>
> **Ошибка 8110. Невозможно подключиться к указанному компьютеру контроллера или получить доступ к объекту контроллера**
>
> Эта ошибка может быть вызвана установкой контроллера тестирования на компьютер с несколькими сетевыми адаптерами. Кроме того, можно успешно установить агентов, а проблема возникнет только при выполнении теста.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="bind-a-test-controller-to-a-specific-network-adapter"></a>Привязка контроллера тестирования к определенному сетевому адаптеру

### <a name="to-obtain-the-ip-addresses-of-the-network-adapters"></a>Получение IP-адресов сетевых адаптеров

1. В операционной системе Microsoft Windows нажмите кнопку **Пуск**, перейдите в поле **Начать поиск**, введите команду **cmd** и нажмите клавишу **ВВОД**.

2. Введите команду **ipconfig /all**.

     Будут отображены IP-адреса для сетевых адаптеров. Запишите IP-адрес сетевого адаптера, к которому требуется привязать контроллер.

### <a name="to-bind-a-network-adapter-to-a-test-controller"></a>Привязка сетевого адаптера к контроллеру тестирования

1. В операционной системе Microsoft Windows нажмите кнопку **Пуск**, перейдите в поле **Начать поиск**, введите **services.msc** и нажмите клавишу **ВВОД**.

     Откроется диалоговое окно **Службы**.

2. В столбце **Имя** в области результатов щелкните правой кнопкой мыши службу **Контроллер тестирования Visual Studio** и выберите команду **Остановить**.

     -или-

     Откройте окно командной строки с повышенными привилегиями и выполните следующую команду:

     `net stop vsttcontroller`

3. Откройте XML-файл конфигурации *QTCcontroller.exe.config*, расположенный в папке *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\\\<edition>\Common7\IDE*.

4. Найдите тег `<appSettings>`.

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

5. Добавьте ключ `BindTo` для указания сетевого адаптера, который должен использоваться в разделе `<appSettings>`.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6. Запустите службу контроллера тестирования. Для этого выполните в командной строке следующую команду:

    `net start vsttcontroller`

    > [!WARNING]
    > Для подключения агента тестирования к контроллеру необходимо заново выполнить установку агента. На этот раз вместо имени контроллера укажите его IP-адрес.

     Это применимо к контроллеру, службе агента и процессу агента. Свойство `BindTo` следует установить для каждого процесса, выполняющегося на компьютере с несколькими сетевыми адаптерами. Процедура установки свойства `BindTo` одинакова для всех процессов (см. описание для контроллера тестирования ранее в этом разделе).

### <a name="to-bind-a-network-interface-card-to-a-test-agent"></a>Привязка сетевого адаптера к агенту тестирования

1. В операционной системе Microsoft Windows нажмите кнопку **Пуск**, перейдите в поле **Начать поиск**, введите **services.msc** и нажмите клавишу **ВВОД**.

    Откроется диалоговое окно **Службы**.

2. В столбце **Имя** в области результатов щелкните правой кнопкой мыши службу **Агент тестирования Visual Studio** и выберите команду **Остановить**.

     -или-

     Откройте окно командной строки с повышенными привилегиями и выполните следующую команду:

     **net stop vsttagent**

3. Откройте XML-файл конфигурации *QTAgentService.exe.config*, расположенный в папке *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\\\<edition>\Common7\IDE*.

4. Найдите тег `<appSettings>`.

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

5. Добавьте ключ `BindTo` для указания сетевого адаптера, который должен использоваться в разделе `<appSettings>`.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6. Запустите службу агента тестирования. Для этого выполните в командной строке следующую команду:

    `net start vsttagent`

## <a name="see-also"></a>См. также

- [Установка и настройка агентов тестирования](../test/lab-management/install-configure-test-agents.md)
- [Изменение параметров ведения журнала для нагрузочного теста](../test/modify-load-test-logging-settings.md)
- [Настройка портов для контроллеров и агентов тестирования](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [Практическое руководство. Задание периодов ожидания для контроллеров тестирования и агентов тестирования](../test/how-to-specify-timeout-periods-for-test-controllers-and-test-agents.md)
