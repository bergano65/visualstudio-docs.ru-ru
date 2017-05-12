---
title: "Интерфейс IDebugApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplication — интерфейс"
ms.assetid: 5dfa941b-4cd9-46fa-a230-3f41df9ea205
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Интерфейс IDebugApplication
Методы отладки, отличный от удаленного предоставляет для использования обработчиков и узлами языка.  
  
 В дополнение к методам, наследуемым от интерфейса `IRemoteDebugApplication`, интерфейс `IDebugApplication` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDebugApplication::SetName](../../winscript/reference/idebugapplication-setname.md)|Задает имя приложения.|  
|[IDebugApplication::StepOutComplete](../../winscript/reference/idebugapplication-stepoutcomplete.md)|Процесс отладки уведомляет диспетчер, что обработчик языка в режиме единый\- шага собирается вернуться к своему вызывающему объекту.|  
|[IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)|Вызывает заданную строку для отображения интегрированной средой разработки отладчика.|  
|[IDebugApplication::StartDebugSession](../../winscript/reference/idebugapplication-startdebugsession.md)|Запускает по умолчанию интегрированная среда разработки и вложение отладчика сеанс отладки к этому приложению, если она еще не вложитьо.|  
|[IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)|Вынуждает текущий поток отключения и отправляет уведомление точки останова в интегрированной среде разработки отладчика.|  
|[IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)|Вызывает это приложение освободить все ссылки и выполнить вход неактивного состояние.|  
|[IDebugApplication::GetBreakFlags](../../winscript/reference/idebugapplication-getbreakflags.md)|Возвращает текущие флаги останова для приложения.|  
|[IDebugApplication::GetCurrentThread](../../winscript/reference/idebugapplication-getcurrentthread.md)|Возвращает поток, связанный с выполняющийся в данный момент поток.|  
|[IDebugApplication::CreateAsyncDebugOperation](../../winscript/reference/idebugapplication-createasyncdebugoperation.md)|Предоставляет асинхронный доступ к заданному синхронному операции отладки.|  
|[IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)|Добавляет поставщик перечислителя кадра стека к данному приложению.|  
|[IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)|Удаляет поставщик перечислителя кадра стека из этого приложения.|  
|[IDebugApplication::QueryCurrentThreadIsDebuggerThread](../../winscript/reference/idebugapplication-querycurrentthreadisdebuggerthread.md)|Определяет, если текущий поток выполнения потока отладчика.|  
|[IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)|Предоставляет механизм для вызывающего кода выполняется в потоке отладчика.|  
|[IDebugApplication::CreateApplicationNode](../../winscript/reference/idebugapplication-createapplicationnode.md)|Создает узел нового приложения, который связан с поставщиком заданного документа.|  
|[IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)|Вызывает событие ресурса к интерфейсу `IApplicationDebugger` отладчика.|  
|[IDebugApplication::HandleRuntimeError](../../winscript/reference/idebugapplication-handleruntimeerror.md)|Вынуждает текущий поток отключения и отправляет уведомление ошибок в интегрированной среде разработки отладчика.|  
|[IDebugApplication::FCanJitDebug](../../winscript/reference/idebugapplication-fcanjitdebug.md)|Определяет, если по требованию \(JIT\) отладчик регистрации.|  
|[IDebugApplication::FIsAutoJitDebugEnabled](../../winscript/reference/idebugapplication-fisautojitdebugenabled.md)|Определяет, если отладчик JIT зарегистрировать к основным приложениям автоматическ\- отладка тупым.|  
|[IDebugApplication::AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)|Добавляет глобальный поставщик контекста выражения к данному приложению.|  
|[IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)|Удаляет глобальный поставщик контекста выражения из этого приложения.|