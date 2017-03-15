---
title: "Статическая переменная &quot;&lt;имя_переменной&gt;&quot;, объявленная без предложения &quot;As&quot;; предполагается, что переменная имеет тип Object | Microsoft Docs"
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
  - "vbc42111"
  - "bc42111"
helpviewer_keywords: 
  - "BC42111"
ms.assetid: ca6b625c-21a5-45f7-ac67-282f6993a724
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Статическая переменная &quot;&lt;имя_переменной&gt;&quot;, объявленная без предложения &quot;As&quot;; предполагается, что переменная имеет тип Object
Для статических локальных переменных компилятор не выводит тип данных. В следующем примере \(для параметра `Option Strict` задано значение `Off`\) тип `m` будет `Object` независимо от того, задано ли для `Option Infer` значение `On` или `Off`. Локальный вывод типов не производится.  
  
```  
Sub Main() Static m = 10 End Sub  
```  
  
 По умолчанию данное сообщение является предупреждением. Дополнительные сведения о том, как скрыть предупреждения или как рассматривать предупреждения как ошибки, см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC42111  
  
### Устранение предупреждения  
  
-   Для статических локальных переменных укажите тип данных.  
  
     Например, если вы хотите, чтобы переменная `m` в предыдущем примере имела тип `Integer`, задайте этот тип в объявлении.  
  
    ```  
    Sub Main() Static m As Integer = 10 End Sub  
  
    ```  
  
## См. также  
 [Оператор Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [НЕ В СБОРКЕ. Практическое руководство: увеличение срока жизни переменной](http://msdn.microsoft.com/ru-ru/04e7c56c-1db0-4fe5-a678-859a39ec654b)   
 [Вывод локального типа](/dotnet/visual-basic/programming-guide/language-features/variables/local-type-inference)   
 [Option Infer \- оператор](/dotnet/visual-basic/language-reference/statements/option-infer-statement)   
 [Static](/dotnet/visual-basic/language-reference/modifiers/static)