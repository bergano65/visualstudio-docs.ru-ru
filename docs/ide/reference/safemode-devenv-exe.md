---
title: -SafeMode (devenv.exe)
ms.date: 11/04/2016
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
ms.openlocfilehash: ed14c3ec0da75df37c5a006f4e25240ac6630d20
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53949658"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
Запускает [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] в безопасном режиме, загружая только среду и службы по умолчанию.

## <a name="syntax"></a>Синтаксис

```cmd
devenv /SafeMode
```

## <a name="remarks"></a>Примечания
 Этот параметр запрещает загрузку пакетов VSPackage сторонних производителей при запуске [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], обеспечивая надежность работы.

## <a name="description"></a>Описание
 В приведенном ниже примере [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] запускается в безопасном режиме.

## <a name="code"></a>Код

```cmd
Devenv.exe /SafeMode
```

## <a name="see-also"></a>См. также раздел

- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)