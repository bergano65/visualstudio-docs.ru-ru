---
title: "IDebugEngineProgram2::WatchForThreadStep | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords: IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 473deca83bea9e2fea9c52d2836291790def5804
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
Следит за выполнение (или останавливает наблюдением за выполнения) или делать это в данном потоке.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
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
 [in] [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) объект, представляющий программе шаг с заходом.  
  
 `dwTid`  
 [in] Указывает идентификатор потока для отслеживания.  
  
 `fWatch`  
 [in] Не равно нулю (`TRUE`) означает начать просмотр для выполнения потока, определяемый `dwTid`; в противном случае — нуль (`FALSE`) означает остановка наблюдения для выполнения на `dwTid`.  
  
 `dwFrame`  
 [in] Указывает индекс кадра, который определяет тип шага. Если это значение равно нулю (0), тип шага — «шаг с заходом» и программе следует остановить всякий раз, когда поток определяется `dwTid` выполняет. Когда `dwFrame` имеет ненулевое значение, тип шага — «шаг с обходом» и программе следует остановить только в том случае, если поток определяется `dwTid` работает в кадре, индекс которого равен или выше в стеке, чем `dwFrame`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Когда диспетчер сеанса отладки (SDM) шагов программы, определяемый `pOriginatingProgram` параметра, он уведомляет всех остальных присоединенных программ путем вызова данного метода.  
  
 Этот метод применим только к пошаговое выполнение в одном потоке.  
  
## <a name="see-also"></a>См. также  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)