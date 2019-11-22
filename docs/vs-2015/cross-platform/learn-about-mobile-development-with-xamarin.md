---
title: Подробности о разработке мобильных приложений с использованием Xamarin | Документы Майкрософт
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: e970d936-1df4-4c0c-96e3-ef6191295882
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: 9924eee661f917334aed586506a107486cd5be0f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299775"
---
# <a name="learn-about-mobile-development-with-xamarin"></a>Подробности о разработке мобильных приложений с использованием Xamarin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этой статье представлены материалы общего характера, которые помогут понять основы разработки кроссплатформенных мобильных приложений с помощью Xamarin. Если вы еще не установили Visual Studio и Xamarin, сначала запустите процесс [Настройка и установка](../cross-platform/setup-and-install.md) , затем вернитесь сюда, чтобы изучить представленные ниже материалы во время выполнения программы установки.  
  
> [!NOTE]
> Если не указано иное, рекомендуется сначала прочитать указанные непосредственно здесь страницы и не переходить по ссылкам на их дочерние страницы. Если после освоения этого списка процесс установки по-прежнему выполняется, вы можете вернуться и изучить дополнительные разделы.  
>   
> Также вы можете просмотреть статьи "Основы" и вернуться к статьям "Подробное рассмотрение" позже.  
  
## <a name="essentials-introduction-to-xamarin"></a>Основы: введение в Xamarin  
 *10–20 минут*  
  
