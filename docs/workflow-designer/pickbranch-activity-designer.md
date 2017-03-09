---
title: "Конструктор действия PickBranch | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.PickBranch.UI"
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
caps.latest.revision: 10
caps.handback.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Конструктор действия PickBranch
Действие <xref:System.Activities.Statements.PickBranch> обеспечивает основанный на событиях путь выполнения в пределах действия <xref:System.Activities.Statements.Pick>, которое может быть вызвано входящим событием.  
  
## PickBranch  
 Объекты <xref:System.Activities.Statements.PickBranch> содержатся в коллекции <xref:System.Activities.Statements.Pick.Branches%2A> действия <xref:System.Activities.Statements.Pick>.Каждое действие <xref:System.Activities.Statements.PickBranch> содержится в ветви действия <xref:System.Activities.Statements.Pick> и может быть выполнено в результате какого\-то входящего события, которое выполняет роль триггера.Таким образом, [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] обеспечивает моделирование потока управления на основе событий.Каждый участок кода <xref:System.Activities.Statements.PickBranch> содержит триггер <xref:System.Activities.Statements.PickBranch.Trigger%2A> и действие <xref:System.Activities.Statements.PickBranch.Action%2A>.  
  
### Использование конструктора действия подбора  
 Конструктор действия **PickBranch** находится в категории **Поток управленияОбласти элементов**, для доступа к нему необходимо перейти на вкладку **Область элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(либо выбрать пункт **Область элементов** в меню **Вид** или нажать CTRL\+ALT\+X\).  
  
 Если конструктор действия **Pick** первоначально перетаскивается на [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], то по умолчанию в качестве элементов действия <xref:System.Activities.Statements.Pick> создаются два пустых объекта <xref:System.Activities.Statements.PickBranch> с отображаемыми именами **Branch1** и **Branch2**.Соответствующие значения свойства <xref:System.Activities.Statements.PickBranch.DisplayName%2A> можно изменить в заголовке конструктора действий **PickBranch** или в окне **Свойства** для каждой ветви.  
  
 Объекты <xref:System.Activities.Statements.PickBranch> можно добавить в коллекцию <xref:System.Activities.Statements.Pick> объекта двумя способами: перетащить конструктор **PickBranch** из **Области элементов** или воспользоваться контекстным меню в области конструктора **Pick**.  
  
1.  При перетаскивании из **Области элементов** в одну из ветвей конструктора действия **Pick** области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] конструктор действия **PickBranch** создает действие <xref:System.Activities.Statements.PickBranch>.Новые объекты <xref:System.Activities.Statements.PickBranch> могут помещаться внутри конструктора <xref:System.Activities.Statements.Pick> слева или справа от любых существующих элементов <xref:System.Activities.Statements.PickBranch>, уже содержащихся в коллекции.При перетаскивании конструктора действия **PickBranch** в конструктор **Pick** с помощью мыши конструктор **Pick** использует вертикальную сине\-серую полосу, которая указывает, куда будет добавлено действие <xref:System.Activities.Statements.PickBranch> в данном положении указателя мыши.  
  
2.  Щелкните правой кнопкой мыши конструктор действия **Pick** \(но не конструктор **PickBranch**\), чтобы открыть контекстное меню, и выберите пункт **Создать ветвь**, чтобы добавить новое действие <xref:System.Activities.Statements.PickBranch>.Обратите внимание, что новый <xref:System.Activities.Statements.PickBranch> добавляется справа от существующих <xref:System.Activities.Statements.PickBranch> объектов в конструкторе **Pick**.  
  
 Конструктор действия **PickBranch** можно расширить для отображения полей **Триггер** и **Действие** либо свернуть, щелкнув двойные стрелки справа от заголовков.Измените <xref:System.Activities.Statements.PickBranch.Trigger%2A> и <xref:System.Activities.Statements.PickBranch.Action%2A> для каждого <xref:System.Activities.Statements.PickBranch>, перетащив действия в поля **Триггер** и **Действие** соответствующих конструкторов.  
  
 Объекты <xref:System.Activities.Statements.PickBranch> в коллекции <xref:System.Activities.Statements.Pick.Branches%2A> объекта <xref:System.Activities.Statements.Pick> можно переупорядочить перетаскиванием на новое место в пределах конструктора **Pick**.Конструктор действия **Pick** использует вертикальную сине\-серую полосу, которая указывает, где будет добавлен <xref:System.Activities.Statements.PickBranch> в данном положении указателя мыши.  
  
 Существует два способа удаления <xref:System.Activities.Statements.PickBranch>.  
  
1.  Выберите конструктор **PickBranch** и удалите его.  
  
2.  Выберите конструктор **PickBranch**, щелкните его правой кнопкой мыши, чтобы вызвать контекстное меню, и выберите команду **Удалить**.  
  
 Убедитесь, что выбран конструктор **PickBranch**, поскольку если по ошибке выбрано одно из действий в полях **Триггер** или **Действие**, то будет удалено оно, а не объект <xref:System.Activities.Statements.PickBranch>.  
  
### Свойства PickBranch в конструкторе рабочих процессов  
 В следующей таблице показаны наиболее полезные свойства действия <xref:System.Activities.Statements.PickBranch> и описано их использование в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Имя свойства|Обязательное|Использование|  
|------------------|------------------|-------------------|  
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|Нет|В заголовке конструктора действия **PickBranch** отображается понятное имя.Значение по умолчанию — Branch.<br /><br /> Несмотря на то, что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|  
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|Каждый <xref:System.Activities.Statements.PickBranch> содержит действие <xref:System.Activities.Statements.PickBranch.Trigger%2A>, которое может вызвать <xref:System.Activities.Statements.PickBranch.Action%2A>.|  
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|Каждый <xref:System.Activities.Statements.PickBranch> содержит <xref:System.Activities.Statements.PickBranch.Action%2A>, которое выполняется при его запуске.|  
  
## См. также  
 [Управление потоком](../workflow-designer/control-flow-activity-designers.md)   
 [Выбор действия](../Topic/Pick%20Activity.md)   
 [Использование действия Pick](../Topic/Using%20the%20Pick%20Activity.md)