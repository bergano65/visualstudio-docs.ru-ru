---
title: "Метод расширения &quot;&lt;имя_метода&gt;&quot;, заданный в &quot;&lt;имя_модуля&gt;&quot;, не имеет сигнатуры, совместимой с делегатом &quot;&lt;имя_делегата&gt;&quot; | Microsoft Docs"
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
  - "bc36710"
  - "vbc36710"
helpviewer_keywords: 
  - "BC36710"
ms.assetid: e439d9e0-7821-451a-a7b7-68c1cf1a85a3
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Метод расширения &quot;&lt;имя_метода&gt;&quot;, заданный в &quot;&lt;имя_модуля&gt;&quot;, не имеет сигнатуры, совместимой с делегатом &quot;&lt;имя_делегата&gt;&quot;
Существует несоответствие между сигнатурами метода расширения и делегата, который вы пытаетесь использовать. Типы параметров и значений, возвращаемых классом делегата, определяются оператором `Delegate`. Для создания экземпляра этого типа делегата можно использовать любую процедуру с совместимыми параметрами, типами параметров и типом возврата.  
  
 **Идентификатор ошибки:** BC36710  
  
## См. также  
 [Неявное преобразование делегата](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [Оператор Delegate](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [НЕ В СБОРКЕ. Делегаты и оператор AddressOf](http://msdn.microsoft.com/ru-ru/7b2ed932-8598-4355-b2f7-5cedb23ee86f)