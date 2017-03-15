---
title: "IPropertyProxyEESide::CreateReplacementObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IPropertyProxyEESide::CreateReplacementObject"
helpviewer_keywords: 
  - "IPropertyProxyEESide::CreateReplacementObject"
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IPropertyProxyEESide::CreateReplacementObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Создает копию конкретного объекта данных в средство оценки выражений \(EE\).  
  
## Синтаксис  
  
```cpp  
HRESULT CreateReplacementObject(  
   IEEDataStorage*  dataIn,  
   IEEDataStorage** dataOut  
);  
```  
  
```c#  
int CreateReplacementObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### Параметры  
 `dataIn`  
 \[in\] [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) объект, содержащий данные, которые необходимо скопировать.  
  
 `dataOut`  
 \[out\] возвращает новую `IEEDataStorage` объект.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Получатель этот метод [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) объект, представляющий массив байтов.  Этот входящий объект данных, как правило, не реализуется EE.  Однако объект, возвращенный этим методом, всегда реализуется EE, который позволяет реализовать EE `IEEDataStorage` интерфейс на любой класс пожелан.  
  
 Обратите внимание, что данные, предоставляемые входящим `IEEDataStorage` объект должен быть одними и теми же данными в общительном  `IEEDataStorage` объект.  
  
## См. также  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)