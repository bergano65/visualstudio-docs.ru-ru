---
title: "Реализация Цветовая подсветка синтаксиса | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 67535bcc2c907978c24d764c617f8311dc51a444
ms.lasthandoff: 02/22/2017

---
# <a name="implementing-syntax-coloring"></a>Реализация Цветовая подсветка синтаксиса
При языковая служба предоставляет цветовое выделение синтаксиса, средство синтаксического анализа преобразует строку текста в массив цветных элементов и возвращает соответствующий эти цветные элементы типов маркеров. Средство синтаксического анализа должна возвращать типы маркеров, входящих в список цветных элементов. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Отображает каждый цветного элемента в окне кода согласно атрибуты, назначенные этим объектом colorizer соответствующий тип маркера.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Указывает интерфейс средства синтаксического анализа, и реализация синтаксического анализа полностью зависит от вас. Тем не менее средство синтаксического анализа реализацию по умолчанию предоставляется в проекте Visual Studio языковой пакет. Для управляемого кода платформа управляемых пакетов (MPF) обеспечивает полную поддержку для выделения цветом текста.  
  
 Устаревший языковые службы реализуются как частью VSPackage, но это использование расширений MEF новый способ реализации возможностей службы языка. Чтобы узнать больше о новый способ реализовать Цветовая подсветка синтаксиса, в разделе [Пошаговое руководство: выделение текста](../../extensibility/walkthrough-highlighting-text.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API как можно быстрее. Это улучшает производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.  
  
## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Действия, выполняемые с помощью редактора для выделения текста цветом  
  
1.  Возвращает редактор colorizer путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>объекта.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>  
  
2.  Вызывает редактор <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A>метод для определения, должен ли colorizer состояние каждой строки, чтобы удовлетворять вне colorizer.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A>  
  
3.  Если colorizer требуется состояние храниться за пределами colorizer, вызывает редактор <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A>метод для получения состояния первой строки.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A>  
  
4.  Для каждой строки в буфере, вызывает редактор <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>методу, который выполняет следующие действия:</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>  
  
    1.  Строки текста, передается сканера преобразуемый текст на лексемы. Каждый маркер указывает текст токена и тип маркера.  
  
    2.  Тип токена преобразуется в индекс в списке цветных элементов.  
  
    3.  Сведения о токене используется для заполнения массива таким образом, что каждый элемент массива соответствует символа в строке. Значения, хранящиеся в массиве, индексы в списке цветных элементов.  
  
    4.  Для каждой строки возвращается состояние в конце строки.  
  
5.  Если colorizer требуется состояние сохраняется, редактор кэширует состояния для этой строки.  
  
6.  Редактор отображает строку текста, с помощью сведений, возвращаемых из <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>метод.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Для этого необходимо выполнить следующие действия:  
  
    1.  Для каждого символа в строке возвращается индекс цветного элемента.  
  
    2.  Если с помощью цветных элементов по умолчанию, доступ к редактора цветных элементов списка.  
  
    3.  В противном случае — вызов службы языка <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>способ получения цветного элемента.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>  
  
    4.  Используйте сведения в цветного элемента для отображения текста на экране.  
  
## <a name="managed-package-framework-colorizer"></a>Colorizer Framework управляемых пакетов  
 Платформа управляемых пакетов (MPF) содержит все классы, необходимые для реализации colorizer. Должны наследовать класс службы языка <xref:Microsoft.VisualStudio.Package.LanguageService>класса и реализовать требуемые методы.</xref:Microsoft.VisualStudio.Package.LanguageService> Необходимо указать сканера и синтаксического анализа путем реализации <xref:Microsoft.VisualStudio.Package.IScanner>интерфейс и возвратить экземпляр этого интерфейса из <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>метод (один из методов, которые должны быть реализованы в <xref:Microsoft.VisualStudio.Package.LanguageService>класса).</xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> </xref:Microsoft.VisualStudio.Package.IScanner> Дополнительные сведения см. в разделе [синтаксиса, выделение цветом в языковую службу для прежних версий](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство: использование встроенных цветных элементов](../../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Пользовательские цветных элементов](../../extensibility/internals/custom-colorable-items.md)   
 [Разработка языковую службу для прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Синтаксис выделения цветом в языковую службу для прежних версий](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
