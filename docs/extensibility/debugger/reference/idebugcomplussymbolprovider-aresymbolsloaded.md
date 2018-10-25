---
title: IDebugComPlusSymbolProvider::AreSymbolsLoaded | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- AreSymbolsLoaded
- IDebugComPlusSymbolProvider::AreSymbolsLoaded
ms.assetid: bbf8707d-f89c-4177-b019-d519f1ec6f4a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5d63b410fc8cae67e27c15d4ed87c59bbed982d8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825846"
---
# <a name="idebugcomplussymbolprovideraresymbolsloaded"></a>IDebugComPlusSymbolProvider::AreSymbolsLoaded
Определяет, если для указанного модуля, заданному идентификатору домена приложения загружаются символы отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT AreSymbolsLoaded (  
   ULONG32 ulAppDomainID,  
   GUID    guidModule  
);  
```  
  
```csharp  
int AreSymbolsLoaded (  
   uint ulAppDomainID,  
   Guid guidModule  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ulAppDomainID`  
 [in] Идентификатор домена приложения.  
  
 `guidModule`  
 [in] Уникальный идентификатор для модуля.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если отладочные символы загружены, возвращает `S_OK`; в противном случае возвращает `S_FALSE`.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для **CDebugSymbolProvider** объекта, который предоставляет [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) интерфейс.  
  
```cpp  
HRESULT CDebugSymbolProvider::AreSymbolsLoaded(  
    ULONG32 ulAppDomainID,  
    GUID guidModule  
)  
{  
    HRESULT hr = S_OK;  
    CComPtr<CModule> pModule;  
    Module_ID idModule(ulAppDomainID, guidModule);  
  
    METHOD_ENTRY( CDebugSymbolProvider::AreSymbolsLoaded );  
  
    IfFalseGo( GetModule( idModule, &pModule ) == S_OK, S_FALSE );  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::AreSymbolsLoaded, hr );  
    return hr;  
}  
```  
  
## <a name="see-also"></a>См. также  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)