---
title: IDebugPointerField (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a69797cc513b96c364f0357f22788fc9bcd65657
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725595"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
Этот интерфейс представляет тип указателя.

## <a name="syntax"></a>Синтаксис

```
IDebugPointerField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Поставщик символов реализует этот интерфейс, чтобы представлять указатель.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Используйте [queryInterface,](/cpp/atl/queryinterface) чтобы получить этот интерфейс из интерфейса [IDebugField,](../../../extensibility/debugger/reference/idebugfield.md) если [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) возвращается. `FIELD_TYPE_POINTER`

## <a name="methods-in-vtable-order"></a>Методы в порядке Vtable
 В дополнение к методам `IDebugField` и `IDebugContainerField` интерфейсам, этот интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Возвращает [IDebugField,](../../../extensibility/debugger/reference/idebugfield.md) описывающий цель указателя.|

## <a name="remarks"></a>Примечания
 В C/C, указатель может быть контейнером, если он используется с обозначением массива. Например, `char *pString`данный, `pString` имеет тип `char`указателя на . `pString[3]`имеет тип контейнера, который является `char` указателем на то, что ссылки на четвертый элемент этого контейнера.

## <a name="requirements"></a>Требования
 Заголовок: sh.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
