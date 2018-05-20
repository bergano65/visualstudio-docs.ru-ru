---
title: Создание приложений с собственным пользовательским интерфейсом с использованием Xamarin в Visual Studio
ms.custom: ''
ms.date: 03/30/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 30f137e6-595d-4ce7-b8f5-415b07c1caa2
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 3d813226dfa79a65da85a2b17e54306d12a4ed09
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/11/2018
---
# <a name="build-apps-with-native-ui-using-xamarin-in-visual-studio"></a>Создание приложений с нативным пользовательским интерфейсом с использованием Xamarin в Visual Studio

Большинство разработчиков, выбирающих Xamarin и C# для создания кроссплатформенных мобильных приложений, используют Xamarin.Forms. Xamarin.Forms определяет пользовательский интерфейс, который сопоставляется с собственными элементами управления в iOS, Android и универсальной платформе Windows (UWP). Описание Xamarin.Forms см. в статье [Основы создания приложений с помощью Xamarin.Forms в Visual Studio](learn-app-building-basics-with-xamarin-forms-in-visual-studio.md).

В этой статье описывается другой подход, который включает в себя доступ к функциям API собственного пользовательского интерфейса для каждой платформы. Работа с собственными API гораздо сложнее, чем использование Xamarin.Forms, поскольку требуются глубокие знания каждой платформы. Преимущество заключается в том, что вы можете адаптировать пользовательский интерфейс к конкретным преимуществам и возможностям каждой платформы, но при этом по-прежнему использовать общую бизнес-логику.

Выполнив действия, описанные в разделах [Установка и настройка](../cross-platform/setup-and-install.md) и [Проверка среды Xamarin](../cross-platform/verify-your-xamarin-environment.md), вы можете перейти к этому пошаговому руководству, в котором описано, как создать базовое приложение Xamarin с собственным пользовательским интерфейсом. При использовании собственного пользовательского интерфейса общий код находится в библиотеке .NET Standard, а проекты для отдельных платформ содержат определения пользовательского интерфейса. Так выглядит приложение, которое мы создадим для (слева направо) телефонов iOS и Android и для Windows 10 Desktop.
  
