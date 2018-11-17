---
title: IDebugProgram2 | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2
helpviewer_keywords:
- IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e0f89f024f0542b8cb20cfbf531fe9f7cf3da561
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741081"
---
# <a name="idebugprogram2"></a>IDebugProgram2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс представляет программу, которая выполняется в процессе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) и поставщика пользовательского порта реализуют этот интерфейс для представления программы в процессе. Диспетчер отладки сеансов (SDM) также реализует этот интерфейс для предоставления сведений о [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md).  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) событие возвращает этот интерфейс для новой программы. Этот интерфейс также используется в качестве параметра для многих методов на нескольких интерфейсах.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugProgram2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Перечисляет потоков, которые выполняются в этой программе.|  
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Возвращает имя программы.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Возвращает процесс, в работе программы.|  
|[Terminate](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|Завершает работу этой программы.|  
|[Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Присоединяет к этой программе.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Определяет, если отладчик (DE) можно отсоединить от программы.|  
|[Detach](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Отключает отладчик от этой программы.|  
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Получает глобальный уникальный идентификатор для этой программы.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Получает программировать свойства.|  
|[Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Продолжает выполнение программы в остановленном состоянии. Все предыдущие состояния выполнения очищается.|  
|[Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Продолжает выполнение программы в остановленном состоянии. Сохраняется все предыдущие состояния выполнения.|  
|[Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Выполняет шаг.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Запрашивает, чтобы эта программа остановил выполнение следующего время один из его потоков выполняет код.|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Возвращает имя и идентификатор для обработчика отладки (DE), выполнение программы.|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Перечисляет контексты кода для заданной позиции в исходном файле.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Получает байты памяти для этой программы.|  
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Возвращает поток Дизассемблированный код для этой программы или часть этой программы.|  
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Перечисляет модули, которые эта программа загрузки и выполнения.|  
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Получает обновления изменить и продолжить "(ENC) для этой программы.<br /><br /> Этот метод не устанавливает пользовательского модуля отладки (всегда должны возвращать `E_NOTIMPL`).|  
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Перечисляет пути кода данной программы.|  
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Записывает в файл дампа.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Примечания  
 Программы — это контейнер поток, выполняться в конкретной архитектуры среды выполнения, а процесс состоит из одной или нескольких программ.  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [Далее](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [Событие](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Присоединение](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)

