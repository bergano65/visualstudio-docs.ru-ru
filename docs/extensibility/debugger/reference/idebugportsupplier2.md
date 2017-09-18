---
title: "IDebugPortSupplier2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier2"
helpviewer_keywords: 
  - "Интерфейс IDebugPortSupplier2"
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugPortSupplier2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Порты предоставляют этого интерфейса к сеансу диспетчер отладки \(SDM\).  
  
## Синтаксис  
  
```  
IDebugPortSupplier2 : IUnknown  
```  
  
## Примечания по реализации  
 Пользовательский поставщик порта, реализующий этот интерфейс, чтобы представить поставщика порта.  
  
## Замечания для вызывающих объектов  
 Вызов `CoCreateInstance` с помощью поставщика порта  `GUID` возвращает этот интерфейс \(это типичный способ получить этот интерфейс\).  Примеры.  
  
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
  
 Вызов [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) возвращает этот интерфейс, представляющий текущего поставщика порта, используемого by  [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].  
  
 [GetPortSupplier](../Topic/IDebugPort2::GetPortSupplier.md) возвращает этот интерфейс, представляющий поставщика порта, который создал порт.  
  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) представляет список  `IDebugPortSupplier` интерфейсы \(  `IEnumDebugPortSuppliers` интерфейс получен из  [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md), представляющий всех зарегистрированных поставщиков портов с  [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]\).  
  
 Отладчик не взаимодействует с поставщиком порта.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugPortSupplier2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Получает имя поставщика порта.|  
|[GetPortSupplierId](../Topic/IDebugPortSupplier2::GetPortSupplierId.md)|Получает идентификатор поставщика порта.|  
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Получает порт от поставщика порта.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Перечисляет порты, которые уже существуют.|  
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Проверяет, что поставщик порта поддерживает добавление новых порты.|  
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Добавить порт.|  
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Удаляет порт.|  
  
## Заметки  
 Поставщик порта может определить именем и идентификатором, добавлять и удалять порты и перечислить все порты, которые поставщик порта.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPortSupplier](../Topic/IDebugPort2::GetPortSupplier.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)   
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)