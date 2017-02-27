---
title: "Автоматизация для конфигурации и SelectedItem объектов | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "автоматизация [Visual Studio SDK] SelectedItem объекта"
  - "автоматизация [Visual Studio SDK] построения"
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Автоматизация для конфигурации и SelectedItem объектов
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Можно автоматизировать процессы построения и выбранного элемента в пределах [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Автоматизация построения  
 Построение или конфигурация которых модель автоматизации, которая обеспечивается при реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>.  Дополнительные сведения см. в разделе [Общие сведения о конфигурациях построения](../../ide/understanding-build-configurations.md).  
  
 При создании VSPackage и нужно отслеживать параметры конфигурации, следует использовать модель автоматизации.  
  
## Автоматизация для SelectedItem  
 Не следует предоставлять реализацию `SelectedItem` объект поскольку Visual Studio содержит стандартную реализацию.  Однако можно реализовать `SelectedItem` объект если вы предпочитаете.  Необходимо реализовывать объект, содержащий <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> интерфейс и возвращает ответ к вызову  <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>метод со значением в VSITEMID  `SelectedItem` .  
  
## См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Способствовали модели автоматизации](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [Общие сведения о конфигурациях построения](../../ide/understanding-build-configurations.md)