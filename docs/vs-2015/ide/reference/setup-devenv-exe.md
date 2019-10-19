---
title: -Setup (devenv.exe) | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
ms.assetid: 87608b7f-a156-400c-80f5-fc823f843e61
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a923d1f3532548ebc6ed651a0739e0e5792f7967
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663536"
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Заставляет [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] выполнить слияние метаданных ресурсов, описывающих меню, панели инструментов и группы команд, из всех доступных пакетов VSPackage.

## <a name="syntax"></a>Синтаксис

```
devenv /setup
```

## <a name="remarks"></a>Примечания
 У этого параметра нет аргументов. Команда `devenv /setup` обычно выдается в качестве последнего этапа процесса установки. Использование параметра `/setup` не приводит к запуску [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

 Для использования параметров `devenv` и [devenv](../../ide/reference/setup-devenv-exe.md) нужно запустить [devenv](../../ide/reference/installvstemplates-devenv-exe.md) от имени администратора.

## <a name="example"></a>Пример
 В этом примере показан последний этап установки версии [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], включающей пакеты VSPackage.

```
devenv /setup
```

## <a name="see-also"></a>См. также
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)
