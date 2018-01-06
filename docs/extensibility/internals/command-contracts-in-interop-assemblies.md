---
title: "Команда контрактов в сборках взаимодействия | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d32a49d780f6ae7929f1442ee70a8085724ca6e0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="command-contracts-in-interop-assemblies"></a>Команда контрактов в сборках взаимодействия
Базовый контракт для обработки команды через <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс является то, что окружение вызывает <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод для определения ли команда поддерживается, и, если он поддерживается, чтобы определить его состояние и текст. Затем среда вызывает метод <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метод для выполнения команды.  
  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Метод обрабатываются одинаково для всех команд. Последующих сеансов связи, при необходимости (например, с помощью раскрывающихся списков), осуществляется путем вызова <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метод с соответствующими параметрами. Интерпретация этих параметров зависит от указанной команды.  
  
 Если целевой объект команды возвращает значения в выходном параметре, вызывающий объект всегда отвечает за освободить все ресурсы, выделенные. Поскольку этот параметр является вариантом, сняв вариант высвобождает ресурсы.  
  
 В случаях, где команды должны работать в окне "Иерархия" <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> интерфейса необходимо использовать. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Интерфейс имеет аналогичные контракт с подобными методами: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>.  
  
## <a name="see-also"></a>См. также  
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Маршрутизация команд в пакеты VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Реализация](../../extensibility/internals/command-implementation.md)