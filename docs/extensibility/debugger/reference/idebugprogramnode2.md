---
title: "IDebugProgramNode2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNode2"
helpviewer_keywords: 
  - "Интерфейс IDebugProgramNode2"
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramNode2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет программу, которая может быть отладки.  
  
## Синтаксис  
  
```  
IDebugProgramNode2 : IUnknown  
```  
  
## Примечания по реализации  
 Отладчик \(DE\) или пользовательского поставщика порта, реализующие этот интерфейс, чтобы представить программу, которая может быть отладки.  Этот интерфейс обычно реализуется для одного и того же объекта, реализующего IDebugProgram2 интерфейс.  Зарегистрирован этот интерфейс с [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] путем вызова  [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).  
  
## Замечания для вызывающих объектов  
 Вызов [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) возвратить этот интерфейс.  Пользовательский поставщик порта получает этот интерфейс через вызов [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md).  DE получает этот интерфейс через вызов [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugProgramNode2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|Возвращает имя программы.|  
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|Возвращает имя процесса размещения программы.|  
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|Возвращает идентификатор системного процесса для процесса размещения программы.|  
|[GetHostMachineName\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|НЕРЕКОМЕНДУЕМЫЙ.  НЕ ИСПОЛЬЗУЙТЕ.|  
|[Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|НЕРЕКОМЕНДУЕМЫЙ.  НЕ ИСПОЛЬЗУЙТЕ.  См. [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) интерфейс для альтернативного подхода.|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|Возвращает имя и идентификатор DE хода этой программы.|  
|[DetachDebugger\_V7](../Topic/IDebugProgramNode2::DetachDebugger_V7.md)|НЕРЕКОМЕНДУЕМЫЙ.  НЕ ИСПОЛЬЗУЙТЕ.|  
  
## Заметки  
 Сеанс отладки вызовы диспетчера \(SDM\) обычно [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) получить этот интерфейс.  
  
## Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)   
 [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)   
 [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)