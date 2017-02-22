---
title: "IDebugObject2::GetBackingFieldForProperty | Microsoft Docs"
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
  - "IDebugObject2::GetBackingFieldForProperty"
helpviewer_keywords: 
  - "Метод IDebugObject2::GetBackingFieldForProperty"
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject2::GetBackingFieldForProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Получает поле или переменную \(если они есть\), могут подпирать свойство, представленное этим объектом.  
  
## Синтаксис  
  
```cpp  
HRESULT GetBackingFieldForProperty(  
   IDebugObject2** ppObject  
);  
```  
  
```c#  
int GetBackingFieldForProperty(  
   out IDebugObject2 ppObject  
);  
```  
  
#### Параметры  
 `ppObject`  
 \[out\] [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) объект, описывающий резервное поле.  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK; в противном случае возвращает код ошибки.  
  
## Заметки  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) объект представляет свойство класса управляемого кода, т е метод с методом доступа get и set.  Эти свойства обычно требуется конструировать переменная содержит значение свойства.  Эта переменная, как резервное поле.  Если резервное поле объекта, необходимо вернуть значение NULL: некоторые вызывающие объекты не могут обратить внимание на возвращаемое значение, а посмотрят, что увидели если значение NULL возвращено in `ppObject`.  
  
## См. также  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)