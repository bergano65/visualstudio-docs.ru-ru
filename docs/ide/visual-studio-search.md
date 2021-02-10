---
title: Поиск в Visual Studio
description: Сведения о том, как находить параметры, меню и элементы кода с помощью функции поиска в Visual Studio.
ms.date: 10/08/2020
ms.topic: how-to
helpviewer_keywords:
- environments [Visual Studio], navigation
- documents [Visual Studio], navigating
- IDE, navigation
- navigation [Visual Studio]
- files [Visual Studio], navigating between
- windows [Visual Studio], navigating
- Window.QuickLaunch
- IDE navigator
ms.assetid: 3870a8fd-4afa-4f1e-a811-9fdf41a9e82d
monikerRange: vs-2019
author: profexorgeek
ms.author: jusjohns
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 101875b3a600a71c832498d05073187d2cf0b774
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873909"
---
# <a name="use-visual-studio-search"></a>Поиск в Visual Studio

В интегрированной среде разработки (IDE) Visual Studio представлено множество меню, параметров и функций, которые не всегда легко запомнить. Функция поиска в Visual Studio реализована в виде единого поля, с помощью которого разработчики могут находить меню и параметры интегрированной среды разработки, а также выполнять поиск в коде. Благодаря ей начинающие и опытные разработчики, использующие Visual Studio, смогут легко находить нужные элементы интегрированной среды разработки и фрагменты кода.

Чтобы открыть поле поиска, нажмите клавиши **CTRL**+**Q** или щелкните поле ввода для поиска в Visual Studio, которое по умолчанию расположено рядом со строкой меню.

:::image type="content" source="media/visual-studio-search-cropped.png" alt-text="Поле поиска в Visual Studio" lightbox="media/visual-studio-search.png":::

> [!NOTE]
> Функция поиска Visual Studio выполняет команду `Window.QuickLaunch`, которая также может называться командой быстрого поиска или быстрого запуска.

В отличие от других функций поиска, таких как поиск в файлах или обозревателе решений, в результаты поиска в Visual Studio включаются функции интегрированной среды разработки, параметры меню, имена файлов и многие другие элементы. В следующих разделах описываются различные типы результатов, которые может возвращать функция поиска Visual Studio.

## <a name="search-menus-options-and-windows"></a>Поиск меню, параметров и окон

Поле поиска Visual Studio можно использовать для поиска настроек, параметров и других элементов конфигурации. Например, поиск по фразе *изменить тему* позволяет быстро найти и открыть диалоговое окно, в котором можно изменить цветовую тему Visual Studio, как показано на следующем снимке экрана.

:::image type="content" source="media/visual-studio-search-options.png" alt-text="Поиск настроек и параметров Visual Studio":::

> [!TIP]
> В большинстве случаев функция поиска в Visual Studio также будет предлагать сведения о меню, сочетаниях клавиш и расположении каждого элемента, представленного в результатах.

В поле поиска Visual Studio также можно искать команды и пункты меню. Например, чтобы быстро найти и выполнить команду "Очистить решение", введите в поле поиска *очистить реш*. В результатах поиска также приводятся сведения о том, где можно найти эту команду в меню, как показано на следующем снимке экрана.

:::image type="content" source="media/visual-studio-search-menu.png" alt-text="Поиск команд и пунктов меню в Visual Studio":::

Наконец, вы можете выполнить поиск окон или панелей, которые могли быть случайно закрыты. Например, чтобы найти и открыть окно обозревателя тестов, введите в поле поиска слово *тест*.

:::image type="content" source="media/visual-studio-search-window.png" alt-text="Поиск окон и панелей Visual Studio":::

## <a name="search-files-and-code"></a>Поиск файлов и кода

Функция поиска в Visual Studio также позволяет находить элементы решения по имени файла, коду, методу и другим совпадениям. На следующем снимке экрана в результате поиска по слову *markdown* были найдены файл MarkdownMetaExtractor.cs, класс `MarkdownMetaExtractor` и два метода в решении.

:::image type="content" source="media/visual-studio-search-files.png" alt-text="Поиск файлов в Visual Studio":::

Можно также выполнить поиск с использованием верблюжьего стиля. На следующем снимке экрана показаны результаты поиска по запросу *FSS*, которые включают файл, класс и метод **F** older **S** ize **S** canner.

:::image type="content" source="media/visual-studio-search-camel.png" alt-text="Поиск в Visual Studio в верблюжьем стиле":::

## <a name="see-also"></a>См. также

- [Команды Visual Studio](reference/visual-studio-commands.md)