---
title: Знакомство с Visual Studio для Mac
description: В этой статье рассматриваются возможности Visual Studio для Mac
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.assetid: 3A130EC1-DD8C-4125-9034-B08D7AF7EA65
ms.openlocfilehash: 738964deed9aa1e51d5a6e4788879bc3165284a7
ms.sourcegitcommit: 522ba712c0d625e51352506146b0556414681964
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2018
ms.locfileid: "37889889"
---
# <a name="introducing-visual-studio-for-mac"></a>Знакомство с Visual Studio для Mac

Visual Studio для Mac — это современная и сложная интегрированная среда разработки (IDE), включающая множество компонентов для создания мобильных, классических и веб-приложений. Она поддерживает следующие типы разработки:

* мобильных приложений с .NET для Android, iOS, tvOS и watchOS;
* классических приложений Mac;
* Приложения .NET Core
* веб-приложений ASP.NET Core;
* Кроссплатформенные игры Unity

Среда включает такие возможности, как полнофункциональный редактор, возможности отладки, встроенную интеграцию с платформами iOS, Mac и Android, а также интегрированную систему управления версиями.

В этой статье рассмотрены различные аспекты Visual Studio для Mac и представлены мощные функции для создания кроссплатформенных приложений.

## <a name="installation"></a>Установка

Скачайте и установите Visual Studio для Mac, следуя указаниям руководства по [установке](installation.md).

## <a name="language-support"></a>Языковая поддержка

Visual Studio для Mac по умолчанию поддерживает разработку на C# и F#.

### <a name="c"></a>C#

C# — самый часто используемый язык для создания кроссплатформенных приложений в Visual Studio для Mac. В среду входит полная поддержка всех возможностей C# 7.

### <a name="f"></a>F#

F# — это строго типизированный функциональный язык программирования, разработанный для .NET. Он доступен в качестве языка программирования пользователям Visual Studio для Mac на Android, Mac и iOS. Дополнительные сведения об использовании F# и созданные на нем примеры см. в руководствах по [F#](https://developer.xamarin.com/guides/cross-platform/fsharp/).

## <a name="platform-support"></a>Поддержка платформ

## <a name="net-core"></a>.NET Core

