---
title: Создание сетевой установки
description: Узнайте, как создать сетевую точку установки для развертывания Visual Studio на предприятии.
ms.date: 01/15/2019
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ee0eadc9d682e41737df00f81b6443daf5e21fb6
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349924"
---
# <a name="create-a-network-installation-of-visual-studio-2017"></a>Создание сетевой установки Visual Studio 2017

Обычно администратор предприятия создает точку сетевой установки для развертывания на клиентских рабочих станциях. Среда Visual Studio 2017 разработана таким образом, чтобы вы могли кэшировать файлы для первоначальной установки вместе со всеми обновлениями продуктов в одну папку. (Этот процесс также известен как _создание макета_.) Это сделано для того, чтобы клиентские рабочие станции могли использовать то же сетевое расположение для управления установкой, даже если они еще не были обновлены до последнего сервисного обновления.

 > [!NOTE]
 > Если вы используете в организации несколько версий Visual Studio (например, Visual Studio Professional и Visual Studio Enterprise), вам нужно создать отдельную сетевую папку установки для каждого выпуска.

## <a name="download-the-visual-studio-bootstrapper"></a>Скачивание загрузчика Visual Studio

Скачайте нужный выпуск Visual Studio. После выбора файла нажмите **Сохранить**, а затем **Открыть папку**.

Это должен быть один из следующих файлов установки &mdash;а точнее, файлов загрузчика&mdash;.

|Выпуск | Скачать|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2017) |
|Visual Studio Professional | [**vs_professional.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2017) |
|Visual Studio Community | [**vs_community.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2017) |

