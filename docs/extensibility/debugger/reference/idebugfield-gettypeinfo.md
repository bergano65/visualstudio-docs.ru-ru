---
title: 'Идебугфиелд:: GetTypeInfo | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetTypeInfo
helpviewer_keywords:
- IDebugField::GetTypeInfo method
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: faa3464f0396999f36604aa88c429235d4849688
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80728777"
---
# <a name="idebugfieldgettypeinfo"></a>IDebugField::GetTypeInfo
Этот метод получает независимые от типа сведения о символе или типе.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetTypeInfo( 
   TYPE_INFO* pTypeInfo
);
```

```csharp
int GetTypeInfo(
   TYPE_INFO[] pTypeInfo
);
```

## <a name="parameters"></a>Параметры
`pTypeInfo`\
заполняет Возвращает сведения о типе в указанной структуре [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) .

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Независимые от типа сведения включают, например, AppDomain, модуль и класс, содержащий символ.

## <a name="see-also"></a>См. также раздел
- [GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
