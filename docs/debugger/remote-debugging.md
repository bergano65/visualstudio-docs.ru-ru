---
title: Удаленная отладка | Документация Майкрософт
ms.custom:
- remotedebugging
- seodec18
ms.date: 07/02/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.overview
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9918a2de67693c0232c94a736f12c7af0a0b959c
ms.sourcegitcommit: 9753c7544cec852ca5efd0834e0956d9e53a5734
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/13/2019
ms.locfileid: "67043311"
---
# <a name="remote-debugging"></a>Remote Debugging
Вы можете отладить приложение Visual Studio, развернутое на другом компьютере. Для этого используется удаленный отладчик Visual Studio.

Подробные инструкции по удаленной отладке см. в статьях.

|Сценарий|Ссылка|
|-|-|-|
|Служба приложений Azure|[Отладчик моментальных снимков](../debugger/debug-live-azure-applications.md) или [удаленная отладка ASP.NET в Azure](../debugger/remote-debugging-azure.md)|
|Виртуальная машина Azure|[Удаленная отладка ASP.NET в Azure](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[Отладка приложения Azure Service Fabric](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[Удаленная отладка ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) или [удаленной отладке ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# или Visual Basic|[Удаленная отладка проекта C# или Visual Basic](../debugger/remote-debugging-csharp.md)|
|C++|[Удаленная отладка проекта на C++](../debugger/remote-debugging-cpp.md)|
|Приложения универсальной Windows (UWP)|[Запуск приложений UWP на удаленном компьютере](../debugger/run-windows-store-apps-on-a-remote-machine.md) или [отладка установленного пакета приложения](../debugger/debug-installed-app-package.md)|

Если вы просто хотите загрузить и установить удаленный отладчик и не нужны дополнительные инструкции для вашего сценария, выполните действия, описанные в этой статье.

## <a name="download-and-install-the-remote-tools"></a>Скачивание и установка инструментов удаленной отладки

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="requirements_msvsmon"></a> Требования

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]

## <a name="fileshare_msvsmon"></a> (Необязательно) Для запуска удаленного отладчика из общей папки

Можно найти удаленный отладчик (*msvsmon.exe*) на компьютере с Visual Studio Community, Professional или Enterprise уже установлен. Для некоторых сценариев самым простым способом настройки удаленной отладки является запуск удаленного отладчика (msvsmon.exe) из общей папки. Ограничения использования, см. в разделе страницы справки удаленный отладчик (**Справка > использование** в удаленный отладчик).

1. Найти *msvsmon.exe* в каталоге, соответствующие вашей версии Visual Studio:

   ::: moniker range=">=vs-2019"

   *Программа файлы (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Программа файлы (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end
   ::: moniker range="vs-2017"

   *Программа файлы (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Программа файлы (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end

2. Общий ресурс **удаленный отладчик** папку на компьютере с Visual Studio.

3. На удаленном компьютере, запустите *msvsmon.exe* из общей папки. Выполните [инструкции по установке](#bkmk_setup).

> [!TIP]
> Установка из командной строки и справочник по командной строке, см. на странице справки для *msvsmon.exe* , введя ``msvsmon.exe /?`` в командной строке на компьютере с установленной среды Visual Studio (или перейдите к **Справка > использование**в удаленный отладчик).

## <a name="bkmk_setup"></a> Установка удаленного отладчика

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure_msvsmon"></a> Настройка удаленного отладчика
После первого запуска удаленного отладчика можно изменить некоторые аспекты его конфигурации.

- Если необходимо добавить разрешения для других пользователей, для подключения к удаленному отладчику, выберите **средства > разрешения**. Для предоставления разрешений или отказа в предоставлении необходимо обладать правами администратора.

     > [!IMPORTANT]
     > Можно запускать удаленный отладчик с учетной записью пользователя, которая отличается от учетной записи пользователя, используемой на компьютере с Visual Studio, но необходимо добавить учетную запись другого пользователя для разрешения удаленного отладчика.

     Кроме того, удаленный отладчик можно запустить из командной строки с **/ allow \<имя пользователя >** параметр: **msvsmon / allow \< username@computer>** .

- Если вам нужно изменить режим аутентификации или номер порта, или задать значение времени ожидания для инструментов удаленной отладки: выберите **Сервис > Параметры**.

     Список номеров портов, используемых по умолчанию, см. в разделе [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md).

     > [!WARNING]
     > Вы можете запускать инструменты удаленной отладки в режиме "без аутентификации", однако настоятельно рекомендуется не использовать этот режим. При работе в этом режиме сетевая безопасность не обеспечивается. Режим без аутентификации можно выбрать, только если вы уверены в отсутствии вредоносного или опасного трафика.

## <a name="bkmk_configureService"></a> (Необязательно) Настройка удаленного отладчика в качестве службы
Для отладки в ASP.NET и других серверных средах, необходимо запустить удаленный отладчик с правами администратора или, при необходимости его всегда работает, запускать удаленный отладчик как службу.

 Если вы хотите настроить удаленный отладчик как службу, выполните следующие действия.

1. Найдите **мастер настройки удаленного отладчика** (rdbgwiz.exe). (Это отдельное приложение, не входящее в состав удаленного отладчика.) Он доступен только в том случае, если вы установили инструменты удаленной отладки. Вместе с Visual Studio он не устанавливается.

2. Запустите мастер настройки. Когда появится первая страница, нажмите кнопку **Далее**.

3. Установите флажок **Запускать удаленный отладчик Visual Studio 2015 как службу** .

4. Добавьте имя учетной записи пользователя и пароль.

    Может потребоваться добавить **вход качестве службы** справа для этой учетной записи (найти **Локальная политика безопасности** (secpol.msc) в **запустить** странице или в окне (или тип  **средства secpol** в командной строке). В открывшемся окне дважды щелкните элемент **Назначение прав пользователя**, а затем в области справа найдите элемент **Вход в качестве службы** . Дважды щелкните его. Добавьте учетную запись пользователя в окно **Свойства** и нажмите кнопку **ОК**.) Нажмите кнопку **Далее**.

5. Выберите тип сети, с которой должны взаимодействовать инструменты удаленной отладки. Должен быть выбран по крайней мере один тип сети. Если компьютеры соединены через домен, необходимо выбрать первый пункт. Если компьютеры соединены посредством рабочей или домашней группы, необходимо выбрать второй или третий пункт. Нажмите кнопку **Далее**.

6. Если службу удается запустить, вы увидите сообщение **Вы успешно завершили работу мастера настройки удаленного отладчика Visual Studio**. Если службу не удается запустить, вы увидите сообщение **Не удалось завершить мастер настройки удаленного отладчика Visual Studio**. На странице также приводится ряд советов по запуску службы.

7. Нажмите кнопку **Готово**.

   Теперь удаленный отладчик должен работать как служба. Чтобы проверить, так ли это, выберите **Панель управления > Службы** и найдите службу **Удаленный отладчик Visual Studio 2015**.

   Останавливать и запускать службу удаленного отладчика можно с помощью компонента **Панель управления > Службы**.

## <a name="set-up-debugging-with-remote-symbols"></a>Настройка отладки с удаленными символами

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>См. также

- [Первое знакомство с отладчиком](../debugger/debugger-feature-tour.md)
- [Настройка брандмауэра Windows для удаленной отладки](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Назначение портов удаленного отладчика](../debugger/remote-debugger-port-assignments.md)
- [Удаленная отладка ASP.NET Core на удаленном компьютере IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Ошибки удаленной отладки и их устранение](../debugger/remote-debugging-errors-and-troubleshooting.md)