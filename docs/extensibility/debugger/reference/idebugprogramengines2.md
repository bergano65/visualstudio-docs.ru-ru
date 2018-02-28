---
title: "IDebugProgramEngines2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramEngines2
helpviewer_keywords:
- IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 8e4830c43fbffeb4f7df627f859e6fd48a4387a7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
Этот интерфейс используется программа узлами для указания всех возможных отладчики (DE), можно отлаживать этой программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugProgramEngines2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 DE или пользовательский порт поставщик реализует этот интерфейс на тот же объект, реализующий [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) для поддержки конкретных DE для конкретной программы установки.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызовите [QueryInterface](/cpp/atl/queryinterface) на `IDebugProgramNode2` интерфейс для получения этого интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugProgramEngines2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|Указывает все возможные DEs, выполнять отладку этой программы.|  
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|Выбирает DE, используемые для отладки этой программы.|  
  
## <a name="remarks"></a>Примечания  
 После DE, выбираемый пользователем, выбор зарегистрирован узел программы путем вызова [SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md). Выбранного ядра становится ядра, возвращенных [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md).  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)