---
title: Разработка кроссплатформенных мобильных приложений
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 8202717a-e990-45cf-b092-438651ccb38a
caps.latest.revision: 66
ms.author: crdun
manager: crdun
ms.openlocfilehash: 1efc8ea7f40c3098e681cc80ac90789b629630a9
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301389"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Кроссплатформенная разработка для мобильных устройств в Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Используя Visual Studio, можно создавать приложения для устройств Android, iOS и Windows.  При разработке приложения вы можете использовать инструменты Visual Studio для добавления подключенных служб, таких как Office 365, служба приложений Azure и Application Insights.

 Поддерживается создание приложений с помощью C# и .NET Framework, HTML и JavaScript или C++. Существует возможность совместного использования кода, строк, изображений, а в некоторых случаях даже пользовательского интерфейса.

 Для создания игр или мощных графических приложений установите инструменты Visual Studio для Unity. Это позволит максимально эффективно использовать функции Visual Studio и Unity — популярного движка и среды разработки для игр и мощных графических приложений в Windows, iOS, Android и на других платформах.

 **В этой статье:**

- [Создайте приложение для Android, iOS и Windows (.NET Framework)](#NET)

  - [Целевая Платформа, iOS и Windows из единой базы кода](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#AndroidHTML)

  - [Целевые устройства Windows 10](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#WindowsHTML)

- [Сборка приложения для устройств Android, iOS и Windows (HTML/JavaScript)](#HTML)

- [Создание приложений для устройств Android и Windows (C++)](#CPP)

- [Создание кросс-платформенной игры для устройств Android, iOS и Windows с использованием инструментов Visual Studio для Unity](#Unity)

## <a name="build-an-app-for-android-ios-and-windows-net-framework"></a><a name="NET"></a> Сборка приложения для устройств Android, iOS и Windows (.NET Framework)
 ![Устройства](../cross-platform/media/homedevices.png "HomeDevices")

 С помощью Xamarin вы можете указать Android, iOS и Windows в качестве целевых устройств в одном и том же решении, при этом код и даже графический интерфейс будут использоваться совместно.

|**Дополнительные сведения**|
|--------------------|
|[Установка Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Сведения о Xamarin в Visual Studio](https://visualstudio.microsoft.com/xamarin/) (VisualStudio.com)|
|[Visual Studio и Xamarin](../cross-platform/visual-studio-and-xamarin.md) (Библиотека MSDN)|
|[Управление жизненным циклом приложений (ALM) c приложениями Xamarin](../cross-platform/application-lifecycle-management-alm-with-xamarin-apps.md) (Библиотека MSDN)|
|[Дополнительные сведения об универсальных приложениях Windows в Visual Studio](https://www.visualstudio.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[Сведения о сходстве между Swift и C#](https://aka.ms/scposter) (download.microsoft.com)|
|[Сведения об эмуляторе Visual Studio для Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|

### <a name="target-android-ios-and-windows-from-a-single-code-base"></a><a name="AndroidHTML"></a> Целевые устройства Android, iOS и Windows из единой базы кода
 Вы можете создавать собственные приложения для Android, iOS и Windows с помощью C# и F# (Visual Basic сейчас не поддерживается).  Чтобы начать работу, установите Visual Studio 2015, выбрав вариант **Пользовательские параметры** в установщике и установив флажок **Кроссплатформенная разработка для мобильных устройств > C#/.NET (Xamarin)**. Вы также можете начать работу с [установщика Xamarin](https://www.xamarin.com/download), который необходим, чтобы установить Xamarin для Visual Studio 2013.

 Если у вас уже установлен Visual Studio 2015, запустите программу установки из меню **Панель управления > Программы и компоненты**, выбрав тот же вариант **Пользовательские параметры**, который использовался выше для установки Xamarin.

 Когда вы закончите, шаблоны проекта отображаются в диалоговом окне **нового проекта.** Чтобы найти шаблоны Xamarin, проще всего ввести "Xamarin" в строке поиска.

 Xamarin предоставляет собственные функции Android, iOS и Windows в виде объектов .NET. Поэтому ваши приложения будут иметь полный доступ к собственным API-интерфейсам и собственным элементам управления и будут вести себя точно так же, как приложения, написанные на собственных языках платформ.

 После создания проекта вы сможете использовать все функции повышения продуктивности в составе Visual Studio. Например, вы сможете создавать страницы с помощью конструктора и изучить собственные API-интерфейсы мобильных платформ с помощью IntelliSense. Запустить готовое приложение и оценить его интерфейс можно в эмуляторе Visual Studio для Android, в эмуляторе пакета SDK для Android, а также запустив собственные приложения Windows в Windows или в эмуляторе Windows Phone. Вы также можете использовать связанные устройства Android и Windows напрямую. Для проектов iOS необходимо подключиться к компьютеру Mac, подключенному к сети, и запустить эмулятор Mac из Visual Studio или подключиться к связанному устройству.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Создание одного набора страниц, отображаемого на всех устройствах, с помощью Xamarin.Forms
 В зависимости от сложности конструкции приложения, возможно, имеет смысл использовать для его создания шаблоны *Xamarin.Forms* в группе шаблонов проектов **Мобильные приложения** . Xamarin.Forms — это набор средств разработки пользовательского интерфейса, с помощью которого можно создать единый интерфейс приложения для совместного использования на устройствах Android, iOS и Windows.  При компиляции решения Xamarin.Forms вы получаете приложение для Android, приложение для iOS и приложение для Windows. Дополнительные сведения см. в разделе [Дополнительные сведения о разработке мобильных приложений с помощью Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).

#### <a name="share-code-between-android-ios-and-windows-apps"></a><a name="ShareHTML"></a> Совместное использование кода приложениями Android, iOS и Windows
 Если вы не используете Xamarin.Forms и предпочитаете разрабатывать приложения для каждой платформы отдельно, вы можете совместно использовать большую часть кода, не относящегося к пользовательскому интерфейсу, в проектах для разных платформ (Android, iOS и Windows). К нему относятся любая бизнес-логика, интеграция в облаке, доступ к базе данных или любой другой код, предназначенный для платформы .NET Framework. Единственным кодом, который нельзя совместно использовать, является код, предназначенный для конкретной платформы.

 ![Совместное использование кода для пользовательского интерфейса Windows, iOS и Android](../cross-platform/media/sharecode.png "ShareCode")

 Код можно совместно использовать с помощью общего проекта, проекта переносимой библиотеки классов или обоих этих проектов. Может оказаться, что какой-то код больше подходит в общем проекте, а другой код лучше себя ведет в рамках проекта переносимой библиотеки классов.

|**Дополнительные сведения**|
|--------------------|
|Выберите нужный вариант совместного использования кода: на основе общих проектов, проектов переносимой библиотеки классов или обоих этих проектов.<br /><br /> [Совместное использование кода несколькими платформами](https://devblogs.microsoft.com/dotnet/sharing-code-across-platforms/) (блог .NET Framework)<br /><br /> [Варианты совместного использования кода](/xamarin/cross-platform/app-fundamentals/code-sharing) (Xamarin)<br /><br /> [Параметры совместного использования кода с платформой .NET Framework](https://msdn.microsoft.com/library/dn720832.aspx) (библиотека MSDN)|

### <a name="target-windows-10-devices"></a><a name="WindowsHTML"></a>Целевые устройства Windows 10
 ![Устройства для Windows](../cross-platform/media/windowsdevices.png "Устройства Windows")

 Если вы хотите создать одно приложение, предназначенное для полного спектра устройств Windows 10, создайте универсальное приложение Windows. Разработка приложения будет осуществляться с помощью одного проекта, а страницы будут отображаться должным образом независимо от того, какое устройство используется для их просмотра.

 Начните с шаблона проекта универсального приложения Windows. Вы можете визуально разрабатывать страницы, а затем открывать их в окне предварительного просмотра, чтобы увидеть, как они будут отображаться для различных типов устройств. Если вас не устраивает, как страница отображается на устройстве, вы можете оптимизировать ее в соответствии с размером экрана, разрешением или ориентацией (горизонтальной или вертикальной). Все это можно сделать с помощью удобных инструментальных окон и пунктов меню в Visual Studio. Когда вы будете готовы к запуску приложения и прохождению кода, вы найдете все эмуляторы и симуляторы устройств для различных типов устройств вместе в одном списке, который находится на панели инструментов **Standard.**

 ОС Windows 10 довольно новая, поэтому вы также можете использовать шаблоны проектов, предназначенные для Windows 8.1. Вы можете использовать эти шаблоны проектов для создания приложений, работающих на телефонах, планшетах и ПК Windows 10. Тем не менее все устройства с Windows 8.1 получат автоматическое обновление до Windows 10, таким образом, если у вас нет определенных причин для выбора Windows 8.1 в качестве целевой платформы, рекомендуется использовать шаблоны проектов, предназначенные для Windows 10.

|**Дополнительные сведения**|
|--------------------|
|[Дополнительные сведения об универсальных приложениях Windows](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx) (Центр разработки для Windows)|
|[Создание первого приложения](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx) (Центр разработки для Windows)|
|[Разработка приложений для универсальной платформы Windows (UWP)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|
|[Перенос приложений на универсальную платформу Windows (UWP)](../misc/migrate-apps-to-the-universal-windows-platform-uwp.md)|

## <a name="build-an-app-for-android-ios-and-windows-htmljavascript"></a><a name="HTML"></a>Создайте приложение для Android, iOS и Windows (HTML/JavaScript)
 ![Устройства](../cross-platform/media/homedevices.png "HomeDevices")

 Если вы разработчик веб-решений и знакомы с HTML и JavaScript, то вы можете создавать приложения для целевых платформ Windows, Android и iOS с помощью средств Visual Studio для Apache Cordova. Такие приложения могут быть ориентированы на все три платформы, и при их создании вы можете полагаться на привычные навыки и процедуры.

 Apache Cordova — это платформа, включающая модель подключаемого модуля. Модель подключаемого модуля предоставляет единый API-интерфейс JavaScript, который можно использовать для доступа к собственным возможностям устройств на всех трех платформах (iOS, Android и Windows).

 Поскольку эти API-интерфейсы являются кроссплатформенными, большую часть написанного кода можно совместно использовать для всех трех платформ. Это снижает расходы на разработку и обслуживание. Кроме того, нет необходимости начинать с нуля. При создании других типов веб-приложений можно предоставить эти файлы приложению Cordova без каких-либо изменений и переработки.

 ![Мульти&#45;гибридные устройства](../cross-platform/media/multidevicehybridapps.png "MultiDeviceHybridApps")

 Чтобы приступить к работе, установите Visual Studio 2015 и выберите **HTML/JavaScript (Apache Cordova)** во время установки. Если вы пользуетесь Visual Studio 2013, установите инструменты Visual Studio для расширения Apache Cordova. В любом случае, инструменты Cordova автоматически установят любое стороннее программное обеспечение, необходимое для создания универсального приложения (для нескольких платформ).

 После установки расширения откройте Visual Studio и создайте проект **Blank App (Apache Cordova).** Затем можно разработать приложение с помощью JavaScript или TypeScript. Кроме того, можно добавлять подключаемые модули для расширения функциональности приложения, и API-интерфейсы из подключаемых модулей будут появляться в IntelliSense в ходе написания кода.

 Когда вы будете готовы к запуску приложения и пошаговому выполнению кода, выберите эмулятор, например, эмулятор Apache Ripple или эмулятор Visual Studio (для Android или Windows Phone), браузер или устройство, которое подключено непосредственно к компьютеру. Запустите приложение. Если вы разрабатываете приложение на компьютере Windows, можно запустить его прямо на нем. Все эти возможности встроены в Visual Studio в составе расширения "Инструменты Visual Studio для Apache Cordova".

 Шаблоны проектов для создания универсальных приложений Windows по-прежнему доступны в Visual Studio, и вы можете свободно использовать их, если планируете ориентироваться только на устройства Windows. Если впоследствии вы решите перейти к устройствам Android и iOS, то всегда сможете перенести свой код в проект Cordova. Существуют версии API-интерфейсов WinJS c открытым исходным кодом, поэтому можно повторно использовать любой код, задействующий эти API. С другой стороны, если вы планируете ориентироваться на другие платформы в будущем, рекомендуем начать работу с набором средств Visual Studio для Apache Cordova.

|**Дополнительные сведения**|
|--------------------|
|[Установка Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Начало работы с Инструментами Visual Studio для Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/?view=toolsforcordova-2017) (taco.visualstudio.com)|
|[Сведения об эмуляторе Visual Studio для Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|

## <a name="build-an-app-for-android-and-windows-c"></a><a name="CPP"></a>Создайте приложение для Android и Windows
 ![Используйте C&#43;&#43; чтобы создать приложение для Android, iOS и Windows](../cross-platform/media/cross-plat-cpp-intro-image.png "Cross_Plat_CPP_Intro_Image")

 Сначала установите Visual Studio 2015 и инструменты Visual C++ для разработки кроссплатформенных мобильных приложений. Затем вы сможете создать приложение native-activity для Android или Windows. Шаблоны C++, предназначенные для устройств iOS, сейчас недоступны. Одно и то же решение можно ориентировать на устройства Android и Windows, а затем наладить совместное использование кода между ними с помощью общей кроссплатформенной статической или динамической библиотеки.

 Если вам нужно создать приложение для Android, требующее сложных операций с графикой (например, игру), можно воспользоваться C++. Начните с проекта **Собственное приложение действия (Android)** . В этом проекте реализована полная поддержка цепочки инструментов Clang.

 ![Шаблон проекта Native Activity](../cross-platform/media/cross-plat-cpp-native.png "Кросс-Plat_CPP_Native")

 Для запуска готового приложения и оценки его интерфейса воспользуйтесь эмулятором Visual Studio для Android. Это быстрый, надежный и простой в установке и настройке инструмент.

 Вы можете создавать приложения, ориентированные на весь спектр устройств под управлением Windows 10, с помощью C++ и шаблона проекта универсального приложения Windows. Дополнительные сведения см. в разделе [Целевые устройства Windows 10](#WindowsHTML) ранее в этой статье.

 С помощью статической или динамической общей библиотеки вы сможете совместно использовать код С++ между устройствами Android и Windows.

 ![Статические и динамические общие библиотеки](../cross-platform/media/cross-plat-cpp-libraries.png "Cross_Plat_CPP_Libraries")

 Эту библиотеку можно использовать в проекте Windows или Android, как описано ранее в этом разделе. Также ее можно использовать в приложении, созданном с помощью Xamarin, Java или любого другого языка, который позволяет вызывать функции в неуправляемой библиотеке DLL.

 При написании кода в этих библиотеках можно использовать IntelliSense для просмотра собственных API платформ Android и Windows. Эти проекты библиотеки полностью интегрированы с отладчиком Visual Studio, поэтому можно задавать точки останова, осуществлять пошаговое выполнение кода, находить и исправлять проблемы, используя расширенные возможности этого отладчика.

|**Дополнительные сведения**|
|--------------------|
|[Скачать Visual Studio.](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Установка Visual C++ для средств разработки кроссплатформенных мобильных приложений.](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (библиотека MSDN)|
|[Дополнительные сведения об использовании C++ для нескольких платформ.](https://www.visualstudio.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Установите нужные компоненты, а затем создайте собственное приложение действия для Android](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (библиотека MSDN)|
|[Сведения об эмуляторе Visual Studio для Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|
|[Дополнительные сведения о совместном использовании кода C++ с приложениями Android и Windows](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/) (VisualStudio.com)|
|[Примеры разработки кроссплатформенных мобильных приложений для C++](https://msdn.microsoft.com/library/dn707596.aspx) (Библиотека MSDN)|
|[Дополнительные примеры разработки кроссплатформенных мобильных приложений для C++](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=android&f%5B1%5D.Type=ProgrammingLanguage&f%5B1%5D.Value=C%2B%2B&f%5B1%5D.Text=C%2B%2B) (code.msdn)|

## <a name="build-a-cross-platform-game-for-android-ios-and-windows-by-using-visual-studio-tools-for-unity"></a><a name="Unity"></a>Создайте кросс-платформечную игру для Android, iOS и Windows с помощью инструментов Visual Studio для Unity
 Visual Studio Tools for Unity — это бесплатное расширение для Visual Studio, которое интегрирует мощные инструменты для редактирования кода, производительности и отладки Visual Studio с *Unity,* популярным кросс-платформенным игровым/графическим движком и средой разработки для иммерсивных приложений, ориентированных на Windows, iOS, Android и другие платформы, включая Интернет.

 ![Среда разработки VSTU](../cross-platform/media/vstu-overview.png "VSTU_Overview")

 Средства Visual Studio для Unity (VSTU) позволяют использовать Visual Studio для создания сценариев игр и редакторов на языке C#, а затем использовать его мощный отладчик для поиска и исправления ошибок. В последнем выпуске VSTU реализована поддержка Unity 5, включена цветовая маркировка синтаксиса для языка шейдера ShaderLab системы Unity, усовершенствована синхронизация с Unity, добавлены дополнительные функции отладки и улучшены механизмы создания кода благодаря использованию мастера MonoBehavior. VSTU также объединяет файлы проекта Unity, сообщения консоли и возможность запускать игру в Visual Studio, чтобы тратить меньше времени на переключение в редактор Unity Editor и из него при написании кода.

 Начните создавать игры с использованием Unity и средств Visual Studio Tools для Unity уже сегодня.

|**Дополнительные сведения**|
|--------------------|
|[Дополнительные сведения о построении игр Unity с помощью Visual Studio](https://www.visualstudio.com/features/unitytools-vs.aspx)|
|[Дополнительные сведения о средствах Visual Studio для Unity](../cross-platform/visual-studio-tools-for-unity.md) (библиотека MSDN)|
|[Начните работать со средствами Visual Studio Tools для Unity](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) (библиотека MSDN)|
|[Читать о последних возможностях Visual Studio Tools для предварительной версии Unity 2.0](https://devblogs.microsoft.com/visualstudio/visual-studio-tools-for-unity-2-0-preview/) (блог Visual Studio)|
|[Смотреть видео с введением в Visual Studio Tools для предварительной версии Unity 2.0](https://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408) (видео)|
|[Сведения о Unity](https://unity.com/) (веб-сайт Unity)|

## <a name="see-also"></a>См. также:

- [Добавление API Office 365 в проект Visual Studio](https://msdn.microsoft.com/library/office/dn605899\(v=office.15\).aspx)
- [Мобильные службы Azure](https://msdn.microsoft.com/library/dn720832\(v=vs.110\).aspx)
- [Application Insights](/azure/application-insights/app-insights-overview)
