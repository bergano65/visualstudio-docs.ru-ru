---
title: "Чтение XML-данных в набор данных | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
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
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 31c17df9b8b3e0a0b54d99f95e8a3d5704140cf7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="read-xml-data-into-a-dataset"></a>Чтение данных XML в объект dataset
ADO.NET предоставляет простые методы для работы с XML-данных. В этом пошаговом руководстве создается приложение Windows, которое загружает XML-данные в набор данных. Набор данных отображается в <xref:System.Windows.Forms.DataGridView> элемента управления. Наконец в текстовом поле отображается XML-схемы на основе содержимого файла XML.  
  
 Данное пошаговое руководство состоит из пяти основных этапов:  
  
1.  Создание нового проекта  
  
2.  Создание XML-файла для чтения в набор данных  
  
3.  Создание пользовательского интерфейса  
  
4.  Создание набора данных, чтение XML-файла и отображение его в <xref:System.Windows.Forms.DataGridView> управления  
  
5.  Добавление кода для отображения XML-схемы на основе XML-файла в <xref:System.Windows.Forms.TextBox> управления  
  
> [!NOTE]
>  Диалоговые окна и команды меню, которые вы видите, могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска вы используете. Чтобы изменить параметры, на **средства** последовательно выберите пункты **Импорт и экспорт параметров**. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="create-a-new-project"></a>Создание нового проекта  
 На этом шаге создается проект Visual Basic или Visual C#, содержащий в данном пошаговом руководстве.  
  
#### <a name="to-create-the-new-windows-project"></a>Порядок создания нового проекта Windows  
  
1. В Visual Studio на **файл** последовательно выберите пункты **New**, **проекта...** .  
  
2. Разверните **Visual C#** или **Visual Basic** на левой панели, затем выберите **классического Windows**.  

3. В средней области выберите **приложение Windows Forms** тип проекта.  

4. Назовите проект **ReadingXML**, а затем выберите **ОК**. 
  
     **ReadingXML** создается и добавляется в проект **обозревателе решений**.  
  
## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Создание XML-файл для чтения в набор данных  
 Поскольку в этом руководстве рассматривается на считывание данных XML в набор данных, предоставляется содержимое XML-файла.  
  
#### <a name="to-create-the-xml-file-that-will-be-read-into-the-dataset"></a>Чтобы создать XML-файл, считываемого в набор данных  
  
1.  На **проекта** последовательно выберите пункты **Добавление нового элемента**.  
  
2.  Выберите **XML-файл**, назовите файл `authors.xml`, а затем выберите **добавить**.  
  
     Загружает в конструктор и Готово для изменения XML-файла.  
  
3.  Вставьте следующий код в редактор после объявления XML:  
  
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
  
4.  На **файл** последовательно выберите пункты **сохранить authors.xml**.  
  
## <a name="create-the-user-interface"></a>Создание пользовательского интерфейса  
 Пользовательский интерфейс для этого приложения состоит из следующих элементов:  
  
-   Объект <xref:System.Windows.Forms.DataGridView> элемент управления, отображающий содержимое XML-файла данных.  
  
-   Объект <xref:System.Windows.Forms.TextBox> элемент управления, отображающий схему XML для XML-файла.  
  
-   Два <xref:System.Windows.Forms.Button> элементов управления.  
  
    -   Первая кнопка считывает XML-файла в наборе данных и отображает его в <xref:System.Windows.Forms.DataGridView> элемента управления.  
  
    -   Вторая кнопка служит для извлечения схемы из набора данных, а также через <xref:System.IO.StringWriter> отображает его в <xref:System.Windows.Forms.TextBox> элемента управления.  
  
#### <a name="to-add-controls-to-the-form"></a>Для добавления элементов управления в форму  
  
1.  Откройте `Form1` в режиме конструктора.  
  
2.  Из **элементов**, перетащите в форму следующие элементы:  
  
    -   Один <xref:System.Windows.Forms.DataGridView> управления  
  
    -   Один <xref:System.Windows.Forms.TextBox> управления  
  
    -   Два <xref:System.Windows.Forms.Button> элементов управления  
  
3.  Задайте следующие свойства:  
  
    |Control|Свойство|Параметр|  
    |-------------|--------------|-------------|  
    |`TextBox1`|**Multiline**|`true`|  
    ||**Полосы прокрутки**|**По вертикали**|  
    |`Button1`|**Имя**|`ReadXmlButton`|  
    ||**Text**|`Read XML`|  
    |`Button2`|**Имя**|`ShowSchemaButton`|  
    ||**Text**|`Show Schema`|  
  
