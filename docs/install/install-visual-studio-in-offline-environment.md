---
title: "Особые рекомендации по установке Visual Studio в автономной среде | Документация Майкрософт"
description: "{{ЗАПОЛНИТЕЛЬ}}"
ms.date: 05/09/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9750A3F3-89C7-4A8F-BA75-B0B06BD772C2
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
ms.openlocfilehash: b596b6b6f9cff58525d253157534b6b990c68fcd
ms.contentlocale: ru-ru
ms.lasthandoff: 05/09/2017

---
# <a name="special-considerations-for-installing-visual-studio-in-an-offline-environment"></a>Особые рекомендации по установке Visual Studio в автономной среде

Visual Studio рассчитана в основном на установку с компьютера, подключенного к Интернету, поскольку многие ее компоненты регулярно обновляются. Но вы можете, выполнив несколько дополнительных действий, создать развертывание Visual Studio и в среде без подключения к Интернету.

## <a name="create-a-network-installation-layout"></a>Создание макета сетевой установки
* Подробнее см. статью [Создание сетевой установки Visual Studio](create-a-network-installation-of-visual-studio.md)

## <a name="install-certificates-needed-for-visual-studio-offline-installation"></a>Установка сертификатов, необходимых для установки Visual Studio в автономном режиме
Программа установки Visual Studio устанавливает только то содержимое, который считается доверенным.  Перед установкой она проверяет наличие подписи Authenticode для скачиваемого содержимого и наличие доверия для этой подписи.  Компьютеры с доступом к Интернету автоматически скачивают и устанавливают все сертификаты, необходимые для проверки подписей файлов.  Но иногда это будет невозможно, если вы работаете в автономной среде или в системе с плохим подключением к Интернету.  В таких случаях вам нужно предварительно установить необходимые сертификаты для всех пользователей.  При создании автономной установки эти сертификаты сохраняются локально на компьютере в папку "certificates".

Чтобы вручную установить сертификаты на клиентском компьютере, дважды щелкните файл сертификата и пройдите процесс мастера управления сертификатами. Если он предложит ввести пароль, оставьте это поле пустым.

Вы можете создать скрипт для установки сертификатов, выполнив следующие действия.

1. Скопируйте файл certmgr.exe в общую папку установки (например, `\server\share\vs2017`). `certmgr.exe` входит в состав Windows SDK, которую можно установить как дополнительный компонент для рабочей нагрузки _Разработка с помощью универсальной платформы Windows_. (например: `"C:\Program Files (x86)\Windows Kits\10\bin\x86\certmgr.exe"`)

2. С помощью следующих команд создайте пакетный файл сценария:

```cmd
\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestSignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestCounterSignCertificates.p12 -n "Microsoft Time-Stamp PCA" -s -r LocalMachine CA

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestCounterSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
```

3. Запустит пакетный файл на клиентском компьютере из командной оболочки с правами администратора или из процесса с повышенными правами.

### <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>Почему сертификаты из папки `certificates` не устанавливаются автоматически?
В среде с подключением к Интернету в процессе проверки подписи используются Windows API для загрузки и добавления сертификатов. Этот процесс включает проверку того, что сертификат является доверенным и допустимым в соответствии с настройками администрирования. В большинстве случаев процесс проверки невозможно выполнить в автономных средах. Установив сертификаты вручную, вы предоставите пользовательским компьютерам возможность убедиться в том, что сертификаты соответствуют требованиям администрирования.

## <a name="install-visual-studio"></a>Установка Visual Studio
Когда сертификаты будут установлены, развертывание Visual Studio можно выполнять в автономном режиме как обычно, без каких-либо дополнительных действий, в соответствии с [приведенными здесь инструкциями](create-a-network-installation-of-visual-studio.md#deploying-from-a-network-installation).


## <a name="see-also"></a>См. также
* [Установка Visual Studio](install-visual-studio.md)
* [Руководство администратора Visual Studio](visual-studio-administrator-guide.md)
* [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Идентификаторы рабочих нагрузок и компонентов Visual Studio](workload-and-component-ids.md)

