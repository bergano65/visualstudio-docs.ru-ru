---
title: "Обзор отладки активных скриптов | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Обзор отладки активных скриптов"
ms.assetid: ce4ec768-d017-4dfa-a7e3-cced3a29e679
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Обзор отладки активных скриптов
Интерфейсы отладки активного сценария позволяют отладка не зависящим от языка, после внесения параметров и поддерживают широкий набор сред разработки.  
  
 ![Процесс основного приложения скрипта](../winscript/media/scp56activdbgarchgif.png "Scp56ActivDbgArchgif")  
Рисунок 1  
  
 Не зависящий от языка среды отладки может поддерживать любой язык программирования или набор языков программирования, без наличия определенной статье любого из этих языков.  Среда отладки также поддерживает переход точки останова на нескольких языках.  \(Этот раздел посвящен главным образом на языках скриптов поддержки, таких как VBScript и [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]\).  
  
 Отладчик после внесения от автоматически можно использовать с любым узлом активного сценария, например Internet Explorer или пользовательское основное приложение.  Элементы управления ведущего приложения, отладчик предоставляет пользователю, из структуры схемы документации к содержимому и раскраске синтаксических конструкций документов отладки.  Это позволяет сеанс исходный код, отображаемое в контексте узла документа.  Например, Internet Explorer может отображать скрипта на странице HTML.  
  
 В подразделах ниже, описывается каждый является ключевым компонентом в активной отладку и связанные интерфейсы.  Однако перед продолжением включена, несколько активных ключевых понятий отладки необходимо указать:  
  
 ведущее приложение  
 Приложение, узлы обработчики скриптов и предоставляет scriptable набор объектов \(или "объектную модель"\).  
  
 обработчик языка  
 Компонент, обеспечивающий анализа, выполнение и отладку абстракции для определенного языка.  
  
 интегрированная среда разработки отладчика  
 Приложение, которое предоставляет пользовательский интерфейс отладки, взаимодействовать с обработчиками ведущего приложения и языка.  
  
 компьютер отладки диспетчер  
 Компонент, который поддерживает реестр отлаживаемого процессов приложений.  
  
 процесс отладки диспетчер  
 Компонент, который поддерживает дерево отлаживаемого документов для конкретного приложения, выполняющиеся потоки отслеживает и т д  
  
 контекст документа  
 Контекст документа абстракция, представляющий определенный диапазон в исходном коде узла документа.  
  
 контекст кода  
 Контекст кода представляет указанное расположение при выполнении кода обработчика языка виртуальный указателя инструкций \(""\).  
  
 контекст выражения  
 Указанный контекст \(например, кадр стека\), в котором выражения могут быть вычислены обработчиком языка.  
  
 просмотр объектов  
 Составные, независимые от языка представление имени объекта, тип значения и вложенных объектов, необходимых для реализации "пользовательского интерфейса окна контрольных значений".  
  
 Ниже обзор каждого из ключевых активных компонентов и соответствовать отладки, соответствующие интерфейсы, за сведениями этих интерфейсов.  
  
## Обработчик языка  
 Предоставляет обработчик языка:  
  
-   Синтаксический анализ и выполнение языка.  
  
-   Поддержка отладки \(точки останова и т д\).  
  
-   Вычисление выражений.  
  
-   Выделение синтаксических конструкций.  
  
-   Для просмотра объекта.  
  
