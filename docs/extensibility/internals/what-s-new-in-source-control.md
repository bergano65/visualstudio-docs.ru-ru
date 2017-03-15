---
title: "Новые возможности системы управления версиями | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "что такое новой системы управления версиями [Visual Studio SDK]"
  - "Система управления версиями [Visual Studio SDK], новые возможности"
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
caps.latest.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 27
---
# Новые возможности системы управления версиями
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

IN [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] можно предоставить глубоко интегрированное решение к системе управления версиями, реализовав систему управления версиями VSPackage.  Этот раздел описывает функции системы управления версиями VSPackages и обзор действий реализации.  
  
## Система управления версиями VSPackage  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] поддерживает 2 типа решений системы управления версиями.  Во всех версиях [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]все еще можно интегрировать подключаемый модуль системы управления версиями API\-основанный подключаемым модулем.  Можно также создать VSPackage для системы управления версиями, которая предоставляет глубок\-среда integration services [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] путь, подходящий для решений системы управления версиями, требующие высокого уровня сложности и автономии.  
  
 VSPackage может добавлять функциональность практически любого типа [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Система управления версиями обеспечивает полную VSPackage функцию системы управления версиями [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]из пользовательского интерфейса, представляемое пользователю на конечный сообщение с системой управления версиями.  
  
 Реализация системы управления версиями VSPackage не требует "все или ничего" стратегия.  Автор системы управления версиями VSPackage должен проинвестировать значительный объем работ по в реализации несколько интерфейсов системы управления версиями и новых элементов пользовательского интерфейса \(диалоговые окна, меню и панели инструментов\) для поддержки всю функциональность системы управления версиями, так же как и интерфейсы, необходимые для любого пакета интегрированные с успешно [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Следующие шаги позволяют общие сведения о том, что необходимо для реализации пакета системы управления версиями.  Дополнительные сведения см. в разделе [Создание VSPackage управления источника](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
1.  Создайте VSPackage, proffers частная службы системы управления версиями.  
  
2.  Реализуйте интерфейсы в службах источника элемент управления\-родственных, proffered by [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(например,  <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> и  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> интерфейс\).  
  
3.  Зарегистрируйте система управления версиями VSPackage.  
  
4.  Реализуйте все пользовательского интерфейса системы управления версиями, в том числе пунктов меню, диалоговых окна, панели инструментов и контекстные меню.  
  
5.  Все события источника элемент управления\-родственные передаются в системе управления версиями VSackage, если оно активно и должно обрабатываться в VSPackage.  
  
6.  Система управления версиями должна прослушивать события VSPackage, что и реализация <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> интерфейс а также события документа проекта прокрутки \(TPD\) \(реализация  <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> интерфейс\) и предполагает, необходимые действия.  
  
## См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Обзор](../../extensibility/internals/source-control-integration-overview.md)   
 [Создание VSPackage управления источника](../../extensibility/internals/creating-a-source-control-vspackage.md)