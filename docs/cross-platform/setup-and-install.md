---
title: Установка Xamarin для Visual Studio | Документы Майкрософт
ms.custom: ''
ms.date: 03/30/2018
ms.topic: conceptual
ms.assetid: 2cfcad00-352c-4161-814c-f5ae32d8ada8
ms.prod: visual-studio-dev15
ms.technology: vs-ide-mobile
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 8bbb27ad3368b53fc3e333d3260f2f30551c4177
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2018
ms.locfileid: "39251196"
---
# <a name="setup-and-install"></a>Настройка и установка

Для создания нативных приложений iOS, Android и Windows из общей базы кода C# и .NET с помощью Xamarin необходимо следующее программное и аппаратное обеспечение:

-   Для работы с приложениями Windows и Android требуется компьютер разработчика Windows (не на виртуальной машине) с установленной средой Visual Studio 2017 (включая средства разработки Xamarin).

-   Для работы с приложениями iOS требуется компьютер Mac под управлением macOS Sierra 10.12 или более поздней версии с установленными XCode и Visual Studio для Mac.

Для использования платформы Xamarin не требуется дополнительных лицензий.

Можно настроить компьютеры Windows и Mac одновременно и во время работы соответствующих установщиков ознакомиться с разделом [Подробности о разработке мобильных приложений с использованием Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md), чтобы прочитать и просмотреть необходимые материалы общего характера.

Если у вас возникают проблемы с использованием платформы Xamarin после установки и настройки, задайте вопрос на сайте [forums.xamarin.com](http://forums.xamarin.com/).

<a name="prereq" />

## <a name="pre-requisites"></a>Предварительные требования

###  <a name="for-targeting-windows-and-android"></a>Для операционных систем Windows и Android

Подробные сведения о необходимых компонентах для установки Visual Studio 2017 см. в разделе [Требования к системе для семейства продуктов Visual Studio 2017](/visualstudio/productinfo/vs2017-system-requirements-vs).

Устанавливайте Visual Studio 2017 на физический компьютер (не на виртуальную машину) под управлением Windows 10 со всеми установленными обновлениями.

### <a name="for-targeting-ios"></a>Для операционной системы iOS

Для работы с эмуляторами и устройствами iOS с компьютера Windows также потребуется подключенный к сети компьютер Mac или Mac mini под управлением macOS 10.12 или более поздней версии и установленным Xcode 8.3. Подробные сведения о требованиях см. в статье [Установка и настройка Visual Studio для Mac](/visualstudio/mac/installation).

<a name="windows" />

##  <a name="windows-setup-visual-studio-and-xamarin"></a>Программа установки Windows (Visual Studio и Xamarin)

Если вы еще не установили Visual Studio 2017, выполните следующие действия:

1.  [Скачайте и запустите установщик для любого выпуска Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) (Community, Professional или Enterprise). Редакция Visual Studio 2017 Community является бесплатной. Выпуски Professional и Enterprise доступны для ознакомления в течение 30 дней, после истечения которого необходимо приобрести лицензию.

2.  Когда откроется диалоговое окно **Установка**, установите следующие флажки:

    - **Мобильные приложения и игры > Разработка мобильных приложений на платформе .NET**. При этом также будут автоматически выбраны различные инструменты Android и пакеты средств разработки.

        ![Выбор параметра "Мобильная разработка" в разделе разработки игр и мобильных приложений](../cross-platform/media/cross-plat-xamarin-setup-2a.png "Кросс-платформенная установка Xamarin 2")

    - **Windows > Разработка с помощью универсальной платформы Windows"** (необязательно).

Если у вас уже установлен Visual Studio 2017, но еще не установлена платформа Xamarin, выполните следующие действия:

1. Запустите **Visual Studio Installer** **Пуск**.

2.  В установщике нажмите кнопку **Дополнительно**, а затем выберите **Изменить**.

    ![Выбор действия "Изменить" в установке Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-1a.png "Кросс-платформенная установка Xamarin 1")

3.  Когда откроется диалоговое окно **Установка**, установите флажок **Мобильные приложения и игры > Разработка мобильных приложений на платформе .NET** и (необязательно) **Windows > Разработка приложений для универсальной платформы Windows**. Параметр **Разработка мобильных приложений на платформе .NET** также обновит установленную версию Xamarin.

Во время выполнения установки можно продолжить изучение инструкций по настройке Mac и ознакомиться со статьей [Подробности о разработке мобильных приложений с использованием Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).

5.  После завершения установки запустите Visual Studio и выполните вход с помощью учетной записи Майкрософт при появлении соответствующего запроса. Это та же учетная запись, что используется в Windows.

6.  Если у вас нет подходящих физических устройств с Android, для тестирования приложений Android используйте [эмулятор Android SDK](/xamarin/android/get-started/installation/android-emulator/).

<a name="mac" />

##  <a name="mac-setup-apple-id-xcode-and-xamarin"></a>Настройка Mac (Apple ID, Xcode и Xamarin)

1.  Создайте бесплатный идентификатор Apple ID в разделе [https://appleid.apple.com](https://appleid.apple.com/), если у вас его нет. Apple ID необходим для установки приложения Xcode и входа в него.

2.  Загрузите и установите Xcode на странице [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/) и добавьте ваш идентификатор Apple ID, как описано в разделе [Добавление учетной записи для Xcode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (apple.com).

3.  Загрузите и установите Visual Studio для Mac, следуя указаниям в статье [Установка и настройка Visual Studio для Mac](/visualstudio/mac/installation).

4.  После завершения установки Xamarin на компьютерах Mac и Windows следуйте инструкциям в статье [Подключение к Mac](/xamarin/ios/get-started/installation/windows/connecting-to-mac/), чтобы обеспечить возможность работы с iOS и Mac из Visual Studio на компьютере под управлением Windows.

Оба компьютера должны находиться в одной локальной сети.
