---
title: Пошаговое руководство. Связывание типа контента с расширением имени файла | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e179c47cc9a4ce5a1c9538340d31e0089255a34
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54953371"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>Пошаговое руководство. Связывание типа контента с расширением имени файла
Можно определить свой собственный тип содержимого и связать его расширение имени файла с помощью Managed Extensibility Framework (MEF) расширения редактора. В некоторых случаях расширение имени файла уже определен на языковой службе. Но, чтобы использовать его с MEF, необходимо по-прежнему связать его с типом содержимого.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не устанавливайте Visual Studio SDK в центре загрузки. Этот пакет включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установить пакет SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-mef-project"></a>Создание проекта MEF  
  
1.  Создайте проект VSIX C#. (В **новый проект** диалоговом окне выберите **Visual C# / Extensibility**, затем **проект VSIX**.) Назовите решение `ContentTypeTest`.  
  
2.  В **source.extension.vsixmanifest** файл, перейдите к **активы** и задайте **тип** поле **Microsoft.VisualStudio.MefComponent**, **источника** поле **проект в текущем решении**и **проекта** на имя проекта.  
  
## <a name="define-the-content-type"></a>Определить тип содержимого  
  
1.  Добавьте файл класса с именем `FileAndContentTypes`.  
  
2.  Добавьте ссылки на следующие сборки:  
  
    1.  System.ComponentModel.Composition  
  
    2.  Microsoft.VisualStudio.Text.Logic  
  
    3.  Microsoft.VisualStudio.CoreUtility  
  
3.  Добавьте следующий `using` директивы.  
  
    ```csharp  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Utilities;  
  
    ```  
  
4.  Объявите статический класс, который содержит определения.  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {. . .}  
    ```  
  
5.  В этом классе Экспорт <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> с именем «hid» и объявить его базового определения, чтобы быть «text».  
  
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
  
-   Чтобы сопоставить расширение имени файла данного типа содержимого, экспортировать <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> , имеет расширение *.hid* и тип содержимого «скрыто».  
  
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
  
## <a name="add-the-content-type-to-an-editor-export"></a>Добавление типа содержимого к экспорту редактора  
  
1.  Создайте расширение редактора. Например, можно использовать модуль глиф полей, описанные в [Пошаговое руководство: Создание глифа поля](../extensibility/walkthrough-creating-a-margin-glyph.md).  
  
2.  Добавьте в класс, определенный в этой процедуре.  
  
3.  При экспорте класс расширения, добавление <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> типа «hid», к нему.  
  
    ```csharp  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## <a name="see-also"></a>См. также  
 [Точки расширения редактора и служба языка](../extensibility/language-service-and-editor-extension-points.md)