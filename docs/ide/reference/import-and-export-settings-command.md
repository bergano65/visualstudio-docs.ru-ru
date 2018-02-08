---
title: "Импорт и экспорт параметров — команда | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d3faa3d77a0aab8edfbe491b9df655931c2f6ed2
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/29/2018
---
# <a name="import-and-export-settings-command"></a>Импорт и экспорт параметров - команда
Импортирует, экспортирует или сбрасывает параметры [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]  
```  
  
## <a name="switches"></a>Переключатели  
 /export:`filename`  
 Необязательный. Экспортирует текущие параметры в указанный файл  
  
 /import:`filename`  
 Необязательный. Импортирует текущие параметры в указанный файл  
  
 /reset  
 Необязательный. Сбрасывает текущие параметры  
  
## <a name="remarks"></a>Примечания

Выполнение этой команды без параметров командной строки открывает мастер **Импорт и экспорт параметров**. Дополнительные сведения см. в описании [синхронизированных параметров](../../ide/synchronized-settings-in-visual-studio.md).

## <a name="example"></a>Пример

Следующая команда экспортирует текущие параметры в файл `MyFile.vssettings`.

```shell
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>См. также

[Персонализация интегрированной среды разработки Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)  
[Команды Visual Studio](../../ide/reference/visual-studio-commands.md)