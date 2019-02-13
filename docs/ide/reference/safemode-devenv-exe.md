---
title: -SafeMode (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 14b2ac3a80a9e17e0c554f56ae8e31ac32450c5e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55938687"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)

Запускает Visual Studio в безопасном режиме, загружая только среду и службы по умолчанию.

## <a name="syntax"></a>Синтаксис

```shell
devenv /SafeMode
```

## <a name="remarks"></a>Примечания

Этот параметр запрещает загрузку пакетов VSPackage сторонних производителей при запуске Visual Studio, обеспечивая стабильное выполнение.

## <a name="example"></a>Пример

В приведенном ниже примере Visual Studio запускается в безопасном режиме.

```shell
devenv /safemode
```

## <a name="see-also"></a>См. также

- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)