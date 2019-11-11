---
title: Как кэшировать данные для использования в автономном режиме или на сервере
ms.date: 02/02/2017
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 551d27cf8d40f2e6e9c996b031fa6c4e0a233355
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189575"
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>Как кэшировать данные для использования в автономном режиме или на сервере
  Можно пометить элемент данных для кэширования в документе, чтобы он был доступен в автономном режиме. Это также делает возможным обработку данных в документе другим кодом, когда документ хранится на сервере.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Можно пометить элемент данных, который будет кэшироваться при объявлении элемента данных в коде, или, если вы используете <xref:System.Data.DataSet>, задав свойство в окне " **Свойства** ". При кэшировании элемента данных, который не является <xref:System.Data.DataSet> или <xref:System.Data.DataTable>, убедитесь, что он соответствует критериям кэширования в документе. Дополнительные сведения см. в разделе [кэширование данных](../vsto/caching-data.md).

> [!NOTE]
> Наборы данных, созданные с помощью Visual Basic, помеченные как **кэшированные** и заданные как **WithEvents** (включая наборы **данных** , перетаскиваемые из окна или **панели элементов** , для которых свойство **CacheInDocument** установлено в **значение true).** ) имеют префикс подчеркивания в именах в кэше. Например, при создании набора данных и наименовании его **Customers**имя <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> будет **_Customers** в кэше. При использовании <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> для доступа к этому кэшированному элементу необходимо указать **_Customers** вместо **Customers**.

### <a name="to-cache-data-in-the-document-using-code"></a>Кэширование данных в документе с помощью кода

1. Объявите открытое поле или свойство для элемента данных как член класса ведущего элемента в проекте, например класс `ThisDocumen`t в проекте Word или класс `ThisWorkbook` в проекте Excel.

2. Примените к элементу атрибут <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>, чтобы отметить элемент данных, который будет храниться в кэше данных документа. В следующем примере этот атрибут применяется к объявлению поля для <xref:System.Data.DataSet>.

     [!code-csharp[Trin_VstcoreDataExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#11)]

3. Добавьте код для создания экземпляра элемента данных и, если это применимо, для его загрузки из базы данных.

     Элемент данных загружается только при первом создании; После этого кэш остается в документе, и для его обновления необходимо написать другой код.

### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>Кэширование набора данных в документе с помощью окно свойств

1. Добавьте набор данных в проект с помощью средств в конструкторе Visual Studio, например, добавив источник данных в проект с помощью окна **Источники данных** .

2. Создайте экземпляр набора данных, если он еще не создан, и выберите экземпляр в конструкторе.

3. В окне **Свойства** присвойте свойству **CacheInDocument** **значение true**.

     Дополнительные сведения см. [в разделе Свойства в проектах Office](../vsto/properties-in-office-projects.md).

4. В окне **Свойства** задайте для свойства **модификаторы** значение **Public** (по умолчанию это **внутренний**).

## <a name="see-also"></a>См. также
- [Кэширование данных](../vsto/caching-data.md)
- [Руководство. программный кэш источника данных в документе Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [Пошаговое руководство. кэширование данных в документе, защищенном паролем](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Доступ к данным в документах на сервере](../vsto/accessing-data-in-documents-on-the-server.md)
- [Сохранение данных](../data-tools/save-data-back-to-the-database.md)
