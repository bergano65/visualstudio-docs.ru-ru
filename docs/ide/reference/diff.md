---
title: "-Diff | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 14deeec64d4645135f19587997844bfdd0b18cd5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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