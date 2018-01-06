---
title: "Конструктор действия Pickbranch | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
caps.latest.revision: "10"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: d583c662de31b990982b78d876bc0046e89089d7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="pickbranch-activity-designer"></a>Конструктор действия PickBranch
Действие <xref:System.Activities.Statements.PickBranch> обеспечивает основанный на событиях путь выполнения в пределах действия <xref:System.Activities.Statements.Pick>, которое может быть вызвано входящим событием.  
  
## <a name="pickbranch"></a>PickBranch  
 Объекты <xref:System.Activities.Statements.PickBranch> содержатся в коллекции <xref:System.Activities.Statements.Pick.Branches%2A> действия <xref:System.Activities.Statements.Pick>. Каждое действие <xref:System.Activities.Statements.PickBranch> содержится в ветви действия <xref:System.Activities.Statements.Pick> и может быть выполнено в результате какого-то входящего события, которое выполняет роль триггера. Таким образом, [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] обеспечивает моделирование потока управления на основе событий. Каждый участок кода <xref:System.Activities.Statements.PickBranch> содержит триггер <xref:System.Activities.Statements.PickBranch.Trigger%2A> и действие <xref:System.Activities.Statements.PickBranch.Action%2A>.  
  
### <a name="how-to-use-the-pick-activity-designer"></a>Использование конструктора действия подбора  
 **PickBranch** можно найти в **поток управления** категории **элементов**, который нажав **элементов** на вкладке [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X).  
  
 Два пустых <xref:System.Activities.Statements.PickBranch> объектов с именами отображения **Branch1** и **Branch2** по умолчанию создаются как элементы <xref:System.Activities.Statements.Pick> действия при **выбора** изначально перетащить конструктор действия на [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. Соответствующие <xref:System.Activities.Statements.PickBranch.DisplayName%2A> значения свойств можно изменить в **PickBranch** заголовке конструктора или в **свойства** для каждой ветви.  
  
 Существует два способа добавления <xref:System.Activities.Statements.PickBranch> объекты в коллекцию <xref:System.Activities.Statements.Pick> объектов: перетаскивание **PickBranch** конструктора из **элементов** или с помощью контекстного меню на в пределах **выбора** конструктора:  
  
1.  **PickBranch** конструктор создает <xref:System.Activities.Statements.PickBranch> при его перетаскивании из **элементов** и перетащить в одной ветви **выбора** конструктора операций в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] поверхности. Новые объекты <xref:System.Activities.Statements.PickBranch> могут помещаться внутри конструктора <xref:System.Activities.Statements.Pick> слева или справа от любых существующих элементов <xref:System.Activities.Statements.PickBranch>, уже содержащихся в коллекции. При перетаскивании **PickBranch** конструктора **выбора** конструктора с помощью мыши **выбора** конструктор использует вертикальную сине серую полосу, чтобы указать, где <xref:System.Activities.Statements.PickBranch> будет добавлен в данном положении указателя мыши.  
  
2.  Щелкните правой кнопкой мыши **выбора** конструктора действий (, но не внутри **PickBranch** конструктор) для получения контекстного меню и выберите **создать ветвь** для добавления новых <xref:System.Activities.Statements.PickBranch>. Обратите внимание, что новый <xref:System.Activities.Statements.PickBranch> добавляется справа от существующих <xref:System.Activities.Statements.PickBranch> объекты в **выбора** конструктора.  
  
 **PickBranch** конструктор можно развернуть, чтобы отобразить **триггер** и **действия** либо свернуть, щелкнув двойные стрелки справа от заголовков. Изменить <xref:System.Activities.Statements.PickBranch.Trigger%2A> и <xref:System.Activities.Statements.PickBranch.Action%2A> каждого <xref:System.Activities.Statements.PickBranch> , перетащив действия в **триггер** и **действия** соответствующих конструкторов.  
  
 <xref:System.Activities.Statements.PickBranch> Объекты в <xref:System.Activities.Statements.Pick.Branches%2A> коллекцию <xref:System.Activities.Statements.Pick> можно переупорядочить с помощью перетаскивания их в новое место в пределах **выбора** конструктора. **Выбора** конструктор использует вертикальную сине серую полосу, чтобы указать, где <xref:System.Activities.Statements.PickBranch> добавляется в данном положении указателя мыши.  
  
 Существует два способа удаления <xref:System.Activities.Statements.PickBranch>.  
  
1.  Выберите **PickBranch** конструктора и удалите его.  
  
2.  Выберите **PickBranch** конструктора, щелкните правой кнопкой мыши, чтобы открыть контекстное меню и выберите пункт **удалить**.  
  
 Не забудьте установить **PickBranch** конструктора, как при выборе одного из действий внутри его **триггер** или **действие** поля по ошибке выбрано одно из этих действий и не <xref:System.Activities.Statements.PickBranch> объекта.  
  
### <a name="pickbranch-properties-in-the-workflow-designer"></a>Свойства PickBranch в конструкторе рабочих процессов  
 В следующей таблице показаны наиболее полезные свойства действия <xref:System.Activities.Statements.PickBranch> и описано их использование в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|Понятное имя, отображаемое в заголовке **PickBranch** конструктора. Значение по умолчанию - Branch.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|  
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|Каждый <xref:System.Activities.Statements.PickBranch> содержит действие <xref:System.Activities.Statements.PickBranch.Trigger%2A>, которое может вызвать <xref:System.Activities.Statements.PickBranch.Action%2A>.|  
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|Каждый <xref:System.Activities.Statements.PickBranch> содержит <xref:System.Activities.Statements.PickBranch.Action%2A>, которое выполняется при его запуске.|  
  
## <a name="see-also"></a>См. также  
 [Поток управления](../workflow-designer/control-flow-activity-designers.md)   
 [Действие Pick](/dotnet/framework/windows-workflow-foundation/pick-activity)   
 [Использование действия Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)