---
title: "Устранение неполадок с удаленной отладкой Azure для Python в Visual Studio | Документы Майкрософт"
description: "Устранение неполадок во время отладки приложения Python, выполняющегося в Службе приложений Azure, с помощью Visual Studio."
ms.custom: 
ms.date: 07/12/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 543358e02f37fffbcc2c3981808fded87a3cb12a
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2018
---
# <a name="remote-debugging-troubleshooter-for-python-and-azure"></a>Устранение неполадок с удаленной отладкой Python и Azure

Если Visual Studio не удается подключиться к [службе приложений Azure для удаленной отладки](debugging-remote-python-code-on-azure.md), это может быть вызвано любой из следующих причин:

| Причина | Решение |
| --- | --- |
| У вас не установлена среда Visual Studio 2013 с обновлением 4 или более поздней версии. | Установите поддерживаемую версию с сайта [visualstudio.com](https://www.visualstudio.com/downloads/). | 
| Проект, развернутый в службе приложений, не соответствует тому, который открыт в Visual Studio. | Загрузите правильный проект в Visual Studio. |
| При развертывании проекта не выбрана конфигурация отладки. | Повторно разверните приложение, щелкнув проект правой кнопкой мыши в обозревателе решений и выбрав действие **Публиковать**. На вкладке **Параметры** убедитесь, что выбрана конфигурация **Отладка**. |
| Служба приложений не запущена. | Запустите службу из обозревателя сервера в Visual Studio или на портале Azure. |
| В службе приложений не настроено использование веб-сокетов. | Откройте [портал Azure](https://portal.azure.com), найдите нужную службу приложений, откройте для нее колонку **Параметры > Параметры приложения**, переведите параметр **Общие параметры > Веб-сокеты** в положение **Включено**, а затем нажмите кнопку **Сохранить**. (Обратите внимание, что представленная на этой вкладке операция **Отладка** *не имеет* отношения к отладке Python). |
| В параметре `web.debug.config` отключен прокси-сервер отладки. | Удалите файл и повторно опубликуйте проект в службе приложений. Visual Studio создаст файл заново. |

См. также:

- [Удаленная отладка Azure в Python](debugging-remote-python-code-on-azure.md)
