---
title: IDebugBinder3::GetMemoryContext64 | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- GetMemoryContext64
- IDebugBinder3::GetMemoryContext64
ms.assetid: f021fd16-9fc7-4c41-86af-e54e6224cfbb
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d828bc17820d04ee5056496bf7c0e5565e113bf1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49261538"
---
# <a name="idebugbinder3getmemorycontext64"></a>IDebugBinder3::GetMemoryContext64
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Преобразует адрес объекта или адрес памяти 64-разрядной памяти контекста.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetMemoryContext64 (  
   IDebugField*           pField,  
   UINT64                 uConstant,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```csharp  
int GetMemoryContext64 (  
   IDebugField              pField,  
   ulong                    uConstant,  
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pField`  
 [in] [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , описывающий объект, который требуется найти. Если `NULL`, затем с помощью `dwConstant` вместо этого.  
  
 `uConstant`  
 [in] Адрес памяти 64-разрядной, например 0x50000000.  
  
 `ppMemCxt`  
 [out] Возвращает [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) интерфейс, который представляет адрес объекта, или адрес в памяти.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="example"></a>Пример  
 Следующие примеры создает объект, реализующий [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md) интерфейс и использует этот метод для получения контекста памяти.  
  
```cpp#  
HRESULT CValueProperty::GetMemoryContext ( IDebugMemoryContext2** out_ppMemoryContext )  
{  
    // precondition  
    REQUIRE( NULL != out_ppMemoryContext );  
  
    if (NULL == out_ppMemoryContext)  
        return E_POINTER;  
  
    *out_ppMemoryContext = NULL;  
  
    INVARIANT( this );  
  
    if (!this->ClassInvariant())  
        return E_UNEXPECTED;  
  
    if (VT_EMPTY == this->m_VarValue.vt)  
    {  
        return E_FAIL;  
    }  
  
    // function body  
    if (NULL != this->m_pBinder)  
    {  
        UINT64 dwOffset = 0;  
  
        DEBUG_PROPERTY_INFO dpInfo;  
        HRESULT HR = this->GetPropertyInfo(DEBUGPROP_INFO_VALUE,  
                                           10, // RADIX  
                                           DEFAULT_TIMEOUT,  
                                           NULL,  
                                           0,  
                                           &dpInfo);  
        if (ENSURE( S_OK == HR ))  
        {  
            REQUIRE( NULL != dpInfo.bstrValue );  
            REQUIRE( NULL == dpInfo.bstrName );  
            REQUIRE( NULL == dpInfo.bstrFullName );  
            REQUIRE( NULL == dpInfo.bstrType );  
            REQUIRE( NULL == dpInfo.pProperty );  
  
            wchar_t * end;  
            dwOffset = _wcstoui64(dpInfo.bstrValue, &end, 0); // base 0 to allow 0x if it's ever output  
            ::SysFreeString(dpInfo.bstrValue);  
        }  
  
        if (CComQIPtr<IDebugBinder3> binder3 = this->m_pBinder)  
            HR = binder3->GetMemoryContext64(NULL, dwOffset, out_ppMemoryContext);  
        else  
            HR = this->m_pBinder->GetMemoryContext(NULL, (DWORD)(__int32)dwOffset, out_ppMemoryContext);  
  
        if (ENSURE( S_OK == HR ))  
        {  
            REQUIRE( NULL != *out_ppMemoryContext );  
        }  
    }  
  
    // postcondition  
    INVARIANT( this );  
  
    HRESULT HR = E_FAIL;  
  
    if (NULL != *out_ppMemoryContext)  
    {  
        HR = S_OK;  
    }  
  
    return HR;  
}  
```  
  
## <a name="see-also"></a>См. также  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)

