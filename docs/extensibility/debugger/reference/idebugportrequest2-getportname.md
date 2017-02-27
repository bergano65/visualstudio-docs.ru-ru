---
title: "IDebugPortRequest2::GetPortName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortRequest2::GetPortName"
helpviewer_keywords: 
  - "IDebugPortRequest2::GetPortName"
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPortRequest2::GetPortName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает имя порта.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetPortName(   
   BSTR* pbstrPortName  
);  
```  
  
```c#  
int GetPortName(   
   out string pbstrPortName  
);  
```  
  
#### Параметры  
 `pbstrPortName`  
 \[out\] возвращает имя порта.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) интерфейс обычно передается из пакета отладки \(клиента\) для поставщика порта \(сервер\) для получения подключение к порту.  И пакет отладки и поставщик порта для порта осведомлены возможных вариантов.  Если простая строка может описать порт, `IDebugPortRequest2::GetPortName` метод обладает достаточными сведениями для установления соединения.  В противном случае дополнительные интерфейсы могут быть предоставлены клиентом, который может быть получен с помощью сервером `IDebugPortRequest2::QueryInterface`.  
  
## См. также  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)