---
title: "Метод &quot;&lt;имя_процедуры&gt;&quot; для события &quot;&lt;имя_события&gt;&quot; нельзя пометить как совместимый с CLS, так как содержащий его тип &quot;&lt;имя_типа&gt;&quot; несовместим с CLS. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40053"
  - "bc40053"
helpviewer_keywords: 
  - "BC40053"
ms.assetid: 5f7aaf64-b5e6-4f97-9ebd-44cd4c7e8bf5
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Метод &quot;&lt;имя_процедуры&gt;&quot; для события &quot;&lt;имя_события&gt;&quot; нельзя пометить как совместимый с CLS, так как содержащий его тип &quot;&lt;имя_типа&gt;&quot; несовместим с CLS.
Пользовательское событие объявляет процедуру `AddHandler` или `RemoveHandler` и помечает ее как `<CLSCompliant(True)>`, но событие определено в типе, который помечен как `<CLSCompliant(False)>` или не помечен вообще.  
  
 При применении атрибута <xref:System.CLSCompliantAttribute> к программному элементу вы задаете для параметра `isCompliant` атрибута значение `True` или `False`, чтобы указать совместимость или несовместимость. Для этого параметра нет значения по умолчанию, и вы должны предоставить значение.  
  
 Если вы не примените <xref:System.CLSCompliantAttribute> к элементу, он считается несоответствующим требованиям.  
  
 По умолчанию данное сообщение является предупреждением. Сведения о сокрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC40053  
  
### Исправление ошибки  
  
-   Если требуется CLS\-совместимость, определите событие в CLS\-совместимом типе.  
  
-   Если требуется, чтобы это событие оставалось в своей иерархии вложений, удалите <xref:System.CLSCompliantAttribute> из его определения или пометьте его как `<CLSCompliant(False)>`.  
  
## См. также  
 [Практическое руководство. Объявление пользовательских событий для предотвращения блокировки](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Avoid%20Blocking%20\(Visual%20Basic\).md)   
 [Практическое руководство. Объявление пользовательских событий для экономии памяти](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Conserve%20Memory%20\(Visual%20Basic\).md)   
 [НЕ В СБОРКЕ. AddHandler и RemoveHandler](http://msdn.microsoft.com/ru-ru/a7a24bd2-519a-46fe-8a2c-2b9df2ca28ef)   
 [\<PAVE OVER\> Создание кода, совместимого с CLS](http://msdn.microsoft.com/ru-ru/4c705105-69a2-4e5e-b24e-0633bc32c7f3)