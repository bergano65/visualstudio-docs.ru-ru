---
title: -ResetSkipPkgs (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6199bf96bc631cf1018b2cb72a4d3c3cf7c703cc
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
Удаляет все параметры для пропуска загрузки, которые были добавлены в пакеты VSPackage пользователями, желающими исключить загрузку проблемных пакетов VSPackage, а затем запускает [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="syntax"></a>Синтаксис

```
Devenv /ResetSkipPkgs
```

## <a name="remarks"></a>Примечания
 Наличие тега SkipLoading отключает загрузку пакета VSPackage, удаление этого тега снова включает загрузку VSPackage.

## <a name="example"></a>Пример
 Следующий пример удаляет все теги SkipLoading.

```
Devenv.exe /ResetSkipPkgs
```

## <a name="see-also"></a>См. также

- [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)