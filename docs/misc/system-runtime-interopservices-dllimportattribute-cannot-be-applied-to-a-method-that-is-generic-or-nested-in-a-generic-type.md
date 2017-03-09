---
title: "System.Runtime.InteropServices.DllImportAttribute не может применяться к общему методу или методу, вложенному в общий тип | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31526"
  - "bc31526"
helpviewer_keywords: 
  - "BC31526"
ms.assetid: 6f153808-1945-4c99-85ae-8bd3b35ee5a2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# System.Runtime.InteropServices.DllImportAttribute не может применяться к общему методу или методу, вложенному в общий тип
Процедура объявлена с атрибутом <xref:System.Runtime.InteropServices.DllImportAttribute>, но является универсальной либо содержится в универсальном классе или структуре.  
  
 Среда CLR распознает этот атрибут и его свойство <xref:System.Runtime.InteropServices._Assembly.EntryPoint%2A> в качестве назначения процедуры замены, определенной в библиотеке DLL неуправляемого кода вне .NET Framework. Когда код вызывает процедуру, к которой применен атрибут <xref:System.Runtime.InteropServices.DllImportAttribute>, среда CLR вызывает вместо этого назначенную процедуру неуправляемого кода.  
  
 Так как неуправляемые платформы вне платформы .NET Framework не распознают универсальные типы, с ними нельзя взаимодействовать с помощью универсальных типов.  
  
 **Идентификатор ошибки:** BC31526  
  
### Исправление ошибки  
  
-   Если ни процедура, ни контейнер не должны быть универсальными, то удалите предложения `Of`, чтобы они перестали быть универсальными.  
  
-   Если процедура или контейнер должны быть универсальными, удалите <xref:System.Runtime.InteropServices.DllImportAttribute> из объявления этой процедуры.  
  
## См. также  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)