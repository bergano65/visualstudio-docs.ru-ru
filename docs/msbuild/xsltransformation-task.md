---
title: Задача XslTransformation | Документация Майкрософт
description: Узнайте, как MSBuild использует задачу XslTransformation для преобразования входных данных XML с помощью XSLT и их вывода на выходное устройство или в файл.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, XslTransformation task
- XslTransformation task [MSBuild]
ms.assetid: 6f3a7d81-3ae3-4703-9a06-870b32b69d80
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f779fc5d222fdd0985adef203f0bb20fc601a429
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847951"
---
# <a name="xsltransformation-task"></a>XslTransformation - задача

Преобразует входные данные XML с помощью XSLT или скомпилированного XSLT и выводит результат на устройство вывода или в выходной файл.

## <a name="parameters"></a>Параметры

 В следующей таблице приводятся параметры задачи `XslTransformation` .

|Параметр|Описание|
|---------------|-----------------|
|`OutputPaths`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Задает выходные файлы для преобразования XML.|
|`Parameters`|Необязательный параметр `String`.<br /><br /> Задает параметры для входного документа XSLT.  Предоставьте необработанный код XML со всеми параметрами в формате `<Parameter Name="" Value="" Namespace="" />`.|
|`XmlContent`|Необязательный параметр `String`.<br /><br /> Указывает входные данные XML в виде строки.|
|`XmlInputPaths`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает входные файлы XML.|
|`XslCompiledDllPath`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Задает скомпилированный XSLT.|
|`XslContent`|Необязательный параметр `String`.<br /><br /> Указывает входные данные XSLT в виде строки.|
|`XslInputPath`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Указывает входной файл XSLT.|

## <a name="remarks"></a>Remarks

 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Пример

В приведенном ниже примере файл преобразования XSL *transform.xslt* используется для изменения XML-файла `$(XmlInputFileName)`. Преобразованный код XML записывается в `$(IntermediateOutputPath)output.xml`. Преобразование XSL принимает `$(Parameter1)` в качестве входного параметра.

```xml
    <XslTransformation XslInputPath="transform.xslt"
                       XmlInputPaths="$(XmlInputFileName)"
                       OutputPaths="$(IntermediateOutputPath)output.xml"
                       Parameters="&lt;Parameter Name='Parameter1' Value='$(Parameter1)'/&gt;"/>
```

## <a name="see-also"></a>См. также раздел

- [Параметры XSLT](/dotnet/standard/data/xml/xslt-parameters)
- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
