---
title: Создание приложения Hello World с помощью WPF на C#
description: Создание простого приложения Windows Desktop .NET на языке C# в Visual Studio с помощью платформы пользовательского интерфейса Windows Presentation Foundation (WPF).
ms.custom: seodec18, get-started
ms.date: 08/09/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 8803bf6992608a496d560b68b71545d764803760
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68924400"
---
# <a name="tutorial-create-a-simple-application-with-c"></a>Учебник. Создание простого приложения на C\#

При изучении этого руководства вы ознакомитесь со многими инструментами, диалоговыми окнами и конструкторами, которые можно использовать для разработки приложений в Visual Studio. Вам предстоит создать простое приложение "Hello, World", разработать пользовательский интерфейс, добавить код и выполнить отладку, одновременно приобретая навыки работы в интегрированной среде разработки ([IDE](visual-studio-ide.md)).

::: moniker range="vs-2017"
Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download), если еще не сделали этого.
::: moniker-end
::: moniker range=">=vs-2019"
Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), если еще не сделали этого.
::: moniker-end

## <a name="configure-the-ide"></a>Настройка интегрированной среды разработки (IDE)

::: moniker range="vs-2017"

При первом открытии Visual Studio вам будет предложено выполнить вход. Для целей этого руководства это необязательно. Затем может появиться диалоговое окно, в котором предлагается выбрать параметры разработки и цветовую тему. Оставьте значения по умолчанию и нажмите **Запуск Visual Studio**.

![Диалоговое окно "Выбор параметров"](../media/exploreide-settings.png)

После запуска Visual Studio вы увидите окна инструментов, меню и панели инструментов, а также основную область окна. Окна инструментов закреплены в левой и правой частях окна приложения, а панель **Быстрый запуск**, строка меню и стандартная панель инструментов закреплены в верхней его части. В центре окна приложения находится **Начальная страница**. При загрузке решения или проекта редакторы и конструкторы отображаются в области **Начальной страницы** . При разработке приложения чаще всего используется именно эта область.

![Интегрированная среда разработки Visual Studio 2017, в которой установлены общие параметры](../media/exploreide-idewithgeneralsettings.png "Снимок экрана интегрированной среды разработки Visual Studio 2017, в которой установлены общие параметры")

::: moniker-end

::: moniker range=">=vs-2019"

При запуске Visual Studio сначала открывается начальное окно. Выберите **Продолжить без кода**, чтобы открыть среду разработки. Вы увидите окна инструментов, меню и панели инструментов, а также основную область окна. Окна инструментов закреплены в левой и правой частях окна приложения, а поле поиска, строка меню и стандартная панель инструментов закреплены в верхней его части. При загрузке решения или проекта редакторы и конструкторы отображаются в центральной области окна приложения. При разработке приложения чаще всего используется именно эта область.

::: moniker-end

## <a name="create-the-project"></a>Создание проекта

При создании приложения в Visual Studio необходимо сначала создать проект и решение. Этот пример демонстрирует создание проекта Windows Presentation Foundation (WPF).

::: moniker range="vs-2017"

1. Создайте новый проект. В строке меню выберите **Файл** > **Создать** > **Проект**.

     ![В строке меню выберите "Файл", "Создать", "Проект"](../media/exploreide-filenewproject.png "Снимок экрана строки меню, в которой нужно выбрать \"Файл\", \"Создать\", \"Проект\"")

1. В диалоговом окне **Новый проект** выберите категорию **Установленные** > **Visual C#**  > **Рабочий стол Windows**, а затем выберите шаблон **Приложения WPF (.NET Framework)** . Присвойте проекту имя **HelloWPFApp** и щелкните **ОК**.

     ![Шаблон приложения WPF в диалоговом окне создания проекта Visual Studio](media/exploreide-newprojectcsharp.png "Снимок экрана с шаблоном приложения WPF в диалоговом окне создания проекта")

::: moniker-end

::: moniker range="vs-2019"

1. Запустите Visual Studio 2019.

1. На начальном экране выберите **Создать проект**.

   ![Просмотр окна создания проекта](../../get-started/media/vs-2019/start-window-create-new-project.png "Снимок экрана с окном создания проекта")

1. На экране **Создание проекта** выполните поиск по строке "WPF", выберите в результатах **приложение WPF (.NET Framework)** и щелкните **Далее**.

   ![Шаблон приложения WPF в диалоговом окне создания проекта](media/vs-2019/exploreide-newprojectcsharp-vs2019.png "Снимок экрана с шаблоном приложения WPF в диалоговом окне создания проекта")

1. На следующем экране присвойте проекту имя **HelloWPFApp** и щелкните **Создать**.

   ![Присвоение проекту имени HelloWPFApp](./media/vs-2019/exploreide-nameproject.png "Снимок экрана с окном назначения имени проекту")

::: moniker-end

Visual Studio создает решение и проект HelloWPFApp, а в **обозревателе решений** выводятся различные файлы. **Конструктор WPF** отображает представление кода и представление XAML *MainWindow.xaml* в представлении с разделением. Сдвигая разделитель, можно делать любое из представлений больше или меньше. Можно выбрать для просмотра только визуальное представление или только представление XAML.

![Проект и решение WPF в интегрированной среде разработки](media/exploreide-wpfproject-cs.png "Снимок экрана с проектом и решением WPF в интегрированной среде разработки")

> [!NOTE]
> Дополнительные сведения о XAML (eXtensible Application Markup Language) см. в [обзоре XAML для WPF](/dotnet/framework/wpf/advanced/xaml-overview-wpf).

После создания проекта его можно настраивать. Для этого выберите **Окно свойств** в меню **Представление** или нажмите клавишу **F4**. Затем можно отображать и изменять параметры элементов проекта, элементов управления и других элементов в приложении.

   ![Окно свойств](../media/exploreide-hellowpfappfiles.png "Снимок экрана окна свойств с именами файлов приложения WPF")   

### <a name="change-the-name-of-mainwindowxaml"></a>Изменение имени MainWindow.xaml

Давайте присвоим файлу MainWindow более конкретное имя.

1. В **Обозревателе решений** выберите файл *MainWindow.xaml*. Должно появиться окно **Свойства**, но если его нет, выберите в меню **Вид** пункт **Окно свойств**. (Или нажмите клавишу **F4**.)

1. Измените значение свойства **Имя файла** на `Greetings.xaml`.

     ![Окно свойств с выделенным свойством "Имя файла"](../media/exploreide-filenameinpropertieswindow.png "Снимок экрана с окном свойств и выделенным свойством имени файла")

     В **обозревателе решений** видно, что файл теперь имеет имя *Greetings.xaml*, а имя вложенного файла кода поменялось на *Greetings.xaml.cs*. Этот файл с кодом программы вложен в узел файла *XAML*, что означает их тесную связь.

     ![Окно свойств и обозреватель решений с именем файла Greetings](../media/exploreide-greetingsfilename.png "Снимок экрана окна свойств и обозревателя решений с именем файла Greetings")     

## <a name="design-the-user-interface-ui"></a>Конструирование пользовательского интерфейса (ИП)

В приложение будут добавлены элементы управления трех типов: элемент управления <xref:System.Windows.Controls.TextBlock>, два элемента управления <xref:System.Windows.Controls.RadioButton> и элемент управления <xref:System.Windows.Controls.Button>.

### <a name="add-a-textblock-control"></a>Добавление элемента управления TextBlock

1. Нажмите **CTRL**+**Q** для активации поля поиска и введите **Панель элементов**. Выберите в списке результатов **Представление > Панель элементов**.

1. В окне **Панель элементов** разверните узел **Типовые элементы управления WPF**, чтобы увидеть элемент управления TextBlock.

     ![Панель элементов с выделенным элементом управления TextBlock](../media/exploreide-textblocktoolbox.png "Снимок экрана с окном панели элементов с выделенным элементом управления TextBlock")

1. Добавьте элемент управления TextBlock в область конструктора, выбрав элемент управления **TextBlock** и перетащив его в окно. Отцентрируйте этот элемент в верхней части окна.

    Окно должно выглядеть так, как показано на следующем рисунке:

    ![Элемент управления TextBlock в окне формы Greetings](../media/exploreide-greetingswithtextblockonly.png "Снимок экрана с элементом управления TextBlock в окне формы Greetings")

   Разметка XAML должна выглядеть приблизительно так, как в следующем примере:

    ```xaml
    <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
    </Grid>
    ```

### <a name="customize-the-text-in-the-text-block"></a>Настройка текста в текстовом блоке

1. В представлении XAML найдите разметку для **TextBlock** и измените атрибут **Text** с `TextBox` на `Select a message option and then choose the Display button.`.

   Разметка XAML должна выглядеть приблизительно так, как в следующем примере:

   ```xaml
   <Grid>
       <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
   </Grid>
   ```

1. При необходимости снова разместите элемент TextBlock по центру и сохраните изменения сочетанием клавиш **CTRL+S** или с помощью пункта меню **Файл**.

Следующий шаг — добавить в форму два элемента управления [RadioButton](/dotnet/framework/wpf/controls/radiobutton).

### <a name="add-radio-buttons"></a>Добавление переключателей

1. На **панели элементов** найдите элемент управления **RadioButton**.

     ![Окно панели элементов с выбранным элементом управления RadioButton](../media/exploreide-radiobuttontoolbox.png "Снимок экрана с окном панели элементов и выбранным элементом управления RadioButton")

