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
ms.openlocfilehash: 6df78ec4be1fc94951634b84a98e80dc1403a41b
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948742"
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

- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)