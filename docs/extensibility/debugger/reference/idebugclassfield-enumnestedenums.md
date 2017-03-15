---
title: "IDebugClassField::EnumNestedEnums | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::EnumNestedEnums"
helpviewer_keywords: 
  - "Метод IDebugClassField::EnumNestedEnums"
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugClassField::EnumNestedEnums
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Создает перечислитель для вложенных перечислителей этого класса.  
  
## Синтаксис  
  
```cpp#  
HRESULT EnumNestedEnums(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumNestedEnums(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### Параметры  
 `ppEnum`  
 \[out\] возвращает [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) объект, представляющий список вложенных перечислений.  Возвращает значение NULL, если нет вложенной перечисления.  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK и возвращает значение S\_FALSE, если нет вложенной перечислителей.  В противном случае возвращает код ошибки.  
  
## Заметки  
 Каждый элемент перечисления [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) объект, описывающий вложенное перечисление.  
  
 Перечисление, объявленное в класс является вложенным перечислением.  Пример:  
  
```  
class RootClass {  
   enum NestedEnum { EnumValue = 0 }  
};  
```  
  
 `EnumNestedEnums` метод вернул бы  [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) объект, содержащий одно  [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) объект, представляющий  `NestedEnum` перечисление.  
  
## См. также  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)