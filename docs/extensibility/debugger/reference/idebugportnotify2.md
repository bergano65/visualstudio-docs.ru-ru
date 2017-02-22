---
title: "IDebugPortNotify2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortNotify2"
helpviewer_keywords: 
  - "Интерфейс IDebugPortNotify2"
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortNotify2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс регистрирует и отменяет регистрацию программа, можно отлаживать с портом он запущен.  
  
## Синтаксис  
  
```  
IDebugPortNotify2 : IUnknown  
```  
  
## Примечания по реализации  
 Пользовательский поставщик порта, реализующий этот интерфейс, чтобы поддерживать добавление и удаление программ из порта.  Обычно реализуется для одного и того же объекта, реализующего IDebugPort2 интерфейс.  
  
## Замечания для вызывающих объектов  
 Вызов [QueryInterface](/visual-cpp/atl/queryinterface) на  `IDebugPort2` интерфейс возвращает этот интерфейс.  Кроме того, вызов [GetPortNotify](../Topic/IDebugDefaultPort2::GetPortNotify.md) возвращает данный интерфейс.  Отладчик может просмотреть этот интерфейс в качестве параметра [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugPortNotify2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Регистрирует программа, можно отлаживать с портом он запущен.|  
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Отменяет регистрацию программа, можно отлаживать от порта он запущен.|  
  
## Заметки  
 Если порт отладки не будет иметь способ знать при загрузке или выгрузке программы пользовательского поставщика порта должен реализовывать данный интерфейс.  Все программы, загруженных для отладки через заданный порт отслеживаются с помощью этого интерфейса.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)