---
title: Задача FileClassifier | Документация Майкрософт
description: Используйте задачу FileClassifier MSBuild для классификации набора исходных ресурсов, которые будут внедрены в сборку.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- classifying a resource set to embed in an assembly [WPF MSBuild]
- non-localizable resources [WPF MSBuild], classifying to embed in an assembly
- FileClassifier task [WPF MSBuild]
ms.assetid: 14e03310-fcc0-4bb2-a84d-cda12be66367
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0f030a240bf02b3261ce903803095b83555a4531
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957365"
---
# <a name="fileclassifier-task"></a>Задача FileClassifier

Задача <xref:Microsoft.Build.Tasks.Windows.FileClassifier> классифицирует набор исходных ресурсов как ресурсов, которые будут внедрены в сборку. Если ресурс является нелокализуемым, он внедряется в основную сборку приложения, в противном случае — во вспомогательную сборку.

## <a name="task-parameters"></a>Параметры задачи

|Параметр|Описание|
|---------------|-----------------|
|`CLREmbeddedResource`|Не используется.|
|`CLRResourceFiles`|Не используется.|
|`CLRSatelliteEmbeddedResource`|Не используется.|
|`Culture`|Необязательный параметр типа **String**.<br /><br /> Задает язык и региональные параметры для сборки. Он может иметь значение **NULL**, если сборка не подлежит локализации. Если указано значение **NULL**, по умолчанию используется значение, возвращаемое **CultureInfo.InvariantCulture**, в нижнем регистре.|
|`MainEmbeddedFiles`|Необязательный параметр вывода **ITaskItem[]**.<br /><br /> Указывает нелокализуемые ресурсы, которые внедряются в основную сборку.|
|`OutputType`|Обязательный параметр **String**.<br /><br /> Задает тип файла, в который будут внедряться указанные исходные файлы. Допустимые значения: **exe**, **winexe**, или **library**.|
|`SatelliteEmbeddedFiles`|Необязательный параметр вывода **ITaskItem[]**.<br /><br /> Указывает локализуемые файлы, которые внедряются во вспомогательную сборку для языка и региональных параметров, указанных в параметре **Culture**.|
|`SourceFiles`|Обязательный параметр **ITaskItem[]** .<br /><br /> Задает список файлов для классификации.|

## <a name="remarks"></a>Remarks

Если не задан параметр **Culture**, то все ресурсы, указанные с помощью параметра **SourceFiles**, считаются нелокализуемыми. В противном случае они считаются локализуемыми, если не связаны с атрибутом **Localizable**, который имеет значение **false**.

## <a name="example"></a>Пример

Следующий пример классифицирует один исходный файл как ресурс и внедряет его во вспомогательную сборку для языка "Французский (Канада)".

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.FileClassifier"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <ItemGroup>
    <Resource Include="Resource1.bmp" />
  </ItemGroup>
  <Target Name="FileClassifierTask">
    <FileClassifier
      SourceFiles="Resource1.bmp"
      Culture="fr-CA"
      OutputType="exe" />
  </Target>
</Project>
```

## <a name="see-also"></a>См. также

- [Справочные сведения о WPF для MSBuild](../msbuild/wpf-msbuild-reference.md)
- [Справочные сведения о задачах](../msbuild/wpf-msbuild-task-reference.md)
- [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
- [Создание приложения WPF](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
