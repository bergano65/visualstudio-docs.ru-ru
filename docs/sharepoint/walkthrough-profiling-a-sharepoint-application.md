---
title: Пошаговое руководство. Профилирование приложения SharePoint | Документация Майкрософт
description: В этом пошаговом руководстве используются средства профилирования в Visual Studio для оптимизации производительности приложения SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 796c41ae50a33f00f72e0286d5e9680f9016cf58
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952568"
---
# <a name="walkthrough-profile-a-sharepoint-application"></a>Пошаговое руководство. Профилирование приложения SharePoint
  В этом пошаговом руководстве рассказывается, как использовать средства профилирования в Visual Studio, чтобы оптимизировать производительность приложений SharePoint. Примером приложения служит приемник событий компонентов SharePoint, который содержит цикл простоя, что ведет к снижению производительности приемника событий компонентов. Профилировщик Visual Studio позволяет нахождение и устранение наиболее дорогостоящей (самой медленной) части проекта, также известной как *горячий путь*.

 В этом пошаговом руководстве описаны следующие задачи.

- [Добавьте приемник событий компонента и](#add-a-feature-and-feature-event-receiver)компонента.

- [Настройка и развертывание приложения SharePoint](#configure-and-deploy-the-sharepoint-application).

- [Запустите приложение SharePoint](#run-the-sharepoint-application).

- [Просмотр и анализ результатов профиля](#view-and-interpret-the-profile-results).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства требуются следующие компоненты:

- Поддерживаемые редакции Microsoft Windows и SharePoint.

- [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].

## <a name="create-a-sharepoint-project"></a>Создание проекта SharePoint
 Сначала создайте проект SharePoint.

### <a name="to-create-a-sharepoint-project"></a>Создание проекта SharePoint

1. В строке меню выберите **файл**  >  **создать**  >  **проект** , чтобы открыть диалоговое окно **Новый проект** .

2. Разверните узел **SharePoint** под управлением **Visual C#** или **Visual Basic**, а затем выберите узел **2010** .

3. В области Шаблоны выберите шаблон **проекта SharePoint 2010** .

4. В поле **имя** введите **профилетест**, а затем нажмите кнопку **ОК** .

    Откроется **Мастер настройки SharePoint** .

5. На странице **Укажите сайт и уровень безопасности для отладки** введите URL-адрес сайта SharePoint Server, на котором нужно выполнить отладку определения сайта, или используйте расположение по умолчанию (http://<em>System Name</em>/).

6. В разделе **что такое уровень доверия для этого решения SharePoint?** выберите параметр **Развернуть как решение фермы** .

    В настоящее время можно профилировать только решения фермы. Дополнительные сведения о изолированных решениях и решениях фермы см. в статье [рекомендации по изолированным решениям](../sharepoint/sandboxed-solution-considerations.md).

7. Нажмите кнопку **Готово**. Проект отобразится в **Обозреватель решений**.

## <a name="add-a-feature-and-feature-event-receiver"></a>Добавление приемника событий компонента и компонента
 Затем добавьте в проект компонент вместе с приемником событий для этого компонента. Этот приемник событий будет содержать код для профилирования.

### <a name="to-add-a-feature-and-feature-event-receiver"></a>Добавление компонента и приемника событий компонента

1. В **Обозреватель решений** откройте контекстное меню узла **компоненты** , выберите пункт **Добавить компонент** и оставьте имя по умолчанию — **Feature1**.

2. В **Обозреватель решений** откройте контекстное меню для **Feature1** и выберите **Добавить приемник событий**.

     В результате в компонент будет добавлен и открыт для редактирования файл с кодом, содержащий несколько закомментированных обработчиков событий.

3. Добавьте следующие объявления переменных в класс приемника событий.

    ```vb
    ' SharePoint site/subsite.
    Private siteUrl As String = "http://localhost"
    Private webUrl As String = "/"
    ```

    ```csharp
    // SharePoint site/subsite.
    private string siteUrl = "http://localhost";
    private string webUrl = "/";
    ```

4. Замените процедуру `FeatureActivated` следующим кодом.

    ```vb
    Public Overrides Sub FeatureActivated(properties As SPFeatureReceiverProperties)
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim announcementsList As SPList = web.Lists("Announcements")

                    ' Add a new announcement to the Announcements list.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()
                    ' Waste some time.
                    TimeCounter()
                    ' Update the list.
                    listItem.Update()
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

                    // Add a new announcement to the Announcements list.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " +
    DateTime.Now.ToString();
                    // Waste some time.
                    TimeCounter();
                    // Update the list.
                    listItem.Update();
                }
            }
        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }
    }
    ```

5. Добавьте следующую процедуру после `FeatureActivated` процедуры.

    ```vb

    Public Sub TimeCounter()
        Dim result As Integer
        For i As Integer = 0 To 99999
            For j As Integer = 0 To 9999
                result = i * j
            Next j
        Next i
    End Sub
    ```

    ```csharp
    public void TimeCounter()
    {
        for (int i = 0; i < 100000; i++)
        {
            for (int j = 0; j < 10000; j++)
            {
                int result = i * j;
            }
        }
    }
    ```

6. В **Обозреватель решений** откройте контекстное меню проекта (**профилетест**) и выберите пункт **Свойства**.

7. В диалоговом окне **Свойства** перейдите на вкладку **SharePoint** .

8. В списке **Активная конфигурация развертывания** выберите **нет активации**.

     Выбор этой конфигурации развертывания позволяет в дальнейшем вручную активировать компонент в SharePoint.

9. Сохраните проект.

## <a name="configure-and-deploy-the-sharepoint-application"></a>Настройка и развертывание приложения SharePoint
 Теперь, когда проект SharePoint готов, настройте и разверните его на сервере SharePoint.

### <a name="to-configure-and-deploy-the-sharepoint-application"></a>Методика настройки и развертывания приложения SharePoint

1. В меню **анализ** выберите команду **запустить мастер производительности**.

2. На странице один из **мастеров производительности** оставьте метод профилирования как **выборка ЦП** и нажмите кнопку **Далее** .

     В более сложных случаях профилирования можно использовать другие методы профилирования. Дополнительные сведения см. в статье [Общие сведения о методах сбора данных по производительности](../profiling/understanding-performance-collection-methods.md).

3. На второй странице **мастера производительности** оставьте целевой профиль **профилетест** и нажмите кнопку **Далее** .

     Если решение содержит несколько проектов, они появятся в этом списке.

4. На третьей странице **мастера производительности** снимите флажок **включить профилирование уровневого взаимодействия** и нажмите кнопку **Далее** .

     Функция профилирования уровневого взаимодействия (TIP) полезна для измерения производительности приложений, которые обращаются к базам данных, и для отображения количества запросов какой-либо веб-страницы. Поскольку эти данные не требуются в данном примере, эта возможность не будет использоваться.

5. На четвертой странице **мастера производительности** оставьте **Профилирование запустить после завершения работы мастера** , а затем нажмите кнопку **Готово** .

     Мастер включает профилирование приложений на сервере, отображает окно **Обозреватель производительности** , а затем выполняет сборку, развертывание и запуск приложения SharePoint.

## <a name="run-the-sharepoint-application"></a>Запуск приложения SharePoint
 Активируйте компонент SharePoint, запустив код события `FeatureActivation`.

### <a name="to-run-the-sharepoint-application"></a>Запуск приложения SharePoint

1. В SharePoint откройте меню **действия сайта** и выберите пункт **Параметры сайта**.

2. В списке **действия сайта** выберите ссылку **Управление компонентами сайта** .

3. В списке **компоненты** нажмите кнопку **активировать** рядом с **профилетест Feature1**.

     При этом возникнет пауза из-за вызова цикла простоя в функции `FeatureActivated`.

4. На панели **быстрого запуска** выберите **списки** , а затем в списке **списки** выберите **извещения**.

     Обратите внимание, что новое извещение о том, что компонент был активирован, добавляется в список.

5. Закройте сайт SharePoint.

     После закрытия SharePoint профилировщик создает и отображает пример отчета профилирования и сохраняет его как VSP-файл в папке проекта **профилетест** .

## <a name="view-and-interpret-the-profile-results"></a>Просмотр и анализ результатов профиля
 Теперь, после запуска и профилирования приложения SharePoint, просмотрите результаты теста.

### <a name="to-view-and-interpret-the-profile-results"></a>Просмотр и анализ результатов профиля

1. В разделе **функции, выполняющие наиболее индивидуальную работу** в отчете профилирования выборки Обратите внимание, что `TimeCounter` находится ближе к началу списка.

     Это положение означает, что `TimeCounter` является одной из функций с наибольшим количеством выборок, а значит она — одно из самых узких мест производительности приложения. Это не удивительно, поскольку она была специально так разработана в демонстрационных целях.

2. В разделе **функции, выполняющие наиболее индивидуальную работу** выберите `ProcessRequest` ссылку, чтобы отобразить распределение затрат для `ProcessRequest` функции.

     Обратите внимание, что в разделе **вызываемые функции** для указано, `ProcessRequest` что функция **феатуреактивиатед** указана как самая ресурсоемкая вызванная функция.

3. В разделе **вызываемые функции** нажмите кнопку **FeatureActivated** .

     В разделе **вызываемые функции** для **FeatureActivated** `TimeCounter` функция указана как самая ресурсоемкая вызываемая функция. В области **представление кода функции** выделенный код ( `TimeCounter` ) является активной областью и указывает, где требуется исправление.

4. Закройте отчет о профилировании выборки.

     Чтобы снова просмотреть отчет в любое время, откройте VSP файл в окне **Обозреватель производительности** .

## <a name="fix-the-code-and-reprofile-the-application"></a>Исправление кода и перепрофилирование приложения
 Теперь, когда наиболее часто используемая функция в приложении SharePoint определена, исправьте ее.

### <a name="to-fix-the-code-and-reprofile-the-application"></a>Исправление кода и перепрофилирование приложения

1. В коде приемника событий компонента закомментируйте вызов метода `TimeCounter` в `FeatureActivated`, чтобы предотвратить его вызов.

2. Сохраните проект.

3. В **Обозреватель производительности** откройте папку targets, а затем выберите узел **профилетест** .

4. На панели инструментов **Обозреватель производительности** на вкладке **действия** нажмите кнопку **запустить профилирование** .

     Если вы хотите изменить какие бы то ни было свойства профилирования до того, как приложение репрофилинг, нажмите кнопку **Мастер производительности запуска** .

5. Следуйте инструкциям в разделе **Запуск приложения SharePoint** , ранее в этом разделе.

     Теперь, когда вызов цикла простоя устранен, компонент должен активироваться гораздо быстрее. Отчет о профилировании выборки должен отражать это.

## <a name="see-also"></a>См. также раздел
- [Обзор сеанса анализа производительности](../profiling/performance-session-overview.md)
- [Обзор профилирования производительности для начинающих](../profiling/beginners-guide-to-performance-profiling.md)
- [Поиск ограничений приложений с профилировщиком Visual Studio](/archive/msdn-magazine/2008/march/find-application-bottlenecks-with-visual-studio-profiler)