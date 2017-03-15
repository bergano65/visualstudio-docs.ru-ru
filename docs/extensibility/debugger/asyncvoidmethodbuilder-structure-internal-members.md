---
title: "Структура AsyncVoidMethodBuilder - внутренние члены | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "отладчики, AsyncVoidMethodBuilder структуры [платформа .NET Framework]"
  - "Структура AsyncVoidMethodBuilder [обработчиков отладки платформы .NET Framework]"
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# Структура AsyncVoidMethodBuilder - внутренние члены
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

В этом разделе описываются внутренним элементам <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> класса. Общие сведения об этом классе см. в разделе <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> раздел справки.  
  
 **Пространство имен:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Сборки:** mscorlib \(в библиотеке mscorlib.dll\)  
  
 Поскольку невозможно получить эти внутренние члены из платформы .NET Framework, следующий синтаксис предоставляется общего промежуточного языка \(CIL\).  
  
## Синтаксис  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## Внутренние элементы  
  
|Имя|Описание|  
|---------|--------------|  
|[Свойство ObjectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|Возвращает объект, который может использоваться для уникальной идентификации этого построителя в отладчик.|  
|[поле m\_objectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|Предоставляет неактивно инициализированные объект, используемый отладчиком для уникальной идентификации этот построитель.|  
  
## См. также  
 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>   
 [Внутренние компоненты параллельных расширений для .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)