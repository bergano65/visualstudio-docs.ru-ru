---
title: "Доступ к области формы во время выполнения"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "инспекторы [разработка решений Office в Visual Studio]"
  - "проводники [разработка решений Office в Visual Studio]"
  - "области формы [разработка решений Office в Visual Studio], доступ во время выполнения"
ms.assetid: 58eaa9e0-acba-4a13-a6dd-b7e37a38156e
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Доступ к области формы во время выполнения
  
  
|Применение|  
|----------------|  
|Сведения, приведенные в данном разделе, относятся только к следующим типам проектов и версиям Microsoft Office. Для получения дополнительной информации см. [Доступность функций по типам приложений Office и проектов](../vsto/features-available-by-office-application-and-project-type.md).<br /><br /> **Тип проекта**<br /><br /> -   Проекты надстроек VSTO<br /><br /> **Версия Microsoft Office**<br /><br /> -   [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]|  
  
 Используйте класс `Globals` для доступа к областям форм из любого места в проекте Outlook. Дополнительные сведения о классе `Globals` см. в разделе [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Доступ к областям форм, которые отображаются в определенном окне инспектора Outlook  
 Для доступа ко всем областям форм, которые отображаются в определенном инспекторе Outlook, вызовите свойство `FormRegions` класса `Globals` и передайте в объект <xref:Microsoft.Office.Interop.Outlook.Inspector>, представляющий инспектор.  
  
 В следующем примере извлекается коллекция областей форм в инспекторе, в котором в текущий момент находится фокус. Затем производится доступ к области формы в коллекции с именем `formRegion1` и задается текст, отображаемый в текстовом поле для `Hello World`.  
  
 [!code-csharp[Trin_Outlook_FR_Access#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#2)]
 [!code-vb[Trin_Outlook_FR_Access#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#2)]  
  
## Доступ к областям форм, которые отображаются в определенном окне проводника Outlook  
 Для доступа ко всем областям форм, которые отображаются в определенном проводнике Outlook, вызовите свойство `FormRegions` класса `Globals` и передайте в объект <xref:Microsoft.Office.Interop.Outlook.Explorer>, представляющий проводник.  
  
 В следующем примере извлекается коллекция областей форм в проводнике, в котором в текущий момент находится фокус. Затем производится доступ к области формы в коллекции с именем `formRegion1` и задается текст, отображаемый в текстовом поле для `Hello World`.  
  
 [!code-csharp[Trin_Outlook_FR_Access#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#3)]
 [!code-vb[Trin_Outlook_FR_Access#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#3)]  
  
## Доступ ко всем областям форм  
 Для доступа ко всем областям форм, отображаемым во всех проводниках и инспекторах, вызовите свойство `FormRegions` класса `Globals`.  
  
 В следующем примере извлекается коллекция областей форм во всех проводниках и всех инспекторах. Затем производится доступ к области формы с именем `formRegion1` и задается текст, отображаемый в текстовом поле для `Hello World`.  
  
 [!code-csharp[Trin_Outlook_FR_Access#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#1)]
 [!code-vb[Trin_Outlook_FR_Access#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#1)]  
  
## Доступ к элементам управления в области формы  
 Для доступа к элементам управления в области формы с помощью класса `Globals` необходимо сделать эти элементы управления доступными для кода вне файла кода области формы.  
  
### Области формы, созданные в конструкторе областей формы  
 Для C\# измените модификатор каждого элемента управления, к которому необходимо получить доступ. Для этого выделите каждый элемент управления в конструкторе областей форм и измените свойство **Модификатор** на **Внутренний** или **Общедоступный** в окне **Свойства**. Например, если изменить свойство **Модификатор** объекта `textBox1` на **Внутренний**, можно получить доступ к `textBox1`, введя `Globals.FormRegions.FormRegion1.textBox1`.  
  
 В Visual Basic изменение модификатора не требуется.  
  
### Импортированные области формы  
 При импорте созданной в Outlook области формы модификатор доступа каждого элемента управления в области формы меняется на закрытый. Поскольку вы не можете использовать конструктор областей форм для изменения импортированной области формы, нет способа изменить модификатор элемента управления в окне **Свойства**.  
  
 Для включения доступа к элементу управления извне файла кода области формы создайте свойство в файле кода области формы для получения этого элемента управления.  
  
 Дополнительные сведения о создании свойств в C\# см. в разделе [Практическое руководство. Объявление и использование свойств чтения и записи &#40;руководство по программированию на C&#35;&#41;](http://msdn.microsoft.com/library/a4962fef-af7e-4c4b-a929-4ae4d646ab8a).  
  
 Дополнительные сведения о создании свойств в Visual Basic см. в разделе [НЕ В СБОРКЕ: Практическое руководство. Добавление полей и свойств в класс](http://msdn.microsoft.com/ru-ru/ae53f61b-3abc-413e-8931-703c5f5e8fc2).  
  
## См. также  
 [Рекомендации по созданию областей формы Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Пошаговое руководство. Разработка области формы Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Практическое руководство. Добавление области формы в проект надстройки Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Пользовательские действия в областях форм Outlook](../vsto/custom-actions-in-outlook-form-regions.md)   
 [Связывание области формы с классом сообщений Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Пошаговое руководство. Импорт области формы, созданной в Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [Практическое руководство. Отсутствие отображения области формы в Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)   
 [Создание областей форм Outlook](../vsto/creating-outlook-form-regions.md)   
 [Доступ к ленте во время выполнения](../vsto/accessing-the-ribbon-at-run-time.md)  
  
  