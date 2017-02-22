---
title: "Свойство AsyncTaskMethodBuilder.ObjectIdForDebugger | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Свойство ObjectForDebugger, структура AsyncTaskMethodBuilder [обработчиков отладки платформы .NET Framework]"
ms.assetid: 78338537-b451-4655-9f04-a21f6fe197a3
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# Свойство AsyncTaskMethodBuilder.ObjectIdForDebugger
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Возвращает объект, который может использоваться для уникальной идентификации этого построителя в отладчик.  
  
 **Пространство имен:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Сборки:** mscorlib \(в библиотеке mscorlib.dll\)  
  
 Так как не удается получить доступ к внутреннему элементу из платформы .NET Framework, следующий синтаксис предоставляется общего промежуточного языка \(CIL\).  
  
## Синтаксис  
  
```c#  
private object ObjectIdForDebugger  
```  
  
## См. также  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>   
 [Внутренние компоненты параллельных расширений для .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)