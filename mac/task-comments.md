---
title: "Комментарии к задачам"
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 674bae5b22c5b9ecc5d6fda4a9a4e30e4fcd1660
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="task-comments"></a>Комментарии к задачам

При написании кода рекомендуется явным образом комментировать незаконченный или сомнительный код или предлагать быстрые обходные пути с предупреждениями. По умолчанию в Visual Studio для Mac предоставляются маркеры сигналов TODO, HACK, FIXME и UNDONE. Персонализированные маркеры можно определить в разделе **Visual Studio > Параметры... > Окружение > Задачи**, как показано на следующем изображении:

 ![Параметры списка задач](media/source-editor-image10.png)

Чтобы добавить новую заметку задачи, добавьте заметку, содержащую ключевое слово этой задачи. Пример:

```
//TODO: Finish this for all properties.
```

Visual Studio для Mac привлекает внимание к этим маркерам, выделяя их на панели списка задач, который можно отобразить с помощью команды **Вид > Панели > Задача**:

![Панель списка задач](media/source-editor-image11.png)