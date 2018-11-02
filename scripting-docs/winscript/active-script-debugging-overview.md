---
title: Обзор отладки активных скриптов | Документы Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Active Script Debugging overview
ms.assetid: ce4ec768-d017-4dfa-a7e3-cced3a29e679
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 447a8faf6e62448e7e8ce9ee8d7d8097fba2dd7b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919368"
---
# <a name="active-script-debugging-overview"></a>Обзор отладки активных скриптов
Интерфейсы отладки активных скриптов обеспечивают не зависящую от языка и узла отладку, а также поддерживают широкий спектр сред разработки.  
  
 ![Хост-процесс скрипта](../winscript/media/scp56activdbgarchgif.gif "Scp56ActivDbgArchgif")  
Рис. 1  
  
 Не зависящая от языка среда отладки способна поддерживать любой язык программирования или сочетание языков, не обладая сведениями о них. Среда отладки также поддерживает пошаговое выполнение и точки останова на разных языках. (Этот обзор посвящен главным образом поддержке скриптовых языков, таких как VBScript и [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].)  
  
 Не зависящий от узла отладчик можно автоматически использовать на любом узле активных скриптов, таком как Internet Explorer или пользовательский узел. Узел определяет, что именно отладчик предоставляет пользователю — от структуры дерева документов до раскраски содержимого и синтаксиса в документах отладки. Это позволяет отобразить отлаженный исходный код в контексте документа узла. Например, Internet Explorer может отобразить скрипт на HTML-странице.  
  
 В подразделах ниже описаны все ключевые компоненты активной отладки и связанные с ними интерфейсы. Тем не менее перед продолжением следует определить некоторые ключевые концепции активной отладки:  
  
 ведущее приложение  
 Приложение, содержащее модули скриптов и предоставляющее набор объектов (или "объектную модель") с поддержкой скриптов.  
  
 модуль языка  
 Компонент, обеспечивающий синтаксический анализ, выполнение и абстракции отладки для определенного языка.  
  
 интегрированная среда разработки отладчика  
 Приложение, предоставляющее пользовательский интерфейс отладки путем взаимодействия с ведущим приложением и модулями языка.  
  
 диспетчер отладки  
 Компонент, который формирует реестр отлаживаемых процессов приложения.  
  
 диспетчер отладки процессов  
 Компонент, который формирует дерево отлаживаемых документов для конкретного приложения, отслеживает запущенные потоки и т. п.  
  
 контекст документа  
 Контекст документа — это абстракция, представляющая определенную область исходного кода документа узла.  
  
 контекст кода  
 Контекст кода представляет определенное место в запущенном коде модуля языка ("виртуальный указатель оператора").  
  
 контекст выражения  
 Определенный контекст (например, кадр стека), в котором выражения могут вычисляться модулем языка.  
  
 просмотр объектов  
 Структурированное и не зависящее от языка представление имени объекта, типа, значения и подчиненных объектов, подходящее для реализации пользовательского интерфейса "окно контрольных значений".  
  
 Ниже приведен обзор каждого из ключевых компонентов активной отладки и связанных с ними интерфейсов, после чего каждый из интерфейсов описан более подробно.  
  
## <a name="language-engine"></a>Модуль языка  
 Модуль языка предоставляет следующие возможности:  
  
- Анализ и выполнение языка.  
  
- Поддержка отладки (точки останова и т. п.).  
  
- Вычисление выражений.  
  
- Раскраска синтаксических конструкций.  
  
- Просмотр объектов.  
  
