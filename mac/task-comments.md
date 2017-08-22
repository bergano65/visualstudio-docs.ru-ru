---
title: "Комментарии к задачам"
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: 973e7b627a7b5c121ff388874577fe59c45529d7
ms.contentlocale: ru-ru
ms.lasthandoff: 08/11/2017

---

# <a name="task-comments"></a>Комментарии к задачам

При написании кода рекомендуется явным образом комментировать незаконченный или сомнительный код или предлагать быстрые обходные пути с предупреждениями. Visual Studio для Mac предоставляет сигнальные токены по умолчанию TODO, HACK, FIXME и UNDONE, однако в разделе **Visual Studio > Параметры... > Окружение > Задачи** можно задать настраиваемые токены, как показано ниже:

 ![Параметры списка задач](media/source-editor-image10.png)

Чтобы добавить новую заметку задачи, добавьте заметку, содержащую ключевое слово этой задачи. Пример:

```
//TODO: Finish this for all properties.
```

Visual Studio для Mac привлекает внимание к этим маркерам, выделяя их на панели списка задач, который можно отобразить с помощью команды **Вид > Панели > Задача**:

![Панель списка задач](media/source-editor-image11.png)
