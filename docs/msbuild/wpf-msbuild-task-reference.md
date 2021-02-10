---
title: Справочные сведения о задачах WPF для MSBuild | Документы Майкрософт
description: См. ссылку на задачу для процесса сборки Windows Presentation Foundation (WPF), для расширения возможностей MSBuild за счет дополнительных задач.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WPF MSBuild task reference [WPF MSBuild], term/definition table
- build tasks [WPF MSBuild], Microsoft build engine
- build tasks using the Microsoft build engine [WPF MSBuild], compile markup and process resources
- WPF MSBuild task reference [WPF MSBuild]
ms.assetid: 96df0370-e50f-4ffc-9771-b12fb8721143
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 94050565e6c5619781434c7a18307bfbf80b51f9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933678"
---
# <a name="wpf-msbuild-task-reference"></a>Справочные сведения о задачах WPF для MSBuild

Процесс сборки Windows Presentation Foundation (WPF) расширяет Microsoft Build Engine с помощью дополнительного набора задач сборки, включая задачи компиляции разметки и обработки ресурсов.

## <a name="in-this-section"></a>Содержание раздела

- [FileClassifier](../msbuild/fileclassifier-task.md)

 Классифицирует набор исходных ресурсов как ресурсов, которые будут внедрены в сборку. Если ресурс является нелокализуемым, он внедряется в основную сборку приложения, в противном случае — во вспомогательную сборку.

- [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)

 Создает сборку, если хотя бы одна страница XAML в проекте ссылается на тип, объявленный в этом проекте локально. Созданная сборка удаляется после успешного или неудачного завершения процесса сборки.

- [GetWinFXPath](../msbuild/getwinfxpath-task.md)

 Возвращает каталог текущей среды выполнения .NET Framework.

- [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)

 Преобразует нелокализуемые файлы проекта XAML в скомпилированный двоичный формат.

- [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)

 Выполняет второй проход компиляции разметки на файлах XAML, которые ссылаются на типы в том же проекте.

- [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)

 Выполняет слияние атрибутов локализации и комментариев одного или нескольких файлов в двоичном формате XAML в один файл для всей сборки.

- [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)

 Внедряет один или несколько ресурсов (файлов *JPG*, *ICO*, *BMP*, XAML в двоичном формате и других) в *RESOURCES-файл*.

- [UidManager](../msbuild/uidmanager-task.md)

 Проверяет, обновляет или удаляет уникальные идентификаторы (UID) для локализации всех элементов MSBuild, включенных в исходные файлы MSBuild.

- [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)

 Добавляет элемент **\<hostInBrowser />** в манифест приложения ( *\<projectname>.exe.manifest*) при сборке проекта Приложение обозревателя XAML (XBAP).

## <a name="see-also"></a>См. также

- [MSBuild](../msbuild/msbuild.md)