[.NET Core](https://www.microsoft.com/net/core#macos) — это платформа для создания приложений, работающих в ОС Windows, Linux и Mac. Visual Studio для Mac поддерживает загрузку, создание, запуск и отладку проектов .NET Core. 

Для запуска проектов .NET Core следует скачать и установить пакет SDK для .NET Core.

.NET Core поддерживает указанные далее компоненты.

* C# и F # IntelliSense.
* Шаблоны проектов .NET Core для консоли, библиотеки и веб-приложений.
* Полная поддержка отладки, включая точки останова, стек вызовов, окно контрольных значений и т. д.
* Восстановление NuGet PackageReferences и восстановление на основе MSBuild.
* Встроенная поддержка модульного тестирования для запуска и отладки тестов на платформе тестирования Visual Studio, входящей в пакет SDK для .NET Core.
* Миграция со старого формата project.json.

Чтобы начать работу, ознакомьтесь с [практическим лабораторным занятием](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started) по веб-приложениям ASP.NET Core.

## <a name="xamarin"></a>Xamarin

Первоклассная поддержка [Xamarin](https://developer.xamarin.com/) позволяет разрабатывать эффективные собственные интерфейсы для Android, macOS, iOS, tvOS и watchOS. Кроссплатформенные приложения Xamarin.Forms позволяют использовать код пользовательского интерфейса на основе XAML в Android, iOS и macOS без ограничения доступ к встроенной функциональности.

Чтобы начать работу, ознакомьтесь с [практическим лабораторным занятием](https://github.com/Microsoft/vs4mac-labs/tree/master/Mobile/Getting-Started) по мобильным приложениям.

### <a name="android"></a>Android

Visual Studio имеет свой встроенный диспетчер пакета SDK для Android.

Visual Studio для Mac включает собственный конструктор для приложений Android, который работает с файлами `.axml` из Android и поддерживает визуальное создание пользовательских интерфейсов. Visual Studio для Mac открывает эти файлы в Android Designer, как показано на следующем рисунке:

![Конструктор пользовательского интерфейса Android](media/intro-image31.png)

См. [обзор Android Designer](https://developer.xamarin.com/Android/Guides/User_Interface/Designer_Overview) для получения дополнительных сведений.

### <a name="ios"></a>iOS

Конструктор iOS полностью интегрирован с Visual Studio для Mac и позволяет визуально редактировать XIB-файлы и файлы раскадровки для создания пользовательских интерфейсов и переходов iOS, tvOS и WatchOS. Весь пользовательский интерфейс можно создавать с помощью перетаскивания между панелью элементов и областью конструктора; при этом предлагается интуитивный подход к обработке событий. Конструктор iOS также поддерживает [пользовательские элементы управления](https://developer.xamarin.com/guides/ios/user_interface/designer/ios_designable_controls_overview/) с возможностью их отрисовки во время разработки.

![Конструктор раскадровки iOS](media/intro-image30.png)

Дополнительные сведения об использовании конструктора iOS см. в посвященных [конструктору](https://developer.xamarin.com/guides/ios/user_interface/designer) документах.

### <a name="mac"></a>Mac

Xamarin включает собственные привязки к API для Mac, позволяющие создавать эффектно выглядящие Mac-приложения.

Дополнительные сведения о написании приложений Mac с помощью Visual Studio для Mac см. в документации по [Xamarin.Mac](https://developer.xamarin.com/guides/#mac).

## <a name="gaming"></a>Игры

Visual Studio для Mac поддерживает разработку кроссплатформенных игр с использованием Unity 5.6.1.

Чтобы начать работу, ознакомьтесь с [практическим лабораторным занятием](https://github.com/Microsoft/vs4mac-labs/tree/master/Unity/Getting-Started) по Unity.

## <a name="enterprise-features"></a>Функции Enterprise

> [!Note]
> Эти продукты можно использовать только с подпиской Visual Studio Enterprise.

### <a name="profiler"></a>профилировщик

В Xamarin Profiler доступно три инструмента для профилирования. В руководстве [Introduction to the Xamarin Profiler](https://developer.xamarin.com/guides/cross-platform/deployment,_testing,_and_metrics/xamarin-profiler/) (Знакомство с Xamarin Profiler) рассказывается, что измеряют эти инструменты и как они анализируют приложение, а также поясняется значение данных, представленных на каждом экране.

### <a name="inspector"></a>Inspector

Xamarin Inspector предлагает интерактивную консоль C# с пользовательскими инструментами. Ее можно использовать в отладке и диагностике работающих приложений, в качестве средства обучения, инструмента для создания документации и для экспериментов.

![Xamarin Inspector](media/intro-inspector.png)

Это полнофункциональная консоль C#, которая представляет собой автономное приложение для программирования под различные платформы (Android, iOS, Mac и Windows) и интегрируется с рабочим процессом отладки вашей IDE. 

Дополнительные сведения см. в руководстве по [Xamarin Inspector](https://developer.xamarin.com/guides/cross-platform/inspector/).

## <a name="next-steps"></a>Следующие шаги

* **Получите общее представление**. Чтобы получить общие сведения о многих основных функциях Visual Studio для Mac, просмотрите [Обзор интегрированной среды разработки](ide-tour.md) Visual Studio для Mac.
* **Установка**. Чтобы узнать, как скачать и установить Visual Studio, см. руководство по [установке](installation.md).
* **Учебники по Xamarin**. Чтобы узнать больше о разработке кода с помощью Xamarin, зайдите в [Центр разработчика](https://developer.xamarin.com) Xamarin.
* **Видеоролики**. Чтобы получить дополнительные сведения о других функциях и аспектах Visual Studio для Mac, посмотрите видеоролики на веб-сайте [Xamarin University](https://university.xamarin.com).
* **Практические лабораторные занятия**. Чтобы начать работу с разнообразными рабочими нагрузками, доступными в Visual Studio для Mac, ознакомьтесь с [практическими лабораторными занятиями](https://github.com/Microsoft/vs4mac-labs).
