---
title: "Пошаговое руководство: Связывание типа контента с расширением имени файла | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] связать новое — тип содержимого расширение имени файла"
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# Пошаговое руководство: Связывание типа контента с расширением имени файла
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Можно определить собственный тип содержимого и связать его расширение имени файла с помощью расширения редактора Managed Extensibility Framework \(MEF\). В некоторых случаях расширение файла уже был определен службой языка; Тем не менее использовать его с MEF по\-прежнему необходимо связать его с типом содержимого.  
  
## Обязательные компоненты  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в установку Visual Studio. VS SDK также можно установить позже. Для получения дополнительной информации см. [Установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Создание проекта MEF  
  
1.  Создайте проект VSIX C\#. \(В **Новый проект** диалогового окна выберите **Visual C\# и расширяемость**, затем **проект VSIX**.\) Присвойте решению имя `ContentTypeTest`.  
  
2.  В **source.extension.vsixmanifest** файл, перейдите к **активы** и установите **тип** на **Microsoft.VisualStudio.MefComponent**,  **источника** на **проект в текущем решении**, и **проекта** поле имя проекта.  
  
## Определение типа содержимого  
  
1.  Добавьте файл класса с именем `FileAndContentTypes`.  
  
2.  Добавьте ссылки на следующие сборки:  
  
    1.  System.ComponentModel.Composition  
  
    2.  Microsoft.VisualStudio.Text.Logic  
  
    3.  Microsoft.VisualStudio.CoreUtility  
  
3.  Добавьте следующие `using` директивы.  
  
    ```c#  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Utilities;  
  
    ```  
  
4.  Объявите статический класс, содержащий определения.  
  
    ```c#  
    internal static class FileAndContentTypeDefinitions  
    {. . .}  
    ```  
  
5.  В этом классе экспорта <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> с именем «скрыто» и объявить его базовому определению, равным «text».  
  
    ```c#  
    internal static class FileAndContentTypeDefinitions  
    {  
        [Export]  
        [Name("hid")]  
        [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
    }  
    ```  
  
## Связывание расширение имени файла с типом содержимого  
  
-   Чтобы сопоставить расширение имени файла этого типа содержимого, экспортировать <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> имеет расширение «.hid» и тип содержимого «скрыто».  
  
    ```c#  
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
  
## Добавление типа содержимого для экспорта редактора  
  
1.  Создайте расширение редактора. Например, можно использовать модуль глиф margin, описанной в [Пошаговое руководство: Создание глифа поля](../extensibility/walkthrough-creating-a-margin-glyph.md).  
  
2.  Добавьте класс, определенный в этой процедуре.  
  
3.  При экспорте класс расширения, добавление <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> «скрыто» для его типа.  
  
    ```c#  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## См. также  
 [Служба языка и точек расширения редактора](../extensibility/language-service-and-editor-extension-points.md)