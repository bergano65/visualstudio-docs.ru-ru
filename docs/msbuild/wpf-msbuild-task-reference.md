---
title: "Справочные сведения о задачах WPF для MSBuild | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "4"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: bdf6da409d3b7e87e95c8eb08f6ce730e3c1b1cc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="wpf-msbuild-task-reference"></a>Справочные сведения о задачах WPF для MSBuild
Процесс сборки Windows Presentation Foundation (WPF) расширяет Microsoft Build Engine с помощью дополнительного набора задач сборки, включая задачи компиляции разметки и обработки ресурсов.  
  
## <a name="in-this-section"></a>Содержание  
 [FileClassifier](../msbuild/fileclassifier-task.md)  
 Классифицирует набор исходных ресурсов как ресурсов, которые будут внедрены в сборку. Если ресурс является нелокализуемым, он внедряется в основную сборку приложения, в противном случае — во вспомогательную сборку.  
  
 [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)  
 Создает сборку, если хотя бы одна страница [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] в проекте ссылается на тип, объявленный в этом проекте локально. Созданная сборка удаляется после успешного или неудачного завершения процесса сборки.  
  
 [GetWinFXPath](../msbuild/getwinfxpath-task.md)  
 Возвращает каталог текущей среды выполнения [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)].  
  
 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)  
 Преобразует нелокализуемые файлы проекта [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] в скомпилированный двоичный формат.  
  
 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)  
 Выполняет второй проход компиляции разметки на файлах [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)], которые ссылаются на типы в том же проекте.  
  
 [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)  
 Выполняет слияние атрибутов локализации и примечаний одного или нескольких файлов в двоичном формате [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] в один файл для всей сборки.  
  
 [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)  
 Внедряет один или несколько ресурсов (файлов JPG, ICO, BMP, [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] в двоичном формате и других) в RESOURCES-файл.  
  
 [UidManager](../msbuild/uidmanager-task.md)  
 Проверяет, обновляет или удаляет уникальные идентификаторы (UID) для локализации всех элементов [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)], включенных в исходные файлы [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].  
  
 [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)  
 Добавляет элемент **\<hostInBrowser />** в манифест приложения (*имя_проекта*.exe.manifest) при сборке проекта [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)].  
  
## <a name="see-also"></a>См. также  
 [MSBuild](../msbuild/msbuild.md)