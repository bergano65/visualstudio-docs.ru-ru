---
title: "Установка в сетевых средах с низкой пропускной способностью или низким уровнем надежности | Документация Майкрософт"
description: "Описание принципов работы установщика Visual Studio в условиях плохого сетевого подключения с инструкциями по скачиванию файлов установки перед началом установки."
ms.date: 04/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 44DB1998-68CD-4560-870A-EE5B993DCF6E
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
ms.openlocfilehash: 9dbe70bce6c246416df64de304b06cd211320f2a
ms.contentlocale: ru-ru
ms.lasthandoff: 05/09/2017

---

# <a name="install-visual-studio-2017-on-low-bandwidth-or-unreliable-network-environments"></a>Установка Visual Studio 2017 в сетевых средах с низкой пропускной способностью или низким уровнем надежности
Мы разработали установщик Visual Studio 2017 так, что он прекрасно работает с разными параметрами сетевой среды и компьютера.

- Файлы, которые потребуются для установки Visual Studio, распространяются через глобальную сеть распространения, и мы можем передать их с локального сервера.
- Во время установки мы используем три разные технологии скачивания (WebClient, BITS и WinInet), чтобы меньше зависеть от работы антивирусных программ и прокси-серверов.
- Новая модель на основе рабочих нагрузок позволяет вам устанавливать меньше файлов, чем для предыдущих версий Visual Studio.

Мы рекомендуем вам опробовать новый веб-установщик и уверены, что вам понравится работать с ним. Но у нас есть решение и на тот случай, если вы хотите сначала скачать все файлы установки, и лишь затем начинать установку Visual Studio. Вы можете перед началом установки с помощью командной строки создать локальный кэш необходимых файлов.

Ниже описывается порядок действий.

## <a name="download-the-visual-studio-bootstrapper"></a>Скачивание загрузчика Visual Studio
Прежде всего следует скачать загрузчик Visual Studio для выбранного выпуска Visual Studio.

Это будет один из следующих файлов установки &mdash;а точнее, файлов загрузчика&mdash; или что-то близкое к ним.

| Выпуск                    | Файл                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio Community    | [vs_community.exe](https://aka.ms/vs/15/release/vs_community.exe)       |
| Visual Studio Professional | [vs_professional.exe](https://aka.ms/vs/15/release/vs_professional.exe) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/15/release/vs_enterprise.exe)     |

## <a name="create-a-local-install-cache"></a>Создание локального кэша установки
Чтобы создать локальный макет, откройте командную строку и выполните одну из команд, приведенных в примерах ниже. В этих примерах предполагается, что вы скачали загрузчик Visual Studio Community. Для других выпусков измените команду соответствующим образом.

- Для разработки веб-приложений .NET или классических приложений .NET выполните следующую команду:
  ```
  vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
  ```
- Для разработки классических приложений .NET и решений Office выполните следующую команду:
  ```
  vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
  ```
- Для разработки классических приложений C++ выполните следующую команду:
  ```
  vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
  ```

- Чтобы создать локальный макет с полным набором компонентов (это будет довольно долго, ведь компонентов у нас _очень много_!), выполните следующую команду:
  ```
  vs_community.exe --layout c:\vs2017layout --lang en-US
  ```

Если вы хотите установить язык, отличный от английского, выберите нужный языковой стандарт вместо `en-US` в нижней части этой страницы. Если потребуется, используйте этот [список доступных компонентов и рабочих нагрузок](workload-and-component-ids.md) для дополнительной настройки кэша установки.

## <a name="install-from-the-local-cache"></a>Установка из локального кэша
При запуске установки из локального кэша применяются локальные версии каждого из этих файлов. Но если во время установки вы выберете компоненты, которые отсутствуют в кэше, мы попытаемся загрузить их из Интернета.

Чтобы устанавливать только те файлы, которые вы уже скачали, все параметры командной строки должны совпадать с теми, которые вы использовали для создания макета кэша. Предположим, что вы создали макет кэша с помощью следующей команды:

```
vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

В этом случае используйте следующую команду для запуска установки:

```
c:\vs2017layout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

## <a name="list-of-language-locales"></a>Список языковых стандартов
| **Язык-языковой стандарт** | **Язык** |
| ----------------------- | --------------- |  
| cs-CZ | Чешский |
| de-DE | Немецкий |
| ru-RU | Английский |
| es-ES | Испанский |
| fr-FR | Французский |
| it-IT | Итальянский |
| ja-JP | Японский |
| ko-KR | Корейский |
| pl-PL | Польский |
| pt-BR | Португальский - Бразильская |
| ru-RU | Русский |
| tr-TR | Турецкий |
| zh-CN | Китайский (упрощенное письмо) |
| zh-TW | Китайский (традиционное письмо) |

## <a name="see-also"></a>См. также
* [Установка Visual Studio](install-visual-studio.md)
* [Руководство администратора Visual Studio](visual-studio-administrator-guide.md)
* [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)

