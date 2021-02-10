---
title: -SafeMode (devenv.exe)
description: Узнайте, как использовать параметр командной строки SafeMode devenv для запуска Visual Studio в безопасном режиме, загружая только среду и службы по умолчанию.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1626776ec41bdbdfe5ad2b611516e62ada4f15a3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957872"
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

## <a name="see-also"></a>См. также раздел

- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)