1. Добавьте два элемента управления RadioButton в область конструктора, выбрав элемент **RadioButton** и перетащив его в область конструктора. Переместите кнопки (выбрав их и используя клавиши со стрелками), чтобы кнопки отображались рядом под элементом управления TextBlock.

   Окно должно выглядеть следующим образом:

   ![Форма Greetings с элементом TextBlock и двумя переключателями](../media/exploreide-greetingswithradiobuttons.png "Снимок экрана с формой Greetings, элементом TextBlock и двумя переключателями")

1. В окне **Свойства** для левого элемента управления RadioButton измените свойство **Имя** (свойство в верхней части окна **Свойства** ), задав ему значение `HelloButton`.

    ![Окно свойств RadioButton](../media/exploreide-buttonproperties.png "Снимок экрана с окном свойств RadioButton")

1. В окне **Свойства** правого элемента управления RadioButton измените свойство **Имя**, задав ему значение `GoodbyeButton`, и затем сохраните изменения.

Теперь вы добавите отображаемый текст для каждого элемента управления RadioButton. Следующая процедура обновляет свойство **Content** элемента управления RadioButton.

### <a name="add-display-text-for-each-radio-button"></a>Добавление отображаемого текста для каждого переключателя

1. В области конструктора откройте контекстное меню элемента управления HelloButton, щелкнув его правой кнопкой мыши, выберите команду **Изменить текст** и затем введите `Hello`.

1. Откройте контекстное меню элемента управления GoodbyeButton, щелкнув его правой кнопкой мыши, выберите команду **Изменить текст** и затем введите `Goodbye`.

   Разметка XAML теперь должна выглядеть следующим образом:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

### <a name="set-a-radio-button-to-be-checked-by-default"></a>Задание переключателя, выбранного по умолчанию

На этом этапе мы настроим элемент HelloButton как выбранный по умолчанию, чтобы всегда был выбран один из переключателей.

1. В представлении XAML найдите разметку для элемента HelloButton.

1. Добавьте атрибут **IsChecked** и задайте для него значение **True**. В частности, добавьте `IsChecked="True"`.

   Разметка XAML теперь должна выглядеть следующим образом:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" IsChecked="True" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

Последний элемент пользовательского интерфейса, который вам предстоит добавить, — это [Button](/dotnet/framework/wpf/controls/button).

### <a name="add-the-button-control"></a>Добавление элемента управления Button

1. На **панели элементов** найдите элемент управления **Button** и добавьте его в область конструктора под элементами управления RadioButton, перетащив его на форму в представлении конструирования.

