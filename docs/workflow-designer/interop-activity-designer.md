---
title: Конструктор рабочих процессов - конструктор действия Interop
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e020e2f4e1ffae9c0e979f2230ff845b1cda203e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55942704"
---
# <a name="interop-activity-designer"></a>Конструктор действия Interop

**Взаимодействия** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.Interop> действия.

## <a name="the-interop-activity"></a>Действие Interop

Действие <xref:System.Activities.Statements.Interop> управляет выполнением типов, являющихся производными от <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> в рабочем процессе.

### <a name="use-the-interop-activity-designer"></a>Использование конструктора операций Interop

**Взаимодействия** конструктора действий можно найти в **миграции** категории **элементов**, который нажав **элементов**вкладки. Можно также выбрать **элементов** из **представление** меню или нажмите клавишу **Ctrl**+**Alt** + **X**.

[Миграции](../workflow-designer/migration-activity-designers.md) категории, содержащей <xref:System.Activities.Statements.Interop> действия выводится только в **элементов** Если проект нацелен на полной .NET Framework 4.

Для проектов C#, можно повторно создавать проект для использования полной платформы .NET Framework 4, щелкните правой кнопкой мыши проект в **обозревателе решений** и выбрав **свойства**. На **приложения** выберите **NET Framework 4** в диалоговом окне **требуемой версии .NET framework**. Выберите **Да** для подтверждения изменения.

Для проектов Visual Basic, можно повторно создавать проект для использования полной платформы .NET Framework 4, щелкните правой кнопкой мыши проект в **обозревателе решений** и выбрав **свойства**. На **компиляции** щелкните **Дополнительные параметры компиляции** кнопки. Выберите **.Net Framework 4** из **списке требуемой версии**, а затем нажмите кнопку **ОК**. Выберите **Да** для подтверждения изменения.

**Взаимодействия** конструктор действия можно перетащить из **элементов** и перетащенной в область конструктора рабочих процессов, везде, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. Удаление **взаимодействия** конструктора действий создает <xref:System.Activities.Statements.Interop> действие по умолчанию **DisplayName** взаимодействия. Можно изменить <xref:System.Activities.Activity.DisplayName%2A> в заголовке **взаимодействия** конструктора действий, или в **DisplayName** поле таблицы свойств.

Нажмите кнопку **нажмите, чтобы просмотреть** текста в **ActivityType** поле, либо на **взаимодействия** действие конструктора или в сетке свойств, чтобы открыть **Обзор и Выберите .net тип** диалоговое окно. Отображаются только типы рабочего процесса 3.0 или 3.5 действий. То есть только типы, производные от <xref:System.Workflow.ComponentModel.Activity> отображаются. Дополнительные сведения об использовании это поле для указания типа, см. в разделе [Обзор и Выбор типа .NET диалоговое окно](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md).

### <a name="the-interop-properties"></a>Свойства Interop

В следующей таблице показаны <xref:System.Activities.Statements.Interop> свойства и описывает, как они используются в конструкторе. Эти свойства можно изменить в таблице свойств или в рабочей области конструктора рабочих процессов.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.Interop>. Значение по умолчанию — **взаимодействия**. Несмотря на то, что отображаемое имя не является обязательной, рекомендуется предоставить один.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|Да|Задает тип действия, содержащегося в действии <xref:System.Activities.Statements.Interop>. Заданный тип должен быть производным от класса <xref:System.Workflow.ComponentModel.Activity>.|

## <a name="see-also"></a>См. также

- [Миграция](../workflow-designer/migration-activity-designers.md)