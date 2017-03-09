---
title: "Практическое руководство. Добавление фирменной символики в пакет VSPackage (C++) | Microsoft Docs"
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
  - "диалоговое окно "О программе""
  - "пакеты VSPackage, экраны-заставки"
  - "пакеты VSPackage, фирменная символика"
ms.assetid: a1b9213f-8702-4716-8623-cd3705d531fa
caps.latest.revision: 10
caps.handback.revision: 10
manager: "douge"
---
# Практическое руководство. Добавление фирменной символики в пакет VSPackage (C++)
Появляться в **О программе** диалоговое окно и экран\-заставку, VSPackages, должны реализовывать  <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> интерфейс.  Это предоставляет следующие сведения [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Имя  
  
-   Идентификатор, как серия или номер версии  
  
-   Сведения  
  
-   Значок эмблемы  
  
 `IVsInstalledProductImpl` класс принимает параметры шаблона дополнительные сведения.  Каждый параметр шаблона идентификатор.  Идентификаторы ресурсов первые 3 строк, а четвертый столбец имеет идентификатор ресурса значка.  
  
## Пример  
 Следующее объявление класса для класса в VSPackage [Примеры VSSDK](../misc/vssdk-samples.md).  
  
```  
class ATL_NO_VTABLE BasicPackage :   
  ...  
  public IVsInstalledProductImpl<  
    IDS_BASICPACKAGE_PRODUCT_NAME,  
    IDS_BASICPACKAGE_PRODUCT_IDENTIFIER,   
    IDS_BASICPACKAGE_PRODUCT_DETAILS,   
    IDI_BASICPACKAGE_LOGO>  
```  
  
 Для тестирования VSPackage см. в разделе [Практическое руководство. Тестирование окна справки о продукте и экранов\-заставок](../misc/how-to-test-the-help-about-and-splash-screens.md).  
  
## См. также  
 [Фирменная символика в пакетах VSPackage](/visual-cpp/misc/vspackage-branding)