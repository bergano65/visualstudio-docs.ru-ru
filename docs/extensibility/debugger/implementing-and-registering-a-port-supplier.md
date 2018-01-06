---
title: "Реализация и регистрации поставщика порта | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1c05dc0bd15dc5c1959024327396d848cd0b1112
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-and-registering-a-port-supplier"></a>Реализация и регистрации поставщика порта
Для отслеживания и указать порты, которые в свою очередь, управление процессами — роль поставщика порта. Во время порта должно быть создано поставщика порта создается с помощью CoCreate с идентификатором GUID поставщика порта (Диспетчер сеанса отладки [SDM] будет использовать поставщика порта выбранный пользователем или поставщика порта, указанный в системе проекта). Затем вызовет SDM [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) для просмотра, могут быть добавлены все порты. Если порт может быть добавлен, путем вызова запрашивается новый порт [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) и передачи его [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) , описывающий порт. `AddPort`Возвращает новый порт, представленный [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) интерфейса.  
  
## <a name="discussion"></a>Обсуждение  
 Порт, созданных поставщика порта, который в свою очередь связан с сервером машины или отладки. Сервер можно перечислить ее поставщики порт через[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) метод и поставщика порта можно перечислить его портам с помощью [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) метод.  
  
 Помимо обычной регистрации COM поставщика порта должен зарегистрироваться с помощью Visual Studio, поместив его имя и идентификатор CLSID в определенные разделы реестра. Пакет SDK для отладки вспомогательная функция, вызываемая `SetMetric` обрабатывает переложить всю работу: вызывается один раз для каждого элемента, чтобы зарегистрировать, таким образом:  
  
```cpp  
SetMetric(metrictypePortSupplier,  
          <GUID of your port supplier>,  
          metricCLSID,  
          <CLSID of your port supplier>,  
          false,  
          NULL)  
SetMetric(metrictypePortSupplier,  
          <GUID of your port supplier>,  
          metricName,  
          <name of your port supplier>,  
          false,  
          NULL);  
```  
  
 Поставщика порта отменяет регистрацию сам путем вызова `RemoveMetric` (Вспомогательная функция другой пакет SDK для отладки) один раз для каждого элемента, который был зарегистрирован, таким образом:  
  
```cpp  
RemoveMetric(metrictypePortSupplier,  
             <GUID of your port supplier>,  
             metricCLSID,  
             NULL);  
RemoveMetric(metrictypePortSupplier,  
             <GUID of your port supplier>,  
             metricName,  
             NULL);  
```  
  
> [!NOTE]
>  [SDK вспомогательные методы для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` и `RemoveMetric` — это статические функции, определенные в dbgmetric.h и компилируются в ad2de.lib. `metrictypePortSupplier`, `metricCLSID`, И `metricName` помощников также определены в dbgmetric.h.  
  
 Порт поставщика можно указать его имя и идентификатор GUID в методах [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) и [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)соответственно.  
  
## <a name="see-also"></a>См. также  
 [Реализация поставщика порта](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [Вспомогательные функции пакета SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Поставщики портов](../../extensibility/debugger/port-suppliers.md)