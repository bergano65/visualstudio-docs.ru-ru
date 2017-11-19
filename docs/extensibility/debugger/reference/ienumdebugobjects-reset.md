---
title: "IEnumDebugObjects::Reset | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugObjects::Reset
helpviewer_keywords: IEnumDebugObjects::Reset method
ms.assetid: 4a245e47-cc39-4177-b83d-083ea0e3190f
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e7b42e3b57752af5ab1e6086711ab020b5ee7946
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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