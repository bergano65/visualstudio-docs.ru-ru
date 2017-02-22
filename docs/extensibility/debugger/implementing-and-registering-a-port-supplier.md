---
title: "Реализация и регистрации поставщика порта | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "отладка [пакет SDK для отладки], регистрация поставщикам портов"
  - "поставщикам портов, регистрация"
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Реализация и регистрации поставщика порта
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Роль поставщика порта порты отслеживания и указывает, которые, в свою очередь, определяют процессы.  При необходимости создания порту, создается поставщик порта с помощью CoCreate с идентификатором GUID поставщика порта \(сеанс отладки диспетчер \[SDM\] будет использовать поставщика порта выделенного пользователя или поставщик порта, определенные системой проекта\).  SDM затем вызывает метод [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) определить, существуют ли порты могут быть добавлены.  Если порт можно добавить, новый запрос, вызвав порт [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) и передайте ему  [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) он описывает порт.  `AddPort` возвращает новый порт, представленный  [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) интерфейс.  
  
## Обсуждение  
 Порт, созданный поставщиком порта, который в свою очередь связаны с компьютером или отладки сервер.  Сервер может перечислять поставщиков портов через своих[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) метод и поставщик порта могут перечислить свои через порты  [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) метод.  
  
 В дополнение к обычной регистрации модели COM, поставщик порта должен зарегистрировать с помощью Visual Studio, поместив его CLSID и имя в конкретных расположениях реестра.  Вспомогательная функция, вызываемая пакет SDK для отладки `SetMetric` обрабатывает эту работу по дому: она вызывается один раз для каждого элемента, который требуется зарегистрировать. таким образом:  
  
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
  
 Отменяет регистрацию сами поставщика порта, вызвав `RemoveMetric` \(одна вспомогательная функция пакет SDK для отладки\) по одному разу для каждого элемента, который был зарегистрирован, таким образом:  
  
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
>  [Вспомогательные пакеты SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` и  `RemoveMetric` статические функции, определенные в dbgmetric.h и компилированные в ad2de.lib.  `metrictypePortSupplier`"  `metricCLSID`и`metricName` вспомогательные объекты также определяются в dbgmetric.h.  
  
 Поставщик порта может указать ее имя и идентификатор GUID через методы [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) и  [GetPortSupplierId](../Topic/IDebugPortSupplier2::GetPortSupplierId.md)соответственно.  
  
## См. также  
 [Реализация поставщика порта](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [Вспомогательные пакеты SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Поставщикам портов](../../extensibility/debugger/port-suppliers.md)