---
title: IDebugGenericParamField::GetFlags | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetFlags
- IDebugGenericParamField::GetFlags
ms.assetid: adcbbca1-8960-4c88-86b0-8b9467056c97
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c68e532c893cd8a51895c8e409f646b003bba85
ms.sourcegitcommit: 845442e2b515c3ca1e4e47b46cc1cef4df4f08d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/20/2019
ms.locfileid: "56449728"
---
# <a name="idebuggenericparamfieldgetflags"></a>IDebugGenericParamField::GetFlags
Извлекает флаги для данного универсального параметра.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetFlags(
    DWORD* pdwFlags
);
```

```csharp
int GetFlags(
    ref uint pdwFlags
);
```

#### <a name="parameters"></a>Параметры
`pdwFlags`  
[out] Возвращает флаги для данного универсального параметра.

## <a name="return-value"></a>Возвращаемое значение
В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
Эти флаги содержат сведения о различных особые ограничения.

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для **CDebugGenericParamFieldType** объекта, который предоставляет [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) интерфейс.

```cpp
HRESULT CDebugGenericParamFieldType::GetFlags(DWORD *pdwFlags)
{
    HRESULT hr = S_OK;

    METHOD_ENTRY( CDebugGenericParamFieldType::GetFlags );

    IfFalseGo( pdwFlags, E_INVALIDARG );
    IfFailGo( this->LoadProps() );
    *pdwFlags = m_dwFlags;

Error:

    METHOD_EXIT( CDebugGenericParamFieldType::GetFlags, hr );
    return hr;
}
```

## <a name="see-also"></a>См. также
[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)
