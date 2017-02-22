---
title: "Команда контрактов в сборках взаимодействия | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Обработка с использованием сборок взаимодействия, команда контракты команд"
  - "сборки взаимодействия, команда контрактов"
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Команда контрактов в сборках взаимодействия
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Основное соглашение для обработки команд через <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс является то, что среда вызывает <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод, чтобы определить команду, поддерживается ли он поддерживается, чтобы определить ее состояние и текст. Затем среда вызывает <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метод для выполнения команды.  
  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Метод обрабатывается одинаково для всех команд. Дальнейшее взаимодействие при необходимости \(например, с помощью раскрывающихся списков\), осуществляется путем вызова <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метод с соответствующими параметрами. Интерпретация этих параметров зависит от указанной команды.  
  
 Если цель команды возвращает значения в выходном параметре, вызывающий объект всегда отвечает за освобождение все ресурсы, выделенные ранее. Поскольку этот параметр является вариантом, сняв вариант освобождает ресурсы.  
  
 В случаях, где должно работать команды в окне "Иерархия" <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> интерфейс должен использоваться.<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Интерфейс имеет аналогичные контракт с аналогичные методы: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>.  
  
## См. также  
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Маршрутизация команд в пакеты VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Реализация](../../extensibility/internals/command-implementation.md)