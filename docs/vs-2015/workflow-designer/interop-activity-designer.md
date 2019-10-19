---
title: Конструктор действий взаимодействия | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 994d7776ff7c32f8dd309e667597550637ef2b5a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659038"
---
# <a name="interop-activity-designer"></a>Конструктор действия Interop
Конструктор действий **взаимодействия** используется для создания и настройки действия <xref:System.Activities.Statements.Interop>.

## <a name="the-interop-activity"></a>Действие Interop
 Действие <xref:System.Activities.Statements.Interop> управляет выполнением типов, являющихся производными от <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> в рабочем процессе.

### <a name="using-the-interop-activity-designer"></a>Использование конструктора операций Interop
 Конструктор действий **взаимодействия** можно найти в категории " **Миграция** " **панели элементов**, щелкнув вкладку " **область элементов** " (или выбрав пункт " **область элементов** " в меню " **вид** " или нажав клавиши CTRL + ALT + X).

 Категория [миграции](../workflow-designer/migration-activity-designers.md) , содержащая действие <xref:System.Activities.Statements.Interop>, отображается на **панели элементов** только в том случае, если проект предназначен для полной [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)].

 Для C# проектов можно перенацелить проект для использования полного [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)], щелкнув правой кнопкой мыши проект в **Обозреватель решений** и выбрав пункт **Свойства**. На вкладке **приложение** выберите параметр **NET Framework 4** в **целевой платформе**. Нажмите кнопку **Да** в диалоговом окне **изменения целевой платформы** , в котором отображается запрос на подтверждение изменения.

 Для проектов VB можно перенацелить проект для использования полного [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)], щелкнув правой кнопкой мыши проект в **Обозреватель решений** и выбрав пункт **свойства**. На вкладке **Компиляция** нажмите кнопку **Дополнительные параметры компиляции** . Выберите **.NET Framework 4** из **списка Целевая платформа** и нажмите кнопку **ОК**. Нажмите кнопку **Да** в диалоговом окне **изменения целевой платформы** , в котором отображается запрос на подтверждение изменения.

 Конструктор действий **взаимодействия** можно перетащить из **панели элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)] область, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. При этом создается действие <xref:System.Activities.Statements.Interop> со значением **DisplayName** по умолчанию для Interop. @No__t_0 можно изменить в заголовке конструктора действий **взаимодействия** или в поле **DisplayName** сетки свойств.

 Нажмите **кнопку для просмотра...** текст в поле **ActivityType** в конструкторе действий **взаимодействия** или в сетке свойств, чтобы открыть диалоговое окно **Обзор и выбор типа .NET** . Отображаются только типы действий рабочего процесса 3.0 или 3.5 (т. е. только типы, являющиеся производными от <xref:System.Workflow.ComponentModel.Activity>). [!INCLUDE[crabout](../includes/crabout-md.md)] использовании этого поля для указания типа см. раздел [диалоговое окно "Обзор и выбор типа .NET"](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md) .

### <a name="the-interop-properties"></a>Свойства Interop
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Interop> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств или в области [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Имя свойства|Обязательное значение|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.Interop>. Значение по умолчанию - Interop. Несмотря на то что использовать отображаемое имя необязательно, его все же рекомендуется задавать.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|Задает тип действия, содержащегося в действии <xref:System.Activities.Statements.Interop>. Заданный тип должен быть производным от класса <xref:System.Workflow.ComponentModel.Activity>.|

## <a name="see-also"></a>См. также раздел
 [Миграция](../workflow-designer/migration-activity-designers.md)