---
title: IDebugEngineProgram2::Stop | Документация Майкрософт
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
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 29067ce022150f53612ba053cee5ce20c2c96fa6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572456"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugEngineProgram2::Stop](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugengineprogram2-stop).  
  
Останавливает все потоки, выполняющиеся у этой программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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

