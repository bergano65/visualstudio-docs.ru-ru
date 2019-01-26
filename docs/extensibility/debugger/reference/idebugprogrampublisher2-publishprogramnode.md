---
title: IDebugProgramPublisher2::PublishProgramNode | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramPublisher2::PublishProgramNode
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgramNode
ms.assetid: d4b72e04-f726-46cf-8e56-5203ff205b12
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db439ebf40d09b822d998ba7b9baf28c7c56e199
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55003036"
---
# <a name="idebugprogrampublisher2publishprogramnode"></a>IDebugProgramPublisher2::PublishProgramNode
Делает узел программы доступными для использования отладчиков (DEs) и сеанс отладки manager (SDM).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT PublishProgramNode(  
   IDebugProgramNode2 *pProgramNode  
);  
```  
  
```csharp  
int PublishProgramNode(  
   IDebugProgramNode2 pProgramNode  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pProgramNode`  
 [in] [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , представляющий узел программы, чтобы сделать доступными.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод позволяет программам требуется запросить сведения до выбора и запуска их для отладки.  
  
 Чтобы удалить узел программы с доступностью, вызовите [UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)