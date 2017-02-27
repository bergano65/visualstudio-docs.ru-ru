---
title: "IDebugProperty2::SetValueAsReference | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::SetValueAsReference"
helpviewer_keywords: 
  - "Метод IDebugProperty2::SetValueAsReference"
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProperty2::SetValueAsReference
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Устанавливает значение данного свойства в значение заданной ссылки.  
  
## Синтаксис  
  
```cpp#  
HRESULT SetValueAsReference(  
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```c#  
int SetValueAsReference(  
   IDebugReference2[] rgpArgs,  
   uint               dwArgCount,  
   IDebugReference2   pValue,  
   uint               dwTimeout  
);  
```  
  
#### Параметры  
 `rgpArgs`  
 \[in\] массив аргументов, передаваемых в сеттеру свойства управляемого кода.  Если задает значение свойства или если это не принимает аргументы [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) объект не ссылается на тот сеттеру свойства  `rgpArgs` должен иметь значение NULL.  Этот параметр обычно значение NULL.  
  
 `dwArgCount`  
 \[in\] количество аргументов в `rgpArgs` массив.  
  
 `pValue`  
 \[in\] ссылка в форме [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) объект, к значению для использования задать это свойство.  
  
 `dwTimeout`  
 \[in\] количество времени, выполняемое для задания значения в миллисекундах.  Типичное значение `INFINITE`.  Это влияет на продолжительность времени, любую допустимую вычисление может выполняться.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки, обычно одно из следующих действий:  
  
|Ошибка|Описание|  
|------------|--------------|  
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|Устанавливать значение из ссылки не поддерживается.|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Значение не может быть задано как это свойство относится к методу.|  
|`E_SETVALUE_VALUE_IS_READONLY`|Значение только для чтения и не может быть задано.|  
|`E_NOTIMPL`|Метод не реализован.|  
  
## См. также  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)