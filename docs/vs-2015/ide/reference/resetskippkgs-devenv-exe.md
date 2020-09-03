---
title: -ResetSkipPkgs (devenv.exe) | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 207ceb92d84c2186aeec49c205d8d32f4d7aa969
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665576"
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Удаляет все параметры для пропуска загрузки, которые были добавлены в пакеты VSPackage пользователями, желающими исключить загрузку проблемных пакетов VSPackage, а затем запускает [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

## <a name="syntax"></a>Синтаксис

```
Devenv /ResetSkipPkgs
```

## <a name="remarks"></a>Remarks
 Наличие тега SkipLoading отключает загрузку пакета VSPackage, удаление этого тега снова включает загрузку VSPackage.

## <a name="example"></a>Пример
 Следующий пример удаляет все теги SkipLoading.

```
Devenv.exe /ResetSkipPkgs
```

## <a name="see-also"></a>См. также:
 [Параметры командной строки для команды devenv](../../ide/reference/devenv-command-line-switches.md)
