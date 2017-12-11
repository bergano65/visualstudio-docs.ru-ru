---
title: "Примеры параметров командной строки для установки Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology: vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: timsneath
ms.author: tims
manager: ghogen
ms.openlocfilehash: a3b12bfe0c289bfdefc6e3107960fd94889df287
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/11/2017
---
# <a name="command-line-parameter-examples-for-visual-studio-2017-installation"></a>Примеры параметров командной строки для установки Visual Studio 2017
Чтобы проиллюстрировать [использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md) на практике, здесь приводится несколько примеров, которые вы можете настроить в соответствии с требуемыми задачами.

В каждом примере `vs_enterprise.exe`, `vs_professional.exe` и `vs_community.exe` представляет собой соответствующий выпуск небольшой программы начальной загрузки Visual Studio (размер файла около 1 МБ), которая запускает процесс скачивания. Если вы используете другой выпуск, выберите соответствующую программу начальной загрузки.

> [!NOTE]
> Для выполнения всех команд требуются повышенные права администратора. Если запустить процесс с другими правами, появится запрос системы контроля учетных записей пользователей.

> [!NOTE]
>  Чтобы объединить несколько строк в одну команду, используйте символ `^` в конце командной строки. Кроме того, можно просто поместить эти строки в одну строку. В PowerShell вместо этого используется символ обратного апострофа (`` ` ``).

* Установите минимальный экземпляр Visual Studio без интерактивных запросов с отображением хода выполнения процесса:
```
vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
```

* Выполните автоматическую установку экземпляра Visual Studio для настольных ПК с французским языковым пакетом. Управление должно возвращаться только после завершения установки продукта.
```
vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
```

> [!NOTE]
>  Параметр `--wait` предназначен для использования в пакетном файле. Выполнение следующей команды в пакетном файле будет продолжено только после завершения установки. Переменная среды `%ERRORLEVEL%` будет содержать значение, возвращаемое командой, как описано на странице [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

* Загрузите базовый редактор Visual Studio (минимальная конфигурация Visual Studio). Включите только английский языковой пакет:

```cmd
vs_community.exe --layout C:\VS2017
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
```

* Скачайте среду .NET для настольного ПК и рабочие нагрузки .NET, а также все рекомендуемые компоненты и расширение GitHub. Включите только английский языковой пакет:
```
vs_community.exe --layout C:\VS2017 ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
```

* Запустите интерактивную установку всех рабочих нагрузок и компонентов, доступных для выпуска Visual Studio 2017 Enterprise:
```
vs_enterprise.exe --all --includeRecommended --includeOptional
```

* Установите второй именованный экземпляр Visual Studio Professional 2017 на компьютер с уже установленным выпуском Visual Studio Community 2017 с поддержкой разработки Node.js:
```
vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
```

* Удалите компонент средств профилирования из установленного по умолчанию экземпляра Visual Studio:
```
vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
```

## <a name="get-support"></a>Техническая поддержка
Иногда возникают проблемы. При сбое установки Visual Studio ознакомьтесь с советами, приведенными на странице [Устранение неполадок и исправление ошибок установки и обновления Visual Studio 2017](troubleshooting-installation-issues.md). Кроме того, вы можете сообщить о проблемах при использовании продукта в корпорацию Майкрософт, используя средство [Сообщить о проблеме](../ide/how-to-report-a-problem-with-visual-studio-2017.md) в Visual Studio IDE или платформу [UserVoice](https://visualstudio.uservoice.com/forums/121579). Вы можете просматривать описания проблем в [сообществе разработчиков Visual Studio](https://developercommunity.visualstudio.com/). Там же можно получать ответы на интересующие вас вопросы. Вы также можете связаться с нами и другими разработчиками Visual Studio, используя [средство для обсуждения Visual Studio в сообществе Gitter](https://gitter.im/Microsoft/VisualStudio) (требуется учетная запись [GitHub](https://github.com/)).

## <a name="see-also"></a>См. также

 * [Руководство администратора Visual Studio](visual-studio-administrator-guide.md)
 * [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
 * [Создание автономной установки Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
