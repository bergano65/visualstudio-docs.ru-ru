---
title: "IDebugPointerObject3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Интерфейс IDebugPointerObject3"
ms.assetid: 11d26af4-1079-435e-96fa-d5269cbea8eb
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPointerObject3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Представляет указатель в дерево синтаксического анализа и расширяет **IDebugPointerObject** интерфейса.  
  
## Синтаксис  
  
```  
IDebugPointerObject3 : IDebugPointerObject  
```  
  
## Примечания для разработчиков  
 Вычислитель выражений \(EE\) реализует этот интерфейс.  
  
## Методы  
 В дополнение к методам на [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) интерфейс, этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetPointerAddress](../../../extensibility/debugger/reference/idebugpointerobject3-getpointeraddress.md)|Извлекает адрес указателя.|  
  
## Требования  
 Заголовок: Ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll