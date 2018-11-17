---
title: IDebugEngine2::DestroyProgram | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngine2::DestroyProgram
helpviewer_keywords:
- IDebugEngine2::DestroyProgram
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f303fb7e5afbca1822d2bb735d161cfad7a5d3c8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51816337"
---
# <a name="idebugengine2destroyprogram"></a>IDebugEngine2::DestroyProgram
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Информирует модуля отладки (DE), то программа, указанная операция была прервана необычайно и что DE следует удалить все ссылки на программы и события уничтожения отправки программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT DestroyProgram(   
   IDebugProgram2* pProgram  
);  
```  
  
```cpp#  
int DestroyProgram(   
   IDebugProgram2 pProgram  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pProgram`  
 [in] [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , представляющий программу, которая необычайно был завершен.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 После вызова этого метода, DE отправляет [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) событие диспетчер отладки сеансов (SDM).  
  
 Этот метод не реализован (возвращает `E_NOTIMPL`) Если DE выполняется в том же процессе, что отлаживаемой программы. Этот метод реализуется только в том случае, если DE выполняется в том же процессе, что SDM.  
  
## <a name="see-also"></a>См. также  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

