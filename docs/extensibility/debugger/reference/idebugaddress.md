---
title: "IDebugAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAddress"
helpviewer_keywords: 
  - "Интерфейс IDebugAddress"
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет адрес элемента.  Он возвращается обработчиком символов.  
  
## Синтаксис  
  
```  
IDebugAddress : IUnknown  
```  
  
## Примечания по реализации  
 Поставщик символов реализующий этот интерфейс, чтобы представлять адрес объекта.  
  
## Замечания для вызывающих объектов  
 Многие методы на множество интерфейсов возвращают этот интерфейс.  
  
## Методы в том порядке Vtable  
 Этот интерфейс реализован следующий метод:  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|Извлекает a [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) структура, описывающая объект и его расположение.|  
  
## Заметки  
 Поставщик символов возвращает этот интерфейс для представления объекта и его расположение в указанной области \(например, функция, метод или класс\).  Этот интерфейс возвращается из и передается другим методам поставщика и средства оценки выражений символов.  Обычно поставщик символов единственная сущность, которую требуется интерпретировать содержимое этого интерфейса.  
  
## Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)