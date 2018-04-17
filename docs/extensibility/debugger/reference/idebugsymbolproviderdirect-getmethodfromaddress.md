---
title: IDebugSymbolProviderDirect::GetMethodFromAddress | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetMethodFromAddress
- GetMethodFromAddress
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2b164e7e317da54f6ea22131e923c55901acec49
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugsymbolproviderdirectgetmethodfromaddress"></a>IDebugSymbolProviderDirect::GetMethodFromAddress
Извлекает сведения о методе по адресу указанного отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetMethodFromAddress(  
   IDebugAddress* pAddress,  
   GUID*          pGuid,  
   DWORD*         pAppID,  
   _mdToken*      pTokenClass,  
   _mdToken*      pTokenMethod,  
   DWORD*         pdwOffset,  
   DWORD*         pdwVersion  
);  
```  
  
```csharp  
int GetMethodFromAddress(  
   IDebugAddress pAddress,  
   out Guid      pGuid,  
   out uint      pAppID,  
   out uint      pTokenClass,  
   out uint      pTokenMethod,  
   out uint      pdwOffset,  
   out uint      pdwVersion  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pAddress`  
 [in] Отладка, представленный адрес [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) интерфейса.  
  
 `pGuid`  
 [out] Уникальный идентификатор модуля.  
  
 `pAppID`  
 [out] Идентификатор домена приложения.  
  
 `pTokenClass`  
 [out] Токен, представляющий содержащего класса.  
  
 `pTokenMethod`  
 [out] Токен, представляющий модуль.  
  
 `pdwOffset`  
 [out] Смещение в байтах от начала `pAddress` параметра.  
  
 `pdwVersion`  
 [out] Номер версии метода.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)