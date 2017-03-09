---
title: "Общие сведения о фирменной символике | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Диалоговое окно "О программе""
  - "пакеты VSPackage, экраны-заставки"
  - "пакеты VSPackage, фирменная символика"
ms.assetid: a47b3645-574c-41c7-8a97-d071cd6b1e82
caps.latest.revision: 11
caps.handback.revision: 11
manager: "douge"
---
# Общие сведения о фирменной символике
Чтобы отобразить сведения о продукте или экран\-заставке **О программе** диалоговое окно в VSPackage, что:  
  
-   Provide детализировал сведения о продукте в разделе реестра InstalledProducts.  
  
     \-или\-  
  
-   Реализуйте интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>.  
  
 Управляемые границы пакетов \(MPF\) <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute> атрибут для наблюдения за регистрацию в разделе реестра InstalledProducts.  Дополнительные сведения см. в разделе [Практическое руководство. Добавление фирменной символики в пакет VSPackage \(C\# и Visual Basic\)](../misc/how-to-brand-a-vspackage-csharp-and-visual-basic.md).  
  
 Библиотека Visual Studio предоставляет `IVsInstalledProductImpl` класс шаблона для создания реализация  <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>.  Дополнительные сведения см. в разделе [Практическое руководство. Добавление фирменной символики в пакет VSPackage \(C\+\+\)](../misc/how-to-brand-a-vspackage-cpp.md).  
  
 Реализация <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> мощны явно более чем с помощью атрибута или шаблон.  
  
-   Можно указать значок экран\-заставки, который отличается от **О программе** значок.  
  
-   Можно указать название продукта экран\-заставки, отличается от **О программе** название продукта.  
  
    > [!IMPORTANT]
    >  При использовании <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute> а также реализация  <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>интерфейс имеет приоритет.  
  
    > [!NOTE]
    >  Один и тот же ресурс значка используется для экран\-заставки и **О программе** диалоговое окно.  Ресурс значка VSPackage должен включать 16 × 16 для экран\-заставки образ и 32 × 32 для образа **О программе** диалоговое окно.  Если указывается только один размер образа, он будет изменен размер по мере необходимости, но визуальные результаты будут субоптимальны.  
  
 Список связанных задач см. в разделе [Пакеты VSPackage](../extensibility/internals/vspackages.md).  
  
## См. также  
 [Пакеты VSPackage](../extensibility/internals/vspackages.md)   
 [Библиотека Visual Studio, обзор](../misc/visual-studio-library-overview.md)