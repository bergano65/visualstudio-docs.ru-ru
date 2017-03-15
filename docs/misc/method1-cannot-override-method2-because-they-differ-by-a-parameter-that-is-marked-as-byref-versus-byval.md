---
title: "&quot;&lt;метод1&gt;&quot; не может переопределять &quot;&lt;метод2&gt;&quot;, так как один из параметров в одном случае помечен как &quot;ByRef&quot;, а в другом&#160;— как &quot;ByVal&quot; | Microsoft Docs"
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
  - "vbc30398"
  - "bc30398"
helpviewer_keywords: 
  - "BC30398"
ms.assetid: 78d62276-4ad9-4876-8c35-a30c9c195638
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;метод1&gt;&quot; не может переопределять &quot;&lt;метод2&gt;&quot;, так как один из параметров в одном случае помечен как &quot;ByRef&quot;, а в другом&#160;— как &quot;ByVal&quot;
Предпринята попытка переопределения одного метода другим. При этом методы отличаются тем, что в первом случае параметр помечен как `ByRef`, а во втором — как `ByVal`. Переопределяемые члены должны иметь те же аргументы, что и члены, унаследованные от базового класса.  
  
 **Идентификатор ошибки:** BC30398  
  
### Исправление ошибки  
  
-   Убедитесь в том, что оба параметра помечены либо как `ByRef`, либо как `ByVal`.  
  
## См. также  
 [НЕ В СБОРКЕ. Переопределение свойств и методов](http://msdn.microsoft.com/ru-ru/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Передача аргументов по значению и по ссылке](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)