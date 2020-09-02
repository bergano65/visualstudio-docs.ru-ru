---
title: 'IDebugEngineProgram2:: останавливается | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cb74cb2940a91bbc64fa4a06f28d07a828357fc6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431489"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Останавливает все потоки, выполняющиеся в этой программе.  
  
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
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Этот метод вызывается при отладке этой программы в среде с несколькими программами. При получении события остановки от какой-либо другой программы этот метод вызывается в этой программе. Реализация этого метода должна быть асинхронной; то есть не все потоки должны быть остановлены перед возвратом этого метода. Реализация этого метода может быть такой же простой, как вызов метода [каусебреак](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) в этой программе.  
  
 В ответ на этот метод не отправляется событие отладки.  
  
## <a name="see-also"></a>См. также:  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
