---
title: Каскад параметров | Инструмент тестирования для разработчиков Microsoft IntelliTest
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Settings waterfall
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 966182ca79ffd06e17642e1b24d6e48b8e637efe
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55923725"
---
# <a name="settings-waterfall"></a>Каскад параметров

Концепция каскада параметров означает, что пользователь может указать параметры на уровне **сборки**, **средства** и **исследования**:

* Сборка — [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
* Фикстура — [PexClass](attribute-glossary.md#pexclass)
* Исследование — [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)

Параметры, указанные на уровне **сборки**, влияют на все средства и исследования в рамках этой сборки. Параметры, указанные на уровне **средства**, влияют на все исследования в рамках этого средства. Дочерние параметры имеют приоритет&mdash;если параметры заданы на уровнях **сборки** и **средства**, используются параметры уровня **средства**.

Обратите внимание, что некоторые параметры относятся исключительно к уровню **сборки** или **фикстуры**.

**Пример**

```csharp
using Microsoft.Pex.Framework;

[assembly: PexAssemblySettings(MaxBranches = 1000)] // we override the default value of maxbranches

namespace MyTests
{
    [PexClass(MaxBranches = 500)] // we override the 1000 value and set maxbranches to 500
    public partial class MyTests
    {
        [PexMethod(MaxBranches = 100)] // we override again, maxbranches = 100
        public void MyTest(...) { ... }
    }
}
```

## <a name="got-feedback"></a>Хотите оставить отзыв?

Делитесь своими идеями и пожеланиями относительно новых функций в [сообществе разработчиков](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).