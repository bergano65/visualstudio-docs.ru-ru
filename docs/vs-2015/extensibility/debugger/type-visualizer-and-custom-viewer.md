---
title: Визуализатор типов и пользовательское средство просмотра | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a85be2978abe35e91096b55fba5ec5281be25fbe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185308"
---
# <a name="type-visualizer-and-custom-viewer"></a>Визуализатор типов и пользовательское средство просмотра
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Визуализатор типов — это компонент, который отображает фрагмент данных в особо определенном формате. Этот формат полностью предназначен для разработчика визуализатора, должен быть конечным пользователем или сторонним поставщиком визуализаторов.  
  
 Пользовательское средство просмотра является частью пользовательского средства оценки выражений, отображающего фрагмент данных в особо определенном формате. Этот формат полностью соответствует разработчику пользовательского средства просмотра, что означает, что этот формат имеет вид, реализующий средство оценки выражений (EE).  
  
## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Поддержка визуализаторов типов в вычислителе выражений  
 EE может поддерживать визуализаторы типов, поддерживая набор интерфейсов, доступных для визуализаторов: таких интерфейсов, как [иивисуализерсервице](../../extensibility/debugger/reference/ieevisualizerservice.md) и [иивисуализердатапровидер](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). Однако обратите внимание, что EE не несет ответственности за реализацию визуализатора типа: EE просто позволяет внешним визуализаторам получить доступ к сведениям о типе. Такие визуализаторы могут поставляться вместе с EE и устанавливаться в соответствующем месте в Visual Studio, предоставленном другим сторонним поставщиком или даже конечным пользователем.  
  
## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Поддержка пользовательских средств просмотра в вычислителе выражений  
 EE также может поддерживать пользовательские средства просмотра, в которых сам EE предоставляет код для просмотра типа данных. Пользовательское средство просмотра реализует интерфейс [идебугкустомвиевер](../../extensibility/debugger/reference/idebugcustomviewer.md) , который обрабатывает все обязанности по отображению данных в любом нужном формате. средство просмотра имеет полный контроль над отображением и даже позволяет изменять данные. Любые пользовательские средства просмотра, предоставляемые EE, поставляются вместе с EE при отгрузке продукта.  
  
## <a name="see-also"></a>См. также:  
 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)   
 [Средство оценки выражений](../../extensibility/debugger/expression-evaluator.md)   
 [Модуль отладки](../../extensibility/debugger/debug-engine.md)   
 [идебугкустомвиевер](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [иивисуализерсервице](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
