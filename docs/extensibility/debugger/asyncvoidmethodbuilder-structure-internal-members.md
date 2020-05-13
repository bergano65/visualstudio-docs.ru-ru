---
title: AsyncVoidMethodBuilder Структура - Внутренние члены (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 866a53fae7bb2cc5325112b84d992da6f95af246
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739301"
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>Структура AsyncVoidMethodBuilder - внутренние участники
Эта тема описывает внутренних <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> членов класса. Для получения общей информации <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> об этом классе, см.

 **Пространство имен:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Сборка:** mscorlib (в mscorlib.dll)

 Поскольку вы не можете получить доступ к этим внутренним членам из рамочного соглашения .NET, следующий синтаксис предоставляется на общем промежуточном языке (CIL).

## <a name="syntax"></a>Синтаксис

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Внутренние члены

|name|Описание|
|----------|-----------------|
|[Свойство ObjectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|Получает объект, который может быть использован для однозначной идентификации этого строителя для отладчика.|
|[m_objectIdForDebugger поле](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|Представляет лениво инициализированный объект, используемый отладчиком для однозначной идентификации этого строителя.|

## <a name="see-also"></a>См. также
- <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>
- [Параллельные внутренние расширения для рамочной программы .NET](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
