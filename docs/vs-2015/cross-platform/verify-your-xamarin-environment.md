---
title: Проверка окружения Xamarin | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd39882e-06d1-4b39-80d2-4d07b6e4f8f5
caps.latest.revision: 15
ms.author: crdun
manager: crdun
ms.openlocfilehash: 66428a7f06aee5449191a13e2712ae119daffb0e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49243496"
---
# <a name="verify-your-xamarin-environment"></a>Проверка окружения Xamarin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
После завершения работы установщиков (см. раздел [Настройка и установка](../cross-platform/setup-and-install.md)) потратьте несколько минут на проверку готовности системы к разработке приложений в Xamarin.  
  
 После завершения этих проверок, можно выполнить одно или оба указанных ниже пошаговых руководства:  
  
-   [Основы создания приложений с помощью Xamarin.Forms в Visual Studio](../cross-platform/learn-app-building-basics-with-xamarin-forms-in-visual-studio.md)  
  
-   [Создание приложений с собственным пользовательским интерфейсом с использованием Xamarin в Visual Studio](../cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md)  
  
## <a name="all-platforms"></a>Все платформы  
 Сначала выберите **"Сервис" > "Параметры"**, разверните пункт **Xamarin > "Другие"** и щелкните ссылку **Проверить сейчас** для поиска обновлений. Следует использовать Xamarin 4.0.3.214 или более поздней версии во избежание имевшихся ранее проблем с лицензированием.  
  
 Создайте новое решение Xamarin в Visual Studio, выбрав **"Файл" > "Новый проект"**; в диалоговом окне разверните **"Шаблоны" > "Другие языки" > "Visual C#" > "Кроссплатформенный"**, выберите **Пустое приложение (Native Portable)** и нажмите кнопку "ОК". При этом будет создано решение с помощью общего проекта переносимой библиотеки классов и отдельные проекты для Android, iOS и Windows:  
  
 ![Результаты создания нового проекта из шаблона пустого приложения &#40;нативного и переносимого&#41;](../cross-platform/media/crossplat-xamarin-verify-1.png "CrossPlat Xamarin Verify 1")  
  
> [!NOTE]
>  Если шаблонов там нет, см. раздел [Нет шаблонов проектов Xamarin? Попробуйте это](#missing) в нижней части этой страницы.  
  
## <a name="android"></a>Android  
  
1. Убедитесь, что установлены самые новые средства пакета SDK для Android, выбрав **Tools > Android > Android SDK Manager** и установив последнюю версию пакета инструментов SDK Android, инструментов платформы SDK Android и инструментов сборки SDK Android. Обратите внимание, что не всегда требуется устанавливать последний уровень API Android; нужный API зависит от уровня платформы, на который вы хотите ориентироваться. В общем случае при установке Xamarin будет установлен требуемый уровень платформы.  

2.  Проверьте конструктор Android: в проекте Android в обозревателе решений откройте файл **"Ресурсы" > "Макет" > "Main.axml"**. (Если вы не видите этот файл, попробуйте найти его в обозревателе решений; он существует только в проекте Android и отсутствует в проекте iOS.)  
  
    - Если появляется ошибка "Слишком старый установленный пакет SDK Android", нажмите кнопку **Open Android SDK** (Открыть пакет SDK для Android) в том сообщении и выберите новейшую версию пакета SDK в рамках описанного выше шага 1. 
  
3.  Проверка сборки и отладки в эмуляторе (или устройстве)  
  
    -   В обозревателе решений щелкните правой кнопкой мыши проект Android и выберите команду **Назначить запускаемым проектом**.  
  
         ![Visual Studio в качестве параметра запуска проекта](../cross-platform/media/crossplat-xamarin-verify-2.png "CrossPlat Xamarin Verify 2")  
  
    -   Выберите подходящий эмулятор в зависимости от целевой версии Android. Если к компьютеру подключено устройство разработки с Android, вы увидите его здесь в списке с эмуляторами:  
  
        -   Для Windows 8 и более поздних версий: выберите целевой объект **Эмулятор VS** в раскрывающемся списке отладки Visual Studio, как показано ниже, и запустите отладчик, нажав клавишу **F5**. Дополнительные сведения см. в статье [Введение в эмулятор Visual Studio для Android](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/12/introducing-visual-studio-s-emulator-for-android.aspx) (блог по Visual Studio ALM). При возникновении проблем с запуском эмулятора см. раздел [Устранение неполадок эмулятора Android для Visual Studio](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md). Можно также создать новые профили устройств для эмулятора, выбрав **"Сервис" > "Эмулятор Visual Studio для Android..."**.  
  
             ![Выбор эмулятора Visual Studio для Android в качестве целевого объекта отладки](../cross-platform/media/crossplat-xamarin-verify-3.png "CrossPlat Xamarin Verify 3")  
  
             Примечание. Если вы не видите пункт меню **"Сервис" > "Эмулятор Visual Studio для Android..."**, возможно у вас не установлен сам эмулятор. Последовательно выберите пункты **"Панель управления" > "Программы и компоненты"**, выберите **Microsoft Visual Studio** и нажмите кнопку **Изменить** для перезапуска установщика. Щелкните **Изменить** в установщике, установите флажок **"Разработка кроссплатформенных мобильных приложений" > "Эмулятор Microsoft Visual Studio для Android"** и нажмите кнопку **Обновить**.  
  
        -   Для Windows 7 и более ранних версий ОС: выберите Xamarin Player для Android в раскрывающемся списке и нажмите клавишу F5 для запуска. Дополнительные сведения о Xamarin Player и его диспетчере устройств, а также советы по устранению проблем см. в статье [Xamarin Android Player](http://developer.xamarin.com/guides/android/getting_started/installation/android-player/) (xamarin.com).  
  
> [!NOTE]
>  В Visual Studio можно заметить наличие на панели инструментов кнопки диспетчера эмулятора Android (показано на следующем рисунке), по нажатию которой открывается диспетчер устройств, используемый конкретно для настройки эмулятора Google Android.  Это не оказывает влияния ни на эмулятор Visual Studio для Android, ни на Xamarin Player, каждый из которых имеет свой диспетчер устройств для настройки профилей.  See [Introducing Visual Studio’s Emulator for Android](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/12/introducing-visual-studio-s-emulator-for-android.aspx) (Visual Studio ALM blog) and [Xamarin Android Player](http://developer.xamarin.com/guides/android/getting_started/installation/android-player/) (xamarin.com) for details.  
> ![Проверка CrossPlat Xamarin 7](../cross-platform/media/crossplat-xamarin-verify-7.png "Проверка CrossPlat Xamarin 7")  
  
## <a name="windows-phone"></a>Windows Phone  
  
1.  Проверьте конструктор Windows Phone: в проекте Windows Phone в обозревателе решений откройте файл **MainPage.xaml** .  
  
2.  Проверьте сборку и отладку в эмуляторе или на устройстве (обратите внимание, что для этого шага необходимо установить эмулятор Windows Phone через программу установки Visual Studio или иметь связанное устройство):  
  
    -   В обозревателе решений щелкните правой кнопкой мыши проект Windows Phone и выберите команду **Назначить запускаемым проектом**.  
  
    -   Выберите в качестве целевого объекта **Emulator 8.1** (Эмулятор 8.1) или подключенное устройство в раскрывающемся списке отладки Visual Studio, как показано ниже, и запустите отладчик, нажав клавишу F5.  
  
         ![Выбор эмулятора Windows Phone в качестве целевого объекта отладки](../cross-platform/media/crossplat-xamarin-verify-4.png "Проверка CrossPlat Xamarin 4")  
  
    -   Если не получается начать работу с эмулятором, ознакомьтесь со статьей [Устранение неполадок в эмуляторе Windows Phone 8](https://msdn.microsoft.com/library/windows/apps/jj681694.aspx).  
  
## <a name="ios"></a>iOS  
  
1.  Убедитесь, что компьютер Mac доступен в сети и связан с Visual Studio, как описано в статье [Подключение к Mac](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/xamarin-mac-agent/) (xamarin.com).  
  
2.  Проверьте конструктор раскадровки: в проекте iOS в обозревателе решений откройте файл **Main.storyboard** . Здесь Visual Studio размещает конструктор, который выполняется удаленно на компьютере Mac.  
  
3.  Проверьте сборку и отладку.  
  
    1.  В обозревателе решений щелкните правой кнопкой мыши проект iOS и выберите команду **Назначить запускаемым проектом**.  
  
    2.  Выберите в качестве целевого объекта **iPhoneSimulator** из раскрывающегося списка сборки Visual Studio, как показано ниже, или **iPhone** , если имеется связанное устройство. Если симуляторов в списке нет, запустите Xcode на компьютере Mac, выберите **Xcode -> Preferences** (Xcode -> Параметры) и нажмите кнопку **Download** (Cкачать). В разделе **Components** (Компоненты) вы должны увидеть доступные для скачивания версии симулятора. Дополнительные инструкции по отладке можно найти на странице Xamarin [Отладка](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) (xamarin.com).  
  
         ![Выбор целевого объекта сборки iPhoneSimulator](../cross-platform/media/crossplat-xamarin-verify-5.png "Проверка CrossPlat Xamarin 5")  
  
    3.  Выберите целевой объект iPhone в раскрывающемся списке отладки Visual Studio, как показано ниже, и запустите отладчик, нажав клавишу F5. Это откроет симулятор на Mac, где можно будет взаимодействовать с приложением во время отладки из Visual Studio. Если у вас есть физический iPhone или iPad, подключенный к Mac, они отобразятся здесь, чтобы вы могли выбрать их. Если вы не видите перечисленные устройства или симуляторы, проверьте подключение к Mac, просмотрев раздел, на который указывает ссылка в шаге 1 выше, или перейдите в раздел **Средства** >**iOS** >**Xamarin Mac Agent**  
  
         ![Выбор целевого объекта отладки iPhone](../cross-platform/media/crossplat-xamarin-verify-6.png "Проверка CrossPlat Xamarin 6")  
  
    4.  Если возникли проблемы с подключением к Mac, ознакомьтесь со статьей [Устранение неполадок при подключении](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/xamarin-mac-agent/xma-troubleshooting/) (xamarin.com).  
  
    5.  Если отображается ошибка "Нет установленных профилей подготовки, которые соответствуют установленным ключам подписи iOS", выполните следующие действия.  
  
        -   Убедитесь, что учетная запись Apple ID добавлена в Xcode на компьютере Mac, как описано в статье [Добавление учетной записи для Xcode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (apple.com).  После добавления учетной записи перезапустите Visual Studio и Xcode.  
  
             ![Проверка CrossPlat Xamarin 8](../cross-platform/media/crossplat-xamarin-verify-8.png "Проверка CrossPlat Xamarin 8")  
  
        -   Убедитесь, что в свойствах проекта iOS на вкладке подписывания пакета iOS поле Custom (Настраиваемые) пусто для активной конфигурации отладки.  Примечание. Удалять этот параметр следует, только если отображается указанное выше сообщение об ошибке.  
  
##  <a name="missing"></a> Нет шаблонов проектов Xamarin? Попробуйте это  
 Шаблоны могут отсутствовать, если приложение Xamarin установлено непосредственно с веб-сайта Xamarin и параллельно с Visual Studio 2013 установлена версия Visual Studio 2015. Это легко исправить: просто включите компонент **Xamarin for Visual Studio 2015** (Xamarin для Visual Studio 2015) в программе установки Xamarin.  
  
1.  На панели управления откройте **Программы и компоненты**, выберите **Xamarin** и нажмите кнопку **Изменить**.  
  
2.  В появившемся мастере установки Xamarin последовательно нажмите кнопки **Далее** и **Изменить**.  
  
3.  В списке дополнительных компонентов для установки разверните узел **Xamarin for Visual Studio 2015**(Xamarin для Visual Studio 2015), выберите **will be installed on local drive**(Будет установлен на локальном диске) и нажмите кнопку **Далее** , чтобы продолжить добавление компонента.

