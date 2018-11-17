---
title: IDebugPortSupplier2 | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d2e992061fa3486f179e3f498846e0f18b8c1598
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51785135"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс предоставляет порты, чтобы диспетчер отладки сеансов (SDM).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugPortSupplier2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Пользовательский порт поставщик реализует этот интерфейс для представления поставщика порта.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Вызов `CoCreateInstance` с поставщика порта `GUID` возвращает этот интерфейс (это типичный способ получения этого интерфейса). Пример:  
  
```cpp#  
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
  
 Вызов [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) возвращает этот интерфейс, представляющий текущий поставщик порта, используемый [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) возвращает этот интерфейс, представляющий поставщика порта, который создан порт.  
  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) представляет список `IDebugPortSupplier` интерфейсы ( `IEnumDebugPortSuppliers` интерфейс получается из [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md), представляющий всех поставщиков порт зарегистрировано [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]).  
  
 Модуль отладки обычно не взаимодействует с поставщика порта.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugPortSupplier2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Получает имя поставщика порта.|  
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|Возвращает идентификатор поставщика порта.|  
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Возвращает порт из поставщика порта.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Перечисляет порты, которые уже существуют.|  
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Проверяет, что поставщик порта поддерживает добавление новых портов.|  
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Добавляет порт.|  
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Удаляет порт.|  
  
## <a name="remarks"></a>Примечания  
 Поставщика порта можно идентифицировать себя имя и идентификатор, добавить и удалить порты и перечислить все порты, которые предоставляет поставщик порта.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)   
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)

