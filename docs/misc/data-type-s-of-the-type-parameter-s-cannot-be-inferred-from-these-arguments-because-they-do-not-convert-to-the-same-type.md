---
title: "Типы данных параметров типа не могут выводиться из этих аргументов, так как они не преобразуются в один тип | Microsoft Docs"
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
  - "vbc36659"
  - "bc36659"
  - "vbc36656"
  - "bc36656"
helpviewer_keywords: 
  - "BC36659"
  - "BC36656"
ms.assetid: 0aa809da-3b44-4d78-b3c5-0a148bdf7ce8
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Типы данных параметров типа не могут выводиться из этих аргументов, так как они не преобразуются в один тип
Типы данных параметров типа не могут выводиться из этих аргументов, так как они не преобразуются в один тип. Явное указание типов данных может исправить эту ошибку.  
  
 Эта ошибка возникает при неудачном разрешении перегрузки. Ошибка появляется в виде сообщения, в котором указывается, почему была исключена определенная потенциальная перегрузка. В сообщении об ошибке объясняется, что компилятору не удается использовать определение типа, чтобы найти типы данных для параметров типа, совместимых с аргументами.  
  
> [!NOTE]
>  Когда аргументы являются обязательными \(например, в операторах выражений запросов\), это сообщение об ошибке отображается без второго предложения.  
  
 Дополнительные сведения и примеры см. в разделе [Типы данных параметров типа в методе "\<имя\_метода\>" не могут выводиться из этих аргументов, так как они не преобразуются в один и тот же тип](../Topic/Data%20type\(s\)%20of%20the%20type%20parameter\(s\)%20in%20method%20'%3Cmethodname%3E'%20cannot%20be%20inferred%20from%20these%20arguments%20because%20they%20do%20not%20convert%20to%20the%20same%20type.md).  
  
 **Идентификатор ошибки:** BC36659 и BC36656  
  
## См. также  
 [Неявное преобразование делегата](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [Универсальные процедуры в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Разрешение перегрузки](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution)