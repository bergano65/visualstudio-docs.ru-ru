---
title: "Параметры &lt;тип&gt; нельзя объявить как &quot;Optional&quot;. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc33010"
  - "vbc33010"
helpviewer_keywords: 
  - "BC33010"
ms.assetid: ec4023e7-9ba6-4532-a6b9-4ae6b4f9063a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Параметры &lt;тип&gt; нельзя объявить как &quot;Optional&quot;.
Определение делегата, события или оператора объявляет параметр [Optional](/dotnet/visual-basic/language-reference/modifiers/optional).  
  
 Параметры `Optional` разрешены только в параметрах `Declare`, `Function`, `Property` и `Sub`.  
  
 **Идентификатор ошибки:** BC33010  
  
### Исправление ошибки  
  
-   Удалите ключевое слово `Optional` из списка параметров.  
  
-   При определении оператора можно достичь функциональности `Optional` с помощью ряда перегрузок.  
  
-   При определении делегата или события необходимо переработать всю логику этой части приложения. Нельзя использовать параметры `Optional` и [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray) или перегруженные версии для параметров делегата или события.  
  
## См. также  
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Процедуры операторов](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Оператор Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)