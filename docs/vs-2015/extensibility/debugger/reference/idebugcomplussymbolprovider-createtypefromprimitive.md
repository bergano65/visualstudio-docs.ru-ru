---
title: 'Идебугкомплуссимболпровидер:: Креатетипефромпримитиве | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::CreateTypeFromPrimitive
- CreateTypeFromPrimitive
ms.assetid: 37213cc2-a038-42ea-9b28-3ae40d4cfe69
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a7f0367be350b433b0ff2add0538cccc06951215
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194799"
---
# <a name="idebugcomplussymbolprovidercreatetypefromprimitive"></a>IDebugComPlusSymbolProvider::CreateTypeFromPrimitive
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Создает тип из указанного примитивного типа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
[C++]  
HRESULT CreateTypeFromPrimitive(  
   DWORD          dwPrimType,  
   IDebugAddress* pAddress,  
   IDebugField**  ppType  
);  
```  
  
```  
[C#]  
int CreateTypeFromPrimitive(  
   uint          dwPrimType,  
   IDebugAddress pAddress,  
   IDebugField   ppType  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwPrimType`  
 окне Значение из [перечисления корелементтипе](/dotnet/framework/unmanaged-api/metadata/corelementtype-enumeration) , представляющее тип-примитив.  
  
 `pAddress`  
 окне Объект Address, представленный интерфейсом [идебугаддресс](../../../extensibility/debugger/reference/idebugaddress.md) .  
  
 `ppType`  
 окне Возвращает объект [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , описывающий тип.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для объекта **кдебугсимболпровидер** , предоставляющего интерфейс [идебугкомплуссимболпровидер](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) .  
  
```cpp#  
HRESULT CDebugSymbolProvider::CreateTypeFromPrimitive(  
    DWORD dwPrimType,  
    IDebugAddress* pAddress,  
    IDebugField** ppType)  
{  
    HRESULT hr = S_OK;  
    CDEBUG_ADDRESS addr;  
    const COR_SIGNATURE* pTypeInfo = (const COR_SIGNATURE*) & dwPrimType;  
    CDebugGenericParamScope* pGenScope = NULL;  
  
    //  
    // This function will only work for primitive types  
    //  
  
    METHOD_ENTRY( CDebugSymbolProvider::CreateTypeFromPrimitive );  
  
    IfFailGo( pAddress->GetAddress( &addr ) );  
  
    IfNullGo( pGenScope = new CDebugGenericParamScope(addr.GetModule(), addr.tokClass, addr.GetMethod()), E_OUTOFMEMORY );  
  
    IfFailGo( CreateType( pTypeInfo,  
                          1,  
                          addr.GetModule(),  
                          addr.GetMethod(),  
                          pGenScope,  
                          ppType ) );  
  
    METHOD_EXIT( CDebugSymbolProvider::CreateTypeFromPrimitive, hr );  
  
Error:  
  
    RELEASE( pGenScope );  
    return hr;  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
