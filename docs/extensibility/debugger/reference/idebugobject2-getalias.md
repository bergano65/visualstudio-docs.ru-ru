---
title: IDebugObject2::GetAlias | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugObject2::GetAlias
helpviewer_keywords:
- IDebugObject2::GetAlias method
ms.assetid: aa6824d5-c932-42ba-8713-950e7d1fb42f
caps.latest.revision: 7
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a487043d6c046a9c117c4845d56db2f18bf51896
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugobject2getalias"></a>IDebugObject2::GetAlias
Получает псевдоним, связанный с этим объектом, если таковая имеется.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetAlias(  
   IDebugAlias** ppAlias  
);  
```  
  
```csharp  
int GetAlias(  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppAlias`  
 [out] Возвращает [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) объект, представляющий псевдоним для этого объекта; в противном случае возвращает значение null.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Псевдоним для объекта создается с помощью вызова [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)