---
title: 'Пошаговое руководство: Связывание тип содержимого с расширением | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cca12f7c04b51bcf2b695e00d9305a7feb72ebc4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-linking-a-content-type-to-a-file-name-extension"></a>Пошаговое руководство: Связывание тип содержимого с расширением имени файла
Можно определить собственные типы содержимого и связать его расширение имени файла с помощью редактора расширений Managed Extensibility Framework (MEF). В некоторых случаях расширение файла уже было определено с языковую службу; Тем не менее для использования с MEF по-прежнему необходимо связать его с типом содержимого.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки Майкрософт. Он включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Создание проекта MEF  
  
1.  Создайте проект VSIX C#. (В **новый проект** диалогового окна выберите **Visual C# / Extensibility**, затем **проект VSIX**.) Присвойте решению имя `ContentTypeTest`.  
  
2.  В **source.extension.vsixmanifest** файл, последовательно выберите пункты **активы** и задайте **тип** на **Microsoft.VisualStudio.MefComponent**, **источника** на **проект в текущем решении**и **проекта** поле имя проекта.  
  
## <a name="defining-the-content-type"></a>Определение типа контента  
  
1.  Добавьте файл класса и назовите его `FileAndContentTypes`.  
  
2.  Добавьте ссылки на следующие сборки:  
  
    1.  System.ComponentModel.Composition  
  
    2.  Microsoft.VisualStudio.Text.Logic  
  
    3.  Microsoft.VisualStudio.CoreUtility  
  
3.  Добавьте следующие `using` директивы.  
  
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
  
5.  В этом классе экспорта <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> с именем «скрыто» и объявить его базовому определению, как «текст».  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {  
        [Export]  
        [Name("hid")]  
        [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
    }  
    ```  
  
## <a name="linking-a-file-name-extension-to-a-content-type"></a>Связывание расширение имени файла с типом содержимого  
  
-   Чтобы сопоставить расширение имени файла этого типа содержимого, экспортировать <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> , имеющий расширение «.hid» и тип содержимого «скрыто».  
  
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
  
## <a name="adding-the-content-type-to-an-editor-export"></a>Добавление типа содержимого Экспорт редактора  
  
1.  Создайте расширение редактора. Например, можно использовать расширение глиф поля, описанной в [Пошаговое руководство: создание глиф поля](../extensibility/walkthrough-creating-a-margin-glyph.md).  
  
2.  Добавьте класс, который определен в этой процедуре.  
  
3.  При экспорте класса модуля, добавьте <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> типа «скрыто» к нему.  
  
    ```csharp  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## <a name="see-also"></a>См. также  
 [Языковая служба и точки расширения редактора](../extensibility/language-service-and-editor-extension-points.md)