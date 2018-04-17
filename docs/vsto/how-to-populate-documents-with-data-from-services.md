---
title: 'Как: Заполнение документов данными из служб | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- Web services [Office development in Visual Studio], populating documents
- data [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7d2d042e5ca30d8aea7fc152c457b380c7c7f4f2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-populate-documents-with-data-from-services"></a>Практическое руководство. Заполнение документов данными из служб
  Доступ к данным в проектах уровня документа для Microsoft Office работает точно так же, как в проектах Windows Forms. Вы используете те же средства и код для получения данных в ваше решение и даже можете отображать данные с помощью элементов управления Windows Forms. Кроме того, можно воспользоваться преимуществами элементов управления ведущего приложения, которые являются собственными объектами в Microsoft Office Excel и Microsoft Office Word, дополненными событиями и функциями привязки данных. Дополнительные сведения см. в разделе [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 В следующем примере показано, как добавить элементы управления с привязкой к данным в документы во время разработки. Пример добавления элементов управления с привязкой к данным в надстройки VSTO во время выполнения см. в разделе [Пошаговое руководство: привязки к данным из службы в VSTO надстройки проекта](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md).  
  
 ![ссылка на видео](../vsto/media/playvideo.gif "ссылку видео") связанные демонстрационные видеоролики см. в разделе [инструкции. взаимодействие с веб-службами из Microsoft Excel?](http://go.microsoft.com/fwlink/?LinkID=130284).  
  
### <a name="to-populate-a-document-level-project-with-data-from-a-web-service"></a>Заполнение проекта уровня документа данными из веб-службы  
  
1.  Откройте окно **Источники данных** и создайте источник данных для проекта. Дополнительные сведения см. в разделе [Добавление новых источников данных](/visualstudio/data-tools/add-new-data-sources).  
  
2.  Перетащите нужное поле или таблицу из окна **Источники данных** в ваш документ.  
  
     В документе создается элемент управления, создается объект <xref:System.Windows.Forms.BindingSource> , привязанный к классу объекта в проекте, и создаются классы для службы.  
  
3.  В коде создайте экземпляр класса веб-службы, к которой вы подключались на шаге 1.  
  
4.  Если имеются свойства, необходимые для взаимодействия с веб-службой, создайте экземпляры этих свойств.  
  
5.  Создайте и отправьте запрос данных с помощью методов, предоставляемых веб-службой, и экземпляров свойств, созданных на шаге 4.  
  
     Методы, которые можно использовать, зависят от веб-службы.  
  
6.  Назначьте данные, возвращенные из веб-службы, свойству <xref:System.Windows.Forms.BindingSource.DataSource%2A> объекта <xref:System.Windows.Forms.BindingSource>.  
  
 При запуске проекта элемент управления отображает первую запись в источнике данных. Вы можете включить прокрутку записей посредством обработки текущих событий, используя объекты в <xref:System.Windows.Forms.BindingSource>.  
  
## <a name="see-also"></a>См. также  
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Добавление новых источников данных](/visualstudio/data-tools/add-new-data-sources)   
 [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Как: заполнение листов данными из базы данных](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Как: Заполнение документов данными из объектов](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Как: Заполнение документов данными из базы данных](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Практическое руководство. Обновление источника данных с помощью данных из элемента управления ведущего приложения](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)  
  
  