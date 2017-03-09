---
title: "&quot;&lt;метод1&gt;&quot; не может переопределить &quot;&lt;метод2&gt;&quot;, так как они отличаются по необязательным параметрам. | Microsoft Docs"
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
  - "vbc30308"
  - "bc30308"
helpviewer_keywords: 
  - "BC30308"
ms.assetid: 591dc351-4b87-4e92-81e1-2c1ff51da295
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;метод1&gt;&quot; не может переопределить &quot;&lt;метод2&gt;&quot;, так как они отличаются по необязательным параметрам.
Предпринята попытка переопределения одного метода другим, отличающимся от первого значениями своих необязательных параметров; это означает, что их сигнатуры разные. Тип может переопределять наследуемый переопределяемый метод, объявив метод с тем же именем и сигнатурой и указав в объявлении модификатор `Overrides`.  
  
 **Идентификатор ошибки:** BC30308  
  
### Исправление ошибки  
  
-   Убедитесь, что два метода имеют одинаковую сигнатуру.  
  
## См. также  
 [НЕ В СБОРКЕ. Переопределение свойств и методов](http://msdn.microsoft.com/ru-ru/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)