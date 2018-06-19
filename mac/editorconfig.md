---
title: EditorConfig
description: Использование файла editorconfig для обеспечения единообразного стиля написания кода в Visual Studio для Mac.
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 26A0DE31-2FBF-4E1B-99FB-083111AA1680
ms.openlocfilehash: 336ec5ef0779bcd67302bea7b51851dced531a7d
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
ms.locfileid: "33957393"
---
# <a name="creating-and-editing-a-custom-editorconfig-file"></a>Создание и редактирование пользовательского файла EditorConfig

В Visual Studio для Mac в проект или базу кода можно добавить файл [EditorConfig](http://editorconfig.org/), чтобы обеспечить использование единообразного стиля написания кода всеми разработчиками, работающими с базой кода. Параметры, объявленные в файле EditorConfig, имеют приоритет над глобальными параметрами текстового редактора Visual Studio. Использование в проекте или в базе кода файла EditorConfig позволяет задать стиль написания кода, настройки и предупреждения для проекта. Благодаря этому всем пользователям Visual Studio для Mac будет проще придерживаться рекомендациям проекта по написанию кода.

Файлы [EditorConfig](http://editorconfig.org/) поддерживаются многими интегрированными средами разработки и редакторами кода, включая Visual Studio 2017. 

## <a name="supported-settings"></a>Поддерживаемые параметры

Редактор в Visual Studio поддерживает основной набор [свойств EditorConfig](http://editorconfig.org/#supported-properties):

- `indent_style`
- `indent_size`
- `tab_width`
- `end_of_line`
- `charset`
- `trim_trailing_whitespace`
- `insert_final_newline`
- `root`

EditorConfig также поддерживает [форматирование стиля кода](https://docs.microsoft.com/visualstudio/ide/editorconfig-code-style-settings-reference) в C#.

## <a name="add-an-editorconfig-file-to-a-project"></a>Добавление файла EditorConfig в проект

### <a name="adding-a-new-editorconfig-file"></a>Добавление нового файла EditorConfig

1. Откройте проект в Visual Studio для Mac. Выберите узел проекта, в который необходимо добавить файлы.

2. Поле выбора узла проекта в строке меню выберите **Файл > Новый файл...**, чтобы открыть диалоговое окно **Новый файл**.

3. Выберите **Прочее > Пустой текстовый файл** и присвойте ему **имя** `.editorconfig`. Нажмите клавишу **Создать** для создания файла и откройте его в редакторе:

    ![Диалоговое окно "Новый файл"](media/editorconfig-image1.png)

4. Измените файл. Пример:

    ```EditorConfig
    # This file is the top-most EditorConfig file
    root = true

    # All Files
    [*]
    indent_style = space
    indent_size = 8
    insert_final_newline = false
    trim_trailing_whitespace = false

    [*.cs]
    csharp_new_line_before_open_brace = none
    ```

4. Добавление файла не приводит к автоматическому обновлению параметров. Чтобы применить параметры из файла `.editorconfig`, выделите узел проекта и выберите **Правка > Формат > Форматировать документ** из строки меню:

    ![Пункт меню "Форматировать документ"](media/editorconfig-image2.png)

### <a name="adding-an-existing-editorconfig-file"></a>Добавление существующего файла EditorConfig

Если вы работаете с проектом или решением, которое уже содержит файл `.editorconfig`, то для применения параметров не требуется никаких действий. Все новые строки кода форматируются в соответствии с параметрами, заданными в файле EditorConfig. Следует отметить, что хотя Visual Studio для Mac и учитывает файлы `.editorconfig` на уровне решения, но они могут не отображаться в области решения, поскольку файлы, начинающиеся с `.`, являются скрытыми в macOS.

Может потребоваться использование уже существующего файла `.editorconfig` в проекте. Чтобы добавить существующий файл, сначала необходимо включить отображение скрытых файлов в Finder, введя следующую команду в **Терминале**:

```bash
$ defaults write com.apple.Finder AppleShowAllFiles true
$ killall Finder
```

После того как файл `.editorconfig` станет видимым, перетащите его в узел проекта. Когда откроется следующее диалоговое окно, выберите вариант **Скопировать файл в каталог** и нажмите **ОК**:

![Пункт меню "Форматировать документ"](media/editorconfig-image3.png)

Чтобы применить параметры из файла `.editorconfig`, выделите узел проекта и выберите **Правка > Формат > Форматировать документ** из строки меню.

## <a name="editing-an-editorconfig-file"></a>Редактирование файла EditorConfig

В файлах EditorConfig используется простой формат для задания параметров, который описывается ниже с помощью предыдущего примера:


```EditorConfig
# This file is the top-most EditorConfig file
root = true

# All Files
[*]
indent_style = space
indent_size = 4
insert_final_newline = false
trim_trailing_whitespace = false

[*.cs]
csharp_new_line_before_open_brace = none
```

Установка параметра `root` в значение `true` пометит этот файл как файл верхнего уровня всей базы кода, и все файлы `.editorconfig` в проекте выше по уровню не будут учитываться, как это описано в разделе [Переопределение параметров EditorConfig](#override-editorconfig-settings).

Каждый раздел файла обозначается квадратными скобками (**[]**) и задает тип файлов, к которым будут применяться параметры данного раздела.

В приведенном выше примере некоторые параметры применяются ко всем файлам в проекте, а другие задаются только для файлов C#. На рисунках ниже изображен код до и после применения параметров из файла `.editorconfig`:

**До**:

![до применения параметров editorconfig](media/editorconfig-image4.png)

**После**:

![после применения параметров editorconfig](media/editorconfig-image5.png)

Дополнительные сведения о доступных параметрах EditorConfig см. в статье [Параметры соглашений о написании кода .NET в EditorConfig](https://docs.microsoft.com/visualstudio/ide/editorconfig-code-style-settings-reference) и в разделе [Supported Properties](http://editorconfig.org/#supported-properties) (Поддерживаемые свойства) официальной документации.

## <a name="override-editorconfig-settings"></a>Переопределение параметров EditorConfig

Можно иметь несколько файлов `.editorconfig` в одном решении. Visual Studio для Mac считывает файлы `.editorconfig` сверху вниз в решении, добавляя и переопределяя параметры по мере прохождения. Это означает, что приоритет будут иметь те параметры, которые находятся в файле `.editorconfig`, _ближайшем_ к файлу, с которым вы работаете. 

Чтобы к этой части базы кода _не_ применялись параметры из любых файлов `.editorconfig` более высокого уровня, добавьте свойство `root=true` в самое начало файла `.editorconfig` более низкого уровня:

```EditorConfig
# top-most EditorConfig file
root = true
```