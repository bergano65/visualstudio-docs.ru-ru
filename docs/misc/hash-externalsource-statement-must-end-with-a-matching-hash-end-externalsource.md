---
title: "Оператор &quot;#ExternalSource&quot; должен заканчиваться соответствующим оператором &quot;#End ExternalSource&quot;. | Microsoft Docs"
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
  - "vbc30579"
  - "bc30579"
helpviewer_keywords: 
  - "BC30579"
ms.assetid: 8d658008-eddc-4b7d-a8d4-036da42957bf
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператор &quot;#ExternalSource&quot; должен заканчиваться соответствующим оператором &quot;#End ExternalSource&quot;.
Директива `#ExternalSource` ссылается на внешний код, что позволяет компилятору выдавать точный отчет об исключениях, возникающих в этом коде. Блок `#ExternalSource` должен начинаться с `#ExternalSource` и заканчиваться `#End ExternalSource`.  
  
 **Идентификатор ошибки:** BC30579  
  
### Исправление ошибки  
  
1.  Добавьте `#End ExternalSource` в соответствующее место в своем коде.  
  
2.  Удалите исходный оператор `#ExternalSource`, если он не нужен.  
  
## См. также  
 [Директива \#ExternalSource](/dotnet/visual-basic/language-reference/directives/externalsource-directive)   
 [НЕ В СБОРКЕ. Условная компиляция \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/ad1e35e0-935e-4a35-a2ae-738bcf2a9240)