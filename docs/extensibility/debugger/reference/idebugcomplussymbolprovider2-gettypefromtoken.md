---
title: IDebugComPlusSymbolProvider2::GetTypeFromToken | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugComPlusSymbolProvider2::GetTypeFromToken
- GetTypeFromToken
ms.assetid: 4452bc5d-0225-40e0-a467-c472a5c7c4ee
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5c514df27914ed0c40239e6d06130ab7df25d07c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49858333"
---
# <a name="idebugcomplussymbolprovider2gettypefromtoken"></a>IDebugComPlusSymbolProvider2::GetTypeFromToken
Возвращает тип, учитывая его маркер.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetTypeFromToken(  
   ULONG32       appDomain,  
   GUID          guidModule,  
   DWORD         tdToken,  
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetTypeFromToken(  
   uint            appDomain,  
   Guid            guidModule,  
   uint            tdToken,  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `appDomain`  
 [in] Идентификатор домена приложения.  
  
 `guidModule`  
 [in] Уникальный идентификатор модуля.  
  
 `tdToken`  
 [in] Токен типа, который требуется получить.  
  
 `ppField`  
 [out] Возвращает тип, представленный [IDebugField](../../../extensibility/debugger/reference/idebugfield.md).  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для **CDebugSymbolProvider** объекта, который предоставляет [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) интерфейс.  
  
```cpp  
HRESULT CDebugSymbolProvider::GetTypeFromToken(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    DWORD tdToken,  
    IDebugField **ppField)  
{  
    HRESULT hr = E_FAIL;  
  
    METHOD_ENTRY( CDebugDynamicFieldSymbol::GetTypeFromToken );  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidWritePtr(ppField, IDebugField*));  
  
    Module_ID idModule(ulAppDomainID, guidModule);  
  
    IfFailGo( this->CreateClassType(idModule, tdToken, ppField) );  
  
Error:  
  
    METHOD_EXIT( CDebugDynamicFieldSymbol::GetTypeFromToken, hr );  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>См. также  
 [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)