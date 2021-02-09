---
title: Создание веб-части Silverlight с отображением OData для SharePoint
titleSuffix: ''
description: Создайте веб-часть Silverlight, которая отображает OData для SharePoint. Настройка приложения Silverlight и изменение и тестирование веб-части Silverlight.
ms.custom: SEO-VS-2020
ms.date: 02/22/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.SPE.SilverlightWebPart
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ee35ecc9cfa49f445e93677df9d2917150bc1e74
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847834"
---
# <a name="walkthrough-create-a-silverlight-web-part-that-displays-odata-for-sharepoint"></a>Пошаговое руководство. Создание веб-части Silverlight, которая отображает OData для SharePoint
  SharePoint 2010 предоставляет свои данные списка с помощью OData. Служба OData реализована в SharePoint службой RESTful (ListData.svc). В данном пошаговом руководстве показано, как создать веб-часть SharePoint, в которой размещается приложение Silverlight. Приложение Silverlight отображает информацию списка извещений SharePoint с помощью ListData.svc. Дополнительные сведения см. в разделе интерфейс и [Open Data Protocol](https://www.odata.org/) [SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ff521587(v=office.14)) .

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства требуются следующие компоненты:

- Поддерживаемые редакции Microsoft Windows и SharePoint.

- [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].

## <a name="create-a-silverlight-application-and-silverlight-web-part"></a>Создание приложения Silverlight и веб-части Silverlight
 Сначала необходимо создать приложение Silverlight в Visual Studio. Приложение Silverlight извлекает данные из списка извещений SharePoint с помощью службы ListData.svc.

> [!NOTE]
> Версии Silverlight младше 4.0 не поддерживают необходимые интерфейсы для ссылки на данные списка SharePoint.

#### <a name="to-create-a-silverlight-application-and-silverlight-web-part"></a>Создание приложения Silverlight и веб-части Silverlight

1. В строке меню выберите **файл**  >  **создать**  >  **проект** , чтобы открыть диалоговое окно **Новый проект** .

2. Разверните узел **SharePoint** под управлением **Visual C#** или **Visual Basic**, а затем выберите узел **2010** .

3. В области Шаблоны выберите шаблон **веб-части Silverlight SharePoint 2010** .

4. В поле **имя** введите **слвебпарттест** , а затем нажмите кнопку **ОК** .

    Откроется диалоговое окно **Мастер настройки SharePoint** .

5. На странице **Укажите сайт и уровень безопасности для отладки** введите URL-адрес сайта SharePoint Server, на котором нужно выполнить отладку определения сайта, или используйте расположение по умолчанию (http://<em>System Name</em>/).

6. В разделе **что такое уровень доверия для этого решения SharePoint?** выберите параметр **Развернуть как решение фермы** .

    Хотя в этом примере используется решение фермы, проекты веб-части Silverlight можно развертывать либо как решения фермы, либо как изолированные решения. Дополнительные сведения о изолированных решениях и решениях фермы см. в статье [рекомендации по изолированным решениям](../sharepoint/sandboxed-solution-considerations.md).

7. В разделе **как связать с веб-частью Silverlight** на странице **Указание сведений о конфигурации Silverlight** выберите **создать новый проект Silverlight и свяжите его с параметром веб-части** .

8. Измените **имя** на **слаппликатион**, задайте для параметра **Language** значение **Visual Basic** или **Visual C#**, а затем задайте для параметра **версия Silverlight** значение **Silverlight 4,0**.

9. Нажмите кнопку **Готово**. Проекты отображаются в **Обозреватель решений**.

     Решение содержит 2 проекта: приложение Silverlight и веб-часть Silverlight. Приложение Silverlight извлекает и отображает данные списка из SharePoint, а веб-часть Silverlight размещает приложение Silverlight, позволяя просматривать его в SharePoint.

## <a name="customize-the-silverlight-application"></a>Настройка приложения Silverlight
 Добавление кода и элементов оформления в приложение Silverlight.

#### <a name="to-customize-the-silverlight-application"></a>Настройка приложения Silverlight

1. Добавьте ссылку на сборку в System.Windows.Data в приложении Silverlight. Дополнительные сведения см. в разделе [как добавить или удалить ссылки с помощью диалогового окна "Добавление ссылки"](/previous-versions/wkze6zky(v=vs.140)).

2. В **Обозреватель решений** откройте контекстное меню для **ссылок** и выберите **Добавление ссылки на службу**.

    > [!NOTE]
    > Если вы используете Visual Basic, необходимо выбрать значок **Показать все файлы** в верхней части **Обозреватель решений** , чтобы отобразить узел **ссылки** .

3. В поле адрес диалогового окна **Добавление ссылки на службу** введите URL-адрес сайта SharePoint, например **http://MySPSite** , и нажмите кнопку **Go (перейти** ).

     Когда Silverlight находит службу OData SharePoint ListData.svc, он заменяет адрес полным URL-адресом службы. В этом примере http://myserver принимается http://myserver/_vti_bin/ListData.svc .

4. Нажмите кнопку **ОК** , чтобы добавить ссылку на службу в проект, и используйте имя службы по умолчанию ServiceReference1.

5. В строке меню последовательно выберите **Сборка** > **Собрать решение**.

6. Добавьте в проект новый источник данных на основе службы SharePoint. Для этого в строке меню выберите **Просмотреть**  >  **другие**  >  **Источники данных** Windows.

     В окне **Источники данных** отображаются все доступные данные списка SharePoint, такие как задачи, объявления и календарь.

7. Добавьте данные списка извещений в приложение Silverlight. Можно перетащить "объявления" из окна **Источники данных** в конструктор Silverlight.

     При этом создается элемент управления "сетка", привязанный к списку извещений сайта SharePoint.

8. Измените размер элемента управления "сетка" в соответствии с размером страницы Silverlight.

9. В файле кода MainPage. XAML (*MainPage.XAML.CS* для Visual C# или *MainPage. XAML. vb* для Visual Basic) добавьте следующие ссылки на пространства имен.

    ```vb
    ' Add the following three Imports statements.
    Imports SLApplication.ServiceReference1
    Imports System.Windows.Data
    Imports System.Data.Services.Client
    ```

    ```csharp
    // Add the following three using directives.
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

     Обязательно замените заполнитель *ServerName* именем сервера, на котором работает SharePoint.

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

## <a name="modify-the-silverlight-web-part"></a>Изменение веб-части Silverlight
 Измените свойство в проекте веб-части Silverlight, чтобы включить отладку Silverlight.

#### <a name="to-modify-the-silverlight-web-part"></a>Изменение веб-части Silverlight

1. Откройте контекстное меню проекта веб-части Silverlight (**слвебпарттест**) и выберите пункт **свойства**.

2. В окне **Свойства** перейдите на вкладку **SharePoint** .

3. Установите флажок **включить отладку Silverlight (вместо отладки скриптов)** , если он еще не установлен.

4. Сохраните проект.

## <a name="test-the-silverlight-web-part"></a>Тестирование веб-части Silverlight
 Протестируйте новую веб-часть Silverlight в SharePoint, чтобы убедиться в том, что он правильно отображает данные списка SharePoint.

#### <a name="to-test-the-silverlight-web-part"></a>Тестирование веб-части Silverlight

1. Нажмите клавишу **F5** , чтобы создать и запустить решение SharePoint.

2. В SharePoint в меню **действия сайта** выберите пункт **создать страницу**.

3. В диалоговом окне **Новая страница** введите заголовок, например **тест веб-части SL**, а затем нажмите кнопку **создать** .

4. В конструкторе страниц на вкладке **средства редактирования** нажмите кнопку **Вставить**.

5. На полосе вкладок выберите **веб-часть**.

6. В поле **категории** выберите **пользовательскую** папку.

7. В списке **веб-части** выберите веб-часть Silverlight, а затем нажмите кнопку **Добавить** , чтобы добавить веб-часть в конструктор.

8. После внесения всех дополнений в нужную веб-страницу перейдите на вкладку **страница** и нажмите кнопку **сохранить & закрыть** на панели инструментов.

     Веб-часть Silverlight теперь должна отображать данные извещений с сайта SharePoint. По умолчанию страница хранится в страницах сайта в SharePoint.

    > [!NOTE]
    > При доступе к данным в Silverlight между доменами, Silverlight защищается от уязвимостей безопасности, которые могут быть использованы для эксплуатации веб-приложений в своих целях. Если при доступе к удаленным данным в Silverlight возникают проблемы, см. раздел [обеспечение доступности службы через границы домена](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc197955(v=vs.95)).

## <a name="see-also"></a>См. также раздел
- [Создание веб-частей для SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Развертывание, публикация и обновление пакетов решений SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)