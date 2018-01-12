---
title: "Как: Заполнение документов данными из базы данных | Документы Microsoft"
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
- documents, populating with data
- data, adding to documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0a5a88cf34e0710869aaf4ac82d78cb79b37ffde
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-populate-documents-with-data-from-a-database"></a>Практическое руководство. Заполнение документов данными из базы данных
  Доступ к данным в проектах уровня документа для Microsoft Office можно получить таким же образом, как при доступе к данным в проектах Windows Forms. Используйте те же средства и код для получения данных из базы данных в ваше решение. Также можно использовать элементы управления Windows Forms для отображения данных.  
  
 Кроме того, данные можно показать с помощью элементов управления ведущего приложения. Элементы управления ведущего приложения представляют собой управляемые объекты Microsoft Office Word, дополненные событиями и функциями привязки данных. Для получения дополнительной информации см. [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 В следующем примере показано, как добавить элементы управления с привязкой к данным в проекты на уровне документа с помощью конструктора. Пример добавления элементов управления с привязкой к данным в проектах надстройки VSTO во время выполнения см. в разделе [Пошаговое руководство: простая привязка данных в VSTO надстройки проекта](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).  
  
 ![ссылка на видео](../vsto/media/playvideo.gif "ссылку видео") связанные демонстрационные видеоролики см. в разделе [привязка данных к Word 2007 содержимого элементов управления с помощью средств Visual Studio для Office (3.0)](http://go.microsoft.com/fwlink/?LinkId=136785).  
  
## <a name="adding-a-control-to-a-document-at-design-time"></a>Добавление элемента управления в документ во время разработки  
  
#### <a name="to-populate-a-document-with-data-from-a-database"></a>Заполнение документа данными из базы данных  
  
1.  Откройте проект уровня документа Word в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] и откройте документ в конструкторе.  
  
2.  Откройте **источники данных** окно и создать источник данных из базы данных. Дополнительные сведения см. в разделе [Добавление новых подключений](../data-tools/add-new-connections.md).  
  
3.  Перетащите нужное поле из **источники данных** в ваш документ.  
  
 В документ добавляется элемент управления содержимым. Тип элемента управления содержимым зависит от типа данных выбранного поля. Для получения дополнительной информации см. [Content Controls](../vsto/content-controls.md).  
  
 Можно добавить другой элемент управления, выбрав поле данных в **источники данных** и выбрав другой элемент управления из раскрывающегося списка.  
  
## <a name="objects-in-the-project"></a>Объекты в проекте  
 Кроме элемента управления, в проект автоматически добавляются следующие объекты, связанные с данными.  
  
-   Типизированный набор данных, который инкапсулирует таблицы данных, подключенные к базе данных. Дополнительные сведения см. в разделе [средства набора данных в Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).  
  
-   Объект <xref:System.Windows.Forms.BindingSource>, который подключает элемент управления к типизированному набору данных. Для получения дополнительной информации см. [BindingSource Component Overview](/dotnet/framework/winforms/controls/bindingsource-component-overview).  
  
-   Адаптер таблицы, который подключает типизированный набор данных к базе данных. Дополнительные сведения см. в разделе [создайте и настройте адаптеры таблиц TableAdapter](../data-tools/create-and-configure-tableadapters.md).  
  
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
 [Как: обновления источника данных с данными из элемента управления ведущего приложения](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [С помощью локальной базы данных файлов решений Office](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Подключение к данным в приложениях Windows Forms](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Общие сведения о компоненте BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)  
  
  