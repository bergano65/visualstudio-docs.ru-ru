---
title: Создание сетевой установки
description: Узнайте, как создать сетевую точку установки для развертывания Visual Studio на предприятии.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 5e499e54a7cf1c5c50a625cfe03482202e3a1f3f
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2019
ms.locfileid: "58857429"
---
# <a name="create-a-network-installation-of-visual-studio"></a>Создание сетевой установки Visual Studio

Обычно администратор предприятия создает точку сетевой установки для развертывания на клиентских рабочих станциях. Среда Visual Studio разработана таким образом, чтобы вы могли кэшировать файлы для первоначальной установки вместе со всеми обновлениями продуктов в одну папку. (Этот процесс также известен как _создание макета_.) 

Это сделано для того, чтобы клиентские рабочие станции могли использовать то же сетевое расположение для управления установкой, даже если они еще не были обновлены до последнего сервисного обновления.

 > [!NOTE]
 > Если вы используете в организации несколько версий Visual Studio (например, Visual Studio Professional и Visual Studio Enterprise), вам нужно создать отдельную сетевую папку установки для каждого выпуска.

## <a name="download-the-visual-studio-bootstrapper"></a>Скачивание загрузчика Visual Studio

Скачайте нужный выпуск Visual Studio. После выбора файла нажмите **Сохранить**, а затем **Открыть папку**.

Это должен быть один из следующих файлов установки &mdash;а точнее, файлов загрузчика&mdash;.

::: moniker range="vs-2017"

|Выпуск | Скачать|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2017) |
|Visual Studio Professional | [**vs_professional.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2017) |

