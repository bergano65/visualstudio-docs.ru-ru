---
title: Диалоговое окно "Параметры", папка "Текстовый редактор", параметры "Все языки", "Полосы прокрутки"
description: Узнайте, как использовать страницу "Полосы прокрутки" в разделе "Все языки", чтобы изменить поведение по умолчанию для полос прокрутки редактора кода в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 10/25/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.Basic.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.CSharp.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.CoffeeScript.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.CSS.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.Dockerfile.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.F%2523.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.HQL.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.HTML.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.HTMLX.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.JavaScript.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.TypeScript.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.JSON.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.LESS.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.ResJSON.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.SCSS.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.SQL_Server_Tools.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.StreamAnalytics.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.U-SQL.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.XAML.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.XML.ScrollBars
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c9f9b53807d0ae2160798f29b98fa315c43c330c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841981"
---
# <a name="options-text-editor-all-languages-scroll-bars"></a>Диалоговое окно "Параметры", папка "Текстовый редактор", параметры "Все языки", "Полосы прокрутки"
Это диалоговое окно позволяет изменять стандартное поведение полосы прокрутки редактора кода. Чтобы отобразить эти параметры, выберите в меню **Сервис** пункт **Параметры**. В папке **Текстовый редактор** разверните вложенную папку **Все языки**, а затем выберите **Полосы прокрутки**.

> [!CAUTION]
> На этой странице задаются параметры по умолчанию для всех языков разработки. Сброс параметра в этом диалоговом окне приведет к возврату параметров полос прокрутки для всех языков к выбранному здесь значению. Чтобы изменить параметры текстового редактора только для одного языка, раскройте подпапку для этого языка и выберите соответствующие страницы параметров.

## <a name="show-horizontal-scroll-bar"></a>Показывать горизонтальную полосу прокрутки

Если этот флажок установлен, отображается горизонтальная полоса прокрутки, позволяющая выполнять прокрутку вправо и влево при просмотре элементов, выходящих за пределы видимой области редактора. Если горизонтальные полосы прокрутки недоступны, для прокрутки можно использовать клавиши управления курсором.

## <a name="show-vertical-scroll-bar"></a>Показывать вертикальную полосу прокрутки

Если этот флажок установлен, отображается вертикальная полоса прокрутки, позволяющая выполнять прокрутку вверх и вниз при просмотре элементов, выходящих за пределы видимой области редактора. Если вертикальные полосы прокрутки недоступны, для прокрутки можно использовать клавиши PAGE UP, PAGE DOWN и клавиши управления курсором.

## <a name="display"></a>Отображение

### <a name="show-annotations-over-vertical-scroll-bar"></a>Показывать заметки над вертикальной полосой прокрутки

Выберите, будет ли вертикальная полоса прокрутки отображать следующие заметки:

- изменения
- метки
- ошибки
- положение курсора.

> [!TIP]
> Параметр **Показывать метки** включает точки останова и закладки.

Посмотрите, как он работает. Для этого откройте большой файл кода и замените любой текст, который повторяется в нескольких местах в файле. На полосе прокрутки отображаются результаты замены, поэтому вы сможете отменить операцию, если изменили что-то не то.

О значении различных цветов и символов при редактировании кода можно узнать из статьи о [расширенной полосе прокрутки](/archive/blogs/cdnstudents/visual-studio-tips-and-tricks-enhanced-scroll-bar).

## <a name="behavior"></a>Поведение

У полосы прокрутки есть два режима: режим полосы и режим карты.

### <a name="use-bar-mode-for-vertical-scroll-bar"></a>Использовать режим полосы для вертикальной полосы прокрутки

В *режиме полосы* индикаторы заметок отображаются на полосе прокрутки. Если щелкнуть полосу прокрутки, вместо перехода к определенному месту в файле страница будет прокручена вверх или вниз.

### <a name="use-map-mode-for-vertical-scroll-bar"></a>Использовать режим карты для вертикальной полосы прокрутки

Если в *режиме карты* щелкнуть определенную точку полосы прокрутки, вместо простой прокрутки страницы вверх или вниз курсор переместится в это расположение в файле. На полосе прокрутки показано миниатюрное изображение строк кода. Вы можете задать ширину столбца карты, выбрав определенное значение для параметра **Обзор исходного кода**. Чтобы при наведении указателя на карту отображалось более широкое окно предварительного просмотра кода, выберите **Показывать подсказку предварительного просмотра**. Свернутые области затенены иначе. Они развертываются, если дважды щелкнуть их.

> [!TIP]
> Можно отключить миниатюрное представление кода в режиме карты. Для этого задайте для параметра **Обзор исходного кода** значение **Выкл.** Если установлен флажок **Показывать подсказку предварительного просмотра**, окно предварительного просмотра кода все так же будет отображаться в том расположении на полосе прокрутки, на которое вы наведите указатель. А если щелкнуть эту точку, курсор по-прежнему будет в нее перемещаться.

## <a name="see-also"></a>См. также раздел

- [Практическое руководство. Настройка полосы прокрутки](../how-to-track-your-code-by-customizing-the-scrollbar.md)