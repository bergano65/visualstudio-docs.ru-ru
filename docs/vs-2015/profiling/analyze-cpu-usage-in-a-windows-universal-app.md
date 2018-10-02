---
title: Анализ загрузки ЦП в универсальных приложениях для Windows | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c122b08e-e3bf-43e6-bd6c-e776e178fd9a
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: f57fdf99c6ccb19c6d8add600943d799d3a28ca4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558118"
---
# <a name="analyze-cpu-usage-in-a-windows-universal-app"></a>Анализ загрузки ЦП в универсальных приложениях для Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [анализ использования ЦП в универсальных приложениях Windows](https://docs.microsoft.com/visualstudio/profiling/analyze-cpu-usage-in-a-windows-universal-app).  
  
Применяется к Windows и Windows Phone] (.. /Image/windows_and_phone_content.PNG «windows_and_phone_content»)  
  
 Если вам нужно проанализировать проблемы с производительностью в своем приложении, следует сначала понять, как оно использует ЦП. Средство **Загрузка ЦП** показывает, в какой части кода затрачивается больше всего ресурсов ЦП. Чтобы сконцентрироваться на определенных сценариях использования ЦП можно запускать с [скорость реагирования ИП XAML](http://msdn.microsoft.com/library/4ff84cd1-4e63-4fda-b34f-3ef862a6e480) средство, [расход энергии](../profiling/analyze-energy-use-in-store-apps.md) средства или оба средства в рамках одного сеанса диагностики.  
  
> [!NOTE]
>  Инструмент **Загрузка ЦП** нельзя использовать с приложениями Silverlight 8.1 Windows Phone.  
  
 В этом пошаговом руководстве рассматривается сбор и анализ данных о загрузке ЦП для простого универсального XAML-приложения для Windows.  
  
##  <a name="BKMK_Create_the_CpuUseDemo_project"></a> Создание проекта CpuUseDemo  
 **CpuUseDemo** — это приложение, созданное для демонстрации сбора и анализа данных о загрузке ЦП. Кнопки выдают число, вызывая метод, который выбирает максимальное значение из нескольких вызовов функции. Вызванная функция создает очень большое количество случайных значений, а затем возвращает последнее из них. Эти данные отображаются в текстовом поле.  
  
1.  Создайте новый проект универсального приложения для Windows на C# с именем **CpuUseDemo**, используя шаблон **BlankApp**.  
  
     ![Создание CpuUseDemoProject](../profiling/media/cpu-use-newproject.png "CPU_USE_NewProject")  
  
2.  Замените MainPage.xaml [этим кодом](#BKMK_MainPage_xaml).  
  
3.  Замените MainPage.xaml.cs [этим кодом](#BKMK_MainPage_xaml_cs).  
  
4.  Выполните сборку приложения и попробуйте поработать с ним. Это приложение является достаточно простым, чтобы продемонстрировать наиболее распространенные примеры анализа данных о загрузке ЦП.  
  
##  <a name="BKMK_Collect_CPU_usage_data"></a> Сбор данных о загрузке ЦП  
 ![Запуск сборки выпуска приложения в симуляторе](../profiling/media/cpu-use-wt-setsimulatorandretail.png "CPU_USE_WT_SetSimulatorAndRetail")  
  
1.  В Visual Studio задайте **Симулятор** в качестве цели развертывания и **Выпуск** в качестве конфигурации решения.  
  
    -   Выполнение приложения в симуляторе позволяет вам легко переключаться между приложением и интерфейсом IDE Visual Studio.  
  
    -   Выполнение этого приложения в режиме **Выпуск** позволяет получить более полное представление о фактической производительности приложения.  
  
2.  В меню **Отладка** выберите пункт **Профилировщик производительности...**  
  
3.  В разделе "Производительность и диагностика" выберите **Загрузка ЦП**, а затем **Запуск**.  
  
     ![Запуск сеанса диагностики CpuUsage](../profiling/media/cpu-use-wt-perfdiaghub.png "CPU_USE_WT_PerfDiagHub")  
  
4.  После запуска приложения нажмите кнопку **Get Max Number**(Получить максимальное количество). После вывода результата подождите примерно одну секунду, а затем нажмите **Get Max Number Async**(Получить максимальное количество асинхронно). Перерыв между нажатиями кнопок облегчает нахождение в диагностическом отчете информации о подпрограммах обработки нажатия кнопок.  
  
5.  После вывода второй строки выберите **Остановка сбора** в разделе "Производительность и диагностика".  
  
 ![Остановка сбора данных CpuUsage](../profiling/media/cpu-use-wt-stopcollection.png "CPU_USE_WT_StopCollection")  
  
 Инструмент "Использование ЦП" анализирует данные и отображает отчет.  
  
 ![Отчет CpuUsage](../profiling/media/cpu-use-wt-report.png "CPU_USE_WT_Report")  
  
##  <a name="BKMK_Analyze_the_CPU_Usage_report"></a> Анализ отчета о загрузке ЦП  
  
###  <a name="BKMK_CPU_utilization_timeline_graph"></a> График зависимости загрузки ЦП от времени  
 ![График временной шкалы CpuUtilization (%)](../profiling/media/cpu-use-wt-timelinegraph.png "CPU_USE_WT_TimelineGraph")  
  
 На графике использования ЦП отображается активность ЦП для приложения в виде процента от совокупного времени ЦП, объединяющего все ядра процессора на устройстве. Данные для этого отчета были собраны на компьютере с двумя ядрами. Два больших всплеска активности ЦП соответствуют двум нажатиям кнопок. `GetMaxNumberButton_Click` выполняется синхронно на одном ядре, поэтому высота графика при таком методе никогда не превышает 50 %. `GetMaxNumberAsycButton_Click` выполняется асинхронно на обоих ядрах, поэтому график показывает, что использование ЦП близко к общему объему ресурсов обоих ядер.  
  
####  <a name="BKMK_Select_timeline_segments_to_view_details"></a> Выбор сегментов временной шкалы для просмотра подробных сведений  
 Используйте полосы выделения на временной шкале **Диагностический сеанс**, чтобы сконцентрироваться на данных GetMaxNumberButton_Click:  
  
 ![Выбранный отчет GetMaxNumberButton_Click](../profiling/media/cpu-use-wt-getmaxnumberreport.png "CPU_USE_WT_GetMaxNumberReport")  
  
 Временная шкала **Диагностический сеанс** теперь отображает выбранный сегмент (в данном отчете он немного превышает 2 секунды) и отфильтровывает дерево вызовов, отображая только те методы, которые выполнялись в рамках выбранного периода.  
  
 Теперь выберите период `GetMaxNumberAsyncButton_Click`.  
  
 ![Выбор отчета GetMaxNumberAsyncButton_Click](../profiling/media/cpu-use-wt-getmaxnumberasync-selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 Этот метод выполняется примерно на одну секунду быстрее, чем `GetMaxNumberButton_Click`, однако значение записей в дереве вызовов не слишком очевидно.  
  
###  <a name="BKMK_The_CPU_Usage_call_tree"></a> Дерево вызовов средства "Загрузка ЦП"  
 Чтобы понять сведения в дереве вызовов, повторно выберите сегмент `GetMaxNumberButton_Click` и просмотрите дерево вызовов.  
  
####  <a name="BKMK_Call_tree_structure"></a> Структура дерева вызовов  
 ![Дерево вызовов GetMaxNumberButton_Click](../profiling/media/cpu-use-wt-getmaxnumbercalltree-annotated.png "CPU_USE_WT_GetMaxNumberCallTree_annotated")  
  
|||  
|-|-|  
|![Шаг 1](../profiling/media/procguid-1.png "ProcGuid_1")|Узел верхнего уровня в деревьях вызовов для использования ЦП представляет собой псевдоузел|  
|![Шаг 2](../profiling/media/procguid-2.png "ProcGuid_2")|В большинстве приложений при отключенном параметре **Показать внешний код** узлом второго уровня является узел **[Внешний код]** , который содержит код системы и инфраструктуры, запускающий и останавливающий приложение, отрисовывающий пользовательский интерфейс, управляющий планированием потоков и предоставляющий приложению другие низкоуровневые службы.|  
|![Шаг 3](../profiling/media/procguid-3.png "ProcGuid_3")|Дочерними элементами узла второго уровня являются методы пользовательского кода и асинхронные подпрограммы, которые вызываются или создаются кодом системы и инфраструктуры на втором уровне.|  
|![Шаг 4](../profiling/media/procguid-4.png "ProcGuid_4")|Дочерние узлы метода содержат данные только для вызова родительского метода. Если параметр **Показать внешний код** отключен, методы приложения также могут содержать узел **[Внешний код]** .|  
  
####  <a name="BKMK_External_Code"></a> Внешний код  
 Внешний код состоит из функций в компонентах системы и платформы, которые исполняются вашим кодом. Внешний код включает функции, которые запускают и останавливают приложение, отрисовывают пользовательский интерфейс, управляют потоками и предоставляют приложению другие низкоуровневые службы. В большинстве случаев внешний код вас интересовать не будет, поэтому дерево вызовов средства "Использование ЦП" собирает внешние функции пользовательского метода в один узел **[Внешний код]** .  
  
 Если вы захотите посмотреть пути к вызовам внешнего кода, выберите **Показать внешний код** в списке **Представление фильтра** и выберите **Применить**.  
  
 ![Выбор "Представление фильтра", а затем "Показать внешний код"](../profiling/media/cpu-use-wt-filterview.png "CPU_USE_WT_FilterView")  
  
 Помните о том, что многие цепочки вызовов имеют глубокий уровень вложенности, поэтому ширина столбца "Имя функции" может превышать ширину многих мониторов. В этом случае имена функций отображаются в виде **[…]**:  
  
 ![Вложенный внешний код в дереве вызовов](../profiling/media/cpu-use-wt-showexternalcodetoowide.png "CPU_USE_WT_ShowExternalCodeTooWide")  
  
 Используйте поле поиска, чтобы найти требуемый узел, а затем воспользуйтесь горизонтальной полосой прокрутки для отображения данных в представлении:  
  
 ![Поиск вложенного внешнего кода](../profiling/media/cpu-use-wt-showexternalcodetoowide-found.png "CPU_USE_WT_ShowExternalCodeTooWide_Found")  
  
###  <a name="BKMK_Call_tree_data_columns"></a> Столбцы данных дерева вызовов  
  
|||  
|-|-|  
|**Общая активность ЦП (%)**|![Уравнение для данных процента общей активности](../profiling/media/cpu-use-wt-totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> Процент активности ЦП приложения за выбранный период времени, потраченной на вызовы функции и функций, которые вызывала данная функция. Обратите внимание, что это отличается от графика временной шкалы **Использование ЦП** , который сравнивает общую активность приложения за период времени с общей доступной емкостью ЦП.|  
|**Собственная активность ЦП (%)**|![Уравнение для процента собственной активности](../profiling/media/cpu-use-wt-selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> Процент активности ЦП приложения за выбранный период времени, потраченной на вызовы функции, исключая выполнение функций, которые вызывала данная функция.|  
|**Общее время ЦП (мс)**|Время в миллисекундах, затраченное на вызовы функции в выбранном временном интервале, и функций, которые были вызваны этой функцией.|  
|**Собственное время ЦП (мс)**|Время в миллисекундах, затраченное на вызовы функции в выбранном временном интервале, и функций, которые были вызваны этой функцией.|  
|**Модуль**|Имя модуля, содержащего функцию, или количество модулей, содержащих функции в узле [Внешний код].|  
  
###  <a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a> Асинхронные функции в дереве вызовов средства "Использование ЦП"  
 Если компилятор обнаруживает асинхронный метод, он создает скрытый класс для контроля выполнения этого метода. По существу, класс представляет собой конечный автомат, содержащий список функций, созданных компилятором, которые асинхронно вызывают операции исходного метода. Также класс включает обратные вызовы, планировщик и итераторы, необходимые для его правильной работы. При вызове исходного метода родительским методом среда выполнения удаляет метод из контекста выполнения родительского метода и выполняет методы скрытого класса в контексте кода системы и инфраструктуры, который управляет выполнением приложения. Асинхронные методы часто, но не всегда выполняются в отдельном потоке (или в нескольких потоках). Этот код отображается в дереве вызовов средства "Использование ЦП" в виде дочерних элементов узла **[Внешний код]** сразу под верхним узлом дерева.  
  
 Чтобы увидеть его в нашем примере, снова выберите период `GetMaxNumberAsyncButton_Click` на временной шкале.  
  
 ![Выбор отчета GetMaxNumberAsyncButton_Click](../profiling/media/cpu-use-wt-getmaxnumberasync-selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 Два первых узла в узле **[Внешний код]** представляют собой созданные компилятором методы класса конечного автомата. Третий узел является вызовом исходного метода. Развернув созданные методы, можно понять, как это работает.  
  
 ![Развернутое дерево вызовов GetMaxNumberAsyncButton_Click](../profiling/media/cpu-use-wt-getmaxnumberasync-expandedcalltree.png "CPU_USE_WT_GetMaxNumberAsync_ExpandedCallTree")  
  
-   `MainPage::GetMaxNumberAsyncButton_Click` выполняет немного функций: управляет списком значений задач, вычисляет максимальное значение на основе результатов и отображает выходные данные.  
  
-   `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` показывает время ЦП, затраченное на планирование и запуск 48 задач, которые являются оболочкой вызова `GetNumberAsync`.  
  
-   `MainPage::<GetNumberAsync>b__b` показывает время ЦП, затраченное на выполнение задач, которые вызывают `GetNumber`.  
  
##  <a name="BKMK_Next_steps"></a> Дальнейшие действия  
 Приложение ДемонстрацияИспользованияЦП нельзя назвать шедевром, но вы можете расширить его возможности, экспериментируя с асинхронными операциями и другими инструментами в разделе "Производительность и диагностика".  
  
-   Обратите внимание на то, что `MainPage::<GetNumberAsync>b__b` проводит больше времени в узле [Внешний код], чем затрачивает на выполнение метода GetNumber. Основная часть этого времени является затратами на выполнение асинхронных операций. Попробуйте увеличить число задач (с помощью константы `NUM_TASKS` в MainPage.xaml.cs) и уменьшить число итераций в `GetNumber` (измените значение `MIN_ITERATIONS`). Запустите сценарий сбора и сравните активность ЦП `MainPage::<GetNumberAsync>b__b` с показаниями исходного диагностического сеанса инструмента "Использование ЦП". Попробуйте сократить число задач и увеличить количество итераций.  
  
-   Часто пользователи вообще не заботятся о фактической производительности своего приложения — их больше волнует производительность и скорость реагирования, воспринимаемая пользователями. Инструмент "Скорость реагирования ИП XAML" отображает сведения об активности потока пользовательского интерфейса, влияющей на воспринимаемую скорость реагирования.  
  
     Создайте новый сеанс в разделе "Производительность и диагностика" и добавьте как инструмент "Скорость реагирования ИП XAML", так и инструмент "Использование ЦП". Запустите сценарий сбора. Если вы дочитали до этого места, скорее всего, вы не нашли в отчете ничего нового, однако графики **Использование потока пользовательского интерфейса** для двух методов имеют весьма характерные различия. В сложных приложениях, используемых в реальных условиях, такое сочетание инструментов может оказаться очень полезным.  
  
##  <a name="BKMK_MainPage_xaml"></a> MainPage.xaml  
  
```csharp  
<Page  
    x:Class="CpuUseDemo.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:local="using:CpuUseDemo"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    mc:Ignorable="d">  
  
    <Page.Resources>  
        <Style TargetType="TextBox">  
            <Setter Property="FontFamily"  Value="Lucida Console" />  
        </Style>  
    </Page.Resources>  
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
        <Grid.RowDefinitions>  
            <RowDefinition Height="Auto" />  
            <RowDefinition Height="*" />  
        </Grid.RowDefinitions>  
        <StackPanel Grid.Row="0" Orientation="Horizontal"  Margin="0,40,0,0">  
            <Button Name="GetMaxNumberButton" Click="GetMaxNumberButton_Click"  Content="Get Max Number" />  
            <Button Name="GetMaxNumberAsyncButton" Click="GetMaxNumberAsyncButton_Click"  Content="Get Max Number Async" />  
        </StackPanel>  
        <StackPanel Grid.Row="1">  
            <TextBox Name="TextBox1" AcceptsReturn="True" />  
        </StackPanel>  
    </Grid>  
  
</Page>  
  
```  
  
##  <a name="BKMK_MainPage_xaml_cs"></a> MainPage.xaml.cs  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.IO;  
using System.Linq;  
using System.Runtime.InteropServices.WindowsRuntime;  
using Windows.Foundation;  
using Windows.Foundation.Collections;  
using Windows.UI.Xaml;  
using Windows.UI.Xaml.Controls;  
using Windows.UI.Xaml.Controls.Primitives;  
using Windows.UI.Xaml.Data;  
using Windows.UI.Xaml.Input;  
using Windows.UI.Xaml.Media;  
using Windows.UI.Xaml.Navigation;  
using Windows.Foundation.Diagnostics;  
using System.Threading;  
using System.Threading.Tasks;  
using System.Collections.Concurrent;  
  
// The Blank Page item template is documented at http://go.microsoft.com/fwlink/?LinkId=234238  
  
namespace CpuUseDemo  
{  
    /// <summary>  
    /// An empty page that can be used on its own or navigated to within a Frame.  
    /// </summary>  
    public sealed partial class MainPage : Page  
    {  
        public MainPage()  
        {  
            this.InitializeComponent();  
        }  
  
        const int NUM_TASKS = 48;  
        const int MIN_ITERATIONS = int.MaxValue / 1000;  
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;  
  
        long m_totalIterations = 0;  
        readonly object m_totalItersLock = new object();  
  
        private void GetMaxNumberButton_Click(object sender, RoutedEventArgs e)  
        {  
            GetMaxNumberAsyncButton.IsEnabled = false;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations = 0;  
            }  
            List<int> tasks = new List<int>();  
            for (var i = 0; i < NUM_TASKS; i++)  
            {  
                var result = 0;  
                result = GetNumber();  
                tasks.Add(result);  
            }  
            var max = tasks.Max();  
            var s = GetOutputString("GetMaxNumberButton_Click", NUM_TASKS, max, m_totalIterations);  
            TextBox1.Text += s;  
            GetMaxNumberAsyncButton.IsEnabled = true;  
        }  
  
        private async void GetMaxNumberAsyncButton_Click(object sender, RoutedEventArgs e)  
        {  
            GetMaxNumberButton.IsEnabled = false;  
            GetMaxNumberAsyncButton.IsEnabled = false;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations = 0;  
            }  
            var tasks = new ConcurrentBag<Task<int>>();  
            for (var i = 0; i < NUM_TASKS; i++)  
            {  
                tasks.Add(GetNumberAsync());  
            }  
            await Task.WhenAll(tasks.ToArray());  
            var max = 0;  
            foreach (var task in tasks)  
            {  
                max = Math.Max(max, task.Result);  
            }  
            var func = "GetMaxNumberAsyncButton_Click";  
            var outputText = GetOutputString(func, NUM_TASKS, max, m_totalIterations);  
            TextBox1.Text += outputText;  
            this.GetMaxNumberButton.IsEnabled = true;  
            GetMaxNumberAsyncButton.IsEnabled = true;  
        }  
  
        private int GetNumber()  
        {  
            var rand = new Random();  
            var iters = rand.Next(MIN_ITERATIONS, MAX_ITERATIONS);  
            var result = 0;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations += iters;  
            }  
            // we're just spinning here  
            // and using Random to frustrate compiler optimizations  
            for (var i = 0; i < iters; i++)  
            {  
                result = rand.Next();  
            }  
            return result;  
        }  
  
        private Task<int> GetNumberAsync()  
        {  
            return Task<int>.Run(() =>  
            {  
                return GetNumber();  
            });  
        }  
  
        string GetOutputString(string func, int cycles, int max, long totalIters)  
        {  
            var fmt = "{0,-35}Tasks:{1,3}    Maximum:{2, 12}    Iterations:{3,12}\n";  
            return String.Format(fmt, func, cycles, max, totalIters);  
        }  
  
    }  
}  
  
```



