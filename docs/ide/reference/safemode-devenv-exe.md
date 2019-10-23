---
title: -SafeMode (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: abaeded184db78085a9629da0e763b2f76dbd328
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655514"
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