## <a name="create-the-dataset-that-receives-the-xml-data"></a>Создание набора данных, который получает XML-данных  
 На этом шаге, создайте новый набор данных с именем `authors`. Дополнительные сведения о наборах данных см. в разделе [средства набора данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
#### <a name="to-create-a-new-dataset-that-receives-the-xml-data"></a>Чтобы создать новый набор данных, который получает XML-данных  
  
1.  В **обозревателе решений**, выберите файл источника для **Form1**и выберите **конструктор представлений** кнопку на **обозревателе решений** панель инструментов.  
  
2.  Из [область элементов, вкладка "данные"](../ide/reference/toolbox-data-tab.md), перетащите **DataSet** на **Form1**.  
  
3.  В **добавить набор данных** выберите **нетипизированный набор данных**, а затем выберите **ОК**.  
  
     **DataSet1** добавляется в область компонентов.  
  
4.  В **свойства** задайте **имя** и <xref:System.Data.DataSet.DataSetName%2A> свойства`AuthorsDataSet`.  
  
## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>Создайте обработчик события для считывания XML-файла в наборе данных  
 **Чтения XML** кнопку считывает XML-файла в наборе данных. Затем устанавливает свойства для <xref:System.Windows.Forms.DataGridView> элемента управления, связать с набором данных.  
  
#### <a name="to-add-code-to-the-readxmlbuttonclick-event-handler"></a>Чтобы добавить код в обработчик событий ReadXmlButton_Click  
  
1.  В **обозревателе решений**выберите **Form1**и выберите **конструктор представлений** кнопку на **обозревателе решений** инструментов.  
  
2.  Выберите **чтения XML** кнопки.  
  
     **Редактор кода** откроется в `ReadXmlButton_Click` обработчика событий.  
  
3.  Введите следующий код в `ReadXmlButton_Click` обработчик событий:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_1.vb)]  
  
4.  В `ReadXMLButton_Click` код обработчика событий, изменение `filepath =` входа на правильный путь.  
  
## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Создайте обработчик событий, чтобы отобразить схему в текстовом поле  
 **Показать схему** кнопка создает <xref:System.IO.StringWriter> объект, который заполняется схемой и отображается в <xref:System.Windows.Forms.TextBox>элемента управления.  
  
#### <a name="to-add-code-to-the-showschemabuttonclick-event-handler"></a>Чтобы добавить код в обработчик событий ShowSchemaButton_Click  
  
1.  В **обозревателе решений**выберите **Form1**и выберите **конструктор представлений** кнопки.  
  
2.  Выберите **Показать схему** кнопки.  
  
     **Редактор кода** откроется в `ShowSchemaButton_Click` обработчика событий.  
  
3.  Введите следующий код в `ShowSchemaButton_Click` обработчика событий.  
  
     [!code-csharp[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_2.vb)]  
  
## <a name="test-the-form"></a>Проверить форму  
 Теперь можно проверить форму, чтобы убедиться в том, что оно правильно работает.  
  
#### <a name="to-test-the-form"></a>Чтобы проверить форму  
  
1.  Выберите **F5** для запуска приложения.  
  
2.  Выберите **чтения XML** кнопки.  
  
     Элемент управления DataGridView отображает содержимое XML-файла.  
  
3.  Выберите **Показать схему** кнопки.  
  
     Текстовое поле отображает схему XML для XML-файла.  
  
## <a name="next-steps"></a>Дальнейшие действия  
 Этом пошаговом руководстве рассматриваются основные принципы считывания файла XML в набор данных, а также для создания схемы на основе содержимого файла XML. Ниже приведены некоторые задачи, которые могут делать Далее.  
  
-   Изменение данных в наборе данных и сохранение их в виде XML. Для получения дополнительной информации см. <xref:System.Data.DataSet.WriteXml%2A>.  
  
-   Изменение данных в наборе данных и записать его в базу данных. Дополнительные сведения см. в разделе [сохранение данных](../data-tools/saving-data.md).  
  
## <a name="see-also"></a>См. также  
 [Доступ к данным в Visual Studio](../data-tools/accessing-data-in-visual-studio.md)       
 [Средства XML в Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)