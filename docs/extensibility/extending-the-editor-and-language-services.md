---
title: "Расширение редактора и языковые службы | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
caps.latest.revision: 22
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 4d04f4588b1005e9b5ccb42c6042d01aacb45710
ms.lasthandoff: 02/22/2017

---
# <a name="extending-the-editor-and-language-services"></a>Расширение редактора и языковые службы
Можно добавить собственный редактор функций службы языка (например, технология IntelliSense) и расширить большинство функций в редакторе кода Visual Studio.  Полный список можно расширить в разделе [языковой службы и точек расширения редактора](../extensibility/language-service-and-editor-extension-points.md).  
  
 Большинство функций редактора можно расширить с помощью Managed Extensibility Framework (MEF). Например, если функции редактора, который требуется расширить Цветовая подсветка синтаксиса, можно написать MEF *компонента* , определяющий категории, для которых необходимо различные цвета и способ их обработки. Редактор также поддерживает несколько расширений такие же возможности.  
  
 Уровень представления редактора основана Windows Presentation Framework (WPF). WPF предоставляет графической библиотеки для гибкой форматирование текста, а также представления, например графики и анимации.  
  
 Пакет SDK для Visual Studio предоставляет адаптеров, известный как *оболочки* для поддержки пакетов VSPackages, написанных для предыдущих версий. Тем не менее при наличии существующего VSPackage, рекомендуется обновить новую технологию, чтобы получить лучшую производительность и надежность.  
  
## <a name="related-topics"></a>Связанные разделы  
  
|Заголовок|Описание|  
|-----------|-----------------|  
|[Приступая к работе с расширениями редактора и языковой службы](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Объясняется, как создать расширение редактора.|  
|[В редакторе](../extensibility/inside-the-editor.md)|Описание общей структуры редактора и перечисляются некоторые из его компонентов.|  
|[Managed Extensibility Framework в редакторе](../extensibility/managed-extensibility-framework-in-the-editor.md)|Описание способов использования Managed Extensibility Framework (MEF) в редакторе.|  
|[Служба языка и точек расширения редактора](../extensibility/language-service-and-editor-extension-points.md)|Список точек расширения редактора. Точки расширения представляют функций редактора, которые могут быть расширены.|  
|[Пошаговое руководство: Создание оформления представления, команд и параметров (направляющие столбцов)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Рассматриваются и объясняется создание представления оформления, который рисует строки в столбце gudie помогает защищать кода для определенных ширины экрана.  Также показано, чтение и запись параметров, а также объявление и реализации команд, которые можно вызвать из окна команд.|  
|[Редактор Imports](../extensibility/editor-imports.md)|Список служб, которые можно импортировать расширения.|  
|[Адаптация кода прежних версий для редактора](../extensibility/adapting-legacy-code-to-the-editor.md)|Описание различных способов адаптировать устаревшего кода (предварительно Visual Studio 2010) для расширения редактора.|  
|[Миграция языковую службу для прежних версий](../extensibility/internals/migrating-a-legacy-language-service.md)|В этой статье описывается перенос языковую службу на основе VSPackage.|  
|[Пошаговое руководство: Связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Показано, как связывание типа контента с расширением имени файла.|  
|[Пошаговое руководство: Создание глифа поля](../extensibility/walkthrough-creating-a-margin-glyph.md)|Показано, как добавить значок для поля.|  
|[Пошаговое руководство: Выделение текста](../extensibility/walkthrough-highlighting-text.md)|Показано, как использовать *теги* для выделения текста.|  
|[Пошаговое руководство: структурирование](../extensibility/walkthrough-outlining.md)|Показано, как добавить структурирование для определенных типов фигурных скобок.|  
|[Пошаговое руководство: Отображение парные фигурные скобки](../extensibility/walkthrough-displaying-matching-braces.md)|Показано, как можно выделить парные фигурные скобки.|  
|[Пошаговое руководство: Отображение кратких сведений подсказки](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Показано, как отображать всплывающие окна кратких сведений, описывающих элементы кода, такие как свойства, методы и события.|  
|[Пошаговое руководство: Отображение справки сигнатуры](../extensibility/walkthrough-displaying-signature-help.md)|Показано, как отображать всплывающие окна, которые предоставляют сведения об количества и типов параметров в сигнатуре.|  
|[Пошаговое руководство. Отображение завершения операторов](../extensibility/walkthrough-displaying-statement-completion.md)|Показано, как реализовать завершения операторов.|  
|[Пошаговое руководство: Реализация фрагменты кода](../extensibility/walkthrough-implementing-code-snippets.md)|Показано, как реализовать расширения фрагмента кода.|  
|[Пошаговое руководство: Отображение лампочки предложения](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Показывает порядок отображения лампочки код предложения.|  
|[Пошаговое руководство: Использование командной оболочки в редакторе расширений](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Показано, как связать команду меню в VSPackage с компонент MEF.|  
|[Пошаговое руководство: Использование сочетаний клавиш в редакторе расширений](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Показано, как связать контекстное меню в VSPackage с компонент MEF.|  
|[Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Предоставляет сведения о Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](http://msdn.microsoft.com/Library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Сведения о Windows Presentation Foundation (WPF).|  
  
## <a name="reference"></a>Ссылка  
 В редакторе Visual Studio включает следующие пространства имен.  
  
 <xref:Microsoft.VisualStudio.Language.Intellisense></xref:Microsoft.VisualStudio.Language.Intellisense>  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification></xref:Microsoft.VisualStudio.Language.StandardClassification>  
  
 <xref:Microsoft.VisualStudio.Editor></xref:Microsoft.VisualStudio.Editor>  
  
 <xref:Microsoft.VisualStudio.Text></xref:Microsoft.VisualStudio.Text>  
  
 <xref:Microsoft.VisualStudio.Text.Adornments></xref:Microsoft.VisualStudio.Text.Adornments>  
  
 <xref:Microsoft.VisualStudio.Text.Classification></xref:Microsoft.VisualStudio.Text.Classification>  
  
 <xref:Microsoft.VisualStudio.Text.Differencing></xref:Microsoft.VisualStudio.Text.Differencing>  
  
 <xref:Microsoft.VisualStudio.Text.Document></xref:Microsoft.VisualStudio.Text.Document>  
  
 <xref:Microsoft.VisualStudio.Text.Editor></xref:Microsoft.VisualStudio.Text.Editor>  
  
 <xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods></xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods>  
  
 <xref:Microsoft.VisualStudio.Text.Formatting></xref:Microsoft.VisualStudio.Text.Formatting>  
  
 <xref:Microsoft.VisualStudio.Text.IncrementalSearch></xref:Microsoft.VisualStudio.Text.IncrementalSearch>  
  
 <xref:Microsoft.VisualStudio.Text.Operations></xref:Microsoft.VisualStudio.Text.Operations>  
  
 <xref:Microsoft.VisualStudio.Text.Outlining></xref:Microsoft.VisualStudio.Text.Outlining>  
  
 <xref:Microsoft.VisualStudio.Text.Projection></xref:Microsoft.VisualStudio.Text.Projection>  
  
 <xref:Microsoft.VisualStudio.Text.Tagging></xref:Microsoft.VisualStudio.Text.Tagging>  
  
 <xref:Microsoft.VisualStudio.Utilities></xref:Microsoft.VisualStudio.Utilities>
