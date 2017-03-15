---
title: "IDebugMethodField::EnumArguments | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::EnumArguments"
helpviewer_keywords: 
  - "Метод IDebugMethodField::EnumArguments"
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugMethodField::EnumArguments
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Создает перечислитель для каждого необходимого типа аргумента, чтобы вызвать метод.  
  
## Синтаксис  
  
```cpp#  
HRESULT EnumArguments(   
   IEnumDebugFields** ppParams  
);  
```  
  
```c#  
int EnumArguments(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### Параметры  
 `ppParams`  
 \[out\] возвращает [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) объект, представляющий список типов аргументов.  Возвращает значение NULL при отсутствии аргументов.  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK и возвращает значение S\_FALSE, если аргументов.  В противном случае возвращает код ошибки.  
  
## Заметки  
 Каждый элемент IDebugField объект, представляющий типы каждого параметра.  Вызовите [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) метод для извлечения сведений о типе каждого параметра.  
  
 Если имя параметра, должны быть одновременно с типом, вызовите [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) метод.  
  
## См. также  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)