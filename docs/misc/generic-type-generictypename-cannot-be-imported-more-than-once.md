---
title: "Универсальный тип &quot;&lt;имя_универсального_типа&gt;&quot; нельзя импортировать более одного раза. | Microsoft Docs"
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
  - "BC32086"
  - "vbc32086"
helpviewer_keywords: 
  - "BC32086"
ms.assetid: d93bae4b-3224-4a6e-a072-8ce231084519
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Универсальный тип &quot;&lt;имя_универсального_типа&gt;&quot; нельзя импортировать более одного раза.
Инструкция [Оператор Imports \(пространство имен .NET и тип\)](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type) указывает универсальный тип, который уже был импортирован с параметризацией другого типа.  
  
 Вы можете объявить из универсального типа несколько сформированных типов, поскольку объявлением сформированного типа вы не переопределяете универсальный тип. Однако если вы импортируете универсальный тип несколько раз, это является эквивалентом нескольких определений.  
  
 **Идентификатор ошибки:** BC32086  
  
### Исправление ошибки  
  
1.  Если исходный файл, содержащий эту инструкцию `Imports`, также содержит другую инструкцию `Imports`, указывающую тот же универсальный тип, удалите одну из них.  
  
2.  Если вам требуется импортировать тот же универсальный тип с параметризациями другого типа, используйте несколько исходных файлов.  
  
## См. также  
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)