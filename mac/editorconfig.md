---
title: EditorConfig
description: Использование файла editorconfig для обеспечения единообразного стиля написания кода в Visual Studio для Mac.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 26A0DE31-2FBF-4E1B-99FB-083111AA1680
ms.openlocfilehash: a2f813bee641b55b52ad3611c155bd273345ba73
ms.sourcegitcommit: 9e796d8a8b737ed9d5bf024db89b1abf99ea809b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/21/2018
ms.locfileid: "43224095"
---
# <a name="creating-and-editing-a-custom-editorconfig-file"></a>Создание и редактирование пользовательского файла EditorConfig

В Visual Studio для Mac в проект или решение можно добавить файл [EditorConfig](http://editorconfig.org/), чтобы обеспечить использование единообразного стиля написания кода всеми разработчиками, работающими с базой кода. Параметры, объявленные в файле EditorConfig, имеют приоритет над глобальными параметрами текстового редактора Visual Studio для Mac. Использование в проекте или в базе кода файла EditorConfig позволяет задать стиль написания кода, настройки и предупреждения для проекта. Поскольку этот файл является частью базы кода, он позволяет следить за тем, чтобы все пользователи придерживались принятых в проекте практик кодирования независимо от интегрированной среды разработки или редактора кода, в которых они работают.

Файлы [EditorConfig](http://editorconfig.org/) поддерживаются многими интегрированными средами разработки и редакторами кода, включая Visual Studio 2017. 

## <a name="supported-settings"></a>Поддерживаемые параметры

Редактор в Visual Studio для Mac поддерживает основной набор [свойств EditorConfig](http://editorconfig.org/#supported-properties):

- `indent_style`
- `indent_size`
- `tab_width`
- `end_of_line`
- `charset`
- `trim_trailing_whitespace`
- `insert_final_newline`
- `root`

Кроме того, EditorConfig поддерживает [соглашения о написании кода](https://docs.microsoft.com/visualstudio/ide/editorconfig-code-style-settings-reference) в C#.

## <a name="add-an-editorconfig-file-to-a-project"></a>Добавление файла EditorConfig в проект

### <a name="adding-a-new-editorconfig-file"></a>Добавление нового файла EditorConfig

1. Откройте проект в Visual Studio для Mac. Выберите решение или узел проекта, в который нужно добавить файл EditorConfig. При добавлении файла в каталог решения параметры .editorconfig применяются ко всем проектам в решении. 

2. Щелкните узел правой кнопкой мыши и выберите команду **Добавить > Новый файл**, чтобы открыть диалоговое окно **Новый файл**:

    ![Пункты меню содержимого](media/editorconfig-image0.png)

3. Выберите **Прочее > Пустой текстовый файл** и присвойте ему **имя** `.editorconfig`. Нажмите клавишу **Создать** для создания файла и откройте его в редакторе:

    ![Диалоговое окно "Новый файл"](media/editorconfig-image1.png)

    Когда элемент добавляется на уровне решения, он автоматически создается и помещается в папку **Элементы решения**:

    ![Элемент решения, отображаемый на панели решения](media/editorconfig-image1a.png)

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

4. Параметры из файла `.editorconfig` применяются к любому новому коду, который вы напишете, но уже существующий код для согласования с новыми параметрами может потребовать переформатирования. Чтобы применить параметры из файла `.editorconfig` к существующему исходному файлу, откройте этот файл и выберите в строке меню параметры **Правка > Формат > Форматировать документ**.

    ![Пункт меню "Форматировать документ"](media/editorconfig-image2.png)

### <a name="adding-an-existing-editorconfig-file"></a>Добавление существующего файла EditorConfig

Если вы работаете с проектом или решением, которое уже содержит файл `.editorconfig`, то для применения параметров не требуется никаких действий. Все новые строки кода форматируются в соответствии с параметрами, заданными в файле EditorConfig. 

Может потребоваться использование уже существующего файла `.editorconfig` в проекте. Чтобы добавить существующий файл, выполните следующие действия.

1. Щелкните папку, которую нужно добавить, правой кнопкой мыши и выберите параметры **Добавить > Добавить файлы…**.

2. Перейдите в каталог, где находится необходимый файл. 

3. Файлы, названия которых начинаются с `.` (например, `.editorconfig`), в macOS являются скрытыми, поэтому нажмите клавиши **Command+Shift+.**, чтобы сделать файл `.editorconfig` видимым.

4. Выберите файл `.editorconfig` и нажмите **Открыть**:

    ![Окно добавления нового файла](media/editorconfig-image3b.png)

5. Когда откроется следующее диалоговое окно, выберите вариант **Скопировать файл в каталог** и нажмите **ОК**:

    ![Параметры диалогового окна добавления файла в папку](media/editorconfig-image3.png)

### <a name="reflecting-editorconfig-settings"></a>Применение параметров .editorconfig

Как только вы добавите файл .EditorConfig в базу кода, весь новый код будет автоматически отформатирован в соответствии с заданными параметрами. К существующему коду параметры применяются автоматически только при форматировании базы кода.

Чтобы применить параметры из файла `.editorconfig`, выделите узел решения и выберите в строке меню параметры **Правка > Формат > Форматировать документ**.

![Форматирование документа из строки меню](media/editorconfig-image3a.png)

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

Можно иметь несколько файлов `.editorconfig` в одном решении. Visual Studio для Mac прочитывает файлы `.editorconfig` в решении сверху вниз, добавляя и переопределяя параметры в процессе операции. Это означает, что параметры в `.editorconfig`, _ближайшие_ к файлу, который вы редактируете, имеют приоритет. Параметры берутся из файла `.editorconfig`, который находится в той же папке (если она существует), затем из файла `.editorconfig` в родительской папке (если она существует) и т. д., пока не будет найдено значение `root=true`.  

Чтобы к этой части базы кода _не_ применялись параметры из любых файлов `.editorconfig` более высокого уровня, добавьте свойство `root=true` в самое начало файла `.editorconfig` более низкого уровня:

```EditorConfig
# top-most EditorConfig file
root = true
```