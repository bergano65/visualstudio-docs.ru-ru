---
title: IDebugEngineLaunch2::CanTerminateProcess | Документация Майкрософт
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
- IDebugEngineLaunch2::CanTerminateProcess
helpviewer_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
ms.assetid: 7973454d-c957-4123-a0ee-80ebcdbbd2d1
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fada150f87fc8e5fbf192a41d668aa61bc77daf1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51742809"
---
# <a name="idebugenginelaunch2canterminateprocess"></a>IDebugEngineLaunch2::CanTerminateProcess
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Определяет, может быть завершен процесс.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT CanTerminateProcess (   
   IDebugProcess2* pProcess  
);  
```  
  
```csharp  
int CanTerminateProcess (   
   IDebugProcess2 pProcess  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pProcess`  
 [in] [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) , представляющий к завершению процесса.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращает `S_FALSE` Если ядро невозможно завершить процесс, к примеру, так как отказано в доступе.  
  
## <a name="remarks"></a>Примечания  
 Если этот метод возвращает `S_OK`, затем его [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md) метод может вызываться действительности завершить процесс.  
  
## <a name="see-also"></a>См. также  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)

