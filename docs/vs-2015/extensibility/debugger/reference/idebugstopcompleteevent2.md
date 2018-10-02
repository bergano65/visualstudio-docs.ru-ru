---
title: IDebugStopCompleteEvent2 | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f880888ab675fc7923b50e3b1fbce144f8108abd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570757"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugStopCompleteEvent2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugstopcompleteevent2).  
  
Модуль отладки (DE) можно отправлять это необязательное событие диспетчер отладки сеансов (SDM) после остановки программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Это новый интерфейс для [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)]. Предыдущие версии не поддерживает асинхронной остановки.  
  
 [Остановить](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) вызывается SDM в сценариях с несколькими процессами или несколькими программы. Если для одной из них отправляет событие stopping SDM, SDM запрашивает другие программы, чтобы остановить, слишком.  
  
 Он используется для асинхронного информирования SDM, который перестал программы. Это полезно для обработчика отладки интерпретатор, где иногда код не выполняется внутри переместится на отлаживаемую программу, поэтому [остановить](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) не может быть завершена синхронно. Если модуль отладки хочет использовать этот асинхронное уведомление, оно должно возвращать `S_ASYNC_STOP` из [остановить](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

