---
title: "Не удается использовать синтаксис инициализатора объекта для инициализации экземпляра типа Object. | Microsoft Docs"
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
  - "bc30994"
  - "vbc30994"
helpviewer_keywords: 
  - "BC30994"
ms.assetid: 2ef65965-f014-4fc1-8c7d-c603f0a764df
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Не удается использовать синтаксис инициализатора объекта для инициализации экземпляра типа Object.
Вы не можете инициализировать экземпляр `Object` с помощью синтаксиса инициализатора объекта. Экземпляр `Object` не имеет свойств или полей, которым можно назначить значение, а в синтаксисе инициализатора объекта требуется хотя бы одно такое свойство или поле.  
  
```  
' Not valid. ' Dim obj1 = New Object With {} ' Dim obj2 = New Object With {.ToString = <some value>}  
```  
  
 **Идентификатор ошибки:** BC30994  
  
### Исправление ошибки  
  
1.  Объявите экземпляры типа `Object` без использования списка инициализатора:  
  
    ```  
    Dim obj3 as Object Dim obj4 as New Object()  
    ```  
  
## См. также  
 [Инициализаторы объектов: именованные и анонимные типы](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Тип данных Object](/dotnet/visual-basic/language-reference/data-types/object-data-type)