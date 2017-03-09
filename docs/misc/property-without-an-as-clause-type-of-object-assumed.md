---
title: "Оператор без конструкции As; предполагаемый тип&#160;— Object | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BC42022"
  - "vbc42022"
helpviewer_keywords: 
  - "BC42022"
ms.assetid: 3379692b-8278-4488-878a-0afb76e554b1
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператор без конструкции As; предполагаемый тип&#160;— Object
В объявлении свойства нет предложения `As`.  
  
 Предложение `As` определяет тип данных, который будет связан с программным элементом. В [Оператор Property](/dotnet/visual-basic/language-reference/statements/property-statement) это задает тип данных значения, которое процедура `Get` свойства возвращает в вызывающий код. Если не включать предложение `As` в оператор `Property`, то по умолчанию для свойства будет задан тип данных `Object`.  
  
 По умолчанию данное сообщение является предупреждением. Дополнительные сведения о скрытии предупреждений и обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC42022  
  
### Исправление ошибки  
  
-   Вставьте предложение `As` в оператор `Property` для указания типа данных свойства.  
  
## См. также  
 [Процедуры свойств](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Оператор Property](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Оператор Get](/dotnet/visual-basic/language-reference/statements/get-statement)