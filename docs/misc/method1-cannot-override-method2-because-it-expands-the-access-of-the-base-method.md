---
title: "Метод &quot;&lt;метод1&gt;&quot; не может переопределить &quot;&lt;метод2&gt;&quot;, поскольку он расширяет доступ базового метода | Microsoft Docs"
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
  - "vbc32203"
  - "bc32203"
helpviewer_keywords: 
  - "BC32203"
ms.assetid: ef7816a4-5f57-4346-80fc-9311bc150b6b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Метод &quot;&lt;метод1&gt;&quot; не может переопределить &quot;&lt;метод2&gt;&quot;, поскольку он расширяет доступ базового метода
Процедура указывает `Overrides`, но объявляет менее строгую доступность, чем переопределяемый метод. Нельзя расширить доступность; это означает, что нельзя сделать переопределяющий метод более доступным, чем переопределяемый им метод. Например, если базовый класс метода — `Protected`, его невозможно переопределить методом `Public`.  
  
 **Идентификатор ошибки:** BC32203  
  
### Исправление ошибки  
  
-   Удалите ключевое слово `Overrides` или измените доступность, чтобы она была не менее строгий, чем в методе базового класса.  
  
## См. также  
 [НЕ В СБОРКЕ. Переопределение свойств и методов](http://msdn.microsoft.com/ru-ru/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Уровни доступа в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)   
 [Сокрытие в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/shadowing)