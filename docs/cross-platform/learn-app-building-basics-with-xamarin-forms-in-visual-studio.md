---
title: "Основы создания приложений с помощью Xamarin.Forms в Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 01/19/2018
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d22b5186-9e03-4e85-afc9-7cbe28522a6d
ms.technology: vs-ide-mobile
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- xamarin
ms.openlocfilehash: 71470cd03844c7761afbd07c9d454214f5dc36ca
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2018
---
# <a name="learn-app-building-basics-with-xamarinforms-in-visual-studio"></a>Основы создания приложений с помощью Xamarin.Forms в Visual Studio

Если вы выполнили шаги в [Setup and install](../cross-platform/setup-and-install.md) и [Verify your Xamarin environment](../cross-platform/verify-your-xamarin-environment.md), в этом пошаговом руководстве будет рассказано, как создать базовое приложение (показано ниже) с помощью Xamarin.Forms. Используя Xamarin.Forms, вы запишете весь код пользовательского интерфейса в один файл библиотеки классов .NET Standard. Xamarin будет автоматически отображать поддерживаемые элементы управления для пользовательского интерфейса на платформах iOS, Android и Windows. Мы рекомендуем использовать именно этот подход вместо совместного использования проектов. Здесь важно то, что библиотеки .NET Standard включают только те интерфейсы API .NET, которые поддерживаются на всех целевых платформах, а Xamarin.Forms позволяет использовать один и тот же код пользовательского интерфейса на разных платформах.  
  
