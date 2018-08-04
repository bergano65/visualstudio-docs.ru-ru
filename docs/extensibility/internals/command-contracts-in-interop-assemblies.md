---
title: Команда контрактов в сборки взаимодействия | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c2ac80125111ebfe3d8a7e5dc89d1f2597f8d3a4
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510859"
---
# <a name="command-contracts-in-interop-assemblies"></a>Контракты команд в сборках взаимодействия
Основное соглашение для обработки команды посредством <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс является то, что среда вызывает <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод для определения ли команда поддерживается, и, если он поддерживается, для определения его состояния и текста. Затем среда вызывает метод <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метод для выполнения команды.  
  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Метод обрабатывается одинаково для всех команд. Последующих сеансов связи, при необходимости (например, с помощью раскрывающихся списков), осуществляется путем вызова <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метод с необходимыми параметрами. Интерпретация этих параметров зависит от указанной команды.  
  
 Если целевой объект команды возвращает значения в выходном параметре, вызывающий объект всегда отвечает за освобождение все ресурсы, выделенные. Так как этот параметр имеет значение variant, сняв вариант освобождает ресурсы.  
  
 В случаях, где команды должны работать внутри окна иерархии <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> необходимо использовать интерфейс. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Интерфейс имеет аналогичные контракт с подобными методами: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>.  
  
## <a name="see-also"></a>См. также  
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Маршрутизация команд в пакеты VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Реализация команды](../../extensibility/internals/command-implementation.md)