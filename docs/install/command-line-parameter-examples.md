---
title: "Примеры параметров командной строки для установки Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 04/05/2017
ms.reviewer: 
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
translationtype: Human Translation
ms.sourcegitcommit: 4e33dc3ebb32569b547aa9bcb6db9a15dbe4fc21
ms.openlocfilehash: ff67313f350264b39151bc0e2f7191ab16300f24
ms.lasthandoff: 04/05/2017

---
# <a name="command-line-parameter-examples-for-visual-studio-2017-installation"></a>Примеры параметров командной строки для установки Visual Studio 2017
Чтобы проиллюстрировать [использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md) на практике, здесь приводится несколько примеров, которые вы можете настроить в соответствии с требуемыми задачами.

В каждом примере `vs_enterprise.exe`, `vs_professional.exe` и `vs_community.exe` представляет собой соответствующий выпуск небольшой программы начальной загрузки Visual Studio (размер файла около 1 МБ), которая запускает процесс скачивания. Если вы используете другой выпуск, выберите соответствующую программу начальной загрузки.

> [!NOTE]
> Для выполнения всех команд требуются повышенные права администратора. Если запустить процесс с другими правами, появится запрос системы контроля учетных записей пользователей.

* Установите минимальный экземпляр Visual Studio без интерактивных запросов с отображением хода выполнения процесса:
```cmd
vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
```

* Выполните автоматическую установку экземпляра Visual Studio для настольных ПК с французским языковым пакетом. Управление должно возвращаться только после завершения установки продукта.
```cmd
vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --quiet --wait
```

  > [!NOTE]
  >  Параметр `--wait` предназначен для использования в пакетном файле. Выполнение следующей команды в пакетном файле будет продолжено только после завершения установки. Переменная среды `%ERRORLEVEL%` будет содержать значение, возвращаемое командой, как описано на странице [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

* Скачайте среду .NET для настольного ПК и рабочие нагрузки .NET, а также все рекомендуемые компоненты и расширение GitHub. Включите только английский языковой пакет:
```cmd
vs_community.exe --layout C:\VS2017
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Microsoft.Net.ComponentGroup.TargetingPacks.Common ^
   --add Microsoft.ComponentGroup.Blend ^
   --add Microsoft.VisualStudio.Component.EntityFramework ^
   --add Microsoft.VisualStudio.Component.DiagnosticTools ^
   --add Microsoft.VisualStudio.Component.DockerTools ^
   --add Microsoft.VisualStudio.Component.CloudExplorer ^
   --add Microsoft.VisualStudio.Component.Wcf.Tooling ^
   --add Component.GitHub.VisualStudio
```

   >[!NOTE]
   Выпуск Enterprise содержит дополнительные рекомендуемые компоненты, помимо включенных здесь. Список всех рекомендуемых компонентов для Visual Studio Enterprise см. в [каталоге компонентов Visual Studio Enterprise 2017](workload-component-id-vs-enterprise.md).

* Запустите интерактивную установку всех рабочих нагрузок и компонентов, доступных для выпуска Visual Studio 2017 Enterprise:
```cmd
vs_enterprise.exe --all --includeRecommended --includeOptional
```

* Установите второй именованный экземпляр Visual Studio Professional 2017 на компьютер с уже установленным выпуском Visual Studio Community 2017 с поддержкой разработки Node.js:
```cmd
vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --nickname VSforNode
```

* Удалите компонент средств профилирования из установленного по умолчанию экземпляра Visual Studio:
```cmd
vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
```

  > [!NOTE]
  >  Чтобы объединить несколько строк в одну команду, используйте символ `^` в конце командной строки. Кроме того, можно просто поместить эти строки в одну строку.

## <a name="see-also"></a>См. также

 * [Руководство администратора Visual Studio](visual-studio-administrator-guide.md)
 * [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
 * [Создание автономной установки Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)

