---
title: Как выполнить  Пропуск специальных знаков в MSBuild | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 752f4c6535f498b074d2c85b4b7cb6e9870ea862
ms.sourcegitcommit: 01334abf36d7e0774329050d34b3a819979c95a2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/07/2019
ms.locfileid: "55853944"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Как выполнить  Пропуск специальных знаков в MSBuild

Некоторые символы имеют особое значение в файлах проекта [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. К ним относятся точка с запятой (`;`) и звездочка (`*`). Полный список таких специальных знаков см. в разделе [Специальные символы в MSBuild](../msbuild/msbuild-special-characters.md).

Чтобы использовать эти специальные символы в качестве литералов в файле проекта, их необходимо задать с помощью синтаксиса `%<xx>`, где `<xx>` представляет шестнадцатеричное значение ASCII символа.

## <a name="msbuild-special-characters"></a>Специальные символы в MSBuild

Одним из примеров применения специальных знаков является атрибут `Include` списков элементов. Например, в следующем списке элементов объявлено два элемента: *MyFile.cs* и *MyClass.cs*.

```xml
<Compile Include="MyFile.cs;MyClass.cs"/>
```

Если требуется объявить элемент, содержащий точку с запятой в имени, используйте синтаксис `%<xx>`, чтобы экранировать точку с запятой и предотвратить объявление двух отдельных элементов в [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Например, следующий элемент экранирует точку с запятой и объявляет один элемент с именем `MyFile.cs;MyClass.cs`.

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
[Основные понятия MSBuild](../msbuild/msbuild-concepts.md)  
[MSBuild](../msbuild/msbuild.md)  
[Элементы](../msbuild/msbuild-items.md)
