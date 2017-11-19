---
title: "Как: заполнение листов данными из базы данных | Документы Microsoft"
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
- worksheets [Office development in Visual Studio], populating
- databases [Office development in Visual Studio], populating worksheets
- data [Office development in Visual Studio], adding to worksheets
ms.assetid: e9e37cf1-53ca-45d0-8409-5428be7f96c5
caps.latest.revision: "39"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3b7cfb842a0372d4410a0794ff8ade901af713b1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-populate-worksheets-with-data-from-a-database"></a>Практическое руководство. Заполнение листов данными из базы данных
  Доступ к данным в проектах Office уровня документа можно таким же образом, как получить доступ к данным в проектах Windows Forms. Вы используете те же средства и код для получения данных в ваше решение и даже можете отображать данные с помощью элементов управления Windows Forms. Кроме того можно воспользоваться преимуществами элементов управления ведущего приложения, которые являются собственными объектами в Microsoft Office Excel, дополненные событиями и функциями привязки данных. Для получения дополнительной информации см. [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 В следующем примере показано, как добавить элементы управления с привязкой к данным в проекты на уровне документа с помощью конструктора. Пример добавления элементов управления с привязкой к данным в проектах уровня приложения во время выполнения см. в разделе [Пошаговое руководство: сложная привязка данных в VSTO надстройки проекта](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md).  
  
 ![ссылка на видео](../vsto/media/playvideo.gif "ссылку видео") связанные демонстрационные видеоролики см. в разделе [как сделать I: передачи данных в лист Excel?](http://go.microsoft.com/fwlink/?LinkID=130277), и [практические советы использовать базы данных данные в Excel?](http://go.microsoft.com/fwlink/?LinkID=130287).  
  
## <a name="adding-a-data-bound-control-to-a-worksheet-at-design-time"></a>Добавление элемента управления с привязкой к данным на лист во время разработки  
  
#### <a name="to-populate-a-worksheet-with-data-from-a-database"></a>Заполнение листов данными из базы данных  
  
1.  Откройте проект уровня документа Excel в Visual Studio откройте лист в конструкторе.  
  
2.  Откройте окно **Источники данных** и создайте источник данных для проекта. Дополнительные сведения см. в разделе [Добавление новых подключений](../data-tools/add-new-connections.md).  
  
3.  Перетащите поле или таблицу из **источники данных** на лист.  
  
 Одно из следующих элементов управления создается на листе:  
  
-   При перетаскивании поля, <xref:Microsoft.Office.Tools.Excel.NamedRange> на листе создается элемент управления. Дополнительные сведения см. в разделе [управления NamedRange](../vsto/namedrange-control.md).  
  
-   При перетаскивании таблицы, <xref:Microsoft.Office.Tools.Excel.ListObject> на листе создается элемент управления. Для получения дополнительной информации см. [ListObject Control](../vsto/listobject-control.md).  
  
 Вы можете добавить другой элемент управления, выбрав таблицу или поле в **источники данных** и выбрав другой элемент управления из раскрывающегося списка.  
  
## <a name="objects-in-the-project"></a>Объекты в проекте  
 Кроме элемента управления, в проект автоматически добавляются следующие объекты, связанные с данными.  
  
-   Типизированный набор данных, который инкапсулирует таблицы данных, подключенные к базе данных. Дополнительные сведения см. в разделе [средства набора данных в Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).  
  
-   Объект <xref:System.Windows.Forms.BindingSource>, который подключает элемент управления к типизированному набору данных. Для получения дополнительной информации см. [BindingSource Component Overview](/dotnet/framework/winforms/controls/bindingsource-component-overview).  
  
-   Адаптер таблицы, который подключает типизированный набор данных к базе данных. Для получения дополнительной информации см. [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).  
  
-   TableAdapterManager, который используется для координации адаптеров таблицы в наборе данных для реализации иерархических обновлений. Дополнительные сведения см. в разделе [иерархическое обновление](../data-tools/hierarchical-update.md) и [TableAdapterManager ссылка](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).  
  
 При выполнении проекта элемент управления отображает первую запись в источнике данных. Вы можете использовать <xref:System.Windows.Forms.BindingSource>, чтобы позволить пользователям прокручивать записи.  
  
#### <a name="to-scroll-through-the-records"></a>Прокрутка записей  
  
-   Используйте методы <xref:System.Windows.Forms.BindingSource>, такие как <xref:System.Windows.Forms.BindingSource.MoveNext%2A> и <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.  
  
 Сведения о том, как отправлять обновления типизированному набору данных и базы данных см. в разделе [как: обновления источника данных с данными из элемента управления ведущего приложения](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
## <a name="see-also"></a>См. также  
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Добавление новых источников данных](/visualstudio/data-tools/add-new-data-sources)   
 [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Как: Заполнение документов данными из объектов](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Как: Заполнение документов данными из базы данных](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Как: Заполнение документов данными из служб](../vsto/how-to-populate-documents-with-data-from-services.md)   
 [Как: обновления источника данных с данными из элемента управления ведущего приложения](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Как I: передачи данных на лист Excel](http://go.microsoft.com/fwlink/?LinkID=130277)   
 [Инструкции. Использование базы данных в Excel?](http://go.microsoft.com/fwlink/?LinkID=130287)  
  
  