---
title: Создание сетевой установки
description: Узнайте, как создать сетевую точку установки для развертывания Visual Studio на предприятии.
ms.date: 08/27/2020
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: b572a6854d505704accd79cc4da2ac4e52c193d6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850180"
---
# <a name="create-a-network-installation-of-visual-studio"></a>Создание сетевой установки Visual Studio

Обычно администратор предприятия создает точку сетевой установки для развертывания на клиентских рабочих станциях. Среда Visual Studio разработана таким образом, чтобы вы могли кэшировать файлы для первоначальной установки вместе со всеми обновлениями продуктов в одну папку. (Этот процесс также известен как _создание макета_.)

Это сделано для того, чтобы клиентские рабочие станции могли использовать то же сетевое расположение для управления установкой, даже если они еще не были обновлены до последнего сервисного обновления.

 > [!NOTE]
 > Если вы используете в организации несколько версий Visual Studio (например, Visual Studio Professional и Visual Studio Enterprise), вам нужно создать отдельную сетевую папку установки для каждого выпуска.

## <a name="download-the-visual-studio-bootstrapper"></a>Скачивание загрузчика Visual Studio

Скачайте файл начального загрузчика для нужного выпуска Visual Studio. Нажмите кнопку **Сохранить** и выберите **Открыть папку**.

::: moniker range="vs-2017"

Сведения о том, как получить начальный загрузчик для Visual Studio 2017, см. на странице скачиваемых материалов [Предыдущие версии Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/).

Исполняемый файл программы установки &mdash; а точнее файл начального загрузчика &mdash; должен иметь одно из перечисленных ниже имен или похожее на него.

| Выпуск | имя_файла |
|-------------|-----------------------|
|Visual Studio Enterprise | **vs_enterprise.exe** |
|Visual Studio Professional | **vs_professional.exe** |
|Visual Studio Build Tools   | **vs_buildtools.exe** |

Другие поддерживаемые начальные загрузчики: **vs_feedbackclient.exe**, **vs_teamexplorer.exe**, **vs_testagent.exe**, **vs_testcontroller.exe** и **vs_testprofessional.exe**.

::: moniker-end

::: moniker range="vs-2019"

Исполняемый файл программы установки &mdash; а точнее файл начального загрузчика &mdash; должен иметь одно из перечисленных ниже имен или похожее на него.

