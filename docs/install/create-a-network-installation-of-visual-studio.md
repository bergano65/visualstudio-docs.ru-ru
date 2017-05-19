---
title: "Создание сетевой установки Visual Studio | Документация Майкрософт"
description: "{{ЗАПОЛНИТЕЛЬ}}"
ms.date: 05/05/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: timsneath
ms.author: tims
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
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: c8c48a92ba4ba75e87d947364919688032842265
ms.contentlocale: ru-ru
ms.lasthandoff: 05/09/2017

---

# <a name="create-a-network-installation-of-visual-studio-2017"></a>Создание сетевой установки Visual Studio 2017

Обычно администратор предприятия создает точку сетевой установки для развертывания на клиентских рабочих станциях. При разработке Visual Studio 2017 мы предоставили вам возможность собрать все файлы для начальной установки и все обновления продукта в одну папку (этот процесс можно назвать _созданием макета_). Благодаря этому клиентские рабочие станции смогут использовать одно сетевое расположение для управления установками, даже если они не обновлены до последней версии служебного обновления.

> [!NOTE]
> Если вы используете в организации нескольких версий Visual Studio (например, Visual Studio Professional и Visual Studio Enterprise), вам нужно создать отдельную сетевую папку установки для каждого выпуска.

## <a name="download-the-visual-studio-bootstrapper"></a>Скачивание загрузчика Visual Studio
**Скачайте** нужный выпуск Visual Studio. После выбора файла нажмите **Сохранить**, а затем **Открыть папку**.

Это будет один из следующих файлов установки &mdash;а точнее, файлов загрузчика&mdash;.

