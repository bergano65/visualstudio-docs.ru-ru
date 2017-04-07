---
title: "Устранение неполадок с удаленной отладкой Azure с помощью Инструментов Python для Visual Studio | Документация Майкрософт"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b723b343-dffb-457e-9af7-ee48c1451e30
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: fcf44a3967c0bd391808c9f6b3a23f39aeff05fd
ms.lasthandoff: 03/07/2017

---

# <a name="remote-debugging-troubleshooter-for-python-and-azure"></a>Устранение неполадок с удаленной отладкой для Python и Azure

Если Visual Studio не может подключиться к [службе приложений Azure для удаленной отладки](debugging-azure-remote.md), это может быть вызвано любой из следующих причин:

| Причина | Решение |
| --- | --- |
| У вас не установлена среда Visual Studio 2013 с обновлением 4 или более поздней версии. | Установите поддерживаемую версию с сайта [visualstudio.com](https://www.visualstudio.com/downloads/). | 
| Проект, развернутый в службе приложений, не соответствует тому, который открыт в Visual Studio. | Загрузите правильный проект в Visual Studio. |
| При развертывании проекта не выбрана конфигурация отладки. | Повторно разверните приложение, щелкнув проект правой кнопкой мыши в обозревателе решений и выбрав действие **Публиковать**. На вкладке **Параметры** убедитесь, что выбрана конфигурация **Отладка**. |
| Служба приложений не запущена. | Запустите службу из обозревателя сервера в Visual Studio или на портале Azure. |
| В службе приложений не настроено использование веб-сокетов. | Откройте [портал Azure](https://portal.azure.com), найдите нужную службу приложений, откройте для нее колонку **Параметры > Параметры приложения**, переведите параметр **Общие параметры > Веб-сокеты** в положение **Включено**, а затем нажмите кнопку **Сохранить**. (Обратите внимание, что представленная на этой вкладке операция **Отладка** *не имеет* отношения к отладке Python). |
| В параметре `web.debug.config` отключен прокси-сервер отладки. | Удалите файл и повторно опубликуйте проект в службе приложений. При этом инструменты Python для Visual Studio создадут файл заново. |

См. также:

- [Удаленная отладка Azure в Python](debugging-azure-remote.md)

