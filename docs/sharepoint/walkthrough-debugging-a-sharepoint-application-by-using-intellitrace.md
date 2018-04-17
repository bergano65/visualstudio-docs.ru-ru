---
title: 'Пошаговое руководство: Отладка приложения SharePoint с помощью IntelliTrace | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IntelliTrace [SharePoint development in Visual Studio]
- standalone data collector
- SharePoint development in Visual Studio, IntelliTrace
- data collector
- IntelliTrace
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 173dbc74a24166f69ca97da6d5f68332345b90ea
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-debugging-a-sharepoint-application-by-using-intellitrace"></a>Пошаговое руководство. Отладка приложения SharePoint при помощи IntelliTrace

С помощью IntelliTrace гораздо легче отлаживать решения SharePoint. Традиционные отладчики показывают только снимок решения в текущий момент. Тем не менее IntelliTrace можно использовать для просмотра прошедших событий решения и контекста, в котором эти события произошли, а также для перехода к коду.

 В этом пошаговом руководстве показано, как отлаживать проект SharePoint 2010 или SharePoint 2013 в Visual Studio с помощью Microsoft Monitoring Agent для сбора данных IntelliTrace из развернутых приложений. Для анализа этих данных, необходимо использовать Visual Studio Enterprise. Этот проект содержит приемник компонента, который при активации этой функции добавляет задачу в список задач и объявление в список объявлений. Если компонент отключен, задача помечается как завершенная, а второе объявление добавляется в список объявлений. Однако процедура содержит логическую ошибку, препятствующую проекта выполняется правильно. С помощью IntelliTrace вы сможете найти и исправить ошибку.

 **Применяется к:** информация в этой статье относится к SharePoint 2010 и SharePoint 2013 решения, созданные в Visual Studio.

 В данном пошаговом руководстве рассмотрены следующие задачи:

