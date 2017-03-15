---
title: "Реализация интерфейса IVsPackage | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "интерфейс IVsPackage"
  - "интерфейсы, реализация IVsPackage"
ms.assetid: 0c76b2e1-ce63-47fc-93ee-847cad281fc1
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# Реализация интерфейса IVsPackage
Все VSPackages должен реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> интерфейс.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] вызывает методы  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> для инициализации и закрыть VSPackages, чтобы получить связать страницы свойств и по другим причинам.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> интерфейс интерфейс шлюза   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и VSPackage.  
  
 Можно написать управляемый VSPackage, как подкласс <xref:Microsoft.VisualStudio.Shell.Package> класс, который реализует  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> от вашего имени.  Дополнительные сведения см. в разделе [Управляемые пакеты VSPackage](../misc/managed-vspackages.md).  
  
> [!NOTE]
>  Многие из неуправляемого кода образца в разделе интеграция Visual Studio [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] использует библиотеку шаблонных классов ATL \(библиотека ATL\).  Нет необходимости использовать библиотеку ATL для создания VSPackages, но необходимо понимание библиотеки ATL для понимания образцы кода.  
  
## См. также  
 [Пакеты VSPackage](../extensibility/internals/vspackages.md)