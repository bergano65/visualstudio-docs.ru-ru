---
title: Конструктор действия "конструктор рабочих процессов повторного создания"
description: Узнайте о действиях повторного создания и о том, как использовать конструктор действий Rethrow для создания и настройки действия "Повторная генерация".
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2e3615c73583e8c5c313d23fd5f9aa6d9fcd5ff4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847327"
---
# <a name="rethrow-activity-designer"></a>Конструктор действия Rethrow

Конструктор действия **Rethrow** используется для создания и настройки <xref:System.Activities.Statements.Rethrow> действия.

## <a name="the-rethrow-activity"></a>Действие "Повторная генерация"

Действие <xref:System.Activities.Statements.Rethrow> вызывает ранее вызванное исключение. Это действие может использоваться только в обработчике <xref:System.Activities.Statements.Catch> в действии <xref:System.Activities.Statements.TryCatch>.

### <a name="use-the-rethrow-activity-designer"></a>Использование конструктора действия Rethrow

Доступ к конструктору действий **Rethrow** в категории " **Обработка ошибок** " **панели элементов**. Конструктор действий **регенерации** можно перетащить из **панели элементов** в конструктор рабочих процессов область, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence> . При удалении конструктора действий создается <xref:System.Activities.Statements.Rethrow> действие со значением **DisplayName** по умолчанию Throw. <xref:System.Activities.Activity.DisplayName%2A>Значение может быть изменено в заголовке конструктора действия **Rethrow** или в поле **DisplayName** сетки свойств.

### <a name="the-rethrow-properties"></a>Свойства Rethrow

В следующей таблице показаны <xref:System.Activities.Statements.Rethrow> Свойства и описано, как они используются в конструкторе.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает необязательное понятное имя действия <xref:System.Activities.Statements.Rethrow>. По умолчанию используется Rethrow.|

## <a name="see-also"></a>См. также раздел

- [Коллекция](../workflow-designer/collection-activity-designers.md)
- [Даче](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)
