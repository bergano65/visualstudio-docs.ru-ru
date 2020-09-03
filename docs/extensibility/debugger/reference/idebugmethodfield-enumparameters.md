---
title: 'Идебугмесодфиелд:: Енумпараметерс | Документация Майкрософт'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727196"
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
Создает перечислитель для параметров метода.

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
заполняет Возвращает объект [иенумдебугфиелдс](../../../extensibility/debugger/reference/ienumdebugfields.md) , представляющий список параметров метода. в противном случае возвращает значение null, если нет параметров.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK или возвращает S_FALSE, если нет параметров. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Remarks
 Каждый элемент является объектом [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , представляющим различные типы параметров. Вызовите метод [Kind](../../../extensibility/debugger/reference/idebugfield-getkind.md) для каждого объекта, чтобы точно определить, какой тип параметра представляет объект.

 Параметр включает как имя переменной, так и ее тип. Первый параметр метода класса обычно является указателем this.

 Если требуются только типы параметров, вызовите метод [енумаргументс](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) .

## <a name="see-also"></a>См. также раздел
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)
