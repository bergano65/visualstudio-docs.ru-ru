---
title: Удаленная отладка Документы Майкрософт
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301059"
---
# <a name="remote-debugging"></a>Удаленная отладка
Вы можете отладить приложение Visual Studio, развернутое на другом компьютере. Для этого используется удаленный отладчик Visual Studio.

Для углубленных инструкций по удаленной отладке см.

|Сценарий|Ссылка|
|-|-|-|
|Служба приложений Azure|[Снимок отладчик](../debugger/debug-live-azure-applications.md) или [удаленная отладка ASP.NET на Azure](../debugger/remote-debugging-azure.md)|
|Azure|[Удаленная отладка ASP.NET в Azure](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[Отчерепное приложение Azure Service Fabric](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[Дистанционная отладка ASP.NET ядра](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) или [ASP.NET удаленного отладки](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# или Visual Basic|[Удаленная отладка проекта C# или Visual Basic](../debugger/remote-debugging-csharp.md)|
|C++|[Дистанционное отладка проекта СЗЗ](../debugger/remote-debugging-cpp.md)|
|Универсальные приложения для Windows (UWP)|[Запуск приложений UWP на удаленной машине](../debugger/run-windows-store-apps-on-a-remote-machine.md) или [отожоблить установленный пакет приложений](../debugger/debug-installed-app-package.md)|

Если вы просто хотите загрузить и установить удаленный отладчик и не нуждаетесь в дополнительных инструкциях для вашего сценария, выполните последующие шаги в этой статье.

## <a name="download-and-install-the-remote-tools"></a>Скачивание и установка инструментов удаленной отладки

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="requirements"></a><a name="requirements_msvsmon"></a>Требования

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]

## <a name="optional-to-run-the-remote-debugger-from-a-file-share"></a><a name="fileshare_msvsmon"></a>(Необязательно) Запуск удаленного отладчика из общего файла

Вы можете найти удаленный отладчик *(msvsmon.exe*) на компьютере с Visual Studio сообщества, профессиональные, или предприятие уже установлен. Для некоторых сценариев самый простой способ настройки удаленной отладки — запустить удаленный отладчик (msvsmon.exe) из общего файла. Для ограничений использования см. страницу справки удаленного отладчика **(Help > Use** in the remote debugger).

1. Найти *msvsmon.exe* в каталоге, соответствующем вашей версии Visual Studio:

   ::: moniker range=">=vs-2019"

   *Программные файлы (x86)»Microsoft Visual Studio»2019-Enterprise-Common7-IDE-Remote Debugger-x86-msvsmon.exe*

   *Программные файлы (x86)»Microsoft Visual Studio»2019-Enterprise-Common7-IDE-Remote Debugger-x64-msvsmon.exe*

   ::: moniker-end
   ::: moniker range="vs-2017"

   *Программные файлы (x86)»Microsoft Visual Studio-2017*

   *Программные файлы (x86)»Microsoft Visual Studio-2017*

   ::: moniker-end

2. Поделитесь папкой **Remote Debugger** на компьютере Visual Studio.

3. На удаленном компьютере выполнить *msvsmon.exe* из общей папки. Следуйте [инструкциям по настройке.](#bkmk_setup)

> [!TIP]
> Для установки командной строки и ссылки на строку команд ``msvsmon.exe /?`` см. страницу справки для *msvsmon.exe,* введя командную строку на компьютере с установленным Visual Studio (или перейдите на **справку > использование** в удаленном отладчике).

## <a name="set-up-the-remote-debugger"></a><a name="bkmk_setup"></a>Настройка удаленного отладчика

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure-the-remote-debugger"></a><a name="configure_msvsmon"></a> Настройка удаленного отладчика
После первого запуска удаленного отладчика можно изменить некоторые аспекты его конфигурации.

- Если вам нужно добавить разрешения для подключения других пользователей к удаленному отладчику, выберите **Инструменты > разрешения.** Для предоставления разрешений или отказа в предоставлении необходимо обладать правами администратора.

     > [!IMPORTANT]
     > Вы можете запустить удаленный отладчик под учетной записью пользователя, которая отличается от учетной записи пользователя, которую вы используете на компьютере Visual Studio, но вы должны добавить другую учетную запись пользователя к разрешениям удаленного отладчика.

     Кроме того, можно запустить удаленный отладчик от командной строки с ** \</разрешить имя пользователя>** параметр: ** \< username@computer msvsmon/позволяет>. **

- Если вам необходимо изменить режим аутентификации или номер порта, или указать значение тайм-аута для удаленных инструментов: выберите **Инструменты > варианты.**

     Для перечисления номеров портов, используемых по умолчанию, [см.](../debugger/remote-debugger-port-assignments.md)

     > [!WARNING]
     > Вы можете запускать инструменты удаленной отладки в режиме "без аутентификации", однако настоятельно рекомендуется не использовать этот режим. При работе в этом режиме сетевая безопасность не обеспечивается. Режим без аутентификации можно выбрать, только если вы уверены в отсутствии вредоносного или опасного трафика.

## <a name="optional-configure-the-remote-debugger-as-a-service"></a><a name="bkmk_configureService"></a>(Необязательно) Настройка удаленного отладчика как услуги
Для отладки в ASP.NET и других серверных средах необходимо либо запустить удаленный отладчик в качестве администратора, либо, если вы хотите, чтобы он всегда работал, запустить удаленный отладчик как службу.

 Если вы хотите настроить удаленный отладчик в качестве службы, выполните следующие действия.

1. Найдите **мастер настройки удаленного отладчика** (rdbgwiz.exe). (Это отдельное приложение от удаленного debugger.) Он доступен только при установке удаленных инструментов. Вместе с Visual Studio он не устанавливается.

2. Запустите мастер настройки. Когда появится первая страница, нажмите кнопку **Далее**.

3. Установите флажок **Запускать удаленный отладчик Visual Studio 2015 как службу** .

4. Добавьте имя учетной записи пользователя и пароль.

    Возможно, вам придется добавить журнал в качестве пользователя **службы** прямо на эту учетную запись (Найдите **местную политику безопасности** (secpol.msc) на странице или окне **старта** (или введите **секпол** в запросе команды). В открывшемся окне дважды щелкните элемент **Назначение прав пользователя**, а затем в области справа найдите элемент **Вход в качестве службы** . Дважды щелкните его. Добавьте учетную запись пользователя в окно **Свойства** и нажмите кнопку **ОК**.) Нажмите кнопку **Далее**.

5. Выберите тип сети, с которой должны взаимодействовать инструменты удаленной отладки. Должен быть выбран по крайней мере один тип сети. Если компьютеры соединены через домен, необходимо выбрать первый пункт. Если компьютеры соединены посредством рабочей или домашней группы, необходимо выбрать второй или третий пункт. Нажмите кнопку **Далее**.

6. Если службу удается запустить, вы увидите сообщение **Вы успешно завершили работу мастера настройки удаленного отладчика Visual Studio**. Если службу не удается запустить, вы увидите сообщение **Не удалось завершить мастер настройки удаленного отладчика Visual Studio**. На странице также приводится ряд советов по запуску службы.

7. Нажмите кнопку **Готово**.

   Теперь удаленный отладчик должен работать как служба. Чтобы проверить, так ли это, выберите **Панель управления > Службы** и найдите службу **Удаленный отладчик Visual Studio 2015**.

   Останавливать и запускать службу удаленного отладчика можно с помощью компонента **Панель управления > Службы**.

## <a name="set-up-debugging-with-remote-symbols"></a>Настройка отладки с удаленными символами

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>См. также раздел

- [Первый взгляд на отладчика](../debugger/debugger-feature-tour.md)
- [Настройка брандмауэра Windows для удаленной отладки](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md) (Назначение портов для удаленного отладчика)
- [Удаленная дебукинг ASP.NET ядро на удаленном компьютере IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Ошибки удаленной отладки и их устранение](../debugger/remote-debugging-errors-and-troubleshooting.md)