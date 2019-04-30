---
title: 'AsyncVoidMethodBuilder внутренние элементы: структура | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0a4c51d76d38680945eaccbd3ace256813668c51
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62890874"
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>AsyncVoidMethodBuilder внутренние элементы: структура
В этом разделе описывается внутренним членам объектов <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> класс. Общие сведения об этом классе см. в разделе <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> справочника.

 **Пространство имен:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Сборка:** mscorlib (в mscorlib.dll)

 Так как при отсутствии доступа к этим внутренним членам платформы .NET Framework, следующий синтаксис предоставляется общего промежуточного языка (CIL).

## <a name="syntax"></a>Синтаксис

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Внутренние элементы

|name|Описание|
|----------|-----------------|
|[Свойство ObjectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|Возвращает объект, который может использоваться для уникальной идентификации этого построителя к отладчику.|
|[поле m_objectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|Представляет неактивно инициализированный объект, используемый отладчиком для уникальной идентификации этого построителя.|

## <a name="see-also"></a>См. также
- <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>
- [Внутренние компоненты параллельных расширений для .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)