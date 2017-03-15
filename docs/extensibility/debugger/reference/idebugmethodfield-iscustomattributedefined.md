---
title: "IDebugMethodField::IsCustomAttributeDefined | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::IsCustomAttributeDefined"
helpviewer_keywords: 
  - "Метод IDebugMethodField::IsCustomAttributeDefined"
ms.assetid: 1b5d95a8-cc87-4acb-9e6a-3928f3632b7c
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugMethodField::IsCustomAttributeDefined
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Определяет, определен ли указанный настраиваемый атрибут.  
  
## Синтаксис  
  
```cpp#  
HRESULT IsCustomAttributeDefined(   
   LPCOLESTR pszCustomAttributeName  
);  
```  
  
```c#  
int IsCustomAttributeDefined(  
   [In] string pszCustomAttributeName  
);  
```  
  
#### Параметры  
 `pszCustomAttributeName`  
 \[in\] строка, содержащая а имя настраиваемого атрибута для поиска.  
  
## Возвращаемое значение  
 Возвращает значение S\_OK, если настраиваемый атрибут задан в этом методе, то в противном случае возвращает значение S\_FALSE.  
  
## См. также  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)