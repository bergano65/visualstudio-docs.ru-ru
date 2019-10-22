---
title: Конструктор действий конструктор рабочих процессов PickBranch
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a43fa99c9f5fe4fbb3cfe336efb983fced655f2a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650059"
---
# <a name="pickbranch-activity-designer"></a>Конструктор действия PickBranch

Действие <xref:System.Activities.Statements.PickBranch> обеспечивает основанный на событиях путь выполнения в пределах действия <xref:System.Activities.Statements.Pick>, которое может быть вызвано входящим событием.

## <a name="pickbranch"></a>PickBranch

Объекты <xref:System.Activities.Statements.PickBranch> содержатся в коллекции <xref:System.Activities.Statements.Pick.Branches%2A> действия <xref:System.Activities.Statements.Pick>. Каждое действие <xref:System.Activities.Statements.PickBranch> содержится в ветви действия <xref:System.Activities.Statements.Pick> и может быть выполнено в результате какого-то входящего события, которое выполняет роль триггера. Таким образом конструктор рабочих процессов обеспечивает моделирование потока управления на основе событий. Каждый участок кода <xref:System.Activities.Statements.PickBranch> содержит триггер <xref:System.Activities.Statements.PickBranch.Trigger%2A> и действие <xref:System.Activities.Statements.PickBranch.Action%2A>.

### <a name="how-to-use-the-pick-activity-designer"></a>Использование конструктора действия подбора

Доступ к конструктору **PickBranch** в категории " **поток управления** " **панели элементов**.

Два пустых <xref:System.Activities.Statements.PickBranch> объектов с отображаемыми именами **branch1** и **branch2** создаются по умолчанию как элементы действия <xref:System.Activities.Statements.Pick> при первоначальном удалении конструктора действия **выбора** в конструктор рабочих процессов. Эти соответствующие <xref:System.Activities.Statements.PickBranch.DisplayName%2A> значения свойств можно изменить в заголовке конструктора **PickBranch** или в окне **свойств** для каждой ветви.

Существует два способа добавления <xref:System.Activities.Statements.PickBranch> объектов в коллекцию <xref:System.Activities.Statements.Pick> объекта: перетаскивание конструктора **PickBranch** из **панели элементов**или с помощью контекстного меню в области конструктора **выборки** .

- Конструктор **PickBranch** создает <xref:System.Activities.Statements.PickBranch>, когда он перетаскивается из **панели элементов** и перемещается в одну из ветвей конструктора действия **выбора** на поверхности конструктор рабочих процессов. Новые объекты <xref:System.Activities.Statements.PickBranch> могут помещаться внутри конструктора <xref:System.Activities.Statements.Pick> слева или справа от любых существующих элементов <xref:System.Activities.Statements.PickBranch>, уже содержащихся в коллекции. При перетаскивании конструктора **PickBranch** в конструкторе **выбора** с помощью мыши конструктор **выборки** использует вертикальную синюю полосу серого цвета для указания места добавления <xref:System.Activities.Statements.PickBranch> для данного размещения мыши.

- Щелкните правой кнопкой мыши элемент **Выбор** конструктора действий (но не в конструкторе **PickBranch** ), чтобы получить контекстное меню, и выберите команду **создать ветвь** , чтобы добавить новый <xref:System.Activities.Statements.PickBranch>. Обратите внимание, что новый <xref:System.Activities.Statements.PickBranch> добавляется справа от существующих объектов <xref:System.Activities.Statements.PickBranch> в конструкторе **выбора** .

Конструктор **PickBranch** можно развернуть, чтобы отобразить поля **триггера** и **действия** или свернуть, щелкнув двойную заметку справа от их заголовков. Измените <xref:System.Activities.Statements.PickBranch.Trigger%2A> и <xref:System.Activities.Statements.PickBranch.Action%2A> каждого <xref:System.Activities.Statements.PickBranch>, удалив действия в окнах **триггера** и **действия** своих конструкторов.

Объекты <xref:System.Activities.Statements.PickBranch> в коллекции <xref:System.Activities.Statements.Pick.Branches%2A> объекта <xref:System.Activities.Statements.Pick> можно переупорядочить, перетащив их в новое место в конструкторе **выбора** . В конструкторе **выборки** используется вертикальная синяя полоса серого цвета для указания места добавления <xref:System.Activities.Statements.PickBranch> для данного размещения мыши.

Существует два способа удаления <xref:System.Activities.Statements.PickBranch>.

- Выберите конструктор **PickBranch** и удалите его.
- Выберите конструктор **PickBranch** , щелкните правой кнопкой мыши, чтобы получить контекстное меню, и выберите пункт **Удалить**.

Не забудьте выбрать конструктор **PickBranch** , выбрав одно из действий в окне **триггера** или **действия** , ошибочно удаляя одно из этих действий, а не объект <xref:System.Activities.Statements.PickBranch>.

### <a name="pickbranch-properties-in-the-workflow-designer"></a>Свойства PickBranch в конструкторе рабочих процессов

В следующей таблице показаны наиболее полезные <xref:System.Activities.Statements.PickBranch> свойства и описано, как их использовать в конструктор рабочих процессов.

|Имя свойства|Обязательное значение|Использование|
|-|--------------|-|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|Понятное имя, отображаемое в заголовке конструктора **PickBranch** . Значение по умолчанию - Branch.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|Каждый <xref:System.Activities.Statements.PickBranch> содержит действие <xref:System.Activities.Statements.PickBranch.Trigger%2A>, которое может вызвать <xref:System.Activities.Statements.PickBranch.Action%2A>.|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|Каждый <xref:System.Activities.Statements.PickBranch> содержит <xref:System.Activities.Statements.PickBranch.Action%2A>, которое выполняется при его запуске.|

## <a name="see-also"></a>См. также

- [Поток управления](../workflow-designer/control-flow-activity-designers.md)
- [Действие Pick](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Использование действия Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)