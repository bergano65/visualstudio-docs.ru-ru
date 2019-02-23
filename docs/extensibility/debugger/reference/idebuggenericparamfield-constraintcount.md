---
title: IDebugGenericParamField::ConstraintCount | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ConstraintCount
- IDebugGenericParamField::ConstraintCount
ms.assetid: 76bef0cb-8a3c-4ce5-87cc-1809de229f33
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f21e872fc04bc3d18ca3c332622844bfc57ece67
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56688918"
---
# <a name="idebuggenericparamfieldconstraintcount"></a>IDebugGenericParamField::ConstraintCount
Возвращает количество ограничений, связанных с этим универсальным параметром.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT ConstraintCount(
    ULONG32* pcConst
);
```

```csharp
int ConstraintCount(
    ref uint pcConst
);
```

#### <a name="parameters"></a>Параметры
`pcConst`

 [in, out] Число ограничений, связанных с этим полем.

## <a name="return-value"></a>Возвращаемое значение
В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для **CDebugGenericParamFieldType** объекта, который предоставляет [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) интерфейс.

```cpp
HRESULT CDebugGenericParamFieldType::ConstraintCount(ULONG32* pcConst)
{
    HRESULT hr = S_OK;
    CComPtr<IMetaDataImport> pMetadata;
    CComPtr<IMetaDataImport2> pMetadata2;
    HCORENUM hEnum = 0;
    ULONG cConst = 0;

    METHOD_ENTRY( CDebugGenericParamFieldType::ConstraintCount );

    IfFalseGo(pcConst, E_INVALIDARG );
    *pcConst = 0;
    IfFailGo( m_spSH->GetMetadata( m_idModule, &pMetadata ) );
    IfFailGo( pMetadata->QueryInterface(IID_IMetaDataImport2, (void**)&pMetadata2) );
    IfFailGo( pMetadata2->EnumGenericParamConstraints( &hEnum,
              m_tokParam,
              NULL,
              0,
              &cConst) );
    IfFailGo( pMetadata->CountEnum(hEnum, &cConst) );
    pMetadata->CloseEnum(hEnum);
    hEnum = NULL;

    *pcConst = cConst;

Error:

    METHOD_EXIT( CDebugGenericParamFieldType::ConstraintCount, hr );
    return hr;
}
```

## <a name="see-also"></a>См. также
- [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)
