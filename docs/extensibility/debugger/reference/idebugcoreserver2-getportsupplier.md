---
title: "IDebugCoreServer2::GetPortSupplier | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCoreServer2::GetPortSupplier
helpviewer_keywords: IDebugCoreServer2::GetPortSupplier
ms.assetid: acf181d4-ef42-4aa5-86f9-95fd5467ea31
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e03a3f73ac98ae736d719201444255dff18273e9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcoreserver2getportsupplier"></a>IDebugCoreServer2::GetPortSupplier
Извлекает поставщик определенный порт.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetPortSupplier(   
   REFGUID               guidPortSupplier,  
   IDebugPortSupplier2** ppPortSupplier  
);  
```  
  
```csharp  
int GetPortSupplier(   
   ref Guid                guidPortSupplier,  
   out IDebugPortSupplier2 ppPortSupplier  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `guidPortSupplier`  
 [in] Идентификатор GUID поставщика порта, который требуется получить.  
  
 `ppPortSupplier`  
 [out] Возвращает [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) объект, предоставляющий сведения о поставщике нужный порт.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)