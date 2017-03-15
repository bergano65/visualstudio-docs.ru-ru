---
title: "Метод &quot;&lt;метод1&gt;&quot; не может переопределить метод &quot;&lt;метод2&gt;&quot;, так как они имеют разные типы возврата. | Microsoft Docs"
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
  - "bc30437"
  - "vbc30437"
helpviewer_keywords: 
  - "BC30437"
ms.assetid: e566ae72-c597-4b33-b70d-5d4ea879d644
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Метод &quot;&lt;метод1&gt;&quot; не может переопределить метод &quot;&lt;метод2&gt;&quot;, так как они имеют разные типы возврата.
Предпринята попытка переопределения одного метода другим методом, отличающимся своим типом возврата. Тип может переопределять наследуемый переопределяемый метод, если объявить метод с тем же именем и сигнатурой и указать в объявлении модификатор `Overrides`. Сигнатуры двух методов должны совпадать.  
  
 **Идентификатор ошибки:** BC30437  
  
### Исправление ошибки  
  
-   Проверьте типы возврата двух методов и при необходимости измените их для соответствия.  
  
## См. также  
 [НЕ В СБОРКЕ. Переопределение свойств и методов](http://msdn.microsoft.com/ru-ru/2167e8f5-1225-4b13-9ebd-02591ba90213)