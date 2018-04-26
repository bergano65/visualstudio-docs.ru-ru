---
title: Конструктор рабочих процессов - конструктора операций Interop
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bb9eb5e8b2dbca57d28f9d350b769b5eaa90e2b2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="interop-activity-designer"></a>Конструктор действия Interop

**Взаимодействия** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.Interop> действия.

## <a name="the-interop-activity"></a>Действие Interop
 Действие <xref:System.Activities.Statements.Interop> управляет выполнением типов, являющихся производными от <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> в рабочем процессе.

### <a name="using-the-interop-activity-designer"></a>Использование конструктора операций Interop
 **Взаимодействия** конструктора действий можно найти в **миграции** категории **элементов**, который нажав **элементов**вкладка (либо выберите **элементов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)

 [Миграции](../workflow-designer/migration-activity-designers.md) категорию, которая содержит <xref:System.Activities.Statements.Interop> действия проявится только в **элементов** Если проект предназначен для полной .NET Framework 4.

 Для проектов C# можно переопределить проект для использования полного .NET Framework 4, щелкните правой кнопкой мыши проект в **обозревателе решений** и выбрав **свойства**. На **приложения** выберите **NET Framework 4** в диалоговом окне **требуемой версии .NET framework**. Выберите **Да** кнопку в **изменение версии .NET Framework** диалоговое окно, которое отображает запрос на подтверждение этого изменения.

 Для проектов VB можно переопределить проект на использование полного .NET Framework 4, щелкнув проект в **обозревателе решений** и выбрав **свойства**. На **компиляции** щелкните **Дополнительные параметры компиляции** кнопки. Выберите **.Net Framework 4** из **списке** и нажмите кнопку **ОК**. Нажмите кнопку **Да** кнопку в **изменение версии .NET Framework** диалоговое окно, которое отображает запрос на подтверждение этого изменения.

 **Взаимодействия** конструктора можно перетащить из **элементов** и удалена на поверхности конструктора рабочих процессов, везде, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. При этом создается <xref:System.Activities.Statements.Interop> действия по умолчанию **DisplayName** взаимодействия. <xref:System.Activities.Activity.DisplayName%2A> Можно изменить в заголовке **взаимодействия** конструктора или в **DisplayName** поле сетки свойств.

 Нажмите кнопку **нажмите, чтобы просмотреть...**  текста в **ActivityType** поле, либо на **взаимодействия** действия конструктора или в сетке свойств, чтобы открыть **Обзор и Выбор типа .net тип** диалоговое окно. Отображаются только типы действий рабочего процесса 3.0 или 3.5 (т. е. только типы, являющиеся производными от <xref:System.Workflow.ComponentModel.Activity>). Дополнительные сведения об использовании это поле для указания типа см. в разделе [Обзор и Выбор типа .NET-диалоговое](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md) раздела.

### <a name="the-interop-properties"></a>Свойства Interop
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Interop> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств или в рабочей области конструктора рабочих процессов.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.Interop>. Значение по умолчанию - Interop. Несмотря на то что использовать отображаемое имя необязательно, его все же рекомендуется задавать.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|Задает тип действия, содержащегося в действии <xref:System.Activities.Statements.Interop>. Заданный тип должен быть производным от класса <xref:System.Workflow.ComponentModel.Activity>.|

## <a name="see-also"></a>См. также

- [Миграция](../workflow-designer/migration-activity-designers.md)