---
title: Основы создания приложений с помощью Xamarin.Forms
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: d22b5186-9e03-4e85-afc9-7cbe28522a6d
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: 6d10240383ddaf4ec2eb242dfc180c59ff084f1d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54780266"
---
# <a name="learn-app-building-basics-with-xamarinforms-in-visual-studio"></a>Основы создания приложений с помощью Xamarin.Forms в Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Если вы выполнили шаги в [Setup and install](../cross-platform/setup-and-install.md) и [Verify your Xamarin environment](../cross-platform/verify-your-xamarin-environment.md), в этом пошаговом руководстве будет рассказано, как создать базовое приложение (показано ниже) с помощью Xamarin.Forms. Используя Xamarin.Forms, вы напишете весь код пользовательского интерфейса один раз в переносимой библиотеке классов (PCL). Затем Xamarin автоматически будет отображать собственные элементы управления пользовательского интерфейса для платформ iOS, Android и Windows. Это рекомендуемый подход, так как переносимая библиотека классов предоставляет оптимальную поддержку только тех интерфейсов API .NET, которые поддерживаются на всех целевых платформах, а также потому, что Xamarin.Forms позволяет совместно использовать код пользовательского интерфейса на разных платформах.

 ![Образец приложения прогнозов погоды на Android, iOS и Windows Phone](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")

 Вам предстоит выполнить следующие действия.

-   [Настройка решения](#solution)

-   [Создание общего кода для службы данных](#dataservice)

-   [Начало создания общего кода пользовательского интерфейса](#uicode)

-   [Проверьте приложение, используя эмулятор Visual Studio для Android](#test)

-   [Завершение пользовательского интерфейса с помощью собственного интерфейса на разных платформах](#finish)

> [!TIP]
>  Полный исходный код для этого проекта можно найти в [репозитории образцов xamarin-forms на GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).

##  <a name="solution"></a> Настройка решения
 Эти шаги создают решение Xamarin.Forms, которое содержит переносимую библиотеку классов для общего кода и два добавленных пакета NuGet.

1.  В Visual Studio создайте новое **пустое приложение (Xamarin.Forms Portable)** и назовите его **WeatherApp**. Проще всего найти этот шаблон, введя **Xamarin.Forms** в поле поиска.

     Если он отсутствует, может потребоваться установить Xamarin или включить компонент Visual Studio 2015 (см. раздел [Установка и настройка](../cross-platform/setup-and-install.md)).

     ![Создание проекта пустого приложения &#40;Xamarin.Forms Portable&#41;](../cross-platform/media/crossplat-xamarin-formsguide-2.png "CrossPlat Xamarin FormsGuide 2")

2.  Нажав кнопку "ОК" для создания решения, вы получите несколько отдельных проектов.

    -   **WeatherApp (переносимое)**: библиотека переносимых классов, в которой вы напишете общий код для разных платформ, включая общую бизнес-логику и код пользовательского интерфейса с помощью Xamarin.Forms.

    -   **WeatherApp.Droid**: проект, который содержит машинный код для Android. Он задается как запускаемый проект по умолчанию.

    -   **WeatherApp.iOS**: проект, который содержит машинный код для iOS.

    -   **WeatherApp.UWP**: проект, который содержит код Windows 10 UWP.

    -   **WeatherApp.Windows (Windows 8.1)**: проект, который содержит машинный код Windows 8.1.

    -   **WeatherApp.WinPhone (Windows Phone 8.1)**: проект, который содержит машинный код Windows Phone.

    > [!NOTE]
    >  Вы можете удалить любой проект, нацеленный не на нужную вам платформу. В этом пошаговом руководстве мы будем ссылаться на проекты Android, iOS и Windows Phone 8.1. Работа с проектами UWP и Windows 8.1 аналогична работе с проектом Windows Phone 8.1.

     В каждом проекте с машинным кодом вы получите доступ к собственному конструктору для соответствующей платформы и можете при необходимости реализовать экраны и функции для конкретной платформы.

3.  Обновите пакет NuGet Xamarin.Forms в решении до последней стабильной версии следующим образом. Это рекомендуется делать каждый раз при создании нового решения Xamarin.

    -   Выберите пункты меню **"Сервис" > "Диспетчер пакетов NuGet" > "Управление пакетами NuGet для решения"**.

    -   На вкладке **Обновления** установите флажки для обновления **Xamarin.Forms** , а также обновлений всех проектов в решении. (Примечание. Не устанавливайте флажки для обновлений Xamarin.Android.Support.)

    -   Укажите в поле **Версия** **последнюю стабильную** версию.

    -   Нажмите кнопку **Обновить**.

         ![Обновление пакета NuGet Xamarin.Forms](../cross-platform/media/crossplat-xamarin-formsguide-4.png "CrossPlat Xamarin FormsGuide 4")

4.  Добавьте **Newtonsoft.Json** и пакет NuGet в проект PCL. Они будут использоваться для обработки информации, полученной от службы данных о погоде.

    -   В диспетчере пакетов NuGet (открытом на шаге 3) выберите вкладку **Обзор** и найдите **Newtonsoft**.

    -   Выберите **Newtonsoft.Json**.

    -   Установите флажок напротив проекта **WeatherApp** (это единственный проект, в котором потребуется установить пакет).

    -   Убедитесь, что в поле **Версия** указана **последняя стабильная** версия.

    -   Нажмите кнопку **Установить**.

    -   ![Поиск и установка пакета NuGet Newtonsoft.Json](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin FormsGuide 5")

5.  Повторите шаги 4, чтобы найти и установить пакет **Microsoft.Net.Http** .

6.  Соберите свое решение и убедитесь в отсутствии ошибок сборки.

##  <a name="dataservice"></a> Создание общего кода для службы данных
 Именно в проекте **WeatherApp (переносимый)** вы будете писать код для переносимой библиотеки классов, общей для всех платформ. Переносимая библиотека классов автоматически включается в пакеты приложений, создаваемые проектами для iOS, Android и Windows Phone.

 Чтобы запустить этот пример, зарегистрируйтесь на сайте [http://openweathermap.org/appid](http://openweathermap.org/appid) для получения бесплатного ключа API.

 В следующих шагах в переносимую библиотеку классов добавляется код для доступа к данным из службы погоды и их хранения.

1.  Щелкните проект **WeatherApp** правой кнопкой мыши и выберите пункт **"Добавить" > "Класс…"**. В диалоговом окне **Добавление нового элемента** дайте файлу имя **Weather.cs**. Этот класс будет использован для хранения данных службы погоды.

2.  Замените все содержимое файла **Weather.cs** следующим кодом:

    ```csharp
    namespace WeatherApp
    {
        public class Weather
        {
            public string Title { get; set; }
            public string Temperature { get; set; }
            public string Wind { get; set; }
            public string Humidity { get; set; }
            public string Visibility { get; set; }
            public string Sunrise { get; set; }
            public string Sunset { get; set; }

            public Weather()
            {
                //Because labels bind to these values, set them to an empty string to
                //ensure that the label appears on all platforms by default.
                this.Title = " ";
                this.Temperature = " ";
                this.Wind = " ";
                this.Humidity = " ";
                this.Visibility = " ";
                this.Sunrise = " ";
                this.Sunset = " ";
            }
        }
    }
    ```

3.  Добавьте в проект переносимой библиотеки классов класс **DataService.cs** , в котором вы будете обрабатывать данные JSON из службы погоды.

4.  Замените все содержимое файла **DataService.cs** следующим кодом:

    ```csharp
    using System.Threading.Tasks;
    using Newtonsoft.Json;
    using System.Net.Http;

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

5.  Добавьте в переносимую библиотеку классов третий класс **Core** , где будет размещаться общая бизнес-логика, которая, например, формирует строку запроса с помощью почтового индекса, вызывает службу погоды и заполняет экземпляр класса **Weather** .

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

7.  Соберите проект переносимой библиотеки классов **WeatherApp** , чтобы убедиться в правильности кода.

##  <a name="uicode"></a> Начало создания общего кода пользовательского интерфейса
 Xamarin.Forms позволяет реализовать общий код пользовательского интерфейса в переносимой библиотеке классов. На этих шагах вы добавите к переносимой библиотеке классов экран с кнопкой, которая меняет свой текст в зависимости от данных, возвращенных кодом службы погоды, добавленным в предыдущем разделе:

1.  Добавьте **страницу Forms Xaml** с именем **WeatherPage.cs**, щелкнув правой кнопкой мыши проект **WeatherApp** и выбрав пункты **"Добавить" > "Новый элемент..."**. В диалоговом окне **Добавление нового элемента** найдите Forms, выберите **страницу Forms Xaml**и назовите ее **WeatherPage.cs**.

     Xamarin.Forms основан на XAML, поэтому на этом шаге создается файл **WeatherPage.xaml** с вложенным файлом кода программной части **WeatherPage.xaml.cs**. Это позволяет создать пользовательский интерфейс в XAML или коде. В этом пошаговом руководстве показаны оба варианта.

     ![Добавление новой страницы XAML Xamarin.Forms](../cross-platform/media/crossplat-xamarin-formsguide-6.png "CrossPlat Xamarin FormsGuide 6")

2.  Чтобы добавить кнопку на экран WeatherPage, замените содержимое WeatherPage.xaml следующим:

    ```xaml
    <?xml version="1.0" encoding="utf-8" ?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
           xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
           x:Class="WeatherApp.WeatherPage">
      <Button x:Name="getWeatherBtn" Text="Get Weather"/>
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
                this.Title = "Sample Weather App";
                getWeatherBtn.Clicked += GetWeatherBtn_Clicked;

                //Set the default binding to a default object for now
                this.BindingContext = new Weather();
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
        MainPage = new NavigationPage(new WeatherPage());
    }
    ```

5.  Соберите проект переносимой библиотеки классов WeatherApp, чтобы убедиться в правильности кода.

##  <a name="test"></a> Проверьте приложение, используя эмулятор Visual Studio для Android
 Теперь вы можете запустить приложение. Запустим только версию для Android, чтобы убедиться, что приложение получает данные из службы погоды. После добавления дополнительных элементов управления пользовательского интерфейса вы также запустите версии для iOS и Windows Phone. (Примечание. При запуске Visual Studio в Windows 7 вы будете следовать тем же шагам, но с Xamarin Player.)

1.  Задайте проект **WeatherApp.Droid** в качестве запускаемого проекта: щелкните его правой кнопкой мыши и выберите **Назначить запускаемым проектом**.

2.  На панели инструментов Visual Studio в качестве целевого проекта будет указан **WeatherApp.Droid** . Выберите один из эмуляторов Android для отладки и нажмите клавишу **F5**. Рекомендуется использовать один из вариантов **эмулятора VS** , который запустит приложение в эмуляторе Visual Studio для Android.

     ![Выбор цели отладки эмулятора VS](../cross-platform/media/crossplat-xamarin-formsguide-7.png "CrossPlat Xamarin FormsGuide 7")

3.  При запуске приложения в эмуляторе нажмите кнопку **Get Weather** (Узнать погоду). Текст кнопки должен измениться на **Weather for Chicago, IL**(Погода в Чикаго, Иллинойс), что соответствует свойству *Title* данных, полученных от поставщика погодных данных.

     ![Приложение прогноза погоды до и после нажатия кнопки](../cross-platform/media/crossplat-xamarin-formsguide-8.png "CrossPlat Xamarin FormsGuide 8")

##  <a name="finish"></a> Завершение пользовательского интерфейса с помощью собственных элементов управления на разных платформах
 Xamarin.Forms отображает собственные элементы управления пользовательского интерфейса на каждой платформе, чтобы приложение автоматически выглядело как изначально предназначенное именно для нее. Чтобы увидеть это более подробно, добавим в пользовательский интерфейс поле ввода для почтового индекса, а затем отобразим данные погоды, возвращенные из службы.

1. Замените содержимое **WeatherPage.xaml** кодом ниже. Обратите внимание, что каждый элемент именован с использованием атрибута **x:Name** , как описано ранее, чтобы на элемент могла указывать ссылка из кода. Xamarin.Forms также предоставляет ряд [параметров макета](http://developer.xamarin.com/guides/xamarin-forms/controls/layouts/) (xamarin.com); здесь WeatherPage использует [StackLayout](http://developer.xamarin.com/api/type/Xamarin.Forms.StackLayout/) (xamarin.com).

   ```xaml
   <?xml version="1.0" encoding="utf-8" ?>
   <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
          xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
          x:Class="WeatherApp.WeatherPage">

     <ContentPage.Resources>
       <ResourceDictionary>
         <Style x:Key="labelStyle" TargetType="Label">
           <Setter Property="TextColor" Value="#a8a8a8" />
           <Setter Property="FontSize" Value="Small" />
         </Style>
         <Style x:Key="fieldStyle" TargetType="Label">
           <Setter Property="TextColor">
             <OnPlatform x:TypeArguments="Color" iOS="Black" Android="White" WinPhone="White" />
           </Setter>
           <Setter Property="FontSize" Value="Medium" />
         </Style>
         <Style x:Key="fieldView" TargetType="ContentView">
           <Setter Property="Padding" Value="10,0,0,0" />
         </Style>
       </ResourceDictionary>
     </ContentPage.Resources>

     <ContentPage.Content>
       <ScrollView>
         <StackLayout>
           <StackLayout Orientation="Horizontal" HorizontalOptions="FillAndExpand"
                 BackgroundColor="#545454">
             <StackLayout Padding="10,10,10,10" HorizontalOptions="Start">
               <Label Text="Search by Zip Code" TextColor="White" FontAttributes="Bold"
                   FontSize="Medium" />
               <Label x:Name="zipCodeLabel" Text="Zip Code" Style="{StaticResource labelStyle}" />
               <Entry x:Name="zipCodeEntry" />
             </StackLayout>
             <StackLayout Padding="0,0,0,10" VerticalOptions="End">
               <Button x:Name="getWeatherBtn" Text="Get Weather" WidthRequest="185" BorderWidth="1" >
                 <!-- Set iOS colors; use defaults on other platforms -->
                 <Button.TextColor>
                   <OnPlatform x:TypeArguments="Color" iOS="White"/>
                 </Button.TextColor>
                 <Button.BorderColor>
                   <OnPlatform x:TypeArguments="Color" iOS="White"/>
                 </Button.BorderColor>
               </Button>
             </StackLayout>
           </StackLayout>
           <StackLayout Padding="10,10,10,10" HorizontalOptions="Start">
             <Label Text="Location" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label Text="{Binding Title}" Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Temperature" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="tempLabel" Text="{Binding Temperature}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Wind Speed" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="windLabel" Text="{Binding Wind}" Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Humidity" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="humidityLabel" Text="{Binding Humidity}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Visibility" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="visibilitylabel" Text="{Binding Visibility}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Time of Sunrise" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="sunriseLabel" Text="{Binding Sunrise}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Time of Sunset" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="sunsetLabel" Text="{Binding Sunset}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
           </StackLayout>
         </StackLayout>
       </ScrollView>
     </ContentPage.Content>
   </ContentPage>
   ```

    Обратите внимание на использование тега **OnPlatform** в Xamarin.Forms. **OnPlatform** выбирает значение свойства, относящееся к текущей платформе, на которой выполняется приложение (см. статью [External XAML Syntax](http://developer.xamarin.com/guides/xamarin-forms/user-interface/xaml-basics/essential_xaml_syntax/) (Внешний синтаксис XAML) на сайте xamarin.com). Мы используем его для задания другого цвета текста для полей данных: Белого на Android и Windows Phone, черного на iOS. Вы можете использовать **OnPlatform** для любых свойств и типов данных в целях внесения специальных настроек в XAML. В файле кода программной части можно использовать [API Device.OnPlatform](http://developer.xamarin.com/guides/xamarin-forms/platform-features/device/) для той же цели.

2. В **WeatherPage.xaml.cs**замените обработчик событий **GetWeatherBtn_Clicked** кодом ниже. Этот код проверяет, существует ли почтовый индекс, указанный в поле ввода, извлекает данные для этого почтового индекса, задает результирующий экземпляр класса Weather в качестве контекста привязки всего экрана, в затем задает в качестве текста кнопки Search Again (Повторить поиск). Обратите внимание, что каждая метка в пользовательском интерфейсе привязывается к свойству класса Weather, поэтому при указании контекста привязки экрана к экземпляру **Weather** эти метки обновляются автоматически.

   ```csharp
   private async void GetWeatherBtn_Clicked(object sender, EventArgs e)
   {
       if (!String.IsNullOrEmpty(zipCodeEntry.Text))
       {
           Weather weather = await Core.GetWeather(zipCodeEntry.Text);
           this.BindingContext = weather;
           getWeatherBtn.Text = "Search Again";
       }
   }
   ```

3. Запустите приложение на всех трех платформах (Android, iOS и Windows Phone): щелкните правой кнопкой мыши соответствующий проект, выберите "Назначить запускаемым проектом" и запустите приложение на устройстве или в эмуляторе. Введите допустимый почтовый индекс в США (например, 60601) и нажмите кнопку Get Weather (Узнать погоду), чтобы отобразить погодные данные для этого региона, как показано ниже. Вам потребуется подключить Visual Studio к компьютеру с Mac OS X в сети в случае проекта для iOS.

    ![Образец приложения прогнозов погоды на Android, iOS и Windows Phone](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")

   Полный исходный код для этого проекта можно найти в [репозитории примеров xamarin-forms на GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).