[![Приложение Xamarin для iOS, Android и Windows](../cross-platform/media/cross-plat-xamarin-build-1.png "Cross-Plat Xamarin Build 1")](../cross-platform/media/cross-plat-xamarin-build-1-Large.png#lightbox)
  
Вам предстоит выполнить следующие действия.  
  
- [Настройка решения](#solution)  
  
- [Создание общего кода для службы данных](#dataservice)  
  
- [Разработка пользовательского интерфейса для приложения Android](#Android)  

- [Разработка пользовательского интерфейса для Windows](#Windows)  
  
- [Дальнейшие действия](#next), включающие проектирование пользовательского интерфейса для iOS
  
> [!TIP]
> Полный исходный код этого проекта можно найти в [репозитории mobile-samples в GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).
>
> При возникновении проблем или ошибок разместите свой вопрос на сайте [forums.xamarin.com](http://forums.xamarin.com). Для исправления многих ошибок можно обновить пакеты SDK Xamarin до последней версии. Эти пакеты описаны в разделе [Заметки о выпуске Xamarin](https://developer.xamarin.com/releases/) для каждой платформы.    
  
> [!NOTE]
> Документация для разработчиков Xamarin также предлагает несколько пошаговых руководств с разделами "Краткое руководство" и "Подробное рассмотрение", приведенными ниже. На этих страницах убедитесь, что выбран пункт Visual Studio, чтобы отображались пошаговые руководства именно для Visual Studio.  
>   
>  -   Приложения Xamarin с нативным пользовательским интерфейсом:  
>     -   [Привет, Android](/xamarin/android/get-started/hello-android/) (простое приложение с одним экраном)  
>     -   [Привет, Android (несколько экранов)](/xamarin/android/get-started/hello-android-multiscreen/) (приложение с переходами между экранами)  
>     -   [Пошаговое руководство по фрагментам в Android](/xamarin/android/platform/fragments/fragments/implementing-with-fragments/walkthrough/) (помимо прочего, используется для иерархических экранов)  
>     -   [Привет, iOS](/xamarin/ios/get-started/hello-iOS/)  
>     -   [Привет, iOS (несколько экранов)](/xamarin/ios/get-started/hello-iOS-multiscreen/) 

>  -   Приложения Xamarin с Xamarin.Forms (общий пользовательский интерфейс)  
>     -   [Привет, Xamarin.Forms](/xamarin/xamarin-forms/get-started/hello-xamarin-forms/quickstart/)  
>     -   [Привет, Xamarin.Forms (несколько экранов)](/xamarin/xamarin-forms/get-started/hello-xamarin-forms-multiscreen/)  
  
<a name="solution" />

##  <a name="set-up-your-solution"></a>Настройка решения  

В Visual Studio отсутствует шаблон решения для создания приложений с собственными пользовательскими интерфейсами, которые совместно используют библиотеку .NET Standard. Однако создание такого решения из отдельных проектов не является сложной задачей. Ниже приведена пошаговая инструкция по созданию решения Xamarin с проектами для каждой платформы.приложения и с библиотекой .NET Standard для общего кода.  
  
1.  В Visual Studio создайте решение **Библиотека классов (.NET Standard)** и назовите его **WeatherApp**. Проще всего найти этот шаблон, выбрав слева **Visual C#** и затем выбрав **.NET Standard**: 

    ![Создание решения .NET Standard](../cross-platform/media/cross-plat-xamarin-build-2.png "Cross-platform Xamarin Build 2")

    После нажатия кнопки "ОК" будет создано решение **WeatherApp**, состоящее из одного проекта с именем **WeatherApp**. 

2.  Если среди целевых платформ есть iOS, добавьте проект iOS в решение. Щелкните правой кнопкой мыши решение в **обозревателе решений** и выберите **Добавить**, затем **Новый проект**.  В диалоговом окне **Новый проект** слева выберите **Visual C#**, затем **iOS** и **Универсальное**. (Если этот пункт отсутствует, то необходимо установить Xamarin или включить компонент Visual Studio 2017, см. раздел [Установка и настройка](../cross-platform/setup-and-install.md).) В списке шаблонов выберите элемент **Приложение с одним представлением (iOS)**. Назовите его **WeatherApp.iOS**.

3.  Если среди целевых платформ есть Android, добавьте проект Android в решение. В диалоговом окне **Новый проект** слева выберите **Visual C#**, затем **Android**. В списке шаблонов выберите **Пустое приложение (Android)**. Назовите его **WeatherApp.Android**. 

4. Если среди целевых платформ есть универсальная платформа Windows, то в диалоговом окне **Новый проект** слева выберите **Visual C#**, затем **Универсальное приложение для Windows**. В списке шаблонов выберите **Пустое приложение (универсальная платформа Windows)** и назовите его **WeatherApp.UWP**.
  
5. Для каждого проекта приложения (iOS, Android и UWP) щелкните правой кнопкой мыши раздел **Ссылки** в **обозревателе решений** и выберите **Добавить ссылку**. В диалоговом окне **Диспетчер ссылок** выберите слева **Проект** и **Решения**. Отобразится список всех проектов в решении, кроме проекта, ссылками которого вы управляете:

   ![Установка ссылки на проект .NET Standard](../cross-platform/media/cross-plat-xamarin-build-3.png "Cross-platform Xamarin Build 3")

   Установите флажок рядом с **WeatherApp**. 

   После того как вы установили флажок для всех проектов приложений, они будут содержать ссылку на библиотеку .NET Standard и могут совместно использовать код из этой библиотеки.
  
6. Добавьте в проект .NET Standard пакет NuGet **Newtonsoft.Json**, который пригодится для обработки информации, полученной от метеослужбы:  
  
    -   Щелкните правой кнопкой на проекте **WeatherApp** в **обозревателе решений** и выберите **Управление пакетами NuGet...**.  
  
         В окне NuGet перейдите на вкладку **Обзор** и наберите **Newtonsoft** в строке поиска.  
  
    -   Выберите **Newtonsoft.Json**.  
  
    -   Убедитесь, что в поле **Версия** указана **последняя стабильная** версия.  
  
    -   Нажмите кнопку **Установить**.  
  
7.  Повторите шаг 6, чтобы найти и установить пакет **Microsoft.CSharp** в проекте .NET Standard. Эта библиотека необходима для использования типа данных C# `dynamic` в библиотеке .NET Standard.
  
8.  Соберите свое решение и убедитесь в отсутствии ошибок сборки.  
  
<a name="dataservice" />

## <a name="write-shared-data-service-code"></a>Создание общего кода для службы данных  

 Проект **WeatherApp** является библиотекой .NET Standard. Это проект, где вы будете писать общий для всех платформ код. Поскольку каждый проект приложения содержит ссылку на библиотеку .NET Standard, то эта библиотека входит в состав пакетов приложений iOS, Android и UWP.  
  
 Следующие действия добавляют в библиотеку .NET Standard код, который получает и сохраняет данные от метеослужбы:  
  
1.  Сначала зарегистрируйтесь на сайте службы погоды для получения бесплатного ключа API на странице [http://openweathermap.org/appid](http://openweathermap.org/appid). Ключ API позволяет приложению получать прогноз погоды по почтовому индексу США. (Сервис не работает для почтовых индексов за пределами США.)
  
2.  Щелкните проект **WeatherApp** правой кнопкой мыши и выберите пункт **Добавить > Класс…** В диалоговом окне **Добавление нового элемента** дайте файлу имя **Weather.cs**. Этот класс будет использован для хранения данных службы погоды.  
  
3.  Замените все содержимое файла **Weather.cs** следующим кодом:  
  
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
  
4.  Добавьте еще один класс в проект .NET Standard с именем **DataService.cs**. Этот класс будет использован для обработки данных JSON, полученных из службы погоды.  
  
5.  Замените все содержимое файла **DataService.cs** следующим кодом:  
  
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
  
6.  Добавьте в библиотеку .NET Standard третий класс с именем **Core.cs**. Этот класс будет использован для формирования строки запроса с указанием почтового индекса, направления этого запроса в метеослужбу и заполнения экземпляра класса **Weather**.  
  
7.  Замените содержимое файла **Core.cs** следующим кодом:  
  
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

                //Make sure developers running this sample replaced the API key
                if (key == "YOUR API KEY HERE")
                {
                    throw new ArgumentException("You must obtain an API key from openweathermap.org/appid and save it in the 'key' variable.");
                }
  
                dynamic results = await DataService.GetDataFromService(queryString).ConfigureAwait(false);  
  
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
  
8. Замените первое вхождение строки *YOUR API KEY HERE* ключом API, полученным на шаге 1. Ключ должен быть заключен в кавычки.
  
9. Удалите файл **MyClass.cs** из библиотеки .NET Standard, так как он не потребуется.  
  
10. Выполните сборку проекта **WeatherApp**, чтобы убедиться в правильности кода.  
  
<a name="Android" />

## <a name="design-ui-for-android"></a>Разработка пользовательского интерфейса для приложения Android  

 Теперь мы разработаем пользовательский интерфейс, подключим его к общему коду и запустим приложение.  
  
### <a name="design-the-look-and-feel-of-your-app"></a>Разработка интерфейса приложения  
  
1.  В **обозревателе решений** разверните узел **WeatherApp.Droid > Ресурсы > макет** и откройте файл **Main.axml**. Эта команда откроет файл в визуальном конструкторе. (При появлении ошибки, связанной с Java, см. следующую [запись в блоге](http://forums.xamarin.com/discussion/32365/connection-to-the-layout-renderer-failed-in-xs-5-7-and-xamarinvs-3-9).)  
  
    > [!TIP]
    >  В этом проекте есть много других файлов. Их изучение выходит за рамки этой статьи, но, если вы хотите подробно рассмотреть структуру проекта Android, обратитесь к разделу [Часть 2. Подробное описание структуры](/xamarin/android/get-started/hello-android/hello-android-deepdive/) статьи "Привет, Android".  
  
2.  Откройте панель элементов, выбрав пункт меню **Просмотр > Другие окна > Панель элементов**.  
  
3.  Перетащите элемент управления **RelativeLayout**с **панели элементов** в конструктор. Этот элемент управления можно использовать в качестве родительского контейнера для других элементов управления.  
  
    > [!TIP]
    >  Если макет отображается неправильно, сохраните файл и переключитесь между вкладками **Структура** и **Исходный код**, чтобы обновить макет.  
  
4.  В окне **Свойства** установите свойство **background** (в группе "Стиль") в значение `#545454`.  С помощью заголовка окна **Свойства** убедитесь, что вы изменяете фон элемента **RelativeLayout**.
  
5.  Перетащите элемент управления **TextView**с **панели элементов** в элемент управления **RelativeLayout** .  
  
6.  В окне **Свойства** задайте следующие свойства. (Примечание: для удобства можно отсортировать список в алфавитном порядке с помощью сортировки кнопки на панели инструментов окна "Свойства"):  
  
    |Свойство.|Значение|  
    |--------------|-----------|  
    |**text**|**Search by Zip Code**|  
    |**id**|`@+id/ZipCodeSearchLabel`|  
    |**layout_marginStart**|`10dp`|  
    |**textColor**|`@android:color/white`|  
    |**textStyle**|`bold`|  
  
    > [!TIP]
    >  Обратите внимание, что многие свойства не содержат раскрывающегося списка значений, доступных для выбора.  Прогнозирование значения, которое следует использовать для какого-либо свойства, может оказаться сложным. Чтобы просмотреть предложения, попробуйте ввести имя свойства на странице класса [R.attr](http://developer.android.com/reference/android/R.attr.html) .  
    >   
    >  Также быстрый поиск в Интернете позволит найти на сайте [http://stackoverflow.com/](http://stackoverflow.com/) страницу, на которой другие пользователи использовали то же свойство.  
  
     Для справки можно переключиться в представление **Исходный код**, и вы должны увидеть следующий код для этого элемента:  
  
    ```xml  
    <TextView  
        android:text="Search by Zip Code"  
        android:layout_width="wrap_content"  
        android:layout_height="wrap_content"  
        android:id="@+id/ZipCodeSearchLabel"  
        android:layout_marginStart="10dp"  
        android:textColor="@android:color/white"  
        android:textStyle="bold" />  
  
    ```  
  
7.  Перетащите элемент управления **TextView** c **панели элементов** на элемент управления **RelativeLayout** и разместите его под элементом управления ZipCodeSearchLabel. Установите новый элемент управления к соответствующей границе существующего элемента управления. Это позволит немного увеличить конструктор для размещения элемента управления.  
  
8. В окне **Свойства** задайте следующие свойства.  
  
    |Свойство|Значение|  
    |--------------|-----------|  
    |**текст**|**Почтовый индекс**|  
    |**id**|`@+id/ZipCodeLabel`|  
    |**layout_marginStart**|`10dp`|  
    |**layout_marginTop**|`6dp`|  
    |**textColor**|`@android:color/white`|  
  
    Код в представлении **Исходный код** должен выглядеть следующим образом:  
  
    ```xml  
    <TextView  
        android:text="Zip Code"  
        android:layout_width="wrap_content"  
        android:layout_height="wrap_content"  
        android:layout_below="@id/ZipCodeSearchLabel"  
        android:id="@+id/ZipCodeLabel"  
        android:layout_marginStart="10dp"
        android:layout_marginTop="6dp"  
        android:textColor="@android:color/white" />  
    ```  
  
9. Перетащите элемент управления **Number** c **панели элементов** на элемент управления **RelativeLayout** и разместите его под меткой **Zip Code**. Затем установите следующие свойства:  
  
    |Свойство.|Значение|  
    |--------------|-----------|  
    |**id**|`@+id/zipCodeEntry`|  
    |**layout_marginStart**|`10dp`|  
    |**layout_marginBottom**|`10dp`|  
    |**width**|`165dp`|  
    |**textColor**|`@android:color/white`|  
  
    **Номер** — это элемент управления, в котором пользователь будет вводить почтовый индекс США из пяти цифр. Ниже представлена разметка, которая соответствует этому элементу управления:  
  
    ```xml  
    <EditText  
        android:inputType="number"  
        android:layout_width="wrap_content"  
        android:layout_height="wrap_content"  
        android:layout_below="@id/ZipCodeLabel"  
        android:id="@+id/zipCodeEntry"  
        android:layout_marginStart="10dp"  
        android:layout_marginBottom="10dp"  
        android:width="165dp"  
        android:textColor="@android:color/white" />  
    ```  
  
10. Перетащите элемент управления **Button** c **панели элементов** на элемент управления **RelativeLayout** и разместите его справа от элемента управления zipCodeEntry. Затем установите следующие свойства:  
  
    |Свойство.|Значение|  
    |--------------|-----------|  
    |**id**|`@+id/weatherBtn`|  
    |**текст**|**Get Weather**|  
    |**layout_marginStart**|`20dp`|  
    |**layout_alignBottom**|`@id/zipCodeEntry`|  
    |**width**|`165dp`|  
  
    ```xml  
    <Button
        android:text="Get Weather"  
        android:layout_width="wrap_content"  
        android:layout_height="wrap_content"  
        android:layout_toRightOf="@id/zipCodeEntry"  
        android:id="@+id/weatherBtn"  
        android:layout_marginStart="20dp"  
        android:layout_alignBottom="@id/zipCodeEntry"  
        android:width="165dp" />  
    ```  
  
11. Теперь вы знаете достаточно, чтобы создать базовый пользовательский интерфейс с помощью конструктора Android. Для создания пользовательского интерфейса также можно добавить разметку непосредственно в файл страницы Main.axml. Чтобы построить таким же образом остальную часть пользовательского интерфейса, переключитесь в конструкторе в режим просмотра исходного кода и вставьте следующую разметку *под* закрывающим тегом `</RelativeLayout>`. (Элементы должны располагаться под тегом, так как они *не* содержатся в `RelativeLayout`.)  
  
    ```xml  
    <TextView  
        android:text="Location"  
        android:textAppearance="?android:attr/textAppearanceSmall"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/locationLabel"  
        android:layout_marginStart="10dp"  
        android:layout_marginTop="10dp" />  
    <TextView  
        android:textAppearance="?android:attr/textAppearanceMedium"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/locationText"  
        android:layout_marginStart="20dp"  
        android:layout_marginBottom="10dp" />  
    <TextView  
        android:text="Temperature"  
        android:textAppearance="?android:attr/textAppearanceSmall"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/tempLabel"  
        android:layout_marginStart="10dp" />  
    <TextView  
        android:textAppearance="?android:attr/textAppearanceMedium"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/tempText"  
        android:layout_marginBottom="10dp"  
        android:layout_marginStart="20dp" />  
    <TextView  
        android:text="Wind Speed"  
        android:textAppearance="?android:attr/textAppearanceSmall"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/windLabel"  
        android:layout_marginStart="10dp" />  
    <TextView  
        android:textAppearance="?android:attr/textAppearanceMedium"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/windText"  
        android:layout_marginBottom="10dp"  
        android:layout_marginStart="20dp" />  
    <TextView  
        android:text="Humidity"  
        android:textAppearance="?android:attr/textAppearanceSmall"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/humidtyLabel"  
        android:layout_marginStart="10dp" />  
    <TextView  
        android:textAppearance="?android:attr/textAppearanceMedium"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/humidityText"  
        android:layout_marginBottom="10dp"  
        android:layout_marginStart="20dp" />  
    <TextView  
        android:text="Visibility"  
        android:textAppearance="?android:attr/textAppearanceSmall"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/visibilityLabel"  
        android:layout_marginStart="10dp" />  
    <TextView  
        android:textAppearance="?android:attr/textAppearanceMedium"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/visibilityText"  
        android:layout_marginBottom="10dp"  
        android:layout_marginStart="20dp" />  
    <TextView  
        android:text="Time of Sunrise"  
        android:textAppearance="?android:attr/textAppearanceSmall"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/sunriseLabel"  
        android:layout_marginStart="10dp" />  
    <TextView  
        android:textAppearance="?android:attr/textAppearanceMedium"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/sunriseText"  
        android:layout_marginBottom="10dp"  
        android:layout_marginStart="20dp" />  
    <TextView  
        android:text="Time of Sunset"  
        android:textAppearance="?android:attr/textAppearanceSmall"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/sunsetLabel"  
        android:layout_marginStart="10dp" />  
    <TextView  
        android:textAppearance="?android:attr/textAppearanceMedium"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/sunsetText"  
        android:layout_marginBottom="10dp"  
        android:layout_marginStart="20dp" />  
    ```  
  
12. Сохраните файл и переключитесь в представление **Макет**. Пользовательский интерфейс будет выглядеть следующим образом:  
  
     ![Пользовательский интерфейс для приложения Android](../cross-platform/media/xamarin_androidui.png "Xamarin_AndroidUI")  
  
13. Откройте файл **MainActivity.cs**. Код должен выглядеть следующим образом:  
  
    ```  
    protected override void OnCreate (Bundle bundle)  
    {  
        base.OnCreate (bundle);  
  
        // Set our view from the "main" layout resource  
        SetContentView (Resource.Layout.Main);  
    }  
    ```  
  
14. Чтобы проверить свою работу, создайте проект Android. В процессе сборки идентификаторы элемента управления будут добавлены в файл **Resource.Designer.cs**, чтобы можно было ссылаться на них по имени в коде.  
  
### <a name="consume-your-shared-code"></a>Использование общего кода  
  
1.  Откройте файл **MainActivity.cs** проекта **WeatherApp** в редакторе кода и замените его содержимое следующим кодом. Этот код вызывает метод `GetWeather` , определенный в общем коде. Затем он отобразит в пользовательском интерфейсе приложения данные, полученные из этого метода.  
  
    ```csharp  
    using System;  
    using Android.App;  
    using Android.Widget;  
    using Android.OS;  
  
    namespace WeatherApp.Droid  
    {  
        [Activity(Label = "Sample Weather App", 
                  Theme = "@android:style/Theme.Material.Light", 
                  MainLauncher = true)]  
        public class MainActivity : Activity  
        {  
            protected override void OnCreate(Bundle bundle)  
            {  
                base.OnCreate(bundle);  
  
                SetContentView(Resource.Layout.Main);  
  
                Button button = FindViewById<Button>(Resource.Id.weatherBtn);  
  
                button.Click += Button_Click;  
            }  
  
            private async void Button_Click(object sender, EventArgs e)  
            {  
                EditText zipCodeEntry = FindViewById<EditText>(Resource.Id.zipCodeEntry);  
  
                if (!String.IsNullOrEmpty(zipCodeEntry.Text))  
                {  
                    Weather weather = await Core.GetWeather(zipCodeEntry.Text);  
                    FindViewById<TextView>(Resource.Id.locationText).Text = weather.Title;  
                    FindViewById<TextView>(Resource.Id.tempText).Text = weather.Temperature;  
                    FindViewById<TextView>(Resource.Id.windText).Text = weather.Wind;  
                    FindViewById<TextView>(Resource.Id.visibilityText).Text = weather.Visibility;  
                    FindViewById<TextView>(Resource.Id.humidityText).Text = weather.Humidity;  
                    FindViewById<TextView>(Resource.Id.sunriseText).Text = weather.Sunrise;  
                    FindViewById<TextView>(Resource.Id.sunsetText).Text = weather.Sunset;  
                }  
            }  
        }  
    }  
    ```  

    Обратите внимание, что действию была назначена тема со светлым фоном.
  
### <a name="run-the-app-and-see-how-it-looks"></a>Запуск и просмотр приложения  
  
1.  В **обозревателе решений** установите проект **WeatherApp.Droid** в качестве проекта, загружаемого при запуске.  
  
2.  Выберите подходящее устройство или эмулятор, а затем запустите приложение, нажав клавишу F5.  

    > [!NOTE]
    > Если Visual Studio показывает, что проект Android не может найти файл Newtonsoft.Json, добавьте этот пакет NuGet для проекта Android. 
  
3.  На устройстве или в эмуляторе введите действительный почтовый индекс США из пяти цифр в поле ввода и нажмите кнопку **Узнать погоду**. В элементах управления появятся данные о погоде в этом регионе.  
  
    [![Приложение Xamarin для Android](../cross-platform/media/cross-plat-xamarin-build-1-android.png "Cross-Plat Xamarin Build 1 Android")](../cross-platform/media/cross-plat-xamarin-build-1-android-Large.png#lightbox)  
  
> [!TIP]
>  Полный исходный код этого проекта можно найти в [репозитории mobile-samples в GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).  
  
<a name="Windows" /> 

## <a name="design-ui-for-windows"></a>Разработка пользовательского интерфейса для Windows

На следующем шаге мы разработаем пользовательский интерфейс для Windows, подключим его к общему коду, а затем запустим приложение.  
  
### <a name="design-the-look-and-feel-of-your-app"></a>Разработка интерфейса приложения  

 Процесс создания собственного пользовательского интерфейса для UWP в приложении Xamarin ничем не отличается от процесса создания интерфейса для других собственных приложений UWP. По этой причине использование конструктора в данной статье не обсуждается. Для получения подробных сведений обратитесь к разделу [Создание пользовательского интерфейса с помощью конструктора XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).  
  
 Либо откройте файл **MainPage.xaml** и замените все содержимое XAML следующей разметкой:   
  
```xaml  
<Page
    x:Class="WeatherApp.UWP.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:WeatherApp.UWP"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d">

    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">

        <StackPanel HorizontalAlignment="Left" 
                    VerticalAlignment="Top" 
                    Height="40" Margin="10,0,0,0" Width="400">
            <TextBlock Text="Weather App" FontSize="30" />
        </StackPanel>
        <StackPanel HorizontalAlignment="Left" 
                    VerticalAlignment="Top" 
                    Height="120" Margin="10,40,0,0" Width="400" 
                    Background="#FF545454">

            <TextBlock Text="Search by Zip Code" TextWrapping="Wrap" 
                       HorizontalAlignment="Left" Margin="10,10,0,0"
                       Foreground="White" FontSize="18" FontWeight="Bold" />
            
            <TextBlock Text="Zip Code" TextWrapping="Wrap" 
                       Margin="10,5,0,0" FontSize="14" Foreground="#FFA8A8A8"/>
            
            <StackPanel Orientation="Horizontal">

                <TextBox x:Name="zipCodeEntry" Text="" 
                         Margin="10,10,0,0" VerticalAlignment="Top" 
                         InputScope="Number" Width="165" />
                
                <Button x:Name="weatherBtn" Content="Get Weather" 
                        Foreground="White" Width="165" Margin="20,0,0,0" Height="60" 
                        Click="GetWeatherButton_Click"/>
            </StackPanel>
        </StackPanel>
        
        <StackPanel Margin="10,175,0,0">
            <StackPanel.Resources>
                <Style x:Key="commonText" TargetType="TextBlock">
                    <Setter Property="HorizontalAlignment" Value="Left" />
                    <Setter Property="VerticalAlignment" Value="Top" />
                    <Setter Property="TextWrapping" Value="Wrap" />
                </Style>
                
                <Style x:Key="labelText" TargetType="TextBlock" BasedOn="{StaticResource commonText}">
                    <Setter Property="FontSize" Value="14" />
                    <Setter Property="Foreground" Value="#FFA8A8A8" />
                </Style>

                <Style x:Key="valueText" TargetType="TextBlock" BasedOn="{StaticResource commonText}">
                    <Setter Property="FontSize" Value="18" />
                    <Setter Property="Margin" Value="10, 0, 0, 10" />
                </Style>
            </StackPanel.Resources>
            
            <TextBlock Text="Location" Style="{StaticResource labelText}" />
            <TextBlock x:Name="locationText" Style="{StaticResource valueText}" />

            <TextBlock Text="Temperature" Style="{StaticResource labelText}" />
            <TextBlock x:Name="tempText" Style="{StaticResource valueText}" />
            
            <TextBlock Text="Wind Speed" Style="{StaticResource labelText}" />
            <TextBlock x:Name="windText" Style="{StaticResource valueText}" />
            
            <TextBlock Text="Humidity" Style="{StaticResource labelText}" />
            <TextBlock x:Name="humidityText" Style="{StaticResource valueText}" />
            
            <TextBlock Text="Temperature" Style="{StaticResource labelText}" />
            <TextBlock x:Name="visibilityText" Style="{StaticResource valueText}" />
            
            <TextBlock Text="Time of Sunrise" Style="{StaticResource labelText}" />
            <TextBlock x:Name="sunriseText" Style="{StaticResource valueText}" />
            
            <TextBlock Text="Time of Sunset" Style="{StaticResource labelText}" />
            <TextBlock x:Name="sunsetText" Style="{StaticResource valueText}" />
        </StackPanel>
    </Grid>
</Page>
```  
  
### <a name="consume-your-shared-code"></a>Использование общего кода  
  
В файле кода программной части **MainPage.xaml.cs** добавьте следующий обработчик события для кнопки: 
  
```csharp  
private async void GetWeatherButton_Click(object sender, RoutedEventArgs e)  
{  
    if (!String.IsNullOrEmpty(zipCodeEntry.Text))  
    {  
        Weather weather = await Core.GetWeather(zipCodeEntry.Text);  
        locationText.Text = weather.Title;  
        tempText.Text = weather.Temperature;  
        windText.Text = weather.Wind;  
        visibilityText.Text = weather.Visibility;  
        humidityText.Text = weather.Humidity;  
        sunriseText.Text = weather.Sunrise;  
        sunsetText.Text = weather.Sunset;  

        weatherBtn.Content = "Search Again";  
    }  
}  
```  
  
Этот код вызывает метод `GetWeather` , определенный в общем коде. `GetWeather` — это тот же метод, который вызывался в приложении Android. Данный код также отображает данные, полученные из этого метода в элементах управления пользовательского интерфейса приложения.  
  
### <a name="run-the-app-and-see-how-it-looks"></a>Запуск и просмотр приложения  
  
1.  В **обозревателе решений** установите проект**WeatherApp.UWP** как автозагружаемый проект.  

2.  В раскрывающемся списке **Платформы решения** выберите **x86**, а затем выберите **Локальный компьютер** для развертывания приложения на Windows 10 Desktop.
  
3.  Запустите приложение, нажав клавишу F5.  
  
4.  Введите действительный почтовый индекс США из пяти цифр в поле ввода и нажмите кнопку **Узнать погоду**. На странице появятся данные о погоде в этом регионе.  

    [![Приложение Xamarin на UWP](../cross-platform/media/cross-plat-xamarin-build-1-uwp.png "Cross-Plat Xamarin Build 1 UWP")](../cross-platform/media/cross-plat-xamarin-build-1-uwp-Large.png#lightbox)  

> [!TIP]
>  Полный исходный код этого проекта можно найти в [репозитории mobile-samples в GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).  

<a name="next" /> 

## <a name="next-steps"></a>Следующие шаги  

 **Добавление пользовательского интерфейса для iOS в решение**  
  
 Расширьте этот пример, добавив собственный пользовательский интерфейс для iOS. Для тестирования кода на iOS необходимо подключиться к компьютеру Mac в локальной сети, на котором установлены Xcode и Xamarin. После этого можно использовать конструктор iOS непосредственно в Visual Studio. Законченное приложение можно найти [в репозитории mobile-samples в GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).  
  
 Также обратитесь к пошаговому руководству [Привет, iOS](/xamarin/ios/get-started/hello-ios/hello-ios-quickstart?tabs=vswin).   
  
 **Добавление кода конкретной платформы в общий проект**  
  
 Общий код в библиотеке .NET Standard является платформонезависимым. Библиотека компилируется один раз и включается во все пакеты приложений для конкретных платформ. Если вы хотите писать общий код, который использует условную компиляцию для изоляции кода для конкретных платформ, можете воспользоваться *общим* проектом. Дополнительные сведения см. в разделе [Варианты общего доступа к коду](/xamarin/cross-platform/app-fundamentals/building-cross-platform-applications/practical-code-sharing-strategies).  
  
## <a name="see-also"></a>См. также  

 [Документация по Xamarin](http://docs.microsoft.com/xamarin)   
 [Центр разработки для Windows](https://dev.windows.com/en-us)   
 [Краткий справочник по Swift и C# в виде таблицы](http://aka.ms/scposter)
