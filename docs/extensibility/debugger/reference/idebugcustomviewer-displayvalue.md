---
title: "IDebugCustomViewer::DisplayValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomViewer::DisplayValue"
helpviewer_keywords: 
  - "IDebugCustomViewer::DisplayValue"
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugCustomViewer::DisplayValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод вызывается для отображения указанного значения.  
  
## Синтаксис  
  
```cpp#  
HRESULT DisplayValue(  
   HWND             hwnd,  
   DWORD            dwID,  
   IUnknown *       pHostServices,  
   IDebugProperty3* pDebugProperty);  
);  
```  
  
```c#  
int DisplayValue(  
   IntPtr          hwnd,   
   uint            dwID,   
   object          pHostServices,   
   IDebugProperty3 pDebugProperty  
);  
```  
  
#### Параметры  
 `hwnd`  
 \[in\] родительское окно  
  
 `dwID`  
 \[in\] идентификатор для пользовательских средств просмотра, которые поддерживают более одного типа.  
  
 `pHostServices`  
 \[in\] Зарезервирован.  Всегда задавайте значение null.  
  
 `pDebugProperty`  
 \[in\] интерфейс, который может быть использован для получения значения для отображения.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Отображение" в "является модальным, что этот метод создает требуемое окно отображает значение ожидает ввода и закрывает окно все перед возвратом вызывающему.  Это означает, что метод должен обрабатывать все аспекты отображения значения свойства, от окно для вывода на ввод пользователя в разрушать окно.  
  
 Поддержка изменить значение с заданным [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) объект, можно воспользоваться  [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) метод \- если значение можно выразить в виде строки.  В противном случае необходимо создать пользовательский интерфейс\-монопольный средству оценки выражений, реализующий данное `DisplayValue` метод\-на одном объекте, реализующий  `IDebugProperty3` интерфейс.  Этот пользовательский интерфейс, предоставленными бы методы для изменения размера и сложности произвольные данные.  
  
## См. также  
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)