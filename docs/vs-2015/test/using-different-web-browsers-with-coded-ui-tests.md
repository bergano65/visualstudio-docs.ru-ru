---
title: Использование различных веб-браузеров в закодированных тестах пользовательского интерфейса | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: a859595f-6517-43f2-9d61-c706cb55a388
caps.latest.revision: 25
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5234dddad13ccb52cc653a68ad1c35370a4eae18
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586337"
---
# <a name="using-different-web-browsers-with-coded-ui-tests"></a>Использование различных веб-браузеров в закодированных тестах пользовательского интерфейса
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Закодированные тесты пользовательского интерфейса могут автоматизировать процесс тестирования веб-приложений путем записи ваших тестов с помощью Internet Explorer. После этого вы сможете настраивать и воспроизводить свои тесты с помощью Internet Explorer или других типов браузеров, поддерживаемых данными веб-приложениями.

 **Требования**

- Visual Studio Enterprise

- Операционные системы:

  - Microsoft Windows 7

  - Microsoft Windows 8

  - Microsoft Windows Server 2008 R2 с пакетом обновления 1 (SP1)

- Версии веб-браузера:

  - Windows Internet Explorer 9

  - Windows Internet Explorer 10

  - Сведения о поддерживаемых версиях Mozilla Firefox и Google Chrome см. [здесь](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting)

- Установите [компоненты Selenium для выполнения закодированных тестов пользовательского интерфейса в различных браузерах](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting).

  **Что поддерживается во всех веб-браузерах?**

