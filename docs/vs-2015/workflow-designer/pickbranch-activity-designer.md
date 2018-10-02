---
title: Конструктор действия PickBranch | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 9c4e8156fffa975a511d0e6bc54ac139b2e10d81
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571236"
---
# <a name="pickbranch-activity-designer"></a>Конструктор действия PickBranch
Действие <xref:System.Activities.Statements.PickBranch> обеспечивает основанный на событиях путь выполнения в пределах действия <xref:System.Activities.Statements.Pick>, которое может быть вызвано входящим событием.  
  
## <a name="pickbranch"></a>PickBranch  
 Объекты <xref:System.Activities.Statements.PickBranch> содержатся в коллекции <xref:System.Activities.Statements.Pick.Branches%2A> действия <xref:System.Activities.Statements.Pick>. Каждое действие <xref:System.Activities.Statements.PickBranch> содержится в ветви действия <xref:System.Activities.Statements.Pick> и может быть выполнено в результате какого-то входящего события, которое выполняет роль триггера. Таким образом, [!INCLUDE[wfd1](../includes/wfd1-md.md)] обеспечивает моделирование потока управления на основе событий. Каждый участок кода <xref:System.Activities.Statements.PickBranch> содержит триггер <xref:System.Activities.Statements.PickBranch.Trigger%2A> и действие <xref:System.Activities.Statements.PickBranch.Action%2A>.  
  
### <a name="how-to-use-the-pick-activity-designer"></a>Использование конструктора действия подбора  
 **PickBranch** конструктора можно найти в **поток управления** категории **элементов**, который нажав **элементов** на вкладке [!INCLUDE[wfd2](../includes/wfd2-md.md)] (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X).  
  
 Два пустых <xref:System.Activities.Statements.PickBranch> объекты с отображаемыми именами **Branch1** и **Branch2** создаются по умолчанию в качестве элементов <xref:System.Activities.Statements.Pick> действия при **выбрать** Конструктор действия изначально перетаскивается на [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Соответствующие <xref:System.Activities.Statements.PickBranch.DisplayName%2A> значения свойств можно изменить в **PickBranch** заголовке конструктора или в **свойства** окна для каждой ветви.  
  
 Существует два способа добавления <xref:System.Activities.Statements.PickBranch> объектов в коллекцию <xref:System.Activities.Statements.Pick> объект: перетаскивания **PickBranch** конструктора из **элементов** или с помощью контекстного меню на в рамках **выбрать** конструктора:  
  
1.  **PickBranch** конструктор создает <xref:System.Activities.Statements.PickBranch> при перетаскивании из **элементов** в одну из ветвей **выбрать** конструктора действий на [!INCLUDE[wfd2](../includes/wfd2-md.md)] поверхности. Новые объекты <xref:System.Activities.Statements.PickBranch> могут помещаться внутри конструктора <xref:System.Activities.Statements.Pick> слева или справа от любых существующих элементов <xref:System.Activities.Statements.PickBranch>, уже содержащихся в коллекции. При перетаскивании **PickBranch** конструктора **выбрать** конструктора с помощью мыши **выбрать** конструктор использует вертикальную сине серую полосу, которая указывает, где <xref:System.Activities.Statements.PickBranch> будет добавлен в данном положении указателя мыши.  
  
2.  Щелкните правой кнопкой мыши **выбрать** конструктора действий (но не **PickBranch** конструктор) для получения контекстного меню и выберите **создать ветвь** Добавление нового <xref:System.Activities.Statements.PickBranch>. Обратите внимание, что новый <xref:System.Activities.Statements.PickBranch> добавляется справа от существующих <xref:System.Activities.Statements.PickBranch> объекты в **выбрать** конструктора.  
  
 **PickBranch** конструктора можно расширить для отображения **триггера** и **действие** либо свернуть, щелкнув двойные стрелки справа от заголовка. Изменить <xref:System.Activities.Statements.PickBranch.Trigger%2A> и <xref:System.Activities.Statements.PickBranch.Action%2A> каждого <xref:System.Activities.Statements.PickBranch> , перетащив действия в **триггера** и **действие** соответствующих конструкторов.  
  
 <xref:System.Activities.Statements.PickBranch> Объекты в <xref:System.Activities.Statements.Pick.Branches%2A> коллекцию <xref:System.Activities.Statements.Pick> объекта, можно изменить порядок сортировки с помощью перетаскивания их в новое расположение в пределах **выбрать** конструктора. **Выбрать** конструктор использует вертикальную сине серую полосу, которая указывает, где <xref:System.Activities.Statements.PickBranch> добавляется в данном положении указателя мыши.  
  
 Существует два способа удаления <xref:System.Activities.Statements.PickBranch>.  
  
1.  Выберите **PickBranch** конструкторе и удалите его.  
  
2.  Выберите **PickBranch** конструктора, щелкните правой кнопкой мыши, чтобы вызвать контекстное меню и выберите **удалить**.  
  
 Не забудьте выбрать **PickBranch** конструктора, как выбрать одно из действий внутри ее **триггера** или **действие** поля по ошибке Удаляет один из этих действий и не <xref:System.Activities.Statements.PickBranch> объекта.  
  
### <a name="pickbranch-properties-in-the-workflow-designer"></a>Свойства PickBranch в конструкторе рабочих процессов  
 В следующей таблице показаны наиболее полезные свойства действия <xref:System.Activities.Statements.PickBranch> и описано их использование в [!INCLUDE[wfd2](../includes/wfd2-md.md)].  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|Понятное имя, отображаемое в заголовке **PickBranch** конструктора. Значение по умолчанию - Branch.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|  
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|Каждый <xref:System.Activities.Statements.PickBranch> содержит действие <xref:System.Activities.Statements.PickBranch.Trigger%2A>, которое может вызвать <xref:System.Activities.Statements.PickBranch.Action%2A>.|  
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|Каждый <xref:System.Activities.Statements.PickBranch> содержит <xref:System.Activities.Statements.PickBranch.Action%2A>, которое выполняется при его запуске.|  
  
## <a name="see-also"></a>См. также  
 [Поток управления](../workflow-designer/control-flow-activity-designers.md)   
 [Действие Pick](http://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e)   
 [Использование действия Pick](http://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6)