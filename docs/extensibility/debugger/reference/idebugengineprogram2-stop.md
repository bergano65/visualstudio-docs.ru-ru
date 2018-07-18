---
title: IDebugEngineProgram2::Stop | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ab5bec65dc3f53681d40743bea694295ff69944b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31113859"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
Остановка всех потоков в этой программе.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Stop(   
   void   
);  
```  
  
```csharp  
int Stop();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается, когда эта программа выполняется отладка в среде с несколькими программы. При получении события остановки из другой программы, этот метод вызывается для данной программы. Реализация этого метода должен быть асинхронным; то есть не все потоки не требуется быть остановлена перед возвратом этот метод. Реализация этого метода может быть достаточно вызвать метод [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) метод для данной программы.  
  
 Событие отладки не отправляется в ответ на этот метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)