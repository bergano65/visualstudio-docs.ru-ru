---
title: "IDebugPointerObject::Dereference | Microsoft Docs"
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
  - "IDebugPointerObject::Dereference"
helpviewer_keywords: 
  - "Метод IDebugPointerObject::Dereference"
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPointerObject::Dereference
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает объект указанно.  
  
## Синтаксис  
  
```cpp#  
HRESULT DeReference(   
   DWORD          dwIndex,  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int Dereference(  
   uint             dwIndex,   
   out IDebugObject ppObject  
);  
```  
  
#### Параметры  
 `dwIndex`  
 \[in\] смещение a simple смещение от начала объекта указал значение.  
  
 `ppObject`  
 \[out\] возвращает IDebugObject объект, представляющий объект указал значение плюс отступ, если таковые имеются.  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK; в противном случае возвращает код ошибки.  Возвращает E\_FAIL, если этот объект не указывает на другой объект.  
  
## Заметки  
 Указанный объект может быть примитивом или более сложного типа в виде класса или структуры.  
  
## См. также  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)