---
title: 'IDebugEngineProgram2:: Ватчфорсреадстеп | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 59489af368c2e95a2d3cc93edbd6f7ab02a1c156
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195655"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Наблюдает за выполнением (или останавливает наблюдение за выполнением) в заданном потоке.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT WatchForThreadStep(   
   IDebugProgram2* pOriginatingProgram,  
   DWORD           dwTid,  
   BOOL            fWatch,  
   DWORD           dwFrame  
);  
```  
  
```csharp  
int WatchForThreadStep(   
   IDebugProgram2 pOriginatingProgram,  
   uint           dwTid,  
   int            fWatch,  
   uint           dwFrame  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pOriginatingProgram`  
 окне Объект [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , представляющий программу, для которой выполняется пошаговое выполнение.  
  
 `dwTid`  
 окне Указывает идентификатор потока для отслеживания.  
  
 `fWatch`  
 окне Ненулевое значение ( `TRUE` ) означает начало наблюдения за потоком, определяемым `dwTid` ; в противном случае нуль ( `FALSE` ) означает завершение наблюдения за выполнением `dwTid` .  
  
 `dwFrame`  
 окне Указывает индекс кадра, который управляет типом шага. Если это значение равно нулю (0), то тип шага — «шаг с заходом», и программа должна останавливаться всякий раз, когда поток определяется по `dwTid` выполнению. Если `dwFrame` имеет ненулевое значение, то шаг имеет тип «шаг с обходом», и программа должна останавливаться только в том случае, если поток, идентифицированный, `dwTid` выполняется в кадре, индекс которого равен или выше в стеке, чем `dwFrame` .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Когда диспетчер отладки сеансов (SDM) выводит программу, определяемую `pOriginatingProgram` параметром, она уведомляет все другие подключенные программы, вызывая этот метод.  
  
 Этот метод применим только к степпингу одного потока.  
  
## <a name="see-also"></a>См. также:  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
