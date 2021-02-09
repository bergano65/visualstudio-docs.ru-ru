---
title: Общие сведения об объектной модели Outlook
description: Узнайте, как можно взаимодействовать с объектами, предоставляемыми объектной моделью Outlook, для разработки надстроек VSTO для Microsoft Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.OutlookAddin
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], object model overview
- object models [Office development in Visual Studio], Office
- objects [Office development in Visual Studio], Office object models
- object models [Office development in Visual Studio], Outlook
- Office object models
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 316ead76be1f84fccc6f675b204587008e8a194a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885304"
---
# <a name="outlook-object-model-overview"></a>Общие сведения об объектной модели Outlook
  Для разработки надстроек VSTO для Microsoft Office Outlook вы можете взаимодействовать с объектами, которые предоставляются объектной моделью Outlook. Объектная модель Outlook предоставляет классы и интерфейсы, которые представляют элементы пользовательского интерфейса. Например, объект <xref:Microsoft.Office.Interop.Outlook.Application> представляет все приложение, объект <xref:Microsoft.Office.Interop.Outlook.Folder> — папку, содержащую электронные сообщения или другие элементы, а объект <xref:Microsoft.Office.Interop.Outlook.MailItem> — электронное сообщение.

 Этот раздел содержит краткий обзор некоторых основных объектов в объектной модели Outlook. Дополнительные сведения о всей объектной модели Outlook см. в разделе [использование документации по объектной модели](#refdoc)Outlook.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="access-objects-in-an-outlook-project"></a>Доступ к объектам в проекте Outlook
 Outlook предоставляет множество различных объектов, с которыми можно взаимодействовать. Для эффективного использования объектной модели вы должны быть знакомы со следующими объектами верхнего уровня:

- <xref:Microsoft.Office.Interop.Outlook.Application>

- <xref:Microsoft.Office.Interop.Outlook.Explorer>

- <xref:Microsoft.Office.Interop.Outlook.Inspector>

- <xref:Microsoft.Office.Interop.Outlook.Folder>

- <xref:Microsoft.Office.Interop.Outlook.MailItem>

- <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>

- <xref:Microsoft.Office.Interop.Outlook.TaskItem>

- <xref:Microsoft.Office.Interop.Outlook.ContactItem>

### <a name="application-object"></a>Объект приложения
 Объект <xref:Microsoft.Office.Interop.Outlook.Application> представляет приложение Outlook. Это объект самого верхнего уровня в объектной модели Outlook. Ниже перечислены некоторые наиболее важные члены этого объекта.

- Метод [CreateItem](/previous-versions/office/developer/office-2003/aa220082(v=office.11)) , который можно использовать для создания элемента, например электронного сообщения, задачи или встречи.

- Свойство <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> , которое можно использовать для доступа к окнам с содержимым папки в пользовательском интерфейсе Outlook.

- Свойство <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> , которое можно использовать для доступа к окнам с содержимым одного элемента, например электронного сообщения или приглашения на собрание.

  Чтобы получить экземпляр <xref:Microsoft.Office.Interop.Outlook.Application> объекта, используйте поле приложения `ThisAddIn` класса в проекте. Дополнительные сведения см. в разделе [программирование VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

> [!NOTE]
> Чтобы избежать предупреждений системы безопасности при использовании свойств и методов, блокируемых системой безопасности объектной модели Outlook, можно получить объекты Outlook из поля приложения `ThisAddIn` класса. Дополнительные сведения см. в статье [вопросы безопасности для решений Office](../vsto/specific-security-considerations-for-office-solutions.md).

### <a name="explorer-object"></a>Объект Explorer
 Объект <xref:Microsoft.Office.Interop.Outlook.Explorer> представляет окно, отображающее содержимое папки с такими элементами, как электронные сообщения, задачи и встречи. Объект <xref:Microsoft.Office.Interop.Outlook.Explorer> содержит методы и свойства, с помощью которых можно изменять окно, а также события, возникающие при изменении окна.

 Чтобы получить объект <xref:Microsoft.Office.Interop.Outlook.Explorer> , выполните одно из следующих действий.

- Используйте свойство <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> объекта <xref:Microsoft.Office.Interop.Outlook.Application> для доступа ко всем объектам <xref:Microsoft.Office.Interop.Outlook.Explorer> в Outlook.

- Используйте метод <xref:Microsoft.Office.Interop.Outlook._Application.ActiveExplorer%2A> объекта <xref:Microsoft.Office.Interop.Outlook.Application> , чтобы получить <xref:Microsoft.Office.Interop.Outlook.Explorer> , который имеет фокус в данный момент.

- Используйте метод `GetExplorer` объекта <xref:Microsoft.Office.Interop.Outlook.Folder>, чтобы получить <xref:Microsoft.Office.Interop.Outlook.Explorer> для текущей папки.

### <a name="inspector-object"></a>Объект инспектора
 Объект <xref:Microsoft.Office.Interop.Outlook.Inspector> представляет окно, в котором отображается отдельный элемент, например электронное сообщение, задача или встреча. Объект <xref:Microsoft.Office.Interop.Outlook.Inspector> содержит методы и свойства, с помощью которых можно изменять окно, а также события, возникающие при изменении окна.

 Чтобы получить объект <xref:Microsoft.Office.Interop.Outlook.Inspector> , выполните одно из следующих действий.

- Используйте свойство <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> объекта <xref:Microsoft.Office.Interop.Outlook.Application> для доступа ко всем объектам <xref:Microsoft.Office.Interop.Outlook.Inspector> в Outlook.

- Используйте метод <xref:Microsoft.Office.Interop.Outlook._Application.ActiveInspector%2A> объекта <xref:Microsoft.Office.Interop.Outlook.Application> , чтобы получить <xref:Microsoft.Office.Interop.Outlook.Inspector> , который имеет фокус в данный момент.

- Используйте метод `GetInspector` определенного элемента, такого как <xref:Microsoft.Office.Interop.Outlook.MailItem> или <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>, для извлечения инспектора, связанного с ним.

### <a name="folder-object"></a>Объект Folder
 Объект <xref:Microsoft.Office.Interop.Outlook.Folder> представляет папку, содержащую электронные сообщения, контакты, задачи и другие элементы. Outlook предоставляет 16 объектов <xref:Microsoft.Office.Interop.Outlook.Folder> по умолчанию.

 Объекты <xref:Microsoft.Office.Interop.Outlook.Folder> по умолчанию определяются значениями перечисления <xref:Microsoft.Office.Interop.Outlook.OlDefaultFolders> . Например,

 Microsoft. Office. Interop. Outlook. Олдефаултфолдерс. Олфолдеринбокс соответствует папке **"Входящие"** в Outlook.

 Пример, демонстрирующий доступ к по умолчанию <xref:Microsoft.Office.Interop.Outlook.Folder> и создание нового <xref:Microsoft.Office.Interop.Outlook.Folder> , см. [в разделе как программно создавать пользовательские элементы папки](../vsto/how-to-programmatically-create-custom-folder-items.md).

### <a name="mailitem-object"></a>Объект MailItem
 Объект <xref:Microsoft.Office.Interop.Outlook.MailItem> представляет электронное сообщение. Объекты<xref:Microsoft.Office.Interop.Outlook.MailItem> обычно находятся в папках, таких как **Входящие**, **Отправленные** и **Исходящие**. <xref:Microsoft.Office.Interop.Outlook.MailItem> предоставляет свойства и методы, которые можно использовать для создания и отправки электронных сообщений.

 Пример создания сообщения электронной почты см. [в разделе руководство. Программное создание элемента электронной почты](../vsto/how-to-programmatically-create-an-e-mail-item.md).

### <a name="appointmentitem-object"></a>Объект Аппоинтментитем
 Объект <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> представляет собрание, однократную или повторяющуюся встречу или собрание в папке **Календарь** . Объект <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> содержит методы для выполнения таких действий, как ответ на приглашения на собрание и их пересылка, а также свойства, определяющие сведения о встрече, например время и место проведения.

 Пример создания встречи см. в разделе как создать приглашение на [собрание программными средствами](../vsto/how-to-programmatically-create-a-meeting-request.md).

### <a name="taskitem-object"></a>Объект TaskItem
 Объект <xref:Microsoft.Office.Interop.Outlook.TaskItem> представляет задачу, выполняемую в течение заданного промежутка времени. Объекты<xref:Microsoft.Office.Interop.Outlook.TaskItem> расположены в папке **Задачи** .

 Чтобы создать задачу, используйте метод [CreateItem](/previous-versions/office/developer/office-2003/aa220082(v=office.11)) объекта <xref:Microsoft.Office.Interop.Outlook.Application> и передайте значение <xref:Microsoft.Office.Interop.Outlook.OlItemType.olTaskItem> для параметра.

### <a name="contactitem-object"></a>Объект ContactItem
 Объект <xref:Microsoft.Office.Interop.Outlook.ContactItem>представляет контакт в папке **Контакты** . Объекты<xref:Microsoft.Office.Interop.Outlook.ContactItem> содержат различные контактные данные для людей, которые они представляют, например адреса, электронные адреса и номера телефонов.

 Пример создания нового контакта см. в разделе [как добавить запись в контакты Outlook программным способом](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md). Пример поиска существующего контакта см. [в разделе как выполнять поиск определенного контакта программным способом](../vsto/how-to-programmatically-search-for-a-specific-contact.md).

## <a name="use-the-outlook-object-model-documentation"></a><a name="refdoc"></a> Использование документации по объектной модели Outlook
 Полные сведения об объектной модели Outlook см. в справочнике по основной сборке взаимодействия (PIA) Outlook и в справочнике по объектной модели VBA.

### <a name="primary-interop-assembly-reference"></a>Ссылка на основную сборку взаимодействия
 В справочных документах по основной сборке взаимодействия Outlook описываются типы основной сборки взаимодействия для Outlook 2010. Дополнительные сведения см. в разделе [Справочник по основной сборке взаимодействия Outlook 2010](/previous-versions/office/developer/office-2010/bb652780(v=office.14)).

 Помимо информации о всех типах в основных сборках взаимодействия, эта документация также содержит дополнительные сведения о структуре основных сборок взаимодействия и примеры кода для общих задач автоматизации Outlook.

### <a name="vba-object-model-reference"></a>Справочник по объектной модели VBA
 В справочных документах по объектной модели VBA объектная модель Outlook описана в том виде, в котором она предоставляется коду Visual Basic для приложений. Дополнительные сведения см. в разделе [Справочник по объектной модели Outlook 2010](/office/vba/api/overview/Outlook/object-model).

 Все объекты и элементы в справочнике объектной модели VBA соответствуют типам и участникам основной сборки взаимодействия Outlook. Например, объект инспектора в справочнике по объектной модели VBA соответствует <xref:Microsoft.Office.Interop.Outlook.Inspector> объекту в основной сборке взаимодействия Outlook. Несмотря на то что в справочнике по объектной модели VBA содержатся примеры кода для большинства свойств, методов и событий, необходимо преобразовать код VBA в этом справочнике в код Visual Basic или Visual C#, если требуется использовать их в проекте надстройки VSTO для Outlook, создаваемом с помощью Visual Studio.

### <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Работа с элементами контактов](../vsto/working-with-contact-items.md)|Содержит разделы, в которых описывается выполнение задач с контактами.|
|[Работа с элементами почты](../vsto/working-with-mail-items.md)|Содержит разделы, в которых описывается выполнение задач с элементами почты.|
|[Работа с папками](../vsto/working-with-folders.md)|Содержит разделы, в которых описывается выполнение задач с папками.|
|[Работа с элементами календаря](../vsto/working-with-calendar-items.md)|Содержит разделы, в которых описывается выполнение задач с элементами календаря.|
|[Руководство. Программное определение текущего элемента Outlook](../vsto/how-to-programmatically-determine-the-current-outlook-item.md)|Здесь показано, как отобразить имя текущей папки и некоторые сведения о выбранном элементе.|
