---
title: IDebugAlias::GetObject | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugAlias::GetObject
helpviewer_keywords:
- IDebugAlias::GetObject method
ms.assetid: 97bc3af6-6e55-4940-8a6d-692c61257806
caps.latest.revision: 7
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: e1b96592e54e36d63da124e1a239430995bfaec5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugaliasgetobject"></a>IDebugAlias::GetObject
Возвращает объект, этот псевдоним.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetObject(  
   IDebugObject2** ppObject  
);  
```  
  
```csharp  
int GetObject(  
   Out IDebugObject2 ppObject  
)  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppObject`  
 [out] [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) представляет этот псевдоним.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)