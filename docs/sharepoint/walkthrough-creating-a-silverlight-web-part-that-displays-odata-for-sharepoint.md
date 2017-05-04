---
title: "Пошаговое руководство. Создание веб-части Silverlight, отображающей данные OData для SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "02/22/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.SPE.SilverlightWebPart"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 92d55e68-8f3f-4bf7-a21b-801c298b04c4
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Пошаговое руководство. Создание веб-части Silverlight, отображающей данные OData для SharePoint
  SharePoint 2010 предоставляет свои данные списка с помощью OData.  В SharePoint служба OData реализована RESTful службой ListData.svc.  В данном пошаговом руководстве показано, как создать веб\-часть SharePoint, в которой размещается приложение Silverlight.  Приложение Silverlight отображает информацию списка объявлений с помощью ListData.svc.  Дополнительные сведения см. в разделах [Интерфейс REST SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=225999) и [Open Data Protocol](http://go.microsoft.com/fwlink/?LinkId=226000).  
  
 В этом пошаговом руководстве показано выполнение следующих задач.  
  
-   [Создание приложения и веб-части Silverlight](#BKMK_creatingSLApp).  
  
-   [Настройка приложения Silverlight](#BKMK_customizeSLApp).  
  
-   [Настройка приложения Silverlight](#BKMK_customizeSLApp).  
  
-   [Настройка приложения Silverlight](#BKMK_customizeSLApp).  
  
-   [Тестирование веб-части Silverlight](#BKMK_testSLApp).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Обязательные компоненты  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   Поддерживаемые выпуски Microsoft Windows и SharePoint.  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Требования по разработке решений SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].  
  
##  <a name="BKMK_creatingSLApp"></a> Создание приложения и веб\-части Silverlight  
 Сначала необходимо создать приложение Silverlight в Visual Studio.  Приложение Silverlight извлекает данные из списка объявлений SharePoint с помощью службы ListData.svc.  
  
> [!NOTE]  
>  Версии Silverlight младше 4.0 не поддерживают необходимые интерфейсы для ссылки на данные списка SharePoint.  
  
#### Создание приложения и веб\-части Silverlight  
  
1.  В строке меню последовательно выберите пункты **Файл**, **Создать**, **Проект**, чтобы открыть диалоговое окно **Новый проект**.  
  
2.  Разверните узел **SharePoint**, расположенный в области **Visual C\#** или **Visual Basic**, и выберите узел **2010**.  
  
3.  В области шаблонов выберите шаблон **Веб\-часть Silverlight SharePoint 2010**.  
  
4.  В поле **Имя** введите SLWebPartTest и нажмите кнопку **ОК**.  
  
     Появится диалоговое окно **Мастер настройки SharePoint**.  
  
5.  На странице **Укажите сайт и уровень безопасности для отладки** введите URL\-адрес сайта сервера SharePoint, на котором будет выполняться отладка определения сайта, или примите значение по умолчанию \(http:\/\/*system name*\/\).  
  
6.  В разделе **Какова степень доверия для этого решения SharePoint?** выберите **Развернуть как решение фермы**.  
  
     Хотя в этом примере используется решение фермы, проекты веб\-части Silverlight можно развертывать либо как решения фермы, либо как изолированные решения.  Дополнительные сведения об изолированных решениях и решениях фермы см. в разделе [Замечания об обезвреженных решениях](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  В разделе **Как связать веб\-часть Silverlight** на странице **Задайте параметры конфигурации Silverlight** выберите переключатель **Создать проект Silverlight и связать его с веб\-частью**.  
  
8.  Измените **Имя** на SLApplication, задайте для свойства **Язык** значение **Visual Basic** или **Visual C \#** и присвойте свойству **Версия Silverlight** значение **Silverlight 4.0**.  
  
9. Нажмите кнопку **Готово**.  Проекты откроются в **обозревателе решений**.  
  
     Решение содержит 2 проекта: приложение Silverlight и веб\-часть Silverlight.  Приложение Silverlight извлекает и отображает данные списка из SharePoint, а веб\-часть Silverlight размещает приложение Silverlight, позволяя просматривать его в SharePoint.  
  
##  <a name="BKMK_customizeSLApp"></a> Настройка приложения Silverlight  
 Добавьте код и элементы оформления в приложение Silverlight.  
  
#### Чтобы настроить приложение Silverlight  
  
1.  Добавьте ссылку на сборку в System.Windows.Data в приложении Silverlight.  Для получения дополнительной информации см. [Практическое руководство. Добавление и удаление ссылок с помощью диалогового окна "Добавление ссылок"](http://msdn.microsoft.com/ru-ru/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
2.  В области **Обозреватель решений** откройте контекстное меню для узла **Ссылки** и выберите **Добавить ссылку на службу**.  
  
    > [!NOTE]  
    >  Если используется Visual Basic, следует выбрать значок **Показать все файлы** в верхней части **обозревателя решений** для отображения узла **Ссылки**.  
  
3.  В поле Адрес диалогового окна **Добавить ссылку на службу** введите URL\-адрес сайта SharePoint, например **http:\/\/MySPSite**, затем нажмите кнопку **Перейти**.  
  
     Когда Silverlight находит OData службу SharePoint ListData.svc, он заменяет адрес полным URL\-адресом службы.  Для этого примера http:\/\/myserver становится http:\/\/myserver\/\_vti\_bin\/ListData.svc.  
  
4.  Нажмите кнопку **ОК**, чтобы добавить ссылку на службу в проект, и используйте имя службы по умолчанию, ServiceReference1.  
  
5.  В строке меню последовательно выберите **Сборка** и **Собрать решение**.  
  
6.  Добавьте в проект новый источник данных на основе службы SharePoint.  Для этого в строке меню выберите **Вид**, **Другие окна**, **Источники данных**.  
  
     Окно **Источники данных** отображает все доступные данные списков SharePoint, например задачи, объявления и календарь.  
  
7.  Добавьте данные списка объявлений в приложение Silverlight.  Можно перетащить «Объявления» из окна **Источники данных** в конструктор Silverlight.  
  
     При этом создается элемент управления "сетка", привязанный к списку объявлений сайта SharePoint.  
  
8.  Измените размер элемента управления "сетка" в соответствии с размером страницы Silverlight.  
  
9. В файле кода MainPage.xaml \(MainPage.xaml.cs для Visual C\# или MainPage.xaml.vb для Visual Basic\) добавьте следующие ссылки на пространства имен.  
  
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
  
<!-- TODO: review snippet reference      [!CODE [SP_SLWebPart#1](SP_SLWebPart#1)]  -->  
  
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
  
<!-- TODO: review snippet reference      [!CODE [SP_SLWebPart#2](SP_SLWebPart#2)]  -->  
  
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
  
<!-- TODO: review snippet reference      [!CODE [SP_SLWebPart#3](SP_SLWebPart#3)]  -->  
  
     Обязательно замените заполнитель *ServerName* на имя сервера, на котором выполняется SharePoint.  
  
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
  
<!-- TODO: review snippet reference      [!CODE [SP_SLWebPart#4](SP_SLWebPart#4)]  -->  
  
## Изменение веб\-части Silverlight  
 Измените свойство в проекте веб\-части Silverlight, чтобы включить отладку Silverlight.  
  
#### Чтобы изменить веб\-часть Silverlight  
  
1.  Откройте контекстное меню для проекта веб\-части Silverlight \(**SLWebPartTest**\) и выберите пункт **Свойства**.  
  
2.  В окне **Свойства** выберите вкладку **SharePoint**.  
  
3.  Установите флажок **Включить отладку Silverlight \(вместо отладки скриптов\)**, если он не установлен.  
  
4.  Сохраните проект.  
  
##  <a name="BKMK_testSLApp"></a> Тестирование веб\-части Silverlight  
 Протестируйте новую веб\-часть Silverlight в SharePoint, чтобы убедиться в том, что он правильно отображает данные списка SharePoint.  
  
#### Тестирование веб\-части Silverlight  
  
1.  Нажмите клавишу F5, чтобы собрать и запустить решение SharePoint.  
  
2.  В SharePoint, в меню **Действия сайта** выберите команду **Создать страницу**.  
  
3.  В диалоговом окне **Создать страницу** введите заголовок, например "SL Web Part Test", а затем нажмите кнопку **Создать**.  
  
4.  В конструкторе веб\-страницы, на вкладке **Средства редактирования** выберите **Вставить**.  
  
5.  В области вкладок выберите **Веб\-часть**.  
  
6.  В поле **Категории** выберите папку **Настраиваемая**.  
  
7.  В списке **веб\-частей** выберите веб\-часть Silverlight, затем нажмите кнопку **Добавить**, чтобы добавить веб\-часть в конструктор.  
  
8.  После того как на веб\-страницу были внесены все добавления, перейдите на вкладку **Страница** и затем нажмите кнопку **Сохранить & закрыть** на панели инструментов.  
  
     Веб\-часть Silverlight теперь должна отображать данные объявлений с сайта SharePoint.  По умолчанию страница хранится в страницах сайта в SharePoint.  
  
    > [!NOTE]  
    >  При доступе к данным в Silverlight между доменами, Silverlight защищается от уязвимостей безопасности, которые могут быть использованы, для эксплуатации веб\-приложений в своих целях.  Если у вас возникнут проблемы при доступе к удаленным данным в Silverlight см. раздел [Создание службы, доступной за пределами границ домена](http://go.microsoft.com/fwlink/?LinkId=223276).  
  
## См. также  
 [Создание веб-частей для SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Развертывание, публикация и обновление пакетов решений SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)  
  
  