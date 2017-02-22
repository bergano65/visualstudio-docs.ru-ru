---
title: "Диалоговое окно &quot;Разрешение неоднозначности&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.Disambig"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Разрешение неоднозначности - диалоговое окно"
  - "отладчик, диалоговое окно "Разрешение неоднозначности""
  - "отладка [C++], разрешение неоднозначности"
ms.assetid: d9f47455-a116-4c84-8bad-2dfbf4d77f74
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Диалоговое окно &quot;Разрешение неоднозначности&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Диалоговое окно `Resolve Ambiguity` появляется, если отладчику не удалось выбрать расположение для отображения.  Например, при использовании шаблонов C\+\+ можно создавать несколько функций из одного шаблона функции.  Если отладчик останавливается в некотором месте исходного кода в шаблоне и выбрана команда `Go To Disassembly`, отладчик оказывается перед выбором.  Каждая функция, созданная из шаблона, имеет собственный дизассемблированный код, и отладчик не знает, какой именно код нужно отобразить.  Диалоговое окно `Resolve Ambiguity` позволяет выбрать желаемое расположение из списка всех соответствующих расположений.  
  
 `Choose the specific location`  
 Перечисляются все расположения, соответствующие команде.  
  
 `Address`  
 Показываются адреса памяти для каждой функции.  
  
 `Function`  
 Отображается имя каждой функции.  
  
 `Module`  
 Отображается модуль \(EXE или DLL\), содержащий объектный код для функции.  
  
## См. также  
 [Выражения в отладчике](../debugger/expressions-in-the-debugger.md)