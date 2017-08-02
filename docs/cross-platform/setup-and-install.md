---
title: "Настройка и установка | Документация Майкрософт"
ms.custom: 
ms.date: 04/13/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2cfcad00-352c-4161-814c-f5ae32d8ada8
caps.latest.revision: 16
author: ghogen
ms.author: ghogen
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: d353d8a0a41ad487191b79aa68f26585cf9902b4
ms.contentlocale: ru-ru
ms.lasthandoff: 05/13/2017

---
# <a name="setup-and-install"></a>Настройка и установка
Для создания нативных приложений iOS, Android и Windows из общей базы кода C# и .NET с помощью Xamarin необходимо следующее:  
  
-   Для работы с приложениями Windows и Android требуется компьютер Windows, настроенный для разработки, на котором установлены Visual Studio 2017 или 2015 и платформа Xamarin. Вы также можете использовать Visual Studio 2013, выполнив указания для [прямой установки Xamarin](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (xamarin.com). 
  
-   Для работы с приложениями iOS требуется компьютер Mac под управлением macOS Sierra 10.12 или более поздней версии с установленными XCode и Xamarin.  
  
 Можно настроить компьютеры Windows и Mac одновременно и во время работы соответствующих установщиков ознакомиться с разделом [Подробности о разработке мобильных приложений с использованием Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md), чтобы прочитать и просмотреть необходимые материалы общего характера.  
 
Если у вас возникают проблемы с использованием Xamarin после установки и настройки, опубликуйте вопрос на сайте [forums.xamarin.com](http://forums.xamarin.com/).
  
> [!NOTE]
>  Начиная с 31 марта 2016 года, Xamarin целиком включается во все выпуски Visual Studio, не требуя дополнительных затрат и отдельной лицензии. Xamarin Studio Community для Mac также предоставляется бесплатно для студентов, разработчиков OSS и небольших групп. Обратите внимание, что для существующих установок Visual Studio, настроенных с помощью более ранних лицензий Xamarin, требуется обновить Xamarin до версии 4.0.3.214 или более поздней. Для этого выберите **"Сервис" > "Параметры" > Xamarin > "Другие"**, щелкните ссылку **Проверить сейчас** и скачайте обновление до версии 4.0.3.214. После перезапуска Visual Studio выберите **"Сервис" > "Учетная запись Xamarin..."** и убедитесь, что отображается обновленное состояние.  
  
##  <a name="prereq"></a> Необходимые компоненты  
  
###  <a name="for-targeting-windows-and-android"></a>Для операционных систем Windows и Android 
  
1.  Рекомендуется: физический компьютер Windows (не виртуальная машина) под управлением Windows 8 или более поздней версии, чтобы обеспечить оптимальную производительность эмулятора Android. (Помните: требуется именно физический компьютер, а не виртуальная машина.)  
  
2.  Можно использовать компьютер с Windows 7 или более ранней версией; в этом случае необходимо использовать проигрыватель Xamarin Player для Android в роли эмулятора. 
    
3. Для любой конфигурации приложения можно запускать непосредственно на подключенных физических устройствах.  
  
### <a name="for-targeting-ios"></a>Для операционной системы iOS  
  
1.  Подключенный к сети компьютер Mac или Mac Mini под управлением macOS Sierra 10.12 или более поздней версии (требуется для Xcode 8.3).  
  
2.  При использовании Visual Studio на компьютере Windows (версии 7 или более поздней) в качестве основной среды разработки, подключенный к сети Mac необходим только для компиляции и отладки приложений iOS, подключения к симулятору iOS или связанным устройствам, а также для использования конструктора раскадровки в Visual Studio для разработки пользовательского интерфейса. Старые модели Mac полностью подходят для этой дополнительной роли.  
  
##  <a name="windows"></a> Программа установки Windows (Visual Studio и Xamarin)  
  
> [!TIP]
>  Эти инструкции предназначены для Visual Studio 2017. Рекомендации для Visual Studio 2015 вы найдете на сайте [MSDN](https://msdn.microsoft.com/en-us/library/mt613162.aspx). Чтобы использовать Xamarin с Visual Studio 2013 (требуется обновление 2), следуйте инструкциям по [прямой установке Xamarin](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (xamarin.com).  
  
1.  [Скачайте и запустите установщик для любого выпуска Visual Studio 2017](https://www.visualstudio.com/downloads/) (Community, Professional или Enterprise). Visual Studio 2017 Community — это бесплатный выпуск; выпуски Professional и Enterprise можно бесплатно использовать для ознакомления в течение 30 дней, по истечении которых необходимо приобрести лицензию.  
  
    1.  Если у вас уже установлен Visual Studio 2017, запустите **установщик Visual Studio** из меню **Пуск**.
  
2.  В программе установки щелкните значок **Выбор дополнительных вариантов** (три полоски), расположенный _рядом с_ кнопкой **Запуск**, затем выберите **Изменить**.  
  
     ![Выбор действия "Изменить" в установке Visual Studio](~/docs/cross-platform/media/cross-plat-xamarin-setup-1a.png "Кросс-платформенная установка Xamarin 1")  
  
3.  Установите следующие флажки.  
  
    1.  **Мобильные приложения и игры > Разработка мобильных приложений на платформе .NET**. При этом также будут автоматически выбраны различные инструменты Android в разделе "Общие средства и пакеты средств разработки". Этот параметр также позволяет обновить любую существующую установку Xamarin.  
  
         ![Выбор параметра "Мобильная разработка" в разделе разработки игр и мобильных приложений](~/docs/cross-platform/media/cross-plat-xamarin-setup-2a.png "Кросс-платформенная установка Xamarin 2")  
  
    2. **Windows > Разработка с помощью универсальной платформы Windows"** (необязательно). Здесь вы можете выбрать образы эмуляторов, на скачивание которых потребуется дополнительное время. Также вы можете запустить установщик Visual Studio в любое время позже, чтобы добавить их. 
  
4.  Нажмите кнопку **Изменить** и дождитесь завершения процесса. Для завершения может потребоваться некоторое время, в течение которого можно продолжить изучение инструкций по настройке Mac и ознакомиться со статьей [Подробности о разработке мобильных приложений с использованием Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).  
  
5.  После завершения установки запустите Visual Studio и выполните вход с помощью учетной записи Майкрософт при появлении соответствующего запроса (это та же учетная запись, что используется и в Windows).  
      
6.  Если у вас нет подходящих физических устройств, для тестирования приложений Android используйте [эмулятор Android SDK](https://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/debug-on-emulator/android-sdk-emulator/). См. примечание ниже.  
  
 **Примечание об эмуляторах на компьютерах Windows.** Так как процессоры поддерживают только одну технологию виртуализации одновременно, рекомендуется использовать только одну из них на компьютере, на котором ведется разработка. Существует три основных технологии виртуализации: Hyper-V (используется эмулятором Visual Studio для Android и эмулятором Windows Phone), Virtual Box (используется Genymotion) и Intel HAXM (используется эмулятором пакета SDK для Android). Из-за различных проблем между Hyper-V и Virtual Box лучше использовать эмуляторы только одного типа для конкретного компьютера, поэтому выше даются рекомендации использовать Hyper-V на компьютерах под управлением Windows 8 и более поздних версий и эмуляторы Intel HAXM на компьютерах под управлением Windows 7 и более ранних версий, а также при запуске Windows на Mac.  
  
##  <a name="mac"></a> Настройка Mac (Apple ID, Xcode и Xamarin)  
  
1.  Создайте бесплатный идентификатор Apple ID на сайте [https://appleid.apple.com](https://appleid.apple.com/), если у вас его нет. Это необходимо для установки приложения Xcode и входа в него.  
  
2.  Скачайте и установите Xcode на странице  [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/)и добавьте ваш идентификатор Apple ID, как описано в разделе [Добавление учетной записи для XCode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (apple.com).  
  
3.  Скачайте и установите Xamarin, следуя указаниям в статье [Установка и настройка Xamarin.iOS](http://developer.xamarin.com/guides/ios/getting_started/installation/mac/) (xamarin.com).  
  
4.  После завершения установки Xamarin на компьютерах Mac и Windows следуйте инструкциям в статье [Подключение к Mac](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/xamarin-mac-agent/) (xamarin.com), чтобы обеспечить возможность работы с iOS и Mac из Visual Studio на компьютере под управлением Windows.  
  
     Обратите внимание, что оба компьютера должны находиться в одной локальной сети.
