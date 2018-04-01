---
title: IDebugEngine2::SetException | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngine2::SetException
helpviewer_keywords:
- IDebugEngine2::SetException
ms.assetid: e6f5ec48-09e8-4b9b-9dc9-55f8d883f1b7
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: aa9ad865c3458c02ccdec95c6cb1f8e4fc68f8f8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugengine2setexception"></a>IDebugEngine2::SetException
Указывает порядок обработки данного исключения отладчик (DE).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetException(   
   EXCEPTION_INFO* pException  
);  
```  
  
```csharp  
int SetException(   
   EXCEPTION_INFO[] pException  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pException`  
 [in] [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) структура, описывающая исключение и как отладить его.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 DE удалось предложено остановить программу возникновения исключений во первый шанс обработки, вторую вероятность, либо не перезаписываются вообще.  
  
## <a name="see-also"></a>См. также  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)