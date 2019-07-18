---
title: IDebugEntryPointEvent2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEntryPointEvent2
helpviewer_keywords:
- IDebugEntryPointEvent2 interface
ms.assetid: a15d1cc3-97b7-438c-8d24-c23149708f42
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 22d7c663dbd1c9c397e7145c9dea74c8424e4383
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65689182"
---
# <a name="idebugentrypointevent2"></a>IDebugEntryPointEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Модуль отладки (DE) отправляет этот интерфейс диспетчер отладки сеансов (SDM) в том случае, когда программа близок к выполнению первой инструкции кода пользователя.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugEntryPointEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 DE реализует этот интерфейс в процессе обычной работы. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) интерфейс должен быть реализован на один и тот же объект как следующий интерфейс. Использует SDM [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) для доступа к `IDebugEvent2` интерфейс.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 DE создает и отправляет этот объект события, когда отлаживаемой программы было загружено и готов к выполнению первой инструкции кода пользователя. Это событие отправляется с помощью [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) функцию обратного вызова, предоставляемую SDM, если он присоединен к отлаживаемой программы.  
  
## <a name="remarks"></a>Примечания  
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) отправляется, когда программа является близок к выполнению очень первой инструкции. Например `IDebugEntryPoint2` отправляется, когда программа является близок к выполнению пользователя `main` функции.  
  
 При отправке DE `IDebugEntryPointEvent2`, текущая позиция кода должно представлять в первой инструкции кода пользователя, например `main`.  
  
## <a name="requirements"></a>Требования  
 Header: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
