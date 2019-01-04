---
title: XML-схемы и данные в настройках уровня документа
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio]
- schemas [Office development in Visual Studio]
- XML [Office development in Visual Studio], XML schemas
- XML schemas [Office development in Visual Studio], about XML schemas and data
- Office development in Visual Studio, XML
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dd9f91b8b0fbf786bc06687df14dfe29d579610a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53966762"
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>XML-схемы и данные в настройках уровня документа
  **Важные** сведения, изложенные в этом разделе, касающиеся Microsoft Word, представленных исключительно для преимущество и лиц и организаций, расположенных за пределами США и их территорий или использующие или разработки программ, выполняемых на, продукты Microsoft Word, лицензированные корпорацией Майкрософт до января 2010 г, при удалении реализация конкретной функции в Microsoft связана с пользовательским XML-из Microsoft Word. Эти сведения, касающиеся Microsoft Word может не читают или используют отдельным лицам или организациям в Соединенных Штатах Америки или их территориях, которые используете, или разработке программ, выполняемых на продукты Microsoft Word, лицензированные корпорацией Майкрософт, начиная с 10 января 2010 г. ; Эти продукты, будет вести себя так же, как продукты до этой даты или приобретенных и лицензируются для использования за пределами США.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Microsoft Office Excel и Microsoft Office Word предоставляют возможность сопоставление схем и документов. Это позволяет упростить импорт и экспорт XML-данных из документа.

 Visual Studio предоставляет сопоставленных элементов схемы в настройках уровня документа, как элементы управления в модели программирования. Для Excel Visual Studio добавляет поддержку для привязки элементов управления к данным в базах данных, веб-служб и объектов. Для Word и Excel Visual Studio добавляет поддержку панелей действий, которые можно использовать с документом схем для создания взаимодействия пользователей с решениями. Дополнительные сведения см. в разделе [Общие сведения о панели действий](../vsto/actions-pane-overview.md).

> [!NOTE]
>  Составные XML-схемы нельзя использовать в решениях Excel.

## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>Объекты, созданные при присоединении схем к книгам Excel
 При присоединении схемы с книгой, Visual Studio автоматически создает несколько объектов и добавляет их в проект. Эти объекты не должны удаляться с помощью средств Visual Studio, так как они управляются с помощью Excel. Чтобы удалить их, удалите сопоставленные элементы из рабочего листа или отсоедините схему с помощью средств Excel.

 Существует два основных объекта:

-   Схемы XML (XSD-файл). Для каждой схемы в книге Visual Studio добавляет в проект схемы. Он отображается как элемент проекта с расширением XSD в **обозревателе решений**.

-   Типизированный класс <xref:System.Data.DataSet>. Этот класс создается на основе схемы. Этот класс набора данных отображается в **представление классов**.

## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>Объекты, созданные при сопоставлении элементов схемы с листов Excel
 При сопоставлении элемент схемы из **источник XML** области задач на лист Visual Studio автоматически создает несколько объектов и добавляет их в проект:

-   Элементы управления. Для каждого сопоставляемого объекта в книге <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> управления (для неповторяющихся элементов схемы) или <xref:Microsoft.Office.Tools.Excel.ListObject> элемента управления (для повторяющихся элементов схем) создается в модели программирования. <xref:Microsoft.Office.Tools.Excel.ListObject> Управления можно удалить, только удалив сопоставления и сопоставленными объектами из книги. Дополнительные сведения об элементах управления см. в разделе [ведущие элементы и размещать элементы управления](../vsto/host-items-and-host-controls-overview.md).

