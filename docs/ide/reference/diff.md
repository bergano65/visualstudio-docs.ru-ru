---
title: -Diff | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 016de0a06615caab723f83900e8bd4103cb142b1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="diff"></a>/Diff
Сравнение двух файлов. Различия отображаются в специальном окне Visual Studio.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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