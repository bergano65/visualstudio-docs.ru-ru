---
title: "IDebugWindowsComputerPort2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Интерфейс IDebugWindowsComputerPort2"
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugWindowsComputerPort2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Разрешает при запросе информации о конечном компьютере.  
  
## Синтаксис  
  
```  
IDebugWindowsComputerPort2 : IUnknown  
```  
  
## Примечания по реализации  
 Этот интерфейс реализуется объектами порта сеанса отладки диспетчер.  
  
## Методы  
 В следующей таблице показаны методы `IDebugWindowsComputerPort2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|Извлекает сведения о компьютере, на котором отладчик находится в запущенном.|  
  
## Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll