---
title: "System.Runtime.InteropServices.DllImportAttribute не может применяться к методам экземпляра. | Microsoft Docs"
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
  - "vbc31529"
  - "bc31529"
helpviewer_keywords: 
  - "BC31529"
ms.assetid: c8bde5d7-c6bf-4d21-bb1a-e8627d65ad29
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# System.Runtime.InteropServices.DllImportAttribute не может применяться к методам экземпляра.
Необщая процедура объявлена с атрибутом <xref:System.Runtime.InteropServices.DllImportAttribute>.  
  
 Среда CLR распознает этот атрибут и его свойство <xref:System.Runtime.InteropServices._Assembly.EntryPoint%2A> в качестве назначения процедуры замены, определенной в библиотеке DLL неуправляемого кода вне .NET Framework. Когда код вызывает процедуру, к которой применен атрибут <xref:System.Runtime.InteropServices.DllImportAttribute>, среда CLR вызывает вместо этого назначенную процедуру неуправляемого кода.  
  
 Так как платформы неуправляемого кода вне .NET Framework не поддерживают необщие процедуры так, как .NET Framework, вы не можете взаимодействовать с ними с использованием необщих процедур.  
  
 **Идентификатор ошибки:** BC31529  
  
### Исправление ошибки  
  
-   Если процедуру не нужно применять отдельно к каждому экземпляру класса или структуры, объявите ее как `Shared`.  
  
-   Если процедура не может быть `Shared`, удалите атрибут <xref:System.Runtime.InteropServices.DllImportAttribute> из объявления этой процедуры.  
  
## См. также  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)