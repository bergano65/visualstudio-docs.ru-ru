---
title: -SafeMode (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 092cc1fc3267113e862646b7572e9091b8f6ddef
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227204"
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