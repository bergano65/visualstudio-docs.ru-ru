---
title: "Операнд оператора Throw должен быть производным от System.Exception | Microsoft Docs"
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
  - "vbc30665"
  - "bc30665"
helpviewer_keywords: 
  - "BC30665"
ms.assetid: 7c228087-39ea-4b30-a410-6ba711e67e5e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Операнд оператора Throw должен быть производным от System.Exception
Аргумент для `Throw` должен быть либо экземпляром `System.Exception`, либо экземпляром класса, производного от `System.Exception`.  
  
 **Идентификатор ошибки:** BC30665  
  
### Исправление ошибки  
  
-   Используйте аргумент, производный от `System.Exception`, как показано в приведенном ниже примере.  
  
    ```  
    Throw New System.Exception("This is an error.")  
    ```  
  
## См. также  
 [Оператор Throw](/dotnet/visual-basic/language-reference/statements/throw-statement)   
 [Оператор Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Класс Exception в Visual Basic](http://msdn.microsoft.com/ru-ru/9aac396f-34ca-4afb-8e6c-e523cb690ba9)   
 [Обработка исключений и ошибок в Visual Basic](http://msdn.microsoft.com/ru-ru/3e351e73-cf23-40ab-8b60-05794160529e)