---
title: "IDebugDocumentPosition2::GetRange | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentPosition2::GetRange"
helpviewer_keywords: 
  - "IDebugDocumentPosition2::GetRange"
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentPosition2::GetRange
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Получает диапазон для этой части документа.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```c#  
int GetRange(   
   TEXT_POSITION[] pBegPosition,  
   TEXT_POSITION[] pEndPosition  
);  
```  
  
#### Параметры  
 `pBegPosition`  
 \[in, out\] a [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) структура, заполняемую с начальной позицией.  Установите этот аргумент значение NULL, если эти данные не требуются.  
  
 `pEndPosition`  
 \[in, out\] a [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) структура, заполняемую с положением окончания.  Установите этот аргумент значение NULL, если эти данные не требуются.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Диапазон, указанное в позиции документа для точки останова расположения используется обработчиком отладки \(DE\) для поиска вперед для выписки, фактически предоставляет код.  Рассмотрим следующий пример кода:  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 Линия 5 не вносит никакой код отлаживаемой программы.  Если отладчик, который задает точку останова на линии 5 хочет DE поиск передне определённое число для первой линии, которая предоставляет код ", отладчик определит диапазон, который содержит дополнительные линии выбранного, где может быть размещена точка останова надлежащим образом.  DE затем искал бы передняя сквозную те линии до тех пор, пока он не оснует линию, которая может принять точку останова.  
  
## См. также  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)