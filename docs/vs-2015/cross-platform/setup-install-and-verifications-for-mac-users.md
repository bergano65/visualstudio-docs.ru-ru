---
title: Программа установки, установка и проверки для пользователей Mac | Документы Майкрософт
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 22725520-59ba-4f6f-80e4-097b1287a34b
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: 623e47e7244e9e4317e89f47cfda02bda465273b
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59670294"
---
# <a name="setup-install-and-verifications-for-mac-users"></a>Программа установки, установка и проверки для пользователей Mac
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эта статья предназначена для разработчиков, которые работают в основном на Mac и которые будут при необходимости использовать Visual Studio на виртуальной машине Windows на компьютере Mac. Если вы работаете в основном на компьютере с Windows и вам нужно настроить дополнительный компьютер Mac, чтобы разрабатывать приложения для iOS, см. основную статью [Настройка и установка](../cross-platform/setup-and-install.md) .  
  
 Для работы с Xamarin на Mac потребуется следующее:  
  
- Учетная запись Xamarin. Перейдите к [ https://www.xamarin.com/ ](https://www.xamarin.com/) и нажмите кнопку **Sign In** в верхнем правом углу страницы, затем нажмите кнопку **создать учетную запись** на появившейся странице. Выберите адрес электронной почты и пароль для учетной записи Xamarin.  
  
- компьютер Mac с OS X Yosemite (10.10) или более поздней версии с установленными Xcode 7 и Xamarin 4;  
  
- одна из следующих конфигураций:  
  
  -   **Для выполнения Xamarin Studio непосредственно на компьютере Mac:** Xamarin Studio — окружение разработки Xamarin которое поддерживает создание приложений Android, iOS и Windows с помощью C#.  Краткий обзор Xamarin Studio см. на [сайте с основной информацией о Xamarin Studio](https://xamarin.com/studio) (xamarin.com).  
  
  -   **Parallels или VMWare уже настроен на компьютере Mac.** Запустите Windows с Visual Studio 2015 и Xamarin 4 внутри Parallels или VMWare.  В такой конфигурации Xamarin — это расширение, установленное для Visual Studio, которое позволяет использовать Visual Studio в качестве окружения разработки для создания приложений Android, iOS и Windows Phone с помощью C#.  Обратите внимание, что можно получить бесплатную 3-месячную подписку на Parallels в рамках программы Visual Studio Developer Essentials. См. публикацию [Microsoft Visual Studio Dev Essentials будет включать доступ к Parallels Desktop Pro и Parallels Access](http://blog.parallels.com/blog/2015/11/18/visual-studio-dev-essentials/) (Microsoft Visual Studio Dev Essentials Will Include Parallels Desktop Pro and Parallels Access, блог Parallels).  
  
  В этой статье содержатся инструкции, связанные с данными требованиями.  Во время установки вы можете получить прочитать статью [Подробности о разработке мобильных приложений с использованием Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md), чтобы изучить и посмотреть необходимые материалы общего характера.  
  
  **Содержание раздела**  
  
- [Настройка Mac (Apple ID, Xcode и Xamarin)](#mac)  
  
- [Программа установки Windows в Parallels (Visual Studio и Xamarin)](#windows)  
  
- [Проверка окружения](#verify)  
  
##  <a name="mac"></a> Настройка Mac (Apple ID, Xcode и Xamarin)  
  
1.  Создайте бесплатный идентификатор Apple ID в разделе [Мой идентификатор Apple ID](https://appleid.apple.com/) , если у вас его нет. Это необходимо для установки приложения Xcode и входа в него.  
  
2.  Загрузите и установите Xcode с сайта [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/).  
  
3.  Скачайте и установите Xamarin, следуя указаниям в статье [Установка и настройка Xamarin.iOS](http://developer.xamarin.com/guides/ios/getting_started/installation/mac/) (xamarin.com).  
  
4.  После завершения установки Xamarin на компьютерах Mac и Windows следуйте инструкциям в статье [Подключение к Mac с помощью XMA](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/#Connecting_to_the_Mac_Using_XMA) (xamarin.com), чтобы обеспечить возможность работы с iOS и Mac из Visual Studio на компьютере под управлением Windows.  
  
##  <a name="windows"></a> Программа установки Windows в Parallels (Visual Studio и Xamarin)  
  
1.  С помощью рабочего стола Windows, который настроен в Parallels или VMWare, [скачайте и запустите установщик для любого выпуска Visual Studio 2015](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx) (Community, Professional или Enterprise). Visual Studio 2015 Community — это бесплатный выпуск; выпуски Professional и Enterprise можно использовать для ознакомления в течение 30 дней.  
  
2.  В программе установки выберите тип установки **Пользовательская** .  
  
     ![Выбор параметра "Выборочная" в установке Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-1.png "Кросс-платформенная установка Xamarin 1")  
  
3.  Установите/снимите следующие флажки:  
  
    1.  Установите флажок **"Разработка кроссплатформенных мобильных приложений" > "C#/.NET (Xamarin)"**. При этом также будут автоматически выбраны различные инструменты Android в разделе "Общие средства и пакеты средств разработки".  
  
         ![Выбор параметра Xamarin в разделе разработки кроссплатформенных мобильных приложений](../cross-platform/media/cross-plat-xamarin-setup-2.png "Кросс-платформенная установка Xamarin 2")  
  
    2.  Снимите флажок **"Разработка кроссплатформенных мобильных приложений" > "Эмулятор Microsoft Visual Studio для Android"**.  
  
4.  Нажмите кнопку "Установить" и запустите процесс. Для завершения может потребоваться некоторое время, в течение которого можно продолжить изучение материалов данного раздела и ознакомиться с разделом [Подробности о разработке мобильных приложений с использованием Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).  
  
5.  После завершения установки запустите Visual Studio и выполните вход с помощью учетной записи Майкрософт при появлении соответствующего запроса (это та же учетная запись, что используется и в Windows). Проверьте наличие обновлений для Xamarin через меню **"Сервис" > "Параметры" > Xamarin** или **"Сервис" > "Параметры" > Xamarin > "Другие"**, где вы найдете ссылку **Проверить сейчас**:  
  
     ![Проверка наличия обновлений Xamarin в параметрах Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-3.png "Кросс-платформенная установка Xamarin 3")  
  
    > [!NOTE]
    >  Требуется обновить Xamarin до версии 4.0.3.214 или более поздней, чтобы избежать проблем с более ранними лицензиями Xamarin.  Если при попытке проверить наличие обновлений возникает ошибка Microsoft Build Tools, см. беседу на [форумах по Xamarin](http://forums.xamarin.com/discussion/69015/xamarin-update-on-vs-2013-says-i-need-the-build-tools-for-vs-2015).
  
6.  После завершения установки Xamarin на компьютерах Mac и Windows следуйте инструкциям в статье [Подключение к Mac с помощью XMA](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/#Connecting_to_the_Mac_Using_XMA) (xamarin.com), чтобы обеспечить возможность работы с iOS из Visual Studio.  
  
##  <a name="verify"></a> Проверка окружения  
 После завершения работы установщиков потратьте несколько минут на проверку готовности системы к разработке приложений в Xamarin.  
  
### <a name="xamarin-studio"></a>Xamarin Studio  
 Во-первых, убедитесь, что при переходе по указанным ссылкам у вас выбран **Xamarin Studio** в правом верхнем углу, чтобы увидеть правильную версию документации по Xamarin:  
  
 ![Выбор Xamarin Studio для просмотра правильной документации на сайте Xamarin.com](../cross-platform/media/crossplat-xamarin-mac-1.png "CrossPlat Xamarin Mac 1")  
  
 **Android**  
  
1. Проверьте, правильно ли создается проект Android, следуя инструкциям в статье [Создание проекта Android](http://developer.xamarin.com/recipes/android/general/projects/create_an_android_project/) (xamarin.com).  
  
2. Проверьте отладку в проигрывателе Android Player с помощью статьи [Android Player > "Документация по интеграции с Xamarin Studio"](https://developer.xamarin.com/guides/android/getting_started/installation/android-player/#Integration_with_Xamarin_Studio) (xamarin.com).  
  
   **iOS**  
  
3. Проверьте, правильно ли создается проект iOS, следуя инструкциям в статье [Создание проекта iOS](http://developer.xamarin.com/recipes/ios/general/projects/create_an_ios_project/) (xamarin.com).  
  
4. Проверьте отладку в симуляторе iOS с помощью статьи [Документация по отладке в симуляторе](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) (xamarin.com).  
  
### <a name="visual-studio"></a>Visual Studio  
 Во-первых, убедитесь, что при переходе по указанным ссылкам у вас выбран **Visual Studio** в правом верхнем углу, чтобы увидеть правильную версию документации по Xamarin:  
  
 ![Выбор Visual Studio для просмотра правильной документации на сайте Xamarin.com](../cross-platform/media/crossplat-xamarin-mac-2.png "CrossPlat Xamarin Mac 2")  
  
 Также войдите с помощью своей учетной записи Xamarin, выбрав **"Сервис" > "Учетная запись Xamarin..."**.  
  
 **Android**  
  
1. Проверьте, правильно ли создается проект Android, следуя инструкциям в статье [Создание проекта Android](http://developer.xamarin.com/recipes/android/general/projects/create_an_android_project/) (xamarin.com).  
  
2. Проверьте конструктор Android: в проекте Android в обозревателе решений откройте файл **"Ресурсы" > "Макет" > "Main.axml"**.  
  
   -   Если появляется ошибка "Слишком старый установленный пакет SDK Android", нажмите **Открыть пакет SDK для Android** в том сообщении и выберите новейшую версию пакета SDK. Обратите внимание, что необходимо использовать Visual Studio от имени администратора, чтобы обновить пакет SDK.  
  
3. Проверьте возможность подключения из Visual Studio к эмулятору, установленному на вашем Mac.  В результате вы должны увидеть проигрыватель Xamarin Player в списке эмуляторов, которые доступны в Visual Studio для отладки.  Чтобы сделать это, следуйте инструкциям в статье [Подключение Visual Studio к Xamarin Android Player](http://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/android-player-with-visual-studio-in-vm/) (xamarin.com).  
  
   **iOS**  
  
4. Убедитесь, что компьютер Mac доступен в сети и соединен с Visual Studio, как описано в статье [Подключение к Mac с помощью XMA](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/#Connecting_to_the_Mac_Using_XMA) (xamarin.com).  
  
5. Проверьте, правильно ли создается проект iOS, следуя инструкциям в статье [Создание проекта iOS](http://developer.xamarin.com/recipes/ios/general/projects/create_an_ios_project/) (xamarin.com).  
  
6. Проверьте конструктор раскадровки: в проекте iOS в обозревателе решений откройте файл **MainStoryboard.storyboard** . Здесь Visual Studio размещает конструктор, который выполняется удаленно на компьютере Mac.  
  
7. Проверьте сборку и отладку.  
  
   1.  В обозревателе решений щелкните правой кнопкой мыши проект iOS и выберите команду **Назначить запускаемым проектом**.  
  
   2.  Выберите целевой объект **iPhoneSimulator** из раскрывающегося списка сборки Visual Studio, как показано ниже. Если симуляторов в списке нет, запустите Xcode на компьютере Mac, выберите **Xcode -> Preferences** (Xcode -> Параметры) и нажмите кнопку **Download** (Cкачать). В разделе **Components** (Компоненты) вы должны увидеть доступные для скачивания версии симулятора. Дополнительные инструкции по отладке можно найти на странице Xamarin [Отладка](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) (xamarin.com).  
  
        ![Выбор целевого объекта сборки iPhoneSimulator](../cross-platform/media/crossplat-xamarin-verify-5.png "Проверка CrossPlat Xamarin 5")  
  
   3.  Выберите целевой объект iPhone в раскрывающемся списке отладки Visual Studio, как показано ниже, и запустите отладчик, нажав клавишу F5. Это откроет симулятор на Mac, где можно будет взаимодействовать с приложением во время отладки из Visual Studio.  
  
        ![Выбор целевого объекта отладки iPhone](../cross-platform/media/crossplat-xamarin-verify-6.png "Проверка CrossPlat Xamarin 6")
