---
title: "Конструктор действия CorrelationScope | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.CorrelationScope.UI"
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Конструктор действия CorrelationScope
Конструктор операций  **CorrelationScope** используется для создания и настройки действия <xref:System.ServiceModel.Activities.CorrelationScope>, которое обеспечивает неявное управление дочерними действиями обмена сообщениями с помощью объекта <xref:System.ServiceModel.Activities.CorrelationHandle>.  
  
## Действие CorrelationScope  
 Свойство <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> задает объект <xref:System.ServiceModel.Activities.CorrelationHandle>, используемый для управления дочерними действиями обмена сообщениями.Действия <xref:System.ServiceModel.Activities.Send> и <xref:System.ServiceModel.Activities.Receive>, содержащиеся в свойстве <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>, настроены на использование свойства <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> содержащегося действия <xref:System.ServiceModel.Activities.CorrelationScope> для выполнения корреляции.  
  
### Использование конструктора операций CorrelationScope  
 Конструктор операций  **CorrelationScope** можно найти в категории **Обмен сообщениямиОбласти элементов**, нажав на вкладку **Область элементов** по левую сторону [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(Иначе выберите **Область элементов** из меню **Просмотр**, или нажмите CTRL\+ALT\+X\).  
  
 Конструктор  **CorrelationScope** можно перетащить из **Области элементов** и поместить в область [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].Будет создано действие <xref:System.ServiceModel.Activities.CorrelationScope> со значением по умолчанию **DisplayName** для CorrelationScope.Значение <xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора операций  **CorrelationScope** либо в поле **DisplayName** окна **Свойства**.  
  
 Чтобы задать объект <xref:System.ServiceModel.Activities.CorrelationHandle>, используемый дочерними действиями обмена сообщений, нажмите кнопку с многоточием рядом с полем **CorrelatesWith** в окне **Свойства** для отображения диалогового окна **Редактор выражений**.Это свойство также можно задать в области конструктора операций.  
  
 Действия, ограниченные пределами корреляции, указываются путем переноса их конструкторов в поле **Тело** внутри конструктора **CorrelationScope**.  
  
### Свойства CorrelationScope  
 В следующей таблице показаны свойства <xref:System.ServiceModel.Activities.CorrelationScope> и описано их использование в конструкторе.Эти свойства можно изменить либо в окне **Свойства**, либо в области конструктора [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], а зачастую и в окне, и в области.  
  
|Имя свойства|Обязательное|Использование|  
|------------------|------------------|-------------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|Нет|Дополнительное понятное имя действия <xref:System.ServiceModel.Activities.InitializeCorrelation>.|  
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|Нет|Задает объект <xref:System.ServiceModel.Activities.CorrelationHandle>, используемый для управления дочерними действиями обмена сообщений.Если это свойство не задано, то действие <xref:System.ServiceModel.Activities.CorrelationScope> создает неявный объект <xref:System.ServiceModel.Activities.CorrelationHandle> автоматически.|  
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|Нет|Указывает действия в области корреляции.|  
  
## См. также  
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Send](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)