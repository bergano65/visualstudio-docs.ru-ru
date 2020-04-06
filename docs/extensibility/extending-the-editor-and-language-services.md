---
title: Расширение служб редактора и языковых услуг (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 239c638ec32cc0dc2b2e275a5dbe0c4213a3423e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711715"
---
# <a name="extend-the-editor-and-language-services"></a>Расширить службы редактора и языка
Функции языкового сервиса (например, IntelliSense) можно добавить в собственный редактор и расширить большинство функций редактора кода Visual Studio.  Полный список того, что можно расширить, [см.](../extensibility/language-service-and-editor-extension-points.md)

 Вы расширяете большинство функций редактора, используя рамку управляемой расширения (MEF). Например, если функция редактора, которую вы хотите расширить, является окраской синтаксиса, можно написать *компонент meF,* определяющую классификацию, для которой вы хотите разную окраску, и то, как вы хотите, чтобы они были обработаны. Редактор также поддерживает несколько расширений одной и той же функции.

 Слой презентации редактора основан на рамочной системе презентаций Windows (WPF). WPF предоставляет графическую библиотеку для гибкого форматирования текста, а также предоставляет визуализации, такие как графика и анимация.

 Visual Studio SDK предоставляет адаптеры, известные как *очерки* для поддержки VSPackages, которые были написаны для более ранних версий. Тем не менее, если у вас есть существующий VSPackage, мы рекомендуем вам обновить его до новой технологии, чтобы получить лучшую производительность и надежность.

## <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Начало работы с языковой службой и расширением редактора](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Объясняет, как создать расширение для редактора.|
|[Внутри редактора](../extensibility/inside-the-editor.md)|Описывает общую структуру редактора и перечисляет некоторые его особенности.|
|[Рамочная система управляемой расширительности в редакторе](../extensibility/managed-extensibility-framework-in-the-editor.md)|Объясняет, как использовать рамочную программу управляемого расширительная доступность (MEF) с редактором.|
|[Языковой сервис и точки расширения редактора](../extensibility/language-service-and-editor-extension-points.md)|Перечисляет точки расширения редактора. Точки расширения представляют функции редактора, которые могут быть расширены.|
|[Прохождение: Создание украшения представления, команд и настроек (направляющие колонки)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Прогулки и объясняет создание поляна, которая рисует линии направляющих столбцов, чтобы помочь вам сохранить код на определенной ширине дисплея.  Также отображается настройки чтения и записи, а также декларирование и реализация команд, которые можно вызвать из окна командования.|
|[Импорт редактора](../extensibility/editor-imports.md)|Перечисляет службы, которые может импортировать расширение.|
|[Адаптация устаревшего кода в редактор](/visualstudio/extensibility/adapting-legacy-code-to-the-editor?view=vs-2015)|Объясняет различные способы адаптации устаревшего кода (pre-Visual Studio 2010) для расширения редактора.|
|[Миграция устаревшей языковой службы](../extensibility/internals/migrating-a-legacy-language-service.md)|Объясняет, как перенести языковую службу vsPackage.|
|[Прохождение: Свяжите тип содержимого с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Показывает, как связать тип содержимого с расширением имени файла.|
|[Прохождение: Создать маржиглиф](../extensibility/walkthrough-creating-a-margin-glyph.md)|Показывает, как добавить значок на маржу.|
|[Пошаговое прохождение: Выделите текст](../extensibility/walkthrough-highlighting-text.md)|Показывает, как использовать теги для *выделения* текста.|
|[Пошаговая прогулка: Добавить описание](../extensibility/walkthrough-outlining.md)|Показывает, как добавить с изложением для конкретных видов скобки.|
|[Прохождение: Отображение соответствующих скобки](../extensibility/walkthrough-displaying-matching-braces.md)|Показывает, как выделить соответствующие скобки.|
|[Прохождение: Отображение инструментов quickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Показывает, как отобразить всплывающие данные quickInfo, описывающие элементы кода, такие как свойства, методы и события.|
|[Прохождение: Помощь в отображении подписи](../extensibility/walkthrough-displaying-signature-help.md)|Показывает, как отобразить всплывающие данные, которые дают информацию о количестве и типах параметров в подписи.|
|[Пошаговое руководство. Отображение завершения операторов](../extensibility/walkthrough-displaying-statement-completion.md)|Показывает, как реализовать завершение оператора.|
|[Прохождение: Реализация фрагментов кода](../extensibility/walkthrough-implementing-code-snippets.md)|Показывает, как реализовать расширение фрагмента кода.|
|[Прохождение: Отображение лампочки предложения](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Показывает, как отобразить лампочки для кодовых предложений.|
|[Прохождение: Используйте команду оболочки с расширением редактора](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Показывает, как связать команду меню в VSPackage с компонентом MEF.|
|[Прохождение: Используйте клавишу ярлыка с расширением редактора](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Показывает, как связать ярлык меню в VSPackage с компонентом MEF.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Предоставляет информацию о Рамочной системе управляемого расширяемости (MEF).|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Предоставляет информацию о Фонде презентации Windows (WPF).|

## <a name="reference"></a>Справочник
 Редактор Visual Studio включает в себя следующие пространства имен.

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
