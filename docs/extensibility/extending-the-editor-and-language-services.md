---
title: Расширение редактора и языковые службы | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4113a033d4e1a2595f4a980405e1b39d57d60958
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="extending-the-editor-and-language-services"></a>Расширение редактора и языковые службы
Можно добавить собственный редактор языка службы компонентов (таких как технология IntelliSense) и расширить большинство возможностей в редакторе кода Visual Studio.  Можно расширить полный список см. в разделе [языковой службы и точек расширения редактора](../extensibility/language-service-and-editor-extension-points.md).  
  
 Большинство функций редактора расширить с помощью Managed Extensibility Framework (MEF). Например, если вы хотите расширить функцию редактора Цветовая подсветка синтаксиса, можно написать MEF *компонента* , определяющий классификации, для которых требуется различные цвета и способ их обработки. Этот редактор также поддерживает несколько расширений одной функции.  
  
 Уровень представления редактора основан Windows Presentation Framework (WPF). WPF предоставляет графическую библиотеку для гибкой форматирования текста, а также представления, например графики и анимации.  
  
 Пакет SDK для Visual Studio предоставляет адаптеров, известный как *оболочки* для поддержки пакетов VSPackage, написанные для предыдущих версий. Тем не менее при наличии существующего пакета VSPackage, рекомендуется обновить его до новой технологии, чтобы получить более высокую производительность и надежность.  
  
## <a name="related-topics"></a>См. также  
  
|Заголовок|Описание|  
|-----------|-----------------|  
|[Начало работы с расширениями редактора и языковой службы](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Объясняется, как создать расширение редактора.|  
|[Компоненты редактора](../extensibility/inside-the-editor.md)|Описание общей структуры редактора и перечислены некоторые из его компонентов.|  
|[Managed Extensibility Framework в редакторе](../extensibility/managed-extensibility-framework-in-the-editor.md)|Описание способов использования Managed Extensibility Framework (MEF) с помощью редактора.|  
|[Языковая служба и точки расширения редактора](../extensibility/language-service-and-editor-extension-points.md)|Список точек расширения редактора. Точки расширения представляют функций редактора, которые могут быть расширены.|  
|[Пошаговое руководство. Создание оформления представления, команд и параметров (направляющие столбцов)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Рассматриваются и объясняется создание оформления представления, который рисует строки в столбце gudie помогает защищать код для определенных ширины экрана.  Также показывает, чтение и запись параметров, а также объявления и реализации команд, которые можно вызвать из окна командной.|  
|[Импорт в редакторе](../extensibility/editor-imports.md)|Список служб, которые можно импортировать расширения.|  
|[Адаптация кода прежних версий в редактор](../extensibility/adapting-legacy-code-to-the-editor.md)|Описание различных способов адаптировать устаревшего кода (предварительно Visual Studio 2010) для расширения редактора.|  
|[Миграция языковой службы прежних версий](../extensibility/internals/migrating-a-legacy-language-service.md)|Описывается процедура переноса языковую службу на основе пакетов VSPackage.|  
|[Пошаговое руководство. Связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Показано, как связать тип содержимого расширение имени файла.|  
|[Пошаговое руководство. Создание глифа поля](../extensibility/walkthrough-creating-a-margin-glyph.md)|Показано, как добавить кнопку на поле.|  
|[Пошаговое руководство. Выделение текста](../extensibility/walkthrough-highlighting-text.md)|Показано, как использовать *теги* для выделения текста.|  
|[Пошаговое руководство. Структурирование](../extensibility/walkthrough-outlining.md)|Показано, как добавить структурирование для определенных типов фигурных скобок.|  
|[Пошаговое руководство. Отображение парных фигурных скобок](../extensibility/walkthrough-displaying-matching-braces.md)|Показано, как выделить парные фигурные скобки.|  
|[Пошаговое руководство. Отображение всплывающих подсказок для кратких сведений](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Показано, как отображать всплывающие окна краткие сведения, описывающие элементы кода, такого как свойства, методы и события.|  
|[Пошаговое руководство. Отображение справки сигнатуры](../extensibility/walkthrough-displaying-signature-help.md)|Показано, как отображать всплывающие окна, которые предоставляют сведения о количестве и типах параметров в сигнатуре.|  
|[Пошаговое руководство. Отображение завершения операторов](../extensibility/walkthrough-displaying-statement-completion.md)|Показано, как реализовать завершение операторов.|  
|[Пошаговое руководство. Реализация фрагментов кода](../extensibility/walkthrough-implementing-code-snippets.md)|Показано, как реализовать расширения фрагмента кода.|  
|[Пошаговое руководство. Отображение предложений лампочки](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Показывает порядок отображения лампочки код предложения.|  
|[Пошаговое руководство. Использование командной оболочки в расширении редактора](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Показано, как связать команду меню в VSPackage с помощью компонента MEF.|  
|[Пошаговое руководство. Использование сочетания клавиш в расширении редактора](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Показано, как связать контекстное меню в VSPackage с помощью компонента MEF.|  
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Предоставляет сведения о Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Предоставляет сведения о Windows Presentation Foundation (WPF).|  
  
## <a name="reference"></a>Ссылка  
 В редакторе Visual Studio включает следующие пространства имен.  
  
 <xref:Microsoft.VisualStudio.Language.Intellisense>  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification>  
  
 <xref:Microsoft.VisualStudio.Editor>  
  
 <xref:Microsoft.VisualStudio.Text>  
  
 <xref:Microsoft.VisualStudio.Text.Adornments>  
  
 <xref:Microsoft.VisualStudio.Text.Classification>  
  
 <xref:Microsoft.VisualStudio.Text.Differencing>  
  
 <xref:Microsoft.VisualStudio.Text.Document>  
  
 <xref:Microsoft.VisualStudio.Text.Editor>  
  
 <xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods>  
  
 <xref:Microsoft.VisualStudio.Text.Formatting>  
  
 <xref:Microsoft.VisualStudio.Text.IncrementalSearch>  
  
 <xref:Microsoft.VisualStudio.Text.Operations>  
  
 <xref:Microsoft.VisualStudio.Text.Outlining>  
  
 <xref:Microsoft.VisualStudio.Text.Projection>  
  
 <xref:Microsoft.VisualStudio.Text.Tagging>  
  
 <xref:Microsoft.VisualStudio.Utilities>