1. [Мобильные приложения в Visual Studio с Xamarin](https://www.visualstudio.com/explore/xamarin-vs) (visualstudio.com) предоставляют очень краткое сводное описание основных характеристик Xamarin.  
  
2. [Создание кроссплатформенных мобильных приложений с помощью C# и Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2015-Final-Release-Event/Building-cross-platform-mobile-apps-using-C-and-Visual-Studio-2015) (Channel9, 15 мин. 16 сек.) с пропагандистом Xamarin, Джеймсом Монтеманьо (James Montemagno). Первые три минуты посвящены обзору Xamarin, затем следуют демонстрации кода.  
  
## <a name="essentials-overview-of-the-visual-studio-and-xamarin-environment"></a>Основы: обзор окружений Visual Studio и Xamarin  
 *5–15 минут*  
  
- Основная часть работы выполняется на компьютерах Windows с Visual Studio и Xamarin. На таких компьютерах напрямую создаются приложения для Windows и Android, а также выполняются их запуск и отладка на устройстве или эмуляторе. Вы также можете удаленно создавать, запускать и отлаживать приложения iOS на компьютере Mac. В Visual Studio на компьютере Windows можно также подключиться к конструктору раскадровки iOS и симулятору iOS.  
  
- Компьютер Mac с Xcode и Xamarin служит в качестве окружения сборки, подписывания и среды выполнения для приложений iOS. Сборки для iOS из Visual Studio на компьютере Windows делегируются этому компьютеру Mac; при отладке приложения iOS из Visual Studio оно запускается в симуляторе iOS на компьютере Mac или напрямую на связанном устройстве. В этом случае необходимо взаимодействовать с приложением на компьютере Mac или рядом с ним и выполнять отладку в Visual Studio.  
  
  Эти связи приведены ниже, и подробнее прочитать о работе с приложениями iOS можно в статье [Введение в Xamarin.iOS для Visual Studio](https://docs.microsoft.com/xamarin/ios/get-started/installation/windows/introduction-to-xamarin-ios-for-visual-studio) (xamarin.com).  
  
  ![The relationship between Windows and Mac dev computers in a Xamarin environment](../cross-platform/media/crossplat-xamarin-learn-1.png "CrossPlat Xamarin Learn 1")  
  
## <a name="essentials-how-projects-are-structured"></a>Основы: как структурированы проекты  
 *10–30 минут*  
  
1. [Варианты совместного использования кода](https://docs.microsoft.com/xamarin/cross-platform/app-fundamentals/code-sharing) (xamarin.com). Рекомендуется использовать переносимые библиотеки классов, так как они наилучшим образом обеспечивают использование только тех интерфейсов API .NET, которые поддерживаются всеми целевыми платформами. Большая часть кода бизнес-логики будет находиться в PCL, включая доступ к базам данных, вызовы интерфейсов API REST и вызовы портативных компонентов Xamarin (см. [Deeper Dive: Xamarin Components](#components) в конце статьи). Общий код пользовательского интерфейса, написанный с помощью Xamarin.Forms, может также находиться в PCL.  
  
2. (Необязательно.) В статье [Практический пример: Tasky](https://docs.microsoft.com/xamarin/cross-platform/app-fundamentals/building-cross-platform-applications/case-study-tasky) (xamarin.com) описаны рекомендации по разработке и структурированию полнофункционального приложения, например структурирование проекта с PCL для общего кода, который разделяет данные, доступ к данным и бизнес-уровни.  
  
## <a name="essentials-native-and-xamarinforms-ui-layers"></a>Основы: встроенные слои и слои пользовательского интерфейса Xamarin.Forms  
 *10–40 минут*  
  
 Xamarin предоставляет два способа для создания отличных нативных приложений: Xamarin Native и Xamarin.Forms.  
  
 В Xamarin Native можно написать отдельный код пользовательского интерфейса для каждой целевой платформы: iOS, Android и Windows.  Такой подход дает прямой доступ к интерфейсам API платформы, позволяя настраивать пользовательский интерфейс для каждой платформы.  Также имеется полный доступ к нативному конструктору и элементам управления для каждой платформы, чтобы помочь в создании соответствующего пользовательского интерфейса.  
  
 Xamarin.Forms предоставляет общий набор интерфейсов API, который позволяет создавать общий уровень пользовательского интерфейса для всех платформ в переносимой библиотеке классов.  Xamarin.Forms отрисовывает нативные элементы управления для каждой целевой платформы, чтобы передать знакомые внешний вид и ощущения.  Вместо использования конструктора в Xamarin.Forms можно создать свой пользовательский интерфейс с помощью C# и XAML.  
  
 Не нужно решать, какой подход использовать сразу, — приложения могут быть реализованы с помощью сочетания Xamarin Native и Xamarin.Forms:  
  
- Xamarin.Forms используется для создания экранов общего назначения, предоставляющих аналогичные пользовательский интерфейс и возможности на разных платформах, например страницы для входа, формы контактов и результаты поиска.  
  
- Используйте различные возможности в Xamarin.Forms для настройки пользовательского интерфейса отдельно для каждой платформы. К ним относятся OnPlatform API, который можно использовать в коде и в XAML, создание настраиваемого представления, расширение существующего и создание пользовательского модуля отрисовки.  
  
- При необходимости используйте Xamarin Native для создания экранов, применяющих уникальные возможности пользовательского интерфейса каждой из платформ, например экрана, который использует нативный захват с камеры и обработку изображений.  
  
  Рекомендуется всегда начинать с решения Xamarin.Forms, чтобы настроить общий доступ к коду пользовательского интерфейса для нескольких платформ, и использовать возможности по настройке для корректировки под конкретную платформу. Если и когда требуется создавать экраны полностью под определенную платформу, можно добавить их по отдельности с помощью Xamarin Native.  
  
  Дополнительные сведения:  
  
1. [Xamarin.Forms](https://docs.microsoft.com/xamarin/xamarin-forms/) (xamarin.com) предоставляет краткий обзор, а также сравнение Xamarin.Forms и уровней нативного пользовательского интерфейса (то есть Xamarin.iOS и Xamarin.Android).  
  
2. Первые три минуты видео Джеймса Монтеманьо [Xamarin.Forms: создание нативных приложений iOS, Android и Windows с помощью C# и XAML](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/704) (Channel9, 13 мин 3 с) содержат еще один обзор; остальная часть видео посвящена демонстрациям.  
  
3. (Необязательно.) [Введение в Xamarin.Forms](https://docs.microsoft.com/xamarin/get-started/quickstarts/deepdive?pivots=windows) (xamarin.com)  
  
4. (Необязательно.) Примеры использования OnPlatform для настройки см. в документации по [классу Device](https://docs.microsoft.com/xamarin/xamarin-forms/platform/device) (xamarin.com)  
  
5. (Необязательно.) Статья [Кроссплатформенная разработка — общий доступ к коду пользовательского интерфейса на мобильных платформах с помощью Xamarin.Forms](https://msdn.microsoft.com/magazine/dn904669.aspx) , автор Джейсон Смит (Jason Smith) из MSDN Magazine. В статье описаны разные возможности настройки в Xamarin.Forms, подробнее о которых написано в другой статье, [Настройка элементов управления для каждой платформы](https://docs.microsoft.com/xamarin/xamarin-forms/app-fundamentals/custom-renderer/) (xamarin.com).  
  
## <a name="deeper-dive-debugging-with-emulators"></a>Подробное рассмотрение: отладка с помощью эмуляторов  
 *10–15 минут*  
  
 Для отладки кроссплатформенных приложений без использования физического устройства необходимо использовать следующие средства.  
  
1. **Эмулятор Android.** В зависимости от того, какая версия Windows используется, рекомендуется либо эмулятор Microsoft Visual Studio для Android или Xamarin Player, которые обеспечивают высокую производительность и поддерживает широкий набор возможностей устройства:  
  
    - **Компьютеры с Windows 8+.** Настоятельно рекомендуется использовать эмулятор Microsoft [Visual Studio для Android](https://www.visualstudio.com/features/msft-android-emulator-vs.aspx), который устанавливается вместе с Visual Studio.  Видео об [эмуляторе Visual Studio для Android](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/711) (Channel9, 5 мин. 55 сек.) содержит еще один обзор и демонстрацию.  
  
    - **Windows 7 и более ранние версии или Windows на Mac OS X**. Используйте [Xamarin Android Player](https://docs.microsoft.com/xamarin/android/deploy-test/debugging/debug-on-emulator?tabs=windows) (xamarin.com).  
  
2. **Симулятор iOS Apple.** Дополнительные сведения см. в статье [Начало работы с симулятором iOS](https://developer.apple.com/library/prerelease/content/documentation/IDEs/Conceptual/iOS_Simulator_Guide/GettingStartedwithiOSSimulator/GettingStartedwithiOSSimulator.html#//apple_ref/doc/uid/TP40012848-CH5-SW1) (apple.com).  
  
3. **Эмулятор Microsoft Windows Phone.** Дополнительные сведения см. в статье [Эмулятор Windows Phone для Windows Phone 8](https://msdn.microsoft.com/library/dn632391.aspx).  
  
## <a name="components"></a> Deeper Dive: Xamarin Components  
 *10 минут*  
  
 Многие расширенные возможности доступны для приложений Xamarin через компоненты Xamarin. Полный каталог доступен для скачивания на сайте [http://components.xamarin.com/](https://docs.microsoft.com/xamarin/cross-platform/troubleshooting/component-nuget?tabs=windows) и включает в себя компоненты для дополнительных элементов управления пользовательского интерфейса, проверки подлинности, разнообразные облачные службы, например Microsoft Azure, и многое другое.
