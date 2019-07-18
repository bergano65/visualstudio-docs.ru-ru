---
title: IDebugMethodField::EnumStaticLocals | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumStaticLocals
helpviewer_keywords:
- IDebugMethodField::EnumStaticLocals method
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 006f1975c18aa7464531654d9b71fd857953afc9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324246"
---
# <a name="idebugmethodfieldenumstaticlocals"></a>IDebugMethodField::EnumStaticLocals
Создает перечислитель для Статические локальные переменные метода.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumStaticLocals( 
   IEnumDebugFields** ppLocals
);
```

```csharp
int EnumStaticLocals(
   out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>Параметры
`ppLocals`\
[out] Возвращает [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) объект, представляющий список статических локальных переменных. Возвращает значение null, если нет статических локальных переменных.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK, или возвращает значение S_FALSE, если нет статических локальных переменных. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
 Каждый элемент является [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) объектов, представляющих различные типы статических локальных переменных. Вызовите [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) для каждого объекта, чтобы определить точно статическая локальная объекте вида метод.

## <a name="see-also"></a>См. также
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)