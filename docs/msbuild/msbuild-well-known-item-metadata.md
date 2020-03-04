---
title: Общеизвестные метаданные элементов MSBuild | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, item metadata
- MSBuild, well-known item metadata
ms.assetid: b5e791b5-c68f-4978-ad8a-9247d03bb6c0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e9320525d770344f131d9e3f04b357de43b5e73
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633100"
---
# <a name="msbuild-well-known-item-metadata"></a>Общеизвестные метаданные элементов MSBuild

В следующей таблице описаны метаданные, которые назначаются каждому элементу при его создании. В каждом примере для включения в проект файла *C:\MyProject\Source\Program.cs* используется следующее объявление элемента.

```xml
<ItemGroup>
    <MyItem Include="Source\Program.cs" />
</ItemGroup>
```

|Метаданные элементов|Описание|
|-------------------|-----------------|
|%(FullPath)|Содержит полный путь к элементу. Пример:<br /><br /> *C:\MyProject\Source\Program.cs*|
|%(RootDir)|Содержит корневой каталог элемента. Пример:<br /><br /> *C:\\*|
|%(Filename)|Содержит имя файла элемента без расширения. Пример:<br /><br /> *Program*|
|%(Extension)|Содержит расширение имени файла элемента. Пример:<br /><br /> *.cs*|
|%(RelativeDir)|Содержит путь, указанный в атрибуте `Include`, до последней обратной косой черты (\\). Пример:<br /><br /> *Source\\*<br /><br /> Если атрибут `Include` представляет полный путь, `%(RelativeDir)` начинается с корневого каталога `%(RootDir)`.  Пример: <br /><br /> *C:\MyProject\Source\\*|
|%(Directory)|Содержит каталог элемента без корневого каталога. Пример:<br /><br /> *MyProject\\Source\\*|
|%(RecursiveDir)|Если атрибут `Include` содержит подстановочный знак \*\*, эти метаданные определяют путь, который используется вместо подстановочного знака. Дополнительные сведения о подстановочных знаках см. в статье [Практическое руководство. Выбор файлов для сборки](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> Если папка *C:\MySolution\MyProject\Source\\* содержит файл *Program.cs*, а файл проекта содержит такой элемент:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> то параметр `%(MyItem.RecursiveDir)` принимает значение *MySolution\MyProject\Source\\* .|
|%(Identity)|Элемент, заданный в атрибуте `Include`. Пример:<br /><br /> *Source\Program.cs*|
|%(ModifiedTime)|Содержит метку времени, соответствующую времени последнего изменения элемента. Пример:<br /><br /> `2004-07-01 00:21:31.5073316`|
|%(CreatedTime)|Содержит метку времени, соответствующую времени создания элемента. Пример:<br /><br /> `2004-06-25 09:26:45.8237425`|
|%(AccessedTime)|Содержит метку времени, соответствующую времени последнего доступа к элементу.<br /><br /> `2004-08-14 16:52:36.3168743`|

## <a name="see-also"></a>См. также

- [Элементы](../msbuild/msbuild-items.md)
- [Пакетная обработка в MSBuild](../msbuild/msbuild-batching.md)
- [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)
