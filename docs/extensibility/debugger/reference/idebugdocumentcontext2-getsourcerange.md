---
title: "IDebugDocumentContext2::GetSourceRange | Microsoft Docs"
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
  - "IDebugDocumentContext2::GetSourceRange"
helpviewer_keywords: 
  - "IDebugDocumentContext2::GetSourceRange"
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentContext2::GetSourceRange
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Получает диапазон исходного кода этого контекста документа.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetSourceRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```c#  
int GetSourceRange(   
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
 Диапазон источника все диапазон исходного кода из текущей выписки обратно на сразу после предыдущей выписке, способствовала код.  Диапазон источника, как правило, используется для выписок смешивание источника, включая комментарии с кодом в окне дизассемблированный код.  
  
 Чтобы получить диапазон только для выписок кода, содержащихся в данном контексте документа, вызовите [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) метод.  
  
## См. также  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)