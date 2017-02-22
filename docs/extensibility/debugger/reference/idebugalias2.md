---
title: "IDebugAlias2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Интерфейс IDebugAlias2"
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugAlias2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Представляет числовые псевдоним для переменной и позволяет вычислитель выражений \(EE\), чтобы получить домен приложения для псевдонима.  
  
## Синтаксис  
  
```  
IDebugAlias2 : IDebugAlias  
```  
  
## Примечания для разработчиков  
 Этот интерфейс реализуется Подсистема управляемой отладки \(DE\).  
  
## Методы  
 В дополнение к методам на [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) интерфейс, этот интерфейс реализует следующий метод:  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|Извлекает идентификатор для домена приложения.|  
  
## Заметки  
 Псевдоним — это десятичное число в виде строки, за которым следует символ \#, например, 1001\#.  
  
## Требования  
 Заголовок: Ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll