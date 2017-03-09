---
title: "Отсутствуют доступные процедуры &quot;&lt;имя_универсальной_процедуры&gt;&quot;, принимающие данное количество аргументов типа | Microsoft Docs"
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
  - "bc32118"
  - "vbc32118"
helpviewer_keywords: 
  - "BC32118"
ms.assetid: 4ee942ba-0fa1-4ec1-9c2c-a0c0dc3f1b17
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Отсутствуют доступные процедуры &quot;&lt;имя_универсальной_процедуры&gt;&quot;, принимающие данное количество аргументов типа
Инструкция вызывает универсальную процедуру, которая имеет несколько перегруженных версий, но ни одна из перегруженных версий не определяет то же количество параметров типа, что и количество аргументов типа в вызове.  
  
 Если имеется только одна универсальная версия, она вызывается без аргументов типа, и компилятор может попытаться выполнить *определение типа*. Дополнительные сведения см. в разделе "Определение типа" статьи [Универсальные процедуры в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures). Однако если имеется несколько универсальных версий, компилятор не сможет выбрать одну из них, пока не будут предоставлены аргументы типа. Если указывается один аргумент типа, необходимо указать аргумент типа для каждого параметра типа, который определяет одна из перегруженных версий.  
  
 **Идентификатор ошибки:** BC32118  
  
### Исправление ошибки  
  
-   Решите, какую из перегруженных версий вы хотите вызвать, а затем укажите соответствующее количество аргументов типа.  
  
## См. также  
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Перегрузка процедур](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Универсальные процедуры в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)