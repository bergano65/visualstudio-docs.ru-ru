---
title: "Пошаговое руководство: Разработка области формы Outlook | Документы Microsoft"
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
helpviewer_keywords: form regions [Office development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: afe17d19ebe87d34ae4857b1477be6cb3e894bb7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-designing-an-outlook-form-region"></a>Пошаговое руководство. Разработка области формы Outlook
  Пользовательские области формы расширяют стандартные или настраиваемые формы Microsoft Office Outlook. В этом пошаговом руководстве показано, как проектировать пользовательскую область формы, которая отображается в виде новой страницы в окне инспектора элемента контактов. В этой области формы отображается карта каждого адреса, указанного для контакта, путем отправки информации об адресе на веб-сайт локального поиска Windows Live. Сведения об областях форм см. в разделе [Создание областей форм Outlook](../vsto/creating-outlook-form-regions.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   Создание нового проекта надстройки Outlook VSTO  
  
-   Добавление области формы в проект надстройки VSTO  
  
-   Разработка макета области формы  
  
-   Настройка поведения области формы  
  
-   Тестирование области формы Outlook  
  
> [!NOTE]  
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] или [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)].  
  
 ![ссылка на видео](../vsto/media/playvideo.gif "ссылку видео") видео версию этого раздела см. в разделе [видео: разработка области формы Outlook](http://go.microsoft.com/fwlink/?LinkID=140824).  
  
## <a name="creating-a-new-outlook-vsto-add-in-project"></a>Создание нового проекта надстройки Outlook VSTO  
 Сначала создайте базовый проект надстройки VSTO.  
  
#### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Порядок создания нового проекта надстройки Outlook VSTO  
  
1.  В [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], создайте проект надстройки Outlook VSTO с именем **MapItAddIn**.  
  
2.  В диалоговом окне **Создание проекта** выберите **Создать каталог для решения**.  
  
3.  Сохраните проект в любом каталоге.  
  
     Дополнительные сведения см. в разделе [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
## <a name="adding-a-form-region-to-the-outlook-vsto-add-in-project"></a>Добавление области формы в проект надстройки Outlook VSTO  
 Решение надстройки Outlook VSTO может содержать один или несколько элементов области формы Outlook. Добавить элемент области формы в проект с помощью **новая область формы Outlook** мастера.  
  
#### <a name="to-add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Порядок добавления области формы в проект надстройки Outlook VSTO  
  
1.  В **обозревателе решений**выберите **MapItAddIn** проекта.  
  
2.  В меню **Проект** выберите пункт **Добавить новый элемент**.  
  
3.  В **Добавление нового элемента** установите флажок **область формы Outlook**, назовите файл **MapIt**, а затем нажмите кнопку **добавить**.  
  
     **Область формы NewOutlook** будет запущен мастер.  
  
4.  На **выберите способ создания области формы** щелкните **создавать новую область формы**, а затем нажмите кнопку **Далее**.  
  
5.  На **выберите тип области формы, которые вы хотите создать** щелкните **отдельные**и нажмите кнопку **Далее**.  
  
     Объект *отдельные* область формы добавляет новую страницу в форму Outlook. Дополнительные сведения о типах областей форм см. в разделе [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md).  
  
6.  На **введите текст описания и выберите параметры отображения** введите **Map It** в **имя** поле.  
  
     Это имя отображается на ленте окна инспектора при открытии элемента контактов.  
  
7.  Выберите **инспекторы в режиме создания** и **инспекторы в режиме чтения**, а затем нажмите кнопку **Далее**.  
  
8.  На **классы сообщений, которые будут отображать эту область формы** снимите **почтовое сообщение**выберите **контакт**и нажмите кнопку **Готово**.  
  
     Файл MapIt.cs или MapIt.vb добавляется в проект.  
  
## <a name="designing-the-layout-of-the-form-region"></a>Разработка макета области формы.  
 Визуальная разработка области формы с помощью *конструктора областей формы*. Управляемые элементы управления можно перетаскивать на поверхность конструктора областей формы. Используйте конструктор и **свойства** окна для настройки управления макета и внешнего вида.  
  
#### <a name="to-design-the-layout-of-the-form-region"></a>Порядок разработки макета области формы  
  
1.  В **обозревателе решений**, разверните **MapItAddIn** проекта, а затем дважды щелкните файл MapIt.cs или MapIt.vb, чтобы открыть конструктор областей формы.  
  
2.  Щелкните правой кнопкой мыши конструктор и нажмите кнопку **свойства**.  
  
3.  В **свойства** задайте **размер** для **664, 469**.  
  
     Это гарантирует, что область формы будет достаточно большой, чтобы отображать карту.  
  
4.  В меню **Вид** выберите пункт **Панель элементов**.  
  
5.  Из **стандартные элементы управления** вкладке **элементов**, добавьте **WebBrowser** в область формы.  
  
     **WebBrowser** будет отображать карту каждого адреса, указанного для контакта.  
  
## <a name="customizing-the-behavior-of-the-form-region"></a>Настройка поведения области формы  
 Для настройки поведения области формы во время выполнения добавьте код в обработчики событий области формы. Для этой области формы код проверяет свойства элемента Outlook и определяет, следует ли отображать область формы Map It. Если область формы отображается, код переходит на веб-сайт локального поиска Windows Live и загружает карту для каждого адреса, включенного в элемент контактов Outlook.  
  
#### <a name="to-customize-the-behavior-of-the-form-region"></a>Порядок настройки поведения области формы  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши файл MapIt.cs или MapIt.vb и нажмите кнопку **Просмотр кода**.  
  
     Файл MapIt.cs или MapIt.vb открывается в редакторе кода.  
  
2.  Разверните **фабрика областей формы** области кода.  
  
     Предоставляется класс фабрики областей формы с именем `MapItFactory`.  
  
3.  Добавьте следующий код в обработчик событий `MapItFactory_FormRegionInitializing`. Этот обработчик событий будет вызываться, когда пользователь открывает элемент контактов. Следующий код определяет, содержит ли элемент контактов адрес. Если элемент контактов не содержит адрес, этот код задает <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> свойство <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> класса **true** и область формы не отображается. В противном случае надстройка VSTO выдает событие <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> и отображает область формы.  
  
     [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
     [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]  
  
4.  Добавьте следующий код в обработчик событий <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing>. Этот код выполняет следующие задачи:  
  
    -   Сцепляет каждый адрес в элементе контактов и создает строку URL-адреса.  
  
    -   Вызывает метод <xref:System.Windows.Forms.WebBrowser.Navigate%2A> объекта <xref:System.Windows.Forms.WebBrowser> и передает строку URL-адреса в качестве параметра.  
  
     Веб-сайт локального поиска отображается в области формы Map It и представляет каждый адрес в тестовой области.  
  
     [!code-csharp[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#2)]
     [!code-vb[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#2)]  
  
## <a name="testing-the-outlook-form-region"></a>Тестирование области формы Outlook  
 При запуске проекта в Visual Studio открывается Outlook. Для просмотра области формы Map It откройте элемент контактов. Область формы Map It отображается в виде страницы в форме каждого элемента контактов, содержащего адрес.  
  
#### <a name="to-test-the-map-it-form-region"></a>Порядок тестирования области формы Map It  
  
1.  Для запуска проекта нажмите клавишу F5.  
  
     Открывается Outlook.  
  
2.  В Outlook на **Главная** щелкните **новые элементы**и нажмите кнопку **контакт**.  
  
3.  В форме контактов введите **Ann Beebe** контактного имени, а затем укажите три следующих адреса.  
  
    |Тип адреса|Адрес|  
    |------------------|-------------|  
    |**Business**|**Main St. 4567 Буффало, NY**|  
    |**Домашняя**|**Северная St. 1234 Буффало, NY**|  
    |**Другое**|**Main St. 3456 Сиэтл, WA**|  
  
4.  Сохраните и закройте элемент контактов.  
  
5.  Снова откройте **Ann Beebe** элемент контактов.  
  
6.  В **Показать** группы ленты элемента щелкните **Map It** открыть область формы Map It.  
  
     Появляется область формы Map It, где отображается веб-сайт локального поиска. **Business**, **Главная**, и **других** в тестовой области появляются адреса. Выберите в тестовой области адрес, который необходимо сопоставить.  
  
## <a name="next-steps"></a>Следующие шаги  
 Дополнительные сведения о настройке пользовательского интерфейса приложения Outlook см. в следующих разделах.  
  
-   Дополнительные сведения о настройке ленты элемента Outlook см. в разделе [Customizing a Ribbon for Outlook](../vsto/customizing-a-ribbon-for-outlook.md).  
  
## <a name="see-also"></a>См. также  
 [Доступ к области формы во время выполнения](../vsto/accessing-a-form-region-at-run-time.md)   
 [Создание областей форм Outlook](../vsto/creating-outlook-form-regions.md)   
 [Рекомендации по созданию областей формы Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Пошаговое руководство: Импорт области формы, разработанной в Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [Как: Добавление области формы в проект надстройки Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Связывание области формы с классом сообщений Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Пользовательские действия в областях форм Outlook](../vsto/custom-actions-in-outlook-form-regions.md)   
 [Практическое руководство: прекращение отображения области формы в Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)  
  
  