- Перечисление и анализ стека.  
  
  Ниже указаны интерфейсы, которые должен поддерживать модуль скриптов, чтобы обеспечивать отладку, вычисление выражений и просмотр объектов. Эти интерфейсы используются ведущим приложением для сопоставления контекста документа и контекстов кода модуля, а также пользовательским интерфейсом отладчика для обеспечения вычисления выражений, перечисления стека и просмотра объектов.  
  
  [Интерфейс IActiveScriptDebug](../winscript/reference/iactivescriptdebug-interface.md)  
  Предоставляет раскраску синтаксических конструкций и перечисление контекста кода.  
  
  [Интерфейс IActiveScriptErrorDebug](../winscript/reference/iactivescripterrordebug-interface.md)  
  Возвращает контексты документов и кадры стека для ошибок.  
  
  [Интерфейс IActiveScriptSiteDebug](../winscript/reference/iactivescriptsitedebug-interface.md)  
  Размещает предоставленную ссылку из модуля скриптов в отладчике.  
  
  [Интерфейс IDebugCodeContext](../winscript/reference/idebugcodecontext-interface.md)  
  Предоставляет виртуальный указатель оператора в потоке.  
  
  [Интерфейс IEnumDebugCodeContexts](../winscript/reference/ienumdebugcodecontexts-interface.md)  
  Перечисляет контексты кода, соответствующие контексту документа.  
  
  [Интерфейс IDebugStackFrame](../winscript/reference/idebugstackframe-interface.md)  
  Представляет логический кадр стека в стеке потоков.  
  
  [Интерфейс IDebugExpressionContext](../winscript/reference/idebugexpressioncontext-interface.md)  
  Предоставляет контекст, в котором можно вычислять выражения.  
  
  [Интерфейс IDebugStackFrameSniffer](../winscript/reference/idebugstackframesniffer-interface.md)  
  Предоставляет способ для перечисления логических кадров стека.  
  
  [Интерфейс IDebugExpression](../winscript/reference/idebugexpression-interface.md)  
  Представляет асинхронно вычисляемое выражение.  
  
  [Интерфейс IDebugSyncOperation](../winscript/reference/idebugsyncoperation-interface.md)  
  Позволяет модулю скриптов абстрагировать операцию, которую требуется выполнить вложенной в определенный заблокированный поток.  
  
  [Интерфейс IDebugAsyncOperation](../winscript/reference/idebugasyncoperation-interface.md)  
  Предоставляет асинхронный доступ к синхронной операции отладки.  
  
  [Интерфейс IDebugAsyncOperationCallBack](../winscript/reference/idebugasyncoperationcallback-interface.md)  
  Предоставляет состояния события, связанные с ходом оценки интерфейса `IDebugAsyncOperation`.  
  
  [Интерфейс IEnumDebugExpressionContexts](../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
  Перечисляет коллекцию объектов `IDebugExpressionContexts`.  
  
  [Интерфейс IProvideExpressionContexts](../winscript/reference/iprovideexpressioncontexts-interface.md)  
  Предоставляет способ для перечисления контекстов выражений, известных по определенному компоненту.  
  
  [Интерфейс IDebugFormatter](../winscript/reference/idebugformatter-interface.md)  
  Позволяет языку или интегрированной среде разработки настроить преобразование значениями VARIANT или типами VARTYPE и строками.  
  
  [Интерфейс IDebugStackFrameSnifferEx](../winscript/reference/idebugstackframesnifferex-interface.md)  
  Перечисляет логические кадры стека для PDM.  
  
## <a name="hosts"></a>Узлы  
 Узел:  
  
- размещает модули языка;  
  
- предоставляет объектную модель (набор объектов, которые можно использовать в скрипте);  
  
- определяет дерево документов, которые можно отлаживать, и их содержимое;  
  
- организует скрипты в виртуальные приложения.  
  
  Существует два типа узлов:  
  
- Оконечный узел ввода-вывода поддерживает только базовые интерфейсы активных скриптов. Он не контролирует организации или структуру документов, они полностью определяются скриптами, предоставленными модулям языка.  
  
- Промежуточный узел поддерживает больше интерфейсов, что позволяет ему определить дерево документов, содержимое документов и раскраску синтаксических структур. Имеется ряд вспомогательных интерфейсов, описанных в следующем подразделе, которые позволяют узлу значительно проще стать промежуточным.  
  
### <a name="smart-host-helper-interfaces"></a>Вспомогательные интерфейсы промежуточных узлов  
 Методы `IDebugDocumentHelper` предоставляют значительно упрощенный набор интерфейсов, которые узел может использовать для получения преимуществ промежуточного узла, не имея дело со всеми сложностями и возможностями полноценных интерфейсов узла.  
  
 Конечного же, для использования этих интерфейсов узел не требуется. Однако благодаря им можно избежать реализации или использования более сложных интерфейсов.  
  
 [Интерфейс IDebugDocumentHelper](../winscript/reference/idebugdocumenthelper-interface.md)  
 Реализуется PDM и предоставляет реализации многих интерфейсов, необходимых для промежуточного размещения.  
  
 [Интерфейс IDebugDocumentHost](../winscript/reference/idebugdocumenthost-interface.md)  
 Реализуется (необязательно) узлом для предоставления функциональных возможностей конкретного узла, например раскраски синтаксиса, отладчику.  
  
 Дополнительные сведения см. в разделе [Реализация вспомогательных интерфейсов промежуточных узлов](../winscript/implementing-smart-host-helper-interfaces.md).  
  
### <a name="full-smart-host-interfaces"></a>Полноценные интерфейсы промежуточных узлов  
 Ниже приведен полный набор интерфейсов, которые промежуточный узел должен реализовывать или использовать, если он не использует вспомогательные интерфейсы.  
  
 Интерфейсы, реализуемые узлом:  
  
 [Интерфейс IDebugDocumentInfo](../winscript/reference/idebugdocumentinfo-interface.md)  
 Предоставляет сведения о документе, экземпляр которого может как создаваться, так и нет.  
  
 [Интерфейс IDebugDocumentProvider](../winscript/reference/idebugdocumentprovider-interface.md)  
 Предоставляет средства для создания экземпляра документа по требованию.  
  
 [Интерфейс IDebugDocument](../winscript/reference/idebugdocument-interface.md)  
 Базовый интерфейс для всех документов отладки.  
  
 [Интерфейс IDebugDocumentText](../winscript/reference/idebugdocumenttext-interface.md)  
 Предоставляет доступ к исключительно текстовой версии документа отладки.  
  
 [Интерфейс IDebugDocumentTextAuthor](../winscript/reference/idebugdocumenttextauthor-interface.md)  
 Разрешает редактирование исключительно текстовой версии документа отладки.  
  
 [Интерфейс IDebugDocumentContext](../winscript/reference/idebugdocumentcontext-interface.md)  
 Предоставляет абстрактное представление части документа, отладка которого выполняется.  
  
 Интерфейсы, реализованные PDM от имени узла:  
  
 [Интерфейс IDebugApplicationNode](../winscript/reference/idebugapplicationnode-interface.md)  
 Расширяет функциональность интерфейса `IDebugDocumentProvider`, предоставляя контекст в дереве проекта.  
  
## <a name="debugger-ide"></a>Интегрированная среда разработки отладчика  
 Интегрированная среда разработки является не зависящим от языка пользовательским интерфейсом отладки. Консоль предоставляет следующие возможности:  
  
- Средства просмотра и редакторы документов.  
  
- Управление точками останова.  
  
- Вычисление выражений и окна контрольных значений.  
  
- Просмотр кадров стека.  
  
- Просмотр объектов/классов.  
  
- Просмотр структуры виртуальных приложений.  
  
  Интерфейсы, реализуемые отладчиком:  
  
  [Интерфейс IApplicationDebugger](../winscript/reference/iapplicationdebugger-interface.md)  
  Основной интерфейс, предоставляемый сеансом IDE отладчика.  
  
  [Интерфейс IApplicationDebuggerUI](../winscript/reference/iapplicationdebuggerui-interface.md)  
  Позволяет внешнему компоненту лучше контролировать пользовательский интерфейс отладчика.  
  
  [Интерфейс IDebugExpressionCallBack](../winscript/reference/idebugexpressioncallback-interface.md)  
  Поставляет события состояния для обозначения хода оценки `IDebugExpression`.  
  
  [Интерфейс IDebugDocumentTextEvents](../winscript/reference/idebugdocumenttextevents-interface.md)  
  Предоставляет события, указывающие на изменения в сопоставленном текстовом документе.  
  
  [Интерфейс IDebugApplicationNodeEvents](../winscript/reference/idebugapplicationnodeevents-interface.md)  
  Предоставляет интерфейс событий для интерфейса `IDebugApplicationNode`.  
  
### <a name="machine-debug-manager"></a>Диспетчер отладки  
 Диспетчер отладки предоставляет точку привязки между виртуальными приложениями и отладчиками, формируя и перечисляя список активных виртуальных приложений.  
  
 [Интерфейс IDebugSessionProvider](../winscript/reference/idebugsessionprovider-interface.md)  
 Устанавливает сеанс отладки для выполняемого приложения.  
  
 [Интерфейс IMachineDebugManager](../winscript/reference/imachinedebugmanager-interface.md)  
 Основной интерфейс для диспетчера отладки.  
  
 [Интерфейс IMachineDebugManagerCookie](../winscript/reference/imachinedebugmanagercookie-interface.md)  
 Аналогичен интерфейсу `IMachineDebugManager`, но этот интерфейс поддерживает файлы "cookie" отладки.  
  
 [Интерфейс IMachineDebugManagerEvents](../winscript/reference/imachinedebugmanagerevents-interface.md)  
 Сигнализирует об изменениях в списке запущенных приложений, формируемом диспетчером отладки.  
  
 [Интерфейс IEnumRemoteDebugApplications](../winscript/reference/ienumremotedebugapplications-interface.md)  
 Перечисляет запущенные приложения на компьютере.  
  
### <a name="process-debug-manager"></a>Диспетчер отладки процессов  
 Диспетчер PDM:  
  
- синхронизирует отладку нескольких модулей языка;  
  
- формирует дерево отлаживаемых документов;  
  
- объединяет кадры стека;  
  
- координирует работу точек останова и пошаговое выполнение в разных модулях языка;  
  
- отслеживает потоки;  
  
- обслуживает поток отладчика для асинхронной обработки;  
  
- взаимодействует с диспетчером отладки и интегрированной средой разработки отладчика.  
  
  Ниже приведены интерфейсы, предоставляемые диспетчером отладки процессов.  
  
  [Интерфейс IProcessDebugManager](../winscript/reference/iprocessdebugmanager-interface.md)  
  Основной интерфейс для диспетчера отладки процессов. Этот интерфейс может создать, добавить или удалить виртуальное приложение в процессе.  
  
  [Интерфейс IRemoteDebugApplication](../winscript/reference/iremotedebugapplication-interface.md)  
  Представляет выполняющееся приложение.  
  
  [Интерфейс IDebugApplication](../winscript/reference/idebugapplication-interface.md)  
  Предоставляет неудаленные методы отладки для использования модулями языка и узлами.  
  
  [Интерфейс IRemoteDebugApplicationThread](../winscript/reference/iremotedebugapplicationthread-interface.md)  
  Представляет поток исполнения в определенном приложении.  
  
  [Интерфейс IDebugApplicationThread](../winscript/reference/idebugapplicationthread-interface.md)  
  Позволяет модулям языка и узлам обеспечивать синхронизацию потоков и хранить сведения о состоянии отладки для конкретного потока.  
  
  [Интерфейс IEnumRemoteDebugApplicationThreads](../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
  Перечисляет запущенные потоки в приложении.  
  
  [Интерфейс IDebugThreadCall](../winscript/reference/idebugthreadcall-interface.md)  
  Диспетчеризирует маршалированные вызовы.  
  
  [Интерфейс IDebugApplicationNode](../winscript/reference/idebugapplicationnode-interface.md)  
  Сохраняет положение документа в иерархии.  
  
  [Интерфейс IEnumDebugApplicationNodes](../winscript/reference/ienumdebugapplicationnodes-interface.md)  
  Перечисляет дочерние узлы узла, связанного с приложением.  
  
  [Интерфейс IEnumDebugStackFrames](../winscript/reference/ienumdebugstackframes-interface.md)  
  Перечисляет кадры стека, соответствующие потоку, с объединением из модулей.  
  
  [Интерфейс IDebugCookie](../winscript/reference/idebugcookie-interface.md)  
  Разрешает отправлять отладочный файл cookie для его задания в отладчиках скриптов.  
  
  [Интерфейс IDebugHelper](../winscript/reference/idebughelper-interface.md)  
  Служит в качестве фабрики для обозревателей объектов и простых точек подключения для модулей скриптов.  
  
  [Интерфейс ISimpleConnectionPoint](../winscript/reference/isimpleconnectionpoint-interface.md)  
  Предоставляет простой способ для описания и перечисление событий, произошедших в конкретной точке подключения, для модулей скриптов.  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы отладчика активных скриптов](../winscript/reference/active-script-debugger-interfaces.md)