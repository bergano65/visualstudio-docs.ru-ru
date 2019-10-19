---
title: Конструктор действий конструктор рабочих процессов DoWhile
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85f8d6c442982fff47a679e8fc2ccc04ee515a9b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650517"
---
# <a name="dowhile-activity-designer"></a>Конструктор действия DoWhile

Действие <xref:System.Activities.Statements.DoWhile> выполняет действие, содержащееся в его <xref:System.Activities.Statements.DoWhile.Body%2A> по крайней мере один раз, пока заданное условие не примет **значение false**. Если необходимо, чтобы действие, содержащееся в теле цикла, выполнялось ноль или более раз, используйте действие <xref:System.Activities.Statements.While>.

## <a name="dowhile-properties-in-the-workflow-designer"></a>Свойства DoWhile в конструкторе рабочих процессов

В следующей таблице показаны наиболее полезные <xref:System.Activities.Statements.DoWhile> свойства действий и описано, как их использовать в конструкторе.

|Имя свойства|Обязательное значение|Использование|
|-|--------------|-|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|Действие, выполняемое, пока условие имеет **значение true**. Чтобы добавить действие <xref:System.Activities.Statements.DoWhile.Body%2A>, перетащите действие из области элементов в поле **текст** в конструкторе действия **DoWhile** с текстом подсказки "перетащите действие сюда".|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|Условие оценивается после каждой итерации цикла. Чтобы задать <xref:System.Activities.Statements.DoWhile.Condition%2A>, введите Visual Basic выражение в поле **условие** в конструкторе действий **DoWhile** или в сетке свойств.|

## <a name="see-also"></a>См. также

- [While](../workflow-designer/while-activity-designer.md)
- [Поток управления](../workflow-designer/control-flow-activity-designers.md)