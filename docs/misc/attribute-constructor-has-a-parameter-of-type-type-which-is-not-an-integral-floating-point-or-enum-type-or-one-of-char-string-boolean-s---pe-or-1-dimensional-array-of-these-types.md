---
title: "Конструктор атрибута имеет параметр типа &quot;&lt;тип&gt;&quot;, который не является ни целым числом, ни числом с плавающей точкой, ни Enum, ни параметром одного из типов Object, Char, String, Boolean или System.Type, ни одномерным массивом их этих типов. | Microsoft Docs"
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
  - "bc30045"
  - "vbc30045"
helpviewer_keywords: 
  - "BC30045"
ms.assetid: 16899755-7901-4c56-ae90-54c3532e8319
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Конструктор атрибута имеет параметр типа &quot;&lt;тип&gt;&quot;, который не является ни целым числом, ни числом с плавающей точкой, ни Enum, ни параметром одного из типов Object, Char, String, Boolean или System.Type, ни одномерным массивом их этих типов.
Определение настраиваемого атрибута включает конструктор, указывающий недопустимый тип данных для параметра. Атрибуты могут принимать в качестве параметров только определенные типы данных, поскольку только эти типы могут быть сериализованы в метаданные для сборки.  
  
 **Идентификатор ошибки:** BC30045  
  
### Исправление ошибки  
  
1.  Измените тип данных параметра на `Byte`, `Short`, `Integer`, `Long`, `Single`, `Double`, `Char`, `String`, `Boolean`, `System.Type` или на тип перечисления.  
  
## См. также  
 [НЕ В СБОРКЕ. Настраиваемые атрибуты в Visual Basic](http://msdn.microsoft.com/ru-ru/d72d8a5c-8f64-4614-b15b-cad66845d047)