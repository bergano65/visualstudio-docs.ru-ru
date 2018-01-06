---
title: "IDebugEngine2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine2
helpviewer_keywords: IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 95a1a8c48bd6eab0f21ccc85a125b5d10f42ef4e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugengine2"></a>IDebugEngine2
Этот интерфейс представляет модуля отладки (DE). Он используется для управления различными аспектами сеанса отладки, от создания точки останова для установки и очистки исключения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Этот интерфейс реализуется пользовательский DE для управления отладки программ. Этот интерфейс должен быть реализован DE.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Этот интерфейс называется диспетчером сеанса отладки (SDM) для сеанса отладки, включая Управление исключениями, Создание точки останова и отвечает на отправленные DE синхронные события управления.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugEngine2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Создает перечислитель для всех программ, для которого выполняется отладка, DE.|  
|[Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Присоединяет Развернутой программы.|  
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|Создает ожидающая точка останова в DE.|  
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Указывает порядок обработки DE данного исключения.|  
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Удаляет указанное исключение, чтобы оно больше не обработано ядро отладки.|  
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|Удаляет из списка исключений, заданные в Интегрированной среде разработки для конкретной архитектуры во время выполнения или языка.|  
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Возвращает идентификатор GUID DE.|  
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Сообщает, DE, необычайно завершен указанную программу, которую необходимо удалить все ссылки на программу и отправить программы DE уничтожения события.|  
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|Вызывается средой SDM для указания получена и обработать событие синхронной отладки, ранее отправленные DE SDM.|  
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|Задает языковой стандарт DE.|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Задает корневой раздел реестра, в настоящее время используется DE.|  
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Задает метрики.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Запросы, все программы, отладку этого DE остановить выполнение при очередном одного из своих потоков попытается запустить.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)