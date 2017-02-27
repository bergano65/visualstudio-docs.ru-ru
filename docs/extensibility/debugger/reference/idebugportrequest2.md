---
title: "IDebugPortRequest2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortRequest2"
helpviewer_keywords: 
  - "Интерфейс IDebugPortRequest2"
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugPortRequest2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс описывает порт.  Это описание используется, чтобы добавить порт для поставщика порта.  
  
## Синтаксис  
  
```  
IDebugPortRequest2 : IUnknown  
```  
  
## Примечания по реализации  
 Visual Studio обычно реализует этот интерфейс в процессе получения порт отладки от поставщика порта.  
  
## Замечания для вызывающих объектов  
 Этот интерфейс передается в [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) создание порт отладки.  Вызов [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) возвращает этот интерфейс, представляющий запрос, используемый для создания порт в первую очередь.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugPortRequest2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Возвращает имя порта создать.|  
  
## Заметки  
 Отладчик не взаимодействует с поставщиком порта и не будет содержать никаких использование этого интерфейса.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)   
 [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)