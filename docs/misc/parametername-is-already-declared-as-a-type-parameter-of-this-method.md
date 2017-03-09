---
title: "Параметр &quot;&lt;имя_параметра&gt;&quot; уже объявлен как параметр типа данного метода. | Microsoft Docs"
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
  - "bc32089"
  - "vbc32089"
helpviewer_keywords: 
  - "BC32089"
ms.assetid: 5e440b4b-f62b-4ff5-9148-2372d4752bf6
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Параметр &quot;&lt;имя_параметра&gt;&quot; уже объявлен как параметр типа данного метода.
Универсальная процедура определяет обычный параметр или локальную переменную с тем же именем, что и параметр типа.  
  
 Каждый параметр процедуры, в том числе каждый параметр типа универсальной процедуры, должен иметь имя, отличное от имен всех остальных параметров. Поскольку параметры процедуры используются в качестве локальных переменных, любая локальная переменная, объявленная внутри процедуры, также должна иметь имя, отличное от имен всех параметров и параметров типа.  
  
 **Идентификатор ошибки:** BC32089  
  
### Исправление ошибки  
  
-   Измените имя обычного параметра или локальной переменной.  
  
## См. также  
 [Универсальные процедуры в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Список параметров](/dotnet/visual-basic/language-reference/statements/parameter-list)