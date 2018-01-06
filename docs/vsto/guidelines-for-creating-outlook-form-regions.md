---
title: "Рекомендации по созданию Outlook области формы | Документы Microsoft"
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
- form regions [Office development in Visual Studio], guidelines
- icons [Office development in Visual Studio]
ms.assetid: 47ad59d3-5cb7-4d27-a314-9c09937143d7
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 197da04c42b97f274979e46a2ba4691747365362
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="guidelines-for-creating-outlook-form-regions"></a>Рекомендации по созданию областей формы Outlook
  Следующие сведения помогут вам оптимизировать области формы и предотвращать потенциальные проблемы.  
  
-   [Использование имен областей формы](#UsingFormRegions).  
  
-   [Отключение наследования областей формы](#DisablingInheritance).  
  
-   [Общие сведения о типах и именах классов сообщений](#ClassNames).  
  
-   [Проектирование смежных областей формы для области чтения](#ReadingPane).  
  
-   [Использование оптимального размера значков](#UsingOptimal).  
  
 Дополнительные сведения об областях форм см. в разделе [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
##  <a name="UsingFormRegions"></a> Using Form Region Names  
 Существует несколько имен, используемых для описания области формы. Важно понимать разницу между этими именами и то, как они влияют на область формы. В следующей таблице представлено описание этих имен.  
  
|Имя области формы|Описание:|  
|----------------------|-----------------|  
|Имя элемента области формы|Имя, заданное для элемента **Область формы Outlook** в диалоговом окне **Добавление нового элемента** . Это имя файла кода области формы, которое отображается в **обозревателе решений**.|  
|Свойство<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> |Вы указываете это имя на странице **Введите текст описания и выберите параметры отображения** мастера **создания области формы Outlook** . Оно отображается как свойство **FormRegionName** в окне **Свойства** .<br /><br /> Используйте свойство <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> , чтобы указать метку, идентифицирующую область формы в пользовательском интерфейсе Outlook. Для отдельных областей формы это имя отображается в виде кнопки на ленте элемента Outlook.<br /><br /> Для соседних областей формы это имя отображается в заголовке над областью формы.|  
|Атрибут Microsoft.Office.Tools.Outlook.FormRegionName|При добавлении в проект Visual Studio элемента **Область формы Outlook** Visual Studio задает в качестве значения этого свойства полное имя области формы. Полное имя по умолчанию — это имя надстройки VSTO, присоединенное к имени области формы через точку, например, `OutlookAddIn1.FormRegion1`.<br /><br /> Это полное имя также отображается как атрибут в верхней части класса фабрики областей формы.<br /><br /> Атрибут Microsoft.Office.Tools.Outlook.FormRegionName используется для уникальной идентификации области формы по всем надстройкам Outlook VSTO. Невозможно изменить значение атрибута Microsoft.Office.Tools.Outlook.FormRegionName путем переименования элемента области формы или изменения <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> свойство. Чтобы изменить это имя, необходимо изменить атрибут Microsoft.Office.Tools.Outlook.FormRegionName в файле кода области формы.|  
  
##  <a name="DisablingInheritance"></a> Disabling Form Region Inheritance  
 По умолчанию специализированный класс сообщений наследует все связи областей формы базового класса сообщений. Например, класс сообщений `IPM.Task.Contoso` является производным от IPM. Задача. Таким образом `IPM.Task.Contoso` наследует связи областей формы IPM. Задача.  
  
 Если вы не хотите, чтобы область формы была связана с каким-либо производным классом сообщений, установите для свойства <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> области формы значение **true**. Например, если вы связываете смежную область формы с IPM. Задача, а также задать <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> свойства **true**, область формы будет добавлена только к нижней части стандартной формы задач. Эта область формы не будет добавлена ни к каким настраиваемым версиям стандартной формы задач.  
  
##  <a name="ClassNames"></a> Общие сведения о типах и именах классов сообщений  
 Имя типа элемента Outlook отличается от имени класса сообщений для элемента Outlook. Например имя типа элемента RSS — Microsoft.Office.Interop.Outlook.PostItem. Имя класса сообщений для элемента RSS — IPM. Post.RSS.  
  
 Используйте имя типа для ссылки на элемент Outlook в коде. Список имен типов см. в разделе [Associating a Form Region with an Outlook Message Class](../vsto/associating-a-form-region-with-an-outlook-message-class.md).  
  
 Используйте имя класса сообщений элемента Outlook в мастере **создания области формы Outlook** , чтобы связать этот элемент с областью формы. Список допустимых имен классов сообщений см. в разделе [Associating a Form Region with an Outlook Message Class](../vsto/associating-a-form-region-with-an-outlook-message-class.md).  
  
##  <a name="ReadingPane"></a> Designing Adjoining Form Regions for the Reading Pane  
 Область чтения Outlook можно использовать для предварительного просмотра элемента Outlook без его открытия. Область чтения предназначена только для чтения. Таким образом, элементы управления для ввода, добавляемые в смежную область формы, например текстовое поле, могут работать некорректно при открытии элемента и области формы в области чтения.  
  
 Например, если в области чтения открыт элемент, имеющий смежную область формы, возможна следующая ситуация.  
  
1.  Выберите какой-либо текст в текстовом поле, которое находится в области формы.  
  
2.  Нажмите клавишу DELETE.  
  
3.  Вместо текста в текстовом поле удаляется все сообщение.  
  
 При конструировании смежной области формы, содержащей элементы управления для ввода, тестируйте эти элементы управления в области чтения, чтобы убедиться, что они работают правильно. Рассмотрите возможность добавления пользовательского кода, который отключает элементы управления, не работающие должным образом.  
  
 Можно также задать для свойства <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ShowInspectorRead%2A> области формы значение **False**. Тогда эту область формы нельзя будет использовать в области чтения.  
  
##  <a name="UsingOptimal"></a> Using Optimal Icon Sizes  
 Вы можете указывать, какие значки должны отображаться в области формы, задавая свойства значков в группе свойств **Значки** окна **Свойства** . Для достижения наилучшего визуального качества следуйте приведенным ниже рекомендациям.  
  
-   Для значка **Страница** используйте файл формата PNG.  
  
-   Значки**Окно** должны иметь размер 32 на 32 пикселя.  
  
-   Все остальные значки должны иметь размер 16 на 16 пикселей.  
  
 Значок **Страница** появляется в ленте инспектора для элементов, имеющих области формы "Разделить", "Заменить" или "Заменить все".  
  
 Значок **Окно** появляется в области уведомлений и в диалоговом окне ALT+TAB для открытых элементов, отображающих области формы "Заменить" и "Заменить все".  
  
## <a name="see-also"></a>См. также  
 [Доступ к области формы во время выполнения](../vsto/accessing-a-form-region-at-run-time.md)   
 [Создание областей форм Outlook](../vsto/creating-outlook-form-regions.md)   
 [Пошаговое руководство: Разработка области формы Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Как: Добавление области формы в проект надстройки Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Связывание области формы с классом сообщений Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
  
  