|Выпуск | Скачать|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
|Visual Studio Professional | [**vs_professional.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
| Visual Studio Build Tools   | [**vs_buildtools.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |

Другие поддерживаемые начальные загрузчики: [vs_teamexplorer.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/4026077127d25d33789f3882998266946608d8ada378b6ed7c8fff8c07f3dde2/vs_TeamExplorer.exe), [vs_testagent.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/1383bf8bcda3d0e986a2e42c14114aaea8a7b085d31aa0623c9f70b2bad130e4/vs_TestAgent.exe) и [vs_testcontroller.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/54dcf24b76e7cd9fb8be0ac518a9dfba6daf18fe9b2aa1543411b1cda8820918/vs_TestController.exe).

::: moniker-end

>[!TIP]
>Если вы ранее скачали файл начального загрузчика и хотите проверить его версию, вот как это сделать. В Windows откройте проводник, щелкните правой кнопкой мыши файл начального загрузчика, выберите **Свойства**, перейдите на вкладку **Подробно**, а затем найдите номер в строке **Версия продукта**. Чтобы сопоставить этот номер с выпуском Visual Studio, перейдите на страницу [Номера сборки и даты выпуска Visual Studio](visual-studio-build-numbers-and-release-dates.md).

## <a name="create-an-offline-installation-folder"></a>Создание папки автономной установки

Для выполнения этого действия необходимо подключение к Интернету. Чтобы создать автономную установку со всеми языками и функциями, используйте одну из команд, подобную приведенным в следующих примерах.

   > [!IMPORTANT]
   > Полный макет для языкового стандарта одного языка требует около 35 ГБ дискового пространства для Visual Studio Community и 42 Гб для Visual Studio Enterprise. Для каждого дополнительного [языкового стандарта](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales) требуется около половины указанного количества ГБ. Дополнительные сведения см. в разделе [Настройка сетевого макета](#customize-the-network-layout).
   >
   > [!TIP]
   > Эти команды необходимо выполнять из каталога загрузки. На компьютере с ОС Windows 10 это обычно каталог `C:\Users\<username>\Downloads`.

- Команда для выпуска Visual Studio Enterprise:

  ```vs_enterprise.exe --layout c:\VSLayout```

- Команда для выпуска Visual Studio Professional:

  ```vs_professional.exe --layout c:\VSLayout```

## <a name="modify-the-responsejson-file"></a>Редактирование файла response.json

В файле response.json вы можете задать новые значения по умолчанию, которые будут использоваться при запуске программы установки.  Например, можно настроить файл `response.json` для автоматического выбора конкретного набора рабочих нагрузок. Подробнее см. в статье об [автоматизации установки Visual Studio с помощью файла ответов](automated-installation-with-response-file.md).

Если возникнет проблема с начальным загрузчиком Visual Studio, вызывающим ошибку при связывании с файлом response.json, ознакомьтесь с разделом о сбое анализа идентификатора родительского процесса в статье [Исправление ошибок сети при установке или использовании Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md#error-failed-to-parse-id-from-parent-process), чтобы получить необходимые инструкции.

## <a name="copy-the-layout-to-a-network-share"></a>Копирование макета в общую сетевую папку

Разместите макет на общем сетевом ресурсе, чтобы запускать его с других компьютеров.

В следующем примере используется [xcopy](/windows-server/administration/windows-commands/xcopy/). Можно также использовать [robocopy](/windows-server/administration/windows-commands/robocopy/).

::: moniker range="vs-2017"

Пример.

```cmd
xcopy /e c:\VSLayout \\server\products\VS2017
```

::: moniker-end

::: moniker range="vs-2019"

```cmd
xcopy /e c:\VSLayout \\server\products\VS2019
```

::: moniker-end

> [!IMPORTANT]
> Чтобы предотвратить ошибку, убедитесь, что полный путь макета содержит менее 80 символов.

## <a name="customize-the-network-layout"></a>Настройка сетевого макета

Для сетевого макета можно настроить несколько параметров. Вы можете создать частичный макет, который содержит только определенный набор [языковых стандартов](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales), [рабочих нагрузок, компонентов, рекомендуемых и дополнительных зависимостей](workload-and-component-ids.md). Это может быть полезно, если вы намерены разворачивать на клиентских рабочих станциях только определенное подмножество рабочих нагрузок. Ниже перечислены типичные параметры командной строки для настройки макета.

* `--add` позволяет указать [идентификаторы рабочих нагрузок и компонентов](workload-and-component-ids.md). <br>Если используется параметр `--add`, загружаются только те рабочие нагрузки и компоненты, которые заданы с помощью `--add`.  Если параметр `--add` не используется, загружаются все компоненты и рабочие нагрузки.
* `--includeRecommended` позволяет включить все рекомендованные компоненты для рабочих нагрузок с указанными идентификаторами.
* `--includeOptional` позволяет включить все рекомендованные и дополнительные компоненты для рабочих нагрузок с указанными идентификаторами.
* `--lang` позволяет указать [языковые стандарты](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).

Далее приводятся примеры для создания неполного пользовательского макета.

* Чтобы скачать все рабочие нагрузки и компоненты только для одного языка, выполните:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --lang en-US
    ```

* Чтобы скачать все рабочие нагрузки и компоненты для нескольких языков, выполните:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --lang en-US de-DE ja-JP
    ```

* Чтобы скачать одну рабочую нагрузку для всех языков, выполните:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --includeRecommended
    ```

* А так вы можете скачать две рабочие нагрузки и один дополнительный компонент для трех языков:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP
    ```

* Чтобы загрузить две рабочие нагрузки со всеми рекомендуемыми компонентами:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended
    ```

* Чтобы загрузить две рабочие нагрузки со всеми рекомендуемыми и дополнительными компонентами, выполните следующую команду:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional
    ```

::: moniker range="vs-2017"

### <a name="new-in-version-153"></a>Новые возможности в версии 15.3

::: moniker-end

::: moniker range="vs-2019"

### <a name="save-your-layout-options"></a>Сохранение параметров макета

::: moniker-end

При выполнении команды макета указанные параметры (например, рабочие нагрузки и языки) будут сохранены. Все предыдущие параметры будут включены в последующие команды макета.  Ниже приведен пример макета с одной рабочей нагрузкой только для английского языка.

```cmd
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
```

Чтобы обновить этот макет до более новой версии, не нужно указывать дополнительные параметры командной строки. Предыдущие параметры сохраняются и используются во всех последующих командах макета в этой папке макета.  Следующая команда используется для обновления существующего частичного макета.

```cmd
vs_enterprise.exe --layout c:\VSLayout
```

Здесь также приведен пример добавления дополнительной рабочей нагрузки. В этом случае добавляется рабочая нагрузка Azure и язык локализации.  Теперь в этот макет включены управляемый рабочий стол и Azure.  Для всех этих рабочих нагрузок также включены языковые ресурсы для английского и немецкого языков. Макет обновляется до последней доступной версии.

```cmd
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
```

Если вы хотите обновить существующий макет до полного макета, используйте параметр --all, как показано в следующем примере.

```cmd
vs_enterprise.exe --layout c:\VSLayout --all
```

## <a name="deploy-from-a-network-installation"></a>Развертывание из сетевой установки

Администраторы могут разворачивать Visual Studio на клиентских рабочих станциях в рамках сценария установки. Также пользователи с правами администратора могут запустить программу установки непосредственно из общей сетевой папки, чтобы установить Visual Studio на своем компьютере.

* Пользователи могут выполнить установку, запустив следующую команду: <br>

    ```cmd
    \\server\products\VS\vs_enterprise.exe
    ```

* Администраторы выполняют установку в автоматическом режиме с помощью следующей команды:

    ```cmd
    \\server\products\VS\vs_enterprise.exe --quiet --wait --norestart
    ```

> [!IMPORTANT]
> Чтобы предотвратить ошибку, убедитесь, что полный путь макета содержит менее 80 символов.

> [!TIP]
> Когда установка выполняется в рамках пакетного файла, параметр `--wait` позволяет гарантировать, что процесс `vs_enterprise.exe` дождется завершения установки, прежде чем возвращать код выхода.
>
> Это полезно, если администратор предприятия хочет выполнить дальнейшие действия в завершенной установке (например, [применить ключ продукта к успешной установке](automatically-apply-product-keys-when-deploying-visual-studio.md)), но вынужден дожидаться завершения установки, чтобы обработать код возврата из этой установки.
>
> Если вы не используете `--wait`, процесс `vs_enterprise.exe` завершается до окончания установки и возвращает неточный код выхода, который не представляет состояние операции установки.
>

::: moniker range="vs-2019"
> [!IMPORTANT]
> Если при установке в автономном режиме появляется сообщение об ошибке "Невозможно найти продукт, соответствующий следующим параметрам", убедитесь, что вы используете параметр — `--noweb` с версией 16.3.5 или более поздней.
>
::: moniker-end

При установке на основе макета содержимое, которое устанавливается, извлекается из макета. Однако если выбрать компонент, которого нет в макете, он будет получен из Интернета.  Чтобы запретить программе установки Visual Studio скачивать содержимое, которое отсутствует в макете, используйте параметр `--noWeb`. Если используется параметр `--noWeb`, а в макете отсутствует выбранное для установки содержимое, программа установки завершается ошибкой.

> [!TIP]
> Чтобы выполнить установку из автономного источника на компьютере, не подключенном к Интернету, укажите параметры `--noWeb` и `--noUpdateInstaller`. Первый блокирует скачивание обновленных рабочих нагрузок, компонентов и т. д. Второй блокирует самообновление установщика с помощью обновлений из Интернета.

> [!IMPORTANT]
> Параметр `--noWeb` не отключает проверку наличия обновлений при установке Visual Studio на компьютере, подключенном к Интернету. Дополнительные сведения см. в статье [Управление обновлением сетевых развертываний Visual Studio](controlling-updates-to-visual-studio-deployments.md).

### <a name="error-codes"></a>Коды ошибок

Если вы используете параметр `--wait`, то в зависимости от результата операции переменная среды `%ERRORLEVEL%` получает одно из следующих значений.

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

## <a name="update-a-network-install-layout"></a>Обновление макета сетевой установки

По мере выхода обновления продукта может потребоваться [обновить макет сетевой установки](update-a-network-installation-of-visual-studio.md), чтобы включить обновленные пакеты.

## <a name="how-to-create-a-layout-for-a-previous-visual-studio-release"></a>Как создать макет для предыдущего выпуска Visual Studio

::: moniker range="vs-2017"

> [!NOTE]
> Начальные загрузчики Visual Studio, доступные на веб-сайте [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017), скачивают и устанавливают последний выпуск Visual Studio, доступный на момент очередного запуска.
>
> Если вы скачаете *загрузчик* Visual Studio сегодня, но запустите его через шесть месяцев, будет установлен выпуск Visual Studio, актуальный на момент запуска загрузчика.
>
> Если же вы создадите *макет* и используете его для установки, на основе этого макета будет установлена определенная версия Visual Studio, включенная в этот макет. Даже если в Интернете уже существует новая версия, вы получите только ту версию Visual Studio, которая включена в ваш макет.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Начальные загрузчики Visual Studio, доступные на веб-сайте [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads), скачивают и устанавливают последний выпуск Visual Studio, доступный на момент очередного запуска.
>
> Если вы скачаете *загрузчик* Visual Studio сегодня, но запустите его через шесть месяцев, будет установлен выпуск Visual Studio, актуальный на момент запуска загрузчика.
>
> Если же вы создадите *макет* и используете его для установки, на основе этого макета будет установлена определенная версия Visual Studio, включенная в этот макет. Даже если в Интернете уже существует новая версия, вы получите только ту версию Visual Studio, которая включена в ваш макет.

::: moniker-end

Если вам нужно создать макет для более ранней версии Visual Studio, откройте страницу [https://my.visualstudio.com](https://my.visualstudio.com) и скачайте фиксированную (fixed) версию начального загрузчика Visual Studio.

### <a name="how-to-get-support-for-your-offline-installer"></a>Техническая поддержка по вопросам, связанным с автономным установщиком

Если что-то во время автономной установки возникнет проблема, мы очень хотим узнать об этом. Передайте нам информацию с помощью средства [сообщения о проблеме](../ide/how-to-report-a-problem-with-visual-studio.md). Это средство позволяет отправлять нам данные телеметрии и журналы, которые помогут диагностировать и устранить возникшую проблему.

Также доступен [**чат по вопросам установки**](https://visualstudio.microsoft.com/vs/support/#talktous), предназначенный для оказания помощи при проблемах с установкой (только на английском языке).

У нас есть и другие возможности технической поддержки. Список можно найти на нашей странице [отзывов](../ide/feedback-options.md).

## <a name="see-also"></a>См. также

- [Руководство администратора Visual Studio](visual-studio-administrator-guide.md)
- [Обновление сетевой установки Visual Studio](update-a-network-installation-of-visual-studio.md)
- [Исправление ошибок сети при установке или использовании Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
- [Управление обновлением сетевых развертываний Visual Studio](controlling-updates-to-visual-studio-deployments.md)
- [Жизненный цикл и обслуживание продуктов Visual Studio](/visualstudio/releases/2019/servicing/)
- [Обновление Visual Studio во время обслуживания](update-servicing-baseline.md)
- [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
- [Идентификаторы рабочих нагрузок и компонентов Visual Studio](workload-and-component-ids.md)
- [Установка сертификатов, необходимых для установки Visual Studio в автономном режиме](install-certificates-for-visual-studio-offline.md)