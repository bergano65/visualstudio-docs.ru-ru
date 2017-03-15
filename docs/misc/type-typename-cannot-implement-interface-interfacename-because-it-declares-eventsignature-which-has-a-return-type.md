---
title: "Тип &quot;&lt;имя_типа&gt;&quot; не может реализовывать интерфейс &quot;&lt;имя_интерфейса&gt;&quot;, так как он объявляет событие &quot;&lt;сигнатура_события&gt;&quot;, которое имеет тип возврата | Microsoft Docs"
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
  - "bc30945"
  - "vbc30945"
helpviewer_keywords: 
  - "BC30945"
ms.assetid: 4f26e71a-949d-4103-b565-35cc8e833d29
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Тип &quot;&lt;имя_типа&gt;&quot; не может реализовывать интерфейс &quot;&lt;имя_интерфейса&gt;&quot;, так как он объявляет событие &quot;&lt;сигнатура_события&gt;&quot;, которое имеет тип возврата
Класс или структура пытается реализовать интерфейс, объявляющий событие, которое возвращает значение.  
  
 В настоящее время Visual Basic не поддерживает объявление событий, возвращающих значения.  
  
 **Идентификатор ошибки:** BC30945  
  
### Исправление ошибки  
  
-   Удалите оператор `Implements` из определения класса или структуры или реализуйте другой интерфейс.  
  
## См. также  
 [НЕ В СБОРКЕ. События и обработчики событий](http://msdn.microsoft.com/ru-ru/95074a0d-1cbc-4221-a95a-964185c7f962)   
 [Оператор Implements](/dotnet/visual-basic/language-reference/statements/implements-statement)   
 [НЕ В СБОРКЕ. Ключевое слово Implements и оператор Implements](http://msdn.microsoft.com/ru-ru/b96560f7-6413-480f-a1e2-f80253bab5be)