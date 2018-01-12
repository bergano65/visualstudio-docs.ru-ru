---
title: "Как: кэширование данных для использования в автономном режиме или на сервере | Документы Microsoft"
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
helpviewer_keywords:
- data caching [Office development in Visual Studio], server use
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- offline data [Office development in Visual Studio]
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio], offline use
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 44130744af5d09e8582e2589bcefb7aca11b5ce2
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>Практическое руководство. Кэширование данных для автономного использования или для использования на сервере
  Можно пометить элемент данных кэшироваться в документе, чтобы оно было доступно вне сети. Это также позволяет для данных в документе должны обрабатываться другим кодом, когда документ хранится на сервере.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Можно пометить элемент данных, кэшируемых при объявлении элемента данных в коде, или, если вы используете <xref:System.Data.DataSet>, задав свойство **свойства** окна. Если элемент данных, не кэшируется <xref:System.Data.DataSet> или <xref:System.Data.DataTable>, убедитесь, что он соответствует критериям кэширования в документе. Для получения дополнительной информации см. [Caching Data](../vsto/caching-data.md).  
  
> [!NOTE]  
>  Наборы данных, созданные с помощью Visual Basic, которые помечены как **Cached** и **WithEvents** (включая наборы данных, при перетаскивании из **источники данных** окна или **Элементов** , имеющих **CacheInDocument** свойство **True**) содержат подчеркивания в своих именах в кэше. Например, если создать набор данных и назовите его **клиентов**, <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> будет называться **_Customers** в кэше. При использовании <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> для доступа к этой кэшированного элемента, необходимо указать **_Customers** вместо **клиентов**.  
  
### <a name="to-cache-data-in-the-document-using-code"></a>Кэширование данных в документ с помощью кода  
  
1.  Объявите открытое поле или свойство для элемента данных как член класса ведущего элемента в проекте, такие как `ThisDocumen`t класса в проекте Word или `ThisWorkbook` класс в проекте Excel.  
  
2.  Применить <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> атрибут для пометки элемента данных, хранящихся в кэше данных документа. В следующем примере этот атрибут применяется к объявлению поля для <xref:System.Data.DataSet>.  
  
     [!code-csharp[Trin_VstcoreDataExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#11)]  
  
3.  Добавьте код для создания экземпляра элемента данных и, если это применимо, чтобы загрузить ее из базы данных.  
  
     Элемент данных загружается только в том случае, когда он впервые создается; После этого в кэше остается с документом, и необходимо написать другой код, чтобы обновить ее.  
  
### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>Для кэширования набора данных в документе с помощью окна «Свойства»  
  
1.  Добавьте в проект набора данных с помощью средств в конструкторе Visual Studio, например, путем добавления источника данных в проект, использующий **источники данных** окна.  
  
2.  Создайте экземпляр набора данных, если вы еще не имеют один и выберите экземпляр в конструкторе.  
  
3.  В **свойства** задайте **CacheInDocument** свойства **True**.  
  
     Дополнительные сведения см. в разделе [свойства в проектах Office](../vsto/properties-in-office-projects.md).  
  
4.  В **свойства** задайте **модификаторы** свойства **открытый** (по умолчанию это **внутренний**).  
  
## <a name="see-also"></a>См. также  
 [Кэширование данных](../vsto/caching-data.md)   
 [Как: программное кэширование источника данных в документах Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [Как: кэширование данных в документе, защищенном паролем](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Доступ к данным в документах на сервере](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Сохранение данных](/visualstudio/data-tools/saving-data)  
  
  