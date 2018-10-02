---
title: IDebugProgramNodeAttach2::OnAttach | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 73e81537ce73a5b7677174d4694ece16a2a823b7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562571"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugProgramNodeAttach2::OnAttach](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogramnodeattach2-onattach).  
  
Присоединяется к соответствующую программу или откладывает процесс присоединения к [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT OnAttach(  
   [in] REFGUID guidProgramId  
);  
```  
  
```csharp  
int OnAttach(  
   ref Guid guidProgramId  
};  
```  
  
#### <a name="parameters"></a>Параметры  
 `guidProgramId`  
 [in] `GUID` Чтобы назначить соответствующую программу.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`. Возвращает `S_FALSE` Если [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) не следует вызывать метод. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается во время присоединения, прежде чем [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) вызывается метод. `OnAttach` Метод может выполнить сам процесс attach (в этом случае этот метод возвращает `S_FALSE`) или отложить процесс присоединения к `IDebugEngine2::Attach` метод ( `OnAttach` возвращает метод `S_OK`). В любом случае `OnAttach` можно задать метод `GUID` программы, отлаживаемой в данный `GUID`.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)

