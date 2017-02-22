---
title: "IDebugDefaultPort2 | Microsoft Docs"
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
  - "IDebugDefaultPort2"
helpviewer_keywords: 
  - "Интерфейс IDebugDefaultPort2"
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDefaultPort2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс предоставляет несколько методов для доступа к возможности сервера и уведомления порта.  
  
## Синтаксис  
  
```  
IDebugDefaultPort2 : IDebugPort2  
```  
  
## Примечания по реализации  
 Visual Studio реализующий этот интерфейс, чтобы представить порт отладки для доступа к программы.  Пользовательский поставщик порта может также реализовать этот интерфейс, если он обрабатывает удаленную отладку.  
  
## Замечания для вызывающих объектов  
 Аргумент к методам на [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) этот интерфейс предоставляет интерфейса.  Вызов [QueryInterface](/visual-cpp/atl/queryinterface) на  [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) интерфейс также может получить этот интерфейс.  
  
## Методы в том порядке Vtable  
 В дополнение к методам, указанным в пределах IDebugPort2этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetPortNotify](../Topic/IDebugDefaultPort2::GetPortNotify.md)|Получает интерфейс уведомления порта от этого порта.|  
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Получает интерфейс на сервер при размещении этот порт.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Указывает, выполняется ли этот порт на локальном компьютере.|  
  
## Заметки  
 Имя "`IDebugDefaultPort2`bit misnomer ", так как он не представляет порт по умолчанию.  Он может быть вызван "IDebugPort3".  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)