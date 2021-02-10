---
title: Контракты команд в сборках взаимодействия | Документация Майкрософт
description: Сведения о базовом контракте для обработки команд через интерфейс Microsoft. VisualStudio. OLE. Interop. IOleCommandTarget.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9ed9435f4f0618ee0c0f4bc47cdb21e2cbf92f77
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940132"
---
# <a name="command-contracts-in-interop-assemblies"></a>Контракты команд в сборках взаимодействия
Базовый контракт для обработки команд через <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс заключается в том, что среда вызывает <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод, чтобы определить, поддерживается ли команда, и, если она поддерживается, для определения ее состояния и текста. Затем среда вызывает <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метод для выполнения команды.

 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>Метод обрабатывается одинаково для всех команд. Дальнейшая связь, если это необходимо (например, с раскрывающимися списками), управляется путем вызова <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метода с соответствующими параметрами. Интерпретация этих параметров зависит от указанной команды.

 Если целевой объект команды возвращает значения в параметре OUTPUT, вызывающий объект всегда отвечает за освобождение всех выделенных ресурсов. Поскольку этот параметр является вариантом, очистка варианта освобождает ресурсы.

 В случаях, когда команды должны работать в окне иерархии, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> необходимо использовать интерфейс. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>Интерфейс имеет похожий контракт с аналогичными методами: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> .

## <a name="see-also"></a>См. также раздел
- [Как пакеты VSPackage добавляют элементы пользовательского интерфейса](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Маршрутизация команд в пакетах VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)
- [Реализация команды](../../extensibility/internals/command-implementation.md)
