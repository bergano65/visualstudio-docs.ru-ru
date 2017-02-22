---
title: "Практическое руководство: автоматизации для Windows | Microsoft Docs"
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
  - "автоматизация [Visual Studio SDK] окна инструментов"
  - "окна инструментов, автоматизация"
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Практическое руководство: автоматизации для Windows
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Можно предоставить автоматизации для документа и окна инструментов.  Защита автоматизацию целесообразен, когда требуется сделать объекты автоматизации доступной в окне, а среда уже не предоставляет готовые объект автоматизации, поскольку она делает со списком задач.  
  
## Автоматизация для окна инструментов  
 Среда предоставляет автоматизацию в окне инструментов, возвращая стандарт <xref:EnvDTE.Window> объект как описано в следующей процедуре:  
  
#### Предоставить автоматизации для окна инструментов  
  
1.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> метод через среду с  <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> Вставить как  `VSFPROPID` параметр, который требуется возвратить  `Window` объект.  
  
2.  Если вызывающий объект запрашивает объект автоматизации VSPackage\-специфического до окончания для окна инструментов <xref:EnvDTE.Window.Object%2A>calls среды  `QueryInterface` для  `IExtensibleObject`"  <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>или  `IDispatch` интерфейсы.  Оба `IExtensibleObject` и  `IVsExtensibleObject` обеспечьте a  <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> метод.  
  
3.  Вызывается, когда среда `GetAutomationObject` передача метода  `NULL`в ответ, передавая обратно объект VSPackage\-специфического.  
  
4.  Если вызов `QueryInterface` для  `IExtensibleObject` и  `IVsExtensibleObject` сбой, после чего вызовы среды  `QueryInterface` для  `IDispatch`.  
  
## Автоматизация для окон документов  
 Standard <xref:EnvDTE.Document> объект также доступен из среды, хотя редактор может иметь собственную реализацию  `T:EnvDTE.Document` объект путем реализации  `IExtensibleObject` интерфейс и реакция на  `GetAutomationObject`.  
  
 Кроме того, редактор может предоставить объект, извлеченный с помощью автоматизации VSPackage\-специфического <xref:EnvDTE.Document.Object%2A> метод путем реализации  `IVsExtensibleObject` OR  `IExtensibleObject` интерфейсы.  [Примеры VSSDK](../../misc/vssdk-samples.md) предоставляет объект автоматизации документ\-специфического RTF.  
  
## См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>