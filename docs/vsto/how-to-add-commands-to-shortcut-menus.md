---
title: 'Как: Добавление команды в контекстное меню | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office menus, creating
- Office development in Visual Studio, context menus
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0d1bf0aee988e194b51220588a710a4b5b8d66ec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-commands-to-shortcut-menus"></a>Практическое руководство. Добавление команд в контекстное меню
  В этом разделе показано, как добавить команды в контекстное меню в приложении Office с помощью надстройки VSTO.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
### <a name="to-add-commands-to-shortcut-menus-in-office"></a>Добавление команд в контекстные меню в Office  
  
1.  Добавьте элемент **Лента (XML)** в проект уровня документа или надстройки VSTO. Для получения дополнительной информации см. [How to: Get Started Customizing the Ribbon](../vsto/how-to-get-started-customizing-the-ribbon.md). Увеличение  
  
2.  В**обозревателе решений**выберите файл **ThisAddIn.cs** или **ThisAddIn.vb**.  
  
3.  В строке меню выберите **Вид**, **Код**.  
  
     Этот файл класса **ThisAddin** откроется в редакторе кода.  
  
4.  Добавьте следующий код в класс **ThisAddin** . Этот код переопределяет метод CreateRibbonExtensibilityObject и возвращает класс XML ленты в приложение Office.  
  
     [!code-csharp[Trin_WordAddIn_Menus#1](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#1)]
     [!code-vb[Trin_WordAddIn_Menus#1](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#1)]  
  
5.  В **обозревателе решений**выберите XML-файл ленты. По умолчанию XML-файл ленты называется Ribbon1.xml.  
  
6.  В строке меню выберите **Вид**, **Код**.  
  
     XML-файл ленты открывается в редакторе кода.  
  
7.  В редакторе кода добавьте XML, описывающий контекстное меню и элемент управления, который требуется добавить в контекстное меню.  
  
     В следующем примере элементы управления "кнопка", "меню" и "коллекция" добавляются в контекстное меню для документа Word. Идентификатор элемента управления этого контекстного меню — ContextMenuText. Полный список элемента управления контекстное Office 2010 см. в разделе [файлы справки Office 2010: Fluent идентификаторы в элемент управления пользовательского интерфейса Office](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?>  
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui">  
      <contextMenus>  
        <contextMenu idMso="ContextMenuText">  
          <button id="MyButton" label="My Button" insertBeforeMso="HyperlinkInsert" onAction="GetButtonID" />  
          <menu id="MySubMenu" label="My Submenu" >  
            <button id="MyButton2" label="Button on submenu" />  
          </menu>  
          <gallery id="galleryOne" label="My Gallery">  
            <item id="item1" imageMso="HappyFace" />  
            <item id="item2" imageMso="HappyFace" />  
            <item id="item3" imageMso="HappyFace" />  
            <item id="item4" imageMso="HappyFace" />  
          </gallery>  
        </contextMenu>  
      </contextMenus>  
    </customUI>  
    ```  
  
8.  В **обозревателе решений**, выберите файл **MyRibbon.cs** или **MyRibbon.vb**.  
  
9. Добавьте метод обратного вызова в класс `Ribbon1` для каждого элемента управления, который требуется обработать.  
  
     Следующий метод обратного вызова обрабатывает кнопку **My Button** . Этот код добавляет строку в активный документ в текущем положении курсора.  
  
     [!code-vb[Trin_WordAddIn_Menus#2](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/ribbon1.vb#2)]
     [!code-csharp[Trin_WordAddIn_Menus#2](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/ribbon1.cs#2)]  
  
## <a name="see-also"></a>См. также  
 [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)   
 [Пошаговое руководство: Создание контекстного меню для закладок](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Настройка контекстных меню в Office 2010](http://go.microsoft.com/fwlink/?LinkId=182186)  
  
  