---
title: Комментарии к задачам
description: Добавление комментариев к задаче в код
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: d88b74ab953f97e061f4be3befc227646006f38b
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2019
ms.locfileid: "67692313"
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