|Выпуск | Скачать|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise.exe**](https://aka.ms/vs/15/release/vs_enterprise.exe) |
|Visual Studio Professional | [**vs_professional.exe**](https://aka.ms/vs/15/release/vs_professional.exe) |
|Visual Studio Community | [**vs_community.exe**](https://aka.ms/vs/15/release/vs_community.exe) |

Другие поддерживаемые загрузчики: [vs_buildtools.exe](https://aka.ms/vs/15/release/vs_buildtools.exe), [vs_feedbackclient.exe](https://aka.ms/vs/15/release/vs_feedbackclient.exe), [vs_teamexplorer.exe](https://aka.ms/vs/15/release/vs_teamexplorer.exe), [vs_testagent.exe](https://aka.ms/vs/15/release/vs_testagent.exe), [vs_testcontroller.exe](https://aka.ms/vs/15/release/vs_testcontroller.exe) и [vs_testprofessional.exe](https://aka.ms/vs/15/release/vs_testprofessional.exe).

## <a name="create-an-offline-installation-folder"></a>Создание папки автономной установки
Чтобы создать автономную установку со всеми языками и функциями, используйте одну из команд, приведенных в следующих примерах.

(Эти команды необходимо выполнять из каталога загрузки. На компьютере под управлением Windows 10 это обычно каталог `C:\Users\<username>\Downloads`).

- Команда для выпуска Visual Studio Enterprise:
  ```
  vs_enterprise.exe --layout c:\vs2017offline
  ```
- Команда для выпуска Visual Studio Professional:
  ```
  vs_professional.exe --layout c:\vs2017offline
  ```
- Команда для выпуска Visual Studio Community:
  ```
  vs_community.exe --layout c:\vs2017offline
  ```

## <a name="modify-the-responsejson-file"></a>Редактирование файла response.json
В файле response.json вы можете задать новые значения по умолчанию, которые будут использоваться при запуске программы установки.  Например, можно настроить файл `response.json` для автоматического выбора конкретного набора рабочих нагрузок.
Подробнее см. в статье об [автоматизации установки Visual Studio с помощью файла ответов](automated-installation-with-response-file.md).

## <a name="copy-the-layout-to-a-network-share"></a>Копирование макета в общую сетевую папку

Разместите макет на общем сетевом ресурсе, чтобы запускать его с других компьютеров.
* Пример<br>
```xcopy /e c:\vs2017offline \\server\products\VS2017```
    
## <a name="customizing-the-network-layout"></a>Настройка сетевого макета
Для сетевого макета можно настроить несколько параметров. Вы можете создать частичный макет, который содержит только определенный набор [языковых стандартов](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales), [рабочих нагрузок, компонентов, рекомендуемых и дополнительных зависимостей](workload-and-component-ids.md). Это может быть полезно, если вы намерены разворачивать на клиентских рабочих станциях только определенное подмножество рабочих нагрузок. Ниже перечислены самые распространенные параметры командной строки для настройки макета.

 - ```--add``` позволяет указать [идентификаторы рабочих нагрузок и компонентов](workload-and-component-ids.md).  Если используется параметр `--add`, будут загружены только те рабочие нагрузки и компоненты, которые заданы с помощью `--add`.  Если параметр `--add` не используется, будут загружены все компоненты и рабочие нагрузки.
 - ```--includeRecommended``` позволяет включить все рекомендованные компоненты для рабочих нагрузок с указанными идентификаторами.
 - ```--includeOptional``` позволяет включить все рекомендованные и дополнительные компоненты для рабочих нагрузок с указанными идентификаторами.
 - ```--lang``` позволяет указать [языковые стандарты](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).
 
Далее приводятся примеры для создания неполного пользовательского макета.

 - Чтобы скачать все рабочие нагрузки и компоненты только для одного языка, выполните: <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US```
 - Чтобы скачать все рабочие нагрузки и компоненты для нескольких языков, выполните: <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US de-DE ja-JP```
 - Чтобы скачать одну рабочую нагрузку для всех языков, выполните: <br> ```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --includeRecommended```
 - А так вы можете скачать две рабочие нагрузки и один дополнительный компонент для трех языков: <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP ```
 - Чтобы загрузить две рабочие нагрузки со всеми рекомендуемыми компонентами, выполните следующую команду: <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended ```
 - Чтобы загрузить две рабочие нагрузки со всеми рекомендуемыми и дополнительными компонентами, выполните следующую команду: <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional ```


## <a name="deploying-from-a-network-installation"></a>Развертывание из сетевой установки
Администраторы могут разворачивать Visual Studio на клиентских рабочих станциях в рамках сценария установки. Также пользователи с правами администратора могут запустить программу установки непосредственно из общей сетевой папки, чтобы установить Visual Studio на своем компьютере.

- Пользователи выполняют следующую команду для установки: <br>```\\server\products\VS2017\vs_enterprise.exe```
- Администраторы выполняют установку в автоматическом режиме с помощью следующей команды: <br>```\\server\products\VS2017\vs_enterprise.exe --quiet --wait --norestart```

> [!TIP]
> Когда установка выполняется в рамках пакетного файла, параметр `--wait` позволяет гарантировать, что процесс `vs_enterprise.exe` дождется завершения установки, прежде чем возвращать код выхода. Это полезно в тех случаях, когда администратор предприятия хочет выполнить дополнительные действия для завершения установки (например, [применить ключ продукта к успешным установкам](automatically-apply-product-keys-when-deploying-visual-studio.md)). если требуется ожидать завершения установки для обработки ее кода возврата.  Если вы не используете параметр `--wait`, процесс vs_enterprise.exe будет завершен до завершения установки и его код выхода не будет отражать состояние операции установки.

### <a name="error-codes"></a>Коды ошибок
Если вы используете параметр `--wait`, то в зависимости от результата операции переменная среды `%ERRORLEVEL%` получит одно из следующих значений.

  | **Значение** | **Результат** |
  | --------- | ---------- |
  | 0 | Операция выполнена успешно. |
  | 3010 | Операция выполнена успешно, но перед началом работы необходимо выполнить перезагрузку. |
  | Другое | Произошел сбой — проверьте журналы для получения дополнительных сведений |

## <a name="updating-a-network-install-layout"></a>Обновление макета сетевой установки
По мере выхода обновления продукта может потребоваться [обновить макет сетевой установки](update-a-network-installation-of-visual-studio.md), чтобы включить обновленные пакеты.

## <a name="how-to-create-a-layout-for-a-previous-visual-studio-2017-release"></a>Как создать макет для предыдущей версии Visual Studio 2017
**Примечание.** Загрузчик VS 2017, доступный по адресу http://www.visualstudio.com, загружает и устанавливает последний выпуск VS 2017, доступный на момент очередного запуска. Если вы скачаете загрузчик VS сегодня, но выполните его через 6 месяцев, будет установлен более поздний выпуск VS 2017. Если же вы создадите макет, при установке VS из этого макета будет установлена определенная версии VS, включенная в этот макет. Даже если уже существует новая версия, вы получите только ту версию VS, которая включена в ваш макет.

Если вам нужно создать макет для более ранней версии Visual Studio 2017, откройте страницу https://my.visualstudio.com и скачайте фиксированную (fixed) версию загрузчике Visual Studio 2017 для любой из поддерживаемых версий. С их помощью вы сможете создать макет сетевой установки, содержащий соответствующую версию. 

### <a name="how-to-get-support-for-your-offline-installer"></a>Техническая поддержка по вопросам, связанным с автономным установщиком
Если что-то во время автономной установки возникнет проблема, мы очень хотим узнать об этом. Передайте нам информацию с помощью средства [сообщения о проблеме](../ide/how-to-report-a-problem-with-visual-studio-2017.md). Это средство позволяет отправлять нам данные телеметрии и журналы, которые помогут диагностировать и устранить возникшую проблему.

У нас есть и другие возможности технической поддержки. Список доступных вариантов вы найдете в статье [Как сообщить о проблеме с версией-кандидатом Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md).

## <a name="see-also"></a>См. также
* [Установка Visual Studio](install-visual-studio.md)
* [Руководство администратора Visual Studio](visual-studio-administrator-guide.md)
* [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Идентификаторы рабочих нагрузок и компонентов Visual Studio](workload-and-component-ids.md)

