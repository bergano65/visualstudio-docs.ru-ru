---
title: "IDebugThread2::EnumFrameInfo | Microsoft Docs"
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
  - "IDebugThread2::EnumFrameInfo"
helpviewer_keywords: 
  - "IDebugThread2::EnumFrameInfo"
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugThread2::EnumFrameInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Извлекает список кадров стека для данного потока.  
  
## Синтаксис  
  
```cpp#  
HRESULT EnumFrameInfo (   
   FRAMEINFO_FLAGS        dwFieldSpec,  
   UINT                   nRadix,  
   IEnumDebugFrameInfo2** ppEnum  
);  
```  
  
```c#  
int EnumFrameInfo (   
   enum_FRAMEINFO_FLAGS     dwFieldSpec,  
   uint                     nRadix,  
   out IEnumDebugFrameInfo2 ppEnum  
);  
```  
  
#### Параметры  
 `dwFieldSpec`  
 \[in\] сочетание пометит из [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) перечисление, которое определяет, какие поля  [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структуры быть заполнянным.  Определение `FIF_FUNCNAME_FORMAT` пометить для форматирования имя функции в одну строку.  
  
 `nRadix`  
 \[in\] корневой каталог, используемый в форматировать числовое сведения в перечислителе.  
  
 `ppEnum`  
 \[out\] возвращает [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) объект, содержащий список  [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структура, описывающая кадр стека.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Кадров потока перечисляются в том порядке, в котором текущий кадр, указанные в первую очередь, а самый старый кадр, представленный последним.  
  
## См. также  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)