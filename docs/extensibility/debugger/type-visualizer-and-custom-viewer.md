---
title: Ввизуатель типа и пользовательский зритель (ru) Документы Майкрософт
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712469"
---
# <a name="type-visualizer-and-custom-viewer"></a>Введите визуализатор и пользовательский зритель
Визуализатор типа — это компонент, отображающие часть данных в определенном формате. Формат полностью зависит от того, кто реализует визуализатор, будь то конечный пользователь или сторонний поставщик визуализаторов.

 Пользовательский зритель — это часть пользовательского оценщика выражения, который отображает часть данных в определенном формате. Этот формат полностью зависит от исполнителя пользовательского просмотра, что означает, что формат зависит от исполнителя оценщика выражения (EE).

## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Поддержка визуализаторов типов в оценщике экспрессии
 EE поддерживает визуализаторы типов, поддерживая набор интерфейсов, доступных для визуализаторов: интерфейсы, такие как [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) и [IEEVisualizerDataProvider.](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) Тем не менее, EE не несет ответственности за реализацию самого визуализатора типа: EE просто позволяет внешним визуализаторам получить доступ к информации о его типе. Такие визуализаторы могут быть отправлены вместе с EE и установлены в соответствующем месте в Visual Studio, поставляемые другим сторонним поставщиком или даже конечным пользователем.

## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Поддержка пользовательских зрителей в оценщике выражений
 EE также может поддерживать пользовательских зрителей, в которых EE сам поставляет код для просмотра типа данных. Пользовательский зритель реализует интерфейс [IDebugCustomViewer,](../../extensibility/debugger/reference/idebugcustomviewer.md) который обрабатывает все обязанности по показу данных в любом желаемом формате; зритель имеет полный контроль над дисплеем и даже может позволить данным быть изменены. Любые пользовательские зрители поставляются EE поставляются с EE, когда продукт поставляется.

## <a name="see-also"></a>См. также
- [Компоненты debugger](../../extensibility/debugger/debugger-components.md)
- [Оценка экспрессии](../../extensibility/debugger/expression-evaluator.md)
- [Двигатель debug](../../extensibility/debugger/debug-engine.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
