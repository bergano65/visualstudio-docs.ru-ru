---
title: "IDebugEnumField::GetValueFromString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEnumField::GetValueFromString"
helpviewer_keywords: 
  - "Метод IDebugEnumField::GetValueFromString"
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugEnumField::GetValueFromString
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод возвращает значение, связанное с именем константы перечисления.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetValueFromString(  
   LPCOLESTR  pszValue,  
   ULONGLONG* pvalue  
);  
```  
  
```c#  
int GetValueFromString(  
   string    pszValue,  
   out ulong pValue  
);  
```  
  
#### Параметры  
 `pszValue`  
 \[in\] строка, указывающая имя для которого нужно получить значение.  Обратите внимание, что для C\+\+, это строка символов юникода.  
  
 `pValue`  
 \[out\] возвращает связанное числовое значение.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает  `S_FALSE`если имя не является частью перечисления или код ошибки.  
  
## Заметки  
 Данный метод не учитывает регистр.  Если поиск без учета регистра не требуется \(например, в языке Visual Basic в качестве где имена без учета регистра\), используйте [GetValueFromStringCaseInsensitive](../Topic/IDebugEnumField::GetValueFromStringCaseInsensitive.md).  
  
## См. также  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromStringCaseInsensitive](../Topic/IDebugEnumField::GetValueFromStringCaseInsensitive.md)