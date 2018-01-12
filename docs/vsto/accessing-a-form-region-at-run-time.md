---
title: "Доступ к области формы во время выполнения | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Explorers [Office development in Visual Studio]
- form regions [Office development in Visual Studio], accessing at run time
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 70e9a970251aa5b95cff5983f5e2ce5e0c804a61
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="accessing-a-form-region-at-run-time"></a>Доступ к области формы во время выполнения
  
  
|Применение|  
|----------------|  
|Сведения, приведенные в данном разделе, относятся только к следующим типам проектов и версиям Microsoft Office. Для получения дополнительной информации см. [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md).<br /><br /> **Тип проекта**<br /><br /> -Проекты надстроек VSTO<br /><br /> **Версия Microsoft Office**<br /><br /> -   [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]|  
  
 Используйте класс `Globals` для доступа к областям форм из любого места в проекте Outlook. Дополнительные сведения о `Globals` см. в описании [глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="accessing-form-regions-that-appear-in-a-specific-outlook-inspector-window"></a>Доступ к областям форм, которые отображаются в определенном окне инспектора Outlook  
 Для доступа ко всем областям форм, которые отображаются в определенном инспекторе Outlook, вызовите свойство `FormRegions` класса `Globals` и передайте в объект <xref:Microsoft.Office.Interop.Outlook.Inspector> , представляющий инспектор.  
  
 В следующем примере извлекается коллекция областей форм в инспекторе, в котором в текущий момент находится фокус. Затем производится доступ к области формы в коллекции с именем `formRegion1` и задается текст, отображаемый в текстовом поле для `Hello World`.  
  
 [!code-vb[Trin_Outlook_FR_Access#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#2)]
 [!code-csharp[Trin_Outlook_FR_Access#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#2)]  
  
## <a name="accessing-form-regions-that-appear-in-a-specific-outlook-explorer-window"></a>Доступ к областям форм, которые отображаются в определенном окне проводника Outlook  
 Для доступа ко всем областям форм, которые отображаются в определенном проводнике Outlook, вызовите свойство `FormRegions` класса `Globals` и передайте в объект <xref:Microsoft.Office.Interop.Outlook.Explorer> , представляющий проводник.  
  
 В следующем примере извлекается коллекция областей форм в проводнике, в котором в текущий момент находится фокус. Затем производится доступ к области формы в коллекции с именем `formRegion1` и задается текст, отображаемый в текстовом поле для `Hello World`.  
  
 [!code-vb[Trin_Outlook_FR_Access#3](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#3)]
 [!code-csharp[Trin_Outlook_FR_Access#3](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#3)]  
  
## <a name="accessing-all-form-regions"></a>Доступ ко всем областям форм  
 Для доступа ко всем областям форм, отображаемым во всех проводниках и инспекторах, вызовите свойство `FormRegions` класса `Globals` .  
  
 В следующем примере извлекается коллекция областей форм во всех проводниках и всех инспекторах. Затем производится доступ к области формы с именем `formRegion1` и задается текст, отображаемый в текстовом поле для `Hello World`.  
  
 [!code-vb[Trin_Outlook_FR_Access#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Access#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#1)]  
  
## <a name="accessing-controls-on-a-form-region"></a>Доступ к элементам управления в области формы  
 Для доступа к элементам управления в области формы с помощью класса `Globals` необходимо сделать эти элементы управления доступными для кода вне файла кода области формы.  
  
### <a name="form-regions-designed-in-the-form-region-designer"></a>Области формы, созданные в конструкторе областей формы  
 Для C# измените модификатор каждого элемента управления, к которому необходимо получить доступ. Для этого выделите каждый элемент управления в конструкторе областей форм и измените свойство **Модификатор** на **Внутренний** или **Общедоступный** в окне **Свойства** . Например, если изменить свойство **Модификатор** объекта `textBox1` на **Внутренний**, можно получить доступ к `textBox1` , введя `Globals.FormRegions.FormRegion1.textBox1`.  
  
 В Visual Basic изменение модификатора не требуется.  
  
### <a name="imported-form-regions"></a>Импортированные области формы  
 При импорте созданной в Outlook области формы модификатор доступа каждого элемента управления в области формы меняется на закрытый. Поскольку вы не можете использовать конструктор областей форм для изменения импортированной области формы, нет способа изменить модификатор элемента управления в окне **Свойства** .  
  
 Для включения доступа к элементу управления извне файла кода области формы создайте свойство в файле кода области формы для получения этого элемента управления.  
  
 Дополнительные сведения о создании свойств в C# см. в разделе [как: объявление и использование чтение и запись свойств &#40; И &#35; Руководство по программированию &#41; ](/dotnet/csharp/programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties).  
  
 Дополнительные сведения о создании свойств в Visual Basic см. в разделе [как: создание свойства (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/procedures/how-to-create-a-property).  
  
## <a name="see-also"></a>См. также  
 [Рекомендации по созданию областей формы Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Пошаговое руководство: Разработка области формы Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Как: Добавление области формы в проект надстройки Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Пользовательские действия в областях форм Outlook](../vsto/custom-actions-in-outlook-form-regions.md)   
 [Связывание области формы с классом сообщений Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Пошаговое руководство: Импорт области формы, разработанной в Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [Как: запретить отображение области формы Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)   
 [Создание областей форм Outlook](../vsto/creating-outlook-form-regions.md)   
 [Доступ к ленте во время выполнения](../vsto/accessing-the-ribbon-at-run-time.md)  
  
  