---
title: "Параметры &lt;тип&gt; нельзя объявить как ParamArray | Microsoft Docs"
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
  - "bc33009"
  - "vbc33009"
helpviewer_keywords: 
  - "BC33009"
ms.assetid: faba9aef-ca4e-4c4d-934c-a3e3d3fa3c3e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Параметры &lt;тип&gt; нельзя объявить как ParamArray
Определение делегата, события или оператора объявляет параметр [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray).  
  
 Параметры `ParamArray` разрешены только в параметрах `Declare`, `Function`, `Property` и `Sub`.  
  
 **Идентификатор ошибки:** BC33009  
  
### Исправление ошибки  
  
-   Удалите ключевое слово `ParamArray` из списка параметров.  
  
-   При определении оператора можно достичь функциональности `ParamArray` с помощью ряда перегрузок.  
  
-   При определении делегата или события необходимо переработать всю логику этой части приложения. Нельзя использовать параметры [Optional](/dotnet/visual-basic/language-reference/modifiers/optional) и `ParamArray` или перегруженные версии для параметров делегата или события.  
  
## См. также  
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Процедуры операторов](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Оператор Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)