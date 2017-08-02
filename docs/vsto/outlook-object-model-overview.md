---
title: "Общие сведения об объектной модели Outlook"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.ProjectItem.OutlookAddin"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Outlook [разработка решений Office в Visual Studio], обзор объектной модели"
  - "объектные модели [разработка решений Office в Visual Studio], Office"
  - "объекты [разработка решений Office в Visual Studio], объектные модели Office"
  - "объектные модели [разработка решений Office в Visual Studio], Outlook"
  - "Office - объектные модели"
ms.assetid: 59704974-b7d9-46d6-949c-e97349c75279
caps.latest.revision: 59
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 58
---
# Общие сведения об объектной модели Outlook
  Для разработки надстроек VSTO для Microsoft Office Outlook вы можете взаимодействовать с объектами, которые предоставляются объектной моделью Outlook. Объектная модель Outlook предоставляет классы и интерфейсы, которые представляют элементы пользовательского интерфейса. Например, объект <xref:Microsoft.Office.Interop.Outlook.Application> представляет все приложение, объект <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> — папку, содержащую электронные сообщения или другие элементы, а объект <xref:Microsoft.Office.Interop.Outlook.MailItem> — электронное сообщение.  
  
 Этот раздел содержит краткий обзор некоторых основных объектов в объектной модели Outlook. Список документации для более глубокого изучения объектной модели Outlook см. в разделе [Использование документации по объектной модели Outlook](#refdoc).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 ![ссылка на видео](~/docs/data-tools/media/playvideo.gif "ссылка на видео") Соответствующие демонстрационные видеоролики см. в разделе [Инструкции. Использование Outlook для создания настраиваемого отчета о задаче](http://go.microsoft.com/fwlink/?LinkID=130315).  
  
## Доступ к объектам в проекте Outlook  
 Outlook предоставляет множество различных объектов, с которыми можно взаимодействовать. Для эффективного использования объектной модели вы должны быть знакомы со следующими объектами верхнего уровня:  
  
-   <xref:Microsoft.Office.Interop.Outlook.Application>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Explorer>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Inspector>  
  
-   <xref:Microsoft.Office.Interop.Outlook.MAPIFolder>  
  
-   <xref:Microsoft.Office.Interop.Outlook.MailItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.TaskItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.ContactItem>  
  
### Объект приложения  
 Объект <xref:Microsoft.Office.Interop.Outlook.Application> представляет приложение Outlook. Это объект самого верхнего уровня в объектной модели Outlook. Ниже перечислены некоторые наиболее важные члены этого объекта.  
  
-   Метод [CreateItem](http://msdn.microsoft.com/ru-ru/771707fb-5f34-473d-9fdf-09a6a7f55ece), который можно использовать для создания элемента, например электронного сообщения, задачи или встречи.  
  
-   Свойство <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A>, которое можно использовать для доступа к окнам с содержимым папки в пользовательском интерфейсе Outlook.  
  
-   Свойство <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A>, которое можно использовать для доступа к окнам с содержимым одного элемента, например электронного сообщения или приглашения на собрание.  
  
 Чтобы получить экземпляр <xref:Microsoft.Office.Interop.Outlook.Application>, используйте поле Application класса `ThisAddIn` в проекте. Для получения дополнительной информации см. [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md).  
  
> [!NOTE]  
>  Чтобы избежать появления предупреждений системы безопасности при использовании свойств и методов, блокируемых системой безопасности объектной модели Outlook, следует получать объекты Outlook из поля Application класса `ThisAddIn`. Дополнительные сведения см. в разделе [Рекомендации по обеспечению безопасности для решений Office](../vsto/specific-security-considerations-for-office-solutions.md).  
  
### Объект Explorer  
 Объект <xref:Microsoft.Office.Interop.Outlook.Explorer> представляет окно, отображающее содержимое папки с такими элементами, как электронные сообщения, задачи и встречи. Объект <xref:Microsoft.Office.Interop.Outlook.Explorer> содержит методы и свойства, с помощью которых можно изменять окно, а также события, возникающие при изменении окна.  
  
 Чтобы получить объект <xref:Microsoft.Office.Interop.Outlook.Explorer>, выполните одно из следующих действий.  
  
-   Используйте свойство <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> объекта <xref:Microsoft.Office.Interop.Outlook.Application> для доступа ко всем объектам <xref:Microsoft.Office.Interop.Outlook.Explorer> в Outlook.  
  
-   Используйте метод <xref:Microsoft.Office.Interop.Outlook._Application.ActiveExplorer%2A> объекта <xref:Microsoft.Office.Interop.Outlook.Application>, чтобы получить <xref:Microsoft.Office.Interop.Outlook.Explorer>, который имеет фокус в данный момент.  
  
-   Используйте метод GetExplorer объекта <xref:Microsoft.Office.Interop.Outlook.MAPIFolder>, чтобы получить <xref:Microsoft.Office.Interop.Outlook.Explorer> для текущей папки.  
  
### Объект Inspector  
 Объект <xref:Microsoft.Office.Interop.Outlook.Inspector> представляет окно, в котором отображается отдельный элемент, например электронное сообщение, задача или встреча. Объект <xref:Microsoft.Office.Interop.Outlook.Inspector> содержит методы и свойства, с помощью которых можно изменять окно, а также события, возникающие при изменении окна.  
  
 Чтобы получить объект <xref:Microsoft.Office.Interop.Outlook.Inspector>, выполните одно из следующих действий.  
  
-   Используйте свойство <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> объекта <xref:Microsoft.Office.Interop.Outlook.Application> для доступа ко всем объектам <xref:Microsoft.Office.Interop.Outlook.Inspector> в Outlook.  
  
-   Используйте метод <xref:Microsoft.Office.Interop.Outlook._Application.ActiveInspector%2A> объекта <xref:Microsoft.Office.Interop.Outlook.Application>, чтобы получить <xref:Microsoft.Office.Interop.Outlook.Inspector>, который имеет фокус в данный момент.  
  
-   Используйте метод GetInspector определенного элемента, такого как <xref:Microsoft.Office.Interop.Outlook.MailItem> или <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>, для извлечения инспектора, связанного с ним.  
  
### Объект MAPIFolder  
 Объект <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> представляет папку, содержащую электронные сообщения, контакты, задачи и другие элементы. Outlook предоставляет 16 объектов <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> по умолчанию.  
  
 Объекты <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> по умолчанию определяются значениями перечисления <xref:Microsoft.Office.Interop.Outlook.OlDefaultFolders>. Например:  
  
 Microsoft.Office.Interop.Outlook.OlDefaultFolders.olFolderInbox соответствует папке **Входящие** в Outlook.  
  
 Пример получения доступа к <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> по умолчанию и создания <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> см. в разделе [Практическое руководство. Программное создание настраиваемых элементов папок](../vsto/how-to-programmatically-create-custom-folder-items.md).  
  
### Объект MailItem  
 Объект <xref:Microsoft.Office.Interop.Outlook.MailItem> представляет электронное сообщение. Объекты <xref:Microsoft.Office.Interop.Outlook.MailItem> обычно находятся в папках, таких как **Входящие**, **Отправленные** и **Исходящие**.<xref:Microsoft.Office.Interop.Outlook.MailItem> предоставляет свойства и методы, которые можно использовать для создания и отправки электронных сообщений.  
  
 Пример, демонстрирующий создание электронного сообщения, см. в разделе [Практическое руководство. Программное создание элемента электронной почты](../vsto/how-to-programmatically-create-an-e-mail-item.md).  
  
### Объект AppointmentItem  
 Объект <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> представляет собрание, однократную или повторяющуюся встречу или собрание в папке **Календарь**. Объект <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> содержит методы для выполнения таких действий, как ответ на приглашения на собрание и их пересылка, а также свойства, определяющие сведения о встрече, например время и место проведения.  
  
 Пример, демонстрирующий создание встречи, см. в разделе [Практическое руководство. Программное создание приглашения на собрание](../vsto/how-to-programmatically-create-a-meeting-request.md).  
  
### Объект TaskItem  
 Объект <xref:Microsoft.Office.Interop.Outlook.TaskItem> представляет задачу, выполняемую в течение заданного промежутка времени. Объекты <xref:Microsoft.Office.Interop.Outlook.TaskItem> расположены в папке **Задачи**.  
  
 Чтобы создать задачу, используйте метод [CreateItem](http://msdn.microsoft.com/ru-ru/771707fb-5f34-473d-9fdf-09a6a7f55ece) объекта <xref:Microsoft.Office.Interop.Outlook.Application> и передайте значение <xref:Microsoft.Office.Interop.Outlook.OlItemType.olTaskItem> для параметра.  
  
### Объект ContactItem  
 Объект <xref:Microsoft.Office.Interop.Outlook.ContactItem> представляет контакт в папке **Контакты**. Объекты <xref:Microsoft.Office.Interop.Outlook.ContactItem> содержат различные контактные данные для людей, которые они представляют, например адреса, электронные адреса и номера телефонов.  
  
 Пример, демонстрирующий создание нового контакта, см. в разделе [Практическое руководство. Программное добавление записи в контакты Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md). Пример, демонстрирующий поиск существующего контакта, см. в разделе [Практическое руководство. Программный поиск определенного контакта](../vsto/how-to-programmatically-search-for-a-specific-contact.md).  
  
##  <a name="refdoc"></a> Использование документации по объектной модели Outlook  
 Полные сведения об объектной модели Outlook см. в справочнике по основной сборке взаимодействия \(PIA\) Outlook и в справочнике по объектной модели VBA.  
  
### Документация по основной сборке взаимодействия  
 В справочных документах по основной сборке взаимодействия Outlook описываются типы основной сборки взаимодействия для Outlook 2010. Дополнительные сведения см. в разделе [Документация по основной сборке взаимодействия Outlook 2010](http://go.microsoft.com/fwlink/?LinkId=189580).  
  
 Помимо информации о всех типах в основных сборках взаимодействия, эта документация также содержит дополнительные сведения о структуре основных сборок взаимодействия и примеры кода для общих задач автоматизации Outlook.  
  
### Справочник по объектной модели VBA  
 В справочных документах по объектной модели VBA объектная модель Outlook описана в том виде, в котором она предоставляется коду Visual Basic для приложений. Дополнительные сведения см. в разделе [Справочник по объектной модели Outlook 2010](http://go.microsoft.com/fwlink/?LinkId=199769).  
  
 Все объекты и элементы в справочнике объектной модели VBA соответствуют типам и участникам основной сборки взаимодействия Outlook. Например, объект Inspector в справочнике по объектной модели VBA соответствует объекту <xref:Microsoft.Office.Interop.Outlook.Inspector> в основной сборке взаимодействия Outlook. Несмотря на то что в справочнике по объектной модели VBA содержатся примеры кода для большинства свойств, методов и событий, необходимо преобразовать код VBA в этом справочнике в код Visual Basic или Visual C\#, если требуется использовать их в проекте надстройки VSTO для Outlook, создаваемом с помощью Visual Studio.  
  
### См. также  
  
|Заголовок|Описание|  
|---------------|--------------|  
|[Работа с элементами контактов](../vsto/working-with-contact-items.md)|Содержит разделы, в которых описывается выполнение задач с контактами.|  
|[Работа с элементами почты](../vsto/working-with-mail-items.md)|Содержит разделы, в которых описывается выполнение задач с элементами почты.|  
|[Работа с папками](../vsto/working-with-folders.md)|Содержит разделы, в которых описывается выполнение задач с папками.|  
|[Работа с элементами календаря](../vsto/working-with-calendar-items.md)|Содержит разделы, в которых описывается выполнение задач с элементами календаря.|  
|[Практическое руководство. Программное определение текущего элемента Outlook](../vsto/how-to-programmatically-determine-the-current-outlook-item.md)|Здесь показано, как отобразить имя текущей папки и некоторые сведения о выбранном элементе.|  
  
  