---
title: "IDebugProcess2::GetPhysicalProcessId | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess2::GetPhysicalProcessId
helpviewer_keywords: IDebugProcess2::GetPhysicalProcessId
ms.assetid: 77da6e10-75af-4308-97dd-c44416ca52d7
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 526a301f58429e449aeac106ce0b986e5059a33c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocess2getphysicalprocessid"></a>IDebugProcess2::GetPhysicalProcessId
Получает идентификатор процесса системы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetPhysicalProcessId(  
   AD_PROCESS_ID* pdwProcessId  
);  
```  
  
```csharp  
int GetPhysicalProcessId(  
   AD_PROCESS_ID[] pdwProcessId  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdwProcessId`  
 [out] [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) структуру, которая содержит идентификатор процесса сведения о системе.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)