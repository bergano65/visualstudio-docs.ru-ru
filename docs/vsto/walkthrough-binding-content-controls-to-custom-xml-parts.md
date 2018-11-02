---
title: 'Пошаговое руководство: Привязка элементов управления содержимым к пользовательским XML-частям'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- PlainTextContentControl, binding to a custom XML part
- custom XML parts, binding to content controls
- content controls [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], content controls
- DropDownListContentControl, binding items to a custom XML part
- DatePickerContentControl, binding to a custom XML part
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1bc8aee0a1294aeda4c57a3416de4a0cc98129f3
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50673046"
---
# <a name="walkthrough-bind-content-controls-to-custom-xml-parts"></a>Пошаговое руководство: Привязка элементов управления содержимым к пользовательским XML-частям
  В этом пошаговом руководстве показано, как привязать элементы управления содержимым в настройке на уровне документа для Word к XML-данным, хранящимся в документе.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Word позволяет хранить XML-данных с именем *пользовательские XML-части*, в документе. Вы можете управлять отображением этих данных, привязывая элементы управления содержимым к элементам в пользовательской XML-части. Пример документа в этом пошаговом руководстве отображает данные о сотрудниках, которые хранятся в пользовательской XML-части. При открытии документа элементы управления содержимым показывают значения XML-элементов. Любые изменения, внесенные в текст в элементах управления содержимым, сохраняются в пользовательской XML-части.  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
- добавление элементов управления содержимым в документ Word в проекте на уровне документа во время разработки;  
  
- создание файла XML-данных и XML-схемы, которая определяет элементы для привязки к элементам управления содержимым;  
  
- добавление схемы XML к документу во время разработки;  
  
- Добавление содержимого XML-файла к пользовательской XML-части в документ во время выполнения.  
  
- привязка элементов управления содержимым к элементам в пользовательской XML-части;  
  
- привязка <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> к набору значений, определенных в схеме XML.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## <a name="create-a-new-word-document-project"></a>Создание нового проекта документа Word  
 Создайте документ Word, который будет использоваться в этом руководстве.  
  
### <a name="to-create-a-new-word-document-project"></a>Создание проекта документа Word  
  
1.  Создайте проект документа Word с именем **EmployeeControls**. Создайте документ для решения. Дополнительные сведения см. в разделе [как: проектов Office, создайте в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Открывает новый документ Word в конструкторе и добавляет **EmployeeControls** проект **обозревателе решений**.  
  
## <a name="add-content-controls-to-the-document"></a>Добавление элементов управления содержимым в документ  
 Создайте таблицу, содержащую три различных типа элементов управления содержимым, в которой пользователь может просмотреть или изменить сведения о сотруднике.  
  
### <a name="to-add-content-controls-to-the-document"></a>Порядок добавления элементов управления содержимым в документ  
  
1. В документе Word, который размещен в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] designer и на ленте выберите **вставить** вкладки.  
  
2. В **таблиц** группе, выберите **таблицы**и вставьте таблицу с двумя столбцами и тремя строками.  
  
3. Введите текст в первый столбец, как показано в следующем столбце:  
  
   ||  
   |-|  
   |**Имя сотрудника**|  
   |**Дата найма**|  
   |**Заголовок**|  
  
4. Во втором столбце таблицы, выберите первую строку (рядом с полем **имя сотрудника**).  
  
