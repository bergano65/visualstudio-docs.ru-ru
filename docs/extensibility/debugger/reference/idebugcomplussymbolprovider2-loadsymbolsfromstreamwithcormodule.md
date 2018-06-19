---
title: IDebugComPlusSymbolProvider2::LoadSymbolsFromStreamWithCorModule | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugComPlusSymbolProvider2::LoadSymbolsFromStreamWithCorModule
- LoadSymbolsFromStreamWithCorModule
ms.assetid: f79b894f-52c4-43c2-9a68-c71536451f6c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 59589c0db502ac5ddbf7c204968ca0684340f685
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103569"
---
# <a name="idebugcomplussymbolprovider2loadsymbolsfromstreamwithcormodule"></a>IDebugComPlusSymbolProvider2::LoadSymbolsFromStreamWithCorModule
Загрузить символы отладки из заданного потока данных **ICorDebugModule** объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT LoadSymbolsFromStreamWithCorModule(  
   ULONG32   ulAppDomainID,  
   GUID      guidModule,  
   ULONGLONG baseAddress,  
   IUnknown* pUnkMetadataImport,  
   IUnknown* pUnkCorDebugModule,  
   IStream*  pStream  
);  
```  
  
```csharp  
int LoadSymbolsFromStreamWithCorModule(  
   uint    ulAppDomainID,  
   Guid    guidModule,  
   ulong   baseAddress,  
   object  pUnkMetadataImport,  
   object  pUnkCorDebugModule,  
   IStream pStream  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ulAppDomainID`  
 [in] Идентификатор домена приложения.  
  
 `guidModule`  
 [in] Уникальный идентификатор модуля.  
  
 `baseAddress`  
 [in] Базовый адрес памяти.  
  
 `pUnkMetadataImport`  
 [in] Объект, содержащий метаданные для символа.  
  
 `pUnkCorDebugModule`  
 [in] Объект, реализующий [ICorDebugModule-интерфейс](/dotnet/framework/unmanaged-api/debugging/icordebugmodule-interface).  
  
 `pStream`  
 [in] Поток данных, содержащий отладочные символы для загрузки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для **CDebugSymbolProvider** объекта, который предоставляет [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) интерфейса.  
  
```cpp  
HRESULT CDebugSymbolProvider::LoadSymbolsFromStreamWithCorModule(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    ULONGLONG baseOffset,  
    IUnknown* pUnkMetadataImport,  
    IUnknown* pUnkCorDebugModule,  
    IStream* pStream  
)  
{  
    CAutoLock Lock(this);  
  
    HRESULT hr = S_OK;  
    CComPtr<IMetaDataImport> pMetadata;  
    CComPtr<ICorDebugModule> pCorModule;  
  
    CModule* pmodule = NULL;  
    CModule* pmoduleNew = NULL;  
    bool fAlreadyLoaded = false;  
    Module_ID idModule(ulAppDomainID, guidModule);  
    DWORD dwCurrentState = 0;  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidInterfacePtr(pUnkMetadataImport, IUnknown));  
  
    METHOD_ENTRY( CDebugSymbolProvider::LoadSymbolsFromStream );  
  
    IfFalseGo( pUnkMetadataImport, E_INVALIDARG );  
    IfFalseGo( pUnkCorDebugModule, E_INVALIDARG );  
  
    IfFailGo( pUnkMetadataImport->QueryInterface( IID_IMetaDataImport,  
              (void**)&pMetadata) );  
  
    IfFailGo( pUnkCorDebugModule->QueryInterface( IID_ICorDebugModule,  
              (void**)&pCorModule) );  
  
    ASSERT(guidModule != GUID_NULL);  
  
    fAlreadyLoaded = GetModule( idModule, &pmodule ) == S_OK;  
  
    IfNullGo( pmoduleNew = new CModule, E_OUTOFMEMORY );  
  
    dwCurrentState = m_pSymProvGroup ? m_pSymProvGroup->GetCurrentState() : 0;  
  
    IfFailGo( pmoduleNew->Create( idModule,  
                                  dwCurrentState,  
                                  pMetadata,  
                                  pCorModule,  
                                  pStream,  
                                  baseOffset ) );  
  
    if (fAlreadyLoaded)  
    {  
        IfFailGo(pmoduleNew->AddEquivalentModulesFrom(pmodule));  
        RemoveModule(pmodule);  
    }  
  
    IfFailGo( AddModule( pmoduleNew ) );  
  
Error:  
  
    RELEASE (pmodule);  
    RELEASE (pmoduleNew);  
  
    METHOD_EXIT( CDebugSymbolProvider::LoadSymbolsFromStream, hr );  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>См. также  
 [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)