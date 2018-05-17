---
title: Комментарии к задачам
description: Добавление комментариев к задаче в код
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 23ce804476b6495d45e114728b287c1f5f85d1d9
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="task-comments"></a>Комментарии к задачам

При написании кода рекомендуется явным образом комментировать незаконченный или сомнительный код или предлагать быстрые обходные пути с предупреждениями. По умолчанию в Visual Studio для Mac предоставляются маркеры сигналов TODO, HACK, FIXME и UNDONE. Персонализированные маркеры можно определить в разделе **Visual Studio > Параметры... > Окружение > Задачи**, как показано на следующем изображении:

 ![Параметры списка задач](media/source-editor-image10.png)

Чтобы добавить новую заметку задачи, добавьте заметку, содержащую ключевое слово этой задачи. Пример:

```csharp
//TODO: Finish this for all properties.
```

Visual Studio для Mac привлекает внимание к этим маркерам, выделяя их на панели списка задач, который можно отобразить с помощью команды **Вид > Панели > Задача**:

![Панель списка задач](media/source-editor-image11.png)