---
title: "Тип визуализатора и пользовательское средство просмотра | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 91aa122c96230c7fd34ce2b65925b9166883def6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="type-visualizer-and-custom-viewer"></a>Тип визуализатора и пользовательское средство просмотра
Тип визуализатора — это компонент, отображает часть данных в конкретный формат. Этот формат является полностью разработчиком визуализатора, будь то конечным пользователем или стороннего поставщика визуализаторов.  
  
 Пользовательское средство просмотра является частью вычислитель пользовательских выражений, который отображает часть данных в конкретный формат. Этот формат является полностью разработчик пользовательское средство просмотра, это означает, что формат разработчиком вычислитель выражений (EE).  
  
## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Поддержка визуализаторами типов при вычислении выражения  
 EE может поддерживать визуализаторами типов с помощью поддержки набор интерфейсов, доступ к визуализаторам: интерфейсы, такие как [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) и [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). Обратите внимание, что EE не отвечает за реализацию типа визуализатор, сам: EE позволяет осуществлять визуализаторы внешний доступ к его сведения о типе. Такие визуализаторы может поставляется вместе с EE и установлены в соответствующее место в Visual Studio поставляется с другого стороннего поставщика или даже конечным пользователем.  
  
## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Поддержка пользовательских средств просмотра в вычислитель выражений  
 EE также может поддерживать пользовательские средства просмотра, в которых EE, сам предоставляет код для просмотра типа данных. Реализует пользовательское средство просмотра [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) требуемого интерфейса, который обрабатывает все операции отображения данных в формате; средство просмотра имеет полный контроль над отображение и даже позволяют изменять данные. Любые пользовательские средства просмотра, предоставляемые EE поставляются с EE после выпуска продукта.  
  
## <a name="see-also"></a>См. также  
 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)   
 [Вычислитель выражений](../../extensibility/debugger/expression-evaluator.md)   
 [Отладка ядра](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)