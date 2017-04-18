---
title: "IEnumDebugPrograms2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
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
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: af46d12f546c2b8e53510ca1b3cd28b634909ea7
ms.lasthandoff: 04/05/2017

---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
Этот интерфейс перечисляет программы, запущенные в текущем сеансе отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumDebugPrograms2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для предоставления списка по DE отлаживаемых программ.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Visual Studio вызывает [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) для получения этого интерфейса. [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) не используется в Visual Studio.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IEnumDebugPrograms2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Далее](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Извлекает указанное число программ в последовательности перечисления.|  
|[Пропустить](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Пропускает указанное число программ в последовательности перечисления.|  
|[Сброс](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Сбрасывает последовательность перечисления в начало.|  
|[Клон](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Создает перечислитель, с тем же состоянием, как у текущего перечислителя.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Возвращает количество программ в перечислителе.|  
  
## <a name="remarks"></a>Примечания  
 Visual Studio использует этот интерфейс для:  
  
-   Заполнение **модули** окна (путем вызова [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) и последующего вызова [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) на каждой программы).  
  
-   Заполнение **присоединиться к процессу** список (путем вызова `IDebugProcess2::EnumPrograms` и последующего вызова [QueryInterface](/cpp/atl/queryinterface) на каждом [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) интерфейс для получения [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) интерфейс).  
  
-   Создать список DEs, можно отлаживать каждой программы в процессе (с помощью [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)).  
  
-   Применить обновления, изменить и продолжить (ENC) для каждой программы (путем вызова IDebugProcess2::EnumPrograms и последующего вызова [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)).  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)
