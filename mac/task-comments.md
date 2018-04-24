---
title: Комментарии к задачам
description: ''
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: c119af47cc3b592033a68b0ec543afa86140c77a
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/20/2018
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