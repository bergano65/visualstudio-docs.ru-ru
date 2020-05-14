---
title: Основные интерфейсы Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8bf01ffceb122ad99d5ecca8fabfaa102a8fc505
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737576"
---
# <a name="core-interfaces"></a>Базовые интерфейсы
Следующие интерфейсы являются основными интерфейсами для расширения отладчика с помощью [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)].

## <a name="discussion"></a>Обсуждение
 Эти интерфейсы в основном используются для создания движка отладки (DE). Они организованы здесь по категориям:

- [Точки останова](#Breakpoints)

- [Контексты](#Contexts)

- [Основной сервер](#CoreServer)

- [Двигатели дебага](#DebugEngines)

- [Документы](#Documents)

- [События](#Events)

- [Выражения](#Expressions)

- [Память](#Memory)

- [Модули](#Modules)

- [Порты](#Ports)

- [Процессов](#Processes)

- [Программы](#Programs)

- [Свойства](#Properties)

- [Кадры стека](#StackFrames)

- [Потоков](#Threads)

- [Визуализаторы типа](#TypeVisualizers)

  Сущности, которые могут реализовать интерфейсы:

- Двигатель дебуга (DE)

- Поставщик порта (PS)

- Оценка экспрессии (EE)

- Визуальная студия (VS)

## <a name="breakpoints"></a><a name="Breakpoints"></a>Точки останова
 Эти интерфейсы связаны с реализацией и отслеживанием точек разрыва.

|Интерфейс|Реализовано|Описание|
|---------------|--------------------|-----------------|
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|Представляет точку разрыва, связанную с местоположением памяти.|
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Отправлено DE, когда точка разрыва привязана к местоположению памяти.|
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|Представляет проверку документов для запроса точки разрыва.|
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Отправлено DE, когда точка разрыва не связана с местом памяти.|
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Отправлено DE при достигеточке разрыва.|
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|Представляет запрос на точку разрыва; используется при создании ожидающего разрыва.|
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|Представляет запрос на точку разрыва; используется при создании ожидающего разрыва.|
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|Представляет информацию, используемую для связывания точки разрыва.|
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Отправлено DE, когда точка разрыва не связана с местом памяти.|
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|Представляет недействительную точку `IDebugBreakpointErrorEvent2`разрыва (возвращенную).|
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|Представляет информацию разрешения о недействительной точке разрыва.|
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|Представляет положение в функции, в которой установлена точка разрыва.|
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|Представляет точку разрыва, которая должна быть связана; используется при создании свяжей точки разрыва.|
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|Представляет перечисление по набору связанных точек разрыва.|
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|Представляет перечисление набора точек разрыва, которые не могут быть привязаны к местоположению памяти.|

## <a name="contexts"></a><a name="Contexts"></a>Контекстах
 Эти интерфейсы представляют различные виды контекстов в отладке программы.

|Интерфейс|Реализовано|Описание|
|---------------|--------------------|-----------------|
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|Представляет исходное положение инструкции по коду.|
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|Расширяет интерфейс [IDebugCodeContext2,](../../../extensibility/debugger/reference/idebugcodecontext2.md) чтобы обеспечить поиск интерфейсов модуля и процесса.|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Представляет позицию в документе.|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Представляет контекст для оценки выражения.|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Представляет стартовое место в память о коллекции байтов.|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Представляет контекст кадра стека в точке разрыва или исключения.|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Представляет контекст кадра стека в точке разрыва или исключения.|
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|Представляет перечисление в наборе контекстов кода.|

## <a name="core-server"></a><a name="CoreServer"></a>Основной сервер
 Эти интерфейсы представляют собой машину, на которой отлажается программа. Они реализуются, [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] но могут быть вызваны двигателями отладки.

|Интерфейс|Реализовано|Описание|
|---------------|--------------------|-----------------|
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|Обеспечивает доступ к портам и поставщикам портов, а также информацию о компьютере.|
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|Представляет [IDebugCoreServer2,](../../../extensibility/debugger/reference/idebugcoreserver2.md) поддерживающий удаленную отладку.|

## <a name="debug-engines"></a><a name="DebugEngines"></a>Двигатели дебага
 Эти интерфейсы представляют собой отладоть двигатели и связанные с ними события.

|Интерфейс|Реализовано|Описание|
|---------------|--------------------|-----------------|
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|Представляет пользовательский движок отладки.|
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|Представляет пользовательский отладочный движок, поддерживающий загрузку символов, JustMyCode и исключений.|
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Отправляется каждым новым экземпляром DE, чтобы показать, что он готов к обработке задач отладки.|
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|Представляет пользовательский отладка двигателя, который поддерживает запуск программ.|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Представляет собой узлы программы, которые обрабатывают несколько двигателей отладки.|
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|Предоставляет SDM способ получить интерфейс для отладки двигателя из потока, программы или стек кадра.|

## <a name="documents"></a><a name="Documents"></a>Документы
 Эти интерфейсы представляют собой документы (исходные файлы) и связанные с ними элементы.

|Интерфейс|Реализовано|Описание|
|---------------|--------------------|-----------------|
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Отправлено DE, чтобы запросить документ, который будет открыт.|
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|Представляет собой поток разобранных инструкций из документа.|
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS, DE|Представляет собой документ, предоставленный DE, с указанием имени и идентификатора класса (CLSID).|
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE, EE|Представляет проверку для отладки документа и позволяет передавать чекмежду через компоненты.|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Представляет контекст документа, позицию в документе, соответствующую конкретному заявлению и контексту кода.|
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS, DE|Представляет общую позицию в документе.|
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|Представляет позицию в исходном файле в качестве смещения символов.|
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS, DE|Представляет текстовый документ, поставляемый DE (производным от [IDebugDocument2),](../../../extensibility/debugger/reference/idebugdocument2.md)поставляя фактический текст.|
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Отправлено DE, чтобы указать изменения в исходном файле, который находится в памяти.|

## <a name="events"></a><a name="Events"></a>События
 Эти интерфейсы представляют все события, отправляемые между DE и диспетчером отладки сеанса (SDM).

| Интерфейс | Реализовано | Описание |
| - |----------------| - |
| [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) | DE | Отправлено DE, чтобы запросить документ, который будет открыт. |
| [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) | DE | Движок отладки (DE) отправляет этот интерфейс диспетчеру отладки сеанса (SDM) для установки сообщения панели статуса во время нагрузок символов. |
| [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) | DE | Отправлено DE, когда перерыв в программе был завершен. |
| [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) | DE | Отправлено DE, когда точка разрыва связана. |
| [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) | DE | Отправлено DE, когда точка разрыва не может быть связана. |
| [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) | DE | Отправлено DE при достигеточке разрыва. |
| [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md) | DE | Отправлено DE, когда точка разрыва не связана. |
| [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md) | DE | Отправлено DE, чтобы определить, следует ли остановиться в определенном месте. |
| [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) | DE | Отправлено DE, чтобы указать изменения в исходном файле, который находится в памяти. |
| [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) | DE | Отправляется каждым новым экземпляром DE, чтобы показать, что он готов к обработке задач отладки. |
| [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) | DE | Отправлено DE, чтобы указать отладить программу, готово выполнить первую инструкцию. |
| [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) | DE | Интерфейс, используемый другими интерфейсами событий, который может вернуть ошибку, для предоставления читаемых человеком сообщений об ошибках. |
| [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) | DE, PS | Базовый интерфейс, из которого вытекают все другие интерфейсы событий. |
| [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) | VS | Представляет интерфейс, реализованный SDM, на который отправляются события (выраженные как объекты, реализующие определенный интерфейс события). |
| [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) | DE | Отправлено DE, когда произошло исключение в отладке программы. |
| [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) | DE | Отправлено DE, когда асинхронная оценка выражения завершена. |
| IDebugFindСимволЬ2 | | Устаревшее. НЕ ИСПОЛЬЗУЙТЕ. |
| [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) | DE | Отправлено DE при обработке для перехваченного исключения было завершено. |
| [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) | DE | Отправлено DE, когда программа завершила загрузку. |
| [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) | DE | Отправлено DE, чтобы IDE отобразить информационное сообщение для пользователя. |
| [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) | DE | Отправлено DE при загрузке или выгрузке модуля. |
| [IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md) | DE | Сигналы [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] uI отладчика, чтобы предупредить пользователя, что символы не могут быть расположены для запущенного исполняемого. |
| [IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md) | DE | Отправлено DE, чтобы iDE отобразить произвольную строку. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | VS, DE | Отправлено портом для передачи событий порта любому слушателю. |
| [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md) | DE, PS | Отправлено DE или портом при создании процесса. |
| [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) | DE, PS | Отправлено DE или портом, когда процесс был уничтожен. |
| [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) | DE, PS | Отправлено DE или портом при создании программы. |
| [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) | DE, PS | Отправлено DE или портом, когда программа была уничтожена. |
| [IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md) | DE | Позволяет отладить движок, чтобы переопределить [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] поведение ui по умолчанию при конце сеанса отладки. |
| [IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md) | DE | Отправлено от отладки двигателя (DE) в диспетчер сеанса отладки (SDM) при изменении названия программы. |
| [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) | DE | Отправлено DE при создании нового свойства `IDebugProperty2` (представленного интерфейсом). |
| [IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md) | DE | Отправлено DE, когда имущество было уничтожено. |
| [IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md) | DE | Отправлено DE при выходе из или над функцией, чтобы значение возврата можно было правильно отображать. |
| [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) | VS | Позволяет отладить двигатели для чтения параметров метрики удаленно. |
| [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md) | DE | Отправлено DE, когда шаг в, более, или из инструкции была завершена. |
| [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) | DE | Отправлено DE, чтобы указать на успех или неудачу загрузки символов для модуля. |
| [IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md) | DE | Отправлено DE при создании потока. |
| [IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) | DE | Отправлено DE, когда поток был уничтожен. |
| [IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md) | DE | Отправлено DE, когда поток изменил свое название. |

## <a name="expressions"></a>Выражения <a name="Expressions"></a>
 Эти интерфейсы представляют выражения, которые необходимо оценить в определенном контексте.

|Интерфейс|Реализовано|Описание|
|---------------|--------------------|-----------------|
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|Представляет выражение, подносиве себя к оценке. Получено из интерфейса [IDebugExpressionExpression2.](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Представляет контекст, в котором оценивается выражение. Получено из интерфейса [IDebugStackFrame2.](../../../extensibility/debugger/reference/idebugstackframe2.md)|
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Отправлено DE, когда асинхронная оценка выражения завершена.|

## <a name="memory"></a><a name="Memory"></a>Памяти
 Эти интерфейсы представляют последовательности байтов в памяти.

|Интерфейс|Реализовано|Описание|
|---------------|--------------------|-----------------|
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|Представляет собой последовательность байтов в памяти, которые могут быть прочитаны или написаны.|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Представляет место в памяти последовательности байтов.|

## <a name="modules"></a><a name="Modules"></a>Модули
 Эти интерфейсы представляют собой модуль, который соответствует исполняемой или . Файл DLL.

|Интерфейс|Реализовано|Описание|
|---------------|--------------------|-----------------|
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|Представляет собой один исполняемый или DLL.|
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|Представляет [IDebugModule2,](../../../extensibility/debugger/reference/idebugmodule2.md) поддерживающий символы.|
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Отправлено DE при загрузке или выгрузке модуля.|
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|Представляет информацию об исходном сервере, содержащуюся в файле PDB.|
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|Представляет перечисление по набору модулей, которые известны [IDebugProgram2.](../../../extensibility/debugger/reference/idebugprogram2.md)|

## <a name="ports"></a><a name="Ports"></a>Порты
 Эти интерфейсы представляют собой порты и поставщиков портов.

| Интерфейс | Реализовано | Описание |
| - |----------------| - |
| [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md) | VS, PS | Представляет порт по умолчанию на локальном компьютере. |
| [IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md) | VS | Позволяет отладить двигатель, который использует [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] DCOM, чтобы спросить uI, чтобы убедиться, что брандмауэр не будет блокировать удаленную отладку. |
| [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) | VS, PS | Представляет порт. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | PS | Отправлено портом для передачи событий порта любому слушателю. |
| [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md) | PS | Представляет собой порт, который может запускать и прекращать процессы. |
| [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) | PS | Используется для регистрации и отрегистрации программ в порту; позволяет порту отслеживать программы, которые в настоящее время отлаживаются. |
| [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md) | PS | Представляет индивидуальный ui для выбора порта. |
| [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) | VS | Представляет запрос на порт, из которого будет создан или расположен новый порт. |
| [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) | PS | Представляет поставщика портов. |
| [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md) | PS | Представляет поставщика портов, которые могут сохранять (сохранять на диске) информацию о созданных портах. |
| [IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md) | PS | Позволяет [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] uI отображать текст в разделе **Транспортная информация** в поле диалога **«Атрим для обработки».** |
| [IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md) | VS | Позволяет запросить информацию о целевом компьютере. |
| [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) | VS, PS | Представляет перечисление набора портов. |
| [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) | VS | Представляет перечисление ряда поставщиков портов. |

## <a name="processes"></a><a name="Processes"></a>Процессов
 Эти интерфейсы представляют процессы, один исполняемый, который содержит одну или несколько программ.

|Интерфейс|Реализовано|Описание|
|---------------|--------------------|-----------------|
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, DE|Представляет процесс, который работает на компьютере.|
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, DE|Представляет процесс, который активно поддерживает отладку (используется для замены методов Step, Continue и Execute на интерфейсе [IDebugProgram2).](../../../extensibility/debugger/reference/idebugprogram2.md)|
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|Отправлено DE или портом при создании процесса.|
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|Отправлено DE или портом, когда процесс был уничтожен.|
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Представляет процесс, который должен отслеживать, какой сеанс прилагается к нему.|
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|Представляет собой перечисление набора процессов в порту.|

## <a name="programs"></a><a name="Programs"></a>Программ
 Эти интерфейсы представляют собой программы, логические единицы исполнения, которые не обязательно соответствуют физическому исполняемому или модулю.

|Интерфейс|Реализовано|Описание|
|---------------|--------------------|-----------------|
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|Представляет [IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) который должен работать совместно с другими программами, которые отлаживаются в то же время.|
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE, PS|Представляет собой логическую единицу исполнения.|
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|Отправлено DE или портом при создании программы.|
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|Отправлено DE или портом, когда программа была уничтожена.|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Представляет [IDebugProgramNode2,](../../../extensibility/debugger/reference/idebugprogramnode2.md) с которым можно справиться с несколькими двигателями отладки.|
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Представляет [IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) который должен быть в состоянии отслеживать, какой сеанс прилагается к нему.|
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE, PS|Представляет [IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) который может вернуть информацию о процессе, в котором он работает.|
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE, PS|Представляет программу, которую можно отладить.|
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE, PS|Позволяет узлам программы получать уведомления о попытке присоединения к связанной программе.|
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|Предоставляет SDM возможность запроса DE о программах, контролируемых этим DE.|
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|Используется DEs для регистрации программ с SDM, чтобы показать, что они отлаживаются.|
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE, PS|Представляет [IDebugProgramNode2,](../../../extensibility/debugger/reference/idebugprogramnode2.md) который может маршал интерфейсов через границы потока или процесса.|
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE, PS|Представляет собой перечисление набора программ.|

## <a name="properties"></a>Свойства <a name="Properties"></a>
 Эти интерфейсы представляют свойства, значение, связанное с определенным контекстом, обычно результат оценки выражения.

|Интерфейс|Реализовано|Описание|
|---------------|--------------------|-----------------|
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Представляет [IDebugProperty2,](../../../extensibility/debugger/reference/idebugproperty2.md) который может отображать его значение на заказ.|
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|Представляет значение кадра стека, документа или результата оценки выражения.|
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|Представляет [IDebugProperty2,](../../../extensibility/debugger/reference/idebugproperty2.md) который поддерживает произвольно длинные строки.|
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Отправлено DE при создании нового свойства (представленного интерфейсом [IDebugProperty2).](../../../extensibility/debugger/reference/idebugproperty2.md)|
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Отправлено DE, когда имущество было уничтожено.|
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|Представляет собой ссылку на свойство, которое может существовать за пределами определенного кадра стека.|
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|Представляет перечисление по набору [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структур, описываемых переменных, регистров, параметров и выражений.|
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|Представляет перечисление по набору [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) структур.|

## <a name="stack-frames"></a><a name="StackFrames"></a>Стек кадры
 Эти интерфейсы представляют собой кадр стека, контекст, в котором произошла точка разрыва или исключение.

|Интерфейс|Реализовано|Описание|
|---------------|--------------------|-----------------|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Представляет контекст, в котором произошла точка разрыва или исключение.|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Представляет [IDebugStackFrame2,](../../../extensibility/debugger/reference/idebugstackframe2.md) который может обрабатывать перехваченные исключения.|
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|Представляет перечисление по набору [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) структур, которые определяют последовательность вызова функции, используемую для входной части кадра стека.|
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|Представляет перечисление по набору структур [FRAMEINFO,](../../../extensibility/debugger/reference/frameinfo.md) описываемых стековых кадров.|

## <a name="threads"></a><a name="Threads"></a>Потоков
 Эти интерфейсы представляют потоки и связанные с ними события.

|Интерфейс|Реализовано|Описание|
|---------------|--------------------|-----------------|
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|Представляет собой поток выполнения.|
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Отправлено DE при создании потока.|
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Отправлено DE, когда поток был уничтожен.|
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Отправлено DE, когда поток изменил свое название.|
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|Представляет перечисление по набору потоков.|

## <a name="type-visualizers"></a><a name="TypeVisualizers"></a>Визуализаторы типа
 Эти интерфейсы обеспечивают поддержку визуализаторов типов. Эти интерфейсы обычно реализуются оценщиком выражения.

|Интерфейс|Реализовано|Описание|
|---------------|--------------------|-----------------|
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Представляет массив байтов, которые будут представлены визуализатору типа.|
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Предоставляет методы для получения доступа к данным, которые будут переданы визуализатор типа.|
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|Представляет свойство, предоставляющее доступ к реализации [IPropertyProxyEESide.](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|

## <a name="see-also"></a>См. также
- [Справка по API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [Создание пользовательского модуля отладки](../../../extensibility/debugger/creating-a-custom-debug-engine.md)
