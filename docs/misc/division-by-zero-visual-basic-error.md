---
title: "Деление на ноль (ошибка Visual Basic) | Microsoft Docs"
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
  - "vbrID11"
ms.assetid: 7dc22e29-8baa-4d82-a1a6-2de64ba9b25d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Деление на ноль (ошибка Visual Basic)
Значение выражения, используемого в качестве делителя, равно нулю.  
  
### Исправление ошибки  
  
1.  Проверьте правильность написания переменных в выражении. Имя переменной, написанное с ошибкой, может неявно создать числовую переменную, которая инициализируется с нулевым значением.  
  
2.  Проверьте предыдущие операции с переменной в выражении, в особенности те, которые передавались в процедуру как аргументы из других процедур.  
  
## См. также  
 [Типы ошибок](/dotnet/visual-basic/programming-guide/language-features/error-types)