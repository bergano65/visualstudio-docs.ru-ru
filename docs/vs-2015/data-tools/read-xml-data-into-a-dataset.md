---
title: Чтение XML-данных в набор данных | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- reading XML
- data access [Visual Studio], XML data
- reading files, XML
- data [Visual Studio], reading from XML files
- reading data, XML files
- XML [Visual Studio], reading
- XML documents, reading
- datasets [Visual Basic], reading XML data
ms.assetid: fae72958-0893-47d6-b3dd-9d42418418e4
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dea8565810a904ff80a0790a9b219f3744b1e156
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63425392"
---
# <a name="read-xml-data-into-a-dataset"></a>Считывание XML-данных в набор данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ADO.NET предоставляет простые методы для работы с XML-данных. В этом пошаговом руководстве создается приложение Windows, которое загружает XML-данные в набор данных. Набор данных отображается в <xref:System.Windows.Forms.DataGridView> элемента управления. Наконец схема XML, на основе содержимого XML-файла отображается в текстовом поле.  
  
 Данное пошаговое руководство состоит из пяти основных этапов:  
  
1. Создание нового проекта  
  
2. Создание файла XML для считывания в набор данных  
  
3. Создание пользовательского интерфейса  
  
4. Создание набора данных, чтение XML-файла и отображения его в <xref:System.Windows.Forms.DataGridView> элемента управления  
  
5. Добавление кода для отображения XML-схемы на основе XML файла в <xref:System.Windows.Forms.TextBox> элемента управления  
  
> [!NOTE]
> Диалоговые окна и команды меню, которые вы видите, могут отличаться от описанных в справке в зависимости от текущих настроек или выпуска вы используете. Чтобы изменить параметры, на **средства** меню, выберите**Импорт и экспорт параметров**. Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="create-a-new-project"></a>Создание нового проекта  
 На этом шаге создайте проект Visual Basic или Visual C#, содержащий в этом пошаговом руководстве.  
  
#### <a name="to-create-the-new-windows-project"></a>Порядок создания нового проекта Windows  
  
1. На **файл** меню, создайте новый проект.  
  
2. Задайте для проекта имя `ReadingXML`.  
  
