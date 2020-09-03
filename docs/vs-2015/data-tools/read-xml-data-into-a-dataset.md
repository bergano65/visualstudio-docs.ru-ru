---
title: Чтение XML-данных в наборе данных | Документация Майкрософт
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c34fb87c02ff60d9b28c43130d6fbf3a12e70349
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652892"
---
# <a name="read-xml-data-into-a-dataset"></a>Считывание XML-данных в набор данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ADO.NET предоставляет простые методы для работы с XML-данными. В этом пошаговом руководстве вы создадите приложение Windows, которое загружает XML-данные в набор данных. Затем набор данных отображается в <xref:System.Windows.Forms.DataGridView> элементе управления. Наконец, схема XML, основанная на содержимом XML-файла, отображается в текстовом поле.

 Это пошаговое руководство состоит из пяти основных этапов.

1. Создание нового проекта

2. Создание XML-файла для чтения в наборе данных

3. Создание пользовательского интерфейса

4. Создание набора данных, чтение XML-файла и отображение его в <xref:System.Windows.Forms.DataGridView> элементе управления

5. Добавление кода для вывода схемы XML на основе XML-файла в <xref:System.Windows.Forms.TextBox> элементе управления

> [!NOTE]
> Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или используемого выпуска. Чтобы изменить параметры, в меню  **Сервис** выберите**Импорт и экспорт параметров**. Дополнительные сведения см. [в разделе Настройка параметров разработки в Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="create-a-new-project"></a>Создание нового проекта
 На этом шаге вы создадите проект Visual Basic или Visual C#, содержащий это пошаговое руководство.

#### <a name="to-create-the-new-windows-project"></a>Порядок создания нового проекта Windows

1. В меню **файл** создайте новый проект.

2. Присвойте проекту имя `ReadingXML`.

3. Выберите **приложение Windows**и нажмите кнопку **ОК**. Дополнительные сведения см. в разделе [Client Applications](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Проект **реадингксмл** создается и добавляется в **Обозреватель решений**.

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Создать XML-файл для чтения в наборе данных
 Поскольку в этом пошаговом руководстве рассматривается чтение XML-данных в наборе данных, предоставляется содержимое XML-файла.

#### <a name="to-create-the-xml-file-that-will-be-read-into-the-dataset"></a>Создание XML-файла, который будет считан в набор данных

1. В меню **проект** выберите команду**Добавить новый элемент**.

2. Выберите **XML-файл**, присвойте файлу имя `authors.xml` и нажмите кнопку **добавить**.

     XML-файл загружается в конструктор и готов к редактированию.

3. Вставьте следующий код в редактор под XML-объявлением:

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

4. В меню **файл** выберите команду**сохранить authors.xml**.

## <a name="create-the-user-interface"></a>Создание пользовательского интерфейса
 Пользовательский интерфейс для этого приложения состоит из следующих компонентов:

- <xref:System.Windows.Forms.DataGridView>Элемент управления, отображающий содержимое XML-файла в виде данных.

- <xref:System.Windows.Forms.TextBox>Элемент управления, отображающий XML-схему для XML-файла.

- Два <xref:System.Windows.Forms.Button> элемента управления.

  - Одна кнопка считывает XML-файл в набор данных и отображает его в <xref:System.Windows.Forms.DataGridView> элементе управления.

  - Вторая кнопка извлекает схему из набора данных, а затем <xref:System.IO.StringWriter> отображает ее в <xref:System.Windows.Forms.TextBox> элементе управления.

#### <a name="to-add-controls-to-the-form"></a>Для добавления элементов управления в форму

1. Откройте `Form1` в режиме конструктора.

2. Перетащите следующие элементы управления из **области элементов**в форму:

    - Один <xref:System.Windows.Forms.DataGridView> элемент управления

    - Один <xref:System.Windows.Forms.TextBox> элемент управления

    - Два <xref:System.Windows.Forms.Button> элемента управления

3. Задайте следующие свойства.

    |Control|Property (Свойство)|Параметр|
    |-------------|--------------|-------------|
    |`TextBox1`|**Multiline**|`true`|
    ||**ScrollBars**|**По вертикали**|
    |`Button1`|**Имя**|`ReadXmlButton`|
    ||**Text**|`Read XML`|
    |`Button2`|**Имя**|`ShowSchemaButton`|
    ||**Text**|`Show Schema`|

## <a name="create-the-dataset-thatreceives-the-xml-data"></a>Создание набора данных, сатрецеивес XML-данные
 На этом шаге вы создадите новый набор данных с именем `authors` . Дополнительные сведения о наборах данных см. [в разделе Инструменты набора DataSet в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

#### <a name="to-create-a-new-dataset-that--receives-the-xml-data"></a>Создание нового набора данных, получающего XML-данные

1. В **Обозреватель решений**выберите исходный файл для **формы Form1**, а затем нажмите кнопку **конструктор представлений** на панели инструментов **Обозреватель решений** .

2. Перетащите **набор данных** из [панели элементов на вкладку "данные"](../ide/reference/toolbox-data-tab.md)на **форму Form1**.

3. В диалоговом окне **Добавление набора данных** выберите параметр **нетипизированный набор данных**, а затем нажмите кнопку **ОК**.

     **DataSet1** добавляется в область компонентов.

4. В окне **Свойства** задайте **имя** и <xref:System.Data.DataSet.DataSetName%2A> свойства для `AuthorsDataSet` .

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>Создание обработчика событий для чтения XML-файла в наборе данных
 Кнопка " **прочитать XML** " считывает XML-файл в наборе данных. Затем в нем устанавливаются свойства <xref:System.Windows.Forms.DataGridView> элемента управления, который привязывает его к набору данных.

#### <a name="to-add-code-to-the-readxmlbutton_click-event-handler"></a>Добавление кода в обработчик событий ReadXmlButton_Click

1. В **Обозреватель решений**выберите **Form1**, а затем нажмите кнопку **конструктор представлений** на панели инструментов **Обозреватель решений** .

2. Нажмите кнопку **чтение XML** .

     **Редактор кода** откроется в `ReadXmlButton_Click` обработчике событий.

3. Введите следующий код в `ReadXmlButton_Click` обработчик событий:

     [!code-csharp[VbRaddataFillingAndExecuting#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#2)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#2)]

4. В `ReadXMLButton_Click` коде обработчика событий измените `filepath =` запись на правильный путь.

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Создание обработчика событий для вывода схемы в текстовое поле
 Кнопка **Показать схему** создает <xref:System.IO.StringWriter> объект, который заполняется схемой и отображается в <xref:System.Windows.Forms.TextBox> элементе управления.

#### <a name="to-add-code-to-the-showschemabutton_click-event-handler"></a>Добавление кода в обработчик событий ShowSchemaButton_Click

1. В **Обозреватель решений**выберите **Form1**, а затем нажмите кнопку **Конструктор представлений** .

2. Нажмите кнопку **отобразить схему** .

     **Редактор кода** откроется в `ShowSchemaButton_Click` обработчике событий.

3. Введите следующий код в `ShowSchemaButton_Click` обработчик событий.

     [!code-csharp[VbRaddataFillingAndExecuting#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#3)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#3)]

## <a name="test-the-form"></a>Тестирование формы

Теперь можно проверить форму, чтобы убедиться, что она ведет себя так, как ожидалось.

1. Нажмите **клавишу F5** , чтобы запустить приложение.

2. Нажмите кнопку **чтение XML** .

     Элемент DataGridView отображает содержимое XML-файла.

3. Нажмите кнопку **отобразить схему** .

     В текстовом поле отображается схема XML для XML-файла.

## <a name="next-steps"></a>Next Steps

В этом пошаговом руководстве рассматриваются основы чтения XML-файла в наборе данных, а также создание схемы на основе содержимого XML-файла. Ниже приведены некоторые задачи, которые можно выполнить далее.

- Изменить данные в наборе данных и записать их обратно в формате XML. Для получения дополнительной информации см. <xref:System.Data.DataSet.WriteXml%2A>.

- Измените данные в наборе данных и запишите их в базу данных.

## <a name="see-also"></a>См. также:
 [Пошаговые руководства](https://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4) [по доступу к данным в Visual Studio](../data-tools/accessing-data-in-visual-studio.md) [Подготовка приложения к получению средств XML для работы с данными](https://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad) [в Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)
