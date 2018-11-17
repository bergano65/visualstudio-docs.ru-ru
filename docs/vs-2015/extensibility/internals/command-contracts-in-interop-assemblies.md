---
title: Команда контрактов в сборки взаимодействия | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8089314293c92a24396a90f4be4dd4120c03bbcd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51725096"
---
# <a name="command-contracts-in-interop-assemblies"></a>Контракты команд в сборках взаимодействия
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Основное соглашение для обработки команды посредством <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс является то, что среда вызывает <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод для определения ли команда поддерживается, и, если он поддерживается, для определения его состояния и текста. Затем среда вызывает метод <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метод для выполнения команды.  
  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Метод обрабатывается одинаково для всех команд. Последующих сеансов связи, при необходимости (например, с помощью раскрывающихся списков), осуществляется путем вызова <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метод с необходимыми параметрами. Интерпретация этих параметров зависит от указанной команды.  
  
 Если целевой объект команды возвращает значения в выходном параметре, вызывающий объект всегда отвечает за освобождение все ресурсы, выделенные. Так как этот параметр имеет значение variant, сняв вариант освобождает ресурсы.  
  
 В случаях, где команды должны работать внутри окна иерархии <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> необходимо использовать интерфейс. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Интерфейс имеет аналогичные контракт с подобными методами: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>.  
  
## <a name="see-also"></a>См. также  
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Маршрутизация команд в пакеты VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Реализация](../../extensibility/internals/command-implementation.md)

