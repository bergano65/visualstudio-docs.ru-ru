---
title: Расширение редактора и языковых служб | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 91eab151680d936c350c8c5745aec6c9fe86e47c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51723066"
---
# <a name="extending-the-editor-and-language-services"></a>Расширение редактора и языковых служб
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно добавить собственный редактор компонентов службы языка (например, технология IntelliSense) и расширить большинство функций уровней в редакторе кода Visual Studio.  Полный список можно расширить, см. в разделе [языковая служба и точки расширения редактора](../extensibility/language-service-and-editor-extension-points.md).  
  
 Большинство функций редактора расширения с помощью Managed Extensibility Framework (MEF). Например, если функцию редактора, который требуется расширить раскраску синтаксических конструкций, можно написать MEF *компонента* , определяющий классификации, для которых требуется настроить различные цвета и способ их обработки. Этот редактор также поддерживает несколько расширений разным функциям.  
  
 Уровень представления редактора основана Windows Presentation Framework (WPF). WPF предоставляет библиотеку графики для гибкой форматирования текста, а также визуализации, например графики и анимации.  
  
 Пакет SDK для Visual Studio содержит адаптеры, известный как *оболочек* для поддержки пакетов VSPackage, разработанные для более ранних версий. Тем не менее при наличии существующего пакета VSPackage, мы рекомендуем обновить его до новой технологии, чтобы получить более высокую производительность и надежность.  
  
## <a name="related-topics"></a>См. также  
  
|Заголовок|Описание:|  
|-----------|-----------------|  
|[Начало работы с расширениями редактора и языковой службы](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Объясняется, как создать расширение редактора.|  
|[Компоненты редактора](../extensibility/inside-the-editor.md)|Описание общей структуры редактора и перечислены некоторые из его компонентов.|  
|[Managed Extensibility Framework в редакторе](../extensibility/managed-extensibility-framework-in-the-editor.md)|В этой статье описывается использование Managed Extensibility Framework (MEF) с помощью редактора.|  
|[Языковая служба и точки расширения редактора](../extensibility/language-service-and-editor-extension-points.md)|Список точек расширения редактора. Точки расширения представляют возможности редактора, которые могут быть расширены.|  
|[Пошаговое руководство. Создание оформления представления, команд и параметров (направляющие столбцов)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Описывается и объясняется создание оформления представления, который рисует строки в столбце gudie помогает защищать кода для определенных ширины экрана.  Также показано, чтение и запись параметров, а также объявления и реализации команд, которые можно вызвать из командного окна.|  
|[Импорт в редакторе](../extensibility/editor-imports.md)|Список служб, которые можно импортировать расширения.|  
|[Адаптация кода прежних версий для редактора](../extensibility/adapting-legacy-code-to-the-editor.md)|Объясняет различные способы адаптировать устаревшего кода (предварительно Visual Studio 2010) для расширения редактора.|  
|[Миграция языковой службы прежних версий](../extensibility/internals/migrating-a-legacy-language-service.md)|Описывается процедура переноса VSPackage на основе языковой службы.|  
|[Пошаговое руководство. Связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Показано, как связывание типа контента с расширением имени файла.|  
|[Пошаговое руководство. Создание глифа поля](../extensibility/walkthrough-creating-a-margin-glyph.md)|В этом разделе показано добавление значка к полям.|  
|[Пошаговое руководство. Выделение текста](../extensibility/walkthrough-highlighting-text.md)|Демонстрируется использование *теги* для выделения текста.|  
|[Пошаговое руководство. Структурирование](../extensibility/walkthrough-outlining.md)|Показано, как добавить структурирование для определенных типов фигурных скобок.|  
|[Пошаговое руководство. Отображение парных фигурных скобок](../extensibility/walkthrough-displaying-matching-braces.md)|Показано, как для выделения парных фигурных скобок.|  
|[Пошаговое руководство. Отображение всплывающих подсказок для кратких сведений](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Показано, как отображать всплывающие окна кратких сведений, описывающих элементы кода, такие как свойства, методы и события.|  
|[Пошаговое руководство. Отображение справки сигнатуры](../extensibility/walkthrough-displaying-signature-help.md)|В этой статье демонстрируется отображение всплывающих окон, которые предоставляют сведения о количестве и типах параметров в сигнатуре.|  
|[Пошаговое руководство. Отображение завершения операторов](../extensibility/walkthrough-displaying-statement-completion.md)|Показан способ реализации завершение операторов.|  
|[Пошаговое руководство. Реализация фрагментов кода](../extensibility/walkthrough-implementing-code-snippets.md)|Показан способ реализации расширения фрагмента кода.|  
|[Пошаговое руководство. Отображение предложений лампочки](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|В этой статье демонстрируется отображение лампочки для предложения кода.|  
|[Пошаговое руководство. Использование командной оболочки в расширении редактора](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Показано, как связать команду меню в VSPackage с помощью компонента MEF.|  
|[Пошаговое руководство. Использование сочетания клавиш в расширении редактора](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Показано, как связать контекстное меню в VSPackage с помощью компонента MEF.|  
|[Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Сведения о Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](http://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Сведения о Windows Presentation Foundation (WPF).|  
  
## <a name="reference"></a>Ссылка  
 В редакторе Visual Studio включает в себя следующие пространства имен.  
  
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

