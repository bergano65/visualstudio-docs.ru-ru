---
title: "Поле AsyncVoidMethodBuilder.m_objectIdForDebugger | Microsoft Docs"
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
  - "поля m_objectIdForDebugger, AsyncVoidMethodBuilder структуры [обработчиков отладки платформы .NET Framework]"
ms.assetid: 81331a7b-6bec-46e4-a53e-515d0fad2400
caps.latest.revision: 3
caps.handback.revision: 3
ms.author: "gregvanl"
manager: "ghogen"
---
# Поле AsyncVoidMethodBuilder.m_objectIdForDebugger
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Предоставляет неактивно инициализированные объект, используемый отладчиком для уникальной идентификации этот построитель.  
  
 **Пространство имен:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Сборки:** mscorlib \(в библиотеке mscorlib.dll\)  
  
 Так как не удается получить доступ к внутреннему элементу из платформы .NET Framework, следующий синтаксис предоставляется общего промежуточного языка \(CIL\).  
  
## Синтаксис  
  
```  
.field private object m_objectIdForDebugger  
```  
  
## См. также  
 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>   
 [Внутренние компоненты параллельных расширений для .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)