---
title: "XML-схемы и данные в настройках уровня документа | Документы Microsoft"
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
- XML schemas [Office development in Visual Studio]
- schemas [Office development in Visual Studio]
- XML [Office development in Visual Studio], XML schemas
- XML schemas [Office development in Visual Studio], about XML schemas and data
- Office development in Visual Studio, XML
ms.assetid: 74bd5773-6cb0-44fb-9738-75e2f2c6e48d
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d53a17484a350e361459f5c975ed3090779332bd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>XML-схемы и данные в настройках на уровне документа
  **Важные** сведения, изложенные в этом разделе, относящаяся к Microsoft Word, представленному исключительно для удобства и лиц и организаций, расположенных за пределами США и их территорий или с помощью или разработки программы, работающие на, продуктов Microsoft Word, лицензированные корпорацией Майкрософт до января 2010 года, когда Microsoft удален реализация конкретной функции, относящиеся к пользовательской XML из Microsoft Word. Эта информация, относящаяся к Microsoft Word нельзя прочитать или используемых отдельным лицам или организациям в Соединенных Штатах Америки или их территориях, которые используете или разработке программ, выполняемых на продукты Microsoft Word, лицензированные корпорацией Майкрософт после 10 января 2010 г. ; Эти продукты будут вести себя таким же, как продукты лицензированных до указанной даты или приобретенных и лицензированных за пределами США.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Microsoft Office Excel и Microsoft Office Word предоставляют возможность сопоставление схем и документов. Это позволяет упростить импорт и экспорт XML-данных из документа.  
  
 Visual Studio представляет сопоставляемые элементы схемы в настройках на уровне документа, как элементы управления в модели программирования. Для Excel Visual Studio добавляет поддержку для привязки элементов управления к данным в базах данных, веб-службы и объекты. Для Word и Excel Visual Studio добавляет поддержку панелей действий, которые можно использовать с документом схем для создания повышения эффективности взаимодействия пользователей с решениями. Дополнительные сведения см. в разделе [Actions Pane Overview](../vsto/actions-pane-overview.md).  
  
> [!NOTE]  
>  Нельзя использовать составные XML-схемы в решениях Excel.  
  
## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>Создаваемые объекты при присоединении схем к книгам Excel  
 Если присоединить схему к книге, Visual Studio автоматически создает несколько объектов и добавляет их в проект. Эти объекты не должны удаляться с помощью средств Visual Studio, поскольку они управляются с помощью Excel. Чтобы их удалить, уберите сопоставленные элементы с листа или отсоедините схему средствами Excel.  
  
 Существует два основных объекта:  
  
-   XML-схемы (XSD-файл). Для каждой схемы в книге Visual Studio добавляет схему в проект. Он отображается как элемент проекта с расширением XSD в **обозревателе решений**.  
  
-   Типизированный класс <xref:System.Data.DataSet>. Этот класс создается на основе схемы. Этот класс набора данных отображается в **представление классов**.  
  
## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>Создаваемые объекты при сопоставлении элементов схемы на листы Excel  
 При сопоставлении элемент схемы из **XML-источник** области задач на лист Visual Studio автоматически создает несколько объектов и добавляет их в проект:  
  
-   Элементы управления. Для каждого сопоставляемого объекта в книге <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> управления (для неповторяющихся элементов схемы) или <xref:Microsoft.Office.Tools.Excel.ListObject> элемента управления (повторяющиеся элементы схемы) создается в модели программирования. <xref:Microsoft.Office.Tools.Excel.ListObject> Управления можно удалить только путем удаления из книги сопоставлений и сопоставляемых объектов. Дополнительные сведения об элементах управления см. в разделе [ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md).  
  
