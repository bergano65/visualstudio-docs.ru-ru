---
title: Считывание XML-данных в набор данных
ms.date: 11/04/2016
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: fa0472ae7ad7200ead372057f1dd778c077f764e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60076033"
---
# <a name="read-xml-data-into-a-dataset"></a>Считывание XML-данных в набор данных

ADO.NET предоставляет простые методы для работы с XML-данных. В этом пошаговом руководстве создается приложение Windows, которое загружает XML-данные в набор данных. Набор данных отображается в <xref:System.Windows.Forms.DataGridView> элемента управления. Наконец схема XML, на основе содержимого XML-файла отображается в текстовом поле.

## <a name="create-a-new-project"></a>Создание нового проекта

Создайте новый **приложения Windows Forms** проекта либо C# или Visual Basic. Назовите проект **ReadingXML**.

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Создать XML-файл для чтения в набор данных

Так как в этом пошаговом руководстве уделяется чтение XML-данных в набор данных, предоставляется содержимое XML-файла.

1. В меню **Проект** выберите пункт **Добавить новый элемент**.

2. Выберите **XML-файл**, назовите файл **authors.xml**, а затем выберите **добавить**.

   XML-файле загружает в конструктор и готов для редактирования.

3. Вставьте следующий XML-данных в редакторе ниже XML-декларации:

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

4. На **файл** меню, выберите **сохранить authors.xml**.

## <a name="create-the-user-interface"></a>Создание пользовательского интерфейса

Пользовательский интерфейс для данного приложения состоит из следующих:

- Объект <xref:System.Windows.Forms.DataGridView> элемент управления, отображающий содержимое XML-файла данных.

- Объект <xref:System.Windows.Forms.TextBox> элемент управления, который отображает схему XML для XML-файле.

- Два <xref:System.Windows.Forms.Button> элементов управления.

    - Одна кнопка считывает XML-файл в набор данных и отображает его в <xref:System.Windows.Forms.DataGridView> элемента управления.

    - Вторая кнопка извлекает схему из набора данных, а также через <xref:System.IO.StringWriter> отображает его в <xref:System.Windows.Forms.TextBox> элемента управления.

### <a name="to-add-controls-to-the-form"></a>Для добавления элементов управления в форму

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

## <a name="create-the-dataset-that-receives-the-xml-data"></a>Создание набора данных, который получает данные XML

На этом шаге, создайте новый набор данных с именем `authors`. Дополнительные сведения о наборах данных см. в разделе [средства набора данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

1. В **обозревателе решений**, выберите исходный файл для **Form1**, а затем выберите **конструктор представлений** , нажмите кнопку **обозревателе решений** панель инструментов.

2. Из [панели элементов, вкладка "данные"](../ide/reference/toolbox-data-tab.md), перетащите **набора данных** на **Form1**.

3. В **добавить набор данных** выберите **нетипизированный набор данных**, а затем выберите **ОК**.

     **DataSet1** добавляется в область компонентов.

4. В **свойства** окне **имя** и <xref:System.Data.DataSet.DataSetName%2A> свойства`AuthorsDataSet`.

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>Создайте обработчик событий для считывания XML-файл в набор данных

**Чтения XML** кнопку считывает XML-файл в набор данных. Затем он устанавливает свойства для <xref:System.Windows.Forms.DataGridView> элемента управления, привязать его к набору данных.

1. В **обозревателе решений**выберите **Form1**, а затем выберите **конструктор представлений** , нажмите кнопку **обозревателе решений** панели инструментов.

2. Выберите **чтения XML** кнопки.

     **Редактор кода** открывается `ReadXmlButton_Click` обработчик событий.

3. Введите следующий код в `ReadXmlButton_Click` обработчик событий:

     [!code-csharp[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_1.vb)]

4. В `ReadXMLButton_Click` код обработчика событий, изменение `filepath =` запись на правильный путь.

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Создать обработчик событий, чтобы отобразить схему в текстовом поле

**Показать схему** создает кнопку <xref:System.IO.StringWriter> объект, который заполняется схемой и отображается в <xref:System.Windows.Forms.TextBox>элемента управления.

1. В **обозревателе решений**выберите **Form1**, а затем выберите **конструктор представлений** кнопки.

2. Выберите **Показать схему** кнопки.

     **Редактор кода** открывается `ShowSchemaButton_Click` обработчик событий.

3. Вставьте в обработчик события `ShowSchemaButton_Click` следующий код.

     [!code-csharp[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_2.vb)]

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

- [Доступ к данным в Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Средства XML в Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)