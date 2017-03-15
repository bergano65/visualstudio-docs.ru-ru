---
title: "IDebugPortPicker::DisplayPortPicker | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DisplayPortPicker"
  - "IDebugPortPicker::DisplayPortPicker"
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugPortPicker::DisplayPortPicker
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Отображает заданное диалоговое окно, которое позволяет пользователю выбрать порт.  
  
## Синтаксис  
  
```cpp#  
HRESULT DisplayPortPicker(  
   HWND hwndParentDialog,  
   BSTR* pbstrPortId  
);  
```  
  
```c#  
public int DisplayPortPicker(  
   int hwndParentDialog,  
   out string pbstrPortId  
);  
```  
  
#### Параметры  
 `hwndParentDialog`  
 \[in\] маркер для родительского диалогового окна.  
  
 `pbstrPortId`  
 \[out\] строка идентификатора порта.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  Возвращаемое значение  `S_FALSE` \(или возвращаемое значение   `S_OK` с  `BSTR` значение  `NULL`указывает, что пользователь щелкнул\)  **Отмена**.  
  
## См. также  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)