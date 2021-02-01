---
title: Указание пути к программам командной строки для профилирования
description: Указание пути к программам командной строки для профилирования в тех случаях, когда путь к средствам профилирования командной строки не добавляется в переменную среды PATH.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fa1cb81d46f0977de2db9d78c6db53f542faa70f
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720037"
---
# <a name="specify-the-path-to-profiling-tools-command-line-tools"></a>Указание пути к программам командной строки средств профилирования

Путь средств профилирования командной строки [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] не добавляется в переменную среды PATH. На 32-разрядных компьютерах эти средства находятся в одном каталоге. Существуют 64- и 32-разрядные версии средств профилирования для 64-разрядных компьютеров.

## <a name="32-bit-computers"></a>32-разрядные компьютеры

Для машинного кода интерфейсы API профилировщика Visual Studio находятся в файле *VSPerf.dll*. Файл заголовка *VSPerf.h* и библиотека импорта *VSPerf.lib* расположены в каталоге *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK*.

 Для управляемого кода интерфейсы API находятся в файле *Microsoft.VisualStudio.Profiler.dll*. Эта библиотека DLL находится в каталоге *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools*.

## <a name="64-bit-computers"></a>64-разрядные компьютеры

На 64-разрядных компьютерах укажите путь в соответствии с целевой платформой профилируемого приложения.

- Для 32-разрядных приложений каталог средств профилирования по умолчанию:

     (Собственный) *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK*
     
     (Управляемый) *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools*

- Для 64-разрядных приложений каталог средств профилирования по умолчанию:

     (Собственный) *Microsoft Visual Studio\2017\Team Tools\Performance Tools\x64\PerfSDK*

     (Управляемый) *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools\x64*
