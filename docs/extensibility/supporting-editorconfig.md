---
title: Расширение языковой службы для поддержки EditorConfig в Visual Studio | Документация Майкрософт
ms.date: 11/22/2017
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3061f1a2efdf05a775f563311ccfbb4c48c49bc9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53830895"
---
# <a name="supporting-editorconfig-for-your-language-service"></a>Поддержка EditorConfig для языковой службы

[EditorConfig](http://editorconfig.org/) файлы позволяют описывать Общие параметры текстового редактора, например размер отступа для каждого проекта. Дополнительные сведения о поддержке Visual Studio для файлов EditorConfig см. в разделе [Создание параметров переносимой редактора, с помощью EditorConfig](../ide/create-portable-custom-editor-options.md).

В большинстве случаев при реализации языковой службы Visual Studio не требуется выполнять никаких дополнительных действий для поддержки универсальных свойств EditorConfig. Редактор кода автоматически обнаруживает и считывает файл .editorconfig, открываемый пользователем, и задает соответствующие параметры текстового буфера и просмотра. Тем не менее некоторые службы языка для редактирования, такие как знаки табуляции и пробелы, необязательно использовать параметр соответствующего контекстуального текстового представления, а не с помощью глобальных параметров. В этих случаях языковую службу нужно обновить для поддержки файлов EditorConfig.

Ниже перечислены изменения, которые необходимы для обновления языковой службы для поддержки файлов EditorConfig, путем замены глобального _конкретного языка_ с параметром _контекстные_ параметр:

## <a name="indent-style"></a>Стиль отступов

Параметры конкретного языка | Контекстные параметры
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs|!textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)<br/>!textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)

## <a name="indent-size"></a>Размер отступа

Параметры конкретного языка | Контекстные параметры
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize|textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)

## <a name="tab-size"></a>Размер шага табуляции

Параметры конкретного языка | Контекстные параметры
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize|textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)

## <a name="see-also"></a>См. также

[Создание параметров переносимой редактора, с помощью EditorConfig](../ide/create-portable-custom-editor-options.md)  
[Расширение редактора и языковой службы](../extensibility/extending-the-editor-and-language-services.md)