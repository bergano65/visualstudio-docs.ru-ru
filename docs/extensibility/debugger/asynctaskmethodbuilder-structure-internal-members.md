---
title: "Структура AsyncTaskMethodBuilder - внутренние члены | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "отладчики, AsyncTaskMethodBuilder структуры [платформа .NET Framework]"
  - "Структура AsyncTaskMethodBuilder [обработчиков отладки платформы .NET Framework]"
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# Структура AsyncTaskMethodBuilder - внутренние члены
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

В этом разделе описываются внутренним элементам <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> класса. Общие сведения об этом классе см. в разделе <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> раздел справки.  
  
 **Пространство имен:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Сборки:** mscorlib \(в библиотеке mscorlib.dll\)  
  
 Поскольку невозможно получить эти внутренние члены из платформы .NET Framework, следующий синтаксис предоставляется общего промежуточного языка \(CIL\).  
  
## Синтаксис  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## Внутренние элементы  
  
|Имя|Описание|  
|---------|--------------|  
|[Свойство ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Возвращает объект, который может использоваться для уникальной идентификации этого построителя в отладчик.|  
|[поле m\_builder](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Представляет объект обычного построителя делегирует этот экземпляр неуниверсальный.|  
  
## См. также  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>   
 [Внутренние компоненты параллельных расширений для .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)