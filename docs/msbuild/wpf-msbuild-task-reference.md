---
title: "Справочные сведения о задачах WPF для MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "задачи построения [WPF MSBuild], Microsoft build engine"
  - "построение задач с помощью Microsoft build engine [WPF MSBuild], компиляция разметки и обработки ресурсов"
  - "справочные сведения о задачах WPF MSBuild [WPF MSBuild]"
  - "справочные сведения о задачах WPF MSBuild [WPF MSBuild], таблица "термин-определение""
ms.assetid: 96df0370-e50f-4ffc-9771-b12fb8721143
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# Справочные сведения о задачах WPF для MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Процесс построения Windows Presentation Foundation \(WPF\) расширяет обработчик построения Майкрософт \(MSBuild\) с помощью дополнительного набора задач построения, включая задачи компиляции разметки и обработки ресурсов.  
  
## В этом подразделе  
 [FileClassifier](../msbuild/fileclassifier-task.md)  
 Классификация набора исходных ресурсов как ресурсов, которые будут внедрены в сборку.  Если ресурс нелокализуем, то он внедряется в основную сборку приложений. В противном случае он внедряется во вспомогательную сборку.  
  
 [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)  
 Создание сборки, если хотя бы одна страница [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] в проекте ссылается на тип, объявленный в этом проекте локально.  Созданная сборка удаляется после завершения или сбоя процесса построения.  
  
 [GetWinFXPath](../msbuild/getwinfxpath-task.md)  
 Возврат каталога текущей среды выполнения [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)].  
  
 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)  
 Преобразование нелокализуемых файлов проекта [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] в скомпилированный двоичный формат.  
  
 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)  
 Выполнение второго прохода компиляции разметки на файлах [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)], которые ссылаются на типы в том же проекте.  
  
 [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)  
 Слияние атрибутов локализации и примечаний одного или нескольких файлов в двоичном формате [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] в один файл для всей сборки.  
  
 [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)  
 Внедрение одного или нескольких ресурсов \(файлов .jpg, .ico, .bmp, [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] в двоичном формате и других\) в файл .resources.  
  
 [UidManager](../msbuild/uidmanager-task.md)  
 Проверка, обновление или удаление уникальных идентификаторов \(UID\) для локализации всех элементов [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)], включенных в исходные файлы [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].  
  
 [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)  
 Добавление элемента **\<hostInBrowser \/\>** к манифесту приложения \(*projectname*.exe.manifest\) при построении проекта [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)].  
  
## См. также  
 [MSBuild](http://msdn.microsoft.com/ru-ru/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)