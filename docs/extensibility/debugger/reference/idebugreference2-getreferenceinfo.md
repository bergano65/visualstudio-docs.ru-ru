---
title: "IDebugReference2::GetReferenceInfo | Microsoft Docs"
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
  - "IDebugReference2::GetReferenceInfo"
helpviewer_keywords: 
  - "IDebugReference2::GetReferenceInfo"
ms.assetid: ae611714-f114-4cf2-b5bb-37461e6ff289
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugReference2::GetReferenceInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) структура, которая содержит ссылку.  Зарезервировано для использования в будущем.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetReferenceInfo (   
   DEBUGREF_INFO_FLAGS   dwFields,  
   DWORD                 nRadix,  
   DWORD                 dwTimeout,  
   IDebugReference2**    rgpArgs,  
   DWORD                 dwArgCount,  
   DEBUG_REFERENCE_INFO* pReferenceInfo  
);  
```  
  
```c#  
int GetReferenceInfo (   
   enum_DEBUGREF_INFO_FLAGS  dwFields,  
   uint                      nRadix,  
   uint                      dwTimeout,  
   IDebugReference2[]        rgpArgs,  
   uint                      dwArgCount,  
   DEBUG_REFERENCE_INFO[]    pReferenceInfo  
);  
```  
  
#### Параметры  
 `dwFields`  
 \[in\] сочетание пометит из [DEBUGREF\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) перечисление, указывающее поля, которое нужно заполнять в  [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) структура.  
  
 `nRadix`  
 \[in\] корневой каталог, используемый в отформатировать любое числовое сведения.  
  
 `dwTimeout`  
 \[in\] максимальное время, в миллисекундах, ожидания возврата из этого метода.  Используйте `INFINITE` ждать бесконечно.  
  
 `rgpArgs`  
 \[in\] массив [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) объекты.  Зарезервировано для использования в будущем. установите в значение NULL.  
  
 `dwArgCount`  
 \[in\] число аргументов ссылки в `rgpArgs` массив.  Зарезервировано для использования в будущем. установите значение 0.  
  
 `pReferenceInfo`  
 \[out\] a [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) структура, заполняемую с описанием свойства.  
  
## Возвращаемое значение  
 Всегда возвращает значение `E_NOTIMPL`.  
  
## См. также  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)