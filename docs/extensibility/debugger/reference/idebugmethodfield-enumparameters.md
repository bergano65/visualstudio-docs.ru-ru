---
title: "IDebugMethodField::EnumParameters | Microsoft Docs"
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
  - "IDebugMethodField::EnumParameters"
helpviewer_keywords: 
  - "Метод IDebugMethodField::EnumParameters"
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMethodField::EnumParameters
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Создает перечислитель для параметров метода.  
  
## Синтаксис  
  
```cpp#  
HRESULT EnumParameters(   
   IEnumDebugFields** ppParams  
);  
```  
  
```c#  
int EnumParameters(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### Параметры  
 `ppParams`  
 \[out\] возвращает [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) объект, представляющий список параметров для метода. в противном случае возвращает значение NULL, если никаких параметров.  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK и возвращает значение S\_FALSE, если параметры.  В противном случае возвращает код ошибки.  
  
## Заметки  
 Каждый элемент IDebugField объект, представляющий различные типы параметров.  Вызовите [GetKind](../Topic/IDebugField::GetKind.md) метод на каждом объекте, чтобы точно задать, какие параметр представляет объект.  
  
 Параметр включает и его имя переменной и его тип.  Первый параметр метода класса, как правило, этот указатель "".  
  
 Если необходимы только типы параметров, вызовите [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) метод.  
  
## См. также  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)