---
title: Конструктор действий создания конструктор рабочих процессов
description: Сведения о действии Throw и о том, как можно использовать конструктор действий Throw для создания и настройки действия Throw.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a1ffd0a9dda243e53431e419910b866853cd3932
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969103"
---
# <a name="throw-activity-designer"></a>Конструктор действия Throw

Конструктор действия **throw** используется для создания и настройки <xref:System.Activities.Statements.Throw> действия.

## <a name="the-throw-activity"></a>Действие Throw

Действие <xref:System.Activities.Statements.Throw> вызывает исключение.

### <a name="using-the-throw-activity-designer"></a>Использование конструктора операций Throw

Доступ к конструктору действий **throw** в категории " **Обработка ошибок** " **панели элементов**.

Конструктор действий **throw** можно перетащить из **панели элементов** в конструктор рабочих процессов область, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence> . При этом создается <xref:System.Activities.Statements.Throw> действие со значением **DisplayName** по умолчанию Throw. <xref:System.Activities.Activity.DisplayName%2A>Значение можно изменить в заголовке конструктора действий **throw** или в поле **DisplayName** сетки свойств. Свойство <xref:System.Activities.Statements.Throw.Exception%2A> должно редактироваться в таблице свойств.

### <a name="the-throw-properties"></a>Свойства Throw

В следующей таблице показаны свойства <xref:System.Activities.Statements.Throw> и описано их использование в конструкторе.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает необязательное понятное имя действия <xref:System.Activities.Statements.Throw>. По умолчанию используется Throw.|
|<xref:System.Activities.Statements.Throw.Exception%2A>|True|Вызываемое исключение. Данное исключение должно быть производным от класса <xref:System.Exception>. Чтобы указать исключение, введите выражение Visual Basic в таблице свойств.|

## <a name="see-also"></a>См. также раздел

- [Коллекция](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Конструктор действия Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)