3. Выберите **приложения Windows**, а затем выберите **ОК**. Дополнительные сведения см. в разделе [клиентских приложений](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     **ReadingXML** проекта создается и добавляется к **обозревателе решений**.  
  
## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Создать XML-файл для чтения в набор данных  
 Так как в этом пошаговом руководстве уделяется чтение XML-данных в набор данных, предоставляется содержимое XML-файла.  
  
#### <a name="to-create-the-xml-file-that-will-be-read-into-the-dataset"></a>Для создания XML-файле, которые будут считываться в набор данных  
  
1. На **проекта** меню, выберите**Добавление нового элемента**.  
  
2. Выберите **XML-файл**, назовите файл `authors.xml`, а затем выберите **добавить**.  
  
     XML-файле загружает в конструктор и готов для редактирования.  
  
3. Вставьте следующий код в редакторе ниже XML-декларации:  
  
    ```xml  
    <Authors_Table>  
      <authors>  
        <au_id>172-32-1176</au_id>  
        <au_lname>White</au_lname>  
        <au_fname>Johnson</au_fname>  
        <phone>408 496-7223</phone>  
        <address>10932 Bigge Rd.</address>  
        <city>Menlo Park</city>  
        <state>CA</state>  
        <zip>94025</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>213-46-8915</au_id>  
        <au_lname>Green</au_lname>  
        <au_fname>Margie</au_fname>  
        <phone>415 986-7020</phone>  
        <address>309 63rd St. #411</address>  
        <city>Oakland</city>  
        <state>CA</state>  
        <zip>94618</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>238-95-7766</au_id>  
        <au_lname>Carson</au_lname>  
        <au_fname>Cheryl</au_fname>  
        <phone>415 548-7723</phone>  
        <address>589 Darwin Ln.</address>  
        <city>Berkeley</city>  
        <state>CA</state>  
        <zip>94705</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>267-41-2394</au_id>  
        <au_lname>Hunter</au_lname>  
        <au_fname>Anne</au_fname>  
        <phone>408 286-2428</phone>  
        <address>22 Cleveland Av. #14</address>  
        <city>San Jose</city>  
        <state>CA</state>  
        <zip>95128</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>274-80-9391</au_id>  
        <au_lname>Straight</au_lname>  
        <au_fname>Dean</au_fname>  
        <phone>415 834-2919</phone>  
        <address>5420 College Av.</address>  
        <city>Oakland</city>  
        <state>CA</state>  
        <zip>94609</zip>  
        <contract>true</contract>  
      </authors>  
    </Authors_Table>  
    ```  
  
4. На **файл** меню, выберите**сохранить authors.xml**.  
  
## <a name="create-the-user-interface"></a>Создание пользовательского интерфейса  
 Пользовательский интерфейс для данного приложения состоит из следующих:  
  
- Объект <xref:System.Windows.Forms.DataGridView> элемент управления, отображающий содержимое XML-файла данных.  
  
- Объект <xref:System.Windows.Forms.TextBox> элемент управления, который отображает схему XML для XML-файле.  
  
- Два <xref:System.Windows.Forms.Button> элементов управления.  
  
    - Одна кнопка считывает XML-файл в набор данных и отображает его в <xref:System.Windows.Forms.DataGridView> элемента управления.  
  
    - Вторая кнопка извлекает схему из набора данных, а также через <xref:System.IO.StringWriter> отображает его в <xref:System.Windows.Forms.TextBox> элемента управления.  
  
#### <a name="to-add-controls-to-the-form"></a>Для добавления элементов управления в форму  
  
1. Откройте `Form1` в режиме конструктора.  
  
2. Из **элементов**, перетащите в форму следующие элементы управления:  
  
    - Один <xref:System.Windows.Forms.DataGridView> элемента управления  
  
    - Один <xref:System.Windows.Forms.TextBox> элемента управления  
  
    - Два <xref:System.Windows.Forms.Button> элементов управления  
  
3. Задайте следующие свойства:  
  
    |Элемент управления|Свойство|Параметр|  
    |-------------|--------------|-------------|  
    |`TextBox1`|**Multiline**|`true`|  
    ||**ScrollBars**|**По вертикали**|  
    |`Button1`|**Name**|`ReadXmlButton`|  
    ||**Text**|`Read XML`|  
    |`Button2`|**Name**|`ShowSchemaButton`|  
    ||**Text**|`Show Schema`|  
  
## <a name="create-the-dataset-thatreceives-the-xml-data"></a>Создание набора данных thatreceives XML-данных  
 На этом шаге, создайте новый набор данных с именем `authors`. Дополнительные сведения о наборах данных см. в разделе [средства набора данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
#### <a name="to-create-a-new-dataset-that--receives-the-xml-data"></a>Чтобы создать новый набор данных, который получает данные XML  
  
1. В **обозревателе решений**, выберите исходный файл для **Form1**, а затем выберите **конструктор представлений** , нажмите кнопку **обозревателе решений** панель инструментов.  
  
2. Из [на панель элементов, вкладка "данные"](../ide/reference/toolbox-data-tab.md), перетащите **набора данных** на **Form1**.  
  
3. В **добавить набор данных** выберите **нетипизированный набор данных**, а затем выберите **ОК**.  
  
     **DataSet1** добавляется в область компонентов.  
  
4. В **свойства** окне **имя** и <xref:System.Data.DataSet.DataSetName%2A> свойства`AuthorsDataSet`.  
  
## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>Создайте обработчик событий для считывания XML-файл в набор данных  
 **Чтения XML** кнопку считывает XML-файл в набор данных. Затем он устанавливает свойства для <xref:System.Windows.Forms.DataGridView> элемента управления, привязать его к набору данных.  
  
#### <a name="to-add-code-to-the-readxmlbuttonclick-event-handler"></a>Чтобы добавить код в обработчик событий ReadXmlButton_Click  
  
1. В **обозревателе решений**выберите **Form1**, а затем выберите **конструктор представлений** , нажмите кнопку **обозревателе решений** панели инструментов.  
  
2. Выберите **чтения XML** кнопки.  
  
     **Редактор кода** открывается `ReadXmlButton_Click` обработчик событий.  
  
3. Введите следующий код в `ReadXmlButton_Click` обработчик событий:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#2)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#2)]  
  
4. В `ReadXMLButton_Click` код обработчика событий, изменение `filepath =` запись на правильный путь.  
  
## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Создать обработчик событий, чтобы отобразить схему в текстовом поле  
 **Показать схему** создает кнопку <xref:System.IO.StringWriter> объект, который заполняется схемой и отображается в <xref:System.Windows.Forms.TextBox>элемента управления.  
  
#### <a name="to-add-code-to-the-showschemabuttonclick-event-handler"></a>Чтобы добавить код в обработчик событий ShowSchemaButton_Click  
  
1. В **обозревателе решений**выберите **Form1**, а затем выберите **конструктор представлений** кнопки.  
  
2. Выберите **Показать схему** кнопки.  
  
     **Редактор кода** открывается `ShowSchemaButton_Click` обработчик событий.  
  
3. Введите следующий код в `ShowSchemaButton_Click` обработчик событий.  
  
     [!code-csharp[VbRaddataFillingAndExecuting#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#3)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#3)]  
  
## <a name="test-the-form"></a>Проверить форму  

Теперь можно проверить форму, чтобы убедиться, что она правильно работает.
  
1. Выберите **F5** для запуска приложения.  
  
2. Выберите **чтения XML** кнопки.  
  
     Элемент управления DataGridView отображает содержимое XML-файла.  
  
3. Выберите **Показать схему** кнопки.  
  
     Текстовое поле отображает схему XML для XML-файле.  
  
## <a name="next-steps"></a>Следующие шаги  

В этом пошаговом руководстве вы научитесь основам считывание XML-файл в набор данных, а также для создания схемы на основе содержимого XML-файла. Ниже приведены некоторые задачи, которые могут делать дальше.  
  
- Изменение данных в наборе данных и сохранение их в виде XML. Дополнительные сведения см. в разделе <xref:System.Data.DataSet.WriteXml%2A>.  
  
- Измените данные в наборе данных и записать его в базу данных.
  
## <a name="see-also"></a>См. также  
 [Пошаговые руководства работы с данными](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Доступ к данным в Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
 [Подготовка приложения к получению данных](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Средства XML в Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)