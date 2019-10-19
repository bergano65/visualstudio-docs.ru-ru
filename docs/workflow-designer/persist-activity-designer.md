---
title: Конструктор действий по сохранению конструктор рабочих процессов
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 882a68e006ac139d717320b0b8b7ce4d75aceb38
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650121"
---
# <a name="persist-activity-designer"></a>Конструктор действия Persist

Конструктор **сохранения** действия используется для создания и настройки действия <xref:System.Activities.Statements.Persist>.

## <a name="the-persist-activity"></a>Действие Persist

Действие <xref:System.Activities.Statements.Persist> сохраняет рабочий процесс на диск, если это возможно. Действие <xref:System.Activities.Statements.Persist> не может быть выполнено в зоне несохраняемости, например в пределах действия <xref:System.Activities.Statements.TransactionScope>. Если вы используете <xref:System.Activities.Statements.Persist> действие в области без сохранения состояния, во время выполнения создается исключение.

### <a name="using-the-persist-activity-designer"></a>Использование конструктора действия Persist

Конструктор **хранимых** операций можно найти в категории **Среда выполнения** **панели элементов**, щелкнув вкладку **область элементов** (также можно выбрать **область элементов** в меню **вид** или CTRL + ALT + X).

Конструктор действий по **сохранению** можно перетащить из **панели элементов** в конструктор рабочих процессовную область, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. Будет создано действие <xref:System.Activities.Statements.Persist> с **отображаемым** по умолчанию значением DisplayName. @No__t_0 можно изменить в заголовке конструктора **сохраненных** действий или в поле **DisplayName** сетки свойств.

### <a name="the-persist-properties"></a>Свойства Persist

В следующей таблице показаны свойства <xref:System.Activities.Statements.Persist> и описано их использование в конструкторе. Эти свойства можно изменять в сетке свойств, а некоторые из них можно редактировать на конструктор рабочих процессов поверхности.

|Имя свойства|Обязательное значение|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.Persist>. По умолчанию используется значение Persist. Несмотря на то что использовать отображаемое имя необязательно, его все же рекомендуется задавать.|

## <a name="see-also"></a>См. также

- [Среда выполнения](../workflow-designer/runtime-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)