---
title: Основные интерфейсы | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 791e76b462a7ae12ac11b9eb5f33c94baff49888
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53919577"
---
# <a name="core-interfaces"></a>Базовые интерфейсы
Следующие интерфейсы являются базовых интерфейсов расширения отладчика с помощью [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)].  

## <a name="discussion"></a>Обсуждение  
 Эти интерфейсы используются главным образом для создания обработчика отладки (DE). Здесь они организованы по категориям:  

- [Точки останова](#Breakpoints)  

- [Контексты](#Contexts)  

- [Core Server](#CoreServer)  

- [Модули отладки](#DebugEngines)  

- [Документы](#Documents)  

- [События](#Events)  

- [Выражения](#Expressions)  

- [Память](#Memory)  

- [Модули](#Modules)  

- [Порты](#Ports)  

- [Процессы](#Processes)  

- [Программы](#Programs)  

- [Свойства](#Properties)  

- [Кадры стека](#StackFrames)  

- [Потоки](#Threads)  

- [Визуализаторы типа](#TypeVisualizers)  

  Сущности, которые могут реализовать интерфейсы являются:  

- Отладка ядра (DE)  

- Поставщика порта (PS)  

- Средство оценки выражений (EE)  

- Visual Studio (VS)  

##  <a name="Breakpoints"></a> Точки останова  
 Эти интерфейсы, относящиеся к реализации и отслеживания точек останова.  

|Интерфейс|Реализуется|Описание:|  
|---------------|--------------------|-----------------|  
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|Представляет точку останова, привязанным к точке памяти.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Отправленные DE при привязке точку останова на адрес памяти.|  
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|Представляет контрольную сумму документа для запроса точки останова.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Отправленные DE, когда не удается привязать к ячейке памяти точки останова.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Отправленные DE при достижении точки останова.|  
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|Представляет запрос для точки останова; использовать при создании ожидающая точка останова.|  
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|Представляет запрос для точки останова; использовать при создании ожидающая точка останова.|  
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|Представляет сведения, используемые для привязки точку останова.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Посылается элементом DE, в то время когда отменяется точку останова из области памяти.|  
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|Представляет недопустимой точки останова (возвращенный `IDebugBreakpointErrorEvent2`).|  
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|Представляет разрешение сведения о недопустимой точки останова.|  
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|Представляет позицию в функции, где установлена точка останова.|  
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|Представляет точку останова, который должен быть привязан; использовать при создании связанная точка останова.|  
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|Представляет перечисление по набору связанных точек останова.|  
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|Представляет перечисление через набор точек останова, которые не удалось выполнить привязку на адрес памяти.|  

##  <a name="Contexts"></a> Контексты  
 Эти интерфейсы представляют различные контексты в отлаживаемой программы.  

|Интерфейс|Реализуется|Описание:|  
|---------------|--------------------|-----------------|  
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|Представляет начальную позицию инструкции кода.|  
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|Расширяет [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) интерфейс, чтобы обеспечить получение модулей и процессов.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Представляет позицию в документе.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Представляет контекст, в котором вычисляется выражение.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Представляет начальное расположение в памяти коллекции байтов.|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Представляет контекст кадра стека в точки останова или исключение.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Представляет контекст кадра стека в точки останова или исключение.|  
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|Представляет перечисление через набор контекстов кода.|  

##  <a name="CoreServer"></a> Core Server  
 Эти интерфейсы являются компьютера, на котором выполняется отладка программы. Они реализованы с [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] , но могут быть вызваны в отладчиков.  

|Интерфейс|Реализуется|Описание|  
|---------------|--------------------|-----------------|  
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|Предоставляет доступ к портам и поставщикам портов, а также сведения о компьютере.|  
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|Представляет [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) , поддерживает удаленную отладку.|  

##  <a name="DebugEngines"></a> Модули отладки  
 Эти интерфейсы являются обработчикам отладки и связанные с ними события.  

|Интерфейс|Реализуется|Описание:|  
|---------------|--------------------|-----------------|  
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|Представляет пользовательского модуля отладки.|  
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|Представляет пользовательского модуля отладки, поддерживает загрузку символов, JustMyCode и исключения.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Отправленные каждого нового экземпляра DE, чтобы указать, что он готов для обработки задачи отладки.|  
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|Представляет пользовательского модуля отладки, поддерживает запуск программ.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Представляет узел программы, который обрабатывает несколько ядер отладки.|  
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|Предоставляет способ для SDM получить интерфейс для обработчика отладки из потока, программы или кадр стека.|  

##  <a name="Documents"></a> Документы  
 Эти интерфейсы представления документов (исходные файлы) и связанных с ними элементов.  

|Интерфейс|Реализуется|Описание|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Отправленные DE запрос документа должны быть открыты.|  
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|Представляет поток Дизассемблированный инструкции из документа.|  
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS, DE|Представляет документ, предоставляемые DE, указав имя и идентификатор класса.|  
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE, EE|Представляет контрольную сумму для документа отладки и обеспечивает передачи контрольную сумму между компонентами.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Представляет контекст документа, положение в документе, соответствующий определенному контексту инструкции и код.|  
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS, DE|Представляет общие позиции в документе.|  
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|Представляет позицию в файле исходного кода как смещение в буфере символов.|  
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS, DE|Представляет текстовый документ, предоставляемые DE (производный от [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)), указав действительный текст.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Отправляет DE определяют изменения в исходный файл, находящийся в памяти.|  

##  <a name="Events"></a> События  
 Эти интерфейсы являются все события, которые передаются между DE и диспетчер отладки сеансов (SDM).  


| Интерфейс | Реализуется | Описание: |
| - |----------------| - |
| [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) | DE | Отправленные DE запрос документа должны быть открыты. |
| [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) | DE | Модуль отладки (DE) отправляет этот интерфейс диспетчер отладки сеансов (SDM), чтобы задать состояние панели сообщения во время загрузки символов. |
| [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) | DE | Отправленные DE разрыв в программе после завершения. |
| [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) | DE | Посылается элементом DE, в то время когда привязана точка останова. |
| [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) | DE | Отправленные DE, когда не удается привязать точку останова. |
| [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) | DE | Отправленные DE при достижении точки останова. |
| [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md) | DE | Посылается элементом DE, в то время когда отменяется привязка точки останова. |
| [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md) | DE | Отправленные DE, чтобы определить, следует ли ему прекратить в определенном месте. |
| [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) | DE | Отправляет DE определяют изменения в исходный файл, находящийся в памяти. |
| [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) | DE | Отправленные каждого нового экземпляра DE, чтобы указать, что он готов для обработки задачи отладки. |
| [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) | DE | Отправленные DE, чтобы указать, что отлаживаемой программы готов к выполнению первой инструкции. |
| [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) | DE | Интерфейс, используемый другие интерфейсы событий, которые могут возвращать ошибку, удобное для восприятия ошибки сообщения с. |
| [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) | DE, PS | Базовый интерфейс, из которого все другие события интерфейсы являются производными. |
| [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) | VS | Представляет интерфейс, реализуемый SDM, в которую отправляются события (в виде объектов, реализующая интерфейс определенного события). |
| [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) | DE | Отправленные DE, когда произошло исключение в отлаживаемую программу. |
| [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) | DE | Отправленные DE после завершения вычисления асинхронные выражения. |
| IDebugFindSymbolEvent2 | | УСТАРЕВШИЕ. НЕ ИСПОЛЬЗУЙТЕ. |
| [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) | DE | Отправленные DE после завершения обработки для перехваченные исключения. |
| [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) | DE | Отправленные DE после завершения загрузки программы. |
| [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) | DE | Отправленные DE для отображения интегрированной среды разработки информационное сообщение для пользователя. |
| [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) | DE | Отправленные DE при загрузке или выгрузке модуля. |
| [IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md) | DE | Сигналы [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] отладчика пользовательского интерфейса, чтобы предупредить пользователя, что символы не удалось найти для запущенный исполняемый файл. |
| [IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md) | DE | Отправленные произвольная строка DE для отображения интегрированной среды разработки. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | VS, DE | Отправленные порт для взаимодействия порт события для всех прослушивателей. |
| [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md) | DE, PS | Отправленных DE или порт, когда процесс будет создана. |
| [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) | DE, PS | Отправленных DE или порт, если процесс был удален. |
| [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) | DE, PS | Отправленных DE или порт, когда программа будет создана. |
| [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) | DE, PS | Отправленных DE или порт, когда программа уничтожается. |
| [IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md) | DE | Включает модуль отладки переопределить поведение по умолчанию [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] пользовательского интерфейса при завершении сеанса отладки. |
| [IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md) | DE | Отправлено из модуля отладки (DE) диспетчер отладки сеансов (SDM) при изменении имени программы. |
| [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) | DE | Отправленные DE, когда новое свойство (представленный `IDebugProperty2` интерфейс) будет создана. |
| [IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md) | DE | Отправленные DE, если свойство было уничтожено. |
| [IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md) | DE | Отправленные DE при пошаговом выполнении из или с помощью функции, поэтому возвращаемое значение может отображаться неправильно. |
| [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) | VS | Модули для чтения метрик параметров отладки позволяет удаленно. |
| [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md) | DE | Отправленные DE после завершения шага в, на или из инструкции. |
| [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) | DE | Отправляет DE указать на успех или сбой загрузки символов для модуля. |
| [IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md) | DE | Отправленные DE, когда был создан поток. |
| [IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) | DE | Посылается элементом DE, в то время когда поток был удален. |
| [IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md) | DE | Отправленные DE при изменении имени потока. |

##  <a name="Expressions"></a> Выражения  
 Эти интерфейсы являются выражения, вычисляемое в указанном контексте.  

|Интерфейс|Реализуется|Описание:|  
|---------------|--------------------|-----------------|  
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|Представляет выражение для оценки. Полученный из [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) интерфейс.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Представляет контекст, в котором вычисляется выражение. Полученный из [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) интерфейс.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Отправленные DE после завершения вычисления асинхронные выражения.|  

##  <a name="Memory"></a> Память  
 Эти интерфейсы являются последовательности байтов в памяти.  

|Интерфейс|Реализуется|Описание|  
|---------------|--------------------|-----------------|  
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|Представляет последовательность байтов в памяти, чтения или записи.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Представляет расположение в памяти последовательности байтов.|  

##  <a name="Modules"></a> Модули  
 Эти интерфейсы являются модуль, который соответствует исполняемый файл или. DLL-файл.  

|Интерфейс|Реализуется|Описание:|  
|---------------|--------------------|-----------------|  
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|Представляет один исполняемый файл или DLL.|  
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|Представляет [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) , поддерживает символы.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Отправленные DE при загрузке или выгрузке модуля.|  
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|Представляет сведения об исходном сервере, содержащийся в PDB-файл.|  
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|Представляет собой перечисление на наборе модулей, которые известны по [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md).|  

##  <a name="Ports"></a> Порты  
 Эти интерфейсы являются порты и поставщикам портов.  


| Интерфейс | Реализуется | Описание |
| - |----------------| - |
| [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md) | VS, PS | Представляет порт по умолчанию на локальном компьютере. |
| [IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md) | VS | Включает отладчик, который использует DCOM попросить [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] пользовательского интерфейса, чтобы убедиться в том, что брандмауэр не блокирует удаленную отладку. |
| [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) | VS, PS | Представляет порт. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | PS | Отправленные порт для взаимодействия порт события для всех прослушивателей. |
| [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md) | PS | Представляет порт, который позволяет запускать и завершать процессы. |
| [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) | PS | Используется для регистрации и отмены регистрации программы с портом; Разрешает порт для отслеживания отлаживаемых программ. |
| [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md) | PS | Представляет настраиваемый пользовательский Интерфейс для выбора порта. |
| [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) | VS | Представляет запрос для порта, из которого будет создана или расположен новый порт. |
| [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) | PS | Представляет поставщика портов. |
| [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md) | PS | Представляет поставщик портов, которые можно сохранить (сохранение на диск) сведения о портах, он создан. |
| [IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md) | PS | Позволяет [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] пользовательского интерфейса для отображения текста внутри **сведения о транспорте** раздел **присоединение к процессу** диалоговое окно. |
| [IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md) | VS | Позволяет запрашивать сведения о конечном компьютере. |
| [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) | VS, PS | Представляет перечисление через набор портов. |
| [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) | VS | Представляет перечисление по набору поставщикам портов. |

##  <a name="Processes"></a> Процессы  
 Эти интерфейсы представления процессов, один исполняемый файл, который содержит один или несколько программ.  

|Интерфейс|Реализуется|Описание:|  
|---------------|--------------------|-----------------|  
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, DE|Представляет процесс, который выполняется на компьютере.|  
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, DE|Представляет процесс, который активно поддерживает отладки (используется для замены шаг, продолжить и выполнение методов на [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) интерфейс).|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|Отправленных DE или порт, когда процесс будет создана.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|Отправленных DE или порт, если процесс был удален.|  
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Представляет процесс, который необходимо отслеживать, какой сеанс подключен к нему.|  
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|Представляет перечисление набор процессов на порте.|  

##  <a name="Programs"></a> Программы  
 Эти интерфейсы являются программы, логические единицы выполнения, которые не обязательно соответствуют физической исполняемый файл или модуль.  

|Интерфейс|Реализуется|Описание:|  
|---------------|--------------------|-----------------|  
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|Представляет [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , который необходимо работать совместно с другими программами, отлаживаемого в то же время.|  
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE, PS|Представляет логическую единицу выполнения.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|Отправленных DE или порт, когда программа будет создана.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|Отправленных DE или порт, когда программа уничтожается.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Представляет [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , могут быть обработаны несколько ядер отладки.|  
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Представляет [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , должен иметь возможность отслеживать, какой сеанс подключен к нему.|  
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE, PS|Представляет [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , может возвращать сведения о процессе, в котором он выполняется.|  
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE, PS|Представляет собой программу, которые можно отлаживать.|  
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE, PS|Позволяет узлу программы для получения уведомлений об попытка присоединить соответствующую программу.|  
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|Предоставляет способ для SDM для запроса DE о программах, контролируется, DE.|  
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|Используется DEs для регистрации программы SDM, чтобы показать, что время их отладки.|  
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE, PS|Представляет [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , может выполнить маршалинг интерфейсы через границы потоков или процессов.|  
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE, PS|Представляет перечисление набор программ.|  

##  <a name="Properties"></a> Свойства  
 Эти интерфейсы представляют свойства, значение, связанное с конкретным контекстом, обычно это результат вычисления выражения.  

|Интерфейс|Реализуется|Описание|  
|---------------|--------------------|-----------------|  
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Представляет [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , можно отобразить ее значение любым способом.|  
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|Представляет значение кадр стека, документа или результат вычисления выражения.|  
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|Представляет [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , поддерживающий произвольно длинных строк.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Отправленные DE, когда новое свойство (представленный [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) интерфейс) будет создана.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Отправленные DE, если свойство было уничтожено.|  
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|Представляет ссылку на свойство, которое может существовать за пределами любой определенный кадр стека.|  
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|Представляет перечисление по набору [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структур, которые описывают переменные, регистры, параметров и выражений.|  
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|Представляет перечисление по набору [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) структуры.|  

##  <a name="StackFrames"></a> Кадры стека  
 Эти интерфейсы являются кадр стека, контекст, в которой произошла точки останова или исключение.  

|Интерфейс|Реализуется|Описание:|  
|---------------|--------------------|-----------------|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Представляет контекст, в которой произошла точки останова или исключение.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Представляет [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) который может обрабатывать перехват исключения.|  
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|Представляет перечисление по набору [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) структур, которые определяют функцию вызвать последовательность, используемая для получения определенный кадр стека.|  
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|Представляет перечисление по набору [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структуры, которые описывают кадров стека.|  

##  <a name="Threads"></a> Потоки  
 Эти интерфейсы являются потоками и связанные с ними события.  

|Интерфейс|Реализуется|Описание:|  
|---------------|--------------------|-----------------|  
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|Представляет поток выполнения.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Отправленные DE, когда был создан поток.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Посылается элементом DE, в то время когда поток был удален.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Отправленные DE при изменении имени потока.|  
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|Представляет перечисление через набор потоков.|  

##  <a name="TypeVisualizers"></a> Визуализаторы типа  
 Эти интерфейсы обеспечивают поддержку визуализаторами типов. Эти интерфейсы обычно реализуются путем вычислитель выражений.  

|Интерфейс|Реализуется|Описание|  
|---------------|--------------------|-----------------|  
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Представляет массив байтов, которые будут отображаться для типа визуализатора.|  
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Предоставляет методы для получения доступа к данным, передается тип визуализатора.|  
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|Представляет свойство, которое предоставляет доступ к [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) реализаций.|  

## <a name="see-also"></a>См. также  
 [Справочник по API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Создание пользовательского модуля отладки](../../../extensibility/debugger/creating-a-custom-debug-engine.md)