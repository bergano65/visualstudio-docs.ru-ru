---
title: Как выполнить Кэшировать данные для использования в автономном режиме или на сервере
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], server use
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- offline data [Office development in Visual Studio]
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio], offline use
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 671b4c18963be4f9c81e15fe33e5d68a410655c9
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/27/2018
ms.locfileid: "53804660"
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>Как выполнить Кэшировать данные для использования в автономном режиме или на сервере
  Можно пометить элемент данных должен кэшироваться в документе, чтобы он был доступен вне сети. Это также позволяет для данных в документе, чтобы управляться другой код, когда документ хранится на сервере.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Можно пометить элемент данных должен быть помещен в кэш при объявлении элемента данных в коде, или, если вы используете <xref:System.Data.DataSet>, задав свойство **свойства** окна. Если элемент данных, не кэшируется <xref:System.Data.DataSet> или <xref:System.Data.DataTable>, убедитесь, что он соответствует критерию для кэширования в документе. Дополнительные сведения см. в разделе [кэшировать данные](../vsto/caching-data.md).

> [!NOTE]
>  Наборы данных, созданных с помощью Visual Basic, которые помечены как **Cached** и **WithEvents** (включая наборы данных, при перетаскивании из **источников данных** окно или **Элементов** , имеющих **CacheInDocument** свойство значение **True**) содержат подчеркивания в своих именах в кэше. Например, если создать набор данных и назовите его **клиентов**, <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> будет называться **_Customers** в кэше. При использовании <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> для доступа к этой кэшированного элемента, необходимо указать **_Customers** вместо **клиентов**.

### <a name="to-cache-data-in-the-document-using-code"></a>Для кэширования данных в документе, с помощью кода

1.  Объявите открытое поле или свойство для элемента данных как член класса ведущего элемента в проекте, такие как `ThisDocumen`t класс в проекте Word или `ThisWorkbook` класс в проекте Excel.

2.  Применить <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> атрибут для пометки элемента данных для сохранения в кэше данных документа. В следующем примере этот атрибут применяется к объявлению поля для <xref:System.Data.DataSet>.

     [!code-csharp[Trin_VstcoreDataExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#11)]

3.  Добавьте код для создания экземпляра элемента данных и, если это применимо, загрузить ее из базы данных.

     Элемент данных загружается только в том случае, при ее создании; После этого в кэше остается с документом, и необходимо написать другой код, чтобы обновить его.

### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>Для кэширования набора данных в документе с помощью окна свойств

1.  Добавьте в проект набора данных с помощью инструментов в конструкторе Visual Studio, например, путем добавления источника данных в проект, использующий **источников данных** окна.

2.  Создайте экземпляр набора данных, если вы еще не сделали и выберите экземпляр в конструкторе.

3.  В **свойства** окне **CacheInDocument** свойства **True**.

     Дополнительные сведения см. в разделе [свойства в проектах Office](../vsto/properties-in-office-projects.md).

4.  В **свойства** окне **модификаторы** свойства **открытый** (по умолчанию, это **внутренний**).

## <a name="see-also"></a>См. также
 [Кэширование данных](../vsto/caching-data.md) [как: Программное кэширование источника данных в документах Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md) [как: Кэширование данных в документе, защищенном паролем](../vsto/how-to-cache-data-in-a-password-protected-document.md) [доступа к данным в документах на сервере](../vsto/accessing-data-in-documents-on-the-server.md) [сохранения данных](../data-tools/saving-data.md)
