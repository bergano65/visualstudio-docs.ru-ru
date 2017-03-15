---
title: "Тип параметра &quot;Set&quot; должен совпадать с типом содержащего его свойства. | Microsoft Docs"
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
  - "vbc31064"
  - "bc31064"
helpviewer_keywords: 
  - "BC31064"
ms.assetid: f0b8310d-68a1-4989-ac64-03b1861528ad
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Тип параметра &quot;Set&quot; должен совпадать с типом содержащего его свойства.
Тип параметра для процедуры свойства `Set` отличается от свойства, к которому принадлежит.  
  
 **Идентификатор ошибки:** BC31064  
  
### Исправление ошибки  
  
-   Измените тип данных параметра на `Set`, чтобы он соответствовал типу данных свойства. Пример:  
  
    ```  
    Class Class1 ' Declare a local variable to hold the property value. Private Fval As Integer Property F() As Integer Get Return Fval End Get Set(ByVal Value As Integer) Fval = Value End Set End Property End Class  
    ```  
  
## См. также  
 [НЕ В СБОРКЕ. Практическое руководство. Добавление полей и свойств в класс](http://msdn.microsoft.com/ru-ru/ae53f61b-3abc-413e-8931-703c5f5e8fc2)   
 [Процедуры свойств](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [НЕ В СБОРКЕ. Свойства и процедуры свойств](http://msdn.microsoft.com/ru-ru/23e2a1ec-7e9d-4109-8940-c703d981077b)