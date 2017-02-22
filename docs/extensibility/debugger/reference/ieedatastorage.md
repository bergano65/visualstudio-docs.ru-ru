---
title: "IEEDataStorage | Microsoft Docs"
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
  - "IEEDataStorage"
helpviewer_keywords: 
  - "Интерфейс IEEDataStorage"
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IEEDataStorage
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет массив байтов.  
  
## Синтаксис  
  
```  
IEEDataStorage : IUnknown  
```  
  
## Примечания по реализации  
 Средство оценки выражений \(EE\) реализует этот интерфейс, чтобы представлять массив байтов, используемых визуализаторами типа для получения и информациями об изменениях через [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) интерфейс\).  EE обычно реализует этот интерфейс, чтобы поддерживать внешние визуализаторы типа.  
  
## Замечания для вызывающих объектов  
 Методы `IPropertyProxyEESide` интерфейс всех возвращает этот интерфейс.  Вызов [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) доступ  [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) интерфейс.  Вызов [QueryInterface](/visual-cpp/atl/queryinterface) на  [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) интерфейс для получения  [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) интерфейс.  
  
## Методы в том порядке Vtable  
 `IEEDataStorage` интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetData](../Topic/IEEDataStorage::GetData.md)|Получает указанное число байтов данных в предоставленный буфер.|  
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Извлекает число байтов доступных данных.|  
  
## Заметки  
 Этот интерфейс используется визуализатором типа для доступа к данным, который содержит указанный объект.  Эти данные обрабатываются как массив байтов, позволяя визуализатор типа для управления их в него требуется любой способ представления пользователю.  
  
 Пользовательский средство просмотра также может использовать этот интерфейс, при необходимости, то, как правило пользовательское средство просмотра использует пользовательский интерфейс [GetMemoryBytes](../Topic/IDebugProperty2::GetMemoryBytes.md) OR  [GetStringChars](../Topic/IDebugProperty3::GetStringChars.md) \(для строка\-ориентированных данных\).  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [Тип визуализатора и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)