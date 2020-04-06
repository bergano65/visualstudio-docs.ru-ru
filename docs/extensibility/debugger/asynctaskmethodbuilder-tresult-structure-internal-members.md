---
title: AsyncTaskMethodbuilder&lt;TResult&gt; Структура - Внутренние члены (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c4f4da7070af09937af9e047ec83142584942e6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739332"
---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>AsyncTaskMethodBuilder&lt;TResult&gt; структура - внутренние члены
Эта тема описывает внутренних <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> членов класса. Для получения общей информации <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> об этом классе, см.

 **Пространство имен:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Сборка:** mscorlib (в mscorlib.dll)

 Поскольку вы не можете получить доступ к этим внутренним членам из рамочного соглашения .NET, следующий синтаксис предоставляется на общем промежуточном языке (CIL).

## <a name="syntax"></a>Синтаксис

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Внутренние члены

|name|Описание|
|----------|-----------------|
|[Свойство ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Получает объект, который может быть использован для однозначной идентификации этого строителя для отладчика.|
|[m_task поле](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Представляет лениво инициализированную задачу.|

## <a name="see-also"></a>См. также
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>
- [Параллельные внутренние расширения для рамочной программы .NET](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
