---
title: Удаленный отладчик загрузки
description: Ссылки на скачивание для удаленного отладчика
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 01ec01ad642333d9ee46296cbcb4a02526152e94
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526877"
---
На удаленном устройстве или сервер, который требуется отладить на, а не компьютера с Visual Studio Загрузите и установите правильную версию инструментов удаленной отладки по ссылкам в следующей таблице.

- Скачайте последние инструменты удаленной отладки для вашей версии Visual Studio. Последнюю версию инструментов удаленной отладки совместим с более ранними версиями Visual Studio, но более ранние версии инструментов удаленной отладки не совместимы с более поздними версиями Visual Studio.
- Загрузите инструменты удаленной отладки с ту же архитектуру, что и их установке на. Например если необходимо выполнить отладку 32-разрядное приложение на удаленном компьютере под управлением 64-разрядной операционной системы, установите средства удаленного 64-разрядной.

::: moniker range=">=vs-2019"

> [!NOTE]
> Пока не станут доступными, если необходимо использовать удаленный отладчик с помощью Visual Studio 2019 г., автономный удаленных средств для Visual Studio 2019 [найти удаленный отладчик](https://docs.microsoft.com/visualstudio/debugger/remote-debugging?view=vs-2017#fileshare_msvsmon) в установке Visual Studio 2019 г., и, либо скопируйте и запустите его на удаленного репозитория машинного или запустить его из общей папкой.

::: moniker-end

|Версия|Ссылка|Примечания|
|-|-|-|
|Visual Studio 2017 (последняя версия)|[Инструменты удаленной отладки](https://visualstudio.microsoft.com/downloads/?q=remote+tools#remote-tools-for-visual-studio-2017)|Совместимость со всеми версиями Visual Studio 2017. Скачайте версию, которая соответствует операционной системе устройства (x 86, x64 или ARM64). В Windows Server, см. в разделе [разблокировать на загрузку файла](../../debugger/remote-debugging-unblock-file-download.md) загрузить инструменты удаленной отладки.|
|Visual Studio 2015|[Инструменты удаленной отладки](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Инструменты удаленной отладки для Visual Studio 2015 доступны из My.VisualStudio.com. При появлении присоединиться к бесплатным [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) программы или войдите с помощью идентификатор вашей подписки Visual Studio. В Windows Server, см. в разделе [разблокировать на загрузку файла](../../debugger/remote-debugging-unblock-file-download.md) загрузить инструменты удаленной отладки.|
|Visual Studio 2013|[Инструменты удаленной отладки](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#Installing_the_Remote_Tools)|Загрузить страницу в документации по Visual Studio 2013|
|Visual Studio 2012|[Инструменты удаленной отладки](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#BKMK_Installing_the_Remote_Tools)|Загрузить страницу в документации по Visual Studio 2012|

Можно запускать удаленный отладчик, скопировав *msvsmon.exe* для удаленного компьютера, а не выполнять установку инструментов удаленной отладки. Тем не менее мастер настройки удаленного отладчика (*rdbgwiz.exe*) доступен только при установке инструментов удаленной отладки. Необходимо использовать мастер для конфигурации, если вы хотите запустить удаленный отладчик как службу. Дополнительные сведения см. в разделе [(необязательно) Настройка удаленного отладчика как службы](../../debugger/remote-debugging.md#bkmk_configureService).

>[!NOTE]
>- Чтобы выполнить отладку приложений Windows 10 на устройствах ARM, используйте ARM64, которая доступна в последнюю версию инструментов удаленной отладки.
>- Для отладки приложений Windows 10 в Windows RT используйте ARM, который доступен только в Visual Studio 2015, скачайте инструменты удаленной отладки.
