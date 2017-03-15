---
title: "Практическое руководство. Получение службы из объекта DTE | Microsoft Docs"
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
  - "службы, из объекта DTE"
ms.assetid: c26a51d4-86f0-454b-9625-5443e55eec7d
caps.latest.revision: 13
caps.handback.revision: 13
manager: "douge"
---
# Практическое руководство. Получение службы из объекта DTE
Службу можно получить из любой программы, которая имеет доступ к объекту <xref:EnvDTE.DTEClass> автоматизации [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Например, можно получить доступ к службе <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> из мастера через объект DTE.  Можно использовать эту службу для записи в журнал действий.  Дополнительные сведения см. в разделе [Практическое руководство: использование журнала действий](../extensibility/how-to-use-the-activity-log.md).  
  
 Объект DTE реализует <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>, который можно использовать для запроса службы из управляемого кода с помощью <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>.  
  
### Получить службу из объекта DTE  
  
1.  Следующий код создает <xref:Microsoft.VisualStudio.Shell.ServiceProvider> из объекта DTE и вызывает <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> с типом службы <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>.  Служба привоженна к интерфейсу <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>, используемый для записи в журнале действий.  Дополнительные сведения abou как записи в журнал действий см. в разделе [Практическое руководство: использование журнала действий](../extensibility/how-to-use-the-activity-log.md).  
  
     [!code-cs[GetAServiceFromTheDTEObject#1](../misc/codesnippet/CSharp/how-to-get-a-service-from-the-dte-object_1.cs)]
     [!code-vb[GetAServiceFromTheDTEObject#1](../misc/codesnippet/VisualBasic/how-to-get-a-service-from-the-dte-object_1.vb)]  
  
## См. также  
 [Использование и предоставления услуг](../extensibility/using-and-providing-services.md)   
 [Основы службы](../extensibility/internals/service-essentials.md)