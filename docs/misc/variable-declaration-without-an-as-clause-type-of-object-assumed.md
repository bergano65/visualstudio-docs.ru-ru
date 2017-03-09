---
title: "Переменная объявлена без предложения &quot;As&quot;; предполагается тип Object. | Microsoft Docs"
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
  - "BC42020"
  - "vbc42020"
helpviewer_keywords: 
  - "BC42020"
ms.assetid: 9422b16d-39b5-4d49-b697-608226ccafea
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Переменная объявлена без предложения &quot;As&quot;; предполагается тип Object.
В объявлении переменной не указано предложение `As`.  
  
 Предложение `As` определяет тип данных, который будет связан с программным элементом. В [Оператор Dim](/dotnet/visual-basic/language-reference/statements/dim-statement) он указывает тип данных переменной или переменных. Если предложение `As` не включено в оператор `Dim`, то по умолчанию для переменной будет задан тип данных `Object`.  
  
 По умолчанию данное сообщение является предупреждением. Сведения о скрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC42020  
  
### Исправление ошибки  
  
-   Включите предложение `As` в оператор `Dim` для указания типа данных переменной.  
  
## См. также  
 [Оператор Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [Объявление переменной](/dotnet/visual-basic/programming-guide/language-features/variables/variable-declaration)