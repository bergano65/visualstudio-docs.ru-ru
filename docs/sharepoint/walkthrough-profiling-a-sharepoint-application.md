---
title: Пошаговое руководство. Профилирование приложения SharePoint | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bf6957b0757da709a7f95ccf58b1b192e0edf098
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56602043"
---
# <a name="walkthrough-profile-a-sharepoint-application"></a>Пошаговое руководство. Профилирование приложения SharePoint
  В этом пошаговом руководстве рассказывается, как использовать средства профилирования в Visual Studio, чтобы оптимизировать производительность приложений SharePoint. Примером приложения служит приемник событий компонентов SharePoint, который содержит цикл простоя, что ведет к снижению производительности приемника событий компонентов. Профилировщик Visual Studio позволяет найти и исключить самый дорогостоящий этап (самые медленные производительность) проекта, также известный как *критический путь*.

 В этом пошаговом руководстве описаны следующие задачи.

- [Добавление компонента и приемника событий компонента](#BKMK_AddFtrandFtrEvntReceiver).

- [Настройка и развертывание приложения SharePoint](#BKMK_ConfigSharePointApp).

- [Запуск приложения SharePoint](#BKMK_RunSPApp).

- [Просмотр и Интерпретация результатов профилирования](#BKMK_ViewResults).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Предварительные требования
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.

-   Поддерживаемые редакции Microsoft Windows и SharePoint.

-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].

## <a name="create-a-sharepoint-project"></a>Создание проекта SharePoint
 Сначала создайте проект SharePoint.

#### <a name="to-create-a-sharepoint-project"></a>Создание проекта SharePoint

1. В строке меню выберите **файл** > **New** > **проекта** для отображения **новый проект** диалоговое окно.

2. Разверните **SharePoint** расположенный в области **Visual C#** или **Visual Basic**, а затем выберите **2010** узла.

3. В области «Шаблоны» выберите **проект SharePoint 2010** шаблона.

4. В **имя** введите **ProfileTest**, а затем выберите **ОК** кнопки.

    **Мастер настройки SharePoint** отображается.

5. На **Укажите сайт и уровень безопасности для отладки** странице, введите URL-адрес сайта сервера SharePoint, где требуется отладка определения сайта или используйте расположение по умолчанию (http://<em>системное имя</em>/) .

6. В **Какова степень доверия для этого решения SharePoint?** выберите **развернуть как решение фермы** переключатель.

    В настоящее время можно профилировать только решения фермы. Дополнительные сведения об изолированных решениях и решений фермы см. в разделе [замечания об изолированных решениях](../sharepoint/sandboxed-solution-considerations.md).

7. Выберите **Готово** кнопки. Проект отображается в **обозревателе решений**.

## <a name="add-a-feature-and-feature-event-receiver"></a>Добавление компонента и приемника событий компонента
 Затем добавьте в проект компонент вместе с приемником событий для этого компонента. Этот приемник событий будет содержать код для профилирования.

#### <a name="to-add-a-feature-and-feature-event-receiver"></a>Добавление компонента и приемника событий компонента

1.  В **обозревателе решений**, откройте контекстное меню для **функции** узел, выберите **добавить компонент**и оставьте имя по умолчанию, **Feature1**.

2.  В **обозревателе решений**, откройте контекстное меню для **Feature1**, а затем выберите **добавить приемник событий**.

     В результате в компонент будет добавлен и открыт для редактирования файл с кодом, содержащий несколько закомментированных обработчиков событий.

3.  Добавьте следующие объявления переменных в класс приемника событий.

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

4.  Замените процедуру `FeatureActivated` следующим кодом.

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

5.  Добавьте следующую процедуру ниже `FeatureActivated`процедуры.

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

6.  В **обозревателе решений**, откройте контекстное меню для проекта (**ProfileTest**), а затем выберите **свойства**.

7.  В **свойства** диалоговом окне выберите **SharePoint** вкладки.

8.  В **активная конфигурация развертывания** выберите **без активации**.

     Выбор этой конфигурации развертывания позволяет в дальнейшем вручную активировать компонент в SharePoint.

9. Сохраните проект.

## <a name="configure-and-deploy-the-sharepoint-application"></a>Настройка и развертывание приложения для SharePoint
 Теперь, когда проект SharePoint готов, настройте и разверните его на сервере SharePoint.

#### <a name="to-configure-and-deploy-the-sharepoint-application"></a>Методика настройки и развертывания приложения SharePoint

1.  На **анализ** меню, выберите **запустить мастер производительности**.

2.  На первой странице **мастер производительности**, оставьте в качестве метода профилирования как **выборка циклов ЦП** и выберите **Далее** кнопки.

     В более сложных случаях профилирования можно использовать другие методы профилирования. Дополнительные сведения см. в статье [Общие сведения о методах сбора данных по производительности](/visualstudio/profiling/understanding-performance-collection-methods).

3.  На странице два **мастер производительности**, оставьте в качестве **ProfileTest** и выберите **Далее** кнопки.

     Если решение содержит несколько проектов, они появятся в этом списке.

4.  На третьей странице **мастер производительности**снимите **включить профилирование уровневого взаимодействия** , а затем нажать **Далее** кнопки.

     Возможность профилирования уровневого взаимодействия (TIP) полезна для измерения производительности приложений, которые обращаются к базам данных, и для отображения количества запросов какой-либо веб-страницы. Поскольку эти данные не требуются в данном примере, эта возможность не будет использоваться.

5.  На четвертой странице **мастер производительности**, оставьте **запустить профилирование после завершения работы мастера** установленным флажок, а затем выберите **Готово** кнопки.

     Мастер включает профилирование приложения на сервере, отображает **Обозреватель производительности** окна, а затем собирает, развертывает и запускает приложение SharePoint.

## <a name="run-the-sharepoint-application"></a>Запуск приложения SharePoint
 Активируйте компонент SharePoint, запустив код события `FeatureActivation`.

#### <a name="to-run-the-sharepoint-application"></a>Запуск приложения SharePoint

1.  В SharePoint, откройте **действия сайта** меню, а затем выберите **параметры сайта**.

2.  В **действия сайта** выберите **Управление компонентами сайта** ссылку.

3.  В **функции** выберите **активировать** рядом с пунктом **ProfileTest Feature1**.

     При этом возникнет пауза из-за вызова цикла простоя в функции `FeatureActivated`.

4.  На **быстрого запуска** панели **перечислены** и затем в **перечислены** выберите **объявления**.

     Обратите внимание, что новое извещение о том, что компонент был активирован, добавляется в список.

5.  Закройте сайт SharePoint.

     После закрытия SharePoint профилировщик создает и отображает отчет о профилировании выборки и сохраняет его как VSP-файл в **ProfileTest** папку проекта.

## <a name="view-and-interpret-the-profile-results"></a>Просмотр и Интерпретация результатов профиля
 Теперь, после запуска и профилирования приложения SharePoint, просмотрите результаты теста.

#### <a name="to-view-and-interpret-the-profile-results"></a>Для просмотра и интерпретации результатов профиля

1.  В **функции, выполняющие максимальную индивидуальную работу** раздел из отчета о профилировании выборки Обратите внимание, что `TimeCounter` находится в верхней части списка.

     Это положение означает, что `TimeCounter` является одной из функций с наибольшим количеством выборок, а значит она — одно из самых узких мест производительности приложения. Это не удивительно, поскольку она была специально так разработана в демонстрационных целях.

2.  В **функции, выполняющие максимальную индивидуальную работу** выберите `ProcessRequest` ссылку для отображения распределения стоимости для `ProcessRequest` функции.

     В **вызывающих функциях** раздел `ProcessRequest`, обратите внимание, что **FeatureActiviated** указана как наиболее затратная вызываемая функция.

3.  В **вызывающих функциях** выберите **FeatureActivated** кнопки.

     В **вызывающих функциях** раздел **FeatureActivated**, `TimeCounter` указана как наиболее затратная вызываемая функция. В **представление кода функции** области, выделенный код (`TimeCounter`) является активной области и указывает, где необходимы исправления.

4.  Закройте отчет о профилировании выборки.

     Чтобы просмотреть отчет в любое время, откройте VSP-файл в **Обозреватель производительности** окна.

## <a name="fix-the-code-and-reprofile-the-application"></a>Исправление кода и Перепрофилирование приложения
 Теперь, когда наиболее часто используемая функция в приложении SharePoint определена, исправьте ее.

#### <a name="to-fix-the-code-and-reprofile-the-application"></a>Исправление кода и перепрофилирование приложения

1.  В коде приемника событий компонента закомментируйте вызов метода `TimeCounter` в `FeatureActivated`, чтобы предотвратить его вызов.

2.  Сохраните проект.

3.  В **Обозреватель производительности**, откройте папку целевых объектов и выберите **ProfileTest** узла.

4.  На **Обозреватель производительности** панели инструментов в **действия** вкладке, выберите **запустить профилирование** кнопки.

     Если вы хотите изменить какие-либо свойства профилирования до перепрофилирования приложения, выберите **запустить мастер производительности** вместо кнопки.

5.  Следуйте инструкциям в **запуск приложения SharePoint** , ранее этой статьи.

     Теперь, когда вызов цикла простоя устранен, компонент должен активироваться гораздо быстрее. Отчет о профилировании выборки должен отражать это.

## <a name="see-also"></a>См. также
- [Обозреватель производительности](/visualstudio/profiling/performance-explorer)
- [Общие сведения о сеансе анализа производительности](/visualstudio/profiling/performance-session-overview)
- [Руководство по профилированию производительности для начинающих](/visualstudio/profiling/beginners-guide-to-performance-profiling)
- [Поиск ограничений приложений с Visual Studio Profiler](http://go.microsoft.com/fwlink/?LinkID=137266)
