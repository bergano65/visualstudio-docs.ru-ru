---
title: Структура AsyncTaskMethodBuilder — внутренние элементы | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739371"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>Структура AsyncTaskMethodBuilder — внутренние элементы
В этом разделе описываются внутренние члены <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> класса. Общие сведения об этом классе см <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> . в разделе справки.

 **Пространство имен:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Сборка:** mscorlib (в mscorlib.dll)

 Так как вы не можете получить доступ к этим внутренним членам из .NET Framework, на стандартном промежуточном языке (CIL) приведен следующий синтаксис.

## <a name="syntax"></a>Синтаксис

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Внутренние члены

|Имя|Описание|
|----------|-----------------|
|[ObjectIdForDebugger, свойство](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Возвращает объект, который может использоваться для уникальной идентификации этого построителя в отладчике.|
|[m_builder поле](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Представляет объект универсального конструктора, для которого этот неуниверсальный экземпляр не является делегатом.|

## <a name="see-also"></a>См. также раздел
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>
- [Внутренние модули параллельного расширения для .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
