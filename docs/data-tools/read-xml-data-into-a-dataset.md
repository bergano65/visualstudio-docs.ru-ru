---
title: "Пошаговое руководство. Считывание XML-данных в набор данных | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "данные [Visual Studio], чтение данных из файлов XML"
  - "доступ к данным [Visual Studio], данные XML"
  - "наборы данных [Visual Basic], чтение данных XML"
  - "чтение данных, XML-файлы"
  - "чтение файлов, XML"
  - "чтение XML"
  - "XML [Visual Studio], чтение"
  - "XML-документы, чтение"
ms.assetid: fae72958-0893-47d6-b3dd-9d42418418e4
caps.latest.revision: 18
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Пошаговое руководство. Считывание XML-данных в набор данных
ADO.NET предоставляет простые методы обработки XML\-данных.  В этом пошаговом руководстве описывается создание приложения Windows, загружающего XML\-данные в набор данных.  Набор данных будет затем показан в <xref:System.Windows.Forms.DataGridView>.  В конце примера в текстовом поле поле отображается схема XML на основе содержимого файла XML.  
  
 Пример включает в себя пять основных этапов:  
  
1.  Создание нового проекта.  
  
2.  Создание файла XML, считываемого в набор данных.  
  
3.  Создание пользовательского интерфейса  
  
4.  Создание набора данных, чтение XML\-файла и отображение его в элементе управления <xref:System.Windows.Forms.DataGridView>.  
  
5.  Добавление кода для отображения XML\-схемы, основанной на XML\-файле, в элементе управления <xref:System.Windows.Forms.TextBox>.  
  
> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих настроек или выпуска.  Чтобы изменить параметры, в меню **Сервис** выберите команду **Импорт и экспорт параметров**.  Дополнительные сведения см. в разделе [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ru-ru/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Создание нового проекта  
 На данном этапе создается проект Visual Basic или Visual C\#, в рамках которого будет реализован этот пример.  
  
#### Чтобы создать новый проект Windows  
  
1.  В меню **Файл** создайте новый проект.  
  
2.  Назовите проект `ReadingXML`.  
  
3.  Выберите **Приложение Windows** и нажмите кнопку **OK**.  Дополнительные сведения см. в разделе [Клиентские приложения](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Проект **ReadingXML** создан и добавлен в "Обозреватель решений".  
  
## Создание файла XML, считываемого в набор данных.  
 Поскольку в пошаговом руководстве основной упор делается на считывание данных XML в набор данных, предоставляется содержимое некоторого файла XML.  
  
#### Создание файла XML, считываемого в набор данных.  
  
1.  В меню **Проект** выберите **Добавить новый элемент**.  
  
2.  Выберите пункт **XML\-файл**, назовите файл `authors.xml` и нажмите кнопку **Добавить**.  
  
     Файл XML загрузится в конструктор в режиме редактирования.  
  
3.  Вставьте следующий код в редактор после объявления XML.  
  
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
  
4.  В меню **Файл** выберите **Сохранить authors.xml**.  
  
## Создание пользовательского интерфейса  
 Ниже перечислены элементы, образующие пользовательский интерфейс создаваемого приложения:  
  
-   Элемент управления <xref:System.Windows.Forms.DataGridView>, отображающий содержимое файла XML в виде данных.  
  
-   Элемент управления <xref:System.Windows.Forms.TextBox>, отображающий схему XML файла XML.  
  
-   Два элемента управления <xref:System.Windows.Forms.Button>.  
  
    -   Первая кнопка инициирует считывание файла XML в набор данных и отображение его в элементе управления <xref:System.Windows.Forms.DataGridView>.  
  
    -   Нажатием второй кнопки извлекается схема из набора данных, и через <xref:System.IO.StringWriter> она отображается в элементе управления <xref:System.Windows.Forms.TextBox>.  
  
#### Для добавления элементов управления в форму:  
  
1.  Откройте `Form1` в Конструкторе.  
  
2.  Из **Панели элементов** перетащите на форму следующие элементы управления:  
  
    -   Один элемент управления <xref:System.Windows.Forms.DataGridView>  
  
    -   Один элемент управления <xref:System.Windows.Forms.TextBox>  
  
    -   Два элемента управления <xref:System.Windows.Forms.Button>  
  
3.  Задайте следующие свойства:  
  
    |Элемент управления|Свойство.|Параметр|  
    |------------------------|---------------|--------------|  
    |`TextBox1`|**Multiline**|`true`|  
    ||**ScrollBars**|**Вертикальный**|  
    |`Button1`|**Имя**|`ReadXmlButton`|  
    ||**Текст**|`Прочитать XML`|  
    |`Button2`|**Имя**|`ShowSchemaButton`|  
    ||**Текст**|`Показать схему`|  
  
## Создание набора данных, получающего данные XML  
 В следующей процедуре будет создан новый набор данных с именем `authors`.  За дополнительными сведениями о наборах данных обратитесь к разделу [Работа с наборами данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
#### Для создания нового набора данных, который будет получать XML\-данные:  
  
1.  Выбрав исходный файл для **Form1** в **обозревателе решений**, нажмите кнопку **Открыть в конструкторе** в панели инструментов **обозревателя решений**.  
  
2.  Перетащите **Набор данных** из [Вкладка "Данные", панель элементов](../ide/reference/toolbox-data-tab.md) на **Form1**.  
  
3.  Выберите **Нетипизированный набор данных** на  **Добавление набора данных** диалоговое окно " и нажмите кнопку  **ОК**.  
  
     **Dataset1** добавляется в область компонентов.  
  
4.  В окне **Свойства** задайте свойствам **Имя** и <xref:System.Data.DataSet.DataSetName%2A> значение `AuthorsDataSet`.  
  
## Создание обработчика событий, считывающего XML в набор данных  
 Кнопка **Прочитать XML** инициирует считывание файла XML в набор данных и задает свойства элемента управления <xref:System.Windows.Forms.DataGridView>, определяющие его привязку к набору данных.  
  
#### Добавление кода в обработчик событий ReadXmlButton\_Click  
  
1.  В **обозревателе решений** выберите **Form1** и нажмите кнопку **Открыть в конструкторе** в панели инструментов **обозревателя решений**.  
  
2.  Дважды щелкните кнопку **Прочитать XML**.  
  
     **Редактор кода** откроется на обработчике событий `ReadXmlButton_Click`.  
  
3.  Введите следующий код в обработчик событий `ReadXmlButton_Click`:  
  
     [!code-cs[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_1.vb)]  
  
4.  В коде обработчика событий `ReadXMLButton_Click` измените параметр `filepath =` на правильный путь.  
  
## Создание обработчика событий, отображающего схему XML в текстовом поле  
 Кнопка **Показать схему** создает объект <xref:System.IO.StringWriter>, который заполняется схемой и отображается в <xref:System.Windows.Forms.TextBox>.  
  
#### Добавление кода в обработчик событий ShowSchemaButton\_Click.  
  
1.  В **обозревателе решений** выберите **Form1** и нажмите кнопку **Открыть в конструкторе**.  
  
2.  Дважды щелкните кнопку **Показать схему**.  
  
     **Редактор кода** откроется на обработчике событий `ShowSchemaButton_Click`.  
  
3.  Введите следующий код в обработчик событий `ShowSchemaButton_Click`:  
  
     [!code-cs[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_2.vb)]  
  
## Проверка  
 Теперь можно проверить форму, чтобы убедиться, что она работает так, как ожидалось.  
  
#### Чтобы проверить форму, выполните следующие действия:  
  
1.  Нажмите клавишу F5 для запуска приложения.  
  
2.  Нажмите кнопку **Прочитать XML**.  
  
     Сетка данных DataGridView заполнится содержимым файла XML.  
  
3.  Нажмите кнопку **Показать схему**.  
  
     В текстовом поле отобразится схема XML для файла XML.  
  
## Следующие действия  
 В настоящем пошаговом руководстве продемонстрирована основная методика считывания файла XML в набор данных и создания схемы на основе содержимого файла XML.  Далее будут рассмотрены следующие задачи:  
  
-   Редактирование записей набора данных и сохранение их в формате XML.  Дополнительные сведения см. в разделе <xref:System.Data.DataSet.WriteXml%2A>.  
  
-   Редактирование записей набора данных и сохранение их в базе данных.  Дополнительные сведения см. в разделе [Сохранение данных](../data-tools/saving-data.md).  
  
## См. также  
 [Пошаговые руководства работы с данными](../Topic/Data%20Walkthroughs.md)   
 [Доступ к данным в Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
 [Подготовка приложения к получению данных](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Средства XML в Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)