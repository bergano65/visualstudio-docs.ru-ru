---
title: "IDebugEngineProgram2::Stop | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngineProgram2::Stop
helpviewer_keywords: IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 21dd14e1cc4d4e8c6b65b5285763a680a5f327f7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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