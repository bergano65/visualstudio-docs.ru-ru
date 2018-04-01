---
title: IDebugEngineLaunch2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
caps.latest.revision: 12
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: fb53f64b6b98ed6d02774977138cfd4faf5b8f83
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
Используется обработчиком отладки (DE) для запуска и завершения программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugEngineLaunch2 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Этот интерфейс реализуется пользовательский DE, он имеет особые требования для запуска процесса, который не может быть обработан полностью другой номер порта. Эта ситуация обычно возникает, когда DE является частью интерпретатор и отлаживаемого процесса — это сценарий: интерпретатор должен запускаться сначала, и затем сценарий загружается и запускается. Порт может запускать интерпретатор, а скрипт может потребоваться специальная обработка (который где DE ролью). Этот интерфейс реализуется только в том случае, если имеются особые требования для запуска программы, которая не может обрабатывать другой номер порта.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Этот интерфейс называется диспетчером сеанса отладки (SDM) Если SDM можно получить этот интерфейс из [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) интерфейс (использование QueryInterface). Если этот интерфейс может быть получен, SDM знает, что DE имеет особые требования и вызывает этот интерфейс, чтобы запустить программу вместо запуска его порт.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugEngineLaunch2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Запускает процесс, посредством DE.|  
|[ResumeProcess для](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Возобновление выполнения процессов.|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Определяет, если процесс может быть завершен.|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Завершает процесс.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)