-   BindingSource. При создании <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> путем сопоставления неповторяющегося элемента схемы в лист <xref:System.Windows.Forms.BindingSource> создается и <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> элемент управления привязан к <xref:System.Windows.Forms.BindingSource>. Необходимо привязать <xref:System.Windows.Forms.BindingSource> на экземпляр источника данных, который соответствует схеме, сопоставляемой документу, таком как экземпляр типизированного <xref:System.Data.DataSet> класс, который был создан. Создание привязки, задав <xref:System.Windows.Forms.BindingSource.DataSource%2A> и <xref:System.Windows.Forms.BindingSource.DataMember%2A> свойства, которые предоставляются в **свойства** окна.  
  
    > [!NOTE]  
    >  <xref:System.Windows.Forms.BindingSource> Не создается для <xref:Microsoft.Office.Tools.Excel.ListObject> объектов. Необходимо вручную связать <xref:Microsoft.Office.Tools.Excel.ListObject> к источнику данных, задав <xref:System.Windows.Forms.BindingSource.DataSource%2A> и <xref:System.Windows.Forms.BindingSource.DataMember%2A> свойства в **свойства** окна.  
  
### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>Office сопоставлены схемы и окна источников данных Visual Studio  
 Функциональность сопоставляемых схем Office и Visual Studio **источники данных** окна может помочь представить данные на листе Excel для создания отчетов или редактирования. В обоих случаях можно перетащить элементы данных на листе Excel. Оба метода создания элемента управления с данными, привязанными через <xref:System.Windows.Forms.BindingSource> с источником данных, такие как <xref:System.Data.DataSet> или веб-службы.  
  
> [!NOTE]  
>  При сопоставлении повторяющегося элемента схемы с листом, Visual Studio создает <xref:Microsoft.Office.Tools.Excel.ListObject>. <xref:Microsoft.Office.Tools.Excel.ListObject> Автоматически не привязан к данным с помощью <xref:System.Windows.Forms.BindingSource>. Необходимо вручную связать <xref:Microsoft.Office.Tools.Excel.ListObject> к источнику данных, задав <xref:System.Windows.Forms.BindingSource.DataSource%2A> и <xref:System.Windows.Forms.BindingSource.DataMember%2A> свойства в **свойства** окна.  
  
 В следующей таблице показаны некоторые различия между этими двумя методами.  
  
|XML-схемы|Источники данных - окно|  
|----------------|-------------------------|  
|Использует интерфейс Office.|Использует **источники данных** окна в Visual Studio.|  
|Включает встроенные функции Office для импорта и экспорта данных из XML-файлов.|Необходимо указать импорта и экспорта программными средствами.|  
|Необходимо написать код для заполнения данными сгенерированных элементов управления.|Элементы управления, добавленные из **источники данных** окно имеет код, автоматически созданный для их заполнения, и необходимые строки подключения при использовании серверов баз данных.|  
  
## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>Поведение при присоединении схем в документы Word  
 Объекты данных не создаются при добавлении схемы в документ Word, который используется в проекте Office на уровне документа. Тем не менее при сопоставлении элемента схемы в документ, создаются элементы управления. Тип элемента управления зависит от типа элемента сопоставления; повторяющиеся элементы генерируют <xref:Microsoft.Office.Tools.Word.XMLNodes> элементов управления и повторяющиеся элементы создания <xref:Microsoft.Office.Tools.Word.XMLNode> элементов управления. Дополнительные сведения см. в разделе [управления XMLNodes](../vsto/xmlnodes-control.md) и [управления XMLNode](../vsto/xmlnode-control.md).  
  
## <a name="deployment-of-solutions-that-include-xml-schemas"></a>Развертывание решений, содержащих XML-схемы  
 Необходимо создать программу установки для развертывания решения, использующего XML-схемы, которой сопоставлен документа. Программа установки должна зарегистрировать схему в библиотеке схем на компьютере пользователя. Если схема не зарегистрирована, решение по-прежнему будут работать, поскольку Word создает временную схему на основе элементов, которые находятся в документ при его открытии пользователем. Тем не менее пользователь не сможет выполнить проверку или сохранение схемы, которая использовалась для создания проекта. Дополнительные сведения об установщиках см. в разделе [развертывание приложений, служб и компонентов](/visualstudio/deployment/deploying-applications-services-and-components).  
  
 Также можно добавить код в проект, чтобы проверить ли схема в библиотеке и зарегистрирована. Если это не так, можно предупредить пользователя.  
  
 [!code-vb[Trin_VstcoreDataWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstcoreDataWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs#1)]  
  
## <a name="see-also"></a>См. также  
 [Как: сопоставление схем в документы Word в Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Практическое руководство. Сопоставление схем и листов в Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  