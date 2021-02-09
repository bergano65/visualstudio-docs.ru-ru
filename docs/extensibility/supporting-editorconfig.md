---
title: Расширение языковой службы для поддержки EditorConfig
description: Сведения об изменениях, внесенных в обновление языковой службы для поддержки файлов EditorConfig. Замените глобальный параметр, зависящий от языка, контекстным параметром.
ms.custom: SEO-VS-2020
ms.date: 11/22/2017
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8ddd7e0c7c1e2655f08b7b7113f43e14bbb37584
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914966"
---
# <a name="supporting-editorconfig-for-your-language-service"></a>Поддержка EditorConfig для языковой службы

Файлы [EditorConfig](https://editorconfig.org/) позволяют описывать общие параметры текстового редактора, такие как размер отступа, для каждого проекта. Дополнительные сведения о поддержке файлов EditorConfig в Visual Studio см. в статье [Создание параметров переносимого редактора с помощью EditorConfig](../ide/create-portable-custom-editor-options.md).

В большинстве случаев при реализации языковой службы Visual Studio не требуется выполнять никаких дополнительных действий для поддержки универсальных свойств EditorConfig. Редактор кода автоматически обнаруживает и считывает файл .editorconfig, открываемый пользователем, и задает соответствующие параметры текстового буфера и просмотра. Однако для таких изменений, как табуляция и пробелы, некоторые языковые службы перед использованием глобальных параметров должны использовать соответствующий контекстный режим представления текста. В этих случаях языковую службу нужно обновить для поддержки файлов EditorConfig.

Ниже приведены изменения, которые необходимо выполнить для обновления языковой службы для поддержки файлов EditorConfig. для этого замените глобальный _языковой_ параметр на _контекстно-зависимый_ .

## <a name="indent-style"></a>Стиль отступов

Параметры, зависящие от языка | Контекстные параметры
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs|!textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)<br/>!textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)

## <a name="indent-size"></a>Размер отступа

Параметры, зависящие от языка | Контекстные параметры
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize|textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)

## <a name="tab-size"></a>Размер интервала табуляции

Параметры, зависящие от языка | Контекстные параметры
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize|textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)

## <a name="see-also"></a>См. также раздел

- [Создание параметров переносимого редактора с помощью EditorConfig](../ide/create-portable-custom-editor-options.md)
- [Расширение редактора и языковых служб](../extensibility/extending-the-editor-and-language-services.md)
