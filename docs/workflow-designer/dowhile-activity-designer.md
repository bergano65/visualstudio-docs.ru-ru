---
title: Конструктор действий конструктор рабочих процессов DoWhile
description: Узнайте, как действие DoWhile выполняет действие, содержащееся в его теле, по крайней мере один раз, пока заданное условие не примет значение false.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6e117fcbea0488c4b6a42125971984b86cf78251
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894261"
---
# <a name="dowhile-activity-designer"></a>Конструктор действия DoWhile

<xref:System.Activities.Statements.DoWhile>Действие выполняет действие, содержащееся по <xref:System.Activities.Statements.DoWhile.Body%2A> крайней мере один раз, пока заданное условие не примет **значение false**. Если необходимо, чтобы действие, содержащееся в теле цикла, выполнялось ноль или более раз, используйте действие <xref:System.Activities.Statements.While>.

## <a name="dowhile-properties-in-the-workflow-designer"></a>Свойства DoWhile в конструкторе рабочих процессов

В следующей таблице показаны наиболее полезные <xref:System.Activities.Statements.DoWhile> Свойства действий и описано, как их использовать в конструкторе.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|Действие, выполняемое, пока условие имеет **значение true**. Чтобы добавить <xref:System.Activities.Statements.DoWhile.Body%2A> действие, перетащите действие из области элементов в поле **текст** в конструкторе действия **DoWhile** с текстом подсказки "перетащите действие сюда".|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|Условие оценивается после каждой итерации цикла. Чтобы задать <xref:System.Activities.Statements.DoWhile.Condition%2A> , введите Visual Basic выражение в поле **условие** в конструкторе действий **DoWhile** или в сетке свойств.|

## <a name="see-also"></a>См. также раздел

- [While](../workflow-designer/while-activity-designer.md)
- [Поток управления](../workflow-designer/control-flow-activity-designers.md)