1. В представлении XAML измените значение свойства **Содержимое** элемента управления Button с `Content="Button"` на `Content="Display"` и сохраните изменения.

     Окно должно выглядеть так, как показано на следующем рисунке.

     ![Форма Greetings с метками элементов управления](media/exploreide-greetingswithcontrollabels-cs.png "Снимок экрана формы Greetings с метками элементов управления")

   Разметка XAML теперь должна выглядеть следующим образом:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" IsChecked="True" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
        <Button Content="Display" HorizontalAlignment="Left" Margin="377,270,0,0" VerticalAlignment="Top" Width="75"/>
   </Grid>
   ```

### <a name="add-code-to-the-display-button"></a>Добавление кода к кнопке Display

После запуска приложения окно сообщения появится только тогда, когда пользователь выберет переключатель, а затем нажмет кнопку **Display**. Одно окно сообщения появится для Hello, и другое — для Goodbye. Чтобы задать такое поведение, добавьте код в событие `Button_Click` в файле *Greetings.xaml.cs*.

1. На поверхности разработки дважды щелкните кнопку **Display** .

     Откроется файл *Greetings.xaml.cs*, а курсор будет установлен на событии `Button_Click`.

    ```csharp
    private void Button_Click_1(object sender, RoutedEventArgs e)
    {

    }
    ```

1. Введите следующий код:

    ```csharp
    if (HelloButton.IsChecked == true)
    {
         MessageBox.Show("Hello.");
    }
    else if (GoodbyeButton.IsChecked == true)
    {
        MessageBox.Show("Goodbye.");
    }
    ```

1. Сохраните приложение.

## <a name="debug-and-test-the-application"></a>Отладка и тестирование приложения

После этого вам предстоит отладить приложение для выявления ошибок и тестирования того, что оба окна сообщений отображаются правильно. Приведенные ниже инструкции описывают, как выполнить сборку и запустить отладчик (дополнительные сведения см. в разделах [Построение приложения WPF](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) и [Отладка WPF](../../debugger/debugging-wpf.md)).

### <a name="find-and-fix-errors"></a>Поиск и исправление ошибок

В этом шаге вам предстоит найти ошибку, которую мы намеренно допустили ранее, изменив имя файла *MainWindow.xaml*.

#### <a name="start-debugging-and-find-the-error"></a>Начало отладки и поиск ошибки

1. Запустите отладчик, нажав клавишу **F5** или выбрав пункты меню **Отладка** и **Начать отладку**.

   Появится окно **Режим приостановки выполнения**, а в окне **Вывод** будет указано, что произошло исключение IOException: "Не удается найти ресурс mainwindow.xaml".

   ![Сообщение IOException](../media/exploreide-ioexception.png "Снимок экрана с сообщением IOException")

1. Остановите отладчик, выбрав в меню **Отладка** > **Остановить отладку**.

Мы переименовали *MainWindow.xaml* в *Greetings.xaml* в начале этого руководства, но код приложения по-прежнему ссылается на *MainWindow.xaml* как универсальный код ресурса (URI), поэтому проект не может быть запущен.

#### <a name="specify-greetingsxaml-as-the-startup-uri"></a>Задание Greetings.xaml в качестве начального универсального кода ресурса (URI)

1. В **обозревателе решений** откройте файл *App.xaml*.

1. Измените `StartupUri="MainWindow.xaml"` на `StartupUri="Greetings.xaml"` и сохраните изменения.

Запустите отладчик снова (клавишей **F5**). Должно появиться окно **Greetings** приложения. Теперь закройте окно приложения, чтобы остановить отладку.

### <a name="debug-with-breakpoints"></a>Отладка с точками останова

Добавив точки останова, можно тестировать код во время отладки. Точки останова можно добавлять, выбирая в меню **Отладка** > **Точка останова**, щелкая в левом поле редактора рядом со строкой кода, в которой требуется приостановить выполнение, или нажимая клавишу **F9**.

#### <a name="add-breakpoints"></a>Добавление точек останова

1. Откройте файл *Greetings.xaml.cs* и выделите строку `MessageBox.Show("Hello.")`.

1. Добавьте точку останова, выбрав меню **Отладка**, затем — **Точка останова**.

     Рядом со строкой кода в крайнем левом поле окна редактора появится красный кружок.

1. Выделите следующую строку: `MessageBox.Show("Goodbye.")`.

1. Нажмите клавишу **F9**, чтобы добавить точку останова, а затем нажмите клавишу **F5**, чтобы начать отладку.

1. В окне **Greetings** выберите переключатель **Hello** и нажмите кнопку **Display** .

    Строка `MessageBox.Show("Hello.")` выделяется желтым цветом. В нижней части интегрированной среды разработки слева закреплены окна "Видимые", "Локальные" и "Контрольные значения", а справа — окна "Стек вызовов", "Точки останова", "Параметры исключений", "Команда", "Интерпретация" и "Вывод".

    ![Точка останова в отладчике](media/exploreide-debugbreakpoint.png "Снимок экрана с точкой останова в отладчике")

1. В строке меню выберите **Отладка** > **Шаг с выходом**.

     Приложение возобновит выполнение, и появится окно сообщения со словом "Hello".

1. Нажмите кнопку **ОК** в окне сообщения, чтобы закрыть его.

1. В окне **Greetings** выберите переключатель **Goodbye** и нажмите кнопку **Display** .

     Строка `MessageBox.Show("Goodbye.")` выделяется желтым цветом.

1. Нажмите клавишу **F5**, чтобы продолжить отладку. Когда появится окно сообщения, нажмите в нем кнопку **ОК** , чтобы закрыть его.

1. Закройте окно приложения, чтобы остановить отладку.

1. В строке меню выберите **Отладка** > **Выключить все точки останова**.

### <a name="build-a-release-version-of-the-application"></a>Сборка окончательной версии приложения

Теперь, когда вы проверили, что все работает, можно подготовить окончательную сборку приложения.

1. Выберите в главном меню **Сборка** > **Очистить решение** для удаления промежуточных файлов и выходных файлов, которые были созданы в ходе предыдущих сборок. Это действие не является обязательным, но оно позволяет очистить результаты отладочной сборки.

1. Измените конфигурацию сборки для HelloWPFApp с **Отладка** на **Выпуск** с помощью раскрывающегося списка на панели инструментов (сейчас это "Отладка").

1. Выполните сборку решения, выбрав **Сборка** > **Собрать решение**.

Поздравляем с завершением этого учебника! Построенный файл *.exe* находится в каталоге решения и проекта ( *...\HelloWPFApp\HelloWPFApp\bin\Release*).

## <a name="next-steps"></a>Следующие шаги

Поздравляем с завершением этого учебника! Для получения дополнительных сведений перейдите к следующим руководствам.

> [!div class="nextstepaction"]
> [Другие руководства по WPF](/dotnet/framework/wpf/getting-started/wpf-walkthroughs/)

## <a name="see-also"></a>См. также

- [Советы по повышению производительности](../../ide/productivity-features.md)