Другие поддерживаемые загрузчики: [vs_buildtools.exe](https://aka.ms/vs/15/release/vs_buildtools.exe), [vs_feedbackclient.exe](https://aka.ms/vs/15/release/vs_feedbackclient.exe), [vs_teamexplorer.exe](https://aka.ms/vs/15/release/vs_teamexplorer.exe), [vs_testagent.exe](https://aka.ms/vs/15/release/vs_testagent.exe), [vs_testcontroller.exe](https://aka.ms/vs/15/release/vs_testcontroller.exe) и [vs_testprofessional.exe](https://aka.ms/vs/15/release/vs_testprofessional.exe).

## <a name="create-an-offline-installation-folder"></a>Создание папки автономной установки

Для выполнения этого действия необходимо подключение к Интернету. Чтобы создать автономную установку со всеми языками и функциями, используйте одну из команд, приведенных в следующих примерах.

   > [!IMPORTANT]
   > Для установки полного макета Visual Studio 2017 потребуется как минимум 35 ГБ дискового пространства. Скачивание этого макета может занять некоторое время.  Чтобы создать макет, содержащий только выбранные компоненты для установки, см. инструкции в разделе [Настройка сетевого макета](#customizing-the-network-layout).
   >
   > [!TIP]
   > Эти команды необходимо выполнять из каталога загрузки. На компьютере с ОС Windows 10 это обычно каталог `C:\Users\<username>\Downloads`.

- Команда для выпуска Visual Studio Enterprise:

  ```vs_enterprise.exe --layout c:\vs2017offline```

- Команда для выпуска Visual Studio Professional:

  ```vs_professional.exe --layout c:\vs2017offline```

- Команда для выпуска Visual Studio Community:

  ```vs_community.exe --layout c:\vs2017offline```

## <a name="modify-the-responsejson-file"></a>Редактирование файла response.json

В файле response.json вы можете задать новые значения по умолчанию, которые будут использоваться при запуске программы установки.  Например, можно настроить файл `response.json` для автоматического выбора конкретного набора рабочих нагрузок.
Подробнее см. в статье об [автоматизации установки Visual Studio с помощью файла ответов](automated-installation-with-response-file.md).

## <a name="copy-the-layout-to-a-network-share"></a>Копирование макета в общую сетевую папку

Разместите макет на общем сетевом ресурсе, чтобы запускать его с других компьютеров.
* Пример<br>
```xcopy /e c:\vs2017offline \\server\products\VS2017```

## <a name="customizing-the-network-layout"></a>Настройка сетевого макета

Для сетевого макета можно настроить несколько параметров. Вы можете создать частичный макет, который содержит только определенный набор [языковых стандартов](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales), [рабочих нагрузок, компонентов, рекомендуемых и дополнительных зависимостей](workload-and-component-ids.md). Это может быть полезно, если вы намерены разворачивать на клиентских рабочих станциях только определенное подмножество рабочих нагрузок. Ниже перечислены типичные параметры командной строки для настройки макета.

* ```--add``` позволяет указать [идентификаторы рабочих нагрузок и компонентов](workload-and-component-ids.md).  Если используется параметр `--add`, загружаются только те рабочие нагрузки и компоненты, которые заданы с помощью `--add`.  Если параметр `--add` не используется, загружаются все компоненты и рабочие нагрузки.
* ```--includeRecommended``` позволяет включить все рекомендованные компоненты для рабочих нагрузок с указанными идентификаторами.
* ```--includeOptional``` позволяет включить все рекомендованные и дополнительные компоненты для рабочих нагрузок с указанными идентификаторами.
* ```--lang``` позволяет указать [языковые стандарты](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).

Далее приводятся примеры для создания неполного пользовательского макета.

* Чтобы скачать все рабочие нагрузки и компоненты только для одного языка, выполните: <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US```
* Чтобы скачать все рабочие нагрузки и компоненты для нескольких языков, выполните: <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US de-DE ja-JP```
* Чтобы скачать одну рабочую нагрузку для всех языков, выполните: <br> ```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --includeRecommended```
* А так вы можете скачать две рабочие нагрузки и один дополнительный компонент для трех языков: <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP ```
* Чтобы загрузить две рабочие нагрузки со всеми рекомендуемыми компонентами, выполните следующую команду: <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended ```
* Чтобы загрузить две рабочие нагрузки со всеми рекомендуемыми и дополнительными компонентами, выполните следующую команду: <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional ```

### <a name="new-in-153"></a>Новые возможности версии 15.3

При выполнении команды макета указанные параметры (например, рабочие нагрузки и языки) будут сохранены. Все предыдущие параметры будут включены в последующие команды макета.  Ниже приведен пример макета с одной рабочей нагрузкой только для английского языка.

```vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US```

Чтобы обновить этот макет до более новой версии, не нужно указывать дополнительные параметры командной строки. Предыдущие параметры сохраняются и используются во всех последующих командах макета в этой папке макета.  Следующая команда используется для обновления существующего частичного макета.

```vs_enterprise.exe --layout c:\VS2017Layout```

Здесь также приведен пример добавления дополнительной рабочей нагрузки. В этом случае добавляется рабочая нагрузка Azure и язык локализации.  Теперь в этот макет включены управляемый рабочий стол и Azure.  Для всех этих рабочих нагрузок также включены языковые ресурсы для английского и немецкого языков. Макет обновляется до последней доступной версии.

```vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE```

Если вы хотите обновить существующий макет до полного макета, используйте параметр --all, как показано в следующем примере.

```vs_enterprise.exe --layout c:\VS2017Layout --all```

## <a name="deploying-from-a-network-installation"></a>Развертывание из сетевой установки

Администраторы могут разворачивать Visual Studio на клиентских рабочих станциях в рамках сценария установки. Также пользователи с правами администратора могут запустить программу установки непосредственно из общей сетевой папки, чтобы установить Visual Studio на своем компьютере.

* Пользователи выполняют следующую команду для установки: <br>```\\server\products\VS2017\vs_enterprise.exe```
* Администраторы выполняют установку в автоматическом режиме с помощью следующей команды: <br>```\\server\products\VS2017\vs_enterprise.exe --quiet --wait --norestart```

> [!IMPORTANT]
> Чтобы предотвратить ошибку, убедитесь, что путь к полной установке содержит менее 80 символов.
>
> [!TIP]
> Когда установка выполняется в рамках пакетного файла, параметр `--wait` позволяет гарантировать, что процесс `vs_enterprise.exe` дождется завершения установки, прежде чем возвращать код выхода. Это полезно, если администратор предприятия хочет выполнить дальнейшие действия в завершенной установке (например, [применить ключ продукта к успешной установке](automatically-apply-product-keys-when-deploying-visual-studio.md)), но вынужден дожидаться завершения установки, чтобы обработать код возврата из этой установки.  Если вы не используете `--wait`, процесс `vs_enterprise.exe` завершается до окончания установки и возвращает неточный код выхода, который не представляет состояние операции установки.


При установке на основе макета содержимое, которое устанавливается, извлекается из макета. Однако если выбрать компонент, которого нет в макете, он будет получен из Интернета.  Чтобы запретить программе установки Visual Studio скачивать содержимое, которое отсутствует в макете, используйте параметр `--noWeb`.  Если используется параметр `--noWeb`, а в макете отсутствует выбранное для установки содержимое, программа установки завершается ошибкой.

### <a name="error-codes"></a>Коды ошибок

Если вы используете параметр `--wait`, то в зависимости от результата операции переменная среды `%ERRORLEVEL%` получает одно из следующих значений.

  | **Значение** | **Результат** |
  | --------- | ---------- |
  | 0 | Операция выполнена успешно. |
  | 3010 | Операция выполнена успешно, но перед началом работы необходимо выполнить перезагрузку. |
  | Другое | Произошел сбой — проверьте журналы для получения дополнительных сведений |

## <a name="updating-a-network-install-layout"></a>Обновление макета сетевой установки

По мере выхода обновления продукта может потребоваться [обновить макет сетевой установки](update-a-network-installation-of-visual-studio.md), чтобы включить обновленные пакеты.

## <a name="how-to-create-a-layout-for-a-previous-visual-studio-2017-release"></a>Как создать макет для предыдущей версии Visual Studio 2017

> [!NOTE]
> Начальные загрузчики Visual Studio 2017, доступные на веб-сайте [visualstudio.microsoft.com](http://visualstudio.microsoft.com), скачивают и устанавливают последний выпуск Visual Studio 2017, доступный на момент очередного запуска. Если вы скачаете загрузчик Visual Studio сегодня, но запустите его через шесть месяцев, будет установлен более поздний выпуск Visual Studio 2017. Если же вы создадите макет, при установке Visual Studio на основе этого макета будет установлена определенная версия Visual Studio, включенная в этот макет. Даже если в Интернете уже существует новая версия, вы получите только ту версию Visual Studio, которая включена в ваш макет.

Если вам нужно создать макет для более ранней версии Visual Studio 2017, откройте страницу https://my.visualstudio.com и скачайте фиксированную (fixed) версию начального загрузчика Visual Studio 2017.

### <a name="how-to-get-support-for-your-offline-installer"></a>Техническая поддержка по вопросам, связанным с автономным установщиком

Если что-то во время автономной установки возникнет проблема, мы очень хотим узнать об этом. Передайте нам информацию с помощью средства [сообщения о проблеме](../ide/how-to-report-a-problem-with-visual-studio-2017.md). Это средство позволяет отправлять нам данные телеметрии и журналы, которые помогут диагностировать и устранить возникшую проблему.

Также доступен [**чат поддержки в реальном времени**](https://visualstudio.microsoft.com/vs/support/#talktous), предназначенный для оказания помощи при проблемах с установкой (только на английском языке).

У нас есть и другие возможности технической поддержки. Список доступных вариантов вы найдете на странице в статье [Talk to us](../ide/how-to-report-a-problem-with-visual-studio-2017.md) (Свяжитесь с нами).

## <a name="see-also"></a>См. также

* [Установка Visual Studio](install-visual-studio.md)
* [Руководство администратора Visual Studio](visual-studio-administrator-guide.md)
* [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Идентификаторы рабочих нагрузок и компонентов Visual Studio](workload-and-component-ids.md)
