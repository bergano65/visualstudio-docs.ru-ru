---
title: AsyncTaskMethodBuilder Структура - Внутренние члены (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c918890551515ab9fadbf329d4c3ee96621c7aae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739371"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>Структура AsyncTaskMethodBuilder - внутренние члены
Эта тема описывает внутренних <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> членов класса. Для получения общей информации <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> об этом классе, см.

 **Пространство имен:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Сборка:** mscorlib (в mscorlib.dll)

 Поскольку вы не можете получить доступ к этим внутренним членам из рамочного соглашения .NET, следующий синтаксис предоставляется на общем промежуточном языке (CIL).

## <a name="syntax"></a>Синтаксис

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Внутренние члены

|name|Описание|
|----------|-----------------|
|[Свойство ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Получает объект, который может быть использован для однозначной идентификации этого строителя для отладчика.|
|[m_builder поле](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Представляет общий объект строителя, на который делегирует этот необщий экземпляр.|

## <a name="see-also"></a>См. также
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>
- [Параллельные внутренние расширения для рамочной программы .NET](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
