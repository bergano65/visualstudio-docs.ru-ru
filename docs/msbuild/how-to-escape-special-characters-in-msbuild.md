---
title: Практическое руководство. Пропуск специальных знаков в MSBuild | Документация Майкрософт
description: Узнайте, как экранировать специальные символы, чтобы их можно было использовать в качестве литералов в файлах проекта MSBuild.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 44e4e713bf8f796f31fcca69a9451a77d120bcfc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914345"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Как обеспечить пропуск специальных знаков в MSBuild

Некоторые символы имеют особое значение в файлах проекта MSBuild. К ним относятся точка с запятой (`;`) и звездочка (`*`). Полный список таких специальных знаков см. в разделе [Специальные символы в MSBuild](../msbuild/msbuild-special-characters.md).

Чтобы использовать эти специальные символы в качестве литералов в файле проекта, их необходимо задать с помощью синтаксиса `%<xx>`, где `<xx>` представляет шестнадцатеричное значение ASCII символа.

## <a name="msbuild-special-characters"></a>Специальные символы в MSBuild

Одним из примеров применения специальных знаков является атрибут `Include` списков элементов. Например, в следующем списке элементов объявлено два элемента: *MyFile.cs* и *MyClass.cs*.

```xml
<Compile Include="MyFile.cs;MyClass.cs"/>
```

Если требуется объявить элемент, содержащий точку с запятой в имени, используйте синтаксис `%<xx>`, чтобы экранировать точку с запятой и предотвратить объявление двух отдельных элементов в MSBuild. Например, следующий элемент экранирует точку с запятой и объявляет один элемент с именем `MyFile.cs;MyClass.cs`.

```xml
<Compile Include="MyFile.cs%3BMyClass.cs"/>
```

Кроме того, можно экранировать строки с помощью [функции свойства](../msbuild/property-functions.md). Например, код далее эквивалентен приведенному выше примеру.

```xml
<Compile Include="$([MSBuild]::Escape('MyFile.cs;MyClass.cs'))" />
```

### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>Использование специального знака MSBuild в качестве символа литерала

Вместо специального знака используйте нотацию `%<xx>`, где `<xx>` представляет собой шестнадцатеричное значение символа ASCII. Например, чтобы использовать символ звездочки (`*`) как буквенный символ, примените значение `%2A`.

## <a name="see-also"></a>См. также
- [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Элементы](../msbuild/msbuild-items.md)
