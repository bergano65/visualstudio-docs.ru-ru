---
title: Новые возможности MSBuild 16.0 | Документация Майкрософт
ms.date: 03/11/2019
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 1a83ce4cf47f8a1607e562dfdb69b5b7374de1a6
ms.sourcegitcommit: ca9375d1c48355f2e9f7bc1b2d3f0e94eb15db00
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/15/2020
ms.locfileid: "76022344"
---
# <a name="whats-new-in-msbuild-160"></a>Новые возможности в MSBuild 16.0

В этой статье описываются обновленные возможности и свойства MSBuild 16.0. Подробные заметки о выпуске см. в статье [MSBuild 16.0](https://github.com/microsoft/msbuild/releases/tag/v16.0.461.62831).

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
