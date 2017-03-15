---
title: "Функция без предложения As; предполагаемый тип возврата — Object | Microsoft Docs"
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
  - "BC42021"
  - "vbc42021"
helpviewer_keywords: 
  - "BC42021"
ms.assetid: c1efadf1-fba3-437b-a311-240c4d07d894
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Функция без предложения As; предполагаемый тип возврата — Object
Процедура `Function` не указывает предложение `As`.  
  
 Предложение `As` определяет тип данных, который будет связан с программным элементом. В [Оператор Function](/dotnet/visual-basic/language-reference/statements/function-statement) это задает тип данных значения, которое процедура `Function` возвращает в вызывающий код. Если предложение `As` не включено в оператор `Function`, то по умолчанию для возвращаемых данных будет задан тип `Object`.  
  
 По умолчанию данное сообщение является предупреждением. Сведения о скрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC42021  
  
### Исправление ошибки  
  
-   Включите предложение `As` в оператор `Function` для указания типа данных переменной.  
  
## См. также  
 [Процедуры Function](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)