5. На ленте выберите **разработчика** вкладки.  
  
   > [!NOTE]  
   >  Если вкладка **Разработчик** не отображается, сделайте ее видимой. Дополнительные сведения см. в разделе [как: Отображение вкладки разработчика на ленте](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
6. В **элементов управления** группе, выберите **текст** кнопку ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") добавление <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>к первой ячейке.  
  
7. Во втором столбце таблицы, выберите вторую строку (рядом с полем **Дата приема на работу**).  
  
8. В **элементов управления** группе, выберите **Date Picker** кнопку ![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl") добавление <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> во вторую ячейку.  
  
9. Во втором столбце таблицы, выберите третью строку (рядом с полем **Title**).  
  
10. В **элементов управления** группе, выберите **с раскрывающимся списком** кнопку ![DropDownListContentControl](../vsto/media/dropdownlist.gif "DropDownListContentControl") для добавления <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> в последнюю ячейку.  
  
    Вот и весь пользовательский интерфейс для этого проекта. При запуске проекта можно ввести текст в первой строке и выбрать дату во второй строке. Следующий шаг — присоединение данных, которые будут отображаться в документе, к XML-файлу.  
  
## <a name="create-the-xml-data-file"></a>Создание файла данных XML  
 Как правило, вы будете получать XML-данные для хранения в пользовательской XML-части из внешнего источника, например файла или базы данных. В этом пошаговом руководстве создается XML-файл, содержащий данные о сотрудниках, помеченные элементами, которые необходимо привязать к элементам управления содержимым в документе. Чтобы сделать данные доступными во время выполнения, внедрите XML-файл в качестве ресурса в сборке настройки.  
  
#### <a name="to-create-the-data-file"></a>Создание файла данных  
  
1.  В меню **Проект** выберите пункт **Добавить новый элемент**.  
  
     Откроется диалоговое окно **Добавление нового элемента**.  
  
2.  В **шаблоны** области выберите **XML-файл**.  
  
3.  Назовите файл **employees.xml**, а затем выберите **добавить** кнопки.  
  
     **Employees.xml** файл откроется в редакторе кода.  
  
4.  Замените содержимое файла **employees.xml** файл со следующим текстом.  
  
    ```xml 
    <?xml version="1.0" encoding="utf-8" ?>  
    <employees xmlns="http://schemas.microsoft.com/vsto/samples">  
      <employee>  
        <name>Karina Leal</name>  
        <hireDate>1999-04-01</hireDate>  
        <title>Manager</title>  
      </employee>  
    </employees>  
    ```  
  
5.  В **обозревателе решений**, выберите **employees.xml** файл.  
  
6.  В **свойства** выберите **действие при построении** свойство, а затем измените значение на **внедренный ресурс**.  
  
     Этот шаг внедряет XML-файл в качестве ресурса в сборку при построении проекта. Это позволяет получить доступ к содержимому XML-файла во время выполнения.  
  
## <a name="create-an-xml-schema"></a>Создание схемы XML  
 Если вам необходимо привязать элемент управления содержимым к одному элементу в пользовательской XML-части, необязательно использовать схему XML. Однако для привязки <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> к набору значений необходимо создать схему XML, которая проверяет созданный ранее файл XML-данных. Схема XML определяет возможные значения для элемента `title`. Вы привяжете <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> к этому элементу далее в этом пошаговом руководстве.  
  
#### <a name="to-create-an-xml-schema"></a>Порядок создания схемы XML  
  
1.  В меню **Проект** выберите пункт **Добавить новый элемент**.  
  
     Откроется диалоговое окно **Добавление нового элемента**.  
  
2.  В **шаблоны** области выберите **схемы XML**.  
  
3.  Назовите схему **employees.xsd** и выберите **добавить** кнопки.  
  
     Открывается конструктор схем.  
  
4.  В **обозревателе решений**, откройте контекстное меню для **employees.xsd**, а затем выберите **Просмотр кода**.  
  
5.  Замените содержимое файла **employees.xsd** файл по следующей схеме.  
  
    ```xml
    <?xml version="1.0" encoding="utf-8" ?>  
    <xs:schema xmlns="http://schemas.microsoft.com/vsto/samples"   
        targetNamespace="http://schemas.microsoft.com/vsto/samples"  
        xmlns:xs="http://www.w3.org/2001/XMLSchema"  
        elementFormDefault="qualified">  
      <xs:element name="employees" type="EmployeesType"></xs:element>  
      <xs:complexType name="EmployeesType">  
        <xs:all>  
          <xs:element name="employee" type="EmployeeType"/>  
        </xs:all>  
      </xs:complexType>  
      <xs:complexType name="EmployeeType">  
        <xs:sequence>  
          <xs:element name="name" type="xs:string" minOccurs="1" maxOccurs="1"/>  
          <xs:element name="hireDate" type="xs:date" minOccurs="1" maxOccurs="1"/>  
          <xs:element name="title" type="TitleType" minOccurs="1" maxOccurs="1"/>  
        </xs:sequence>  
      </xs:complexType>  
      <xs:simpleType name="TitleType">  
        <xs:restriction base="xs:string">  
          <xs:enumeration value ="Engineer"/>  
          <xs:enumeration value ="Designer"/>  
          <xs:enumeration value ="Manager"/>  
        </xs:restriction>  
      </xs:simpleType>  
    </xs:schema>  
    ```  
  
6.  На **файл** меню, щелкните **сохранить все** сохранить изменения, внесенные в **employees.xml** и **employees.xsd** файлов.  
  
## <a name="attach-the-xml-schema-to-the-document"></a>Добавление схемы XML к документу  
 XML-схему необходимо присоединить к документу, чтобы привязать <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> к допустимым значениям элемента `title`.  
  
### <a name="to-attach-the-xml-schema-to-the-document--includeword15shortvstoincludesword-15-short-mdmd"></a>Добавление схемы XML к документу ( [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)])  
  
1.  Активировать **EmployeeControls.docx** в конструкторе.  
  
2.  На ленте выберите **разработчика** вкладке, а затем выберите **Add-Ins** кнопки.  
  
3.  В **шаблоны и надстройки** диалоговое окно, выберите **схемы XML** вкладке, а затем выберите **Добавление схемы** кнопки.  
  
4.  Перейдите к **employees.xsd** созданной ранее схеме, который находится в каталоге проекта, а затем выберите **откройте** кнопки.  
  
5.  Выберите **ОК** кнопку **параметры схемы** диалоговое окно.  
  
6.  Выберите **ОК** кнопку, чтобы закрыть **шаблоны и надстройки** диалоговое окно.  
  
### <a name="to-attach-the-xml-schema-to-the-document-word-2010"></a>Добавление схемы XML к документу (Word 2010)  
  
1.  Активировать **EmployeeControls.docx** в конструкторе.  
  
2.  На ленте выберите **разработчика** вкладки.  
  
3.  В **XML** группе, выберите **схемы** кнопки.  
  
4.  В **шаблоны и надстройки** диалоговое окно, выберите **схемы XML** вкладке, а затем выберите **Добавление схемы** кнопки.  
  
5.  Перейдите к **employees.xsd** схему, созданную ранее, который находится в каталоге проекта и выберите **откройте** кнопки.  
  
6.  Выберите **ОК** кнопку **параметры схемы** диалоговое окно.  
  
7.  Выберите **ОК** кнопку, чтобы закрыть **шаблоны и надстройки** диалоговое окно.  
  
     **XML-структуру** откроется панель задач.  
  
8.  Закрыть **XML-структуру** области задач.  
  
## <a name="add-a-custom-xml-part-to-the-document"></a>Добавление пользовательской XML-части в документ  
 Перед привязкой элементов управления содержимым к элементам в XML-файле необходимо добавить содержимое XML-файла в новую пользовательскую XML-часть в документе.  
  
### <a name="to-add-a-custom-xml-part-to-the-document"></a>Порядок добавления пользовательской XML-части в документ  
  
1.  В **обозревателе решений**, откройте контекстное меню для **ThisDocument.cs** или **ThisDocument.vb**, а затем выберите **Просмотр кода**.  
  
2.  Добавьте в класс `ThisDocument` следующие объявления. В этом коде объявляются несколько объектов, которые будут использоваться для добавления пользовательской XML-части в документ.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#1](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#1](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#1)]  
  
3.  Добавьте следующий метод в класс `ThisDocument` . Этот метод получает содержимое файла данных XML, внедренного в сборку в качестве ресурса, и возвращает содержимое в виде XML-строки.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#3](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#3)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#3](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#3)]  
  
4.  Добавьте следующий метод в класс `ThisDocument` . Метод `AddCustomXmlPart` создает пользовательскую XML-часть, которая содержит XML-строку, передаваемую в метод.  
  
     Чтобы пользовательская XML-часть создавалась всего один раз, метод создает ее, только если пользовательская XML-часть с соответствующим идентификатором GUID еще не существует в документе. При первом вызове этого метода он сохраняет значение свойства <xref:Microsoft.Office.Core._CustomXMLPart.Id%2A> в строке `employeeXMLPartID`. Значение `employeeXMLPartID` строки хранится в документе, поскольку он был объявлен с помощью атрибута <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#4](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#4)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#4](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#4)]  
  
## <a name="bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>Привязать элементы управления содержимым к элементам в пользовательской XML-части  
 Привяжите каждый элемент управления содержимым к элементу в пользовательской XML-части с помощью **XMLMapping** свойство каждого элемента управления.  
  
### <a name="to-bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>Порядок привязки элементов управления содержимым к элементам в пользовательской XML-части  
  
1.  Добавьте следующий метод в класс `ThisDocument` . Он привязывает каждый элемент управления содержимым к элементу в пользовательской XML-части и задает формат отображения даты <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#5](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#5)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#5](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#5)]  
  
## <a name="run-your-code-when-the-document-is-opened"></a>Выполнять код при открытии документа  
 Создайте пользовательскую XML-часть и привяжите пользовательские элементы управления к данным при открытии документа.  
  
### <a name="to-run-your-code-when-the-document-is-opened"></a>Порядок выполнения кода после открытия документа  
  
1.  Добавьте в метод `ThisDocument_Startup` класса `ThisDocument` следующий код. Этот код получает строку XML из **employees.xml** файл, добавляет строку XML к новой пользовательской XML-части в документе и привязывает элементы управления содержимым к элементам в пользовательской XML-части.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#2](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#2](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#2)]  
  
## <a name="test-the-project"></a>Тестирование проекта  
 При открытии документа элементы управления содержимым отображают данные из элементов в пользовательской XML-части. Можно щелкнуть <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> для выбора одного из трех допустимых значений `title` элемента, которые определяются в **employees.xsd** файл. Если изменить данные в любом из элементов управления содержимым, новые значения сохраняются в пользовательской XML-части в документе.  
  
### <a name="to-test-the-content-controls"></a>Проверка элементов управления содержимым  
  
1.  Нажмите клавишу **F5** для запуска проекта.  
  
2.  Убедитесь, что таблица в документе похожа на следующую таблицу. Каждая строка во втором столбце извлекается из элемента в пользовательской XML-части в документе.  
  
    |||  
    |-|-|  
    |**Имя сотрудника**|**Карина Leal**|  
    |**Дата найма**|**1 апреля 1999 г.**|  
    |**Заголовок**|**Диспетчер**|  
  
3.  Выберите ячейку справа от **имя сотрудника** ячейку и введите другое имя.  
  
4.  Выберите ячейку справа от **Дата приема на работу** ячейку и выберите другую дату в элементе выбора даты.  
  
5.  Выберите ячейку справа от **Title** ячейку и выберите элемент из раскрывающегося списка.  
  
6.  Сохраните и закройте документ.  
  
7.  В проводнике откройте *\bin\Debug* папку в папке проекта.  
  
8.  Откройте контекстное меню для **EmployeeControls.docx** и выберите **Переименовать**.  
  
9. Назовите файл **EmployeeControls.docx.zip**.  
  
     **EmployeeControls.docx** документ сохраняется в формате Open XML. Переименовав этот документ с *ZIP-файл* расширение имени файла можно просмотреть содержимое документа. Дополнительные сведения об Open XML см. в технической статье [форматы файлов, знакомство с Office (2007) Open XML](/previous-versions/office/developer/office-2007/aa338205(v=office.12)).  
  
10. Откройте **EmployeeControls.docx.zip** файла.  
  
11. Откройте **customXml** папки.  
  
12. Откройте контекстное меню для **item2.xml** и выберите **откройте**.  
  
     Этот файл содержит пользовательскую XML-часть, которая была добавлена в документ.  
  
13. Убедитесь, что элементы `name`, `hireDate` и `title` содержат новые значения, введенные в элементы управления содержимым в документе.  
  
14. Закрыть **item2.xml** файла.  
  
## <a name="next-steps"></a>Следующие шаги  
 Дополнительные сведения об использовании элементов управления содержимым см. в следующих разделах.  
  
-   Использование всех доступных элементов управления содержимым для создания шаблона. Дополнительные сведения см. в разделе [Пошаговое руководство: Создание шаблона с помощью элементов управления содержимым](../vsto/walkthrough-creating-a-template-by-using-content-controls.md).  
  
-   Изменение данных в пользовательских XML-частях при закрытии документа. При следующем открытии документа пользователем элементы управления содержимым, привязанные к XML-элементам, покажут новые данные.  
  
-   Использование элементов управления содержимым для защиты частей документов. Дополнительные сведения см. в разделе [как: защита частей документов с помощью элементов управления содержимым](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).  
  
## <a name="see-also"></a>См. также  
 [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)   
 [Элементы управления содержимым](../vsto/content-controls.md)   
 [Практическое: Добавление элементов управления содержимым в документы Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Практическое: защита частей документов с помощью элементов управления содержимым](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)   
 [Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  