---
title: Как сопоставлять схемы с листами в Visual Studio
titleSuffix: ''
ms.custom: seodec18
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c8a0437b940953e89e24969314f63df34d223496
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538142"
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

8. Нажмите кнопку **ОК**.

     Схема представлена в окне « **Источник XML** ». В проекте на основе схемы создается типизированный объект, <xref:System.Data.DataSet> а <xref:System.Windows.Forms.BindingSource> создается.

9. Перетащите элементы из окна **источника XML** в места на листе, где нужно создать соответствующие элементы управления.

     Если перетащить неповторяющийся элемент схемы, проект Office создаст <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> элемент управления, который автоматически привязывается к <xref:System.Windows.Forms.BindingSource> .

     При перетаскивании повторяющегося элемента схемы проект Office создает <xref:Microsoft.Office.Tools.Excel.ListObject> элемент управления, который не привязывается автоматически к источнику данных. Дополнительные сведения см. [в разделе XML-схемы и данные в настройках уровня документа](../vsto/xml-schemas-and-data-in-document-level-customizations.md).

## <a name="see-also"></a>См. также
- [Как сопоставлять схемы с документами Word в Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [XML-схемы и данные в настройках уровня документа](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
