---
title: "Пошаговое руководство. Отладка приложения SharePoint при помощи IntelliTrace | Microsoft Docs"
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
  - "IntelliTrace [разработка приложений SharePoint в Visual Studio]"
  - "автономный сборщик данных"
  - "разработка приложений SharePoint в Visual Studio, IntelliTrace"
  - "сборщик данных"
  - "IntelliTrace"
ms.assetid: 4bd80d2f-f680-4bf4-81c3-f14e8185f6a4
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Пошаговое руководство. Отладка приложения SharePoint при помощи IntelliTrace
  С помощью IntelliTrace гораздо легче отлаживать решения SharePoint.  Традиционные отладчики показывают только моментальный снимок решения в текущий момент.  Тем не менее IntelliTrace можно использовать для просмотра прошедших событий решения и контекста, в котором эти события произошли, а также для перехода к коду.  
  
 В этом пошаговом руководстве показано, как выполнить отладку проекта SharePoint 2010 или SharePoint 2013 в Visual Studio Ultimate с помощью Microsoft Monitoring Agent для сбора данных IntelliTrace из развертываемых приложений.  Для анализа этих данных необходимо использовать Visual Studio Ultimate.  Этот проект содержит приемник компонента, который, когда компонент активен, добавляет задачу в список задач и объявление в список объявлений.  Когда компонент отключен, задача помечается как завершенная, а второе объявление добавляется в список объявлений.  Тем не менее процедура содержит логическую ошибку, препятствующую правильной работе проекта.  С помощью IntelliTrace можно найти и исправить ошибку.  
  
 **Применимо к:** Сведения из этого раздела применимы в решениях SharePoint 2010 и SharePoint 2013, созданных в Visual Studio.  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   [Создание приемника компонента](#BKMK_CreateReceiver)  
  
-   [Добавление кода в приемник компонента](#BKMK_AddCode)  
  
-   [Тестирование проекта.](#BKMK_Test1)  
  
-   [Сбор данных IntelliTrace с помощью Microsoft Monitoring Agent.](#BKMK_CollectDiagnosticData)  
  
-   [Отладка и исправление решения SharePoint](#BKMK_DebugSolution)  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Обязательные компоненты  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   Поддерживаемые версии Windows и SharePoint.  См. раздел [Требования по разработке решений SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio Ultimate.  
  
##  <a name="BKMK_CreateReceiver"></a> Создание приемника компонента  
 Сначала создайте пустой проект SharePoint с приемником компонента.  
  
#### Создание приемника компонента  
  
1.  Создайте проект решения SharePoint 2010 или SharePoint 2013 и назовите его IntelliTraceTest.  
  
     Появляется **Мастер настройки SharePoint**, в котором можно указать сайт SharePoint своего проекта и уровень доверия решения.  
  
2.  Выберите переключатель **Развернуть как решение фермы**, а затем нажмите кнопку **Готово**.  
  
     IntelliTrace работает только на решениях фермы.  
  
3.  В области **Обозреватель решений** откройте контекстное меню для узла **Компоненты** и выберите команду **Добавить компонент**.  
  
     Появится компонент Feature1.feature.  
  
4.  Откройте контекстное меню для Feature1.feature, а затем выберите **Добавить приемник событий**, чтобы добавить модуль кода в компонент.  
  
##  <a name="BKMK_AddCode"></a> Добавление кода в приемник компонента  
 Затем добавьте код в два метода приемника компонента: `FeatureActivated` и `FeatureDeactivating`.  Эти методы активируются каждый раз, когда компонент включается или отключается в SharePoint, соответственно.  
  
#### Добавление кода в приемник компонента  
  
1.  В верхней части класса `Feature1EventReceiver` добавьте следующий код для объявления переменных, которые задают сайт и дочерний сайт SharePoint:  
  
    ```vb  
    ' SharePoint site and subsite.  
    Private siteUrl As String = "http://localhost"  
    Private webUrl As String = "/"  
    ```  
  
    ```csharp  
    // SharePoint site and subsite.  
    private string siteUrl = "http://localhost";  
    private string webUrl = "/";  
    ```  
  
2.  Замените метод `FeatureActivated` следующим кодом:  
  
    ```vb  
    Public Overrides Sub FeatureActivated(ByVal properties As SPFeatureReceiverProperties)  
        Try  
            Using site As New SPSite(siteUrl)  
                Using web As SPWeb = site.OpenWeb(webUrl)  
                    ' Reference the lists.  
                    Dim announcementsList As SPList = web.Lists("Announcements")  
                    Dim taskList As SPList = web.Lists("Tasks")  
  
                    ' Add an announcement to the Announcements list.  
                    Dim listItem As SPListItem = announcementsList.Items.Add()  
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)  
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()  
                    listItem.Update()  
  
                    ' Add a task to the Task list.  
                    Dim newTask As SPListItem = taskList.Items.Add()  
                    newTask("Title") = "Deactivate feature: " & Convert.ToString(properties.Definition.DisplayName)  
                    newTask.Update()  
                End Using  
            End Using  
  
        Catch e As Exception  
            Console.WriteLine("Error: " & e.ToString())  
        End Try  
  
    End Sub  
    ```  
  
    ```csharp  
    public override void FeatureActivated(SPFeatureReceiverProperties properties)  
    {  
        try  
        {  
            using (SPSite site = new SPSite(siteUrl))  
            {  
                using (SPWeb web = site.OpenWeb(webUrl))  
                {  
                    // Reference the lists.  
                    SPList announcementsList = web.Lists["Announcements"];  
                    SPList taskList = web.Lists["Tasks"];  
  
                    // Add an announcement to the Announcements list.  
                    SPListItem listItem = announcementsList.Items.Add();  
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;  
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " + DateTime.Now.ToString();  
                    listItem.Update();  
  
                    // Add a task to the Task list.  
                    SPListItem newTask = taskList.Items.Add();  
                    newTask["Title"] = "Deactivate feature: " + properties.Definition.DisplayName;  
                    newTask.Update();  
                }  
            }  
        }  
  
        catch (Exception e)  
        {  
            Console.WriteLine("Error: " + e.ToString());  
        }  
  
    }  
    ```  
  
3.  Замените метод `FeatureDeactivating` следующим кодом:  
  
    ```vb  
    Public Overrides Sub FeatureDeactivating(ByVal properties As SPFeatureReceiverProperties)  
        ' The following line induces an error to demonstrate debugging.  
        ' Remove this line later for proper operation.  
        Throw New System.InvalidOperationException("Serious error occurred!")  
        Try  
            Using site As New SPSite(siteUrl)  
                Using web As SPWeb = site.OpenWeb(webUrl)  
                    ' Reference the lists.  
                    Dim taskList As SPList = web.Lists("Tasks")  
                    Dim announcementsList As SPList = web.Lists("Announcements")  
  
                    ' Add an announcement that the feature was deactivated.  
                    Dim listItem As SPListItem = announcementsList.Items.Add()  
                    listItem("Title") = "Deactivated Feature: " & Convert.ToString(properties.Definition.DisplayName)  
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was deactivated on: " & DateTime.Now.ToString()  
                    listItem.Update()  
  
                    ' Find the task that the feature receiver added to the Task list when the  
                    ' feature was activated.  
                    Dim qry As New SPQuery()  
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>"  
                    Dim taskItems As SPListItemCollection = taskList.GetItems(qry)  
  
                    For Each taskItem As SPListItem In taskItems  
                        ' Mark the task as complete.  
                        taskItem("PercentComplete") = 1  
                        taskItem("Status") = "Completed"  
                        taskItem.Update()  
                    Next  
                End Using  
  
            End Using  
  
        Catch e As Exception  
            Console.WriteLine("Error: " & e.ToString())  
        End Try  
  
    End Sub  
    ```  
  
    ```csharp  
    public override void FeatureDeactivating(SPFeatureReceiverProperties properties)  
    {  
        // The following line induces an error to demonstrate debugging.  
        // Remove this line later for proper operation.  
        throw new System.InvalidOperationException("A serious error occurred!");   
        try  
        {  
            using (SPSite site = new SPSite(siteUrl))  
            {  
                using (SPWeb web = site.OpenWeb(webUrl))  
                {  
                    // Reference the lists.  
                    SPList taskList = web.Lists["Tasks"];  
                    SPList announcementsList = web.Lists["Announcements"];  
  
                    // Add an announcement that the feature was deactivated.  
                    SPListItem listItem = announcementsList.Items.Add();  
                    listItem["Title"] = "Deactivated Feature: " + properties.Definition.DisplayName;  
                    listItem["Body"] = properties.Definition.DisplayName + " was deactivated on: " + DateTime.Now.ToString();  
                    listItem.Update();  
  
                    // Find the task that the feature receiver added to the Task list when the  
                    // feature was activated.  
                    SPQuery qry = new SPQuery();  
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>";  
                    SPListItemCollection taskItems = taskList.GetItems(qry);  
  
                    foreach (SPListItem taskItem in taskItems)  
                    {  
                        // Mark the task as complete.  
                        taskItem["PercentComplete"] = 1;  
                        taskItem["Status"] = "Completed";  
                        taskItem.Update();  
                    }  
                }  
            }  
  
        }  
  
        catch (Exception e)  
        {  
            Console.WriteLine("Error: " + e.ToString());  
        }  
    }  
    ```  
  
##  <a name="BKMK_Test1"></a> Тестирование проекта.  
 Теперь, когда код добавлен в приемник компонента и сборщик данных выполняется, разверните и запустите решение SharePoint для тестирования правильности выполнения.  
  
> [!IMPORTANT]  
>  В этом примере возникает ошибка в обработчике событий FeatureDeactivating.  Далее в пошаговом руководстве ошибка обнаруживается с помощью .iTrace\-файла, созданного сборщиком данных.  
  
#### Тестирование проекта  
  
1.  Разверните решение в SharePoint, а затем откройте сайт SharePoint в браузере.  
  
     Компонент автоматически активируется, что приводит к добавлению приемником компонента объявления и задачи.  
  
2.  Отобразить содержимое списков объявлений и задач.  
  
     В списке объявлений должно присутствовать новое объявление с именем **Activated feature: IntelliTraceTest\_Feature1**, а в списке задач должна присутствовать новая задача с именем **Deactivate feature: IntelliTraceTest\_Feature1**.  Если один из этих элементов отсутствует, проверьте, активирован ли компонент.  Если он не активирован, активируйте его.  
  
3.  Отключите компонент, выполнив следующие действия:  
  
    1.  В SharePoint в меню **Действия сайта** выберите **Параметры сайта**.  
  
    2.  В разделе **Действия сайта** выберите ссылку **Управление компонентами сайта**.  
  
    3.  Рядом с **IntelliTraceTest Feature1**, нажмите кнопку **Деактивировать**.  
  
    4.  На странице предупреждений выберите ссылку **Отключить этот компонент**.  
  
     Обработчик событий FeatureDeactivating\(\) вызывает ошибку.  
  
##  <a name="BKMK_CollectDiagnosticData"></a> Сбор данных IntelliTrace с помощью Microsoft Monitoring Agent.  
 После установки Microsoft Monitoring Agent в систему, на которой выполняется SharePoint, можно отлаживать решения SharePoint с помощью более конкретных данных, по сравнению с возвращаемыми IntelliTrace универсальными сведениями.  Агент работает вне Visual Studio с помощью командлетов PowerShell для захвата отладочной информации в процессе выполнения решения SharePoint.  
  
> [!NOTE]  
>  Сведения о конфигурации в этом разделе относятся к этому примеру.  Дополнительные сведения о других параметрах конфигурации см. в разделе [Использование автономного сборщика данных IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
1.  На компьютере где запущен SharePoint [set up Microsoft Monitoring Agent and start to monitor your solution](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
2.  Отключите компонент:  
  
    1.  В SharePoint в меню **Действия сайта** выберите **Параметры сайта**.  
  
    2.  В разделе **Действия сайта** выберите ссылку **Управление компонентами сайта**.  
  
    3.  Рядом с **IntelliTraceTest Feature1**, нажмите кнопку **Деактивировать**.  
  
    4.  На странице предупреждений выберите ссылку **Отключить этот компонент**.  
  
     Возникает ошибка \(в данном случае из\-за возникшей в обработчике событий FeatureDeactivating\(\) ошибки\).  
  
3.  В окне PowerShell запустите команду [Stop\-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313687) для создания .iTrace\-файла, остановки отслеживания и перезапуска решения SharePoint.  
  
     **Stop\-WebApplicationMonitoring**  *"\<SharePointSite\>\\\<SharePointAppName\>"*  
  
##  <a name="BKMK_DebugSolution"></a> Отладка и исправление решения SharePoint  
 Теперь можно просмотреть файл журнала IntelliTrace в Visual Studio для поиска и исправления ошибки в решении SharePoint.  
  
#### Отладка и исправление решения SharePoint  
  
1.  В папке \\IntelliTraceLogs откройте .iTrace\-файл в Visual Studio.  
  
     Появится страница **Сводка IntelliTrace**.  Поскольку ошибка не была обработана, идентификатор корреляции SharePoint \(GUID\) отображается в области необработанного исключения раздела **Анализ**.  Нажмите кнопку **Стек вызовов**, если необходимо просмотреть стек вызовов, где возникла ошибка.  
  
2.  Нажмите кнопку **Отладка исключения**.  
  
     При появлении соответствующего запроса загрузите символьные файлы.  В окне **IntelliTrace** исключение подсвечивается как «Возникла cерьёзная ошибка\!».  
  
     В окне IntelliTrace выберите исключение для отображения кода, который завершился ошибкой.  
  
3.  Исправьте ошибку, открыв решение SharePoint и, затем, или закомментировав, или удалив оператор **throw** в верхней части процедуры FeatureDeactivating\(\).  
  
4.  Перестройте решение в Visual Studio, а затем заново разверните его в SharePoint.  
  
5.  Отключите компонент, выполнив следующие действия:  
  
    1.  В SharePoint в меню **Действия сайта** выберите **Параметры сайта**.  
  
    2.  В разделе **Действия сайта** выберите ссылку **Управление компонентами сайта**.  
  
    3.  Рядом с **IntelliTraceTest Feature1**, нажмите кнопку **Деактивировать**.  
  
    4.  На странице предупреждений выберите ссылку **Отключить этот компонент**.  
  
6.  Откройте список задач и проверьте, что значение **Состояние** задачи Deactivate равно "Завершено", а значение **% завершения** равно "100%".  
  
     Теперь код будет выполнен правильно.  
  
## См. также  
 [Проверка и отладка кода SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md)   
 [Использование IntelliTrace](../debugger/intellitrace.md)   
 [Пошаговое руководство. Проверка кода SharePoint при помощи модульных тестов](http://msdn.microsoft.com/ru-ru/3d2c4aaf-3cb5-4825-b21b-f10222abe818)  
  
  