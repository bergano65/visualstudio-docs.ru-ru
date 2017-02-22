---
title: "IEnumCodePaths2 | Microsoft Docs"
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
  - "IEnumCodePaths2"
helpviewer_keywords: 
  - "Интерфейс IEnumCodePaths2"
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumCodePaths2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет список путей кода.  
  
## Синтаксис  
  
```  
IEnumCodePaths2 : IUnknown  
```  
  
## Примечания по реализации  
 Отладчик \(DE\) реализует этот интерфейс, чтобы представлять список путей кода.  
  
## Замечания для вызывающих объектов  
 Вызов [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) получить этот интерфейс.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IEnumCodePaths2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Далее](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|Извлекает заданное количество путей кода в последовательности перечисления.|  
|[Пропустить](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|Пропустить указанное количество путей кода в последовательности перечисления.|  
|[Сбросить](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|Сбросить последовательность перечисления в начало.|  
|[Клонировать](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|  
|[GetCount](../Topic/IEnumCodePaths2::GetCount.md)|Возвращает количество путей кода в перечислителе.|  
  
## Заметки  
 Путь кода представляет точку разветвления или вызов функции в программе.  Список путей кода представляет путь, с помощью которого выполнение кода принимало.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)