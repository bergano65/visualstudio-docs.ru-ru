---
title: IDebugProviderProgramNode2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
caps.latest.revision: 8
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 8c083d9b054ecde18d1e1fff8ca5bb8cbb6be659
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
Этот интерфейс маршалирует интерфейсы, связанные с программой через границы процессов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugProviderProgramNode2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс на тот же объект, реализующий [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) для поддержки интерфейсов маршалинга через границы процессов.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызовите [QueryInterface](/cpp/atl/queryinterface) на `IDebugProgramNode2` интерфейс для получения этого интерфейса. Если этот интерфейс не может быть получен, DE не поддерживает маршалинг интерфейсов.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 Этот интерфейс реализует следующий метод:  
  
|Метод|Описание:|  
|------------|-----------------|  
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|Возвращает указанный интерфейс через границы процессов.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс реализуется, когда запускается DE в отдельную рабочую область из отлаживаемой программы: например, когда DE работает в пространстве процесса Visual Studio вместо пространство процесса отлаживаемой программы.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)