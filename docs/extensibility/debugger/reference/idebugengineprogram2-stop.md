---
title: IDebugEngineProgram2::Stop | Документация Майкрософт
ms.date: 11/04/2016
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
ms.openlocfilehash: 089b8c14db3caa1c9f4b3a2ad0a364bcfbb5a096
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53840360"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
Останавливает все потоки, выполняющиеся у этой программы.  
  
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
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается, когда эта программа отлаживается в среде с несколькими программы. При получении событии остановки из другой программы, этот метод вызывается для данной программы. Реализация этого метода должен быть асинхронным; то есть не все потоки должен обязательно быть остановлена перед возвратом этот метод. Реализация этого метода может быть простым вызовом [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) метод для данной программы.  
  
 Событие отладки не отправляется в ответ на этот метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)