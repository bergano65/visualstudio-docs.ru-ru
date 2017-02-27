---
title: "IDebugSymbolProviderDirect::GetMethodFromAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSymbolProviderDirect::GetMethodFromAddress"
  - "GetMethodFromAddress"
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSymbolProviderDirect::GetMethodFromAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Получить данные о конкретном методе на отладочные адрес.  
  
## Синтаксис  
  
```cpp#  
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
  
```c#  
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
  
#### Параметры  
 `pAddress`  
 \[in\] адрес, представленного отладки [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) интерфейс.  
  
 `pGuid`  
 \[out\] уникальный идентификатор модуля.  
  
 `pAppID`  
 \[out\] идентификатор домена приложения.  
  
 `pTokenClass`  
 \[out\] маркер, представляющий содержащий класс.  
  
 `pTokenMethod`  
 \[out\] маркер, представляющий модуль.  
  
 `pdwOffset`  
 \[out\] смещение в байтах от начала `pAddress` параметр.  
  
 `pdwVersion`  
 \[out\] номер версии метода.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)