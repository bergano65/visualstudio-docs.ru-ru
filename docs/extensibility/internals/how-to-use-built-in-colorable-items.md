---
title: "Практическое руководство: использование встроенных цветных элементов | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "цветные элементы"
  - "языковые службы, встроенные цветных элементов"
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Практическое руководство: использование встроенных цветных элементов
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Прежде чем использовать встроенные цветного элементы, сначала необходимо указать в интегрированной среде разработки \(ide\), которая не предоставить собственные пользовательские цветного элементы, которые в этом случае были бы <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> объекты.  Это можно сделать, установив запись реестра для языковой службы.  
  
### Использовать встроенные цветного элементы  
  
1.  В разделе HKEY\_LOCAL\_MACHINE \\ VisualStudio \\*X.Y*Языки языка \\ \\ services \\*название языка*, где  *X.Y* версия   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и  *название языка* имя языка, создает записи реестра типа DWORD с именем значение  `RequestStockColors`.  
  
2.  Установка `RequestStockColors` значение записи реестра до 1.  
  
     После создания записи реестра, colorizer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> метод может использовать члены  <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> перечисление, чтобы заполнить массив атрибутов цвета для использования редактором.  
  
    > [!NOTE]
    >  Не устанавливайте эту запись реестра, если предоставляется пользовательский цветного элементы.  Дополнительные сведения см. в разделе [Пользовательские цветных элементов](../../extensibility/internals/custom-colorable-items.md).  
  
## См. также  
 [В редакторах синтаксиса](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Синтаксиса в языковую службу для прежних версий](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Реализация Цветовая подсветка синтаксиса](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Пользовательские цветных элементов](../../extensibility/internals/custom-colorable-items.md)   
 [Регистрация службы языка для прежних версий](../../extensibility/internals/registering-a-legacy-language-service2.md)