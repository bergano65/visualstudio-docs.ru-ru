---
title: 'Практическое: Локализация разметки ASPX | Документация Майкрософт'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- localizing XML [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 68e74f743c1c00bb940a89039e4fd5cfcf8e63e4
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119553"
---
# <a name="how-to-localize-aspx-markup"></a>Практическое: Локализация разметки ASPX
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] страницы (ASPX), обычно используют жестко заданные строковые значения. Чтобы локализовать эти строки, замените их выражения, ссылающиеся на локализованные ресурсы.  
  
## <a name="localize-aspx-markup"></a>Локализация разметки ASPX  
  
#### <a name="to-localize-aspx-markup"></a>Для локализации разметки ASPX  
  
1.  Добавьте отдельные файлы ресурсов: одного для языка по умолчанию и по одному для каждого языка локализации.  
  
     При локализации только разметку и не код, добавьте элемент проекта глобальные файлы ресурсов. При локализации кода и разметки, добавьте файл ресурсов элемента проекта.  
  
    1.  Чтобы добавить глобальный файл ресурсов, в **обозревателе решений**, откройте контекстное меню для элемента проекта SharePoint и выберите **добавить** > **новый элемент**. В разделе SharePoint **2010** узел, выберите **глобальные файлы ресурсов** шаблона.  
  
    2.  Чтобы добавить файл ресурсов в **обозревателе решений**, откройте контекстное меню для элемента проекта SharePoint и выберите **добавить** > **новый элемент**. В области **Visual Basic** или **Visual C#** узел, выберите **файл ресурсов** шаблона.  
  
    > [!NOTE]  
    >  Не забудьте добавить файлы ресурсов на элемент проекта SharePoint, чтобы включить свойство типа развертывания. Это свойство необходимо далее в этой процедуре. Если решение не содержит элемента проекта SharePoint, можно добавить пустой проект SharePoint и удалите значение по умолчанию *Elements.xml* файл.  
  
2.  Имя файла ресурсов языка по умолчанию по своему усмотрению, дополненный *.resx* расширение, например MyAppResources.resx. Используйте же базовое имя для каждого локализованного файла ресурсов, но добавить язык и региональные параметры [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Например, имя немецкий локализованных ресурсов *MyAppResources.de-DE.resx*.  
  
3.  Измените значение свойства **тип развертывания** свойства каждого файла ресурсов для **AppGlobalResource** целью вызвать их для развертывания в папке сервера App_GlobalResources.  
  
4.  При использовании ресурсов для локализации кода вместе с разметкой ASPX, оставьте значение **действие при построении** свойство как **внедренный ресурс**. Если вы используете файлы ресурсов для локализации разметки, при необходимости можно изменить значение свойства файлов, которые **содержимого**. Дополнительные сведения см. в разделе [решений SharePoint, локализовать](../sharepoint/localizing-sharepoint-solutions.md).  
  
5.  Откройте каждый файл ресурсов и добавьте локализованные строки, используя одинаковые идентификаторы строки в каждом файле.  
  
6.  В [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] разметки ASPX-страницы или элемента управления, замените жестко запрограммированные строки со значениями, используйте следующий формат:  
  
    ```aspx-csharp  
    <%$Resources:Resource File Name, String ID%>  
    ```  
  
     Например чтобы локализовать текст метки элемента управления на страницу приложения, необходимо изменить:  
  
    ```aspx-csharp  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="Label text"></asp:Label>  
    </asp:Content>  
    ```  
  
     в  
  
    ```aspx-csharp  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="<%$Resources:MyAppResources,String1%>"></asp:Label>  
    </asp:Content>  
    ```  
  
7.  Выберите **F5** ключ для сборки и запуска приложения.  
  
8.  В SharePoint необходимо измените язык по умолчанию.  
  
     Локализованные строки будут отображаться в приложении. Чтобы отобразить локализованные ресурсы, на сервер SharePoint должен иметь установлен языковой пакет, соответствующий файл ресурсов языка и региональных параметров.  
  
## <a name="see-also"></a>См. также
 [Локализация решений SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Практическое: Локализация компонента](../sharepoint/how-to-localize-a-feature.md)   
 [Способ: добавить файл ресурсов](../sharepoint/how-to-add-a-resource-file.md)   
 [Практическое: локализация кода](../sharepoint/how-to-localize-code.md)  
  
