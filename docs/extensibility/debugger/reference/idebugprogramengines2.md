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
caps.latest.revision: 11
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 7e9573c4c039a335fc65776483760d06067d94ff
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
Этот интерфейс используется программа узлами для указания всех возможных отладчики (DE), можно отлаживать программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugProgramEngines2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 DE или пользовательский порт поставщик реализует этот интерфейс на тот же объект, реализующий [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) для поддержки конкретных DE для определенной программы установки.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызов [QueryInterface](/visual-cpp/atl/queryinterface) на `IDebugProgramNode2` интерфейса для получения этого интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugProgramEngines2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|Указывает все возможные DEs, можно отлаживать программы.|  
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|Выбирает DE, используемые для отладки программы.|  
  
## <a name="remarks"></a>Примечания  
 После выбора пользователем DE Выбор регистрируется с узлом программы путем вызова [SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md). Выбранного ядра становится ядра, возвращенный [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md).  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)
