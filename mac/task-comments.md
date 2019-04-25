---
title: Комментарии к задачам
description: Добавление комментариев к задаче в код
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 3caef73ba46afd8eaf90826540248cb2d5c4efef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62999725"
---
# <a name="task-comments"></a>Комментарии к задачам

При написании кода рекомендуется явным образом комментировать незаконченный или сомнительный код или предлагать быстрые обходные пути с предупреждениями. По умолчанию в Visual Studio для Mac предоставляются маркеры сигналов TODO, HACK, FIXME и UNDONE. Персонализированные токены можно определить в разделе **Visual Studio > Параметры > Окружение > Задачи**, как показано на следующем изображении:

![Параметры списка задач](media/source-editor-image10.png)

Чтобы добавить новую заметку задачи, добавьте заметку, содержащую ключевое слово этой задачи. Например:

```csharp
//TODO: Finish this for all properties.
```

Visual Studio для Mac привлекает внимание к этим токенам, выделяя их на панели **Список задач**, который можно отобразить с помощью команды **Вид > Панели > Задача**.

![Панель списка задач](media/source-editor-image11.png)

## <a name="see-also"></a>См. также

- [Использование списка задач (Visual Studio в Windows)](/visualstudio/ide/using-the-task-list)