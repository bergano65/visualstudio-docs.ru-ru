---
title: "Оператор &quot;&lt;символ_оператора&gt;&quot; не возвращает значение во всех путях кода | Microsoft Docs"
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
  - "vbc42106"
  - "bc42106"
helpviewer_keywords: 
  - "BC42106"
ms.assetid: 175b2bc9-5233-462d-97de-9d97b003cc46
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператор &quot;&lt;символ_оператора&gt;&quot; не возвращает значение во всех путях кода
Оператор "\<символ\_оператора\>" не возвращает значение во всех путях кода. Во время выполнения может возникнуть исключение, связанное с пустой ссылкой, когда используется результат.  
  
 Процедура оператора содержит по крайней мере один возможный путь во всем коде, который не возвращает значение.  
  
 Вы можете возвращать значение из процедуры оператора, только включив его в [Оператор Return](/dotnet/visual-basic/language-reference/statements/return-statement).  
  
 Если управление передается в инструкцию `End Operator`, процедура оператора возвращает значение по умолчанию типа данных свойства. Дополнительные сведения см. в разделе "Поведение" статьи [Оператор Function](/dotnet/visual-basic/language-reference/statements/function-statement).  
  
 По умолчанию данное сообщение является предупреждением. Дополнительные сведения о скрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC42106  
  
### Исправление ошибки  
  
-   Проверьте логику потока управления и убедитесь, что каждый возможный путь заканчивается инструкцией `Return`. В частности, последней инструкцией перед `End Operator` должна быть инструкция `Return`.  
  
## См. также  
 [Процедуры операторов](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Оператор Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)