---
title: -Diff
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6cbf0f8f9fa2e97908e2ae13e3961382a7250a91
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704919"
---
# <a name="diff"></a>/Diff
Сравнение двух файлов. Различия отображаются в специальном окне Visual Studio.

## <a name="syntax"></a>Синтаксис

```cmd
devenv /Diff SourceFile, TargetFile, [SourceDisplayName],[TargetDisplayName]
```

## <a name="arguments"></a>Аргументы
 `SourceFile`

 Обязательно. Полный путь и имя первого файла, который следует сравнить.

 `TargetFile`

 Обязательно. Полный путь и имя второго файла, который следует сравнить.

 `SourceDisplayName`

 Необязательный. Отображаемое имя первого файла.

 `TargetDisplayName`

 Необязательный. Отображаемое имя второго файла.