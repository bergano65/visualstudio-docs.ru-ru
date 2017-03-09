---
title: "Не удается инициализировать переменную с типом &quot;&lt;имя_элемента&gt;&quot;, не являющимся массивом | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36536"
  - "bc36536"
helpviewer_keywords: 
  - "BC36536"
ms.assetid: 959415de-164e-4971-aab0-faad315753e9
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Не удается инициализировать переменную с типом &quot;&lt;имя_элемента&gt;&quot;, не являющимся массивом
Переменная, объявленная как массив, должна быть инициализирована со значением массива.  
  
```  
' Not valid. ' The following line causes this error when executed with Option Strict off. ' Dim arrayVar1() = 10  
```  
  
 **Идентификатор ошибки:** BC36536  
  
### Исправление ошибки  
  
-   Инициализируйте переменную массива со значением массива:  
  
    ```  
    ' With Option Strict off. Dim arrayVar2() = {1, 2, 3} ' With Option Strict on. Dim arrayVar3() As Integer = {1, 2, 3}  
    ```  
  
## См. также  
 [НЕ В СБОРКЕ. Переменная массива](http://msdn.microsoft.com/ru-ru/c2da78bd-6928-46ba-805f-44f819dfaf93)