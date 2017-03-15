---
title: "IDebugExtendedField::GetExtendedKind | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugExtendedField::GetExtendedKind"
  - "GetExtendedKind"
ms.assetid: 20dc1c13-3cc0-4bb4-9c99-fa85587c86c3
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugExtendedField::GetExtendedKind
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Извлекает указанный расширенный тип поля.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetExtendedKind(  
   FIELD_KIND_EX* pdwKind  
);  
```  
  
```c#  
int GetExtendedKind(  
   ref enum_FIELD_KIND_EX pdwKind  
);  
```  
  
#### Параметры  
 `pdwKind`  
 \[in, out\] значение [FIELD\_KIND\_EX](../../../extensibility/debugger/reference/field-kind-ex.md) перечисление, определяющее тип поля.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)