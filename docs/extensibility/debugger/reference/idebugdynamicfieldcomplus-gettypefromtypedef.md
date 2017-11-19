---
title: "IDebugDynamicFieldCOMPlus::GetTypeFromTypeDef | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GetTypeFromTypeDef
- IDebugDynamicFieldCOMPlus::GetTypeFromTypeDef
ms.assetid: 7f6cd3d3-f4da-4893-be91-8dd104be8010
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4ff4d4df3051719e62af2b0a2fad8a238387ba5b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdynamicfieldcomplusgettypefromtypedef"></a>IDebugDynamicFieldCOMPlus::GetTypeFromTypeDef
Возвращает тип, указанному токену.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetTypeFromTypeDef(  
   ULONG32       ulAppDomainID,  
   GUID          guidModule,  
   _mdToken      tokClass,  
   IDebugField** ppType  
);  
```  
  
```csharp  
int GetTypeFromTypeDef(  
   uint            ulAppDomainID,  
   Guid            guidModule,  
   int             tokClass,  
   out IDebugField ppType  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ulAppDomainID`  
 [in] Идентификатор домена приложения.  
  
 `guidModule`  
 [in] Уникальный идентификатор модуля.  
  
 `tokClass`  
 [in] Токен, представляющий тип.  
  
 `ppType`  
 [out] Возвращает [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , содержащий тип.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)