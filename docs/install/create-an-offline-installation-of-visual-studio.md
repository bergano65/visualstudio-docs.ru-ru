---
title: "Создание автономного установщика Visual Studio 2017 | Документация Майкрософт"
description: "Сведения о создании автономного установщика Visual Studio."
ms.custom: 
ms.date: 03/21/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- offline installer [Visual Studio]
- ISO [Visual Studio]
ms.assetid: 7bd7e724-7bfd-43f1-9935-981919be5a00
author: TerryGLee
ms.author: tglee
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
translationtype: Human Translation
ms.sourcegitcommit: 5b6334c38a6c058f274498c06f8e07c934931910
ms.openlocfilehash: 563c78a49eb55886b1ddbd4f437951c99c6568e5
ms.lasthandoff: 03/22/2017

---
# <a name="create-an-offline-installer-for-visual-studio-2017"></a>Создание автономного установщика Visual Studio 2017
Мы знаем, что многим клиентам нужен автономный установщик для [Visual Studio 2017](https://go.microsoft.com/fwlink/?linkid=844067). Мы не предоставляем готовый ISO-образ, но вы легко можете создать папку, из которой установку можно выполнять в автономном режиме.

Ниже описывается порядок действий.

## <a name="download-the-setup-file-you-want"></a>Скачивание файла установки
**[Скачайте](https://www.visualstudio.com/downloads?utm_source=mscom&utm_campaign=msdocs)** нужный выпуск Visual Studio. После выбора файла нажмите **Сохранить**, а затем **Открыть папку**.

Это будет один из следующих файлов установки (а точнее, файлов загрузчика).

|Выпуск | Файл|  
|-------------|-----------------------|  
|Visual Studio Enterprise |**vs_enterprise.exe**|  
|Visual Studio Professional |**vs_professional.exe**|  
|Visual Studio Community |**vs_community.exe**|

Другие поддерживаемые начальные загрузчики: vs_buildtools.exe, vs_feedbackclient.exe, vs_teamexplorer.exe, vs_testagent.exe, vs_testcontroller.exe и vs_testprofessional.exe.

## <a name="create-an-offline-installation-folder"></a>Создание папки автономной установки
Чтобы создать автономную установку со всеми языками и функциями, используйте одну из команд, приведенных в следующих примерах.

(Эти команды необходимо выполнять из каталога загрузки. На компьютере под управлением Windows 10 это обычно каталог `C:\Users\<username>\Downloads`).

- Команда для выпуска Visual Studio Enterprise: <br>  ```vs_enterprise.exe --layout c:\vs2017offline```
- Команда для выпуска Visual Studio Professional: <br> ```vs_professional.exe --layout c:\vs2017offline```
- Команда для выпуска Visual Studio Community: <br> ```vs_community.exe --layout c:\vs2017offline```

Дополнительные примеры см. в разделе [Настройка автономного установщика](#how-to-customize-your-offline- installer) на этой странице.

## <a name="install-from-the-offline-installation-folder"></a>Установка из папки автономной установки
Вы можете запустить автономную установку в любой удобный момент. В любом случае потребуется выполнить следующие действия.

  1. Установите сертификаты (они находятся в папке Certificates, которая расположена в папке Layout. Чтобы установить сертификаты, щелкните каждый из них правой кнопкой мыши).

  2. Запустите файл установки. Вот пример команды для запуска: <br> ```c:\vs2017offline\vs_enterprise.exe```

## <a name="additional-tips-for-offline-installers"></a>Дополнительные советы по автономным установщикам
Вы можете легко настроить или обновить автономный установщик, и сейчас мы расскажем как. Если во время работы автономного установщика произойдет ошибка, вы можете воспользоваться нашей информацией по устранению неполадок и технической поддержкой.

### <a name="how-to-customize-your-offline-installer"></a>Настройка автономного установщика
Для автономного установщика можно настроить много разных параметров. Вот лишь несколько примеров персонализации с помощью [языкового стандарта](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).

 - Чтобы скачать все рабочие нагрузки и компоненты только для одного языка, выполните: <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US```
 - Чтобы скачать все рабочие нагрузки и компоненты для нескольких языков, выполните: <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US de-DE ja-JP```
 - Чтобы скачать одну рабочую нагрузку для всех языков, выполните: <br> ```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure ```
 - А так вы можете скачать две рабочие нагрузки и один дополнительный компонент для трех языков: <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure Microsoft.VisualStudio.Workload.ManagedDesktop Component.GitHub.VisualStudio --lang en-US de-DE ja-JP ```Дополнительные сведения о параметрах, которые можно использовать для настройки установки см. в статье [Использование параметров командной строки для установки Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md).


### <a name="how-to-update-an-offline-installer"></a>Обновление автономного установщика
Возможно, позднее вы захотите обновить ваш автономный установщик. Ниже описывается порядок действий.
* Чтобы обновить экземпляр Visual Studio, установленный из папки автономной установки, запустите программу установки Visual Studio и нажмите кнопку **Обновить**.
* Чтобы обновить саму папку автономной установки с учетом последних обновлений, снова запустите команду ```--layout```. Обязательно укажите в этой команде ту же папку, которая использовалась ранее. Тогда будут скачаны только те компоненты, которые изменились с момента предыдущего запуска ```--layout```.


### <a name="how-to-troubleshoot-an-offline-installer"></a>Устранение неполадок с автономным установщиком
Иногда возникают проблемы. Здесь мы приводим список известных проблем и варианты решений, которые могут оказаться полезными.

| Проблеми       | Элемент                   | Решение |
| ----------- | ---------------------- | -------- |
| Появляется предупреждение о невозможности установки некоторых компонентов и пакетов.  | Программа установки Android SDK (уровень API) | Если вы хотите включить пакеты SDK Android (уровень API), для создания автономного установщика потребуется подключение к Интернету. Если вы находитесь в сети с ограниченным доступом, необходимо разрешить доступ к следующим URL-адресам: <br><br> — http://dl.google.com:443 <br> — http://dl-ssl.google.com:443 <br>  — https://dl-ssl.google.com/android/repository/*<br><br>Дополнительные сведения об устранении возможных проблем с параметрами прокси-сервера см. в записи блога [Сбои установки Visual Studio (программа установки Android SDK) при использовании прокси-сервера](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/).  |  
| У пользователей отсутствуют права доступа к файлам. | Разрешения (ACL) | *Прежде* чем открывать общий доступ к автономной установке, необходимо настроить разрешения (ACL) и предоставить пользователям права на чтение. |
| Не удается установить новые рабочие нагрузки, компоненты или языки.  | `--layout`  | Если вы производите установку из частичного макета и выбираете рабочие нагрузки, компоненты или языки, которых нет в этом макете, вам потребуется доступ в Интернет. |

### <a name="how-to-get-support-for-your-offline-installer"></a>Техническая поддержка по вопросам, связанным с автономным установщиком
Если что-то во время автономной установки возникнет проблема, мы очень хотим узнать об этом. Передайте нам информацию с помощью средства [сообщения о проблеме](../ide/how-to-report-a-problem-with-visual-studio-2017.md). Это средство позволяет отправлять нам данные телеметрии и журналы, которые помогут диагностировать и устранить возникшую проблему.

У нас есть и другие возможности технической поддержки. Список доступных вариантов вы найдете в статье [Как сообщить о проблеме с версией-кандидатом Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md).


## <a name="see-also"></a>См. также
* [Установка Visual Studio](install-visual-studio.md)
* [Руководство администратора Visual Studio](visual-studio-administrator-guide.md)
* [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Идентификаторы рабочих нагрузок и компонентов Visual Studio](workload-and-component-ids.md)

