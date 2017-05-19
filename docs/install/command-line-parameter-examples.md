---
title: "Примеры параметров командной строки для установки Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
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
ms.openlocfilehash: 0f07824b29e7851e353d472838a897853e227d6c
ms.contentlocale: ru-ru
ms.lasthandoff: 05/09/2017

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

## <a name="see-also"></a>См. также

 * [Руководство администратора Visual Studio](visual-studio-administrator-guide.md)
 * [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
 * [Создание автономной установки Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)

