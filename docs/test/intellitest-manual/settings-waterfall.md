---
title: Каскад параметров | Инструмент тестирования для разработчиков Microsoft IntelliTest
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Settings waterfall
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: ec6364b3d130ab3ca333838c7e1b6eb2fdcb4a3d
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815055"
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

Публикуйте свои идеи и запросы функций на сайте [UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest).
