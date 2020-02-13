---
title: Конструктор действия "конструктор рабочих процессов повторного создания"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3cb73a674e702d54f970c5dea7ec051f100382c9
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114748"
---
# <a name="rethrow-activity-designer"></a>Конструктор действия Rethrow

Конструктор действия **Rethrow** используется для создания и настройки действия <xref:System.Activities.Statements.Rethrow>.

## <a name="the-rethrow-activity"></a>Действие "Повторная генерация"

Действие <xref:System.Activities.Statements.Rethrow> вызывает ранее вызванное исключение. Это действие может использоваться только в обработчике <xref:System.Activities.Statements.Catch> в действии <xref:System.Activities.Statements.TryCatch>.

### <a name="use-the-rethrow-activity-designer"></a>Использование конструктора действия Rethrow

Доступ к конструктору действий **Rethrow** в категории " **Обработка ошибок** " **панели элементов**. Конструктор действий **регенерации** можно перетащить из **панели элементов** в конструктор рабочих процессов область, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. При удалении конструктора действий создается <xref:System.Activities.Statements.Rethrow> действие со значением **DisplayName** по умолчанию Throw. Значение <xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора действий **Rethrow** или в поле **DisplayName** сетки свойств.

### <a name="the-rethrow-properties"></a>Свойства Rethrow

В следующей таблице показаны свойства <xref:System.Activities.Statements.Rethrow> и описано, как они используются в конструкторе.

|Имя свойства|Обязательное|Метрики|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Ложь|Указывает необязательное понятное имя действия <xref:System.Activities.Statements.Rethrow>. По умолчанию используется Rethrow.|

## <a name="see-also"></a>См. также:

- [Коллекция](../workflow-designer/collection-activity-designers.md)
- [Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)
