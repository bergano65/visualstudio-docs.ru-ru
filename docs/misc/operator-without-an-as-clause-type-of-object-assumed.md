---
title: "Оператор без предложения As; предполагаемый тип — Object. | Microsoft Docs"
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
  - "vbc41005"
  - "bc41005"
helpviewer_keywords: 
  - "BC41005"
ms.assetid: 42be84ed-7aa6-4ac0-9dd4-663e90f13e09
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператор без предложения As; предполагаемый тип — Object.
Процедура оператора не указывает предложение `As`.  
  
 Предложение `As` определяет тип данных, который будет связан с программным элементом. В [Оператор Operator](/dotnet/visual-basic/language-reference/statements/operator-statement) это задает тип данных значения, которое процедура оператора возвращает в вызывающий код. Если предложение `As` не включено в оператор `Operator`, то по умолчанию для возвращаемых данных будет задан тип `Object`.  
  
 По умолчанию данное сообщение является предупреждением. Сведения о скрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC41005  
  
### Исправление ошибки  
  
-   Включите предложение `As` в оператор `Operator` для указания типа данных переменной.  
  
## См. также  
 [Процедуры операторов](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Оператор Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)