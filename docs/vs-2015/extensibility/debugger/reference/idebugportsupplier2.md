---
title: IDebugPortSupplier2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b6d9c3f8b45affd192d4109db08454345dcd0814
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188222"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс предоставляет порты диспетчеру отладки сеансов (SDM).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugPortSupplier2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Пользовательский поставщик портов реализует этот интерфейс для представления поставщика порта.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызов `CoCreateInstance` с помощью поставщика порта `GUID` возвращает этот интерфейс (это типичный способ получения этого интерфейса). Пример:  
  
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
  
 Вызов [жетпортсупплиер](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) возвращает этот интерфейс, представляющий текущего поставщика портов, используемого [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] .  
  
 [Жетпортсупплиер](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) возвращает этот интерфейс, представляющий поставщика порта, который создал порт.  
  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) представляет список `IDebugPortSupplier` интерфейсов ( `IEnumDebugPortSuppliers` интерфейс получен от [енумпортсупплиерс](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md), представляющий всех поставщиков портов, зарегистрированных в [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ).  
  
 Модуль отладки обычно не взаимодействует с поставщиком порта.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugPortSupplier2` .  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Возвращает имя поставщика порта.|  
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|Возвращает идентификатор поставщика порта.|  
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Возвращает порт от поставщика порта.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Перечисляет уже существующие порты.|  
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Проверяет, поддерживает ли поставщик портов Добавление новых портов.|  
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Добавляет порт.|  
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Удаляет порт.|  
  
## <a name="remarks"></a>Remarks  
 Поставщик порта может идентифицировать себя по имени и ИДЕНТИФИКАТОРу, добавлять и удалять порты, а также перечислять все порты, предоставляемые поставщиком портов.  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)   
 [жетпортсупплиер](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)   
 [жетпортсупплиер](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)   
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
