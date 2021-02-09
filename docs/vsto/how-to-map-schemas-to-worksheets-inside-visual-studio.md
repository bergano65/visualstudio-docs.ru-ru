---
title: Как сопоставлять схемы с листами в Visual Studio
description: Узнайте, как можно сопоставлять схему XML с Microsoft Office листом Excel, пока лист открыт в Visual Studio.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Excel worksheets
- Excel [Office development in Visual Studio], XML schemas
- worksheets [Office development in Visual Studio], XML schemas
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0e6d868655e3f697a7f659064026929568f2e400
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900856"
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>Как сопоставлять схемы с листами в Visual Studio
  Схему XML можно сопоставлять с листом, когда лист открыт в Visual Studio. Вы используете те же средства Microsoft Office Excel, которые используются, когда книга открыта вне Visual Studio. Проект Office создает те же объекты независимо от того, сопоставляется ли схема с листом до или после создания решения Excel.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> В решениях Excel нельзя использовать составные XML-схемы.

## <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>Привязка схемы XML к листу Excel в Visual Studio

1. Откройте книгу Excel или проект шаблона в Visual Studio.

2. Щелкните лист, чтобы переместить фокус в конструктор.

3. На ленте перейдите на вкладку **Разработчик** .

    > [!NOTE]
    > Если вкладка **Разработчик** не отображается, сделайте ее видимой. Дополнительные сведения см. в разделе [инструкции. Отображение вкладки разработчика на ленте](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. В группе **XML** щелкните **источник**.

     Откроется окно **XML-источник** .

5. В окне « **Источник XML** » щелкните элемент **карты XML**.

     Откроется диалоговое окно **карты XML** .

6. В диалоговом окне **карты XML** нажмите кнопку **Добавить**.

7. Перейдите к файлу схемы, выберите его и нажмите кнопку **Открыть**.

8. Нажмите кнопку **OK**.

     Схема представлена в окне « **Источник XML** ». В проекте на основе схемы создается типизированный объект, <xref:System.Data.DataSet> а <xref:System.Windows.Forms.BindingSource> создается.

9. Перетащите элементы из окна **источника XML** в места на листе, где нужно создать соответствующие элементы управления.

     Если перетащить неповторяющийся элемент схемы, проект Office создаст <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> элемент управления, который автоматически привязывается к <xref:System.Windows.Forms.BindingSource> .

     При перетаскивании повторяющегося элемента схемы проект Office создает <xref:Microsoft.Office.Tools.Excel.ListObject> элемент управления, который не привязывается автоматически к источнику данных. Дополнительные сведения см. [в разделе XML-схемы и данные в настройках уровня документа](../vsto/xml-schemas-and-data-in-document-level-customizations.md).

## <a name="see-also"></a>См. также раздел
- [Как сопоставлять схемы с документами Word в Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [XML-схемы и данные в настройках уровня документа](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
