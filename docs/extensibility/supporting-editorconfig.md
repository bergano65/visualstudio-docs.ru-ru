---
title: Расширение языковой службы для поддержки EditorConfig в Visual Studio | Документы Microsoft
ms.custom: ''
ms.date: 11/22/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2aa80903b3e5ea2723ec576fa463161b8d003c93
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139478"
---
# <a name="supporting-editorconfig-for-your-language-service"></a>Поддержка EditorConfig языковой службы

[EditorConfig](http://editorconfig.org/) файлов позволяют описывать Общие параметры текстового редактора, таких как размер отступа для каждого проекта. Дополнительные сведения о поддержке EditorConfig файлы Visual Studio см. в разделе [Создание переносимой редактора параметров с помощью EditorConfig](../ide/create-portable-custom-editor-options.md).

В большинстве случаев при реализации языковой службы Visual Studio не требуется выполнять никаких дополнительных действий для поддержки универсальных свойств EditorConfig. Редактор кода автоматически обнаруживает и считывает файл .editorconfig, открываемый пользователем, и задает соответствующие параметры текстового буфера и просмотра. Однако для изменения, такие как знаки табуляции и пробелы, некоторые службы языка начать использовать параметр соответствующие контекстные текстовые представления, а не с помощью глобальных параметров. В этих случаях языковую службу нужно обновить для поддержки файлов EditorConfig.

Ниже перечислены изменения, необходимые для обновления языковой службы для поддержки EditorConfig файлы, заменив глобальный _языку_ вариант с _контекстные_ параметр:

## <a name="indent-style"></a>Стиль отступов

Параметры языка | Контекстные параметры
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs|!textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)<br/>!textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)

## <a name="indent-size"></a>Размер отступа

Параметры языка | Контекстные параметры
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize|textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)

## <a name="tab-size"></a>Размер шага табуляции

Параметры языка | Контекстные параметры
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize|textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)

## <a name="see-also"></a>См. также

[Создание переносимых редактора параметров, с помощью EditorConfig](../ide/create-portable-custom-editor-options.md)  
[Расширение служб редактора и язык](../extensibility/extending-the-editor-and-language-services.md)