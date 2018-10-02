---
title: IDebugPortEx2 | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 091cad434d4674e568afa5cf09eb05d8cb729735
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563276"
---
# <a name="idebugportex2"></a>IDebugPortEx2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugPortEx2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportex2).  
  
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

