---
title: "Тип &quot;&lt;имя_типа&gt;&quot; не может наследовать от параметра типа | Microsoft Docs"
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
  - "bc32055"
  - "vbc32055"
helpviewer_keywords: 
  - "BC32055"
ms.assetid: 97af7cad-6e40-41e3-892d-1fbcbd86356d
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Тип &quot;&lt;имя_типа&gt;&quot; не может наследовать от параметра типа
Класс или интерфейс включает [Инструкция Inherits](/dotnet/visual-basic/language-reference/statements/inherits-statement), указывающую параметр универсального типа.  
  
 Тип не может наследовать от типа, который еще не определен. Наследование включает возможность повторно использовать элементы базового класса, а для этого необходимо, чтобы эти элементы были определены. Параметр универсального типа является заполнителем, который должен быть заменен специальным типом, предоставленным аргументом типа. Таким образом, тип не может наследовать от заполнителя.  
  
 **Идентификатор ошибки:** BC32055  
  
### Исправление ошибки  
  
-   Если наследующий тип должен наследовать от другого типа, используйте специальный тип вместо параметра типа.  
  
-   Если базовый тип должен быть представлен параметром универсального типа, никакой другой тип не может наследовать от него. Удалите параметр [Инструкция Inherits](/dotnet/visual-basic/language-reference/statements/inherits-statement).  
  
## См. также  
 [НЕ В СБОРКЕ. Наследование в Visual Basic](http://msdn.microsoft.com/ru-ru/e5e6e240-ed31-4657-820c-079b7c79313c)   
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)