---
title: IDebugClassField Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField
helpviewer_keywords:
- IDebugClassField interface
ms.assetid: 49358cbc-8973-4862-9dcc-79b1248e6712
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11b0e4cd7c851e65edf299f45ec97273804c25d8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734291"
---
# <a name="idebugclassfield"></a>IDebugClassField
Этот интерфейс представляет класс как тип.

## <a name="syntax"></a>Синтаксис

```
IDebugClassField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Поставщик символов реализует этот интерфейс на том же объекте, который реализует интерфейс [IDebugContainerField.](../../../extensibility/debugger/reference/idebugcontainerfield.md) Этот интерфейс представляет собой специализацию, представляющую тип класса.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Ряд интерфейсов имеют методы, которые могут вернуть этот интерфейс, включая [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md), и [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md). Кроме того, вы можете использовать [QueryInterface](/cpp/atl/queryinterface) для получения этого интерфейса из интерфейса `FIELD_TYPE_CLASS` [IDebugContainerField,](../../../extensibility/debugger/reference/idebugcontainerfield.md) если метод [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) возвращает флаг.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В дополнение к методам на интерфейсах [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) и [IDebugContainerField,](../../../extensibility/debugger/reference/idebugcontainerfield.md) этот интерфейс реализует следующие:

|Метод|Описание|
|------------|-----------------|
|[EnumBaseClasses](../../../extensibility/debugger/reference/idebugclassfield-enumbaseclasses.md)|Создает регистратор для базовых классов этого класса.|
|[DoesInterfaceExist](../../../extensibility/debugger/reference/idebugclassfield-doesinterfaceexist.md)|Определяется, определяется ли определенный интерфейс в классе.|
|[EnumNestedClasses](../../../extensibility/debugger/reference/idebugclassfield-enumnestedclasses.md)|Создает регистратор для вложенных классов этого класса.|
|[GetEnclosingClass](../../../extensibility/debugger/reference/idebugclassfield-getenclosingclass.md)|Получает класс, который примыкает к этому классу.|
|[EnumInterfacesImplemented](../../../extensibility/debugger/reference/idebugclassfield-enuminterfacesimplemented.md)|Создает регистратор для интерфейсов, реализованных этим классом.|
|[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)|Создает регистратор для конструкторов этого класса.|
|[GetDefaultIndexer](../../../extensibility/debugger/reference/idebugclassfield-getdefaultindexer.md)|Получает имя индекса по умолчанию.|
|[EnumNestedEnums](../../../extensibility/debugger/reference/idebugclassfield-enumnestedenums.md)|Создает регистратор для вложенных регистраторов этого класса.|

## <a name="requirements"></a>Требования
 Заголовок: sh.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
