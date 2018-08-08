---
title: Устранение неполадок с удаленной отладкой в Azure для Python
description: Устранение неполадок во время отладки приложения Python, выполняющегося в Службе приложений Azure, с помощью Visual Studio.
ms.date: 06/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: f545fa223aa929b79016352e799d112bceddaf1c
ms.sourcegitcommit: 4f82c178b1ac585dcf13b515cc2a9cb547d5f949
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/30/2018
ms.locfileid: "39341467"
---
# <a name="remote-debugging-troubleshooter-for-python-and-azure"></a>Устранение неполадок с удаленной отладкой Python и Azure

Если Visual Studio не удается подключиться к [службе приложений Azure для удаленной отладки](debugging-remote-python-code-on-azure.md), это может быть вызвано любой из следующих причин:

| Причина | Решение |
| --- | --- |
| У вас не установлена среда Visual Studio 2013 с обновлением 4 или более поздней версии. | Установите поддерживаемую версию с сайта [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017). |
| Проект, развернутый в службе приложений, не соответствует тому, который открыт в Visual Studio. | Загрузите правильный проект в Visual Studio. |
| При развертывании проекта не выбрана конфигурация **отладки**. | Повторно разверните приложение, щелкнув проект правой кнопкой мыши в **обозревателе решений** и выбрав действие **Публиковать**. На вкладке **Параметры** убедитесь, что выбрана конфигурация **Отладка**. |
| Служба приложений не запущена. | Запустите службу из **обозревателя сервера** в Visual Studio или на портале Azure. |
| В службе приложений не настроено использование веб-сокетов. | Откройте [портал Azure](https://portal.azure.com), найдите нужную службу приложений, откройте для нее колонку **Параметры** > **Параметры приложения**, переведите параметр **Общие параметры** > **Веб-сокеты** в положение **Включено**, а затем нажмите кнопку **Сохранить**. (Обратите внимание, что представленная на этой вкладке операция **Отладка** *не имеет* отношения к отладке Python). |
| В файле *web.debug.config* отключен прокси-сервер отладки. | Удалите файл и повторно опубликуйте проект в службе приложений. Visual Studio создаст файл заново. |

См. также:

- [Удаленная отладка Azure в Python](debugging-remote-python-code-on-azure.md)
