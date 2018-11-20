---
title: Комментарии к задачам
description: Добавление комментариев к задаче в код
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 3caef73ba46afd8eaf90826540248cb2d5c4efef
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2018
ms.locfileid: "51294283"
---
# <a name="task-comments"></a>Комментарии к задачам

При написании кода рекомендуется явным образом комментировать незаконченный или сомнительный код или предлагать быстрые обходные пути с предупреждениями. По умолчанию в Visual Studio для Mac предоставляются маркеры сигналов TODO, HACK, FIXME и UNDONE. Персонализированные токены можно определить в разделе **Visual Studio > Параметры > Окружение > Задачи**, как показано на следующем изображении:

![Параметры списка задач](media/source-editor-image10.png)

Чтобы добавить новую заметку задачи, добавьте заметку, содержащую ключевое слово этой задачи. Пример:

```csharp
//TODO: Finish this for all properties.
```

Visual Studio для Mac привлекает внимание к этим токенам, выделяя их на панели **Список задач**, который можно отобразить с помощью команды **Вид > Панели > Задача**.

![Панель списка задач](media/source-editor-image11.png)

## <a name="see-also"></a>См. также

- [Использование списка задач (Visual Studio в Windows)](/visualstudio/ide/using-the-task-list)