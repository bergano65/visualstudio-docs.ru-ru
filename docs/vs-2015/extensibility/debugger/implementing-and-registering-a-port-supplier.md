---
title: Реализация и регистрация поставщика портов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 377aa88df71fd0d3c42745fe2d3ce3b648191aa4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843116"
---
# <a name="implementing-and-registering-a-port-supplier"></a>Реализация и регистрация поставщика порта
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Роль поставщика порта заключается в отслеживании и предоставлении портов, которые, в свою очередь, управляют процессами. На момент создания порта поставщик порта создается с помощью команды Create с идентификатором GUID поставщика порта (диспетчер отладки сеанса [SDM] будет использовать поставщика порта, выбранного пользователем, или поставщика порта, указанного в системе проекта). Затем SDM выполнит вызов [канаддпорт](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) , чтобы узнать, можно ли добавить какие либо порты. Если порт можно добавить, запрашивается новый порт путем вызова [аддпорт](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) и передачи ему [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) , описывающего порт. `AddPort` вернет новый порт, представленный интерфейсом [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) .  
  
## <a name="discussion"></a>Разговор  
 Порт создается поставщиком порта, который, в свою очередь, связан с компьютером или сервером отладки. Сервер может перечислить поставщиков портов с помощью метода[енумпортсупплиерс](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) , а поставщик порта может перечислить его порты с помощью метода [енумпортс](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) .  
  
 Помимо обычной регистрации COM, поставщик порта должен зарегистрироваться в Visual Studio, поместив его CLSID и имя в определенные расположения реестра. Вспомогательная функция SDK отладки с именем `SetMetric` обрабатывает эту работу: она вызывается один раз для каждого регистрируемого элемента, таким образом:  
  
```cpp#  
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
  
 Поставщик портов отменяет регистрацию самостоятельно путем вызова `RemoveMetric` (другой вспомогательной функции SDK отладки) для каждого зарегистрированного элемента, таким образом:  
  
```cpp#  
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
> [Вспомогательные функции SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` и `RemoveMetric` являются статическими функциями, определенными в дбгметрик. h и скомпилированными в ad2de. lib. `metrictypePortSupplier` `metricCLSID` Вспомогательные методы, и `metricName` также определяются в дбгметрик. h.  
  
 Поставщик порта может предоставить свое имя и идентификатор GUID с помощью методов [жетпортсупплиернаме](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) и [жетпортсупплиерид](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)соответственно.  
  
## <a name="see-also"></a>См. также:  
 [Реализация поставщика порта](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [Вспомогательные методы SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Поставщики портов](../../extensibility/debugger/port-suppliers.md)
