---
title: "IDebugPortEx2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: fa36bf7ae96058c4eb7c0462114af50fa08af656
ms.lasthandoff: 04/05/2017

---
# <a name="idebugportex2"></a>IDebugPortEx2
Этот интерфейс позволяет сеанса отладки (SDM) диспетчера управления программы и процессы, запущенные на порт.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugPortEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Поставщик пользовательский порт реализует этот интерфейс на тот же объект, реализующий [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md).  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызовы SDM [QueryInterface](/cpp/atl/queryinterface) на `IDebugPort2` интерфейс для получения этого интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugPortEx2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|Запускает исполняемый файл.|  
|[ResumeProcess для](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Возобновляет выполнение процесса.|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|Определяет, можно ли завершить процесс.|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|Завершает процесс.|  
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|Получает идентификатор процесса порта самого.|  
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Возвращает программу, связанный с узлом программы.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс является обычно закрытым между SDM и поставщика другой номер порта.  
  
 При желании модуля отладки (DE) можно найти этот интерфейс [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) передается интерфейс [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) и использовать [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) для запуска программы. Это не обязательное требование, но DE можно сделать то, что его нужно сделать, чтобы запустить программу запроса.  
  
## <a name="requirements"></a>Требования  
 Заголовок: portpriv.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
