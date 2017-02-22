---
title: "IPropertyProxyEESide | Microsoft Docs"
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
  - "IPropertyProxyEESide"
helpviewer_keywords: 
  - "Интерфейс IPropertyProxyEESide"
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IPropertyProxyEESide
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс предоставляет методы данные представления для связанного объекта.  Этот интерфейс является частью поддержки визуализаторов типа.  
  
## Синтаксис  
  
```  
IPropertyProxyEESide : IUnknown  
```  
  
## Примечания по реализации  
 Средство оценки выражений реализующий этот интерфейс, чтобы поддерживать визуализаторы типа.  
  
## Замечания для вызывающих объектов  
 Вызов [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) получить этот интерфейс.  Вызов [QueryInterface](/visual-cpp/atl/queryinterface) на  [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) интерфейс для получения  [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) интерфейс.  
  
## Методы в том порядке Vtable  
 Следующие методы реализуются этим интерфейсом.  
  
|Метод|Описание|  
|-----------|--------------|  
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|Инициализирует поставщика источника данных, чтобы данные объекта можно получить доступ.|  
|[GetManagedViewerCreationData](../Topic/IPropertyProxyEESide::GetManagedViewerCreationData.md)|Извлекает сведения о сборке объекта.|  
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|Возвращает исходные данные для объекта.|  
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|Создает копию существующего хранилища данных.|  
|[InPlaceUpdateObject](../Topic/IPropertyProxyEESide::InPlaceUpdateObject.md)|Создает ссылку на существующий хранилище данных.|  
|[ResolveAssemblyRef](../Topic/IPropertyProxyEESide::ResolveAssemblyRef.md)|Извлекает сведения о конкретной сборке в контексте сборки, содержащей данный объект.|  
  
## Заметки  
 Визуализатор типа использует этот интерфейс для доступа к значениям, связанные с объектом, что этот интерфейс является частью.  Доступ к данным через [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) интерфейс, который предоставляет только для чтения представление данных.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Тип визуализатора и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)