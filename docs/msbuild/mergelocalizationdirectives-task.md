---
title: Задача MergeLocalizationDirectives | Документация Майкрософт
description: Сведения об использовании задачи MergeLocalizationDirectives в MSBuild для слияния атрибутов локализации и комментариев файлов в двоичном формате XAML в один файл.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- localizing XAML [WPF MSBuild], moving comments and attributes to a separate file
- MergeLocalizationDirectives task [WPF MSBuild], parameters
- MergeLocalizationDirectives task [WPF MSBuild]
- moving localization comments and attributes to a separate file [WPF MSBuild]
ms.assetid: 9095b4f1-88da-4194-914b-ee1456826830
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 69a7c6a472023dd8bd41b087b3749e5451382a5e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950310"
---
# <a name="mergelocalizationdirectives-task"></a>Задача MergeLocalizationDirectives

Задача <xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> выполняет слияние атрибутов локализации и комментариев одного или нескольких файлов в двоичном формате XAML в один файл для всей сборки.

## <a name="task-parameters"></a>Параметры задачи

| Параметр | Описание |
|------------------------------| - |
| `GeneratedLocalizationFiles` | Обязательный параметр **ITaskItem[]** .<br /><br /> Определяет список файлов директив локализации для отдельных файлов в двоичном формате XAML. |
| `OutputFile` | Обязательный параметр вывода **String**.<br /><br /> Определяет выходной путь скомпилированной сборки директив локализации. |

## <a name="remarks"></a>Комментарии

Вы можете добавлять комментарии и атрибуты локализации к содержимому XAML. Благодаря поддержке локализации Windows Presentation Foundation можно удалить комментарии и атрибуты локализации, поместив их в файл *.loc* отдельно от созданной сборки. Это можно сделать с помощью атрибута **LocalizationPropertyStorage**. См. дополнительные сведения об атрибуте **LocalizationPropertyStorage** в разделе, посвященном [комментариям и атрибутам локализации](/dotnet/framework/wpf/advanced/localization-attributes-and-comments).

## <a name="example"></a>Пример

В следующем примере выполняется слияние комментариев локализации нескольких файлов XAML в двоичном формате в один файл *.loc*.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="MergeLocalizationDirectivesTask">
    <MergeLocalizationDirectives
      GeneratedLocalizationFiles="obj\debug\page1.loc;obj\debug\page2.loc;obj\debug\page3.loc"
      OutputFile="obj\debug\WPFMSBuildSample.loc" />
  </Target>
</Project>
```

## <a name="see-also"></a>См. также

- [Справочные сведения о WPF для MSBuild](../msbuild/wpf-msbuild-reference.md)
- [Справочные сведения о задачах WPF для MSBuild](../msbuild/wpf-msbuild-task-reference.md)
- [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)
- [Справочник по задачам MSBuild](../msbuild/msbuild-task-reference.md)
- [Создание приложения WPF](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
