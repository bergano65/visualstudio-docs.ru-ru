---
title: Новые возможности Visual Studio 2019
titleSuffix: ''
description: Сведения о новых возможностях Visual Studio 2019.
ms.date: 02/14/2019
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 00bec66b-bcee-46f5-91d9-f73a2b469744
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 41582f9f27b16a41c3ef10196f3cd29323579b4b
ms.sourcegitcommit: 845442e2b515c3ca1e4e47b46cc1cef4df4f08d8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/20/2019
ms.locfileid: "56450260"
---
# <a name="whats-new-in-visual-studio-2019-preview"></a>Новые возможности предварительной версии Visual Studio 2019

**Обновлено для [выпуска предварительной версии 3](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017)**

>[!div class="button"]
>[Скачать предварительную версию](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019+preview)

Предварительная версия Visual Studio 2019 включает ряд общих улучшений, а также новые функции для оптимизации производительности труда разработчиков и совместной работы. Разработчики, которые впервые работают с Visual Studio, и те, кто использует эту среду годами, смогут воспользоваться ее преимуществами для всех аспектов жизненного цикла разработки&mdash;: от упрощенного создания проектов и управления работоспособностью кода до рабочих процессов совместной работы при участии в командной разработке и разработке открытого кода.<br/><br/>

>[!VIDEO https://channel9.msdn.com/Events/Connect/Microsoft-Connect--2018/D190/player]

Ниже приведен общий обзор возможностей Visual Studio.

* **[Личная и командная производительность](#personal-and-team-productivity)**. Оптимальная среда работы для всех пользователей.
* **[Поддержка разработки современных приложений](#modern-development-support)**. Поддержка текущих проектов и будущих решений.
* **[Непрерывные инновации](#continuous-innovation)**. Эффективное создание кода с интеллектуальной облачной поддержкой.

> [!NOTE]
> Полный список новых возможностей и функций предварительной версии Visual Studio 2019 см. в [заметках о выпуске](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017).

## <a name="personal-and-team-productivity"></a>Личная и командная производительность

Улучшениям производительности мы уделяем огромное внимание в каждом выпуске Visual Studio, однако в данном выпуске мы ориентировались на повышение производительности вашего труда. И вот что мы придумали.

### <a name="new-start-window"></a>Новое окно запуска

Первое, что вы заметите при открытии Visual Studio 2019, — новое окно запуска.

   ![Новые окна запуска в Visual Studio 2019](media/start-window.png)

Новое окно запуска дает возможность клонировать или извлечь код, открыть проект или решение, открыть локальную папку или создать новый проект. Эти возможности, представленные в виде простого диалогового окна, помогают как начинающим, так и опытным пользователям Visual Studio быстро перейти к коду.

Дополнительные сведения см. в записи блога [Get to code: How we designed the new Visual Studio start window](https://devblogs.microsoft.com/visualstudio/get-to-code-how-we-designed-the-new-visual-studio-start-window/) (Приступая к написанию кода. Как мы разработали новое окно запуска Visual Studio).

### <a name="better-search"></a>Улучшенный поиск

Новый интерфейс поиска, ранее называвшийся "Быстрый запуск", стал быстрее и эффективнее. Теперь результаты поиска отображаются динамически при вводе запроса. Результаты поиска включают сочетания клавиш для команд, что упрощает их запоминание для использования в будущем.

   ![Новая функция поиска в Visual Studio 2019](media/search-feature.png)

Новая функция поиска упрощает поиск команд, параметров, документации и многих других полезных вещей.

### <a name="one-click-code-cleanup"></a>Очистка кода одним щелчком

Новый индикатор работоспособности документа дополнен новой командой очистки кода. Эту новую команду можно использовать для определения и устранения предупреждений и предложений одним нажатием кнопки.

   ![Новая функция очистки кода в Visual Studio 2019](media/code-cleanup.png)

Функция очистки выполнит форматирование кода и применит исправления согласно [текущим параметрам](code-styles-and-quick-actions.md), [файлам editorconfig](create-portable-custom-editor-options.md) или [анализаторам Roslyn](../code-quality/roslyn-analyzers-overview.md).

### <a name="debugger-improvements"></a>Усовершенствования отладчика

#### <a name="search-within-a-watch-window-and-format-watch-values"></a>Поиск в окне контрольных значений и форматирование контрольных значений

Наверное, вам приходилось искать одну строку из набора значений в окне контрольных значений. В предварительной версии Visual Studio 2019 мы добавили поиск в окнах "Контрольные значения", "Локальные" и "Видимые", чтобы помочь вам быстрее находить нужные объекты и значения.

Также можно выбрать формат отображения значения в окнах "Контрольные значения", "Локальные" и "Видимые".  Дважды щелкните один из элементов в любом окне и добавьте запятую (",") для доступа к раскрывающемуся списку спецификаторов формата, каждый из которых включает описание предполагаемого результата.

   ![Новое окно контрольных значений и функция форматирования значений в Visual Studio 2019](media/search-watch-window.png)

Дополнительные сведения см. в записи блога [Улучшения в Visual Studio 2019: поиск объектов и свойств в окне контрольных значений, "Видимые" и "Локальные"](https://devblogs.microsoft.com/visualstudio/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/).

### <a name="visual-studio-live-share"></a>Visual Studio Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) — это служба для разработчиков, которая позволяет предоставить базу кода и соответствующий контекст коллеге и обеспечить двунаправленное взаимодействие непосредственно из среды Visual Studio. Благодаря Live Share коллега может легко и безопасно просматривать, изменять и отлаживать проект, предоставленный вами для общего доступа.

В предварительной версии Visual Studio 2019 эта служба устанавливается по умолчанию.

![Анимированный GIF-файл, демонстрирующий возможности службы Live Share в Visual Studio 2019](media/live-share-collaboration.gif)

Дополнительные сведения см. в записи блога [Visual Studio Live Share for real-time code reviews and interactive education](https://devblogs.microsoft.com/visualstudio/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) (Visual Studio Live Share: проверка кода в режиме реального времени и интерактивное обучение).

## <a name="modern-development-support"></a>Поддержка разработки современных приложений

### <a name="manage-pull-requests-prs-from-the-ide"></a>Управление запросами на вытягивание в интегрированной среде разработки

Мы представляем новое расширение, которое можно скачать для использования в предварительной версии Visual Studio 2019. С помощью этого нового расширения можно просматривать, запускать и даже выполнять отладку запросов на вытягивание, не выходя из интегрированной среды разработки Visual Studio [(IDE)](../get-started/visual-studio-ide.md). На данный момент поддерживается код в репозиториях Azure, однако мы намерены реализовать поддержку GitHub и повысить общую эффективность.

Чтобы приступить к работе, скачайте расширение [Запросы на вытягивание для Visual Studio](https://aka.ms/pr4vs) из Visual Studio Marketplace.

### <a name="develop-with-net-core-3-preview"></a>Разработка с помощью .NET Core 3 (предварительная версия)

Предварительная версия Visual Studio 2019 поддерживает создание приложений [.NET Core 3](https://dotnet.microsoft.com/download/dotnet-core/3.0) для любой платформы. Мы продолжим расширять поддержку и совершенствовать возможности кроссплатформенной разработки C++, а также разработки мобильных приложений .NET для iOS и Android с помощью Xamarin.

   ![Разработка приложений с помощью .NET Core 3 (предварительная версия) в Visual Studio 2019](media/dot-net-core-three-dev.png)

Дополнительные сведения см. на следующих страницах:

* Заметки о выпуске [.NET Core 3 (предварительная версия 1)](https://github.com/dotnet/core/blob/master/release-notes/3.0/preview/3.0.0-preview1.md) и [.NET Core 3 (предварительная версия 2)](https://github.com/dotnet/core/blob/master/release-notes/3.0/preview/3.0.0-preview2.md).
* Записи блога [Announcing .NET Core 3 Preview 1](https://blogs.msdn.microsoft.com/dotnet/2018/12/04/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/) (Объявление о выпуске .NET Core 3, предварительная версия 1) и [Announcing .NET Core 3 Preview 2](https://blogs.msdn.microsoft.com/dotnet/2019/01/29/announcing-net-core-3-preview-2/) (Объявление о выпуске .NET Core 3, предварительная версия 2).

## <a name="continuous-innovation"></a>Непрерывные инновации

### <a name="per-monitor-aware-pma-rendering"></a>Отрисовка, учитывающая параметры монитора (PMA)

Если вы используете мониторы, на которых настроены разные коэффициенты масштабирования отображения, или удаленно подключаетесь к компьютеру, коэффициенты масштабирования отображения которого отличаются от основного устройства, вы можете заметить, что изображение Visual Studio выглядит размытым или отображается с некорректным масштабом.

В выпуске Visual Studio 2019 (предварительная версия) мы делаем первые шаги к реализации в Visual Studio отрисовки, учитывающей параметры монитора (PMA). Мы заложили основу, которая позволит Visual Studio правильно выполнять отрисовку, независимо от используемых коэффициентов масштабирования отображения.

   ![Отрисовка, учитывающая параметры монитора (PMA) в Visual Studio 2019](media/per-monitor-aware-dpi-scaling.png)

Дополнительные сведения см. в записи блога [Better multi-monitor experience with Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/a-better-multi-monitor-experience-with-visual-studio-2019/) (Улучшенная работа с несколькими мониторами в Visual Studio 2019).

### <a name="visual-studio-intellicode"></a>Visual Studio IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) — это расширение, которое повышает эффективность разработки программного обеспечения с помощью искусственного интеллекта (ИИ). Для создания рекомендаций IntelliCode анализирует 2000 проектов с открытым кодом на GitHub (&mdash;каждый из которых имеет более 100 звезд&mdash;).

Ниже приведено несколько примеров того, как Visual Studio IntelliCode может помочь повысить производительность:

* обеспечивает контекстно зависимое завершение кода;
* помогает разработчикам придерживаться шаблонов и стилей написания кода в команде;
* выполняет поиск трудновыявляемых ошибок в коде;
* при проверке обращает внимание на те участки кода, которые действительно требуют проверки.

 ![Пример предложения IntelliSense](media/intellicode-intellisense-suggestion.png)

Изначально, в первой предварительной версии расширения IntelliCode для Visual Studio, поддерживался только язык C#. Теперь мы добавили поддержку C++ и XAML в Visual Studio.

А если вы используете C#, мы также добавили возможность обучения пользовательской модели на основе собственного кода.

Дополнительные сведения см. в записи блога [Visual Studio IntelliCode supports more languages and learns from your code](https://devblogs.microsoft.com/visualstudio/visual-studio-intellicode-supports-more-languages-and-learns-from-your-code/) (Visual Studio IntelliCode поддерживает больше языков и самообучается, анализируя ваш код). Найти дополнительные сведения о расширении и скачать его можно на странице [предварительной версии Visual Studio IntelliCode](https://go.microsoft.com/fwlink/?linkid=872707) на сайте Microsoft DevLabs.

## <a name="give-us-feedback"></a>Обратная связь

Зачем отправлять отзыв группе Visual Studio? Потому что мы серьезно относимся к отзывам клиентов. Они влияют на многие наши действия.

* Если вы хотите внести предложение по улучшению Visual Studio, это можно сделать с помощью средства [Отправить предложение](talk-to-us.md#i-want-to-make-a-suggestion-about-visual-studio-features).

* В случае зависания, сбоя или других проблем с производительностью вы можете предоставить нам шаги для воспроизведения и вспомогательные файлы с помощью средства [Сообщить о проблеме](talk-to-us.md#i-want-to-report-a-problem-with-visual-studio).

## <a name="see-also"></a>См. также

* [Заметки о выпуске Visual Studio 2019](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017)
* [Конференция Microsoft Connect(); 2018](https://www.microsoft.com/connectevent)
* [Новые возможности Visual Studio 2017](whats-new-visual-studio-2017.md)
