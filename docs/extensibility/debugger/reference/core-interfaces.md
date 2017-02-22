---
title: "Базовых интерфейсов | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "отладка [пакет SDK для отладки], основных интерфейсов"
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# Базовых интерфейсов
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Следующие интерфейсы базовые интерфейсы для расширения отладчика с помощью [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)].  
  
## Обсуждение  
 Эти интерфейсы в основном используются для создания обработчика отладки \(DE\).  Здесь они упорядочены по категориям:  
  
-   [Точки останова](#Breakpoints)  
  
-   [Контексты](#Contexts)  
  
-   [Основной сервер](#CoreServer)  
  
-   [Обработчики отладка](#DebugEngines)  
  
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
  
 Сущности, которые могут реализовать интерфейсы:  
  
-   Обработчик отладки \(DE\)  
  
-   Поставщик порта \(PS\)  
  
-   Средство оценки выражений \(EE\)  
  
-   Visual Studio \(VS\)  
  
##  <a name="Breakpoints"></a> Точки останова  
 Эти интерфейсы относящиеся к реализации и обнаружением точек останова.  
  
|Интерфейс|Реализуется определяемая|Описание|  
|---------------|------------------------------|--------------|  
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|Представляет точку останова привязанную к расположение в памяти.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|При отправке DE точка останова будет привязана к расположение в памяти.|  
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|К|Представляет контрольную сумму документа для запроса точки останова.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|При отправке DE точка останова не может быть привязанным к расположение в памяти.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Отправлено DE при достижении точки останова.|  
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|К|Представляет запрос для точки останова. используется для создания ожидается точка останова.|  
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|К|Представляет запрос для точки останова. используется для создания ожидается точка останова.|  
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|Представляет сведения, используемые для привязки точка останова.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|При отправке DE точка останова будет отменена привязка из области памяти.|  
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|Представляет недопустимую точку останова \(возвращенную by `IDebugBreakpointErrorEvent2`\).|  
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|Представляет сведения о разрешениях о недопустимой точки останова.|  
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|Представляет позицию в функции, в которой задана точка останова.|  
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|Представляет точку останова, которая быть привязанным; используется для создания связанной точку останова.|  
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|Представляет перечисление над набором связанных точек останова.|  
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|Представляет перечисление над набором точек останова, которые не удалось привязанны на расположение в памяти.|  
  
##  <a name="Contexts"></a> Контексты  
 Эти интерфейсы представляют различные типы контекстов в пределах, отлаживанными программы.  
  
|Интерфейс|Реализуется определяемая|Описание|  
|---------------|------------------------------|--------------|  
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|Представляет начальную позицию инструкции кода.|  
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|Расширяет IDebugCodeContext2 интерфейс, чтобы включить получение модуля и интерфейсов процесса.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|С DE|Представляет позиции в документе.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Представляет контекст, в котором оценить выражение.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Представляет начальное местоположение в памяти коллекции байтов.|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Представляет контекст кадра стека в точке останова или исключении.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Представляет контекст кадра стека в точке останова или исключении.|  
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|Представляет перечисление по набору контекстов кода.|  
  
##  <a name="CoreServer"></a> Основной сервер  
 Эти интерфейсы представляют компьютер, на котором программа отлаживается.  Они реализуются by [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] но может быть вызван в by отладка обработчики.  
  
|Интерфейс|Реализуется определяемая|Описание|  
|---------------|------------------------------|--------------|  
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|К|Предоставляет доступ к портам и поставщикам портов, а также сведения о компьютере.|  
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|К|Представляет [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) были поддерживает удаленную отладку.|  
  
##  <a name="DebugEngines"></a> Обработчики отладка  
 Эти интерфейсы представляют собой отладочные обработчики и связанные с ними событий.  
  
|Интерфейс|Реализуется определяемая|Описание|  
|---------------|------------------------------|--------------|  
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|Представляет пользовательский обработчик отладки.|  
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|Представляет пользовательский обработчик отладки, поддерживающий загрузку символов, JustMyCode и исключений.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Отправленное каждым новым экземпляром DE для отображения готов обработать задачи отладки.|  
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|Представляет пользовательский обработчик отладки, поддерживает запуск программы.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Представляет узел программы, который обрабатывает несколько обработчиков отладки.|  
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|Предоставляет способ для SDM получить интерфейс в обработчик отладки из потока, программ или кадра стека.|  
  
##  <a name="Documents"></a> Документы  
 Эти интерфейсы представляют документы \(исходные файлы\), и связанные с ними элементы.  
  
|Интерфейс|Реализуется определяемая|Описание|  
|---------------|------------------------------|--------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Отправлено DE для запроса документа его открытия.|  
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|Представляет поток демонтированных инструкций из документа.|  
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|С DE|Представляет документ, предоставленный DE, указав имя и идентификатор класса \(CLSID\).|  
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE " EE|Представляет контрольную сумму для документа отладки, а также передача контрольную сумму между компонентами.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|С DE|Представляет контекст рисования, позицию в документе, соответствующий заданному контексту выписки и кода.|  
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|С DE|Представляет общие позиции в документе.|  
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|К|Представляет позицию в файле источника как сдвиг знака.|  
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|С DE|Представляет текстовый документ \(производным от предоставленного DE [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)\), указав фактическое текста.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Отправлено DE для идентификации изменений к файлу источника, который в памяти.|  
  
##  <a name="Events"></a> События  
 Эти интерфейсы представляют все события, которые передаются между DE и сеансом \(SDM\) диспетчер отладки.  
  
|Интерфейс|Реализуется определяемая|Описание|  
|---------------|------------------------------|--------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Отправлено DE для запроса документа его открытия.|  
|[IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)|DE|Отладчик \(DE\) отправляет этот интерфейс для сеанса отладки \(SDM\) диспетчер для задания сообщение строки состояния во время загрузки символов.|  
|[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)|DE|При завершении прерывания будет отправлено DE в программе.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|При отправке DE точка останова будет привязана.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|При отправке DE точка останова не может быть привязанным.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Отправлено DE при достижении точки останова.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|При отправке DE точка останова будет отменена привязка.|  
|[IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)|DE|Отправлено DE, чтобы определить, должна ли она останавливаться в указанном месте.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Отправлено DE для идентификации изменений к файлу источника, который в памяти.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Отправленное каждым новым экземпляром DE для отображения готов обработать задачи отладки.|  
|[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)|DE|Отправлено DE для отображения готов к выполнению отлаживаемой программы первая инструкция.|  
|[IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)|DE|Интерфейс, который используется другими интерфейсами события, которые могут предоставить возвращать ошибку, понятных для человека сообщения об ошибке.|  
|[IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)|DE, PS|Базовый интерфейс, от которого наследуются все другие интерфейсы событий.|  
|[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)|К|Представляет интерфейс, реализованный SDM, к которому события \(выраженные как объекты, реализующие указанный интерфейс события\).|  
|[IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)|DE|Отправлено DE, когда произойдет исключение в отлаживаемом программе.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Отправлено DE когда асинхронная вычисление выражений завершена.|  
|IDebugFindSymbolEvent2||УСТАРЕЛ.  НЕ ИСПОЛЬЗУЙТЕ.|  
|[IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|DE|При отправке DE будет выполнена обработка для перехваченного исключения.|  
|[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|DE|Когда программа завершает загрузку отправляется DE.|  
|[IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)|DE|Отправлено DE для отображения интегрированной среды разработки информационное сообщение для пользователя.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Отправлено DE при загрузке или будет выгружен модуль.|  
|[IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md)|DE|Сигнализирует [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] пользовательский интерфейс отладчика для предупреждения пользователей, что символы не удалось обнаружить для запущенного исполняемого файла.|  
|[IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md)|DE|Отправлено DE для отображения интегрированной среды разработки произвольная строка.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|С DE|Отправлено порт для передачи события порта к любому прослушивателю.|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|Отправлено DE или портом, когда процесс будет создан.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|Отправлено DE или портом, когда процесс будет уничтожен.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|Отправлено DE или портом, когда программа будет создана.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|Отправлено DE или портом, когда программа будет разрушена.|  
|[IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md)|DE|Разрешает ядро отладки для переопределения по умолчанию применяются расширения функциональности [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Пользовательский интерфейс после завершения сеанса отладки.|  
|[IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md)|DE|Отправляется из обработчика отладки \(DE\) к сеансу отладки \(SDM\), если имя диспетчера программ изменится.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|При отправке DE новое свойство \(представленное `IDebugProperty2` интерфейс\) был создан.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|При отправке DE свойство будет удалено.|  
|[IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|DE|При отправке DE выход из или за функцией поэтому возвращаемым значением может правильно отобразить.|  
|[IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)|К|Разрешает ядро отладки для чтения метрические параметры удаленно.|  
|[IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|DE|Отправлено DE при завершении будет шаг с заходом, через или из инструкцию.|  
|[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|DE|Отправлено DE для указания на успешное или неуспешное выполнение символов загрузки модуля.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Отправлено DE, когда поток будет создан.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Отправлено DE, когда поток будет уничтожен.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Отправлено DE, когда поток изменяет его имя.|  
  
##  <a name="Expressions"></a> Выражения  
 Эти интерфейсы представляют выражения, которое вычисляется в определенном контексте.  
  
|Интерфейс|Реализуется определяемая|Описание|  
|---------------|------------------------------|--------------|  
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|Представляет выражение для вычисления.  Получено из IDebugExpressionContext2 интерфейс.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Представляет контекст, в котором вычисляется выражение.  Получено из [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) интерфейс.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Отправлено DE когда асинхронная вычисление выражений завершена.|  
  
##  <a name="Memory"></a> Память  
 Эти интерфейсы представляют собой последовательности байтов в памяти.  
  
|Интерфейс|Реализуется определяемая|Описание|  
|---------------|------------------------------|--------------|  
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|Представляет последовательность байтов в памяти, которая может быть считано из или записано.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Представляет расположение в памяти о последовательности байтов.|  
  
##  <a name="Modules"></a> Модули  
 Эти интерфейсы представляют собой модуль, который соответствует исполняемому файлу или dll\-файла.  
  
|Интерфейс|Реализуется определяемая|Описание|  
|---------------|------------------------------|--------------|  
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|Представляет один исполняемый файл или библиотеку DLL.|  
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|Представляет IDebugModule2 были поддерживает символы.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Отправлено DE при загрузке или будет выгружен модуль.|  
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|Представляет сведения о сервере источника, в котором содержится в файле PDB.|  
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|Представляет перечисление по набору модулей, которые известны IDebugProgram2.|  
  
##  <a name="Ports"></a> Порты  
 Эти интерфейсы представляют порты и поставщиков портов.  
  
|Интерфейс|Реализуется определяемая|Описание|  
|---------------|------------------------------|--------------|  
|[IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)|VS, PS|Представляет порт по умолчанию на локальном компьютере.|  
|[IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md)|К|Включает отладчик, использует DCOM для запроса [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Пользовательский интерфейс, чтобы убедиться в том, что брандмауэр не блокирует удаленная отладка.|  
|[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)|VS, PS|Представляет порт.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|PS|Отправлено порт для передачи события порта к любому прослушивателю.|  
|[IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)|PS|Представляет порт, который может начинаться и заканчиваться процессов.|  
|[IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)|PS|Используется для регистрации и отмены регистрации программы с портом. разрешает порт в текущий момент, отлаживанными программы отслеживания.|  
|[IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)|PS|Представляет настраиванный пользовательский интерфейс для выбора порт.|  
|[IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)|К|Представляет запрос для порта, из которого будет создан новый номер порта или будет найден.|  
|[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)|PS|Представляет поставщика с динамическими портами.|  
|[IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)|PS|Представляет поставщика портов, которые могут сохранять \(сохранить на диск\) сведения о портах его создал.|  
|[IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md)|PS|Включает [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Пользовательский интерфейс для отображения текста внутри  **Сведения о транспорте** раздел   **Присоединение к процессу** диалоговое окно.|  
|[IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)|К|Разрешает при запросе информации о конечном компьютере.|  
|[IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)|VS, PS|Представляет перечисление по набору портов.|  
|[IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)|К|Представляет перечисление над набором поставщиков портов.|  
  
##  <a name="Processes"></a> Процессы  
 Эти интерфейсы представляют собой процессы один исполняемый файл, содержащий один или несколько программ.  
  
|Интерфейс|Реализуется определяемая|Описание|  
|---------------|------------------------------|--------------|  
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, DE|Представляет процесс, который в настоящий момент выполняется на компьютере.|  
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, DE|Представляет процесс, который активно поддерживает отладку \(используемую для замены шаг, возобновления и выполнения методов IDebugProgram2 интерфейс\).|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|Отправлено DE или портом, когда процесс будет создан.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|Отправлено DE или портом, когда процесс будет уничтожен.|  
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Представляет процесс, который нужно отслеживать, сеанс вложен в него.|  
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|Представляет перечисление набора процессов на порт.|  
  
##  <a name="Programs"></a> Программы  
 Эти интерфейсы представляют программы, логические блоки выполнения, которые не обязательно соответствуют физическим исполняемому файлу или модуль.  
  
|Интерфейс|Реализуется определяемая|Описание|  
|---------------|------------------------------|--------------|  
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|Представляет IDebugProgram2 , необходимо работать совместно с другими программами, отлаживанными одновременно.|  
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE, PS|Представляет логический блок выполнения.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|Отправлено DE или портом, когда программа будет создана.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|Отправлено DE или портом, когда программа будет разрушена.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Представляет IDebugProgramNode2 это может быть обработано кратным обработчиков отладки.|  
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Представляет IDebugProgram2 необходимо иметь возможность отслеживания, который вложен в ней сеанс.|  
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE, PS|Представляет IDebugProgram2 может возвращать сведения о процессе, в котором он запущен.|  
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE, PS|Представляет программу, которая может быть отладки.|  
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE, PS|Позволяет узлу программы, уведомляемого попытки вложить в связанную программе.|  
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|Предоставляет способ для SDM запросить DE о программах контролируемых разделах DE.|  
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|К|Используется DEs для регистрации программы с SDM, чтобы отобразить их отладки.|  
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE, PS|Представляет IDebugProgramNode2 это может маршалировать интерфейсы через границы потоков или процесса.|  
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE, PS|Представляет перечисление набора служебных программ.|  
  
##  <a name="Properties"></a> Свойства  
 Эти интерфейсы представляют свойства, значение, связанное с заданным контекстом, обычно результатом оценки выражений.  
  
|Интерфейс|Реализуется определяемая|Описание|  
|---------------|------------------------------|--------------|  
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Представляет IDebugProperty2 это позволяет отображать свое значение в пользовательском образом.|  
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|Представляет значение кадра стека, документов или результатов оценки выражений.|  
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|Представляет IDebugProperty2 произвольно, поддерживает длинные строки.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|При отправке DE новое свойство \(представленное IDebugProperty2 интерфейс\) был создан.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|При отправке DE свойство будет удалено.|  
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|Представляет ссылку на свойство, которая может существовать вне любого кадра стека.|  
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|Представляет перечисление по набору [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структуры, которые описывают переменные, регистры, параметров и выражений.|  
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|Представляет перечисление по набору [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) структуры.|  
  
##  <a name="StackFrames"></a> Кадры стека  
 Эти интерфейсы представляют кадр стека, контекст, в котором точка останова или исключение было.  
  
|Интерфейс|Реализуется определяемая|Описание|  
|---------------|------------------------------|--------------|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Представляет контекст, в котором точка останова или исключение было.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Представляет [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) что может обрабатывать перехваченные исключения.|  
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|Представляет перечисление по набору [CODE\_PATH](../../../extensibility/debugger/reference/code-path.md) структуры, которые определяют последовательность вызова функций, используемую для прибытия на указанный кадр стека.|  
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|Представляет перечисление по набору [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структуры, которые описывают кадры стека.|  
  
##  <a name="Threads"></a> Потоки  
 Эти интерфейсы представляют потоки и связанные с ними событий.  
  
|Интерфейс|Реализуется определяемая|Описание|  
|---------------|------------------------------|--------------|  
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|Представляет поток выполнения.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Отправлено DE, когда поток будет создан.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Отправлено DE, когда поток будет уничтожен.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Отправлено DE, когда поток изменяет его имя.|  
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|Представляет перечисление по набору потоков.|  
  
##  <a name="TypeVisualizers"></a> Визуализаторы типа  
 Эти интерфейсы визуализаторов предоставляют поддержку для типа.  Эти интерфейсы обычно реализуются средством оценки выражений.  
  
|Интерфейс|Реализуется определяемая|Описание|  
|---------------|------------------------------|--------------|  
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Представляет массив байтов в визуализатору типа.|  
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Предоставляет методы для получения, что доступ к данным, передаваемым на визуализатору типа.|  
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|Представляет свойство, которое предоставляет доступ к [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) реализации.|  
  
## См. также  
 [Справочник по интерфейсам API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Создание пользовательские отладки ядра](../../../extensibility/debugger/creating-a-custom-debug-engine.md)