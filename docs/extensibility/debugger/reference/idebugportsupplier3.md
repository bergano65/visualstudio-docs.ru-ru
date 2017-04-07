---
title: "IDebugPortSupplier3 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
caps.latest.revision: 8
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
ms.openlocfilehash: 0eb7cf542fa61d53220cd10f54e3fbd7c6165bf4
ms.lasthandoff: 04/05/2017

---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
Этот интерфейс позволяет вызывающему объекту для определения поставщика порта, чтобы защитить порты (их записи на диск) между вызовами отладчика и затем получить список сохраненных порты.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugPortSupplier3 : IDebugPortSupplier2  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Пользовательский порт поставщика реализует этот интерфейс поддерживает сохранение или сохранить сведения о порте на диск. Этот интерфейс должен быть реализован на один и тот же объект как [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) интерфейса.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызовите [QueryInterface](/cpp/atl/queryinterface) на `IDebugPortSupplier2` интерфейс для получения этого интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 Помимо методов, наследуемых от [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) интерфейс, этот интерфейс поддерживает следующие:  
  
|Метод|Описание|  
|------------|-----------------|  
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Возвращает, может ли поставщика порта сохранять портов (по их записи на диск) между вызовами отладчика.|  
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Возвращает объект, который может использоваться для перечисления через все порты, которые были записаны на диск поставщика этого порта.|  
  
## <a name="remarks"></a>Примечания  
 Если поставщика порта может быть сохранено порты между вызовами, он должен реализовывать этот интерфейс. Порты должны быть загружены при создании экземпляра поставщика порта, а записываются на диск при уничтожении поставщика порта.  
  
 Модуль отладки обычно не взаимодействуют с поставщика порта и не понадобится для этого интерфейса.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
