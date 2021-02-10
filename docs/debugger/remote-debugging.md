---
title: Удаленная отладка | Документация Майкрософт
description: Отладка приложения Visual Studio, развернутого на другом компьютере, с помощью удаленного отладчика Visual Studio.
ms.custom:
- remotedebugging
- seodec18
- SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f67035dc2f7a33fb436c0c51ba2214272ab2cf79
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891427"
---
# <a name="remote-debugging"></a>Remote Debugging
Вы можете отладить приложение Visual Studio, развернутое на другом компьютере. Для этого используется удаленный отладчик Visual Studio.

Подробные инструкции по удаленной отладке см. в следующих разделах.

|Сценарий|Ссылка|
|-|-|-|
|Служба приложений Azure|[Удаленная отладка ASP.NET в Azure](../debugger/remote-debugging-azure.md) или, для Visual Studio Enterprise, [Snapshot Debugger](../debugger/debug-live-azure-applications.md)|
|Виртуальная машина Azure|[Удаленная отладка ASP.NET в Azure](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[Отладка приложения Azure Service Fabric](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[Удаленная отладка ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) или [Удаленная отладка ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# или Visual Basic|[Удаленная отладка проекта C# или Visual Basic](../debugger/remote-debugging-csharp.md)|
|C++|[Удаленная отладка проекта на C++](../debugger/remote-debugging-cpp.md)|
|Универсальные приложения Windows (UWP)|[Запуск приложений UWP на удаленном компьютере](../debugger/run-windows-store-apps-on-a-remote-machine.md) или [Отладка установленного пакета приложения](../debugger/debug-installed-app-package.md)|

Если нужно просто скачать и установить удаленный отладчик, и вам не нужны дополнительные инструкции для своего сценария, выполните действия, описанные в этой статье.

## <a name="download-and-install-the-remote-tools"></a>Скачивание и установка инструментов удаленной отладки

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="requirements"></a><a name="requirements_msvsmon"></a> Требования

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]

## <a name="optional-to-run-the-remote-debugger-from-a-file-share"></a><a name="fileshare_msvsmon"></a> (Дополнительно) Запуск удаленного отладчика из общей папки

Удаленный отладчик (*msvsmon.exe*) можно найти на компьютере с уже установленным Visual Studio Community, Professional или Enterprise. В некоторых сценариях самый простой способ настроить удаленную отладку — запустить удаленный отладчик (msvsmon.exe) из общей папки. Об ограничениях использования см. на странице справки удаленного отладчика (**Справка > Использование** в удаленном отладчике).

1. Найдите файл *msvsmon.exe* в каталоге, соответствующем вашей версии Visual Studio:

   ::: moniker range=">=vs-2019"

   *Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end
   ::: moniker range="vs-2017"

   *Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end

2. Предоставьте общий доступ к папке **удаленного отладчика** на компьютере с Visual Studio.

3. На удаленном компьютере запустите файл *msvsmon.exe* из общей папки. Следуйте [инструкциям по установке](#bkmk_setup).

> [!TIP]
> Сведения об установке из командной строки и справочник по командной строке см. на странице справки для *msvsmon.exe*. Для этого введите ``msvsmon.exe /?`` в командной строке на компьютере с установленным Visual Studio (или перейдите в раздел **Справка > Использование** в удаленном отладчике).

## <a name="set-up-the-remote-debugger"></a><a name="bkmk_setup"></a> Установка удаленного отладчика

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure-the-remote-debugger"></a><a name="configure_msvsmon"></a> Настройка удаленного отладчика
После первого запуска удаленного отладчика можно изменить некоторые аспекты его конфигурации.

- Если нужно добавить разрешения на подключение к удаленному отладчику для других пользователей, выберите **Инструменты > Разрешения**. Для предоставления разрешений или отказа в предоставлении необходимо обладать правами администратора.

     > [!IMPORTANT]
     > Вы можете запускать удаленный отладчик в учетной записи пользователя, отличной от используемой на компьютере Visual Studio, но эту учетную запись нужно добавить в список разрешений удаленного отладчика.

     Кроме того, удаленный отладчик можно запускать из командной строки с помощью параметра **/allow \<username>** : **msvsmon /allow \<username@computer>** .

- Чтобы изменить режим аутентификации или номер порта либо задать значение времени ожидания для инструментов удаленной отладки, выберите **Инструменты > Параметры**.

     Список номеров портов, используемых по умолчанию, см. в разделе [Назначения портов удаленного отладчика](../debugger/remote-debugger-port-assignments.md).

     > [!WARNING]
     > Вы можете запускать инструменты удаленной отладки в режиме "без аутентификации", однако настоятельно рекомендуется не использовать этот режим. При работе в этом режиме сетевая безопасность не обеспечивается. Режим без аутентификации можно выбрать, только если вы уверены в отсутствии вредоносного или опасного трафика.

## <a name="optional-configure-the-remote-debugger-as-a-service"></a><a name="bkmk_configureService"></a> (Дополнительно) Настройка удаленного отладчика как службы
Для отладки в ASP.NET и других серверных средах необходимо запускать удаленный отладчик от имени администратора, либо, если вы хотите, чтобы он всегда выполнялся, запускать его как службу.

 Чтобы настроить удаленный отладчик как службу, выполните следующие действия.

1. Найдите **мастер настройки удаленного отладчика** (rdbgwiz.exe). (Это отдельное приложение, не входящее в состав удаленного отладчика.) Он доступен только в том случае, если вы установили инструменты удаленной отладки. Вместе с Visual Studio он не устанавливается.

2. Запустите мастер настройки. Когда появится первая страница, нажмите кнопку **Далее**.

3. Установите флажок **Запускать удаленный отладчик Visual Studio 2015 как службу** .

4. Добавьте имя учетной записи пользователя и пароль.

    Может потребоваться добавить в эту учетную запись право пользователя **Вход в качестве службы** (выполните поиск **локальной политики безопасности** (secpol.msc) на **начальной** странице или окне или введите **secpol** в командной строке). В открывшемся окне дважды щелкните элемент **Назначение прав пользователя**, а затем в области справа найдите элемент **Вход в качестве службы** . Дважды щелкните его. Добавьте учетную запись пользователя в окно **Свойства** и нажмите кнопку **ОК**.) Нажмите кнопку **Далее**.

5. Выберите тип сети, с которой должны взаимодействовать инструменты удаленной отладки. Должен быть выбран по крайней мере один тип сети. Если компьютеры соединены через домен, необходимо выбрать первый пункт. Если компьютеры соединены посредством рабочей или домашней группы, необходимо выбрать второй или третий пункт. Нажмите кнопку **Далее**.

6. Если службу удается запустить, вы увидите сообщение **Вы успешно завершили работу мастера настройки удаленного отладчика Visual Studio**. Если службу не удается запустить, вы увидите сообщение **Не удалось завершить мастер настройки удаленного отладчика Visual Studio**. На странице также приводится ряд советов по запуску службы.

7. Нажмите кнопку **Готово**.

   Теперь удаленный отладчик должен работать как служба. Чтобы проверить, так ли это, выберите **Панель управления > Службы** и найдите службу **Удаленный отладчик Visual Studio 2015**.

   Останавливать и запускать службу удаленного отладчика можно с помощью компонента **Панель управления > Службы**.

## <a name="set-up-debugging-with-remote-symbols"></a>Настройка отладки с использованием удаленных символов

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>См. также

- [Первое знакомство с отладчиком](../debugger/debugger-feature-tour.md)
- [Настройка брандмауэра Windows для удаленной отладки](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Назначение портов удаленного отладчика](../debugger/remote-debugger-port-assignments.md)
- [Удаленная отладка ASP.NET Core на удаленном компьютере IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Ошибки удаленной отладки и их устранение](../debugger/remote-debugging-errors-and-troubleshooting.md)