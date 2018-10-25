---
title: Конструктор рабочих процессов - конструктор действия DoWhile
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 19817fb23bd8a22532df7d349262b689f632a3a7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839626"
---
# <a name="dowhile-activity-designer"></a>Конструктор действия DoWhile

<xref:System.Activities.Statements.DoWhile> Действия выполняет действие, содержащееся в его <xref:System.Activities.Statements.DoWhile.Body%2A> по крайней мере один раз, пока заданное условие не примет значение **false**. Если необходимо, чтобы действие, содержащееся в теле цикла, выполнялось ноль или более раз, используйте действие <xref:System.Activities.Statements.While>.

## <a name="dowhile-properties-in-the-workflow-designer"></a>Свойства DoWhile в конструкторе рабочих процессов

В следующей таблице показаны наиболее полезных <xref:System.Activities.Statements.DoWhile> свойства действия и описывается их использование в конструкторе:

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|Действие, которое выполняется, пока условие имеет **true**. Чтобы добавить <xref:System.Activities.Statements.DoWhile.Body%2A> действие, перетащите его из области элементов в **текст** поле **DoWhile** конструктора действий с текстом подсказки «Перетащить действие сюда».|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|Да|Условие оценивается после каждой итерации цикла. Чтобы задать <xref:System.Activities.Statements.DoWhile.Condition%2A>, введите выражение Visual Basic в **условие** поле **DoWhile** действие конструктора или в сетке свойств.|

## <a name="see-also"></a>См. также

- [While](../workflow-designer/while-activity-designer.md)
- [Поток управления](../workflow-designer/control-flow-activity-designers.md)