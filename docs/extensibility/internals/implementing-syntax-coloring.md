---
title: Реализация Цветовая подсветка синтаксиса | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5502bd30378130e5977d427acb9df5b73226a05b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131859"
---
# <a name="implementing-syntax-coloring"></a>Реализация Цветовая подсветка синтаксиса
При языковая служба предоставляет окрашивание синтаксиса, средство синтаксического анализа преобразует строки текста в массиве цветных элементов и возвращает соответствующий эти цветные элементы типов маркеров. Средство синтаксического анализа должен возвращать маркера типов, входящих в перечень цветных элементов. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Отображает каждого цветного элемента в окне кода согласно атрибуты, назначенные в объекте colorizer соответствующий тип маркера.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Указывает интерфейс средства синтаксического анализа, а средство синтаксического анализа станет полностью вы сами. Тем не менее средство синтаксического анализа реализацию по умолчанию предоставляется в проекте Visual Studio языкового пакета. Для управляемого кода платформы управляемых пакетов (MPF) обеспечивает полную поддержку для выделения цветом текста.  
  
 Прежних версий языка службы реализованы как часть пакета VSPackage, но новой реализации возможностей службы языка можно выполнить с помощью расширений MEF. Дополнительные сведения о новых способ реализации Цветовая подсветка синтаксиса, в разделе [Пошаговое руководство: выделение текста](../../extensibility/walkthrough-highlighting-text.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API, как можно быстрее. Это повысит быстродействие языковой службы и позволяют воспользоваться преимуществами новых функций редактора.  
  
## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Действия, выполняемые с помощью редактора для выделения текста цветом  
  
1.  Редактор получает colorizer путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> объекта.  
  
2.  Вызывает редактор <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> метод, чтобы определить, нуждается ли colorizer состояние каждой строки, чтобы удовлетворять вне colorizer.  
  
3.  Если colorizer требует сохранения вне colorizer состояния, вызывает редактор <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> метод для получения состояния первой строки.  
  
4.  Для каждой строки в буфере вызывает редактор <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> метод, который выполняет следующие действия:  
  
    1.  Сканер для преобразования текста в маркеры передается строка текста. Каждый маркер указывает текст токена и тип маркера.  
  
    2.  Тип токена преобразуется в индекс в списке цветных элементов.  
  
    3.  Сведения о токене используется для заполнения массива таким образом, что каждый элемент массива соответствует символа в строке. Значений, хранящихся в массиве, индексы в список цветных элементов.  
  
    4.  Для каждой строки возвращается состояние в конце строки.  
  
5.  Если colorizer требует сохранения состояния, редактор кэширует состояние для этой строки.  
  
6.  Редактор отображает строку текста, с помощью сведений, возвращаемых из <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> метод. Для этого необходимо выполнить следующие действия:  
  
    1.  Для каждого символа в строке возвращается индекс цветного элемента.  
  
    2.  Если с помощью цветные элементы по умолчанию, доступ к редактора цветные элементы списка.  
  
    3.  В противном случае вызов службы языка <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> метод, чтобы получить цветного элемента.  
  
    4.  Используйте сведения в цветного элемента для отрисовки текста на экране.  
  
## <a name="managed-package-framework-colorizer"></a>Managed Package Framework Colorizer  
 Managed package framework (MPF) предоставляет все классы, которые необходимы для реализации colorizer. Следует наследовать класс службы языка <xref:Microsoft.VisualStudio.Package.LanguageService> класса и реализовать требуемые методы. Необходимо указать сканера и синтаксического анализа путем реализации <xref:Microsoft.VisualStudio.Package.IScanner> интерфейсов и получить экземпляр этого интерфейса от <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> метод (один из методов, которые должны быть реализованы в <xref:Microsoft.VisualStudio.Package.LanguageService> класса). Дополнительные сведения см. в разделе [синтаксис Раскраска в языковую службу прежних версий](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>См. также  
 [Как: использовать встроенные цветных элементов](../../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Цветные настраиваемые элементы](../../extensibility/internals/custom-colorable-items.md)   
 [Разработке службы языка для прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Цветовая маркировка синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)