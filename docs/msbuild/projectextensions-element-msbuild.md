---
title: Элемент ProjectExtensions (MSBuild) | Документы Майкрософт
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ProjectExtensions
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ProjectExtensions> element [MSBuild]
- ProjectExtensions element [MSBuild]
ms.assetid: f95f312f-ff92-41eb-9469-ad99e236a307
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94f2d88aa19bf01ebe6f25c7d80772c812abcc59
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632970"
---
# <a name="projectextensions-element-msbuild"></a>Элемент ProjectExtensions (MSBuild)

Позволяет хранить в файлах проектов MSBuild информацию, не относящуюся к MSBuild. Все, что находится внутри элемента `ProjectExtensions`, будет игнорироваться MSBuild.

 \<Project> \<ProjectExtensions>

## <a name="syntax"></a>Синтаксис

```xml
<ProjectExtensions>
    Non-MSBuild information to include in file.
</ProjectExtensions>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты

 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

 Отсутствуют

### <a name="child-elements"></a>Дочерние элементы

 Отсутствуют

### <a name="parent-elements"></a>Родительские элементы

| Элемент | Описание |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Обязательный корневой элемент файла проекта MSBuild. |

## <a name="remarks"></a>Примечания

 В проекте MSBuild может использоваться только один элемент `ProjectExtensions`.

## <a name="example"></a>Пример

 В следующем примере кода демонстрируется хранение информации из интегрированной среды разработки в элементе `ProjectExtensions`.

```xml
<ProjectExtensions>
    <VSIDE>
        <External>
            <!--
            Raw XML passed to the IDE by an external source
            -->
        </External>
    </VSIDE>
</ProjectExtensions>
```

## <a name="see-also"></a>См. также

- [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
