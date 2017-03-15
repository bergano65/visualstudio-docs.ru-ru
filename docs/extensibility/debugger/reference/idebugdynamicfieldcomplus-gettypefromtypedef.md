---
title: "IDebugDynamicFieldCOMPlus::GetTypeFromTypeDef | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetTypeFromTypeDef"
  - "IDebugDynamicFieldCOMPlus::GetTypeFromTypeDef"
ms.assetid: 7f6cd3d3-f4da-4893-be91-8dd104be8010
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDynamicFieldCOMPlus::GetTypeFromTypeDef
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает тип заданного свой маркер.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetTypeFromTypeDef(  
   ULONG32       ulAppDomainID,  
   GUID          guidModule,  
   _mdToken      tokClass,  
   IDebugField** ppType  
);  
```  
  
```c#  
int GetTypeFromTypeDef(  
   uint            ulAppDomainID,  
   Guid            guidModule,  
   int             tokClass,  
   out IDebugField ppType  
);  
```  
  
#### Параметры  
 `ulAppDomainID`  
 \[in\] идентификатор домена приложения.  
  
 `guidModule`  
 \[in\] уникальный идентификатор модуля.  
  
 `tokClass`  
 \[in\] маркер, представляющий тип.  
  
 `ppType`  
 \[out\] возвращает [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) объект, который содержит тип.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)