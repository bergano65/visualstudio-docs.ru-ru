---
title: Идебугпоинтерфиелд | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725595"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
Этот интерфейс представляет тип указателя.

## <a name="syntax"></a>Синтаксис

```
IDebugPointerField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Поставщик символов реализует этот интерфейс для представления указателя.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Используйте [QueryInterface](/cpp/atl/queryinterface) для получения этого интерфейса из интерфейса [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , если метод [Kind](../../../extensibility/debugger/reference/idebugfield-getkind.md) возвращает `FIELD_TYPE_POINTER` .

## <a name="methods-in-vtable-order"></a>Методы в порядке vtable
 Помимо методов в `IDebugField` `IDebugContainerField` интерфейсах и, этот интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Возвращает [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , описывающий цель указателя.|

## <a name="remarks"></a>Remarks
 В C/C++ указатель может быть контейнером, если он используется с нотацией массива. Например, `char *pString` `pString` имеет тип указателя на `char` . `pString[3]` имеет тип контейнера, который является указателем на `char` , ссылающийся на четвертый элемент этого контейнера.

## <a name="requirements"></a>Требования
 Заголовок: sh. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
