---
title: "Тип визуализатора и пользовательское средство просмотра | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "отладка [пакет SDK для отладки], пользовательское средство просмотра"
  - "отладка [отладка SDK] типа визуализатора"
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Тип визуализатора и пользовательское средство просмотра
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Визуализатор типа компонента, который указывает часть данных в очень определенном формате.  Этот формат является полностью принимает разработчик визуализатора, пользователь или стороннего поставщика визуализаторов.  
  
 Пользовательский средство просмотра часть пользовательского средства оценки выражений, которое указывает часть данных в очень определенном формате.  Этот формат является полностью принимает разработчик пользовательского представления. это означает, что формат принимает разработчик вычислителя выражений \(EE\).  
  
## Поддержка визуализаторов типа в средстве оценки выражений  
 EE может поддерживать визуализаторы типа путем поддержки набор интерфейсов, доступных для визуализаторам: интерфейсы [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) и  [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md).  Обратите внимание, что EE не отвечает за реализация визуализатора самого типа. EE просто позволяет визуализаторов внешний доступ к информации о типе.  Такие визуализаторы могут быть поставляются вместе с EE и устанавливается в соответствующем месте в Visual Studio, предоставленными другим стороннего поставщика или даже пользователем.  
  
## Поддержка пользовательских средств просмотра, в средстве оценки выражений  
 EE может также поддерживать пользовательских средств просмотра, в которых предоставляет EE самого код для просмотра тип данных.  Пользовательский средство просмотра реализует [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) интерфейс, который обрабатывает все обязанности отображение данных в любой формат пожелан; средство просмотра имеет полный контроль над отображением и даже может разрешить данные, которые требуется изменить.  Все пользовательские средства просмотра, предоставляемые EE поставляемых с EE, когда продукт поставлен.  
  
## См. также  
 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)   
 [Вычислитель выражений](../../extensibility/debugger/expression-evaluator.md)   
 [Отладка ядра](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)