---
title: "Ожидался идентификатор с предшествующей перед ним точкой | Microsoft Docs"
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
  - "bc36576"
  - "vbc36576"
helpviewer_keywords: 
  - "BC36576"
ms.assetid: 02217cc4-8972-4a6d-97a6-4ecbb7399af2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ожидался идентификатор с предшествующей перед ним точкой
В список инициализаторов объявления анонимных типов было включено значение без имени свойства; на основе этого значения нельзя определить имя свойства.  
  
```  
' Not valid. ' Dim anon1 = New With {.grade = 100, 95}  
```  
  
 **Идентификатор ошибки:** BC36576  
  
### Исправление ошибки  
  
-   Укажите имя свойства для каждого значения в списке инициализаторов, как показано в следующем коде:  
  
    ```  
    Dim anon2 = New With {.grade1 = 100, .grade2 = 95}  
    ```  
  
## См. также  
 [Инициализаторы объектов: именованные и анонимные типы](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Практическое руководство. Объявление экземпляра анонимного типа \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/119f616c-9bcd-4731-ac00-4285be5959f7)   
 [Практическое руководство. Выведение имен свойств и типов в объявлениях анонимных типов](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)