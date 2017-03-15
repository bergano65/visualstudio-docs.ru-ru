---
title: "IDebugProperty2::SetValueAsString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::SetValueAsString"
helpviewer_keywords: 
  - "IDebugProperty2::SetValueAsString"
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProperty2::SetValueAsString
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Устанавливает значения свойства из данной строки.  
  
## Синтаксис  
  
```cpp#  
HRESULT SetValueAsString (   
   LPCOLESTR pszValue,  
   UINT      nRadix,  
   DWORD     dwTimeout  
);  
```  
  
```c#  
int SetValueAsString (   
   string pszValue,  
   uint   nRadix,  
   uint   dwTimeout  
);  
```  
  
#### Параметры  
 `pszValue`  
 \[in\] строка, содержащая a значение, которое необходимо задать.  
  
 `nRadix`  
 \[in\] корневой узел a для использования в интерпретации любое числовое сведения.  Это может быть 0 для определения корень автоматически.  
  
 `dwTimeout`  
 \[in\] задает максимальное время, в миллисекундах, ожидания возврата из этого метода.  Используйте `INFINITE` ждать бесконечно.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  В следующей таблице приведены другие возможные значения.  
  
|Значение|Описание|  
|--------------|--------------|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Строка не может быть преобразована в значение свойства или значение свойства не может быть задано.|  
|`E_SETVALUE_VALUE_IS_READONLY`|Свойство доступно только для чтения.|  
  
## См. также  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)