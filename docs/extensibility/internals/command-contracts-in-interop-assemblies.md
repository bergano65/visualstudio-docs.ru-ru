---
title: Командные контракты в Межопоповых Собраниях (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f20a4f479d62cd1b64c3b13ff6e1a949656a668
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709685"
---
# <a name="command-contracts-in-interop-assemblies"></a>Командные контракты в межпромсборках
Основной контракт для обработки <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> команд через интерфейс <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> состоит в том, что среда вызывает метод, чтобы определить, поддерживается ли команда, и, если она поддерживается, определить ее состояние и текст. Затем среда вызывает <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метод выполнения команды.

 Метод <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> обрабатывается одинаково для всех команд. Дальнейшее общение, если требуется (например, со списками <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> выпадающих), управляется путем вызова метода с соответствующими параметрами. Интерпретация этих параметров зависит от указанной команды.

 Если цель команды возвращает значения в параметре вывода, абонент всегда несет ответственность за освобождение всех ресурсов, которые были выделены. Поскольку этот параметр является вариантом, очистка варианта освобождает ресурсы.

 В тех случаях, когда команды должны работать <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> в окне иерархии, интерфейс должен использоваться. Интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> имеет аналогичный контракт с <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> аналогичными методами: и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>.

## <a name="see-also"></a>См. также
- [Как VSPackages добавляют элементы пользовательского интерфейса](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Командная размытая в VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)
- [Реализация командования](../../extensibility/internals/command-implementation.md)
