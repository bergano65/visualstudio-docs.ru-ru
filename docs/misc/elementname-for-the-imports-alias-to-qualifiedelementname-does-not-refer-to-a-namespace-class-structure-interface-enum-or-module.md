---
title: "&quot;&lt;elementname&gt;&quot; для псевдонима Imports для &quot;&lt;qualifiedelementname&gt;&quot; не ссылается на Namespace, Class, Structure, Interface, Enum или Module | Microsoft Docs"
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
  - "bc30798"
  - "vbc30798"
helpviewer_keywords: 
  - "BC30798"
ms.assetid: bfa66627-516a-4955-977d-92372bcea090
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;elementname&gt;&quot; для псевдонима Imports для &quot;&lt;qualifiedelementname&gt;&quot; не ссылается на Namespace, Class, Structure, Interface, Enum или Module
Инструкция [Оператор Imports \(пространство имен .NET и тип\)](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type) указывает программный элемент, который не может быть импортирован.  
  
 Инструкция `Imports` используется для уменьшения или устранения необходимости уточняющей строки перед именем элемента. Вы уточняете элемент в самой инструкции `Imports`, чтобы предоставить однозначный путь для уникального объявления элемента. После этого не потребуется уточнять ссылки на этот элемент.  
  
 `Imports` чаще всего используется для пространств имен, но можно также импортировать класс, модуль, структуру, интерфейс или перечисление, чтобы разрешить ссылку на элементы этого объекта без длинной уточняющей строки.  
  
 Дополнительные сведения см. в разделе "Импорт элементов с содержимым" статьи [НЕ В СБОРКЕ. Разрешение ссылки, если несколько переменных имеют одинаковые имена](http://msdn.microsoft.com/ru-ru/9601e39f-1911-44e1-ace5-3f6e090408b9).  
  
 **Идентификатор ошибки:** BC30798  
  
### Исправление ошибки  
  
1.  Проверьте правильность написания элементов в уточняющей строке в инструкции `Imports`, особенно последний элемент в строке, являющийся тем элементом, который вы уточняете.  
  
2.  Убедитесь, что элемент, который вы уточняете, имеет подходящий тип \(является пространством имен, классом, модулем, структурой, интерфейсом или перечислением\). В противном случае удалите инструкцию `Imports`.  
  
## См. также  
 [Ссылки и оператор Imports](/dotnet/visual-basic/programming-guide/program-structure/references-and-the-imports-statement)