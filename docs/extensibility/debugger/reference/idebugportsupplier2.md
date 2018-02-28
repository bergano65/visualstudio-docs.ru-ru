---
title: "IDebugPortSupplier2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 257bbf334adbdfd3a93cf172de0b15bf63cb3217
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
Этот интерфейс предоставляет порты для диспетчера сеанса отладки (SDM).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugPortSupplier2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Поставщик пользовательский порт реализует этот интерфейс для представления поставщика порта.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызов `CoCreateInstance` с поставщика порта `GUID` возвращает этот интерфейс (это типичный способ получить этот интерфейс). Пример:  
  
```cpp  
IDebugPortSupplier2 *GetPortSupplier(GUID *pPortSupplierGuid)  
{  
    IDebugPortSupplier2 *pPS = NULL;  
    if (pPortSupplierGuid != NULL) {  
        CComPtr<IDebugPortSupplier2> spPortSupplier;  
        spPortSupplier.CoCreateInstance(*pPortSupplierGuid);  
        if (spPortSupplier != NULL) {  
            pPS = spPortSupplier.Detach();  
        }  
    }  
    return (pPS);  
}  
```  
  
 Вызов [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) возвращает этот интерфейс, представляющий текущего поставщика порта, используемого [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].  
  
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) возвращает этот интерфейс, представляющий поставщика порта, который создан порт.  
  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) представляет список `IDebugPortSupplier` интерфейсы ( `IEnumDebugPortSuppliers` интерфейса берется из [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md), представляющий всех поставщиков порт зарегистрирована [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]).  
  
 Модуль отладки обычно не взаимодействует с поставщика порта.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugPortSupplier2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Получает имя поставщика порта.|  
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|Возвращает идентификатор поставщика порта.|  
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Возвращает порт из поставщика порта.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Перечисляет порты, которые уже существуют.|  
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Проверяет, что поставщика порта поддерживает добавление новых портов.|  
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Добавление порта.|  
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Удаляет порт.|  
  
## <a name="remarks"></a>Примечания  
 Поставщика порта могут идентифицироваться по имени и идентификатора, добавить и удалить порты и перечислить все порты, которые предоставляет поставщика порта.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)   
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)