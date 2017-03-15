---
title: "Объявление пространства имен с префиксом не может содержать пустое значение в литералах XML | Microsoft Docs"
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
  - "bc31184"
  - "vbc31184"
helpviewer_keywords: 
  - "BC31184"
ms.assetid: dde656b4-df3b-4a2e-8871-4e14832ca778
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Объявление пространства имен с префиксом не может содержать пустое значение в литералах XML
Объявление пространства имен XML литерале XML не включает значение пространства имен. Например, приведенный ниже код вызывает эту ошибку.  
  
```vb#  
Dim book = <book xmlns:ns=""/>  
```  
  
 **Идентификатор ошибки:** BC31184  
  
### Исправление ошибки  
  
-   Включите допустимое пространство имен в объявление пространства имен XML или удалите объявление пространства имен XML из литерала XML.  
  
     В качестве альтернативы можно использовать оператор `Imports` для определения префикса пустого пространства имен. Пример:  
  
    ```vb#  
    Imports <xmlns:ns="">  
    ```  
  
## См. также  
 [XML\-литералы](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)   
 [Оператор Imports \(пространство имен XML\)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)