---
title: Практическое руководство. Добавление команд в контекстное меню
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office menus, creating
- Office development in Visual Studio, context menus
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3b20b10a37908e2c9744aeac63bb3eda091da478
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60074496"
---
# <a name="how-to-add-commands-to-shortcut-menus"></a>Практическое руководство. Добавление команд в контекстное меню
  В этом разделе показано, как добавить команды в контекстное меню в приложении Office с помощью надстройки VSTO.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

### <a name="to-add-commands-to-shortcut-menus-in-office"></a>Добавление команд в контекстные меню в Office

1. Добавьте элемент **Лента (XML)** в проект уровня документа или надстройки VSTO. Дополнительные сведения см. в разделе [Как Приступая к настройке ленты](../vsto/how-to-get-started-customizing-the-ribbon.md). Увеличение

2. В**обозревателе решений**выберите файл **ThisAddIn.cs** или **ThisAddIn.vb**.

3. В строке меню выберите **Вид** > **Код**.

     Этот файл класса **ThisAddin** откроется в редакторе кода.

4. Добавьте следующий код в класс **ThisAddin** . Этот код переопределяет метод `CreateRibbonExtensibilityObject` и возвращает XML-класс ленты в приложение Office.

     [!code-csharp[Trin_WordAddIn_Menus#1](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#1)]
     [!code-vb[Trin_WordAddIn_Menus#1](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#1)]

5. В **обозревателе решений**выберите XML-файл ленты. По умолчанию является имя XML-файле ленты *Ribbon1.xml*.

6. В строке меню выберите **Вид** > **Код**.

     XML-файл ленты открывается в редакторе кода.

7. В редакторе кода добавьте XML, описывающий контекстное меню и элемент управления, который требуется добавить в контекстное меню.

     В следующем примере элементы управления "кнопка", "меню" и "коллекция" добавляются в контекстное меню для документа Word. Идентификатор элемента управления этого контекстного меню — ContextMenuText. Полный список элемента управления Office 2010 ярлык идентификации, см. в разделе [файлы справки Office 2010: Идентификаторы элементов управления интерфейса Office fluent пользователя](http://go.microsoft.com/fwlink/?LinkID=181052).

    ```xml
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

8. В **обозревателе решений**, выберите файл **MyRibbon.cs** или **MyRibbon.vb**.

9. Добавьте метод обратного вызова, `Ribbon1` класс для каждого элемента управления, который необходимо обработать.

     Следующий метод обратного вызова обрабатывает кнопку **My Button** . Этот код добавляет строку в активный документ в текущем положении курсора.

     [!code-vb[Trin_WordAddIn_Menus#2](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/ribbon1.vb#2)]
     [!code-csharp[Trin_WordAddIn_Menus#2](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/ribbon1.cs#2)]

## <a name="see-also"></a>См. также
- [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)
- [Пошаговое руководство: Создать контекстное меню для закладок](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
- [Настройка контекстных меню в Office 2010](http://go.microsoft.com/fwlink/?LinkId=182186)
