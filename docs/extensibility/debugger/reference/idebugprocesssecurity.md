---
title: "IDebugProcessSecurity | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Интерфейс IDebugProcessSecurity"
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugProcessSecurity
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

`IDebugProcessSecurity` реализует поставщика порта для оповещения пользователя о том, что вложение в процесс является небезопасным.  
  
## Синтаксис  
  
```  
IDebugProcessSecurity : IUnknown  
```  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugProcessSecurity`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Возвращает имя пользователя от поставщика порта.|  
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Предупреждать пользователь, вложение в процесс отладки является небезопасным.|  
  
## Заметки  
 Реализуйте этот интерфейс, чтобы отображать предупреждение и предоставление пользователю возможности отменить, если процесс, куда вложите можно считать небезопасным.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Порты](../../../extensibility/debugger/ports.md)   
 [Поставщикам портов](../../../extensibility/debugger/port-suppliers.md)   
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)