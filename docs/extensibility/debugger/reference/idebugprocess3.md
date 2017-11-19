---
title: "IDebugProcess3 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess3
helpviewer_keywords: IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cc6c8fe7553a1fdff43875ec305978ea4f983843
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocess3"></a>IDebugProcess3
Этот интерфейс представляет выполняющемуся процессу и его программ. Этот интерфейс существует как на замену в несколько методов [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) интерфейса. Она обеспечивает контроль над все программы, в процессе.  
  
> [!NOTE]
>  [Продолжить](../../../extensibility/debugger/reference/idebugprogram2-continue.md), [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md), и [шаг](../../../extensibility/debugger/reference/idebugprogram2-step.md) методы считаются устаревшими и больше не может использоваться. Использовать соответствующие методы `IDebugProcess3` интерфейса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugProcess3 : IDebugProcess2  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Этот интерфейс реализуется пользовательский порт поставщика для управления программами в группу. При управлении программы как группу, можно управлять их выполнением и установить язык для вычислитель выражений. Этот интерфейс должен быть реализован поставщиком порта.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Этот интерфейс называется главным образом диспетчером сеанса отладки (SDM) для взаимодействия с группой программы, указанные в этом процессе.  
  
 Вызовите [QueryInterface](/cpp/atl/queryinterface) на [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) интерфейс для получения этого интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 Помимо методов, наследуемых от [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md), `IDebugProcess3` реализует следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Продолжает выполнение или пошаговое выполнение процесса.|  
|[Выполнение](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Начинает выполнение процесса.|  
|[Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Шаги Переслать одну инструкцию или инструкции в процессе.|  
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Возвращает причину, что процесс был запущен для отладки.|  
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Задает язык, размещения, чтобы модуль отладки можно загрузить соответствующий выражений.|  
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Получает текущий язык для этого процесса.|  
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Отключает Изменить и продолжить (ENC) для этого процесса.<br /><br /> Поставщик другой номер порта не реализует этот метод (всегда должны возвращать `E_NOTIMPL`).|  
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Получает состояние ENC для этого процесса.<br /><br /> Поставщик другой номер порта не реализует этот метод (всегда должны возвращать `E_NOTIMPL`).|  
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Извлекает массив уникальных идентификаторов для Доступные отладчики.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)