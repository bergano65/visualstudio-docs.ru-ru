---
title: Основы создания приложений с помощью Xamarin.Forms в Visual Studio | Документы Майкрософт
ms.custom: ''
ms.date: 03/30/2018
ms.topic: conceptual
ms.assetid: d22b5186-9e03-4e85-afc9-7cbe28522a6d
ms.prod: visual-studio-dev15
ms.technology: vs-ide-mobile
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: f9f233b5f43555f86f0a49c5e5853cad6d7456b1
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2018
ms.locfileid: "37924428"
---
# <a name="learn-app-building-basics-with-xamarinforms-in-visual-studio"></a>Основы создания приложений с помощью Xamarin.Forms в Visual Studio

После того как мы выполнили [Настройку и установку](../cross-platform/setup-and-install.md) и [Проверку окружения Xamarin](../cross-platform/verify-your-xamarin-environment.md), в этом пошаговом руководстве мы расскажем, как создать базовое приложение с помощью Xamarin.Forms. Используя Xamarin.Forms, вы запишете весь код пользовательского интерфейса в один файл библиотеки классов .NET Standard. Xamarin будет автоматически отображать поддерживаемые элементы управления для пользовательского интерфейса на платформах iOS, Android и Windows.

Обычно для общего кода лучше использовать библиотеку .NET Standard, а не общий проект. Библиотека .NET Standard включает те функции .NET API, которые могут выполняться на всех целевых платформах.

Так выглядит приложение, которые мы будем создавать. Она выполняется (слева направо) на телефонах с iOS и Android и на универсальной платформе Windows (UWP) в ОС Windows 10:

