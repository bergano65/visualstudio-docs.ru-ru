---
title: "Использование службы градиента в окне инструментов | Microsoft Docs"
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
  - "службы, пошаговые руководства"
  - "окна инструментов, служба градиента"
  - "служба градиента, пошаговые руководства"
  - "службы, использование"
ms.assetid: 67590982-6e1f-4e4b-be18-7d1b294cabff
caps.latest.revision: 44
caps.handback.revision: 44
manager: "douge"
---
# Использование службы градиента в окне инструментов
Поскольку окна инструментов [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] построенные с Windows Presentation Foundation \(WPF\), не следует вызывать службу градиента в Коде.  Вместо этого в конструкторе, представляющий поверхность окна инструментов, выберите элемент `StackPanel` , а затем в окне **Свойства** , измените свойство **Фон** для задания градиент.  Дополнительные сведения см. в разделе [Задание цветов, градиентов и прозрачности](../misc/setting-colors-gradients-and-opacity.md).  
  
## См. также  
 [NOT IN BUILD: Tool Window Walkthroughs](http://msdn.microsoft.com/ru-ru/ecffc579-0e96-48ad-90f3-01a3d80f3ce5)   
 [Расширение окон инструментов](../misc/extending-tool-windows.md)   
 [Задание цветов, градиентов и прозрачности](../misc/setting-colors-gradients-and-opacity.md)