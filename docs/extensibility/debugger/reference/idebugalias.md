---
title: "IDebugAlias | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAlias"
helpviewer_keywords: 
  - "Интерфейс IDebugAlias"
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugAlias
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Представляет числовые псевдоним для переменной. Псевдоним является просто другое имя для переменной.  
  
## Синтаксис  
  
```  
IDebugAlias : IUnknown  
```  
  
## Примечания для разработчиков  
 Вычислитель выражений \(EE\) реализует этот интерфейс для поддержки псевдонимы числовых переменных.  
  
## Примечания для вызывающих объектов  
 [CreateAlias](../Topic/IDebugObject2::CreateAlias.md) создает псевдоним для определенного объекта. Чтобы найти псевдонимы, используйте [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) или [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md).  
  
## Методы в порядке таблицы Vtable  
 Следующие методы определяются в `IDebugAlias` интерфейса.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|Возвращает объект, к которому относится этот псевдоним.|  
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|Возвращает имя псевдонима.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|Извлекает `ICorDebugValue` интерфейс, обеспечивающий доступ для управляемого кода сведения об этом объекте \(только управляемый код\).|  
|[Метод Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|Помечает данный псевдоним как больше не используется.|  
  
## Заметки  
 Псевдоним — это десятичное число в виде строки, за которым следует символ \#, например, 1001\#.  
  
## Требования  
 Заголовок: ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Интерфейсы вычисление выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [CreateAlias](../Topic/IDebugObject2::CreateAlias.md)   
 [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)   
 [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)