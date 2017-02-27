---
title: "IDebugProgramEx2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramEx2"
helpviewer_keywords: 
  - "Интерфейс IDebugProgramEx2"
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# IDebugProgramEx2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс позволяет сеансу отладки \(SDM\) диспетчер вложение в программе и возвращает узел программы, связанные с приложениями.  
  
## Синтаксис  
  
```  
IDebugProgramEx2 : IUnknown  
```  
  
## Примечания по реализации  
 Пользовательский поставщик порта реализует этот интерфейс на одном объекте как IDebugProgram2 интерфейс разрешить SDM вложить в программе обеспечивая в то же время позволяя поставщик порта для отслеживания всех сеансов вложить в программе.  Пользовательский поставщик порта может реализовать этот интерфейс, если он выбирает.  
  
## Замечания для вызывающих объектов  
 Вызовы SDM [QueryInterface](/visual-cpp/atl/queryinterface) на  `IDebugProgram2` интерфейс для получения этот интерфейс, чтобы отслеживать сеансы, вложили программы.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugProgramEx2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Вложение программа к сеансу.|  
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Получает узел программы, связанные с приложениями.|  
  
## Заметки  
 Этот интерфейс является частным между SDM и приложениями.  
  
## Требования  
 Заголовок: Portpriv.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)