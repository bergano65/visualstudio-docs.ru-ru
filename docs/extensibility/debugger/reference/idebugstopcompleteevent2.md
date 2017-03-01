---
title: "IDebugStopCompleteEvent2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: 6
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
ms.openlocfilehash: 55061440f4690c9b9f9b7a90dc5474391f908046
ms.lasthandoff: 02/22/2017

---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
Отладчик (DE) можно отправлять этот необязательный элемент события диспетчера сеанса отладки (SDM) после остановки программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Это новый интерфейс [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]. Предыдущие выпуски не поддерживает асинхронной остановки.  
  
 [Остановить](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) вызывается SDM в сценариях с несколькими процессами или несколькими программы. Когда одна программа отправляет событие остановки SDM, SDM запрашивает другие программы, чтобы остановить слишком.  
  
 Он используется для информирования SDM, которая перестала программу асинхронно. Это полезно для отладки механизм интерпретатор, где иногда код не работает в отлаживаемой программы, [остановить](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) не может быть завершена синхронно. Если отладчик хочет использовать асинхронные уведомления, она должна вернуть `S_ASYNC_STOP` из [остановить](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
