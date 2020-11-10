---
title: Конструктор рабочих процессов — конструктор действий взаимодействия
description: Сведения о конструкторе действий взаимодействия и о том, как можно использовать конструктор действий взаимодействия для создания и настройки действия взаимодействия.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4a45187f01469f568a98098a8470ad62f67307a6
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437779"
---
# <a name="interop-activity-designer"></a>Конструктор действия Interop

Конструктор действий **взаимодействия** используется для создания и настройки <xref:System.Activities.Statements.Interop> действия.

## <a name="the-interop-activity"></a>Действие Interop

Действие <xref:System.Activities.Statements.Interop> управляет выполнением типов, являющихся производными от <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> в рабочем процессе.

### <a name="use-the-interop-activity-designer"></a>Использование конструктора действий взаимодействия

Конструктор действий **взаимодействия** можно найти в категории " **Миграция** " **панели элементов** , щелкнув вкладку **область элементов** . Кроме того, можно выбрать **область элементов** в меню **вид** или нажать клавиши **CTRL** + **ALT** + **X**.

Категория [миграции](../workflow-designer/migration-activity-designers.md) , содержащая действие, <xref:System.Activities.Statements.Interop> отображается в **области элементов** только в том случае, если проект предназначен для .NET Framework 4 (полная) или более поздней версии. При необходимости можно изменить версию платформы, для которой предназначен проект.

Конструктор действий **взаимодействия** можно перетащить из **области элементов** в конструктор рабочих процессов область, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence> . При удалении конструктора действия **взаимодействия** создается <xref:System.Activities.Statements.Interop> действие со значением **DisplayName** по умолчанию для взаимодействия. Можно изменить <xref:System.Activities.Activity.DisplayName%2A> в заголовке конструктора действий **взаимодействия** или в поле **DisplayName** сетки свойств.

Нажмите **кнопку, чтобы просмотреть** текст в поле **ActivityType** в конструкторе действий **взаимодействия**  или в сетке свойств, чтобы открыть диалоговое окно **Обзор и выбор типа .NET** . Отображаются только типы для действий рабочего процесса 3,0 или Workflow 3,5. То есть отображаются только типы, производные от <xref:System.Workflow.ComponentModel.Activity> . Дополнительные сведения об использовании этого поля для указания типа см. в разделе [диалоговое окно "Обзор и выбор типа .NET"](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md).

### <a name="the-interop-properties"></a>Свойства Interop

В следующей таблице показаны <xref:System.Activities.Statements.Interop> Свойства и описано, как они используются в конструкторе. Эти свойства можно изменить в сетке свойств или на поверхности конструктор рабочих процессов.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Неверно|Понятное имя действия <xref:System.Activities.Statements.Interop>. Значение по умолчанию — **Interop**. Хотя отображаемое имя не является обязательным, рекомендуется указать его.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|Верно|Задает тип действия, содержащегося в действии <xref:System.Activities.Statements.Interop>. Заданный тип должен быть производным от класса <xref:System.Workflow.ComponentModel.Activity>.|

## <a name="see-also"></a>См. также раздел

- [Миграция](../workflow-designer/migration-activity-designers.md)