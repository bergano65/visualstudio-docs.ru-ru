---
title: "Структура AsyncTaskMethodBuilder &lt; TResult &gt; - внутренние члены | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Структура AsyncTaskMethodBuilder < TResult > [обработчиков отладки платформы .NET Framework]"
  - "отладчики, AsyncTaskMethodBuilder < TResult > структуры [платформа .NET Framework]"
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# Структура AsyncTaskMethodBuilder &lt; TResult &gt; - внутренние члены
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

В этом разделе описываются внутренним элементам <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> класса. Общие сведения об этом классе см. в разделе <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> раздел справки.  
  
 **Пространство имен:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Сборки:** mscorlib \(в библиотеке mscorlib.dll\)  
  
 Поскольку невозможно получить эти внутренние члены из платформы .NET Framework, следующий синтаксис предоставляется общего промежуточного языка \(CIL\).  
  
## Синтаксис  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## Внутренние элементы  
  
|Имя|Описание|  
|---------|--------------|  
|[Свойство ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Возвращает объект, который может использоваться для уникальной идентификации этого построителя в отладчик.|  
|[поле m\_task](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Предоставляет неактивно инициализированные встроенных задач.|  
  
## См. также  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>   
 [Внутренние компоненты параллельных расширений для .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)