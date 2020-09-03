---
title: Конструктор сохранения действия | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 60a63dd4036863641646e85a89f5018cba786802
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672625"
---
# <a name="persist-activity-designer"></a>Конструктор действия Persist
Конструктор **сохранения** действий используется для создания и настройки <xref:System.Activities.Statements.Persist> действия.

## <a name="the-persist-activity"></a>Действие Persist
 Действие <xref:System.Activities.Statements.Persist> сохраняет рабочий процесс на диск, если это возможно. Действие <xref:System.Activities.Statements.Persist> не может быть выполнено в зоне несохраняемости, например в пределах действия <xref:System.Activities.Statements.TransactionScope>. Если действие <xref:System.Activities.Statements.Persist> все же используется в области несохраняемости, то во время выполнения возникнет исключение.

### <a name="using-the-persist-activity-designer"></a>Использование конструктора действия Persist
 Конструктор **хранимых** операций можно найти в категории **Среда выполнения** **панели элементов**, щелкнув вкладку **область элементов** (также можно выбрать **область элементов** в меню **вид** или CTRL + ALT + X).

 Конструктор действий по **сохранению** можно перетащить из **панели элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)] область, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence> . <xref:System.Activities.Statements.Persist>Будет создано действие с **отображаемым значением DisplayName** по умолчанию. <xref:System.Activities.Activity.DisplayName%2A>Можно изменить в заголовке конструктора **хранимых** операций или в поле **DisplayName** сетки свойств.

### <a name="the-persist-properties"></a>Свойства Persist
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Persist> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств, а некоторые из них можно изменить в области [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Неверно|Понятное имя действия <xref:System.Activities.Statements.Persist>. По умолчанию используется значение Persist. Несмотря на то что использовать отображаемое имя необязательно, его все же рекомендуется задавать.|

## <a name="see-also"></a>См. также:
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md) [среды выполнения](../workflow-designer/runtime-activity-designers.md)