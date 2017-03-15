---
title: "IDebugClassField::DoesInterfaceExist | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::DoesInterfaceExist"
helpviewer_keywords: 
  - "Метод IDebugClassField::DoesInterfaceExist"
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugClassField::DoesInterfaceExist
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Определяет, определен в классе определенный интерфейс.  
  
## Синтаксис  
  
```cpp#  
HRESULT DoesInterfaceExist(   
   LPCOLESTR pszInterfaceName  
);  
```  
  
```c#  
int DoesInterfaceExist(  
   [In] string pszInterfaceName  
);  
```  
  
#### Параметры  
 `pszInterfaceName`  
 \[in\] строка, содержащая а имя интерфейса, в котором выполняется поиск.  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK, возвращает значение S\_FALSE, если интерфейс не существует. в противном случае возвращает код ошибки.  
  
## Заметки  
 В результате этот метод возвращает перечисление всех интерфейсов и ищет список для соответствующего интерфейса.  
  
## См. также  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)