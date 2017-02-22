---
title: "IDebugBinder3 | Microsoft Docs"
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
  - "IDebugBinder3"
helpviewer_keywords: 
  - "Интерфейс IDebugBinder3"
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBinder3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Этот интерфейс обеспечивает доступ к типам, псевдонимы и пользовательский визуализатор служб.  
  
## Синтаксис  
  
```  
IDebugBinder3 : IDebugBinder  
```  
  
## Примечания для разработчиков  
 Подсистема отладки реализует этот интерфейс для поддержки псевдонимы, пользовательский визуализатор служб и доступа к информации о типе объекта.  
  
## Примечания для вызывающих объектов  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) Интерфейс получает этот интерфейс, с помощью [QueryInterface](/visual-cpp/atl/queryinterface).  
  
## Методы в порядке таблицы Vtable  
 Помимо методов, предоставляемых [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) интерфейс, этот интерфейс реализует следующие:  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|Извлекает объект памяти, представляющий памяти, с которым связан этот объект.|  
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|Получает исключение, связанное с объектом \(если есть\)|  
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|Возвращает псевдоним с заданным именем|  
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|Извлекает массив все псевдонимы для этого объекта|  
|[GetTypeArgumentCount](../Topic/IDebugBinder3::GetTypeArgumentCount.md)|Возвращает количество типов аргументов, связанных с этим объектом|  
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|Получает список типов аргументов, связанных с этим объектом|  
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|Возвращает интерфейс для службы визуализатора|  
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|Преобразует расположение объекта или адрес памяти 64\-разрядных контекст памяти.|  
  
## Требования  
 Заголовок: ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Интерфейсы вычисление выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)