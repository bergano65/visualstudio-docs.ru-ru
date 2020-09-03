---
title: Пошаговое руководство. Связывание типа содержимого с расширением имени файла | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: beae9d0526cb9f2f294f2267a8da52d3ce3d8c08
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201998"
---
# <a name="walkthrough-linking-a-content-type-to-a-file-name-extension"></a>Пошаговое руководство. Связывание типа контента с расширением имени файла
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно определить собственный тип содержимого и связать с ним расширение имени файла с помощью расширений редактора Managed Extensibility Framework (MEF). В некоторых случаях расширение имени файла уже определено в языковой службе; Тем не менее, чтобы использовать его с MEF, необходимо связать его с типом содержимого.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Кроме того, пакет SDK для VS можно установить позже. Дополнительные сведения см. [в разделе Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Создание проекта MEF  
  
1. Создание проекта VSIX C#. (В диалоговом окне **Новый проект** выберите **Visual C#/Extensibility**, а затем **проект VSIX**.) Присвойте решению имя `ContentTypeTest` .  
  
2. В файле **source. extension. vsixmanifest** перейдите на вкладку **активы** и задайте для поля **Тип** значение **Microsoft. VisualStudio. MefComponent**, поле **источник** для **проекта в текущем решении**, а в поле **проект** — имя проекта.  
  
## <a name="defining-the-content-type"></a>Определение типа содержимого  
  
1. Добавьте файл класса с именем `FileAndContentTypes`.  
  
2. Добавьте ссылки на следующие сборки:  
  
    1. System.ComponentModel.Composition  
  
    2. Microsoft. VisualStudio. Text. Logic  
  
    3. Microsoft. VisualStudio. Кореутилити  
  
3. Добавьте следующие `using` директивы.  
  
    ```csharp  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Utilities;  
  
    ```  
  
4. Объявите статический класс, содержащий определения.  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {. . .}  
    ```  
  
5. В этом классе экспортируйте <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> с именем "HID" и объявите его базовое определение как "Text".  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {  
        [Export]  
        [Name("hid")]  
        [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
    }  
    ```  
  
## <a name="linking-a-file-name-extension-to-a-content-type"></a>Связывание расширения имени файла с типом содержимого  
  
- Чтобы отобразить этот тип содержимого в расширение имени файла, экспортируйте объект с <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> расширением. HID и типом содержимого HID.  
  
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
  
## <a name="adding-the-content-type-to-an-editor-export"></a>Добавление типа содержимого в экспорт редактора  
  
1. Создайте расширение редактора. Например, можно использовать расширение глифа поля, описанное в [разделе Пошаговое руководство. Создание глифа поля](../extensibility/walkthrough-creating-a-margin-glyph.md).  
  
2. Добавьте класс, определенный в этой процедуре.  
  
3. При экспорте класса расширения добавьте <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> к нему тип "HID".  
  
    ```csharp  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## <a name="see-also"></a>См. также:  
 [Языковая служба и точки расширения редактора](../extensibility/language-service-and-editor-extension-points.md)
