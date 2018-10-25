---
title: Конструктор рабочих процессов - конструктор действия Persist
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51f74b5348c7e99824659ee713171bd71c5f522e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831346"
---
# <a name="persist-activity-designer"></a>Конструктор действия Persist

**Persist** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.Persist> действия.

## <a name="the-persist-activity"></a>Действие Persist

Действие <xref:System.Activities.Statements.Persist> сохраняет рабочий процесс на диск, если это возможно. Действие <xref:System.Activities.Statements.Persist> не может быть выполнено в зоне несохраняемости, например в пределах действия <xref:System.Activities.Statements.TransactionScope>. Если действие <xref:System.Activities.Statements.Persist> все же используется в области несохраняемости, то во время выполнения возникнет исключение.

### <a name="using-the-persist-activity-designer"></a>Использование конструктора действия Persist

**Persist** конструктора действий можно найти в **среды выполнения** категории **элементов**, который нажав **элементов** Вкладка (Кроме того, выберите **элементов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)

**Persist** конструктор действия можно перетащить из **элементов** и сбрасываться в область конструктора рабочих процессов, везде, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. При этом создается <xref:System.Activities.Statements.Persist> действие по умолчанию **DisplayName** из Persist. <xref:System.Activities.Activity.DisplayName%2A> Можно изменить в заголовке **Persist** конструктора действий или в **DisplayName** поле таблицы свойств.

### <a name="the-persist-properties"></a>Свойства Persist

В следующей таблице показаны свойства <xref:System.Activities.Statements.Persist> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств, и некоторые из них можно изменить на поверхности конструктора рабочих процессов.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.Persist>. По умолчанию используется значение Persist. Несмотря на то что использовать отображаемое имя необязательно, его все же рекомендуется задавать.|

## <a name="see-also"></a>См. также

- [Среда выполнения](../workflow-designer/runtime-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)