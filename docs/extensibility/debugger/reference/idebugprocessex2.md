---
title: "IDebugProcessEx2 | Microsoft Docs"
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
  - "IDebugProcessEx2"
helpviewer_keywords: 
  - "Интерфейс IDebugProcessEx2"
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcessEx2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс позволяет сеансу отладки \(SDM\) уведомляет диспетчер процесс, что вложение или finally удаляет из процесса.  
  
## Синтаксис  
  
```  
IDebugProcessEx2 : IUnknown  
```  
  
## Примечания по реализации  
 Пользовательский поставщик порта реализует этот интерфейс на одном объекте как IDebugProcess2 интерфейс:  
  
-   Отслеживание поддержки сеансов, подключенных к процессу  
  
-   Поддержка автоматическ\-вложит через несколько обработчиков отладки  
  
 Пользовательский поставщик порта может реализовать этот интерфейс, если он выбирает.  
  
## Замечания для вызывающих объектов  
  
-   Вызовы SDM [QueryInterface](/visual-cpp/atl/queryinterface) на  `IDebugProcess2` интерфейс для получения этого интерфейса.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugProcessEx2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Attach](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Сообщает, что сеанс отладки процесса теперь процесс.|  
|[Detach](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Информирует процесс, что сеанс не процесс отладки.|  
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Добавляет список обработчиков узлы программы отладки.|  
  
## Заметки  
 Этот интерфейс является частным между SDM и процессом.  
  
## Требования  
 Заголовок: Portpriv.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)