Другие поддерживаемые загрузчики: [vs_buildtools.exe](https://aka.ms/vs/15/release/vs_buildtools.exe), [vs_feedbackclient.exe](https://aka.ms/vs/15/release/vs_feedbackclient.exe), [vs_teamexplorer.exe](https://aka.ms/vs/15/release/vs_teamexplorer.exe), [vs_testagent.exe](https://aka.ms/vs/15/release/vs_testagent.exe), [vs_testcontroller.exe](https://aka.ms/vs/15/release/vs_testcontroller.exe) и [vs_testprofessional.exe](https://aka.ms/vs/15/release/vs_testprofessional.exe).

::: moniker-end

::: moniker range="vs-2019"

|Выпуск | Скачать|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
|Visual Studio Professional | [**vs_professional.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |

Другие поддерживаемые загрузчики: [vs_buildtools.exe](https://aka.ms/vs/16/release/vs_buildtools.exe), [vs_teamexplorer.exe](https://aka.ms/vs/16/release/vs_teamexplorer.exe), [vs_testagent.exe](https://aka.ms/vs/16/release/vs_testagent.exe) и [vs_testcontroller.exe](https://aka.ms/vs/16/release/vs_testcontroller.exe).

::: moniker-end

## <a name="create-an-offline-installation-folder"></a>Создание папки автономной установки

Для выполнения этого действия необходимо подключение к Интернету. Чтобы создать автономную установку со всеми языками и функциями, используйте одну из команд, приведенных в следующих примерах.

   > [!IMPORTANT]
   > Для установки полного макета Visual Studio потребуется как минимум 35 ГБ дискового пространства. Загрузка может занять некоторое время. Чтобы создать макет, содержащий только выбранные компоненты для установки, см. инструкции в разделе [Настройка сетевого макета](#customize-the-network-layout).
   >
   > [!TIP]
   > Эти команды необходимо выполнять из каталога загрузки. На компьютере с ОС Windows 10 это обычно каталог `C:\Users\<username>\Downloads`.

- Команда для выпуска Visual Studio Enterprise:

  ```vs_enterprise.exe --layout c:\vsoffline```

- Команда для выпуска Visual Studio Professional:

  ```vs_professional.exe --layout c:\vsoffline```

## <a name="modify-the-responsejson-file"></a>Редактирование файла response.json

В файле response.json вы можете задать новые значения по умолчанию, которые будут использоваться при запуске программы установки.  Например, можно настроить файл `response.json` для автоматического выбора конкретного набора рабочих нагрузок.
Подробнее см. в статье об [автоматизации установки Visual Studio с помощью файла ответов](automated-installation-with-response-file.md).

## <a name="copy-the-layout-to-a-network-share"></a>Копирование макета в общую сетевую папку

Разместите макет на общем сетевом ресурсе, чтобы запускать его с других компьютеров.

::: moniker range="vs-2017"

Пример

```cmd
xcopy /e c:\vsoffline \\server\products\VS2017
```

::: moniker-end

::: moniker range="vs-2019"

```cmd
xcopy /e c:\vsoffline \\server\products\VS2019
```

::: moniker-end

> [!IMPORTANT]
> Чтобы предотвратить ошибку, убедитесь, что полный путь макета содержит менее 80 символов.

## <a name="customize-the-network-layout"></a>Настройка сетевого макета

Для сетевого макета можно настроить несколько параметров. Вы можете создать частичный макет, который содержит только определенный набор [языковых стандартов](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales), [рабочих нагрузок, компонентов, рекомендуемых и дополнительных зависимостей](workload-and-component-ids.md). Это может быть полезно, если вы намерены разворачивать на клиентских рабочих станциях только определенное подмножество рабочих нагрузок. Ниже перечислены типичные параметры командной строки для настройки макета.

* `--add` позволяет указать [идентификаторы рабочих нагрузок и компонентов](workload-and-component-ids.md). <br>Если используется параметр `--add`, загружаются только те рабочие нагрузки и компоненты, которые заданы с помощью `--add`.  Если параметр `--add` не используется, загружаются все компоненты и рабочие нагрузки.
* `--includeRecommended` позволяет включить все рекомендованные компоненты для рабочих нагрузок с указанными идентификаторами
* `--includeOptional` позволяет включить все рекомендованные и дополнительные компоненты для рабочих нагрузок с указанными идентификаторами.
* `--lang` позволяет указать [языковые стандарты](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).

Далее приводятся примеры для создания неполного пользовательского макета.

* Чтобы скачать все рабочие нагрузки и компоненты только для одного языка, выполните:

    ```cmd
    vs_enterprise.exe --layout C:\vsoffline --lang en-US
    ```

* Чтобы скачать все рабочие нагрузки и компоненты для нескольких языков, выполните:

    ```cmd
    vs_enterprise.exe --layout C:\vsoffline --lang en-US de-DE ja-JP
    ```

* Чтобы скачать одну рабочую нагрузку для всех языков, выполните:

    ```cmd
    vs_enterprise.exe --layout C:\vsoffline --add Microsoft.VisualStudio.Workload.Azure --includeRecommended
    ```

* А так вы можете скачать две рабочие нагрузки и один дополнительный компонент для трех языков:

    ```cmd
    vs_enterprise.exe --layout C:\vsoffline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP
    ```

* Чтобы загрузить две рабочие нагрузки со всеми рекомендуемыми компонентами:

    ```cmd
    vs_enterprise.exe --layout C:\vsoffline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended 
    ```

* Чтобы загрузить две рабочие нагрузки со всеми рекомендуемыми и дополнительными компонентами, выполните следующую команду:

    ```cmd
    vs_enterprise.exe --layout C:\vsoffline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional 
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
    \server\products\VS\vs_enterprise.exe --quiet --wait --norestart
    ```

> [!IMPORTANT]
> Чтобы предотвратить ошибку, убедитесь, что полный путь макета содержит менее 80 символов.
>
> [!TIP]
> Когда установка выполняется в рамках пакетного файла, параметр `--wait` позволяет гарантировать, что процесс `vs_enterprise.exe` дождется завершения установки, прежде чем возвращать код выхода.
>
> Это полезно, если администратор предприятия хочет выполнить дальнейшие действия в завершенной установке (например, [применить ключ продукта к успешной установке](automatically-apply-product-keys-when-deploying-visual-studio.md)), но вынужден дожидаться завершения установки, чтобы обработать код возврата из этой установки.
>
> Если вы не используете `--wait`, процесс `vs_enterprise.exe` завершается до окончания установки и возвращает неточный код выхода, который не представляет состояние операции установки.

При установке на основе макета содержимое, которое устанавливается, извлекается из макета. Однако если выбрать компонент, которого нет в макете, он будет получен из Интернета.  Чтобы запретить программе установки Visual Studio скачивать содержимое, которое отсутствует в макете, используйте параметр `--noWeb`. Если используется параметр `--noWeb`, а в макете отсутствует выбранное для установки содержимое, программа установки завершается ошибкой.

> [!IMPORTANT]
> Параметр `--noWeb` не отключает проверку наличия обновлений при установке Visual Studio. Дополнительные сведения см. в статье [Управление обновлением сетевых развертываний Visual Studio](controlling-updates-to-visual-studio-deployments.md).

### <a name="error-codes"></a>Коды ошибок

Если вы используете параметр `--wait`, то в зависимости от результата операции переменная среды `%ERRORLEVEL%` получает одно из следующих значений.

  | **Значение** | **Результат** |
  | --------- | ---------- |
  | 0 | Операция выполнена успешно. |
  | 3010 | Операция выполнена успешно, но перед началом работы необходимо выполнить перезагрузку. |
  | Другое | Произошел сбой — проверьте журналы для получения дополнительных сведений |

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
> Начальные загрузчики Visual Studio, доступные на веб-сайте [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), скачивают и устанавливают последний выпуск Visual Studio, доступный на момент очередного запуска.
> 
> Если вы скачаете *загрузчик* Visual Studio сегодня, но запустите его через шесть месяцев, будет установлен выпуск Visual Studio, актуальный на момент запуска загрузчика.
> 
> Если же вы создадите *макет* и используете его для установки, на основе этого макета будет установлена определенная версия Visual Studio, включенная в этот макет. Даже если в Интернете уже существует новая версия, вы получите только ту версию Visual Studio, которая включена в ваш макет.

::: moniker-end

Если вам нужно создать макет для более ранней версии Visual Studio, откройте страницу [https://my.visualstudio.com](https://my.visualstudio.com) и скачайте фиксированную (fixed) версию начального загрузчика Visual Studio.

### <a name="how-to-get-support-for-your-offline-installer"></a>Техническая поддержка по вопросам, связанным с автономным установщиком

Если что-то во время автономной установки возникнет проблема, мы очень хотим узнать об этом. Передайте нам информацию с помощью средства [сообщения о проблеме](../ide/how-to-report-a-problem-with-visual-studio.md). Это средство позволяет отправлять нам данные телеметрии и журналы, которые помогут диагностировать и устранить возникшую проблему.

Также доступен [**чат поддержки в реальном времени**](https://visualstudio.microsoft.com/vs/support/#talktous), предназначенный для оказания помощи при проблемах с установкой (только на английском языке).

У нас есть и другие возможности технической поддержки. Список доступных вариантов вы найдете на странице в статье [Talk to us](../ide/talk-to-us.md) (Свяжитесь с нами).

## <a name="see-also"></a>См. также

* [Обновление сетевой установки Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Управление обновлением сетевых развертываний Visual Studio](controlling-updates-to-visual-studio-deployments.md)
* [Руководство администратора Visual Studio](visual-studio-administrator-guide.md)
* [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Идентификаторы рабочих нагрузок и компонентов Visual Studio](workload-and-component-ids.md)
