---
title: "Как: Локализация разметки ASPX | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
manager: ghogen
ms.workload: office
ms.openlocfilehash: 99683e590a2bc6638a809bd3d14486c951a2ad02
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-localize-aspx-markup"></a>Практическое руководство. Локализация разметки ASPX
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)](.aspx) страницы обычно используют жестко запрограммированные значения строк. Чтобы локализовать эти строки, замените их выражения, ссылающиеся на локализованные ресурсы.  
  
## <a name="localizing-aspx-markup"></a>Локализация разметки ASPX  
  
#### <a name="to-localize-aspx-markup"></a>Локализация разметки ASPX  
  
1.  Добавьте отдельные файлы ресурсов: один для языка по умолчанию и по одному для каждого языка локализации.  
  
     При локализации только разметки, без кода, добавьте глобальный файл ресурсов элемента проекта. При локализации кода и разметки, добавьте файл ресурсов элемента проекта.  
  
    1.  Чтобы добавить глобальный файл ресурсов в **обозревателе решений**, откройте контекстное меню для элемента проекта SharePoint и нажмите кнопку **добавить**, **новый элемент**. В списке SharePoint **2010** узел, выберите **глобальный файл ресурсов** шаблона.  
  
    2.  Чтобы добавить файл ресурсов в **обозревателе решений**, откройте контекстное меню для элемента проекта SharePoint и нажмите кнопку **добавить**, **новый элемент**. В рамках одного **Visual Basic** или **Visual C#** узел, выберите **файл ресурсов** шаблона.  
  
    > [!NOTE]  
    >  Не забудьте добавить файлы ресурсов в элемент проекта SharePoint, чтобы включить свойство типа развертывания. Это свойство требуется далее в этой процедуре. Если решение не имеет элемента проекта SharePoint, можно добавить пустой проект SharePoint и удалите его файл Elements.xml по умолчанию.  
  
2.  Присвойте имя по своему усмотрению с расширением RESX, например MyAppResources.resx файла ресурсов для языка по умолчанию. Используйте же базовое имя для каждого локализованного файла ресурсов, но добавить язык и региональные параметры [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Например имя немецком MyAppResources.de-DE.resx локализованный ресурс.  
  
3.  Измените значение **тип развертывания** свойство для каждого файла ресурсов для **AppGlobalResource** можно развернуть папке сервера App_GlobalResources.  
  
4.  При использовании ресурсов для локализации кода вместе с разметкой ASPX, оставьте значение параметра **действие при построении** для каждого файла, как **внедренный ресурс**. При использовании файлов ресурсов только для локализации разметки можно дополнительно изменить значение свойства файлов, которые **содержимого**. Дополнительные сведения см. в разделе [локализация решений SharePoint](../sharepoint/localizing-sharepoint-solutions.md).  
  
5.  Откройте каждый файл ресурсов и добавьте локализованные строки, используя одинаковые идентификаторы строки в каждом файле.  
  
6.  В [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] разметки ASPX-страницу или элемента управления, замените жестко запрограммированных строк со значениями, используйте следующий формат:  
  
    ```  
    <%$Resources:Resource File Name, String ID%>  
    ```  
  
     Например для локализации текста для элемента управления label на страницу приложения, необходимо изменить:  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="Label text"></asp:Label>  
    </asp:Content>  
    ```  
  
     в  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="<%$Resources:MyAppResources,String1%>"></asp:Label>  
    </asp:Content>  
    ```  
  
7.  Нажмите клавишу F5, чтобы выполнить сборку и запуск приложения.  
  
8.  В SharePoint необходимо измените язык по умолчанию.  
  
     Локализованные строки отображаются в приложении. Для отображения локализованных ресурсов, сервере SharePoint необходимо установить языковой пакет, соответствующий файл ресурсов языка и региональных параметров.  
  
## <a name="see-also"></a>См. также  
 [Локализация решений SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Как: Локализация компонента](../sharepoint/how-to-localize-a-feature.md)   
 [Способ: добавьте файл ресурсов](../sharepoint/how-to-add-a-resource-file.md)   
 [Практическое руководство. Локализация кода](../sharepoint/how-to-localize-code.md)  
  
  