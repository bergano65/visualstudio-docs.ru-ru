---
title: Импорт и экспорт параметров - команда
ms.date: 11/21/2018
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 409c0f40adfd374065dedb842965d2d1237bc9a0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75568832"
---
# <a name="import-and-export-settings-command"></a>Импорт и экспорт параметров - команда

Импортирует, экспортирует или сбрасывает параметры Visual Studio.

## <a name="syntax"></a>Синтаксис

```cmd
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Переключатели

/export:`filename`

Необязательный элемент. Экспортирует текущие параметры в указанный файл

/import:`filename`

Необязательный элемент. Импортирует текущие параметры в указанный файл

/reset

Необязательный элемент. Сбрасывает текущие параметры

## <a name="remarks"></a>Примечания

Выполнение этой команды без параметров командной строки открывает мастер **Импорт и экспорт параметров**. Дополнительные сведения см. в статьях о [синхронизации параметров](../synchronized-settings-in-visual-studio.md) и [параметрах среды](../environment-settings.md).

## <a name="example"></a>Пример

Следующая команда экспортирует текущие параметры в файл `MyFile.vssettings`.

```cmd
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>См. также

- [Параметры среды](../../ide/environment-settings.md)
- [Синхронизация параметров](../../ide/synchronized-settings-in-visual-studio.md)
- [Персонализация интегрированной среды разработки Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
