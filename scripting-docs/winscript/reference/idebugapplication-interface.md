---
title: Интерфейс IDebugApplication | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication interface
ms.assetid: 5dfa941b-4cd9-46fa-a230-3f41df9ea205
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8229f234f8a8ce607f36c48e070cb3d40a211d45
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62990827"
---
# <a name="idebugapplication-interface"></a>Интерфейс IDebugApplication
Предоставляет методы отладки без удаленного для использования модулями языка и узлами.  
  
 Помимо методов, наследуемых от `IRemoteDebugApplication`, `IDebugApplication` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugApplication::SetName](../../winscript/reference/idebugapplication-setname.md)|Задает имя приложения.|  
|[IDebugApplication::StepOutComplete](../../winscript/reference/idebugapplication-stepoutcomplete.md)|Уведомляет диспетчер отладки процессов, что модуль языка в пошаговом режиме будет возвращать его вызывающему.|  
|[IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)|Вызывает заданную строку для отображения в отладчике интегрированной среды разработки.|  
|[IDebugApplication::StartDebugSession](../../winscript/reference/idebugapplication-startdebugsession.md)|Запускает отладчик по умолчанию интегрированная среда разработки и присоединяет сеанс отладки данного приложения, если один еще не присоединен.|  
|[IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)|Приводит к блокировке текущего потока и отправляет уведомление точки останова в отладчике интегрированной среды разработки.|  
|[IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)|Вызывает это приложение освободить все ссылки и введите в неактивном состоянии.|  
|[IDebugApplication::GetBreakFlags](../../winscript/reference/idebugapplication-getbreakflags.md)|Возвращает текущий флаги break для приложения.|  
|[IDebugApplication::GetCurrentThread](../../winscript/reference/idebugapplication-getcurrentthread.md)|Возвращает поток, связанный с текущим выполняемым потоком.|  
|[IDebugApplication::CreateAsyncDebugOperation](../../winscript/reference/idebugapplication-createasyncdebugoperation.md)|Предоставляет асинхронный доступ к данной синхронной операции отладки.|  
|[IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)|Добавляет поставщик перечислитель кадра стека к этому приложению.|  
|[IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)|Удаляет поставщик перечислитель кадра стека из этого приложения.|  
|[IDebugApplication::QueryCurrentThreadIsDebuggerThread](../../winscript/reference/idebugapplication-querycurrentthreadisdebuggerthread.md)|Определяет, является ли текущий поток выполнения потока отладчика.|  
|[IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)|Предоставляет механизм для запуска кода в отладчике потока вызывающего объекта.|  
|[IDebugApplication::CreateApplicationNode](../../winscript/reference/idebugapplication-createapplicationnode.md)|Создает новый узел приложения, связанные с конкретным документом.|  
|[IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)|Срабатывает универсального события отладчика `IApplicationDebugger` интерфейс.|  
|[IDebugApplication::HandleRuntimeError](../../winscript/reference/idebugapplication-handleruntimeerror.md)|Приводит к блокировке текущего потока и отправляет уведомление об ошибке отладчика интегрированной среды разработки.|  
|[IDebugApplication::FCanJitDebug](../../winscript/reference/idebugapplication-fcanjitdebug.md)|Определяет, зарегистрирован ли отладчик just-in-time (JIT).|  
|[IDebugApplication::FIsAutoJitDebugEnabled](../../winscript/reference/idebugapplication-fisautojitdebugenabled.md)|Определяет, если JIT-отладчик был зарегистрирован для ввода-вывода узлы auto-debug.|  
|[IDebugApplication::AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)|Добавляет поставщик контекста глобальное выражение для этого приложения.|  
|[IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)|Удаляет поставщик контекста глобальное выражение из этого приложения.|