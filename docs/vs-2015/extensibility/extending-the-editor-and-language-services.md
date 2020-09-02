---
title: Расширение редактора и языковых служб | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 085e1b5c1fbfbbaf5649966738f2864e0b72ed35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65674786"
---
# <a name="extending-the-editor-and-language-services"></a>Расширение редактора и языковых служб
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете добавить функции языковой службы (например, IntelliSense) в собственный редактор и расширить большинство функций редактора кода Visual Studio.  Полный список возможностей, которые можно расширить, см. в разделе [точки расширения языковой службы и редактора](../extensibility/language-service-and-editor-extension-points.md).  
  
 Большинство функций редактора расширяется с помощью Managed Extensibility Framework (MEF). Например, если расширяемая функция редактора является цветовым выделением синтаксиса, можно написать *часть компонента* MEF, определяющую классификации, для которых необходимо выделить различные цвета и способ их обработки. Редактор также поддерживает несколько расширений одной и той же функции.  
  
 Уровень представления редактора основан на Windows Presentation Framework (WPF). WPF предоставляет графическую библиотеку для гибкого форматирования текста, а также предоставляет визуализации, такие как графика и анимации.  
  
 Пакет SDK для Visual Studio предоставляет адаптеры, называемые *оболочками совместимости* , для поддержки пакетов VSPackage, написанных для более ранних версий. Тем не менее, если у вас уже есть пакет VSPackage, рекомендуется обновить его до новой технологии, чтобы получить лучшую производительность и надежность.  
  
## <a name="related-topics"></a>См. также  
  
|Заголовок|Описание|  
|-----------|-----------------|  
|[Начало работы с расширениями редактора и языковой службы](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Объясняет, как создать расширение для редактора.|  
|[Компоненты редактора](../extensibility/inside-the-editor.md)|Описание общей структуры редактора и список некоторых его функций.|  
|[Managed Extensibility Framework в редакторе](../extensibility/managed-extensibility-framework-in-the-editor.md)|Объясняется, как использовать Managed Extensibility Framework (MEF) с редактором.|  
|[Языковая служба и точки расширения редактора](../extensibility/language-service-and-editor-extension-points.md)|Перечисляет точки расширения редактора. Точки расширения представляют функции редактора, которые можно расширять.|  
|[Пошаговое руководство. Создание оформления представления, команд и параметров (направляющие столбцов)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Пошаговое руководство по созданию элемента оформления представления, который рисует строки гудие столбцов, чтобы обеспечить определенную ширину отображения кода.  Также демонстрируется чтение и запись параметров, а также объявление и реализация команд, которые можно вызывать из командного окна.|  
|[Импорт в редакторе](../extensibility/editor-imports.md)|Список служб, которые может импортировать расширение.|  
|[Адаптация кода прежних версий для редактора](../extensibility/adapting-legacy-code-to-the-editor.md)|Описание различных способов адаптации устаревшего кода (до Visual Studio 2010) для расширения редактора.|  
|[Миграция языковой службы прежних версий](../extensibility/internals/migrating-a-legacy-language-service.md)|Объясняется, как выполнить миграцию языковой службы на основе VSPackage.|  
|[Пошаговое руководство. Связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Показывает, как связать тип содержимого с расширением имени файла.|  
|[Пошаговое руководство. Создание глифа поля](../extensibility/walkthrough-creating-a-margin-glyph.md)|Показывает, как добавить значок в поле.|  
|[Пошаговое руководство. Выделение текста](../extensibility/walkthrough-highlighting-text.md)|Показывает, как использовать *теги* для выделения текста.|  
|[Пошаговое руководство. Структурирование](../extensibility/walkthrough-outlining.md)|Показывает, как добавить структуризацию для определенных типов фигурных скобок.|  
|[Пошаговое руководство. Отображение парных фигурных скобок](../extensibility/walkthrough-displaying-matching-braces.md)|Показывает, как выделить Парные фигурные скобки.|  
|[Пошаговое руководство. Отображение всплывающих подсказок для кратких сведений](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Показывает, как отображать всплывающие окна краткие сведения, описывающие элементы кода, такие как свойства, методы и события.|  
|[Пошаговое руководство. Отображение справки сигнатуры](../extensibility/walkthrough-displaying-signature-help.md)|Показывает, как отображать всплывающие окна, предоставляющие сведения о количестве и типах параметров в сигнатуре.|  
|[Пошаговое руководство. Отображение завершения операторов](../extensibility/walkthrough-displaying-statement-completion.md)|Показывает, как реализовать завершение операторов.|  
|[Пошаговое руководство. Реализация фрагментов кода](../extensibility/walkthrough-implementing-code-snippets.md)|Показывает, как реализовать расширение фрагментов кода.|  
|[Пошаговое руководство. Отображение предложений лампочки](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Показывает, как отображать лампочки для предложений кода.|  
|[Пошаговое руководство. Использование командной оболочки в расширении редактора](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Показывает, как связать команду меню в VSPackage с компонентом MEF.|  
|[Пошаговое руководство. Использование сочетания клавиш в расширении редактора](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Показывает, как связать ярлык меню в VSPackage с компонентом MEF.|  
|[Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Содержит сведения о Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](https://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Предоставляет сведения о Windows Presentation Foundation (WPF).|  
  
## <a name="reference"></a>Справочник  
 Редактор Visual Studio включает следующие пространства имен.  
  
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
