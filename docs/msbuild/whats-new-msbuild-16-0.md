---
title: Новые возможности MSBuild 16.0 | Документация Майкрософт
ms.date: 03/11/2019
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 9fb23c8a48493056c9a37f510cefea3cc3374095
ms.sourcegitcommit: 4c7a0c2d712eb24609216577a793e912a6083eaf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2019
ms.locfileid: "57987211"
---
# <a name="whats-new-in-msbuild-160"></a>Новые возможности в MSBuild 16.0

В этой статье описываются обновленные возможности и свойства MSBuild 16.0. Подробные заметки о выпуске (предварительная редакция) см. в статье об [ MSBuild 16.0](https://gist.github.com/rainersigwald/009627466f03964d0028e16fda633d9c).

## <a name="changed-path"></a>Измененный путь

 MSBuild устанавливается в папку *\Current* каждой версии Visual Studio. Например *C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\MSBuild*. Для поиска MSBuild можно использовать следующий модуль PowerShell: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

## <a name="changed-properties"></a>Измененные свойства

 В связи с выходом нового номера версии изменены следующие свойства MSBuild.

- `MSBuildToolsVersion` для этой версии средств считается текущей. Версия сборки имеет такой же номер, как и Visual Studio 2017, т. е. 15.1.0.0.

- `VisualStudioVersion` для этой версии средств имеет значение 16.0.

## <a name="updates"></a>Обновления

MSBuild и Visual Studio теперь по умолчанию создают код для .NET Framework 4.7.2. Если вы хотите использовать новые функции API MSBuild, необходимо также обновить сборку, но существующий код будет продолжать работать.

## <a name="see-also"></a>См. также
- [MSBuild](../msbuild/msbuild.md)
