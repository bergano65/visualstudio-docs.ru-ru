---
title: "Аргумент типа &quot;&lt;имя_типа_аргумента&gt;&quot; объявлен как MustInherit и не соответствует ограничению New для параметра типа &quot;&lt;имя_типа_параметра&gt;&quot; | Microsoft Docs"
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
  - "vbc32082"
  - "BC32082"
helpviewer_keywords: 
  - "BC32082"
ms.assetid: 597e5944-a61b-4858-ada5-efb80b27f26b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Аргумент типа &quot;&lt;имя_типа_аргумента&gt;&quot; объявлен как MustInherit и не соответствует ограничению New для параметра типа &quot;&lt;имя_типа_параметра&gt;&quot;
Универсальный тип вызывается с классом `MustInherit` в качестве аргумента типа, в то время как соответствующий параметр типа объявлен с ограничением `New`.  
  
 Ограничение `New` требует, чтобы тип, передаваемый в соответствующий аргумент типа, поддерживал создание объектов. Однако *абстрактный* класс, то есть класс, объявленный как `MustInherit`, не предоставляет никакие конструкторы, поэтому вы не можете создавать из него какие\-либо объекты.  
  
 **Идентификатор ошибки:** BC32082  
  
### Исправление ошибки  
  
1.  Если класс, используемый в аргументе типа, не должен быть абстрактным, удалите из его объявления ключевое слово `MustInherit`.  
  
2.  Если класс, используемый в аргументе типа, должен быть абстрактным, но не требуется использовать его для создания универсального типа, то передайте в качестве аргумента типа другой класс.  
  
3.  Если не требуется, чтобы соответствующий параметр типа создавал объекты из переданного в него типа, удалите из его объявления ограничение `New`.  
  
## См. также  
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Оператор New](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)