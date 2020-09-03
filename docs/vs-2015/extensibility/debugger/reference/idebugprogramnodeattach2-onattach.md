---
title: 'IDebugProgramNodeAttach2:: onattach | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 845ec66215c5d999aaf3b5c9658bc0fb8e7295a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148545"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Присоединяется к связанной программе или откладывает процесс присоединения к методу [attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) .  
  
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
 [входные] `GUID` для назначения связанной программе.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает значение `S_FALSE` , если метод [attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) не должен вызываться. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Этот метод вызывается во время процесса присоединения до вызова метода [attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) . `OnAttach`Метод может выполнить сам процесс присоединения (в этом случае этот метод возвращает `S_FALSE` ) или отложить процесс присоединения к `IDebugEngine2::Attach` методу ( `OnAttach` метод возвращает `S_OK` ). В любом из этих событий `OnAttach` метод может задать для `GUID` отлаживаемой программы заданный объект `GUID` .  
  
## <a name="see-also"></a>См. также:  
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
