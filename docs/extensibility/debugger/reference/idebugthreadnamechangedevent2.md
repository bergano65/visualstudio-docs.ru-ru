---
title: "IDebugThreadNameChangedEvent2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugThreadNameChangedEvent2
helpviewer_keywords:
- IDebugThreadNameChangedEvent2
ms.assetid: 34c1652e-f019-48ba-8b26-ace20f8a158c
caps.latest.revision: 10
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d57362fa76e5131976a72a77dc030e7a2b117d62
ms.lasthandoff: 02/22/2017

---
# <a name="idebugthreadnamechangedevent2"></a>IDebugThreadNameChangedEvent2
Этот интерфейс отправляется ядром отладки (DE) диспетчера сеанса отладки (SDM) при изменении имени потока в отлаживаемой программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugThreadNameChangedEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 DE реализует этот интерфейс для отчета об изменении имени потока. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) на тот же объект, как этот интерфейс должен быть реализован интерфейс. Использует SDM [QueryInterface](/visual-cpp/atl/queryinterface) для доступа к `IDebugEvent2` интерфейс.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 DE создает и отправляет этот объект события для отчета об изменении имени потока. Это событие отправляется с помощью [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) функции обратного вызова, предоставляемую SDM, когда он присоединен к отлаживаемой программы.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
