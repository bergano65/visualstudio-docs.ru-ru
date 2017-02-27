---
title: "IDebugObject2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject2"
helpviewer_keywords: 
  - "Интерфейс IDebugObject2"
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IDebugObject2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Этот интерфейс предоставляет дополнительные сведения об объекте.  
  
## Синтаксис  
  
```  
IDebugObject2 : IDebugObject  
```  
  
## Примечания для разработчиков  
 Средство оценки выражений реализует этот интерфейс предлагает поддержку псевдонимы и доступ к информации об объекте.  
  
## Примечания для вызывающих объектов  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Интерфейса можно получить этот интерфейс, используя [QueryInterface](/visual-cpp/atl/queryinterface). Кроме того [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) возвращает этот интерфейс.  
  
## Методы в порядке таблицы Vtable  
 В дополнение к методам на [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) интерфейс, `IDebugObject2` интерфейс реализует следующие:  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|Возвращает поля или переменной \(если таковые имеются\), может Резервное свойство, представленное этим объектом.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|Возвращает объект управляемого кода, который представляет значение этого объекта.|  
|[CreateAlias](../Topic/IDebugObject2::CreateAlias.md)|Создает уникальный идентификатор для данного объекта или возвращает существующего псевдонима.|  
|[GetAlias](../Topic/IDebugObject2::GetAlias.md)|При наличии получает псевдоним, связанные с данным объектом.|  
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|Возвращает тип этого объекта.|  
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|Определяет, представляет ли этот объект данных пользователя.|  
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|Определяет ли изменить и продолжить состояние больше не действительна.<br /><br /> Пользовательских выражений не реализует этот метод \(всегда должны возвращать `E_NOTIMPL`\).|  
  
## Заметки  
 В разделе [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) Обсуждение псевдонимы.  
  
## Требования  
 Заголовок: ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Интерфейсы вычисление выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)