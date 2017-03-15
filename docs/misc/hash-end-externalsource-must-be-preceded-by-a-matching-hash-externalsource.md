---
title: "Директиве #End ExternalSource должна предшествовать соответствующая директива #ExternalSource. | Microsoft Docs"
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
  - "bc30578"
  - "vbc30578"
helpviewer_keywords: 
  - "BC30578"
ms.assetid: f011673d-eced-46a7-a08e-d54d86c8a76b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Директиве #End ExternalSource должна предшествовать соответствующая директива #ExternalSource.
Директива `#ExternalSource` ссылается на внешний код, что позволяет компилятору выдавать точный отчет об исключениях, возникающих в этом коде. Блок `#ExternalSource` должен начинаться с `#ExternalSource` и заканчиваться `#End ExternalSource`.  
  
 **Идентификатор ошибки:** BC30578  
  
### Исправление ошибки  
  
1.  Добавьте `#ExternalSource` в соответствующее место в своем коде.  
  
2.  Удалите `#End ExternalSource`, если он не нужен.  
  
## См. также  
 [Директива \#ExternalSource](/dotnet/visual-basic/language-reference/directives/externalsource-directive)   
 [НЕ В СБОРКЕ. Условная компиляция \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/ad1e35e0-935e-4a35-a2ae-738bcf2a9240)