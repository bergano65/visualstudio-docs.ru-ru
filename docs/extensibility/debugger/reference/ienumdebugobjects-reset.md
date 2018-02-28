---
title: "IEnumDebugObjects::Reset | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugObjects::Reset
helpviewer_keywords:
- IEnumDebugObjects::Reset method
ms.assetid: 4a245e47-cc39-4177-b83d-083ea0e3190f
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ad2044d73957bb5df7f3c7ebccb12e7c8bafc4e2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugobjectsreset"></a>IEnumDebugObjects::Reset
Этот метод сбрасывает перечисления на первый элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Reset(void);  
```  
  
```csharp  
int Reset();  
```  
  
#### <a name="parameters"></a>Параметры  
 Нет  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 После вызова этого метода, при следующем вызове [Далее](../../../extensibility/debugger/reference/ienumdebugobjects-next.md) возвращает первый элемент перечисления.  
  
## <a name="see-also"></a>См. также  
 [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)   
 [Вперед](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)