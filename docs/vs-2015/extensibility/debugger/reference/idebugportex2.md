---
title: IDebugPortEx2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 35a1acf88acda7a96dffc10706b8467253ae816d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58991170"
---
# <a name="idebugportex2"></a>IDebugPortEx2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс позволяет сеанс отладки управление manager (SDM), программы и процессы, запущенные на порт.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugPortEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Пользовательский порт поставщик реализует этот интерфейс на тот же объект, реализующий [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md).  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Вызовы SDM [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) на `IDebugPort2` интерфейс для получения этого интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugPortEx2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|Запускает исполняемый файл.|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Возобновляет выполнение процесса.|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|Определяет, можно ли завершить процесс.|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|Завершает процесс.|  
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|Получает идентификатор процесса сам класс port.|  
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Возвращает программу, сопоставленную с узлом программы.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс обычно закрыт между SDM и поставщика пользовательского порта.  
  
 При желании модуля отладки (DE) можно найти на этом интерфейсе [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) передается интерфейс [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) и использовать [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) для запуска программы. Это не является обязательным, но DE можно сделать то, что нужно сделать, чтобы запустить программу запроса.  
  
## <a name="requirements"></a>Требования  
 Заголовок: portpriv.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
