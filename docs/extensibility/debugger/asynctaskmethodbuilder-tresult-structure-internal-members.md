---
title: AsyncTaskMethodBuilder&lt;TResult&gt; структуры — внутренним членам | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4b5c9c3b0ff653384ff7a14487899d8205975cd5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>AsyncTaskMethodBuilder&lt;TResult&gt; структуры — внутренние элементы
В этом разделе описывает внутренние элементы <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> класса. Общие сведения об этом классе см. в разделе <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> справочном разделе.  
  
 **Пространство имен:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Сборка:** mscorlib (в библиотеке mscorlib.dll)  
  
 Так как не удается получить доступ к эти внутренние члены из платформы .NET Framework, синтаксиса предоставляется общего промежуточного языка (CIL).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Внутренние элементы  
  
|name|Описание|  
|----------|-----------------|  
|[Свойство ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Возвращает объект, который может использоваться для уникальной идентификации этого конструктора в режим отладчика.|  
|[поле m_task](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Представляет отложенной инициализацией встроенные задачи.|  
  
## <a name="see-also"></a>См. также  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>   
 [Внутренние компоненты параллельных расширений для .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)