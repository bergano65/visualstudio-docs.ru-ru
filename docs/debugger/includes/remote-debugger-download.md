---
title: Загрузка удаленного отладчика
description: Ссылки для загрузки удаленного отладчика
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 1e90a1d9e03892cf81bd2257d3dcc6e25ab36246
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68149204"
---
На удаленном устройстве или сервере, на котором требуется выполнить отладку (не на компьютере Visual Studio), скачайте и установите правильную версию инструментов удаленной отладки по ссылкам, приведенным в следующей таблице.

- Скачайте последние версии инструментов удаленной отладки для вашей версии Visual Studio. Последняя версия инструментов удаленной отладки совместима с более ранними версиями Visual Studio, но более ранние версии инструментов удаленной отладки несовместимы с более поздними версиями Visual Studio. (Например, если вы используете Visual Studio 2017, скачайте последнее обновление инструментов удаленной отладки для Visual Studio 2017. В этом случае не следует скачивать средства удаленной отладки для Visual Studio 2019.)
- Скачивайте средства удаленной отладки с архитектурой, соответствующей архитектуре компьютера, на котором они будут устанавливаться. Например, если вы хотите отлаживать 32-разрядное приложение на удаленном компьютере под управлением 64-разрядной операционной системы, установите 64-разрядные инструменты удаленной отладки.

::: moniker range=">=vs-2019"

|Version|Ссылка|Примечания|
|-|-|-|
|Visual Studio 2019|[Инструменты удаленной отладки](https://visualstudio.microsoft.com/downloads#remote-tools-for-visual-studio-2019)|Совместимы со всеми версиями Visual Studio 2019. Скачивайте версию, соответствующую операционной системе вашего устройства (x86, x64 или ARM64). Справку по загрузке инструментов удаленной отладки для Windows Server см. в разделе [Разблокировка загрузки файла](../../debugger/remote-debugging-unblock-file-download.md).|
|Visual Studio 2017|[Инструменты удаленной отладки](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Совместимы со всеми версиями Visual Studio 2017. Скачивайте версию, соответствующую операционной системе вашего устройства (x86, x64 или ARM64). Справку по загрузке инструментов удаленной отладки для Windows Server см. в разделе [Разблокировка загрузки файла](../../debugger/remote-debugging-unblock-file-download.md).|
|Visual Studio 2015|[Инструменты удаленной отладки](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Инструменты удаленной отладки для Visual Studio 2015 доступны по адресу My.VisualStudio.com. При запросе присоединитесь к бесплатной программе [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) или войдите со своим идентификатором подписки Visual Studio. Справку по загрузке инструментов удаленной отладки для Windows Server см. в разделе [Разблокировка загрузки файла](../../debugger/remote-debugging-unblock-file-download.md).|
|Visual Studio 2013|[Инструменты удаленной отладки](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#installing-the-remote-tools)|Страница загрузки в документации Visual Studio 2013|
|Visual Studio 2012|[Инструменты удаленной отладки](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#installing-the-remote-tools)|Страница загрузки в документации Visual Studio 2012|

::: moniker-end

::: moniker range="vs-2017"

|Version|Ссылка|Примечания|
|-|-|-|
|Visual Studio 2017|[Инструменты удаленной отладки](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Совместимы со всеми версиями Visual Studio 2017. Скачивайте версию, соответствующую операционной системе вашего устройства (x86, x64 или ARM64). Справку по загрузке инструментов удаленной отладки для Windows Server см. в разделе [Разблокировка загрузки файла](../../debugger/remote-debugging-unblock-file-download.md). Последнюю версию инструментов удаленной отладки можно узнать в [документации Visual Studio 2019](../../debugger/remote-debugging.md?view=vs-2019).|
|Visual Studio 2015|[Инструменты удаленной отладки](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Инструменты удаленной отладки для Visual Studio 2015 доступны по адресу My.VisualStudio.com. При запросе присоединитесь к бесплатной программе [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) или войдите со своим идентификатором подписки Visual Studio. Справку по загрузке инструментов удаленной отладки для Windows Server см. в разделе [Разблокировка загрузки файла](../../debugger/remote-debugging-unblock-file-download.md).|
|Visual Studio 2013|[Инструменты удаленной отладки](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#installing-the-remote-tools)|Страница загрузки в документации Visual Studio 2013|
|Visual Studio 2012|[Инструменты удаленной отладки](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#installing-the-remote-tools)|Страница загрузки в документации Visual Studio 2012|

::: moniker-end

Чтобы запустить удаленный отладчик, можно не устанавливать инструменты удаленной отладки, а просто скопировать файл *msvsmon.exe* на удаленный компьютер. Однако мастер настройки удаленного отладчика (*rdbgwiz.exe*) доступен только после установки инструментов удаленной отладки. Этот мастер может потребоваться для настройки, если вы захотите запускать удаленный отладчик как службу. Дополнительные сведения см. в разделе [ (Дополнительно) Настройка удаленного отладчика как службы](../../debugger/remote-debugging.md#bkmk_configureService).

>[!NOTE]
>- Для отладки приложений Windows 10 на устройствах ARM используйте ARM64, доступный с последней версией инструментов удаленной отладки.
>- Для отладки приложений Windows 10 на устройствах Windows RT используйте ARM, доступный только при загрузке инструментов удаленной отладки Visual Studio 2015.
