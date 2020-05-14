---
title: Условия MSBuild | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, conditions
- conditions [MSBuild]
- Exists, MSBuild condition function
- HasTrailingSlash, MSBuild condition function
ms.assetid: 9d7aa308-b667-48ed-b4c9-a61e49eb0a85
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 61ffb650a87fa992a07d749687498cbb8ec6482d
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586832"
---
# <a name="msbuild-conditions"></a>Условия MSBuild

MSBuild поддерживает определенный набор условий, которые можно применять везде, где разрешен атрибут `Condition`. В следующей таблице описаны эти условия.

|Условие|Описание|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|Принимает значение `true`, если `stringA` равна `stringB`.<br /><br /> Пример:<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> Одинарные кавычки можно не применять для простой последовательности букв и цифр или логических значений. Но они необходимы для пустых значений. В этой проверке регистр не учитывается.|
|'`stringA`' != '`stringB`'|Принимает значение `true`, если `stringA` не равна `stringB`.<br /><br /> Пример:<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> Одинарные кавычки можно не применять для простой последовательности букв и цифр или логических значений. Но они необходимы для пустых значений. В этой проверке регистр не учитывается.|
|\<, >, \<=, >=|Проверяет числовые значения операндов. Возвращает `true`, если отношение справедливо. Значения операндов могут быть десятичными или шестнадцатеричными числами. Шестнадцатеричные числа должны начинаться с "0x". **Примечание.**  В XML символы `<` и `>` следует записывать в виде escape-последовательностей. Символ `<` представляется в виде `&lt;`. Символ `>` представляется в виде `&gt;`.|
|Exists('`stringA`')|Принимает значение `true`, если файл или папка с именем `stringA` существует.<br /><br /> Пример:<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> Одинарные кавычки можно не применять для простой последовательности букв и цифр или логических значений. Но они необходимы для пустых значений.|
|HasTrailingSlash('`stringA`')|Принимает значение `true`, если указанная строка содержит завершающий символ обратной косой черты (\\) или символ прямой косой черты (/).<br /><br /> Пример:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Одинарные кавычки можно не применять для простой последовательности букв и цифр или логических значений. Но они необходимы для пустых значений.|
|!|Принимает значение `true`, если операнд имеет значение `false`.|
|И|Принимает значение `true`, если оба операнда имеют значение `true`.|
|Или|Принимает значение `true`, если по крайней мере один операнд имеет значение `true`.|
|()|Механизм группирования. Результат принимает значение `true`, если выражения, содержащиеся внутри, имеют значение `true`.|
|$if$ (%expression%), $else$, $endif$|Проверяет, равняется ли значение указанного `%expression%` строковому значению переданного параметра пользовательского шаблона. Если результат проверки условия `$if$` принимает значение `true`, его операторы выполняются, в противном случае проверяется условие `$else$`. Если результат проверки условия `$else$` принимает значение `true`, его операторы выполняются, в противном случае условие `$endif$` завершает проверку выражений.<br /><br /> Примеры использования см. в разделе [Логика параметра-шаблона проекта или элемента Visual Studio](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|

Вы можете использовать методы строк в условиях, как показано в следующем примере, где функция [TrimEnd()](/dotnet/api/system.string.trimend) используется для сравнения только релевантной части строки, чтобы можно было различать целевые платформы .NET Framework и .NET Core.

```xml
<Project Sdk="Microsoft.NET.Sdk">

    <PropertyGroup>
        <TargetFrameworks>net45;net48;netstandard2.1;netcoreapp2.1;netcoreapp3.1</TargetFrameworks>
    </PropertyGroup>

    <PropertyGroup Condition="'$(TargetFramework.TrimEnd(`0123456789.`))' == 'net'">
        <!-- Properties for .NET Framework -->
    </PropertyGroup>

</Project>
```

## <a name="see-also"></a>См. также

- [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)
- [Условные конструкции](../msbuild/msbuild-conditional-constructs.md)
- [Пошаговое руководство: Создание файла проекта MSBuild с нуля](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
