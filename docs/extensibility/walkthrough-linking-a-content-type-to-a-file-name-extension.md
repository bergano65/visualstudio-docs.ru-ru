---
title: 'Прохождение: Привязка типа содержимого к расширению имени файла (ru) Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 328be013b5d522938cd7450fc53d4866c632abb3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697082"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>Прохождение: Свяжите тип содержимого с расширением имени файла
Вы можете определить свой собственный тип содержимого и связать с ним расширение имени файла с помощью расширений рамочной инфраструктуры управления (MEF) редактора. В некоторых случаях расширение имени файла уже определяется языковой службой. Но, чтобы использовать его с MEF, вы все равно должны связать его с типом содержимого.

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, вы не устанавливаете Visual Studio SDK из центра загрузки. Он включен в качестве дополнительной функции в Visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, [см.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-mef-project"></a>Создание проекта MEF

1. Создайте проект СЗ VSIX. (В **диалоге нового проекта** выберите **Visual C / Расширяемость,** затем **VSIX Project**.) Назовите решение. `ContentTypeTest`

2. В файле **source.extension.vsixmanifest** перейдите на вкладку **Активы** и установите поле **типа** на **Microsoft.VisualStudio.MefComponent**, поле **исходного** кода для **проекта в текущем решении,** и поле **проекта** на название проекта.

## <a name="define-the-content-type"></a>Определение типа содержимого

1. Добавьте файл класса с именем `FileAndContentTypes`.

2. Добавьте ссылки на следующие сборки:

    1. System.ComponentModel.Composition

    2. Microsoft.VisualStudio.Text.Logic

    3. Microsoft.VisualStudio.CoreUtility

3. Добавьте `using` следующие директивы.

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Classification;
    using Microsoft.VisualStudio.Utilities;

    ```

4. Объявить статический класс, содержащий определения.

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {. . .}
    ```

5. В этом классе <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> экспортировать имя "спрятал" и объявить свое базовое определение "текстом".

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {
        [Export]
        [Name("hid")]
        [BaseDefinition("text")]
        internal static ContentTypeDefinition hidingContentTypeDefinition;
    }
    ```

## <a name="link-a-file-name-extension-to-a-content-type"></a>Связать расширение имени файла с типом содержимого

- Чтобы сопоставить этот тип содержимого с <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> расширением имени файла, вывесьте a, который имеет расширение *.hid* и тип содержимого "спрятал".

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {
         [Export]
         [Name("hid")]
         [BaseDefinition("text")]
        internal static ContentTypeDefinition hidingContentTypeDefinition;

         [Export]
         [FileExtension(".hid")]
         [ContentType("hid")]
        internal static FileExtensionToContentTypeDefinition hiddenFileExtensionDefinition;
    }
    ```

## <a name="add-the-content-type-to-an-editor-export"></a>Добавление типа содержимого в экспорт редактора

1. Создайте расширение редактора. Например, можно использовать расширение глифа, описанное в [Walkthrough: Создание глифа поля.](../extensibility/walkthrough-creating-a-margin-glyph.md)

2. Добавьте класс, определенный в этой процедуре.

3. При экспорте класса расширения <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> добавьте к нему тип "спрятался".

    ```csharp
    [Export]
    [ContentType("hid")]
    ```

## <a name="see-also"></a>См. также
- [Языковой сервис и точки расширения редактора](../extensibility/language-service-and-editor-extension-points.md)
