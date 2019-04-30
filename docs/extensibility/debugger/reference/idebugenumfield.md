---
title: IDebugEnumField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField
helpviewer_keywords:
- IDebugEnumField interface
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e2bcb8f8562b5b20231879d46c64eb73af027f0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920247"
---
# <a name="idebugenumfield"></a>IDebugEnumField
Этот интерфейс представляет тип перечисления.

## <a name="syntax"></a>Синтаксис

```
IDebugEnumField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Символ поставщик реализует этот интерфейс для представления перечисления.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Используйте [QueryInterface](/cpp/atl/queryinterface) для получения этого интерфейса из [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) интерфейс, если [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) возвращает `FIELD_TYPE_ENUM`.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы VTable
 В дополнение к методам на `IDebugField` и `IDebugContainerField` интерфейсы, этот интерфейс реализует следующие методы:

|Метод|Описание|
|------------|-----------------|
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|Возвращает [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) описывающий имя для этого типа перечисления.|
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|Возвращает имя константы перечисления, связанный с заданным значением.|
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|Возвращает значение, связанное с именем константы заданное перечисление|
|[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)|Возвращает значение, связанное с заданное перечисление постоянное имя, но без учета регистра букв.|

## <a name="remarks"></a>Примечания
 Это базовый символ, который фактически связан в расположение с [привязать](../../../extensibility/debugger/reference/idebugbinder-bind.md).

## <a name="requirements"></a>Требования
 Заголовок: sh.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)