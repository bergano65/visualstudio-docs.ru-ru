---
title: 'Как: Добавление области формы в проект надстройки Outlook | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.Page1
- VSTO.NewFormRegionWizard.Page3
- VSTO.NewFormRegionWizard.Page2
- VSTO.NewFormRegionWizard.Page0
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], adding
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b8a02070bf76a1c4220c56afc397abb3b7fd3e1b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-form-region-to-an-outlook-add-in-project"></a>Практическое руководство. Добавление области формы в проект надстройки Outlook
  Создайте область формы для расширения стандартной или настраиваемой формы Microsoft Office Outlook с помощью мастера **создания области формы Outlook** . Вы можете создать новую область формы и разработать пользовательский интерфейс в Visual Studio или импортировать область формы, сконструированную в Outlook, и добавить код Visual Basic или C#.  
  
 Если у вас есть область формы Outlook, которую вы использовали в другом проекте Outlook, ее можно повторно использовать в текущем проекте надстройки Outlook VSTO с помощью диалогового окна **Добавление существующего элемента** . Дополнительные сведения см. в разделе [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
### <a name="to-add-a-new-form-region-to-an-outlook-project"></a>Добавление области формы в проект Outlook  
  
1.  Откройте или создайте проект надстройки VSTO Outlook в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Дополнительные сведения см. в разделе [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  В **обозревателе решений**выберите узел проекта надстройки VSTO Outlook.  
  
3.  В меню **Проект** выберите пункт **Добавить новый элемент**.  
  
4.  В диалоговом окне **Добавление нового элемента** выберите элемент **Область формы Outlook**.  
  
5.  Введите имя области формы в поле **Имя** а затем нажмите кнопку **Добавить**.  
  
     **Область формы NewOutlook** будет запущен мастер.  
  
6.  На странице **выбора способа создания области формы** выберите, хотите ли вы конструировать область формы путем перетаскивания управляемых элементов управления в визуальный конструктор или импортировать область формы, разработанной в Outlook.  
  
    > [!NOTE]  
    >  При выборе импорта области формы, разработанной в Outlook, необходимо указать расположение файла хранилища форм Outlook (OFS-файла). В область формы, разработанной в Outlook, нельзя добавлять управляемые элементы управления; можно добавить только код программной части существующего пользовательского интерфейса. Дополнительные сведения см. в разделе [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md).  
  
7.  На странице **Выберите тип области формы, которую следует создать** просмотрите типы областей формы, выберите один из них и нажмите кнопку **Далее**. Дополнительные сведения о типах областей форм см. в разделе [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md).  
  
8.  На странице **Введите текст описания и выберите параметры отображения** введите имя для области формы в поле **Имя** . Для типов областей формы "Заменить" и "Заменить все" также доступны поля **Заголовок** и **Описание** .  
  
     Сведения о том, где в Outlook отображается имя, заголовок и описание при развертывании области формы, см. в разделе [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md).  
  
9. Выберите один или несколько режимов отображения, в которых должна появляться область формы.  
  
     Все типы областей формы могут отображаться в инспекторах, в режиме создания (для создания элементов) и в режиме чтения (для просмотра элементов). Типы областей формы "Смежные", "Заменить" и "Заменить все" также могут отображаться в области чтения.  
  
10. Нажмите кнопку **Далее**.  
  
11. На странице **Укажите классы сообщений, в которых будет отображаться эта область формы** выберите стандартный класс сообщений Outlook или введите имена одного или нескольких пользовательских классов сообщений и нажмите кнопку **Готово**. Для получения дополнительной информации см. [Associating a Form Region with an Outlook Message Class](../vsto/associating-a-form-region-with-an-outlook-message-class.md).  
  
## <a name="see-also"></a>См. также  
 [Доступ к области формы во время выполнения](../vsto/accessing-a-form-region-at-run-time.md)   
 [Решения Outlook](../vsto/outlook-solutions.md)   
 [Создание областей форм Outlook](../vsto/creating-outlook-form-regions.md)   
 [Рекомендации по созданию областей формы Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Пошаговое руководство: Разработка области формы Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Пошаговое руководство: Импорт области формы, разработанной в Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [Пользовательские действия в областях формы Outlook](../vsto/custom-actions-in-outlook-form-regions.md)  
  
  