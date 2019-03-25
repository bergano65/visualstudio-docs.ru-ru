---
title: Известные проблемы для контейнеров
description: В этой статье описаны известные проблемы, которые могут возникать при установке Visual Studio Build Tools в контейнере Windows.
ms.date: 04/18/2018
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: 140083f1-05bc-4014-949e-fb5802397c7a
author: heaths
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 52e3ab107aac36f50307db910c71e03b5a8b439b
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "57983706"
---
# <a name="known-issues-for-containers"></a>Известные проблемы для контейнеров

Существует несколько проблем, возникающих при установке Visual Studio в контейнер Docker.

::: moniker range="vs-2017"

## <a name="windows-container"></a>Контейнер Windows

Указанные ниже известные проблемы возникают при установке Visual Studio Build Tools 2017 в контейнер Windows.

* Вы не можете установить Visual Studio в контейнер, основанный на образе microsoft/windowsservercore:10.0.14393.1593. Образы, для которых указана версия, отличная от Windows SDK 10.0.14393, должны работать.
* Вы не можете установить пакет Windows SDK 10.0.14393 или более ранней версии. Установка некоторых пакетов завершается со сбоем, а зависящие от них рабочие нагрузки не функционируют.
* Передайте `-m 2GB` (или больше) при сборке образа. Некоторым рабочим нагрузкам требуется больше памяти, чем 1 ГБ, назначаемый по умолчанию при установке.
* Настройте Docker для использования дисков, размер которых больше стандартных 20 ГБ.
* Передайте `--norestart` в командной строке. На момент публикации при попытке перезапустить контейнер Windows из контейнера на узел возвращается `ERROR_TOO_MANY_OPEN_FILES`.
* Если образ основан непосредственно на microsoft/windowsservercore, платформа .NET Framework может не установиться правильно, причем сообщения об ошибках выводиться не будут. После завершения установки управляемый код может не запускаться. Вместо этого создайте образ на основе [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) или более поздней версии. Например, при выполнении сборки с помощью MSBuild может возникнуть такая ошибка:

  > C:\BuildTools\MSBuild\15.0\bin\Roslyn\Microsoft.CSharp.Core.targets(84,5): ошибка MSB6003: не удается запустить указанный исполняемый файл задачи csc.exe. Не удалось загрузить файл или сборку "System.IO.FileSystem, Version=4.0.1.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" или одну из их зависимостей. Не удается найти указанный файл.

* Вы не можете установить Visual Studio 2017 версии 15.8 или более ранней версии (любого продукта) на образ mcr<span></span>.microsoft.com/windows/servercore:1809 или более поздней версии. Дополнительные сведения см. в разделе https://aka.ms/setup/containers/servercore1809.

::: moniker-end

## <a name="build-tools-container"></a>Контейнер Build Tools

При использовании контейнера Build Tools могут возникнуть указанные ниже известные проблемы. Чтобы узнать, устранены ли эти проблемы и имеются ли другие известные проблемы, посетите сайт https://developercommunity.visualstudio.com.

* IntelliTrace может не работать в [некоторых сценариях](https://github.com/Microsoft/vstest/issues/940) внутри контейнера.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Установка средств сборки в контейнер](build-tools-container.md)
* [Расширенный пример для контейнеров](advanced-build-tools-container.md)
* [Идентификаторы рабочих нагрузок и компонентов для Visual Studio Build Tools](workload-component-id-vs-build-tools.md)
