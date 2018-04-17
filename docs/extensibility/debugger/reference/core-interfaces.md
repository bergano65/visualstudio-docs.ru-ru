---
title: Основные интерфейсы | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 45521c0db16ac892d2e0e43e34c4b030075f7be2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="core-interfaces"></a>Базовых интерфейсов
Следующие интерфейсы являются базовых интерфейсов расширения отладчика с помощью [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)].  
  
## <a name="discussion"></a>Обсуждение  
 Эти интерфейсы используются в основном для создания модуля отладки (DE). Здесь они организованы по категориям:  
  
-   [Точки останова](#Breakpoints)  
  
-   [Контексты](#Contexts)  
  
-   [Основных серверных компонентов](#CoreServer)  
  
-   [Отладка ядра](#DebugEngines)  
  
-   [Документы](#Documents)  
  
-   [События](#Events)  
  
-   [Выражения](#Expressions)  
  
-   [Память](#Memory)  
  
-   [Модули](#Modules)  
  
-   [Порты](#Ports)  
  
-   [Процессы](#Processes)  
  
-   [Программы](#Programs)  
  
-   [Свойства](#Properties)  
  
-   [Кадры стека](#StackFrames)  
  
-   [Потоки](#Threads)  
  
-   [Визуализаторы типа](#TypeVisualizers)  
  
 Перечислены сущности, которые могут реализовывать интерфейсы.  
  
-   Отладка ядра (DE)  
  
-   Порт поставщика (PS).  
  
-   Вычислитель выражений (Эстония)  
  
-   Visual Studio (VS)  
  
##  <a name="Breakpoints"></a> Точки останова  
 Эти интерфейсы относящиеся к реализации и отслеживания точек останова.  
  
|Интерфейс|Реализуемый|Описание|  
|---------------|--------------------|-----------------|  
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|Представляет точку останова, привязанный к расположение в памяти.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Отправленные DE при привязке точку останова на расположение в памяти.|  
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|Представляет документ контрольной суммы для запроса точки останова.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Отправленные DE при сбое точка останова может быть привязано к расположение в памяти.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Отправленное DE при достижении точки останова.|  
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|Представляет запрос на точке останова. используется при создании ожидающая точка останова.|  
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|Представляет запрос на точке останова. используется при создании ожидающая точка останова.|  
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|Представляет сведения, используемые для привязки точки останова.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Посылается элементом DE когда отменяется точку останова из области памяти.|  
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|Представляет недопустимой точки останова (возвращенный `IDebugBreakpointErrorEvent2`).|  
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|Представляет разрешение сведения о недопустимой точки останова.|  
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|Представляет позицию в функции, в которой задана точка останова.|  
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|Представляет точку останова, который должен быть связанными; используется при создании связанная точка останова.|  
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|Представляет собой перечисление по набору связанных точек останова.|  
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|Представляет собой перечисление по набору точки останова, которые не были привязаны к расположение в памяти.|  
  
##  <a name="Contexts"></a> Контексты  
 Эти интерфейсы представляют различные виды контекстов в отлаживаемой программы.  
  
|Интерфейс|Реализуемый|Описание|  
|---------------|--------------------|-----------------|  
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|Представляет начальную позицию инструкции кода.|  
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|Расширяет [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) интерфейс, чтобы обеспечить получение модулей и процессов.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Представляет позицию в документе.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Представляет контекст, в котором для вычисления выражения.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Представляет собой начальное расположение в памяти коллекции байтов.|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Представляет контекст кадр стека на точке останова или исключение.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Представляет контекст кадр стека на точке останова или исключение.|  
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|Представляет собой перечисление на множестве контекстов кода.|  
  
##  <a name="CoreServer"></a> Основных серверных компонентов  
 Эти интерфейсы представляют компьютера, на котором выполняется отладка программы. Они реализуются [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] , но может вызываться в отладчики.  
  
|Интерфейс|Реализуемый|Описание|  
|---------------|--------------------|-----------------|  
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|Предоставляет доступ к портам и поставщикам портов, а также сведения о компьютере.|  
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|Представляет [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) , поддерживает удаленную отладку.|  
  
##  <a name="DebugEngines"></a> Отладка ядра  
 Эти интерфейсы представляют отладчики и связанные с ними события.  
  
|Интерфейс|Реализуемый|Описание|  
|---------------|--------------------|-----------------|  
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|Представляет модулем отладки.|  
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|Представляет пользовательский отладчик, который поддерживает загрузку символов, JustMyCode и исключений.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Отправленные DE каждого нового экземпляра, чтобы указать, что он готов к обработке задачи отладки.|  
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|Представляет пользовательский отладчик, который поддерживает при запуске программы.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE PS|Представляет узел программы, который обрабатывает несколько отладчики.|  
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|Предоставляет способ для SDM получает интерфейс для модуля отладки из потока, программы или кадр стека.|  
  
##  <a name="Documents"></a> Документы  
 Эти интерфейсы представляют документы (файлы источника) и связанных с ними элементов.  
  
|Интерфейс|Реализуемый|Описание|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Отправленные DE для запроса документа должен быть открыт.|  
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|Представляет поток дизассемблированные инструкции из документа.|  
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS, DE|Представляет документ, предоставляемые DE, указав имя и идентификатор класса.|  
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE EE|Представляет контрольную сумму для документа отладки и обеспечивает передачи контрольная сумма между компонентами.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Представляет контекст документа, позиции в документе, соответствующий данному контексту инструкции и код.|  
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS, DE|Представляет общие позиции в документе.|  
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|Представляет позицию в исходном файле как смещение символа.|  
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS, DE|Представляет текстовый документ, предоставляемые DE (производный от [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)), указав действительный текст.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Отправленные DE для указания изменения в исходный файл, находящийся в памяти.|  
  
##  <a name="Events"></a> События  
 Эти интерфейсы являются все события, которые передаются между DE и диспетчера сеанса отладки (SDM).  
  
|Интерфейс|Реализуемый|Описание|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Отправленные DE для запроса документа должен быть открыт.|  
|[IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)|DE|Модуль отладки (DE) отправляет этот интерфейс диспетчера сеанса отладки (SDM), чтобы задать состояние панели сообщений во время загрузки символов.|  
|[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)|DE|Отправленные DE при завершении разрыв в программе.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Отправленные DE при привязке точки останова.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Отправленные DE, когда не удается привязать точку останова.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Отправленное DE при достижении точки останова.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Посылается элементом DE когда отменяется привязка точки останова.|  
|[IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)|DE|Отправленные DE, чтобы определить, следует ли ему прекратить в определенном месте.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Отправленные DE для указания изменения в исходный файл, находящийся в памяти.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Отправленные DE каждого нового экземпляра, чтобы указать, что он готов к обработке задачи отладки.|  
|[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)|DE|Отправленные DE, чтобы указать, что отлаживаемой программы готов к выполнению первой инструкции.|  
|[IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)|DE|Интерфейс, используемый интерфейсы других событий, которые может вернуть ошибку, для предоставления сообщения восприятия об ошибках.|  
|[IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)|DE PS|Базовый интерфейс, из которого все другие события интерфейсы являются производными.|  
|[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)|VS|Представляет интерфейс, реализуемый SDM, на который отправляются события (в виде объектов, реализующая интерфейс определенного события).|  
|[IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)|DE|Отправленные DE, когда возникло исключение в отлаживаемую программу.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|После завершения вычисления выражения асинхронных отправленных DE.|  
|IDebugFindSymbolEvent2||УСТАРЕВШИЕ. НЕ СЛЕДУЕТ ИСПОЛЬЗОВАТЬ.|  
|[IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|DE|Отправленные DE после завершения обработки для перехваченного исключения.|  
|[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|DE|Когда программа завершила загрузку отправленных DE.|  
|[IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)|DE|Отправленные DE возможность отображения интегрированной среды разработки информационное сообщение для пользователя.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Отправленное DE при загрузке или выгрузке модуля.|  
|[IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md)|DE|Сигналы [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] отладчика пользовательского интерфейса, чтобы предупредить пользователя о том, что символы не удалось найти для запущенный исполняемый файл.|  
|[IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md)|DE|Отправленные произвольная строка DE возможность отображения интегрированной среды разработки.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|VS, DE|Отправленные порт для взаимодействия порт события для всех прослушивателей.|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE PS|Отправленные DE или порта при создании процесса.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE PS|Отправленные DE или порт при уничтожении процесса.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE PS|Отправленные DE или порта при создании программы.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE PS|Отправленные DE или порт при уничтожении программы.|  
|[IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md)|DE|Включает модуль отладки для переопределения поведения по умолчанию [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] пользовательского интерфейса при завершении сеанса отладки.|  
|[IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md)|DE|Отправлено из модуля отладки (DE) для диспетчера сеанса отладки (SDM) при изменении имени программы.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Отправленные DE, когда новое свойство (представленного `IDebugProperty2` интерфейса) был создан.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Отправленные DE при уничтожении свойство.|  
|[IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|DE|Отправленные DE при пошаговой отладки из или через функцию, поэтому возвращаемое значение может отображаться неправильно.|  
|[IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)|VS|Включает отладки ядер для чтения параметры метрик удаленно.|  
|[IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|DE|Отправленные DE при завершении шага в, с обходом или из инструкции.|  
|[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|DE|Отправленные DE, которое указывает успешность или сбой загрузить символы для модуля.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Отправленные DE, когда был создан поток.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Отправленные DE, если поток был удален.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Отправленные DE, когда поток изменилось его имя.|  
  
##  <a name="Expressions"></a> Выражения  
 Эти интерфейсы представляют выражения для вычисления в определенном контексте.  
  
|Интерфейс|Реализуемый|Описание|  
|---------------|--------------------|-----------------|  
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|Представляет выражение для вычисления. Получено из [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) интерфейса.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Представляет контекст, в котором вычисляется выражение. Получено из [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) интерфейса.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|После завершения вычисления выражения асинхронных отправленных DE.|  
  
##  <a name="Memory"></a> Память  
 Эти интерфейсы представляют последовательность байтов в памяти.  
  
|Интерфейс|Реализуемый|Описание|  
|---------------|--------------------|-----------------|  
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|Представляет последовательность байтов в памяти, чтения или записи.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Представляет расположение в памяти последовательности байтов.|  
  
##  <a name="Modules"></a> Модули  
 Эти интерфейсы являются модуль, который соответствует исполняемый файл или. DLL-файл.  
  
|Интерфейс|Реализуемый|Описание|  
|---------------|--------------------|-----------------|  
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|Представляет один исполняемый файл или DLL.|  
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|Представляет [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) , поддерживает символы.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Отправленное DE при загрузке или выгрузке модуля.|  
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|Представляет сведения об исходном сервере, содержащихся в PDB-файл.|  
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|Представляет перечисление через набор модулей, известные [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md).|  
  
##  <a name="Ports"></a> Порты  
 Эти интерфейсы являются порты и поставщикам портов.  
  
|Интерфейс|Реализуемый|Описание|  
|---------------|--------------------|-----------------|  
|[IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)|VS, PS|Представляет порт по умолчанию на локальном компьютере.|  
|[IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md)|VS|Включает отладчик, который использует DCOM попросить [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] пользовательского интерфейса, чтобы убедиться в том, что брандмауэр не блокирует удаленную отладку.|  
|[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)|VS, PS|Представляет порт.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|PS|Отправленные порт для взаимодействия порт события для всех прослушивателей.|  
|[IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)|PS|Представляет порт, который можно запустить и завершать процессы.|  
|[IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)|PS|Позволяет регистрировать и отменять регистрацию программы с портом; Разрешает порт для отслеживания отлаживаемых программ.|  
|[IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)|PS|Представляет настраиваемый пользовательский Интерфейс для выбора порта.|  
|[IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)|VS|Представляет запрос для порта, из которого будет создан или найти новый порт.|  
|[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)|PS|Представляет поставщика порты.|  
|[IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)|PS|Представляет поставщика порты, которые могут сохраняться (сохранить на диск) сведения о портах, он создан.|  
|[IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md)|PS|Включает [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] пользовательский Интерфейс для отображения текста внутри **сведения о транспорте** раздел **присоединиться к процессу** диалоговое окно.|  
|[IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)|VS|Позволяет запрашивать сведения о конечном компьютере.|  
|[IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)|VS, PS|Представляет собой перечисление через набор портов.|  
|[IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)|VS|Представляет собой перечисление по набору поставщикам портов.|  
  
##  <a name="Processes"></a> Процессы  
 Эти интерфейсы представления процессов, один исполняемый файл, содержащий одну или несколько программ.  
  
|Интерфейс|Реализуемый|Описание|  
|---------------|--------------------|-----------------|  
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, DE|Представляет процесс, который выполняется на компьютере.|  
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, DE|Представляет процесс, который активно поддерживает отладки (используется для замены шаг, продолжить и выполнение методов с [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) интерфейс).|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE PS|Отправленные DE или порта при создании процесса.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE PS|Отправленные DE или порт при уничтожении процесса.|  
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Представляет процесс, который необходимо отследить, какие сеанса присоединен к нему.|  
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|Представляет собой перечисление набор процессов для порта.|  
  
##  <a name="Programs"></a> Программы  
 Эти интерфейсы представляют программы LUN выполнения, которые не обязательно соответствуют физической исполняемого файла или модуля.  
  
|Интерфейс|Реализуемый|Описание|  
|---------------|--------------------|-----------------|  
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|Представляет [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , который необходимо работать совместно с другими программами, отлаживаемого в то же время.|  
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE PS|Представляет логическую единицу выполнения.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE PS|Отправленные DE или порта при создании программы.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE PS|Отправленные DE или порт при уничтожении программы.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE PS|Представляет [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) может обрабатываться несколькими ядрами отладки.|  
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Представляет [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , необходимо отслеживать, какие сеанса привязано.|  
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE PS|Представляет [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , может возвращать сведения о процессе, в котором он выполняется.|  
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE PS|Представляет программу, которая может отлаживаться.|  
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE PS|Позволяет узлу программы для получения уведомлений об попытка подключения к соответствующую программу.|  
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|Предоставляет способ для SDM для запроса DE о программах, которые управляются, DE.|  
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|Используемый алгоритм DEs для регистрации SDM, чтобы показать, что они отлаживаемых программ.|  
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE PS|Представляет [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , может выполнить маршалинг интерфейсов за пределами границ потока или процесса.|  
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE PS|Представляет собой перечисление набор программ.|  
  
##  <a name="Properties"></a> Свойства  
 Эти интерфейсы представляют свойства, значение, связанное с указанном контексте, обычно это результат вычисления выражения.  
  
|Интерфейс|Реализуемый|Описание|  
|---------------|--------------------|-----------------|  
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Представляет [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , можно отобразить ее значение любым способом.|  
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|Представляет значение кадр стека, документа или результат вычисления выражения.|  
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|Представляет [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , поддерживает произвольной длины строки.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Отправленные DE, когда новое свойство (представленного [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) интерфейса) был создан.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Отправленные DE при уничтожении свойство.|  
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|Представляет ссылку на свойство, которое может существовать за пределами любого определенного кадра стека.|  
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|Представляет перечисление по набору [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структур, которые описывают переменные, регистры, параметров и выражений.|  
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|Представляет перечисление по набору [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) структуры.|  
  
##  <a name="StackFrames"></a> Кадры стека  
 Эти интерфейсы являются кадр стека, контекст, в котором точки останова или исключения произошло.  
  
|Интерфейс|Реализуемый|Описание|  
|---------------|--------------------|-----------------|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Представляет контекст, в котором точки останова или исключения произошло.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Представляет [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) который может обрабатывать перехват исключения.|  
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|Представляет перечисление по набору [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) структуры, которые определяют функции вызова последовательность, используемая для получения определенного кадра стека.|  
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|Представляет перечисление по набору [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структуры, которые описывают кадры стека.|  
  
##  <a name="Threads"></a> Потоки  
 Эти интерфейсы представляют потоки и связанные с ними события.  
  
|Интерфейс|Реализуемый|Описание|  
|---------------|--------------------|-----------------|  
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|Представляет поток выполнения.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Отправленные DE, когда был создан поток.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Отправленные DE, если поток был удален.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Отправленные DE, когда поток изменилось его имя.|  
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|Представляет собой перечисление по набору потоков.|  
  
##  <a name="TypeVisualizers"></a> Визуализаторы типа  
 Эти интерфейсы обеспечивают поддержку визуализаторами типов. Эти интерфейсы обычно реализуются в средстве оценки выражений.  
  
|Интерфейс|Реализуемый|Описание|  
|---------------|--------------------|-----------------|  
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Представляет массив байтов, которые должны быть представлены тип визуализатора.|  
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Предоставляет методы для получения доступа к данным должны быть переданы тип визуализатора.|  
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|Представляет свойство, которое предоставляет доступ к [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) реализации.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Создание пользовательского модуля отладки](../../../extensibility/debugger/creating-a-custom-debug-engine.md)