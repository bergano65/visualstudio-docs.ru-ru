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
ms.openlocfilehash: d38ef64a370b11c2695ea1e03d2e3ceead7cb63c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="diff"></a>/Diff
Сравнение двух файлов. Различия отображаются в специальном окне Visual Studio.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
devenv /Diff SourceFile, TargetFile, [SourceDisplayName],[TargetDisplayName]  
```  
  
## <a name="arguments"></a>Аргументы  
 `SourceFile`  
 Обязательный. Полный путь и имя первого файла, который следует сравнить.  
  
 `TargetFile`  
 Обязательный. Полный путь и имя второго файла, который следует сравнить.  
  
 `SourceDisplayName`  
 Необязательно. Отображаемое имя первого файла.  
  
 `TargetDisplayName`  
 Необязательно. Отображаемое имя второго файла.