- [Создание приемника компонента](#BKMK_CreateReceiver)

- [Добавление кода в приемник компонента](#BKMK_AddCode)

- [Тестирование проекта](#BKMK_Test1)

- [Сбор данных IntelliTrace с помощью Microsoft Monitoring Agent](#BKMK_CollectDiagnosticData)

- [Отладка и исправление решения SharePoint](#BKMK_DebugSolution)

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Предварительные требования

Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.

- Поддерживаемые выпуски Windows и SharePoint. В разделе [требования по разработке решений SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).

- Visual Studio Enterprise.

## <a name="BKMK_CreateReceiver"></a> Создание приемника компонента

Сначала создайте пустой проект SharePoint с приемником компонента.

1. Создайте проект решения SharePoint 2010 или SharePoint 2013 и назовите его **IntelliTraceTest**.

     **Мастер настройки SharePoint** отображается, в котором можно указать сайт SharePoint для вашего проекта и уровень доверия решения.

2. Выберите **развернуть как решение фермы** переключатель, а затем выберите **Готово** кнопки.

     IntelliTrace работает только в решениях фермы.

3. В **обозревателе решений**, откройте контекстное меню для **функции** узел и выберите **добавить компонент**.

     Появится Feature1.feature.

4. Откройте контекстное меню для Feature1.feature, а затем выберите **добавить приемник событий** добавить модуль кода в компонент.

## <a name="BKMK_AddCode"></a> Добавление кода в приемник компонента

Добавьте код для двух методов в приемник компонента: `FeatureActivated` и `FeatureDeactivating`. Эти методы активируются каждый раз, когда компонент включается или отключается в SharePoint, соответственно.

1. В верхней части класса `Feature1EventReceiver` добавьте следующий код для объявления переменных, которые задают сайт и дочерний сайт SharePoint.

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

2. Замените метод `FeatureActivated` следующим кодом:

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

3. Замените метод `FeatureDeactivating` следующим кодом:

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

## <a name="BKMK_Test1"></a> Тестирование проекта

Теперь, когда код добавлен в приемник компонента и сборщик данных выполняется, разверните и запустите решение SharePoint для тестирования правильности работы.

> [!IMPORTANT]
> В этом примере возникает ошибка в обработчике событий FeatureDeactivating. Далее в этом пошаговом руководстве ошибка обнаруживается с помощью .iTrace-файла, созданного сборщиком данных.

1. Разверните решение в SharePoint, а затем откройте сайт SharePoint в браузере.

     Возможность автоматически активируется, что приводит к добавлению приемником возможности объявления и задачи.

2. Отображение содержимого списков извещений и задач.

     Списке извещений должно присутствовать новое извещение с именем **Activated feature: IntelliTraceTest_Feature1**, и в списке задач должна присутствовать новая задача, которая называется **Deactivate feature: IntelliTraceTest_ Feature1**. Если один из этих элементов отсутствует, проверьте, активирован ли компонент. Если он не активирован, активируйте его.

3. Отключите компонент, выполнив следующие действия.

    1. На **действия сайта** в SharePoint, в меню выберите **параметры сайта**.

    2. В разделе **действия сайта**, выберите **управление возможностями сайта** ссылку.

    3. Рядом с **IntelliTraceTest Feature1**, выберите **деактивировать** кнопки.

    4. На странице предупреждений выберите **деактивировать этот компонент** ссылку.

     Обработчик событий FeatureDeactivating() вызывает ошибку.

## <a name="BKMK_CollectDiagnosticData"></a> Сбор данных IntelliTrace с помощью Microsoft Monitoring Agent

Если установить Microsoft Monitoring Agent в системе, на котором выполняется SharePoint, можно отлаживать решения SharePoint с использованием данных, более точно, чем универсальный информации, которую возвращает IntelliTrace. Агент работает вне Visual Studio с помощью командлетов PowerShell для захвата отладочной информации в процессе выполнения решения SharePoint.

> [!NOTE]
> Сведения о конфигурации в этом разделе относятся к этому примеру. Дополнительные сведения о других параметрах конфигурации см. в разделе [использование автономного сборщика IntelliTrace](/visualstudio/debugger/using-the-intellitrace-stand-alone-collector).

1. На компьютере, на котором выполняется SharePoint [настройте Microsoft Monitoring Agent и начните отслеживание своего решения](/visualstudio/debugger/using-the-intellitrace-stand-alone-collector).

2. Отключение компонента.

    1. На **действия сайта** в SharePoint, в меню выберите **параметры сайта**.

    2. В разделе **действия сайта**, выберите **управление возможностями сайта** ссылку.

    3. Рядом с **IntelliTraceTest Feature1**, выберите **деактивировать** кнопки.

    4. На странице предупреждений выберите **деактивировать этот компонент** ссылку.

     Возникает ошибка (в данном случае из-за возникшей в обработчике событий FeatureDeactivating() ошибки).

3. В окне PowerShell, выполните [Stop-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313687) команду, чтобы создать ITRACE-файл, остановить наблюдение и перезапустите решения SharePoint.

     **STOP-WebApplicationMonitoring***»\<SharePointSite >\\< SharePointAppName\>»*

## <a name="BKMK_DebugSolution"></a> Отладка и исправление решения SharePoint

Теперь можно просмотреть файл журнала IntelliTrace в Visual Studio для поиска и исправления ошибки в решении SharePoint.

1. В папке \IntelliTraceLogs откройте .iTrace-файл в Visual Studio.

     **Сводка IntelliTrace** появится страница. Из-за ошибки не было обработано, идентификатор корреляции SharePoint (GUID) отображается в области необработанного исключения **Analysis** раздела. Выберите **стек вызовов** кнопку, чтобы просмотреть стек вызовов, где произошла ошибка.

2. Выберите **исключение отладки** кнопки.

     При появлении соответствующего запроса загрузите символьные файлы. В **IntelliTrace** окна, исключение выделяется как «вызванное: произошла серьезная ошибка!».

     В окне IntelliTrace выберите исключение для отображения кода, в котором произошла ошибка.

3. Исправить ошибку, открыв решение SharePoint и закомментирования или удаления **throw** в верхней части процедуры FeatureDeactivating().

4. Повторите сборку решения в Visual Studio, а затем заново разверните его в SharePoint.

5. Отключите компонент, выполнив следующие действия.

    1. На **действия сайта** в SharePoint, в меню выберите **параметры сайта**.

    2. В разделе **действия сайта**, выберите **управление возможностями сайта** ссылку.

    3. Рядом с **IntelliTraceTest Feature1**, выберите **деактивировать** кнопки.

    4. На странице предупреждений выберите **деактивировать этот компонент** ссылку.

6. Откройте список задач и убедитесь, что **состояние** задачи Deactivate равно «завершено» и его **% завершено** значение — 100%.

     Теперь код будет выполнен правильно.

## <a name="see-also"></a>См. также

[Проверка и отладка кода SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md)  
[IntelliTrace](/visualstudio/debugger/intellitrace)  
[Пошаговое руководство: Проверка кода SharePoint с помощью модульных тестов](https://msdn.microsoft.com/library/gg599006(v=vs.100).aspx)
