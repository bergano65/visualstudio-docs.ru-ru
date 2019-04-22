---
title: IDebugProperty3::GetStringChars | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01558ccf2d4f0e06231a9cbe152c47b1601bfdb2
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59658111"
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
Извлекает строку, связанную с этим свойством и сохраняет его в буфер, предоставленный пользователем.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetStringChars(
    ULONG  buflen,
    WCHAR* rgString,
    ULONG* pceltFetched
);
```

```csharp
int GetStringChars(
    uint       buflen,
    out string rgString,
    out uint   pceltFetched
);
```

#### <a name="parameters"></a>Параметры
`buflen`

 [in] Максимальное количество символов, которые может содержать буфер предоставленное пользователем.

`rgString`

 [out] Возвращает строку.

 [C++ только], `rgString` — это указатель на буфер, получающий строки символы Юникода. Этот буфер должен быть по крайней мере `buflen` символов (не байтов) в размер.

`pceltFetched`

 [out] Где возвращается число символов, фактически хранятся в буфере. (Может быть `NULL` в C++.)

## <a name="return-value"></a>Возвращаемое значение
В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
В C++, следует принять меры, чтобы гарантировать, что буфер не ниже `buflen` символов Юникода. Обратите внимание, что символ Юникода 2 байт.

> [!NOTE]
> В C++ возвращаемая строка не включает завершающий нуль-символ. Если он задан, `pceltFetched` будет указать число символов в строке.

## <a name="example"></a>Пример

```cpp
CStringW RetrievePropertyString(IDebugProperty2 *pPropInfo)
{
    CStringW returnString = L"";
    CComQIPtr<IDebugProperty3> pProp3 = pPropInfo->pProperty;
    If (pProp3 != NULL) {
        ULONG dwStrLen = 0;
        HRESULT hr;
        hr = pProp3->GetStringCharLength(&dwStrLen);
        if (SUCCEEDED(hr) && dwStrLen > 0) {
            ULONG dwRead;
            CStrBufW buf(returnString,dwStrLen,CStrBuf::SET_LENGTH);
            hr = pProp3->GetStringChars(dwStrLen,
                                        reinterpret_cast<WCHAR*>(static_cast<CStringW::PXSTR>(buf)),
                                        &dwRead);
        }
    }
    return(returnString);
}
```

## <a name="see-also"></a>См. также
- [GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