[![Образец приложения прогнозов погоды для iOS, Android и UWP](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")](../cross-platform/media/crossplat-xamarin-formsguide-1-Large.png#lightbox)

Для создания этого приложения вам предстоит выполнить следующие действия:

-   [Настройка решения](#solution)

-   [Создание общего кода для службы данных](#dataservice)

-   [Начало создания общего кода пользовательского интерфейса](#uicode)

-   [Проверьте приложение, используя эмулятор Visual Studio для Android](#test)

-   [Завершение пользовательского интерфейса с помощью собственного интерфейса на разных платформах](#finish)

> [!TIP]
> Полный исходный код для этого проекта можно найти в [репозитории образцов xamarin-forms на GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).

<a name="solution" />

## <a name="set-up-your-solution"></a>Настройка решения

Эти шаги создают решение Xamarin.Forms, которое содержит библиотеку классов .NET Standard и два дополнительных пакета NuGet.

1. В Visual Studio создайте новое **кроссплатформенное приложение (Xamarin.Forms Portable)** и назовите его **WeatherApp**. Чтобы найти шаблон, в списке слева выберите **Visual C#** и **Кроссплатформенные**.

    ![Создание нового проекта кроссплатформенного приложения Xamarin.Forms](../cross-platform/media/crossplat-xamarin-formsguide-2.png "CrossPlat Xamarin FormsGuide 2")

    Если шаблон отсутствует, может потребоваться установить Xamarin или включить компонент Visual Studio 2017. См. раздел [Настройка и установка](../cross-platform/setup-and-install.md).

2.  Нажав кнопку "ОК", вы сможете настроить некоторые параметры. Выберите **Пустое приложение** и **.NET Standard**:

    ![Создание нового проекта кроссплатформенного приложения](../cross-platform/media/crossplat-xamarin-formsguide-3.png "CrossPlat Xamarin FormsGuide 3")

3.  Нажав кнопку "ОК" для создания решения, вы получите одно решение с четырьмя проектами:

    -   **WeatherApp**. Это библиотека .NET Standard, в которую вы поместите основанный на Xamarin.Forms код базовой бизнес-логики и пользовательского интерфейса для использования на нескольких платформах.

    -   **WeatherApp.Droid**. Это проект, который содержит машинный код для Android.

    -   **WeatherApp.iOS**: проект, который содержит машинный код для iOS.

    -   **WeatherApp.UWP**: проект, который содержит код Windows 10 UWP.

    > [!NOTE]
    >  Вы можете удалить любой проект, нацеленный не на нужную вам платформу.

     В каждом проекте с машинным кодом вы получите доступ к собственному конструктору для соответствующей платформы и можете при необходимости реализовать экраны и функции для конкретной платформы.

4.  Обновите пакет NuGet Xamarin.Forms в решении до последней стабильной версии следующим образом:

    -   Выберите пункты меню **"Сервис" > "Диспетчер пакетов NuGet" > "Управление пакетами NuGet для решения"**.

    -   На вкладке **Обновления** выберите пакет **Xamarin.Forms** и установите флажки для обновления всех проектов в решении. (Не выбирайте обновления библиотек поддержки Android для Xamarin.)

    -   Укажите в поле **Версия** **последнюю стабильную** версию.

    -   Нажмите кнопку **Установить**.

         ![Обновление пакета NuGet Xamarin.Forms](../cross-platform/media/crossplat-xamarin-formsguide-4.png "CrossPlat Xamarin FormsGuide 4")

    У вас должно войти в привычку обновлять версию Xamarin.Forms каждый раз при создании нового решения Xamarin.Forms. Не обновляйте никакие библиотеки поддержки Android. При необходимости эти библиотеки будут обновлены при обновлении Xamarin.Forms.

5.  Добавьте пакет NuGet **Newtonsoft.Json** в проект **WeatherApp**. Эта библиотека используется для обработки информации, полученной от метеослужбы:

    -   В диспетчере пакетов NuGet (который вы открыли на шаге 4) выберите вкладку **Обзор** и найдите **Newtonsoft**.

    -   Выберите **Newtonsoft.Json**.

    -   Установите флажок напротив проекта **WeatherApp**, это единственный проект, для которого требуется установить пакет.

    -   Убедитесь, что в поле **Версия** указана **последняя стабильная** версия.

    -   Нажмите кнопку **Установить**.

    ![Поиск и установка пакета NuGet Newtonsoft.Json](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin FormsGuide 5")

6.  Повторите шаг 5, чтобы найти и установить пакет **Microsoft.CSharp** в проекте .NET Standard. Эта библиотека необходима для использования типа данных C# `dynamic` в библиотеке .NET Standard.

7.  Соберите свое решение и убедитесь в отсутствии ошибок сборки.

<a name="dataservice" />

## <a name="write-shared-data-service-code"></a>Создание общего кода для службы данных

Именно в проекте библиотеки .NET Standard **WeatherApp** вы будете писать общий для всех платформ код. На эту библиотеку будут ссылаться все пакеты приложений из проектов для iOS, Android и Windows.

Чтобы запустить этот пример, зарегистрируйтесь на сайте [http://openweathermap.org/appid](http://openweathermap.org/appid) для получения бесплатного ключа API.

Следующие действия добавляют в библиотеку .NET Standard код, который получает и сохраняет данные от метеослужбы:

1.  Щелкните проект **WeatherApp** правой кнопкой мыши и выберите пункт **Добавить > Класс…** В диалоговом окне **Добавление нового элемента** дайте файлу имя **Weather.cs**. Этот класс будет использован для хранения данных службы погоды.

2.  Замените все содержимое файла **Weather.cs** следующим кодом:

    ```csharp
    namespace WeatherApp
    {
        public class Weather
        {
            // Because labels bind to these values, set them to an empty string to
            // ensure that the label appears on all platforms by default.
            public string Title { get; set; } = " ";
            public string Temperature { get; set; } = " ";
            public string Wind { get; set; } = " ";
            public string Humidity { get; set; } = " ";
            public string Visibility { get; set; } = " ";
            public string Sunrise { get; set; } = " ";
            public string Sunset { get; set; } = " ";
        }
    }
    ```

3.  Добавьте в проект **WeatherApp** класс с именем **DataService.cs**, в котором вы будете обрабатывать полученные от метеослужбы данные JSON.

4.  Замените все содержимое файла **DataService.cs** следующим кодом:

    ```csharp
    using System.Net.Http;
    using System.Threading.Tasks;
    using Newtonsoft.Json;

    namespace WeatherApp
    {
        public class DataService
        {
            public static async Task<dynamic> getDataFromService(string queryString)
            {
                HttpClient client = new HttpClient();
                var response = await client.GetAsync(queryString);

                dynamic data = null;
                if (response != null)
                {
                    string json = response.Content.ReadAsStringAsync().Result;
                    data = JsonConvert.DeserializeObject(json);
                }

                return data;
            }
        }
    }
    ```

5.  Добавьте в проект **WeatherApp** третий класс с именем **Core.cs**, где будет размещаться базовая бизнес-логика. Этот код создает строку запроса с указанием почтового индекса, направляет этот запрос в метеослужбу, а затем заполняет экземпляр класса `Weather`.

6.  Замените содержимое файла **Core.cs** следующим кодом:

    ```csharp
    using System;
    using System.Threading.Tasks;

    namespace WeatherApp
    {
        public class Core
        {
            public static async Task<Weather> GetWeather(string zipCode)
            {
                //Sign up for a free API key at http://openweathermap.org/appid
                string key = "YOUR API KEY HERE";
                string queryString = "http://api.openweathermap.org/data/2.5/weather?zip="
                    + zipCode + ",us&appid=" + key + "&units=imperial";

                dynamic results = await DataService.getDataFromService(queryString).ConfigureAwait(false);

                if (results["weather"] != null)
                {
                    Weather weather = new Weather();
                    weather.Title = (string)results["name"];
                    weather.Temperature = (string)results["main"]["temp"] + " F";
                    weather.Wind = (string)results["wind"]["speed"] + " mph";
                    weather.Humidity = (string)results["main"]["humidity"] + " %";
                    weather.Visibility = (string)results["weather"][0]["main"];

                    DateTime time = new System.DateTime(1970, 1, 1, 0, 0, 0, 0);
                    DateTime sunrise = time.AddSeconds((double)results["sys"]["sunrise"]);
                    DateTime sunset = time.AddSeconds((double)results["sys"]["sunset"]);
                    weather.Sunrise = sunrise.ToString() + " UTC";
                    weather.Sunset = sunset.ToString() + " UTC";
                    return weather;
                }
                else
                {
                    return null;
                }
            }
        }
    }
    ```

7. Замените текст *YOUR API KEY HERE* полученным ключом API. Ключ должен быть заключен в кавычки.

8.  Выполните сборку проекта библиотеки **WeatherApp**, чтобы убедиться в правильности кода.

 <a name="uicode" />

## <a name="begin-writing-shared-ui-code"></a>Начало создания общего кода пользовательского интерфейса

Xamarin.Forms позволяет реализовать общий код пользовательского интерфейса в библиотеке .NET Standard. С помощью следующих действий мы добавим страницу в проект с кнопкой. Кнопка будет обновлять на странице данные, получаемые от метеослужбы, как было показано в предыдущем разделе:

1.  Добавьте **страницу содержимого** с именем **WeatherPage**, щелкнув правой кнопкой мыши проект **WeatherApp** и выбрав пункты **Добавить > Новый элемент**. В диалоговом окне **Добавление нового элемента** выберите **Страница содержимого**. Не перепутайте этот элемент с вариантами **Страница содержимого (C#)** и **Представление содержимого**. Назовите его **WeatherPage.xaml**.

    ![Добавление новой страницы XAML Xamarin.Forms](../cross-platform/media/crossplat-xamarin-formsguide-6.png "CrossPlat Xamarin FormsGuide 6")

     Xamarin.Forms основан на XAML, поэтому на этом шаге создается файл **WeatherPage.xaml** с вложенным файлом кода программной части **WeatherPage.xaml.cs**. Логику пользовательского интерфейса можно написать как в XAML, так и в коде. В этом пошаговом руководстве показаны оба варианта.

2.  Чтобы добавить кнопку на экран **WeatherPage**, замените содержимое файла **WeatherPage.xaml** следующей разметкой:

    ```xaml
    <?xml version="1.0" encoding="utf-8" ?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
           xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
           x:Class="WeatherApp.WeatherPage"
           Title="Sample Weather App">
      <Button x:Name="getWeatherBtn"
              Text="Get Weather"
              Clicked="GetWeatherBtn_Clicked" />
    </ContentPage>
    ```

     Обратите внимание, что имя кнопки должно быть задано с использованием атрибута `x:Name`, чтобы вы могли сослаться на эту кнопку по имени из файла кода программной части.

3.  Чтобы добавить обработчик событий `Clicked` кнопки в целях изменения текста кнопки, замените содержимое **WeatherPage.xaml.cs** на код, приведенный ниже. (Вы можете изменить 60601 на другой почтовый индекс.)

    ```csharp
    using System;
    using Xamarin.Forms;

    namespace WeatherApp
    {
        public partial class WeatherPage: ContentPage
        {
            public WeatherPage()
            {
                InitializeComponent();

                //Set the default binding to a default object for now
                BindingContext = new Weather();
            }

            private async void GetWeatherBtn_Clicked(object sender, EventArgs e)
            {
                Weather weather = await Core.GetWeather("60601");
                getWeatherBtn.Text = weather.Title;
            }
        }
    }
    ```

4.  Чтобы открывать **WeatherPage** в качестве первого экрана при запуске приложения, замените конструктор по умолчанию в **App.xaml.cs** следующим кодом:

    ```csharp
    public App()
    {
        InitializeComponent();

        MainPage = new NavigationPage(new WeatherPage());
    }
    ```

5.  Выполните сборку проекта **WeatherApp**, чтобы убедиться в правильности кода.

<a name="test" />

## <a name="test-your-app-using-the-visual-studio-emulator-for-android"></a>Проверьте приложение, используя эмулятор Visual Studio для Android

Теперь вы можете запустить приложение. Запустим только версию для Android, чтобы убедиться, что приложение получает данные из службы погоды. Версии для iOS и UWP вы проверите позже, когда добавите новые элементы интерфейса.

1.  Задайте проект **WeatherApp.Android** в качестве запускаемого проекта, щелкнув его правой кнопкой мыши и выбрав действие **Назначить запускаемым проектом**.

2.  Теперь на панели инструментов Visual Studio в качестве целевого проекта будет указан **WeatherApp.Android**. Выберите один из эмуляторов Android для отладки и нажмите клавишу **F5**. Мы рекомендуем использовать один из вариантов **эмулятора VisualStudio**, который запустит приложение в эмуляторе Visual Studio для Android.

    ![Выбор цели отладки для эмулятора Android](../cross-platform/media/crossplat-xamarin-formsguide-7.png "CrossPlat Xamarin FormsGuide 7")

    > [!NOTE]
    > Если Visual Studio показывает, что проект Android не может найти файл Newtonsoft.Json, добавьте этот пакет NuGet для проекта Android.

3.  При запуске приложения в эмуляторе нажмите кнопку **Get Weather** (Узнать погоду). Текст кнопки должен измениться на **Chicago** (Чикаго), так как именно это значение мы получили от метеослужбы в свойстве `Title`.

     ![Приложение прогноза погоды до и после нажатия кнопки](../cross-platform/media/crossplat-xamarin-formsguide-8.png "CrossPlat Xamarin FormsGuide 8")

<a name="finish" />

## <a name="finish-the-ui-with-a-native-look-and-feel-across-platforms"></a>Завершение пользовательского интерфейса с помощью собственного интерфейса на разных платформах

Xamarin.Forms отображает собственные элементы управления пользовательского интерфейса на каждой платформе, чтобы приложение автоматически выглядело как изначально предназначенное именно для нее. Чтобы продемонстрировать особенности собственного интерфейса более наглядно, завершим создание пользовательского интерфейса, добавив поле ввода для почтового индекса и элементы управления для отображения данных о погоде.

1.  Замените содержимое **WeatherPage.xaml** следующей разметкой. Элементы, имена которых задаются с помощью атрибута `x:Name`, как описано ранее, можно указывать в виде ссылок в коде. Xamarin.Forms также поддерживает некоторые [параметры макета](/xamarin/xamarin-forms/user-interface/controls/layouts). В нашем случае в WeatherPage используются элементы [Grid](http://developer.xamarin.com/api/type/Xamarin.Forms.Grid/) и [StackLayout](http://developer.xamarin.com/api/type/Xamarin.Forms.StackLayout/).

    ```xaml
    <?xml version="1.0" encoding="utf-8" ?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
                 xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
                 x:Class="WeatherApp.WeatherPage"
                 Title="Sample Weather App">

        <ContentPage.Resources>
            <ResourceDictionary>
                <Style x:Key="labelStyle" TargetType="Label">
                    <Setter Property="FontSize" Value="Small" />
                    <Setter Property="TextColor" Value="#404040" />
                </Style>
                <Style x:Key="fieldStyle" TargetType="Label">
                    <Setter Property="FontSize" Value="Medium" />
                    <Setter Property="Margin" Value="10,0,0,0" />
                </Style>
            </ResourceDictionary>
        </ContentPage.Resources>

        <StackLayout>
            <Grid BackgroundColor="#545454" Padding="10, 10, 10, 10">
                <Grid.RowDefinitions>
                    <RowDefinition Height="Auto" />
                    <RowDefinition Height="Auto" />
                </Grid.RowDefinitions>

                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="Auto" />
                    <ColumnDefinition Width="*" />
                    <ColumnDefinition Width="Auto" />
                </Grid.ColumnDefinitions>

                <Label Text="Search by Zip Code"
                       Grid.Row="0" Grid.Column="0" Grid.ColumnSpan="3"
                       HorizontalOptions="Center"
                       TextColor="White" FontAttributes="Bold" FontSize="Medium" />

                <Label x:Name="zipCodeLabel" Text="Zip Code:"
                       Grid.Row="1" Grid.Column="0"
                       VerticalOptions="Center"
                       Style="{StaticResource labelStyle}"
                       TextColor="#C0C0C0" />

                <Entry x:Name="zipCodeEntry"
                       Grid.Row="1" Grid.Column="1"
                       VerticalOptions="Center"
                       Margin="5,0"
                       BackgroundColor="DarkGray"
                       TextColor="White" />

                <Button x:Name="getWeatherBtn" Text="Get Weather"
                        Grid.Row="1" Grid.Column="2"
                        HorizontalOptions="Center"
                        VerticalOptions="Center"
                        BorderWidth="1"
                        BorderColor="White"
                        BackgroundColor="DarkGray"
                        TextColor="White"
                        Clicked="GetWeatherBtn_Clicked" />
            </Grid>

            <ScrollView VerticalOptions="FillAndExpand">
                <StackLayout Padding="10,10,10,10" HorizontalOptions="Start">
                    <Label Text="Location" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Title}" Style="{StaticResource fieldStyle}" />

                    <Label Text="Temperature" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Temperature}" Style="{StaticResource fieldStyle}" />

                    <Label Text="Wind Speed" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Wind}" Style="{StaticResource fieldStyle}" />

                    <Label Text="Humidity" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Humidity}" Style="{StaticResource fieldStyle}" />

                    <Label Text="Visibility" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Visibility}" Style="{StaticResource fieldStyle}" />

                    <Label Text="Time of Sunrise" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Sunrise}" Style="{StaticResource fieldStyle}" />

                    <Label Text="Time of Sunset" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Sunset}" Style="{StaticResource fieldStyle}" />
                </StackLayout>
            </ScrollView>
        </StackLayout>
    </ContentPage>
     ```

     Тег `OnPlatform` файлов XAML, который здесь не представлен, позволяет выбрать значение свойства, относящееся к текущей платформе, на которой выполняется приложение (см. руководство по [основному синтаксису XAML](/xamarin/xamarin-forms/xaml/xaml-basics/essential-xaml-syntax/)). По файлу кода программной части можно определить, на какой платформе выполняются приложения, путем сравнения значения свойства [`Device.RuntimePlatform`](https://developer.xamarin.com/api/property/Xamarin.Forms.Device.RuntimePlatform/) с константами, определенными в классе [`Device`](https://developer.xamarin.com/api/type/Xamarin.Forms.Device/): [`Device.iOS`](https://developer.xamarin.com/api/field/Xamarin.Forms.Device.iOS/), [`Device.Android`](https://developer.xamarin.com/api/field/Xamarin.Forms.Device.Android/) и [`Device.UWP`](https://developer.xamarin.com/api/field/Xamarin.Forms.Device.UWP/).

2.  В **WeatherPage.xaml.cs** замените обработчик событий `GetWeatherBtn_Clicked` следующим кодом. Этот код проверяет, введен ли почтовый индекс в поле ввода, и получает данные для этого почтового индекса. Затем он задает контекст привязки всей страницы на результирующий экземпляр класса `Weather`. В завершении код устанавливает текст "Искать еще раз" в качестве текста кнопки. Каждая метка в пользовательском интерфейсе привязывается к свойству класса `Weather`. После установки значение контекста привязки экрана на экземпляр класса `Weather` эти метки будут обновляться автоматически.

    ```csharp
    private async void GetWeatherBtn_Clicked(object sender, EventArgs e)
    {
        if (!String.IsNullOrEmpty(zipCodeEntry.Text))
        {
            Weather weather = await Core.GetWeather(zipCodeEntry.Text);
            BindingContext = weather;
            getWeatherBtn.Text = "Search Again";
        }
    }
    ```

3.  Запустите приложение на всех трех платформах. Для этого щелкните нужный проект правой кнопкой мыши, выберите **Назначить запускаемым проектом** и откройте приложение на устройстве или в эмуляторе. Введите допустимый пятизначный почтовый индекс США и нажмите кнопку **Get Weather** (Узнать погоду), чтобы отобразить погодные данные для этого региона. Чтобы запустить проект в iOS, Visual Studio необходимо подключить по сети к компьютеру Mac.

     [![Образец приложения прогнозов погоды для iOS, Android и UWP](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")](../cross-platform/media/crossplat-xamarin-formsguide-1-Large.png#lightbox)

Полный исходный код для этого проекта можно найти в [репозитории примеров xamarin-forms на GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).
