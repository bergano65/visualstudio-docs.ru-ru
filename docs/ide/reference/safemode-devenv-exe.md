---
title: -SafeMode (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
ms.openlocfilehash: c2c678d7304c879cf42c24de9d83704971043676
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704152"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
Запускает [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] в безопасном режиме, загружая только среду и службы по умолчанию.

## <a name="syntax"></a>Синтаксис

```cmd
devenv /SafeMode
```

## <a name="remarks"></a>Примечания
 Этот параметр запрещает загрузку пакетов VSPackage сторонних производителей при запуске [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], обеспечивая надежность работы.

## <a name="description"></a>Описание:
 В приведенном ниже примере [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] запускается в безопасном режиме.

## <a name="code"></a>Код

```cmd
Devenv.exe /SafeMode
```

## <a name="see-also"></a>См. также

- [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)