-   Перечисление и анализа стека.  
  
 Ниже интерфейсы, обработчик скриптов для поддержки для предоставления отладки, вычисление выражений, и просмотра объекта.  Эти интерфейсы используются ведущим приложением сопоставления между его контексте документа и контекстами обработчик, а также вычислением выражений задачи пользовательского интерфейса отладчика, перечислением стека и просмотра объекта.  
  
 [Интерфейс IActiveScriptDebug](../winscript/reference/iactivescriptdebug-interface.md)  
 Содержит перечисление контекста цветового выделения синтаксических конструкций и кода.  
  
 [Интерфейс IActiveScriptErrorDebug](../winscript/reference/iactivescripterrordebug-interface.md)  
 Возвращает контекст и кадры стека документа для ошибок.  
  
 [Интерфейс IActiveScriptSiteDebug](../winscript/reference/iactivescriptsitedebug-interface.md)  
 Ссылка предусмотренная узла из обработчика скриптов в отладчике.  
  
 [Интерфейс IDebugCodeContext](../winscript/reference/idebugcodecontext-interface.md)  
 Предоставляет виртуальный "указателя инструкций" в потоке.  
  
 [Интерфейс IEnumDebugCodeContexts](../winscript/reference/ienumdebugcodecontexts-interface.md)  
 Перечисляет контексты кода, соответствующие контексту документа.  
  
 [Интерфейс IDebugStackFrame](../winscript/reference/idebugstackframe-interface.md)  
 Представляет логический кадр стека в стеке потока.  
  
 [Интерфейс IDebugExpressionContext](../winscript/reference/idebugexpressioncontext-interface.md)  
 Предоставляет контекст, в котором для вычисления выражений.  
  
 [Интерфейс IDebugStackFrameSniffer](../winscript/reference/idebugstackframesniffer-interface.md)  
 Предоставляет способ отображения логических кадры стека.  
  
 [Интерфейс IDebugExpression](../winscript/reference/idebugexpression-interface.md)  
 Представляет асинхронно, вычисляемое выражение.  
  
 [Интерфейс IDebugSyncOperation](../winscript/reference/idebugsyncoperation-interface.md)  
 Позволяет легко абстрактно представить обработчика скриптов операцию, которую необходимо запускать, вложенным в определенном заблокированного потока.  
  
 [Интерфейс IDebugAsyncOperation](../winscript/reference/idebugasyncoperation-interface.md)  
 Предоставляет доступ к синхронному асинхронный отладки операции.  
  
 [Интерфейс IDebugAsyncOperationCallBack](../winscript/reference/idebugasyncoperationcallback-interface.md)  
 Предоставляет события, связанные с состояния ход выполнения вычислений интерфейса `IDebugAsyncOperation`.  
  
 [Интерфейс IEnumDebugExpressionContexts](../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
 Содержит коллекцию объектов `IDebugExpressionContexts`.  
  
 [Интерфейс IProvideExpressionContexts](../winscript/reference/iprovideexpressioncontexts-interface.md)  
 Предоставляет способ отображения контекстах выражения известные некоторым компонентом.  
  
 [Интерфейс IDebugFormatter](../winscript/reference/idebugformatter-interface.md)  
 Позволяет язык или интегрированная среда разработки настраивать преобразование между значениями или РАЗЛИЧНЫМИ типами и строками VARTYPE.  
  
 [Интерфейс IDebugStackFrameSnifferEx](../winscript/reference/idebugstackframesnifferex-interface.md)  
 Список логических кадры стека для PDM.  
  
## узлы  
 Узла.  
  
-   Узлы обработчики языка.  
  
-   Предоставляет объектную модель \(набор объектов, который может быть написанный\).  
  
-   Задает дерево документов, которые можно отлаживать и их содержимое.  
  
-   Формирует скрипты в виртуальных приложения.  
  
 2 Типа узлов:  
  
-   Тупой узел поддерживает только основные интерфейсы активного сценария.  Он не имеет элемент управления над структурой или двумя документа; это определяется все обработчики скриптов снабженными языка.  
  
-   Промежуточный узел поддерживает более крупный набор интерфейсов, позволяющий его для определения схемы документации, содержимое документа и цветового выделения синтаксических конструкций.  Вспомогательный набор интерфейсов, описанных в следующем подразделе, которые делают их гораздо проще для узла быть промежуточным узлом.  
  
### Интерфейсы поддержки промежуточного узла  
 Методы `IDebugDocumentHelper` предоставляют значительно упрощенный набор интерфейсов, узел может использоваться для получения преимущества SMART\- размещения без обработки \(полная сложность и степень\) полных интерфейсов узла.  
  
 Узел не требуется для использования этих интерфейсов, конечно.  Однако с помощью этих интерфейсов позволяет избежать реализовать или использовать несколько более осложненных интерфейсов.  
  
 [Интерфейс IDebugDocumentHelper](../winscript/reference/idebugdocumenthelper-interface.md)  
 Не реализовано PDM и предоставляет реализации для многих необходимых интерфейсов для умного размещения.  
  
 [Интерфейс IDebugDocumentHost](../winscript/reference/idebugdocumenthost-interface.md)  
 Реализован \(при необходимости\) узла, чтобы для публикации после внесения функции, например выделение синтаксических конструкций, в отладчике.  
  
 Для получения дополнительной информации см. [Реализация вспомогательных интерфейсов промежуточных узлов](../winscript/implementing-smart-host-helper-interfaces.md).  
  
### Полные интерфейсы узла.  
 Ниже полный набор интерфейсов, реализуемых промежуточный узел должен реализовывать или использовать, если он не использует интерфейсы поддержки.  
  
 Интерфейсы, реализованном основным приложением.  
  
 [Интерфейс IDebugDocumentInfo](../winscript/reference/idebugdocumentinfo-interface.md)  
 Сведения о документе, который может и не может быть создан экземпляр.  
  
 [Интерфейс IDebugDocumentProvider](../winscript/reference/idebugdocumentprovider-interface.md)  
 Предоставляет средства для создания документа по требованию.  
  
 [Интерфейс IDebugDocument](../winscript/reference/idebugdocument-interface.md)  
 Базовый интерфейс для всех отладки документы.  
  
 [Интерфейс IDebugDocumentText](../winscript/reference/idebugdocumenttext-interface.md)  
 Предоставляет доступ к версии документа текст только для отладки.  
  
 [Интерфейс IDebugDocumentTextAuthor](../winscript/reference/idebugdocumenttextauthor-interface.md)  
 Позволяет изменить текст версии документа только для отладки.  
  
 [Интерфейс IDebugDocumentContext](../winscript/reference/idebugdocumentcontext-interface.md)  
 Предоставляет абстрактное представление части отлаживаемой документа.  
  
 Интерфейсы, PDM от имени узла.  
  
 [Интерфейс IDebugApplicationNode](../winscript/reference/idebugapplicationnode-interface.md)  
 Расширяет функциональные возможности интерфейса `IDebugDocumentProvider`, указав контекст в дерево проекта.  
  
## Интегрированная среда разработки отладчика  
 Интегрированная среда разработки использовать независимый от языка пользовательского интерфейса отладки.  Он предоставляет:  
  
-   Просмотр\/редакторы документа.  
  
-   Управление точки останова.  
  
-   Вычисления выражений и окна контрольных значений.  
  
-   Просмотр кадра стека.  
  
-   Просмотр объекта или класса.  
  
-   Просмотреть структуру виртуального приложения.  
  
 Интерфейсы, отладчиком.  
  
 [Интерфейс IApplicationDebugger](../winscript/reference/iapplicationdebugger-interface.md)  
 Основной интерфейс предоставленный сеансом интегрированной среды разработки отладчика.  
  
 [Интерфейс IApplicationDebuggerUI](../winscript/reference/iapplicationdebuggerui-interface.md)  
 Дает внешний компонент более элементов управления в интерфейсе пользователя \(UI\) отладчика.  
  
 [Интерфейс IDebugExpressionCallBack](../winscript/reference/idebugexpressioncallback-interface.md)  
 Предоставляет события состояния выполнения для выполнения вычисления `IDebugExpression`.  
  
 [Интерфейс IDebugDocumentTextEvents](../winscript/reference/idebugdocumenttextevents-interface.md)  
 Предоставляет события, изменения в связанный текстовый документ.  
  
 [Интерфейс IDebugApplicationNodeEvents](../winscript/reference/idebugapplicationnodeevents-interface.md)  
 Предоставляет интерфейс событий для интерфейса `IDebugApplicationNode`.  
  
### Компьютер отладки диспетчер  
 Компьютер отладки диспетчер предоставляет точку соединения между виртуальными приложениями и отладчиками, обслуживая и перечисления списка активных виртуальных приложений.  
  
 [Интерфейс IDebugSessionProvider](../winscript/reference/idebugsessionprovider-interface.md)  
 Задает сеанс отладки для выполняющегося приложения.  
  
 [Интерфейс IMachineDebugManager](../winscript/reference/imachinedebugmanager-interface.md)  
 Основной интерфейс к компьютеру диспетчер отладки.  
  
 [Интерфейс IMachineDebugManagerCookie](../winscript/reference/imachinedebugmanagercookie-interface.md)  
 Аналогично интерфейсу `IMachineDebugManager`, но этот интерфейс поддерживает отладки файла cookie.  
  
 [Интерфейс IMachineDebugManagerEvents](../winscript/reference/imachinedebugmanagerevents-interface.md)  
 Изменения сигналов в выполняющемся поддерживаемом списке отладки приложения компьютером менеджера.  
  
 [Интерфейс IEnumRemoteDebugApplications](../winscript/reference/ienumremotedebugapplications-interface.md)  
 Перечисляет выполнение приложения на компьютере.  
  
### Процесс отладки диспетчер  
 PDM выполняет следующие действия:  
  
-   Синхронизирует отладка обработчиков нескольких языков.  
  
-   Поддерживает дерево отлаживаемого документов.  
  
-   Оптимизатором кадры стека.  
  
-   Координат точки останова и пошаговое выполнение с заходом обработчики языка.  
  
-   Отслеживает потоков.  
  
-   Поддерживает поток отладчика для асинхронного действия.  
  
-   Взаимодействует с компьютером отладки и диспетчер интегрированная среда разработки отладчика.  
  
 Следующие интерфейсы, предоставляемые в процессе отладки диспетчера.  
  
 [Интерфейс IProcessDebugManager](../winscript/reference/iprocessdebugmanager-interface.md)  
 Базовый интерфейс для процесса отладки диспетчера.  Этот интерфейс может создать, добавление или удаление виртуальное приложение из процесса.  
  
 [Интерфейс IRemoteDebugApplication](../winscript/reference/iremotedebugapplication-interface.md)  
 Представляет работающее приложение.  
  
 [Интерфейс IDebugApplication](../winscript/reference/idebugapplication-interface.md)  
 Методы отладки представлены non\-remotable для использования обработчиками и узлами языка.  
  
 [Интерфейс IRemoteDebugApplicationThread](../winscript/reference/iremotedebugapplicationthread-interface.md)  
 Представляет поток выполнения внутри данного приложения.  
  
 [Интерфейс IDebugApplicationThread](../winscript/reference/idebugapplicationthread-interface.md)  
 Позволяет обработчики и узлы языка, чтобы обеспечить синхронизацию потока и поддержки потока с, данные DEBUG\- состояния.  
  
 [Интерфейс IEnumRemoteDebugApplicationThreads](../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
 Перечисляет выполняющиеся потоки в приложении.  
  
 [Интерфейс IDebugThreadCall](../winscript/reference/idebugthreadcall-interface.md)  
 Вызовы маршалированные диспетчеризациями.  
  
 [Интерфейс IDebugApplicationNode](../winscript/reference/idebugapplicationnode-interface.md)  
 Поддерживает позицию для документа в иерархии.  
  
 [Интерфейс IEnumDebugApplicationNodes](../winscript/reference/ienumdebugapplicationnodes-interface.md)  
 Перечисляет дочерние узлы узла, связанного с приложением.  
  
 [Интерфейс IEnumDebugStackFrames](../winscript/reference/ienumdebugstackframes-interface.md)  
 Перечисляет кадры стека, соответствующая поток, объединенный из обработчиков.  
  
 [Интерфейс IDebugCookie](../winscript/reference/idebugcookie-interface.md)  
 Поддерживает файлы cookie отладки, настройку в отладчики скрипта.  
  
 [Интерфейс IDebugHelper](../winscript/reference/idebughelper-interface.md)  
 Служит в качестве фабрики для обозревателей объектов и простых точек подключения для обработчиков скриптов.  
  
 [Интерфейс ISimpleConnectionPoint](../winscript/reference/isimpleconnectionpoint-interface.md)  
 Предоставляет простой способ для описания и перечисления увольнянные события в заданной точке подключения, для обработчиков скриптов.  
  
## См. также  
 [Интерфейсы отладчика активных скриптов](../winscript/reference/active-script-debugger-interfaces.md)