---
title: Визуализатор типов и пользовательское средство просмотра | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b8def9d28279f601ff488fca457982806629c0b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712469"
---
# <a name="type-visualizer-and-custom-viewer"></a>Визуализатор типов и пользовательское средство просмотра
Визуализатор типов — это компонент, отображающий фрагмент данных в определенном формате. Формат полностью зависит от того, кто реализует визуализатор, является ли он конечным пользователем или сторонним поставщиком визуализаторов.

 Пользовательское средство просмотра является частью пользовательского средства оценки выражений, отображающего фрагмент данных в определенном формате. Этот формат полностью соответствует разработчику пользовательского средства просмотра, что означает, что этот формат имеет вид, реализующий средство оценки выражений (EE).

## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Поддержка визуализаторов типов в вычислителе выражений
 EE поддерживает визуализаторы типов, поддерживая набор интерфейсов, доступных визуализаторам: такие интерфейсы, как [иивисуализерсервице](../../extensibility/debugger/reference/ieevisualizerservice.md) и [иивисуализердатапровидер](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). Однако EE не несет ответственности за реализацию визуализатора типа: EE просто позволяет внешним визуализаторам получить доступ к сведениям о типе. Такие визуализаторы могут поставляться вместе с EE и устанавливаться в соответствующем месте в Visual Studio, предоставленном другим сторонним поставщиком или даже конечным пользователем.

## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Поддержка пользовательских средств просмотра в вычислителе выражений
 EE также может поддерживать пользовательские средства просмотра, в которых сам EE предоставляет код для просмотра типа данных. Пользовательское средство просмотра реализует интерфейс [идебугкустомвиевер](../../extensibility/debugger/reference/idebugcustomviewer.md) , который обрабатывает все обязанности по отображению данных в любом нужном формате. средство просмотра имеет полный контроль над отображением и даже позволяет изменять данные. Любые пользовательские средства просмотра, предоставляемые EE, поставляются вместе с EE при отгрузке продукта.

## <a name="see-also"></a>См. также раздел
- [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)
- [Средство оценки выражений](../../extensibility/debugger/expression-evaluator.md)
- [Модуль отладки](../../extensibility/debugger/debug-engine.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