- [Добавление пользовательского кода для управления компонентами](https://devblogs.microsoft.com/devops/coded-ui-test-configuring-search-properties-while-recording-on-internet-explorer/), такими как свойства, поиск и ожидающие объекты воспроизведения.

- Всплывающие окна и диалоговые окна

- [Выполнение базового JavaScript без возвращаемого типа](https://devblogs.microsoft.com/devops/introducing-javascript-execution-on-internetexplorer-and-crossbrowser-in-coded-ui-test/)

- Надежный поиск (с помощью интеллектуального сопоставления) и [повышенная производительность](https://devblogs.microsoft.com/devops/guidelines-on-improving-performance-of-coded-ui-test-playback/)

## <a name="why-should-i-use-coded-ui-tests-across-multiple-web-browser-types"></a>Зачем нужно использовать закодированные тесты пользовательского интерфейса в нескольких типах веб-браузеров?
 При тестировании веб-приложения с помощью различных типов веб-браузеров рекомендуется эмулировать взаимодействие с пользовательским интерфейсом для пользователей, которые могут запускать приложение в различных браузерах. Например, приложение может включать элемент управления или код в Internet Explorer, который несовместим с другими веб-браузерами. Выполнив закодированные тесты пользовательского интерфейса с другими браузерами, можно найти и исправить любые проблемы, прежде чем они повлияют на работу клиентов.

## <a name="how-do-i-record-and-play-back-coded-ui-tests-on-web-applications-using-the-supported-web-browsers"></a>Инструкции по записи и воспроизведению закодированных тестов пользовательского интерфейса для веб-приложений с использованием поддерживаемых веб-браузеров
 **Запись.** Для записи теста веб-приложений с помощью Internet Explorer необходимо использовать построитель закодированных тестов пользовательского интерфейса. При необходимости можно добавить код проверки и пользовательский код для тестируемых элементов управления с помощью предопределенного набора свойств, как это обычно происходит в случае закодированных тестов пользовательского интерфейса. Дополнительные сведения см. в разделе [Использование модели автоматизации пользовательского интерфейса для тестирования кода](../test/use-ui-automation-to-test-your-code.md).

> [!NOTE]
> Невозможно записать закодированные тесты пользовательского интерфейса с помощью веб-браузеров Google Chrome или Mozilla Firefox.

 **Воспроизведение с помощью Internet Explorer.** Если браузер не указан явно, тесты будут выполняться в Internet Explorer по умолчанию. Можно явно указать браузер для использования, задав свойство **BrowserWindow.CurrentBrowser** в тестовом коде. Для использования Internet Explorer это свойство должно иметь значение **IE** или **Internet Explorer**.

 **Воспроизведение в веб-браузере, отличном от Internet Explorer.** Для воспроизведения в веб-браузере, отличном от Internet Explorer, измените значение свойства BrowserWindow.CurrentBrowser в тестовом коде на **Firefox** или **Chrome**.

 Для воспроизведения тестов в веб-браузере, отличном от Internet Explorer, необходимо установить **компоненты Selenium для выполнения закодированных тестов пользовательского интерфейса в различных браузерах**.

#### <a name="installing-selenium-components"></a>Установка компонентов Selenium

1. В меню **Сервис** щелкните **Расширения и обновления**.

2. В диалоговом окне "Расширения и обновления" выполните поиск `Selenium components for Cross Browser Testing`.

3. Выберите расширение и нажмите кнопку **Скачать**.

   > [!TIP]
   > Кроме того, компоненты Selenium для выполнения закодированных тестов пользовательского интерфейса можно скачать [здесь](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting).

   Дополнительные сведения о создании и использовании закодированных тестов пользовательского интерфейса см. в разделе [Создание закодированных тестов пользовательского интерфейса](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).

### <a name="enable-debugging"></a>Включение отладки
 Чтобы включить отладку веб-приложения, необходимо указать следующие параметры конфигурации.

1. Включить только мой код:

    1. В меню **Сервис** выберите **Параметры** и затем **Отладка**.

    2. Выберите **Включить только мой код**.

2. Отключить исключения CLR:

    1. В меню **Отладка** выберите **Исключения**.

    2. В поле **Исключения среды CLR** снимите флажок **Не обработанное пользовательским кодом**.

## <a name="i-dont-see-the-option-to-change-browserwindowcurrentbrowser-in-the-coded-ui-test"></a><a name="generate"></a> *Я не вижу, как изменить параметр BrowserWindow.CurrentBrowser в закодированном тесте пользовательского интерфейса.*
 Возможно, вы используете версию [!INCLUDE[vs2011_first](../includes/vs2011-first-md.md)], которая не поддерживает закодированные тесты пользовательского интерфейса в различных веб-браузерах. Чтобы использовать такие закодированные тесты пользовательского интерфейса, необходимо использовать Visual Studio Enterprise.

 *Что еще мне нужно знать?*
 **Примечания**

- ![Предварительное требование предварительное](../test/media/prereq.png "Prereq") Веб-браузер Apple Safari не поддерживается.

- ![Предварительное требование предварительное](../test/media/prereq.png "Prereq") Действие запуска веб-браузера должно быть частью закодированного теста пользовательского интерфейса.

   Если веб-браузер уже открыт и в нем требуется выполнить действия, воспроизведение завершится ошибкой, если используется не Internet Explorer. Поэтому рекомендуется включить запуск веб-браузера в закодированные тесты пользовательского интерфейса.

- ![Предварительное требование предварительное](../test/media/prereq.png "Prereq") Автоматизация действий пользовательского интерфейса, основанных на браузерах, таких как максимизация, сворачивания и восстановление, не поддерживается.

  **"Советы"**

- ![Совет](../test/media/tip.png "Подсказка") Можно настроить вывод для включения снимков экрана в закодированные журналы пользовательского интерфейса. Для этого необходимо задать некоторые параметры конфигурации в файле QTAgent32.exe.config. По умолчанию этот файл устанавливается в следующую папку:

   **C:\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE**

   Задайте следующие значения:

  - `EqtTraceLevel` в разделе `system.diagnostics`.

  - `<add name="EqtTraceLevel" value="4" />`

     Если задать значение равным 3 или выше, снимки экрана будут создаваться для каждого действия. Если значение равно 1 или 2, снимки экрана создаются только для ошибочных действий.

    Дополнительные сведения см. в разделе [Анализ закодированных тестов пользовательского интерфейса с помощью журналов закодированных тестов пользовательского интерфейса](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).

## <a name="external-resources"></a>Внешние ресурсы

### <a name="videos"></a>Видео
 [Запись в IE и воспроизведение в любом браузере](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!183&authkey=!ANqaLtCZbtJrImU)

 [Создание тестов для различных браузеров с помощью построителя закодированных тестов пользовательского интерфейса](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!184&authkey=!AKG8CSow_qmeTq8)

 [Создание тестов для различных браузеров с помощью простой кодировки вручную без карты пользовательского интерфейса](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!186&authkey=!AJaEvxJnsefyAT4)

 [Последовательный запуск тестов для различных браузеров в различных браузерах](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!187&authkey=!ADI8eCQkxHnpOR8)

 [Устранение неполадок в случае сбоев тестов для различных браузеров](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!182&authkey=!AEpS48i295B49FI)

### <a name="guidance"></a>Руководство
 [Тестирование непрерывной доставки с Visual Studio 2012 — глава 2. Модульное тестирование. Внутреннее тестирование](https://msdn.microsoft.com/library/jj159340.aspx)

 [Тестирование непрерывной поставки с помощью Visual Studio 2012 – Глава 5. Автоматизация системных тестов](https://msdn.microsoft.com/library/jj159335.aspx)

### <a name="faq"></a>часто задаваемые вопросы
 [Часто задаваемые вопросы о закодированных тестах пользовательского интерфейса. Часть 1](https://docs.microsoft.com/archive/blogs/mathew_aniyan/content-index-for-coded-ui-test)

 [Часто задаваемые вопросы о закодированных тестах пользовательского интерфейса. Часть 2](https://social.msdn.microsoft.com/Forums/en-US/vsautotest/thread/3a74dd2c-cef8-4923-abbf-7a91f489e6c4)

### <a name="forum"></a>Форум
 [Тестирование автоматизации пользовательского интерфейса в Visual Studio (включает Coded UI)](https://social.msdn.microsoft.com/Forums/en-US/vsautotest)

## <a name="see-also"></a>См. также
 [Использование модели автоматизации пользовательского интерфейса для тестирования поддерживаемых в коде](../test/use-ui-automation-to-test-your-code.md) [конфигураций и платформ для ЗАКОДИРОВАННЫХ тестов пользовательского интерфейса и записей действий](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md) [Анализ закодированных тестов пользовательского интерфейса с помощью журналов закодированных тестов пользовательского](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md) интерфейса
