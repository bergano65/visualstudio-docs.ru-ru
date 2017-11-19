---
title: "Пошаговое руководство: Создание веб-часть Silverlight, отображающей данные OData для SharePoint | Документы Microsoft"
ms.custom: 
ms.date: 02/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.SPE.SilverlightWebPart
dev_langs:
- VB
- CSharp
ms.assetid: 92d55e68-8f3f-4bf7-a21b-801c298b04c4
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0a6999a7a390c207c184f26d36e0ca5d64d5fef5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint"></a>Пошаговое руководство. Создание веб-части Silverlight, отображающей данные OData для SharePoint
  SharePoint 2010 предоставляет свои данные списка с помощью OData. Служба OData реализована в SharePoint службой RESTful (ListData.svc). В данном пошаговом руководстве показано, как создать веб-часть SharePoint, в которой размещается приложение Silverlight. Приложение Silverlight отображает информацию списка извещений SharePoint с помощью ListData.svc. Дополнительные сведения см. в разделе [интерфейс REST SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=225999) и [Open Data Protocol](http://go.microsoft.com/fwlink/?LinkId=226000).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   Поддерживаемые редакции Microsoft Windows и SharePoint. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Требования по разработке решений SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].  
  
##  <a name="creating-a-silverlight-application-and-silverlight-web-part"></a>Создание приложения и веб-части Silverlight  
 Сначала необходимо создать приложение Silverlight в Visual Studio. Приложение Silverlight извлекает данные из списка извещений SharePoint с помощью службы ListData.svc.  
  
> [!NOTE]  
>  Версии Silverlight младше 4.0 не поддерживают необходимые интерфейсы для ссылки на данные списка SharePoint.  
  
#### <a name="to-create-a-silverlight-application-and-silverlight-web-part"></a>Создание приложения и веб-части Silverlight  
  
1.  В строке меню выберите **файл**, **New**, **проекта** для отображения **новый проект** диалоговое окно.  
  
2.  Разверните **SharePoint** узел в рамках одного **Visual C#** или **Visual Basic**, а затем выберите **2010** узла.  
  
3.  В области шаблонов выберите **веб-часть Silverlight SharePoint 2010** шаблона.  
  
4.  В **имя** введите **SLWebPartTest** и выберите **ОК** кнопки.  
  
     **Мастер настройки SharePoint** откроется диалоговое окно.  
  
5.  На **Укажите сайт и уровень безопасности для отладки** введите URL-адрес сайта сервера SharePoint, где требуется отладка определения сайта или использовать расположение по умолчанию (http://*системное имя*/) .  
  
6.  В **Какова степень доверия для этого решения SharePoint?** выберите **развернуть как решение фермы** переключатель.  
  
     Хотя в этом примере используется решение фермы, проекты веб-части Silverlight можно развертывать либо как решения фермы, либо как изолированные решения. Дополнительные сведения об изолированных решениях и решениях фермы см. в разделе [замечания об изолированных решениях](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  В **способ связать веб-часть Silverlight** раздел **задайте параметры конфигурации Silverlight** выберите **создайте новый проект Silverlight и свяжите его с веб-части** переключатель.  
  
8.  Изменение **имя** для **SLApplication**, задайте **язык** либо **Visual Basic** или **Visual C#**, а затем установите **версии Silverlight** для **Silverlight 4.0**.  
  
9. Выберите **Готово** кнопки. Проекты откроются в **обозревателе решений**.  
  
     Решение содержит 2 проекта: приложение Silverlight и веб-часть Silverlight. Приложение Silverlight извлекает и отображает данные списка из SharePoint, а веб-часть Silverlight размещает приложение Silverlight, позволяя просматривать его в SharePoint.  
  
##  <a name="customizing-the-silverlight-application"></a>Настройка приложения Silverlight  
 Добавление кода и элементов оформления в приложение Silverlight.  
  
#### <a name="to-customize-the-silverlight-application"></a>Настройка приложения Silverlight  
  
1.  Добавьте ссылку на сборку в System.Windows.Data в приложении Silverlight. Дополнительные сведения см. в разделе [как: Добавление и удаление ссылок с помощью диалоговое окно Добавить ссылку](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
2.  В **обозревателе решений**, откройте контекстное меню для **ссылки**, а затем выберите **добавить ссылку на службу**.  
  
    > [!NOTE]  
    >  Если вы используете Visual Basic, необходимо выбрать **Показать все файлы** значок в верхней части **обозревателе решений** для отображения **ссылки** узла.  
  
3.  В адресной строке **добавить ссылку на службу** диалогового окна введите URL-адрес сайта SharePoint, такие как **http://MySPSite**и нажмите кнопку **Go** кнопки.  
  
     Когда Silverlight находит службу OData SharePoint ListData.svc, он заменяет адрес полным URL-адресом службы. В данном случае http://myserver становится http://myserver/_vti_bin/ListData.svc.  
  
4.  Выберите **ОК** кнопку, чтобы добавить ссылку на службу в проект и используйте имя службы по умолчанию: ServiceReference1.  
  
5.  В строке меню последовательно выберите **Сборка**и **Собрать решение**.  
  
6.  Добавьте в проект новый источник данных на основе службы SharePoint. Для этого в строке меню выберите **представление**, **другие окна**, **источники данных**.  
  
     **Источники данных** окне показаны все доступные данные списков SharePoint, например задачи, извещения и календарь.  
  
7.  Добавьте данные списка извещений в приложение Silverlight. Можно перетащить «Извещения» из **источники данных** на окно конструктора Silverlight.  
  
     При этом создается элемент управления "сетка", привязанный к списку извещений сайта SharePoint.  
  
8.  Измените размер элемента управления "сетка" в соответствии с размером страницы Silverlight.  
  
9. В файле кода MainPage.xaml (MainPage.xaml.cs для Visual C# или MainPage.xaml.vb для Visual Basic) добавьте следующие ссылки на пространства имен.  
  
    ```vb  
    ' Add the following three Imports statements.  
    Imports SLApplication.ServiceReference1  
    Imports System.Windows.Data  
    Imports System.Data.Services.Client  
    ```  
  
    ```csharp  
    // Add the following three using statements.  
    using SLApplication.ServiceReference1;  
    using System.Windows.Data;  
    using System.Data.Services.Client;  
    ```  
  
10. Добавьте следующие объявления переменных в начало класса.  
  
    ```vb  
    Private context As TeamSiteDataContext  
    Private myCollectionViewSource As CollectionViewSource  
    Private announcements As New DataServiceCollection(Of AnnouncementsItem)()  
    ```  
  
    ```csharp  
    private TeamSiteDataContext context;  
    private CollectionViewSource myCollectionViewSource;  
    DataServiceCollection<AnnouncementsItem> announcements = new DataServiceCollection<AnnouncementsItem>();  
    ```  
   
11. Замените процедуру `UserControl_Loaded` следующим кодом.  
  
    ```vb  
    Private Sub UserControl_Loaded_1(sender As Object, e As RoutedEventArgs)  
        ' The URL for the OData service.  
        ' Replace <server name> in the next line with the name of your SharePoint server.  
        context = New TeamSiteDataContext(New Uri("http://<server name>/_vti_bin/ListData.svc"))  
  
        ' Do not load your data at design time.  
        If Not System.ComponentModel.DesignerProperties.GetIsInDesignMode(Me) Then  
            'Load your data here and assign the results to the CollectionViewSource.  
            myCollectionViewSource =   DirectCast(Me.Resources("announcementsViewSource"), System.Windows.Data.CollectionViewSource)  
            announcements.LoadCompleted += New EventHandler(Of LoadCompletedEventArgs)(AddressOf announcements_LoadCompleted)  
            announcements.LoadAsync(context.Announcements)  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void UserControl_Loaded_1(object sender, RoutedEventArgs e)  
    {  
        // The URL for the OData service.  
        // Replace <server name> in the next line with the name of your   
        // SharePoint server.  
        context = new TeamSiteDataContext(new Uri("http://ServerName>/_vti_bin/ListData.svc"));  
  
        // Do not load your data at design time.  
        if (!System.ComponentModel.DesignerProperties.GetIsInDesignMode(this))  
        {  
            //Load your data here and assign the results to the CollectionViewSource.  
            myCollectionViewSource = (System.Windows.Data.CollectionViewSource)this.Resources["announcementsViewSource"];  
            announcements.LoadCompleted += new EventHandler<LoadCompletedEventArgs>(announcements_LoadCompleted);  
            announcements.LoadAsync(context.Announcements);  
        }  
    }  
    ```  
     Обязательно замените *ServerName* заполнитель с именем сервера, на котором выполняется SharePoint.  
  
12. Добавьте следующую процедуру обработки ошибок.  
  
    ```vb  
    Private Sub announcements_LoadCompleted(sender As Object, e As LoadCompletedEventArgs)  
        ' Handle any errors.  
        If e.[Error] Is Nothing Then  
            myCollectionViewSource.Source = announcements  
        Else  
            MessageBox.Show(String.Format("ERROR: {0}", e.[Error].Message))  
        End If  
    End Sub  
  
    ```  
  
    ```csharp  
    void announcements_LoadCompleted(object sender, LoadCompletedEventArgs e)  
    {  
        // Handle any errors.  
        if (e.Error == null)  
        {  
            myCollectionViewSource.Source = announcements;  
        }  
        else  
        {  
            MessageBox.Show(string.Format("ERROR: {0}", e.Error.Message));  
        }  
    }  
    ```  
       
## <a name="modifying-the-silverlight-web-part"></a>Изменение веб-части Silverlight  
 Измените свойство в проекте веб-части Silverlight, чтобы включить отладку Silverlight.  
  
#### <a name="to-modify-the-silverlight-web-part"></a>Изменение веб-части Silverlight  
  
1.  Откройте контекстное меню для проекта веб-части Silverlight (**SLWebPartTest**), а затем выберите **свойства**.  
  
2.  В **свойства** окно, выберите **SharePoint** вкладки.  
  
3.  Если он еще не выбран, выберите **включить отладку Silverlight (вместо отладки скриптов)** флажок.  
  
4.  Сохраните проект.  
  
##  <a name="testing-the-silverlight-web-part"></a>Тестирование веб-части Silverlight  
 Протестируйте новую веб-часть Silverlight в SharePoint, чтобы убедиться в том, что он правильно отображает данные списка SharePoint.  
  
#### <a name="to-test-the-silverlight-web-part"></a>Тестирование веб-части Silverlight  
  
1.  Нажмите клавишу F5, чтобы выполнить сборку и запуск решения SharePoint.  
  
2.  В SharePoint на **действия сайта** меню, выберите **новую страницу**.  
  
3.  В **новая страница** диалоговое окно, введите заголовок, например **SL Web Part Test**и нажмите кнопку **создать** кнопки.  
  
4.  В конструкторе страниц на **средства правки** выберите **вставить**.  
  
5.  В области вкладок выберите **веб-часть**.  
  
6.  В **категории** выберите **настраиваемый** папки.  
  
7.  В **веб-части** выберите веб-часть Silverlight, а затем выберите **добавить** кнопку, чтобы добавить веб-часть в конструктор.  
  
8.  Веб-страницы, вы должны были внесены все добавления, выберите **страницы** , а затем выберите **сохранить и закрыть** кнопки на панели инструментов.  
  
     Веб-часть Silverlight теперь должна отображать данные извещений с сайта SharePoint. По умолчанию страница хранится в страницах сайта в SharePoint.  
  
    > [!NOTE]  
    >  При доступе к данным в Silverlight между доменами, Silverlight защищается от уязвимостей безопасности, которые могут быть использованы для эксплуатации веб-приложений в своих целях. Если возникли проблемы при доступе к удаленным данным в Silverlight см. раздел [внесения службы через границы домена](http://go.microsoft.com/fwlink/?LinkId=223276).  
  
## <a name="see-also"></a>См. также  
 [Создание веб-частей для SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Развертывание, публикация и обновление пакетов решений SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)  
  
  
