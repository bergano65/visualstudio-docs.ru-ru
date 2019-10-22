---
title: Конструктор действий создания конструктор рабочих процессов
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe6a530888c7c28c5c1556114db03a6cd7369fe6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649851"
---
# <a name="throw-activity-designer"></a>Конструктор действия Throw

Конструктор действия **throw** используется для создания и настройки действия <xref:System.Activities.Statements.Throw>.

## <a name="the-throw-activity"></a>Действие Throw

Действие <xref:System.Activities.Statements.Throw> вызывает исключение.

### <a name="using-the-throw-activity-designer"></a>Использование конструктора операций Throw

Доступ к конструктору действий **throw** в категории " **Обработка ошибок** " **панели элементов**.

Конструктор действий **throw** можно перетащить из **панели элементов** в конструктор рабочих процессов область, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. При этом создается действие <xref:System.Activities.Statements.Throw> со значением **DisplayName** по умолчанию Throw. Значение <xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора действий **throw** или в поле **DisplayName** сетки свойств. Свойство <xref:System.Activities.Statements.Throw.Exception%2A> должно редактироваться в таблице свойств.

### <a name="the-throw-properties"></a>Свойства Throw

В следующей таблице показаны свойства <xref:System.Activities.Statements.Throw> и описано их использование в конструкторе.

|Имя свойства|Обязательное значение|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает необязательное понятное имя действия <xref:System.Activities.Statements.Throw>. По умолчанию используется Throw.|
|<xref:System.Activities.Statements.Throw.Exception%2A>|True|Вызываемое исключение. Данное исключение должно быть производным от класса <xref:System.Exception>. Чтобы указать исключение, введите выражение Visual Basic в таблице свойств.|

## <a name="see-also"></a>См. также

- [Коллекция](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Конструктор действия Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)