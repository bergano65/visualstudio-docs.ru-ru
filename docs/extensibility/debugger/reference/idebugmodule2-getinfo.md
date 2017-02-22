---
title: "IDebugModule2::GetInfo | Microsoft Docs"
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
  - "IDebugModule2::GetInfo"
helpviewer_keywords: 
  - "Метод GetInfo"
  - "Метод IDebugModule2::GetInfo"
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugModule2::GetInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает сведения о данном модуле.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetInfo(   
   MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO*       pInfo  
);  
```  
  
```cpp#  
int GetInfo(   
   enum_MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO[]           pInfo  
);  
```  
  
#### Параметры  
 `dwFields`  
 \[in\] сочетание пометит из [MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) перечисление, указывающее которых полей  `pInfo` быть заполнянным.  
  
 `pInfo`  
 \[in, out\] a [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) структура, заполняемую с описанием модуля.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) структура содержит имя модуля, который отображается в  **Модули** окна.  
  
## См. также  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)