-   BindingSource. При создании <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> путем сопоставления неповторяющегося элемента схемы в лист, <xref:System.Windows.Forms.BindingSource> создается и <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> привязан элемент управления <xref:System.Windows.Forms.BindingSource>. Необходимо привязать <xref:System.Windows.Forms.BindingSource> для экземпляра источника данных, которые соответствуют схеме сопоставляются с документа, например: экземпляр типизированного <xref:System.Data.DataSet> класс, который был создан. Создать привязку, задав <xref:System.Windows.Forms.BindingSource.DataSource%2A> и <xref:System.Windows.Forms.BindingSource.DataMember%2A> свойства, которые представлены на **свойства** окна.

    > [!NOTE]
    >  <xref:System.Windows.Forms.BindingSource> Не создается для <xref:Microsoft.Office.Tools.Excel.ListObject> объектов. Необходимо вручную связать <xref:Microsoft.Office.Tools.Excel.ListObject> к источнику данных, задав <xref:System.Windows.Forms.BindingSource.DataSource%2A> и <xref:System.Windows.Forms.BindingSource.DataMember%2A> свойств в **свойства** окна.

### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>Office сопоставлены схемы и в окне источников данных Visual Studio
 Функциональность сопоставляемых схем Office и Visual Studio **источников данных** окно может помочь представить данные на листе Excel для создания отчетов или редактирования. В обоих случаях можно перетащить элементы данных на листе Excel. Оба метода создания элемента управления с привязкой через <xref:System.Windows.Forms.BindingSource> к источнику данных, такие как <xref:System.Data.DataSet> или веб-службы.

> [!NOTE]
>  При сопоставлении повторяющегося элемента схемы в лист, Visual Studio создает <xref:Microsoft.Office.Tools.Excel.ListObject>. <xref:Microsoft.Office.Tools.Excel.ListObject> Автоматически не привязан к данным с помощью <xref:System.Windows.Forms.BindingSource>. Необходимо вручную связать <xref:Microsoft.Office.Tools.Excel.ListObject> к источнику данных, задав <xref:System.Windows.Forms.BindingSource.DataSource%2A> и <xref:System.Windows.Forms.BindingSource.DataMember%2A> свойств в **свойства** окна.

 В следующей таблице показаны некоторые различия между двумя методами.

|XML-схемы|Источники данных - окно|
|----------------|-------------------------|
|Использует интерфейс Office.|Использует **источников данных** окно в Visual Studio.|
|Включает встроенные функции Office для импорта и экспорта данных из XML-файлов.|Необходимо указать импорта и экспорта программным способом.|
|Необходимо написать код для заполнения создавать элементы управления данными.|Элементы управления, добавленные из **источников данных** окно имеет код, созданный автоматически для их заполнения, а также необходимые строки подключения при использовании серверов баз данных.|

## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>Поведение при присоединении схем в документы Word
 Объекты данных не создаются при добавлении схемы в документ Word, который используется в проекте уровня документа Office. Тем не менее при сопоставлении элемента схемы в документ, создаются элементы управления. Тип элемента управления зависит от типа элемента в сопоставлении; повторяющиеся элементы генерируют <xref:Microsoft.Office.Tools.Word.XMLNodes> элементов управления и повторяющиеся элементы создания <xref:Microsoft.Office.Tools.Word.XMLNode> элементов управления. Дополнительные сведения см. в разделе [управления XMLNodes](../vsto/xmlnodes-control.md) и [элемент управления XMLNode](../vsto/xmlnode-control.md).

## <a name="deployment-of-solutions-that-include-xml-schemas"></a>Развертывание решений, содержащих XML-схемы
 Необходимо создать программу установки, чтобы развернуть решение, которое использует схему XML, сопоставленный с документом. Программа установки должна зарегистрировать схему в библиотеку схем на компьютере пользователя. Если схема не зарегистрирована, решение по-прежнему будут работать, поскольку Word создает временную схему на основе элементов, которые находятся в документ при его открытии пользователем. Тем не менее пользователь не сможет выполнить проверку или сохранение схемы, которая использовалась для создания проекта. Дополнительные сведения об установщиках см. в разделе [развертывания приложений, служб и компонентов](../deployment/deploying-applications-services-and-components.md).

 Можно также добавить код в проект, проверить ли схема в библиотеке и зарегистрирована. Если это не так, можно предупредить пользователя.

 [!code-vb[Trin_VstcoreDataWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstcoreDataWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs#1)]

## <a name="see-also"></a>См. также

- [Практическое руководство. Сопоставление схем и документов Word в Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Практическое руководство. Сопоставление схем и листов внутри Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
