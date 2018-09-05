---
title: Комментарии к задачам
description: Добавление комментариев к задаче в код
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 44d82becfbf3a16ccd2158ac05e171e8530cd721
ms.sourcegitcommit: 2597236a481afbaf1ad4915743898ee1aee49760
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/10/2018
ms.locfileid: "43223906"
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