![Образец приложения прогнозов погоды для Android, iOS и Windows](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")  
  
Вам предстоит выполнить следующие действия.  
  
-   [Настройка решения](#solution)  
  
-   [Создание общего кода для службы данных](#dataservice)  
  
-   [Начало создания общего кода пользовательского интерфейса](#uicode)  
  
-   [Проверьте приложение, используя эмулятор Visual Studio для Android](#test)  
  
-   [Завершение пользовательского интерфейса с помощью собственного интерфейса на разных платформах](#finish)  
  
> [!TIP]
> Полный исходный код для этого проекта можно найти в [репозитории образцов xamarin-forms на GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).  
  
##  <a name="solution"></a> Настройка решения  

Эти шаги создают решение Xamarin.Forms, которое содержит библиотеку классов .NET Standard и два дополнительных пакета NuGet.  
  
1.  В Visual Studio создайте новое **кроссплатформенное приложение (Xamarin.Forms Portable)** и назовите его **WeatherApp**. Чтобы найти шаблон, в списке слева выберите **Visual C#** и **Кроссплатформенные**.  
  
     Если он отсутствует, вам придется установить Xamarin или включить компонент Visual Studio 2017 (см. раздел [Установка и настройка](../cross-platform/setup-and-install.md)).  
  
     ![Создание проекта пустого кроссплатформенного приложения &#40;Xamarin.Forms Portable&#41;](../cross-platform/media/crossplat-xamarin-formsguide-2.png "CrossPlat Xamarin FormsGuide 2")

2.  Нажав кнопку "ОК", вы сможете настроить некоторые параметры. Выберите **Пустое приложение**, **Xamarin.Forms** и **.NET Standard**:

     ![Создание нового проекта кроссплатформенного приложения](../cross-platform/media/crossplat-xamarin-formsguide-3.png "CrossPlat Xamarin FormsGuide 3")
  
3.  Нажав кнопку ОК для создания решения, вы получите несколько отдельных проектов.  
  
    -   **WeatherApp**. Это библиотека .NET Standard, в которую вы поместите основанный на Xamarin.Forms код базовой бизнес-логики и пользовательского интерфейса для использования на нескольких платформах.  
  
    -   **WeatherApp.Droid**. Это проект, который содержит машинный код для Android. Он задается как запускаемый проект по умолчанию.  
  
    -   **WeatherApp.iOS**: проект, который содержит машинный код для iOS.  
  
    -   **WeatherApp.UWP**: проект, который содержит код Windows 10 UWP.  
  
    > [!NOTE]
    >  Вы можете удалить любой проект, нацеленный не на нужную вам платформу.   
  
     В каждом проекте с машинным кодом вы получите доступ к собственному конструктору для соответствующей платформы и можете при необходимости реализовать экраны и функции для конкретной платформы.  
  
4.  Обновите пакет NuGet Xamarin.Forms в решении до последней стабильной версии следующим образом. Это рекомендуется делать каждый раз при создании нового решения Xamarin.  
  
    -   Выберите пункты меню **"Сервис" > "Диспетчер пакетов NuGet" > "Управление пакетами NuGet для решения"**.  
  
    -   На вкладке **Обновления** выберите пакет **Xamarin.Forms** и установите флажки для обновления всех проектов в решении. (Примечание. Не устанавливайте флажки для обновлений Xamarin.Android.Support.)  
  
    -   Укажите в поле **Версия** **последнюю стабильную** версию.  
  
    -   Нажмите кнопку **Установить**.  
  
         ![Обновление пакета NuGet Xamarin.Forms](../cross-platform/media/crossplat-xamarin-formsguide-4.png "CrossPlat Xamarin FormsGuide 4")  
  
5.  Добавьте в проект **WeatherApp** пакет NuGet **Newtonsoft.Json**, который пригодится для обработки информации, полученной от метеослужбы.  
  
    -   В диспетчере пакетов NuGet (который вы открыли на шаге 4) выберите вкладку **Обзор** и найдите **Newtonsoft**.  
  
    -   Выберите **Newtonsoft.Json**.  
  
    -   Установите флажок напротив проекта **WeatherApp** (это единственный проект, в котором потребуется установить пакет).  
  
    -   Убедитесь, что в поле **Версия** указана **последняя стабильная** версия.  
  
    -   Нажмите кнопку **Установить**.  
  
    ![Поиск и установка пакета NuGet Newtonsoft.Json](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin FormsGuide 5")  
  
6.  Повторите шаг 5, чтобы найти и установить пакет **Microsoft.Net.Http**.  
  
7.  Соберите свое решение и убедитесь в отсутствии ошибок сборки.  
  
##  <a name="dataservice"></a> Создание общего кода для службы данных  

Именно в проекте **WeatherApp** вы будете писать код для библиотеки .NET Standard, общей для всех платформ. Эта библиотека автоматически включается во все пакеты приложений из проектов для iOS, Android и Windows.  
  
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
  
5.  Добавьте в проект **WeatherApp** третий класс с именем **Core**, где будет размещаться базовая бизнес-логика. Этот код создает строку запроса с указанием почтового индекса, направляет этот запрос в метеослужбу, а затем заполняет экземпляр класса **Weather**.  
  
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
                string key = "YOUR KEY HERE";  
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
  
7.  Выполните сборку проекта библиотеки **WeatherApp**, чтобы убедиться в правильности кода.  
  
##  <a name="uicode"></a> Начало создания общего кода пользовательского интерфейса  

Xamarin.Forms позволяет реализовать общий код пользовательского интерфейса в библиотеке .NET Standard. На этих шагах вы добавите в проект новую страницу с кнопкой, текст которой изменяется в зависимости от данных метеослужбы, полученных в коде предыдущего раздела:  
  
1.  Добавьте **страницу содержимого** с именем **WeatherPage.cs**, щелкнув правой кнопкой мыши проект **WeatherApp** и выбрав пункты **Добавить > Новый элемент**. В диалоговом окне **Добавление нового элемента** выберите **Страница содержимого**. Не перепутайте этот элемент с вариантами **Страница содержимого (C#)** и **Представление содержимого**. Назовите его **WeatherPage.cs**.  
  
     ![Добавление новой страницы XAML Xamarin.Forms](../cross-platform/media/crossplat-xamarin-formsguide-6.png "CrossPlat Xamarin FormsGuide 6")  
  
     Xamarin.Forms основан на XAML, поэтому на этом шаге создается файл **WeatherPage.xaml** с вложенным файлом кода программной части **WeatherPage.xaml.cs**. Это позволяет создать пользовательский интерфейс в XAML или коде. В этом пошаговом руководстве показаны оба варианта.  
  
2.  Чтобы добавить кнопку на экран WeatherPage, замените содержимое файла **WeatherPage.xaml** следующим текстом:  
  
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
  
     Обратите внимание, что имя кнопки должно быть задано с использованием атрибута **x:Name** , чтобы вы могли сослаться на эту кнопку по имени из файла кода программной части.  
  
3.  Чтобы добавить обработчик событий **Clicked** кнопки в целях изменения текста кнопки, замените содержимое **WeatherPage.xaml.cs** на код, приведенный ниже. (Вы можете изменить 60601 на другой почтовый индекс.)  
  
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
  
4.  Чтобы открывать **WeatherPage** в качестве первого экрана при запуске приложения, замените конструктор по умолчанию в **App.cs** следующим кодом:  
  
    ```csharp  
    public App()  
    {
        InitializeComponent();

        MainPage = new NavigationPage(new WeatherPage());  
    }  
    ```  
  
5.  Выполните сборку проекта **WeatherApp**, чтобы убедиться в правильности кода.  
  
##  <a name="test"></a> Проверьте приложение, используя эмулятор Visual Studio для Android  

Теперь вы можете запустить приложение. Запустим только версию для Android, чтобы убедиться, что приложение получает данные из службы погоды. Версии для iOS и UWP вы проверите позже, когда добавите новые элементы интерфейса.   
  
1.  Задайте проект **WeatherApp.Android** в качестве запускаемого проекта, щелкнув его правой кнопкой мыши и выбрав действие **Назначить запускаемым проектом**.  
  
2.  Теперь на панели инструментов Visual Studio в качестве целевого проекта будет указан **WeatherApp.Android**. Выберите один из эмуляторов Android для отладки и нажмите клавишу **F5**. Мы рекомендуем использовать один из вариантов **эмулятора VisualStudio**, который запустит приложение в эмуляторе Visual Studio для Android.  
  
     ![Выбор цели отладки для эмулятора Android](../cross-platform/media/crossplat-xamarin-formsguide-7.png "CrossPlat Xamarin FormsGuide 7")  
  
3.  При запуске приложения в эмуляторе нажмите кнопку **Get Weather** (Узнать погоду). Текст кнопки должен измениться на **Chicago** (Чикаго), так как именно это значение мы получили от метеослужбы в свойстве *Title*.  
  
     ![Приложение прогноза погоды до и после нажатия кнопки](../cross-platform/media/crossplat-xamarin-formsguide-8.png "CrossPlat Xamarin FormsGuide 8")  
  
##  <a name="finish"></a> Завершение пользовательского интерфейса с помощью собственных элементов управления на разных платформах  

Xamarin.Forms отображает собственные элементы управления пользовательского интерфейса на каждой платформе, чтобы приложение автоматически выглядело как изначально предназначенное именно для нее. Чтобы увидеть это более подробно, добавим в пользовательский интерфейс поле ввода для почтового индекса, а затем отобразим данные погоды, возвращенные из службы.  
  
1.  Замените содержимое **WeatherPage.xaml** кодом ниже. Элементы, имена которых задаются с помощью атрибута **x:Name**, как описано ранее, можно указывать в виде ссылок в коде. Xamarin.Forms также поддерживает некоторые [параметры макета](http://developer.xamarin.com/guides/xamarin-forms/controls/layouts/) (xamarin.com). Наше приложение WeatherPage использует [Grid](http://developer.xamarin.com/api/type/Xamarin.Forms.Grid/) (xamarin.com) и [StackLayout](http://developer.xamarin.com/api/type/Xamarin.Forms.StackLayout/) (xamarin.com).  
  
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
  
     Тег **OnPlatform**, который здесь не представлен, позволяет выбрать значение свойства, относящееся к текущей платформе, на которой выполняется приложение (см. руководство по [основному синтаксису XAML](http://developer.xamarin.com/guides/xamarin-forms/user-interface/xaml-basics/essential_xaml_syntax/) на сайте xamarin.com). В файле кода программной части можно использовать [API Device.OnPlatform](http://developer.xamarin.com/guides/xamarin-forms/platform-features/device/) для той же цели.  
  
2.  В **WeatherPage.xaml.cs**замените обработчик событий **GetWeatherBtn_Clicked** кодом ниже. Этот код проверяет, существует ли указанный в поле ввода почтовый индекс, извлекает данные для этого почтового индекса, задает полученный экземпляр класса **Weather** в качестве контекста привязки для всей страницы и заменяет текст кнопки фразой "Search Again" (Повторить поиск). Обратите внимание, что каждая метка в пользовательском интерфейсе привязывается к свойству класса **Weather**, поэтому метки обновляются автоматически, когда вы указываете контекста привязки экрана к экземпляру **Weather**.  
  
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
  
3.  Запустите приложение на всех трех платформах (Android, iOS и Windows). Для этого щелкните нужный проект правой кнопкой мыши, выберите **Set as startup project** (Назначить запускаемым проектом) и откройте приложение на устройстве или в эмуляторе. Введите допустимый пятизначный почтовый индекс США и нажмите кнопку **Get Weather** (Узнать погоду), чтобы отобразить погодные данные для этого региона, как показано ниже. Чтобы запустить проект в iOS, Visual Studio необходимо подключить по сети к компьютеру под управлением Mac OS X.  
  
     ![Образец приложения прогнозов погоды на Android, iOS и Windows Phone](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")  
  
Полный исходный код для этого проекта можно найти в [репозитории примеров xamarin-forms на GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).