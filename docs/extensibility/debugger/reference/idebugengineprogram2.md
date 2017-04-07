---
title: "IDebugEngineProgram2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 2897213b9c94a2c8a140c12bfdbc3d4deb29052e
ms.lasthandoff: 04/05/2017

---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
Этот интерфейс обеспечивает поддержку многопоточных отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugEngineProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки реализует этот интерфейс для поддержки одновременная отладка нескольких потоков. Этот интерфейс реализуется на тот же объект, реализующий [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) интерфейса.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Используйте [QueryInterface](/cpp/atl/queryinterface) получить этот интерфейс из `IDebugProgram2` интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugEngineProgram2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Остановить](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Остановка всех потоков в этой программе.|  
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Следит за выполнение (или остановки наблюдения за выполнения) или делать это в данном потоке.|  
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Разрешает или запрещает вычисления выражения для данного потока, даже если программа остановлена.|  
  
## <a name="remarks"></a>Примечания  
 Visual Studio вызывает этот интерфейс в ответ на [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) событий и для задания «Контрольные значения для шаг потоков» и «Контрольное значение для выражения вычисления в потоке» состояния программы. [Остановить](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) вызывается каждый раз, когда нужно остановить программу; этот метод дает программе возможность завершить все потоки.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
