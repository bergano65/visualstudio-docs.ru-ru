---
title: Импорт и экспорт параметров — команда | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e3ee8549fd8cf1a4551818c013551ba24128f95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671052"
---
# <a name="import-and-export-settings-command"></a>Импорт и экспорт параметров - команда
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Импортирует, экспортирует или сбрасывает параметры [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

## <a name="syntax"></a>Синтаксис

```
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Коммутаторы
 /export:`filename` (необязательно). Экспортирует текущие параметры в указанный файл

 /Import: `filename` необязательный. Импортирует текущие параметры в указанный файл

 /reset Необязательный. Сбрасывает текущие параметры

## <a name="remarks"></a>Remarks
 Выполнение этой команды без параметров командной строки открывает мастер **Импорт и экспорт параметров**. Дополнительные сведения см. в статье [Практическое руководство. Совместное использование параметров на разных компьютерах или в разных версиях Visual Studio](https://msdn.microsoft.com/1131fb10-35c1-42da-9cd8-91aa3235b882).

## <a name="example"></a>Пример
 Следующая команда экспортирует текущие параметры в файл `MyFile.vssettings`.

```
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>См. также:
 [Настройка параметров разработки для](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [команд](../../ide/reference/visual-studio-commands.md) Visual Studio Visual Studio
