---
title: "Интерфейс IDebugApplication | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplication interface
ms.assetid: 5dfa941b-4cd9-46fa-a230-3f41df9ea205
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07964292785634212099a0bfcf8174ebb55e8713
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplication-interface"></a>Интерфейс IDebugApplication
Предоставляет неудаленной отладки методы для использования, обработчиками языка и узлы.  
  
 Помимо методов, наследуемых от `IRemoteDebugApplication`, `IDebugApplication` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugApplication::SetName](../../winscript/reference/idebugapplication-setname.md)|Задает имя приложения.|  
|[IDebugApplication::StepOutComplete](../../winscript/reference/idebugapplication-stepoutcomplete.md)|Уведомляет диспетчер отладки процессов, языковая подсистема в пошаговом режиме собирается возвращает вызывающему.|  
|[IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)|Вызывает заданную строку для отображения в отладчике интегрированной среды разработки.|  
|[IDebugApplication::StartDebugSession](../../winscript/reference/idebugapplication-startdebugsession.md)|Для запуска отладчика по умолчанию интегрированная среда разработки и присоединяет сеанс отладки для этого приложения, если один еще не подключен.|  
|[IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)|Приводит к блокировке текущего потока и отправит уведомление точки останова в отладчике интегрированной среды разработки.|  
|[IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)|В результате этого приложения освободить все ссылки и введите в неактивном состоянии.|  
|[IDebugApplication::GetBreakFlags](../../winscript/reference/idebugapplication-getbreakflags.md)|Возвращает текущий флаги приостановки выполнения приложения.|  
|[IDebugApplication::GetCurrentThread](../../winscript/reference/idebugapplication-getcurrentthread.md)|Возвращает поток, связанный с текущим выполняемым потоком.|  
|[IDebugApplication::CreateAsyncDebugOperation](../../winscript/reference/idebugapplication-createasyncdebugoperation.md)|Предоставляет асинхронный доступ к отладки данного синхронной операции.|  
|[IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)|Добавляет поставщик перечислитель кадр стека для этого приложения.|  
|[IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)|Удаляет поставщик перечислитель кадра стека из этого приложения.|  
|[IDebugApplication::QueryCurrentThreadIsDebuggerThread](../../winscript/reference/idebugapplication-querycurrentthreadisdebuggerthread.md)|Определяет, является ли текущий поток выполнения потока отладчика.|  
|[IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)|Предоставляет механизм для вызывающего объекта, для выполнения кода в поток отладки.|  
|[IDebugApplication::CreateApplicationNode](../../winscript/reference/idebugapplication-createapplicationnode.md)|Создает новый узел приложения, связанные с конкретным документом.|  
|[IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)|Универсальный событие в отладчик `IApplicationDebugger` интерфейса.|  
|[IDebugApplication::HandleRuntimeError](../../winscript/reference/idebugapplication-handleruntimeerror.md)|Приводит к блокировке текущего потока и отправляет уведомление об ошибке в IDE отладчик.|  
|[IDebugApplication::FCanJitDebug](../../winscript/reference/idebugapplication-fcanjitdebug.md)|Определяет, зарегистрирован ли отладчик just-in-time (JIT).|  
|[IDebugApplication::FIsAutoJitDebugEnabled](../../winscript/reference/idebugapplication-fisautojitdebugenabled.md)|Определяет, если JIT-отладчика был зарегистрирован для узлов ввода-вывода отладки автоматически.|  
|[IDebugApplication::AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)|Добавляет поставщик контекста глобальные выражения к этому приложению.|  
|[IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)|Удаляет поставщик контекста глобальные выражения из этого приложения.|