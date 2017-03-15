---
title: "IDebugDocumentContext2::Compare | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentContext2::Compare"
helpviewer_keywords: 
  - "IDebugDocumentContext2::Compare"
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentContext2::Compare
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Сравнивает этот контекст рисования в данный массив контекстов документа.  
  
## Синтаксис  
  
```cpp#  
HRESULT Compare(   
   DOCCONTEXT_COMPARE       compare,  
   IDebugDocumentContext2** rgpDocContextSet,  
   DWORD                    dwDocContextSetLen,  
   DWORD*                   pdwDocContext  
);  
```  
  
```c#  
int Compare(   
   enum_ DOCCONTEXT_COMPARE compare,  
   IDebugDocumentContext2[] rgpDocContextSet,  
   uint                     dwDocContextSetLen,  
   out uint                 pdwDocContext  
);  
```  
  
#### Параметры  
 `compare`  
 \[in\] значение из [DOCCONTEXT\_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) перечисление, которое указывает тип сравнения.  
  
 `rgpDocContextSet`  
 \[in\] массив IDebugDocumentContext2 объекты, которые представляют сравниваемые контексты документа.  
  
 `dwDocContextSetLen`  
 \[in\] длина массива контекстов документа для сравнения.  
  
 `pdwDocContext`  
 \[out\] возвращает индекс `rgpDocContextSet` массив первого контекста документа, удовлетворяющий сравнение.  
  
## Возвращаемое значение  
 Возвращает `S_OK` если соответствие найдено.  Возвращает `S_FALSE` если совпадение не найдено.  В противном случае возвращает код ошибки.  
  
## Заметки  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) объекты, которые передаются в массив необходимо передать один и тот же обработчик отладки, реализующий  `IDebugDocumentContext2` объект вызываемого on; в противном случае сравнение недопустимо.  
  
## См. также  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [DOCCONTEXT\_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)