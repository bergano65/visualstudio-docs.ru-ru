---
title: "Диалоговое окно &#171;Инициализация корреляции&#187; | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "InitializeCorrelation.UI"
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Диалоговое окно &#171;Инициализация корреляции&#187;
Диалоговое окно **Инициализация корреляции** используется в [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] для изменения свойства <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> действия <xref:System.ServiceModel.Activities.InitializeCorrelation>.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)] см. раздел [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md).  
  
 В следующей таблице приведено описание элементов пользовательского интерфейса диалогового окна **Инициализация корреляции**.  
  
|Элемент пользовательского интерфейса|Описание|  
|------------------------------------------|--------------|  
|**Корреляция**|Дескриптор корреляции <xref:System.ServiceModel.Activities.CorrelationHandle> для инициализации.|  
|**Инициализация**|По ключу\/паре значений, содержащих данные инициализации.Это соответствует свойству <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>.Пример допустимого ключа\/пары значений: ключ с названием «OrderID», спаренный со значением, имя которого — «OrderID».|  
  
## Вызов диалогового окна «Инициализация корреляции»  
  
-   Щелкните **Просмотр** в конструкторе операций **InitializeCorrelation** или выберите операцию <xref:System.ServiceModel.Activities.InitializeCorrelation> в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], после чего нажмите кнопку с многоточием рядом со свойством <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> в таблице свойств.  
  
## См. также  
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)