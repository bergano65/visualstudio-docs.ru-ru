---
title: "IDebugProgram2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2"
helpviewer_keywords: 
  - "Интерфейс IDebugProgram2"
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# IDebugProgram2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет программу, которая выполняется в процессе.  
  
## Синтаксис  
  
```  
IDebugProgram2 : IUnknown  
```  
  
## Примечания по реализации  
 Отладчик \(DE\) и пользовательского поставщика порта реализуйте этот интерфейс для представления программу в процессе.  Сеанс отладки \(SDM\) диспетчер также реализует этот интерфейс, чтобы предоставить сведения [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md).  
  
## Замечания для вызывающих объектов  
 IDebugProgramCreateEvent2 событие возвращает этот интерфейс для новой программы.  Этот интерфейс также используется в качестве параметра для многих методов на нескольких интерфейсах.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugProgram2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Перечисляет потоки, работающие в этой программе.|  
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Возвращает имя программы.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Возвращает процесс, что эта программа выполняется.|  
|[Завершить](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|Завершает этой программы.|  
|[Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Вложение в этой программе.|  
|[CanDetach](../Topic/IDebugProgram2::CanDetach.md)|Определяет, если обработчик отладки \(DE\) может наконец удалить из программы.|  
|[Detach](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Наконец удаляет отладчик из этой программы.|  
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Возвращает глобальный уникальный идентификатор для этой программы.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Возвращает свойства программы.|  
|[Выполнение](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Продолжает выполнять эту программу от остановленного состояния.  Любое предыдущее состояние выполнения.|  
|[Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Продолжает выполнять эту программу от остановленного состояния.  Любое предыдущее состояние выполнения сохраняются.|  
|[Шаг](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Выполняет шаг.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Запросы, что эта программа останавливает выполнение при следующем запуске одного из своих потоков выполняют код.|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Получает имя обработчика отладки и идентификатор \(DE\) при выполнении этой программы.|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Перечисляет контексты кода для заданной позиции в файле источника.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Возвращает байты памяти для этой программы.|  
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Получает поток, дизассемблированный код для этих программ или части этой программы.|  
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Перечисляет модули, эта программа нагружала и выполняется.|  
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Возвращает правку и продолжить обновление \(ENCL\) для этой программы.<br /><br /> Пользовательский обработчик отладки не реализует этот метод \(она должна всегда возвращать `E_NOTIMPL`\).|  
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Перечисляет пути кода этой программы.|  
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Записывает в файл дампа.|  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Заметки  
 Программа работы контейнера потока в заданной архитектуры среды выполнения, пока процесс состоит из одного или нескольких программ.  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProgram](../Topic/IDebugThread2::GetProgram.md)   
 [Далее](../Topic/IEnumDebugPrograms2::Next.md)   
 [Событие](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)