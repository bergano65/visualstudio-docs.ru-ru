---
title: -Updateconfiguration (devenv.exe) | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 50773821b328ea81381744bc6f32b3907cd1c5bc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657920"
---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Предписывает [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] выполнить слияние пакетов [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] в системе и проверить наличие изменений в кэше MEF.

## <a name="syntax"></a>Синтаксис

```
devenv /updateconfiguration
```

## <a name="remarks"></a>Примечания
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] выполняет эту команду автоматически при установке пакета VSIX. После исправления файлов следует выполнить команду `devenv.exe /updateconfiguration`, чтобы среда [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] обновила кэш MEF. Это позволит оценить достаточность исправления.

## <a name="example"></a>Пример
 Приведенная ниже команда предписывает [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] выполнить слияние пакетов [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] в системе и проверить наличие изменений в кэше MEF.

```
Devenv.exe /updateconfiguration
```

## <a name="see-also"></a>См. также
 [Настройка параметров разработки в](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [параметрах командной строки](../../ide/reference/devenv-command-line-switches.md) для Visual Studio devenv
