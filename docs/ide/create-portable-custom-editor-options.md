---
title: "Создание переносимых настраиваемых параметров редактора с EditorConfig | Документы Майкрософт"
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- editor
ms.assetid: 
caps.latest.revision: 29
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 46846db26bee30841e6cb35913d533b512d01ba0
ms.openlocfilehash: f377ada139d9c0e8b01b640cf603cf349dc1c3c3
ms.lasthandoff: 03/27/2017

---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>Создание переносимых настраиваемых параметров редактора с EditorConfig
Параметры текстового редактора в Visual Studio применяются ко всем проектам заданного типа. Так, например, измененный параметр текстового редактора C# применяется ко *всем* проектам C# в Visual Studio. Однако в некоторых случаях может потребоваться использовать соглашения, которые отличаются от ваших собственных настроек редактора. Это можно сделать с помощью файлов [EditorConfig](http://editorconfig.org/), предоставляющих общие параметры текстового редактора для каждого проекта. Параметры EditorConfig, которые содержатся в файле .editorconfig, добавляются в базу кода, заменяя глобальные параметры текстового редактора Visual Studio. Это означает, что каждую базу кода можно настроить для использования нужных вам параметров текстового редактора. Для использования этой возможности в Visual Studio подключаемый модуль не требуется.

## <a name="coding-consistency"></a>Согласованность при кодировании
Параметры в файлах EditorConfig позволяют поддерживать согласованность стилей и параметров написания кода для языка, например стиль отступа, интервал табуляции, символ конца строки, кодирование и т. д., в базе кода независимо от используемого редактора или интегрированной среды разработки. Например, при программировании на языке C#, если в базе кода существует соглашение о том, что отступы всегда состоят из пяти символов пробела, для документов используется кодировка UTF-8 и каждая строка всегда заканчивается CR/LF, а файл .editorconfig можно настроить для выполнения этих условий.

Соглашения для кодирования, используемые вами в личных проектах, могут отличаться от тех, которые действуют в командных проектах. Например, вы предпочитаете, чтобы при нажатии клавиши TAB во время кодирования добавлялся символ табуляции. Однако в команде может быть принято, чтобы при отступе вместо символа табуляции добавлялись четыре символа пробела. Файлы EditorConfig устраняют эту проблему, позволяя создавать конфигурацию для каждого сценария.

Поскольку параметры содержатся в файле в базе кода, они передаются вместе с этой базой кода. Параметры текстового редактора применяются при открытии файла кода в редакторе, совместимом с EditorConfig. Дополнительные сведения о файлах EditorConfig см. на веб-сайте [EditorConfig.org](http://editorconfig.org/). При редактировании большого количества файлов .editorconfig может быть полезно расширение [Языковая служба EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig).

## <a name="override-editorconfig-settings"></a>Переопределение параметров EditorConfig
При добавлении файла .editorconfig в папку в иерархии файлов его параметры применяются ко всем соответствующим файлам на этом уровне и ниже. Чтобы переопределить параметры EditorConfig для конкретного проекта или базы кода и использовать другие или переопределенные значения, отличные от значений файла .editorconfig верхнего уровня, просто добавьте файл .editorconfig на уровень, который требуется изменить.

![Иерархия EditorConfig](../ide/media/vside_editorconfig_hierarchy.png)

Новые параметры файла .editorconfig будут применяться к уровню, на котором он находится, и ко всем его вложенным файлам.

## <a name="supported-settings"></a>Поддерживаемые параметры
Редактор в Visual Studio поддерживает следующие значения основного набора параметров EditorConfig.
- indent_style
- indent_size
- tab_width
- end_of_line
- charset
- корневой
- [соглашения о стиле кода](../ide/editorconfig-code-style-settings-reference.md)

Параметры EditorConfig поддерживаются во всех языках, поддерживаемых Visual Studio, за исключением XML.

## <a name="example"></a>Пример
Ниже приведен пример, показывающий состояние отступа во фрагменте кода C# до и после добавления в проект файла .editorconfig. Параметр **Табуляции** в диалоговом окне **Параметры** текстового редактора Visual Studio задан для вывода символов пробела при нажатии клавиши TAB в коде.

![Параметр "Табуляция" в текстовом редакторе](../ide/media/vside_editorconfig_tabsetting.png)

Как и ожидалось, нажатие клавиши TAB в следующей сроке приводит к отступу строки путем добавления четырех дополнительных символов пробела.

![Код до использования EditorConfig](../ide/media/vside_editorconfig_before.png)

Добавим следующее в новый файл .editorconfig в проект. (Параметр `[*.cs]` означает, что это изменение будет применено только к CS-файлам в этом проекте.)

![Файл .editorconfig, добавленный в проект](../ide/media/vside_editorconfig_addconfig.png)

Теперь при нажатии клавиши TAB вместо пробелов будут применяться символы табуляции.

![TAB добавляет символ табуляции](../ide/media/vside_editorconfig_tab.png)

> [!NOTE]
>  Добавление файла .editorconfig в проект или базу кода не приведет к преобразованию существующих стилей в новые. Изменение будет применяться только к новым добавленным строкам. При удалении файла .editorconfig из проекта или базы кода необходимо перезагрузить файлы кода для параметров редактора, чтобы восстановить глобальные параметры. Все ошибки в файлах .editorconfig выводятся в окне ошибок в Visual Studio.

## <a name="support-editorconfig-for-your-language-service"></a>Поддержка EditorConfig для языковой службы

В большинстве случаев при реализации языковой службы Visual Studio не требуется выполнять никаких дополнительных действий для поддержки универсальных свойств EditorConfig. Редактор кода автоматически обнаруживает и считывает файл .editorconfig, открываемый пользователем, и задает соответствующие параметры текстового буфера и просмотра. Но в некоторых языковых службах во время редактирования или форматирования текста пользователем вместо глобальных параметров для таких элементов, как знаки табуляции и пробелы, используется параметр соответствующего контекстуального текстового представления. В этих случаях языковую службу нужно обновить для поддержки файлов EditorConfig.

В следующей таблице приведены изменения, необходимые для обновления языковой службы для поддержки файлов EditorConfig.

| Нерекомендуемый глобальный параметр, зависящий от языка | Заменяющий контекстный параметр |
| :------------- | :------------- |
| Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs или Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs | !textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId) или !textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId) |
| Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize или Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize | textBufferOptions.GetOptionValue(DefaultOptions. IndentSizeOptionId) или textView.Options.GetOptionValue(DefaultOptions. IndentSizeOptionId) |
| Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize или Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize | textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId) или textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId) |

# <a name="see-also"></a>См. также
[Создание переносимых настраиваемых параметров редактора с EditorConfig](create-portable-custom-editor-options.md)
