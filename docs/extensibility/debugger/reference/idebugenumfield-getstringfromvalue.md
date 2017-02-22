---
title: "IDebugEnumField::GetStringFromValue | Microsoft Docs"
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
  - "IDebugEnumField::GetStringFromValue"
helpviewer_keywords: 
  - "Метод IDebugEnumField::GetStringFromValue"
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEnumField::GetStringFromValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод возвращает имя константы перечисления заданным значением.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetStringFromValue(  
   ULONGLONG value,  
   BSTR*     pbstrValue  
);  
```  
  
```c#  
int GetStringFromValue(  
   ulong      value,  
   out string pbstrValue  
);  
```  
  
#### Параметры  
 `value`  
 \[in\] значение, для которого нужно получить имя константы перечисления.  
  
 `pbstrValue`  
 \[out\] возвращает имя константы перечисления.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает  `S_FALSE` если значение не имеет связанное имя или возвращает код ошибки.  
  
## Заметки  
 Если более чем одно имя, связанное с тем же значением, то возвращается имя, указанное в перечислении.  
  
## См. также  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)