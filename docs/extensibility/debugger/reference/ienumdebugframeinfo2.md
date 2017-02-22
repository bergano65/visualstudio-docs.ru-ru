---
title: "IEnumDebugFrameInfo2 | Microsoft Docs"
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
  - "IEnumDebugFrameInfo2"
helpviewer_keywords: 
  - "IEnumDebugFrameInfo2"
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugFrameInfo2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс перечисляет [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структуры.  
  
## Синтаксис  
  
```  
IEnumDebugFrameInfo2 : IUnknown  
```  
  
## Примечания по реализации  
 Отладчик \(DE\) реализует этот интерфейс, чтобы предоставить список структур, который описывает текущий стек вызова.  
  
## Замечания для вызывающих объектов  
 Вызовы Visual Studio [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) получить этот интерфейс, если точка останова, исключение или " остановка ", возникающих в отлаживанными программе.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IEnumDebugFrameInfo2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Далее](../Topic/IEnumDebugFrameInfo2::Next.md)|Получает заданное число [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структуры в последовательности перечисления.|  
|[Пропустить](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Пропустить заданное число [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структуры в последовательности перечисления.|  
|[Сбросить](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Сбросить последовательность перечисления в начало.|  
|[Клонировать](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|  
|[GetCount](../Topic/IEnumDebugFrameInfo2::GetCount.md)|Получает число [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структуры в перечислителе.|  
  
## Заметки  
 Visual Studio получает этот интерфейс в качестве первого шага обработки точку останова, исключение или пользователь\-произведенную на выполнение отлаживаемой программы.  Список  [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структуры представляют текущий стек вызовов с текущим вызовом функции в начале списка и более старым вызовом функции в конце списка.  Каждое `FRAMEINFO` представляет кадр стека, контекст, в котором выражения можно вычислять и локальные переменные поиска.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)