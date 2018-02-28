---
title: "IEnumDebugModules2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: c87b22de02324544bbf1ea0919254535f6cc2702
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
Этот интерфейс перечисляет список модулей.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumDebugModules2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для представления списка модулей, загруженных для программы.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Visual Studio вызывает [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) для получения этого интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IEnumDebugModules2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[Вперед](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Извлекает указанное число модулей в последовательности перечисления.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Пропускает указанное число модулей в последовательности перечисления.|  
|[Сброс](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Сбрасывает последовательность перечисления в начало.|  
|[Клон](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Создает перечислитель, с тем же состоянием, как у текущего перечислителя.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Возвращает число модулей.|  
  
## <a name="remarks"></a>Примечания  
 Visual Studio использует этот интерфейс в первую очередь, чтобы обновить **модули** окна.  
  
 В целях отладки в Visual Studio программа находится в логической последовательности инструкций кода, может выходить за границы модуля, поэтому необходимость список модулей одного и того же [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) интерфейса. Первый модуль в списке обычно содержит точку начальную запись для соответствующую программу.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)