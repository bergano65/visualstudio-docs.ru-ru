---
title: IDebugMethodField::EnumParameters Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13df02cf5870e630c4aecb34e9295d218ba7a0eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727196"
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
Создает регистратор параметров метода.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumParameters( 
   IEnumDebugFields** ppParams
);
```

```csharp
int EnumParameters(
   out IEnumDebugFields ppParams
);
```

## <a name="parameters"></a>Параметры
`ppParams`\
(ваут) Возвращает в метод объект [IEnumDebugFields,](../../../extensibility/debugger/reference/ienumdebugfields.md) представляющий список параметров; в противном случае возвращает нулевую стоимость, если нет параметров.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращает S_OK или возвращает S_FALSE, если нет параметров. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
 Каждый элемент представляет собой объект [IDebugField,](../../../extensibility/debugger/reference/idebugfield.md) представляющий различные типы параметров. Вызов метод [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) на каждом объекте, чтобы точно определить, какой параметр представляет объект.

 Параметр включает в себя как его переменное имя, так и его тип. Первым параметром метода класса обычно является указатель "этот".

 Если необходимы только типы параметров, позвоните в метод [EnumArguments.](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)

## <a name="see-also"></a>См. также
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)
