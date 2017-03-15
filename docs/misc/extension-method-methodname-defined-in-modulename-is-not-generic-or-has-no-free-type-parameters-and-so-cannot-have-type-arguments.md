---
title: "Метод расширения &quot;&lt;имя_метода&gt;&quot;, определенный в модуле &quot;&lt;имя_модуля&gt;&quot;, не является универсальным (или не имеет параметров свободного типа) и поэтому не может иметь аргументов типа. | Microsoft Docs"
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
  - "bc36907"
  - "vbc36907"
helpviewer_keywords: 
  - "BC36907"
ms.assetid: 45191e93-89d1-48ec-99a5-ff9661a2a6ee
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Метод расширения &quot;&lt;имя_метода&gt;&quot;, определенный в модуле &quot;&lt;имя_модуля&gt;&quot;, не является универсальным (или не имеет параметров свободного типа) и поэтому не может иметь аргументов типа.
Аргумент типа был указан при вызове метода расширения, который либо не имеет универсальных параметров, либо не имеет тех универсальных параметров, для которых тип еще не задан. Например, следующий код вызывает эту ошибку.  
  
```vb#  
' The extension method is not generic. <Extension()> _ Sub Example(ByVal str As String) ' Body of the Sub. End Sub  
```  
  
```vb#  
Dim str = "hi" '' The call to Example specifies a type argument. '' Not valid. 'str.Example(Of String)()  
```  
  
 **Идентификатор ошибки:** BC36907  
  
### Исправление ошибки  
  
-   Добавьте параметр типа к определению метода расширения.  
  
-   Удалите лишний аргумент типа из вызова процедуры.  
  
## См. также  
 [Методы расширения](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Универсальные процедуры в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)