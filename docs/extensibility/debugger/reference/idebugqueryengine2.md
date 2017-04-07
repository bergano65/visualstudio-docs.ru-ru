---
title: "IDebugQueryEngine2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
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
ms.openlocfilehash: cdf774a97ef3b1d0bfeec0be8482d2c116806885
ms.lasthandoff: 04/05/2017

---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
Этот интерфейс позволяет сеанса, диспетчер отладочной (SDM) получить интерфейс, который представляет модуль отладки (DE).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugQueryEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 DE реализует этот интерфейс для объектов, которые реализуют интерфейсы наиболее распространенные DE (такие как [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md), и [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)) для получения доступа к [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) DE, сам интерфейс.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызовите [QueryInterface](/cpp/atl/queryinterface) на типичный DE-интерфейс для получения этого интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugQueryEngine2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Получает интерфейс отладочных ядра (DE).|  
  
## <a name="remarks"></a>Примечания  
 Обычно этот интерфейс реализуется в объект, реализующий [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) интерфейс для поддержки упорядоченные причинно-следственных связей пошаговое выполнение функции; т. е когда отладчик находится шаг с выходом из функции, исполнение функции могут не быть предыдущей функции в стеке, но функции в другом потоке полностью. Определение «причинно-следственных связей» см. в разделе [глоссарий отладчик Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
