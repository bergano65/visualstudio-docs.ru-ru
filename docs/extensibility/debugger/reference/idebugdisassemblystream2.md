---
title: "IDebugDisassemblyStream2 | Microsoft Docs"
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
  - "IDebugDisassemblyStream2"
helpviewer_keywords: 
  - "Интерфейс IDebugDisassemblyStream2"
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDisassemblyStream2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет поток инструкций.  
  
## Синтаксис  
  
```  
IDebugDisassemblyStream2 : IUnknown  
```  
  
## Примечания по реализации  
 Отладчик реализующий этот интерфейс, чтобы поддерживать разборку кода программы.  
  
## Замечания для вызывающих объектов  
 Вызов [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) этот метод возвращает интерфейс.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugDisassemblyStream2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Чтение](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|Считывает инструкцию, начиная с текущей позицией курсора в потоке дизассемблированный код.|  
|[Поиск](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|Перемещает указатель чтения в потоке дизассемблирования заданное число инструкций по отношению к указанной позиции.|  
|[GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md)|Возвращает идентификатор расположение кода для заданного контекста.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|Возвращает объект контекста кода, соответствующее указанному идентификатору расположение кода.|  
|[GetCurrentLocation](../Topic/IDebugDisassemblyStream2::GetCurrentLocation.md)|Возвращает идентификатор расположение кода, который представляет текущее расположение кода.|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|Получает исходный документ, связанный с данным потоком дизассемблированный код.|  
|[GetScope](../Topic/IDebugDisassemblyStream2::GetScope.md)|Получает область данного потока дизассемблированный код.|  
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|Возвращает размер данного потока дизассемблированный код.|  
  
## Заметки  
 Поток дизассемблированный код может быть создан для представления всех адресным пространством или просто функцию или модуль внутри пробел.  Каждая инструкция представлена a [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) структура, возвращаемую вызовом  [Чтение](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) метод.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)