---
title: 'AsyncTaskMethodBuilder внутренние элементы: структура | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3f080e7a0fef7a03b878c253f09661338b5704df
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317633"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>AsyncTaskMethodBuilder внутренние элементы: структура
В этом разделе описывается внутренним членам объектов <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> класс. Общие сведения об этом классе см. в разделе <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> справочника.

 **Пространство имен:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Сборка:** mscorlib (в mscorlib.dll)

 Так как при отсутствии доступа к этим внутренним членам платформы .NET Framework, следующий синтаксис предоставляется общего промежуточного языка (CIL).

## <a name="syntax"></a>Синтаксис

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Внутренние элементы

|name|Описание|
|----------|-----------------|
|[Свойство ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Возвращает объект, который может использоваться для уникальной идентификации этого построителя к отладчику.|
|[поле m_builder](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Представляет обычный построитель объект, к которому делегирует этот экземпляр не являющегося универсальным.|

## <a name="see-also"></a>См. также
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>
- [Внутренние компоненты параллельных расширений для .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)