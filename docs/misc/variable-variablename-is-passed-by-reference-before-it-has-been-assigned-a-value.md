---
title: "Переменная &quot;&lt;variablename&gt;&quot; передана по ссылке до того, как ей было назначено значение | Microsoft Docs"
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
  - "vbc42030"
  - "BC42030"
helpviewer_keywords: 
  - "BC42030"
ms.assetid: 8f1aae99-f032-4fdf-b6dc-3360cc5b94de
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Переменная &quot;&lt;variablename&gt;&quot; передана по ссылке до того, как ей было назначено значение
Переменная "\<variablename\>" передана по ссылке до того, как ей было назначено значение. Во время выполнения может возникнуть исключение "пустая ссылка".  
  
 Вызов процедуры передает переменную в качестве аргумента `ByRef` до того, как переменной было назначено значение.  
  
 Если переменной никогда не назначалось значение, она содержит значение по умолчанию для своего типа данных. Для ссылочного типа данных значение по умолчанию — [Nothing](/dotnet/visual-basic/language-reference/nothing). Чтение переменной ссылки, которая имеет значение `Nothing`, в некоторых случаях может привести к исключению <xref:System.NullReferenceException>.  
  
 Передача аргумента в параметр `ByRef` процедуры может привести к изменению этой процедурой переменной, представляющей аргумент.  
  
 По умолчанию данное сообщение является предупреждением. Дополнительные сведения о скрытии предупреждений и обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC42030  
  
### Исправление ошибки  
  
-   Если вы предполагаете, что процедура должна назначать значение переменной с помощью аргумента `ByRef`, и не важно, содержит ли уже переменная значение, то никакие действия не требуются.  
  
-   Если логика в процедуре считывает аргумент перед назначением ему какого\-либо значения и если переменная имеет тип значения, убедитесь, что логика процедуры не зависит от того, содержит ли переменная значение по умолчанию или нет.  
  
-   Если логика в процедуре считывает аргумент перед назначением ему какого\-либо значения и если переменная имеет ссылочный тип, убедитесь, что логика процедуры может обрабатывать значение `Nothing`. Например, она может использовать [Оператор Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement) для перехвата <xref:System.NullReferenceException>.  
  
## См. также  
 [Оператор Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [Типы значений и ссылочные типы](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)   
 [Передача аргументов по значению и по ссылке](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)   
 [ByRef](/dotnet/visual-basic/language-reference/modifiers/byref)   
 [Объявление переменной](/dotnet/visual-basic/programming-guide/language-features/variables/variable-declaration)   
 [Устранение неполадок, связанных с переменными](/dotnet/visual-basic/programming-guide/language-features/variables/troubleshooting-variables)