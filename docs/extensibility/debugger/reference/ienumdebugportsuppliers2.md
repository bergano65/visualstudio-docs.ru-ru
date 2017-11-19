---
title: "IEnumDebugPortSuppliers2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugPortSuppliers2
helpviewer_keywords: IEnumDebugPortSuppliers2
ms.assetid: cd0a73dc-dd25-46fd-8c4f-5b011501afeb
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 55481d339d9aad5e668ebdf5e3715af18768ed01
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugportsuppliers2"></a>IEnumDebugPortSuppliers2
Этот интерфейс перечисляет поставщикам портов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumDebugPortSuppliers2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Visual Studio реализует этот интерфейс для представления списка поставщиков порта.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызовите [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) для получения списка поставщиков порта.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IEnumDebugPortSuppliers2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Вперед](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-next.md)|Извлекает указанное число портов поставщиков из последовательности перечисления.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|Пропускает указанное число портов поставщиков из последовательности перечисления.|  
|[Сброс](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|Сбрасывает последовательность перечисления в начало.|  
|[Клон](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-clone.md)|Создает перечислитель, с тем же состоянием, как у текущего перечислителя.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|Возвращает номер порта поставщиков в перечислителе.|  
  
## <a name="remarks"></a>Примечания  
 Модуль отладки обычно не нужно получить этот интерфейс.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)