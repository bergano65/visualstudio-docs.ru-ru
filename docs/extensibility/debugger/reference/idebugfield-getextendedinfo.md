---
title: "IDebugField::GetExtendedInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugField::GetExtendedInfo"
helpviewer_keywords: 
  - "Метод IDebugField::GetExtendedInfo"
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugField::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод возвращает подробные сведения о поле.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetExtendedInfo(   
   REFGUID guidExtendedInfo,  
   BYTE**  prgBuffer,  
   DWORD*  pdwLen  
);  
```  
  
```c#  
int GetExtendedInfo(  
   ref Guid guidExtendedInfo,   
   IntPtr[] prgBuffer,   
   ref uint pdwLen  
);  
```  
  
#### Параметры  
 `guidExtendedInfo`  
 \[in\] выбирает сведения, которые необходимо вернуть.  Допустимые значения:  
  
|Значение|Описание|  
|--------------|--------------|  
|`guidConstantValue`|Значение как последовательность байтов.|  
|`guidConstantType`|Тип как тип подписи.|  
  
 `prgBuffer`  
 \[out\] возвращает расширенные сведения.  
  
 `pdwLen`  
 \[in, out\] возвращает размер расширенного сведения в байтах.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 В настоящее время этот метод возвращает только тип или значение константы.  Вызывающий объект должен освободить буфер, возвращенный in `prgBuffer` с помощью модели COM  `CoTaskMemFree` функция or \(C\+\+\)  <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> \(C\#\).  
  
## См. также  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)