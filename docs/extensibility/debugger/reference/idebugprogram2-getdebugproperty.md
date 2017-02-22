---
title: "IDebugProgram2::GetDebugProperty | Microsoft Docs"
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
  - "IDebugProgram2::GetDebugProperty"
helpviewer_keywords: 
  - "IDebugProgram2::GetDebugProperty"
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::GetDebugProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает свойства программы.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetDebugProperty(   
   IDebugProperty2** ppProperty  
);  
```  
  
```c#  
int GetDebugProperty(   
   out IDebugProperty2 ppProperty  
);  
```  
  
#### Параметры  
 `ppProperty`  
 \[out\] возвращает IDebugProperty2 объект, представляющий свойства программы.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Свойства, возвращаемые этим методом, определенный в программе.  Если программе необходимо вернуть несколько свойство [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) объект, возвращаемый этим методом, контейнер дополнительных свойств и вызвать  [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) метод возвращает список всех свойств.  
  
 Программа может предоставить любое количество и тип дополнительных свойств, которые можно описать с помощью `IDebugProperty2` интерфейс.  Интегрированная среда разработки может указывать дополнительные свойства программы через универсальный шаблон пользовательского интерфейса обозревателя свойств.  
  
## См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)