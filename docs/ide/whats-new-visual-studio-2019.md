---
title: Новые возможности Visual Studio 2019
titleSuffix: ''
description: Сведения о новых возможностях Visual Studio 2019.
ms.date: 04/04/2019
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 00bec66b-bcee-46f5-91d9-f73a2b469744
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 25a7f5f0e53518e9beb4b509ab27ae4de0f28fa7
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018159"
---
# <a name="whats-new-in-visual-studio-2019"></a>Новые возможности Visual Studio 2019

**Обновлено для [выпуска 16.0](/visualstudio/releases/2019/release-notes/)**

>[!div class="button"]
>[Скачивание Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)

С помощью Visual Studio 2019 г. вы получите лучшие в своем классе средства и службы для любого разработчика, любого приложения и любой платформы. Независимо от того, сколько времени вы уже используете Visual Studio, в этой новой версии вы найдете много интересного для себя.

Обзор новых возможностей:

* **[Разработка.](#develop)** Сосредоточьтесь на главном и повышайте продуктивность благодаря оптимизированной производительности, возможности мгновенной очистки кода и более точным результатам поиска.
* **[Совместная работа.](#collaborate)** Воспользуйтесь возможностями совместной работы в рамках рабочего процесса на базе облака, функциями редактирования и отладки, а также рецензирования кода прямо в Visual Studio.
* **[Отладка.](#debug)** Выделяйте определенные значения и переходите к ним; оптимизируйте использование памяти и создавайте автоматические моментальные снимки при выполнении вашего приложения.

Полный список новых возможностей в этой версии см. в [заметках о выпуске](/visualstudio/releases/2019/release-notes/). 

## <a name="develop"></a>Разработка

Экономьте время с помощью новых функций.
<br><br>
> [!VIDEO https://www.youtube.com/embed/n5sJ4EewKGk]

### <a name="improved-search"></a>Улучшенный поиск

Новый интерфейс поиска, ранее называвшийся "Быстрый запуск", стал быстрее и эффективнее. Теперь результаты поиска отображаются динамически при вводе запроса. Результаты поиска часто включают сочетания клавиш для команд, что упрощает их запоминание для использования в будущем.

   ![Анимация нового интерфейса поиска в Visual Studio 2019](media/vs-2019/new-search-feature.gif)

Новая логика поиска нечетких соответствий поможет вам найти все, что вам требуется, независимо от наличия опечаток. Новая функция поиска упрощает поиск команд, параметров, документации и многих других полезных вещей.

### <a name="refactorings"></a>Рефакторинг

Новые функции рефакторинга C# помогают упорядочить код. Быстро вызывайте операции рефакторинга, нажав клавиши **CTRL+.** и выбрав требуемое действие. 

   ![Анимация нового интерфейса рефакторинга в Visual Studio 2019](media/vs-2019/refactorings.gif)

Мы добавили много новых функций рефакторинга, включая возможность заключать параметры метода в оболочку.

### <a name="intellicode"></a>IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) — это расширение, которое повышает эффективность разработки программного обеспечения с помощью искусственного интеллекта (ИИ). Для создания рекомендаций IntelliCode анализирует 2000 проектов с открытым кодом на GitHub (&mdash;каждый из которых имеет более 100 звезд&mdash;).

 ![Анимация IntelliCode в Visual Studio 2019](media/vs-2019/IntelliCode.gif)

Ниже приведено несколько примеров того, как Visual Studio IntelliCode может помочь повысить производительность:

* обеспечивает контекстно зависимое завершение кода;
* помогает разработчикам придерживаться шаблонов и стилей написания кода в команде;
* выполняет поиск трудновыявляемых ошибок в коде;
* при проверке обращает внимание на те участки кода, которые действительно требуют проверки.

Изначально, в первой предварительной версии расширения IntelliCode для Visual Studio, поддерживался только язык C#. Теперь мы добавили поддержку C++ и XAML в Visual Studio.

А если вы используете C#, мы также добавили возможность обучения пользовательской модели на основе собственного кода.

Подробнее об IntelliCode см. в записи блога, посвященной [оптимизации работы с Visual Studio IntelliCode](https://devblogs.microsoft.com/visualstudio/code-more-scroll-less-with-visual-studio-intellicode/). 

### <a name="code-cleanup"></a>Очистка кода

Новый индикатор работоспособности документа дополнен новой командой очистки кода. Эту новую команду можно использовать для определения и устранения предупреждений и предложений одним нажатием кнопки.

Функция очистки выполнит форматирование кода и применит исправления согласно [текущим параметрам](code-styles-and-quick-actions.md), [файлам editorconfig](create-portable-custom-editor-options.md) или [анализаторам Roslyn](../code-quality/roslyn-analyzers-overview.md).

   ![Снимок экрана: новое средство очистки кода в Visual Studio 2019](media/vs-2019/code-cleanup-profile.png)

Вы также можете сохранять наборы исправлений как профили. Например, если у вас есть небольшой набор целевых исправлений, которые часто применяются при написании кода, а также другой полный набор исправлений, которые применяются перед проверкой кода, вы можете настроить разные профили для решения этих задач.

   ![Снимок экрана: новое средство очистки кода в Visual Studio 2019](media/vs-2019/code-cleanup-profile-configure.png)

## <a name="collaborate"></a>Совместная работа

Объединяйте усилия для решения проблем.
<br><br>
> [!VIDEO https://www.youtube.com/embed/dKLJsiK1QU8]

### <a name="cloud-first-workflow"></a>Рабочий процесс на базе облака

Первое, что вы заметите при открытии Visual Studio 2019, — новое окно запуска.

   ![Снимок экрана: новое окно запуска в Visual Studio 2019](media/vs-2019/start-window-dark.png)

С помощью этого окна запуска можно быстро перейти к коду несколькими способами. Мы включили возможность клонирования или извлечения кода из репозитория.  

   ![Анимация нового интерфейса Git-first в Visual Studio 2019](media/vs-2019/git-first.gif)

Окно запуска также позволяет открыть проект, решение и локальную папку или создать новый проект.

Дополнительные сведения см. в записи блога [Приступая к написанию кода: Как мы разработали новое окно запуска Visual Studio](https://devblogs.microsoft.com/visualstudio/get-to-code-how-we-designed-the-new-visual-studio-start-window/).

### <a name="live-share"></a>Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) — это служба для разработчиков, которая позволяет предоставить базу кода и соответствующий контекст коллеге и обеспечить двунаправленное взаимодействие непосредственно из среды Visual Studio. Благодаря Live Share коллега может легко и безопасно просматривать, изменять и отлаживать проект, предоставленный вами для общего доступа.

В Visual Studio 2019 эта служба устанавливается по умолчанию.

![Анимация: возможности совместной работы Live Share в Visual Studio 2019](media/vs-2019/live-share.gif)

Дополнительные сведения см. в разделе [Visual Studio Live Share для проверки кода в режиме реального времени и интерактивного обучения](https://devblogs.microsoft.com/visualstudio/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) записи блога и [Live Share, теперь включены с помощью Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/live-share-now-included-with-visual-studio-2019/) записи блога.

### <a name="integrated-code-reviews"></a>Интегрированная проверка кода

Мы представляем новое расширение, которое можно скачать для использования в Visual Studio 2019. С помощью этого нового расширения можно просматривать, запускать и даже выполнять отладку запросов на вытягивание, не выходя из Visual Studio. Мы включили поддержку кода в репозиториях GitHub и DevOps в Azure.

   ![Снимок экрана: новое окно запуска в Visual Studio 2019](media/vs-2019/pr-experience.png)

Чтобы приступить к работе, скачайте расширение [Запросы на вытягивание для Visual Studio](https://aka.ms/pr4vs) из Visual Studio Marketplace.

## <a name="debug"></a>Отладка

Сосредотачивайтесь на важном благодаря точному определению целевых объектов.
<br><br>
> [!VIDEO https://www.youtube.com/embed/hr72Fs8n_9c]

### <a name="performance-gains"></a>Повышение производительности

Мы адаптировали уникальную функцию точек останова в данных в C++ и адаптировали их для приложений .NET Core.

   ![Анимация: отладочные точки останова в данных в Visual Studio 2019](media/vs-2019/debug-data-breakpoints.gif)

Поэтому независимо от рабочей платформы (C++ или .NET Core) использование точек останова в данных может быть хорошей альтернативой размещению обычных точек останова. Точки останова в данных также отлично подходят для таких сценариев, как поиск, когда глобальные объекты изменяются, а также добавляются в список или удаляются из него. 

Благодаря тому, что в Visual Studio 2019 обработка символов является внепроцессной, разработчики крупных приложений C++могут выполнять отладку приложений, не испытывая проблем, связанных с нехваткой памяти.

### <a name="search-while-debugging"></a>Поиск во время отладки

Наверное, вам приходилось искать одну строку из набора значений в окне контрольных значений. В Visual Studio 2019 мы добавили поиск в окнах "Контрольные значения", "Локальные" и "Видимые", чтобы помочь вам быстрее находить нужные объекты и значения.

   ![Анимация: окно поиска по время отладки в Visual Studio 2019](media/vs-2019/debug-window-search.gif)

Также можно выбрать формат отображения значения в окнах "Контрольные значения", "Локальные" и "Видимые".  Дважды щелкните один из элементов в любом окне и добавьте запятую (",") для доступа к раскрывающемуся списку спецификаторов формата, каждый из которых включает описание предполагаемого результата.

   ![Новое окно контрольных значений и функция форматирования значений в Visual Studio 2019](media/search-watch-window.png)

Дополнительные сведения см. в записи блога [Улучшения в Visual Studio 2019: поиск объектов и свойств в окне контрольных значений, "Видимые" и "Локальные"](https://devblogs.microsoft.com/visualstudio/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/).

### <a name="snapshot-debugger"></a>Отладчик моментальных снимков

Получайте моментальные снимки при выполнении приложения в облаке, чтобы в точности знать, что происходит. (Эта возможность доступна в только в Visual Studio Enterprise.)

   ![Анимация: Snapshot Debugger в Visual Studio 2019 Enterprise](media/vs-2019/snapshot-debugger.gif)

Мы добавили поддержку целевых приложений ASP.NET (приложения Core и классические приложения), которые выполняются на виртуальных машинах Azure. Также мы добавили поддержку приложений, которые выполняются в Службе Azure Kubernetes. Средство Snapshot Debugger позволяет значительно сократить затраты времени на устранение проблем, возникающих в рабочих средах.

Дополнительные сведения см. в статье [Отладка интерактивных приложений ASP.NET Azure с использованием Snapshot Debugger](../debugger/debug-live-azure-applications.md) и записи блога [Introducing Time Travel Debugging for Visual Studio Enterprise 2019](https://devblogs.microsoft.com/visualstudio/introducing-time-travel-debugging-for-visual-studio-enterprise-2019/) (Представление отладки перехода по времени для Visual Studio Enterprise 2019).

## <a name="give-us-feedback"></a>Обратная связь

Зачем отправлять отзыв группе Visual Studio? Потому что мы серьезно относимся к отзывам клиентов. Они влияют на многие наши действия.

* Если вы хотите внести предложение по улучшению Visual Studio, это можно сделать с помощью средства [Отправить предложение](talk-to-us.md#i-want-to-make-a-suggestion-about-visual-studio-features).

* В случае зависания, сбоя или других проблем с производительностью вы можете предоставить нам шаги для воспроизведения и вспомогательные файлы с помощью средства [Сообщить о проблеме](talk-to-us.md#i-want-to-report-a-problem-with-visual-studio).

## <a name="see-also"></a>См. также

* [Объявление о выпуске Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/visual-studio-2019-code-faster-work-smarter-create-the-future/)
* [Заметки о выпуске Visual Studio 2019](/visualstudio/releases/2019/release-notes/)
* [Новые возможности пакета SDK для Visual Studio 2019](../extensibility/whats-new-visual-studio-2019-sdk.md)
* [Выпущена версия Visual Studio 2019 для Mac](https://devblogs.microsoft.com/visualstudio/visual-studio-2019-for-mac-is-now-available/)
* [Конференция Microsoft Connect(); 2018](https://www.microsoft.com/connectevent)
