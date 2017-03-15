---
title: "Директивы &quot;#ExternalSource&quot; не могут быть вложенными | Microsoft Docs"
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
  - "bc30580"
  - "vbc30580"
helpviewer_keywords: 
  - "BC30580"
ms.assetid: 56c6ef4b-28b1-4a62-8afa-d83a7742b507
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Директивы &quot;#ExternalSource&quot; не могут быть вложенными
Предпринята попытка поместить директиву `#ExternalSource` в другой блок `#ExternalSource`. Директива `#ExternalSource` ссылается на внешний код, что позволяет компилятору выдавать точный отчет об исключениях, возникающих в этом коде.  
  
 Блоки `#ExternalSource` не могут быть вложены в другие блоки `#ExternalSource`.  
  
 **Идентификатор ошибки:** BC30580  
  
### Исправление ошибки  
  
-   Переместите внутреннюю директиву `#ExternalSource` за пределы включающего ее блока `#ExternalSource`.  
  
## См. также  
 [Директива \#ExternalSource](/dotnet/visual-basic/language-reference/directives/externalsource-directive)   
 [НЕ В СБОРКЕ. Условная компиляция \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/ad1e35e0-935e-4a35-a2ae-738bcf2a9240)