---
title: 'Пошаговое руководство: Связывание типа контента с расширением имени файла | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f543992ba23e08be25d5c8206d2b5b0565d33948
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51739876"
---
# <a name="walkthrough-linking-a-content-type-to-a-file-name-extension"></a>Пошаговое руководство. Связывание типа контента с расширением имени файла
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно определить свой собственный тип содержимого и связать его расширение имени файла с помощью Managed Extensibility Framework (MEF) расширения редактора. В некоторых случаях расширение имени файла уже был определен на языковой службе; Тем не менее использовать его в MEF по-прежнему необходимо связать его с типом содержимого.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Создание проекта MEF  
  
1.  Создайте проект VSIX C#. (В **новый проект** диалоговом окне выберите **Visual C# / Extensibility**, затем **проект VSIX**.) Назовите решение `ContentTypeTest`.  
  
2.  В **source.extension.vsixmanifest** файл, перейдите к **активы** и задайте **тип** поле **Microsoft.VisualStudio.MefComponent**, **источника** поле **проект в текущем решении**и **проекта** на имя проекта.  
  
## <a name="defining-the-content-type"></a>Определение типа содержимого  
  
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
  
## <a name="linking-a-file-name-extension-to-a-content-type"></a>Связывание расширение имени файла с типом содержимого  
  
-   Чтобы сопоставить расширение имени файла данного типа содержимого, экспортировать <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> , имеет расширение «.hid» и тип содержимого «скрыто».  
  
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
  
## <a name="adding-the-content-type-to-an-editor-export"></a>Добавление типа содержимого к экспорту редактора  
  
1.  Создайте расширение редактора. Например, можно использовать модуль глиф полей, описанные в [Пошаговое руководство: создание глифа поля](../extensibility/walkthrough-creating-a-margin-glyph.md).  
  
2.  Добавьте в класс, определенный в этой процедуре.  
  
3.  При экспорте класс расширения, добавление <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> типа «hid», к нему.  
  
    ```csharp  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## <a name="see-also"></a>См. также  
 [Языковая служба и точки расширения редактора](../extensibility/language-service-and-editor-extension-points.md)

