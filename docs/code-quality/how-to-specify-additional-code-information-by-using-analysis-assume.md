---
title: Использование _Analysis_assume для указания анализа кода
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _Analysis_assume
helpviewer_keywords:
- _Analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 1fec348108afdfe3cdac3325e0a1750b55332db4
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2020
ms.locfileid: "77271640"
---
# <a name="how-to-specify-additional-code-information-by-using-_analysis_assume"></a>Инструкции. Указание дополнительных сведений о коде с помощью _Analysis_assume

Вы можете предоставить подсказки средству анализа кода для C/C++ Code, которые помогут анализировать процесс анализа и сокращать предупреждения. Чтобы предоставить дополнительные сведения, используйте следующую функцию:

`_Analysis_assume(`  `expr`  `)`

`expr` — любое выражение, для которого предполагается вычисление значения true.

Средство анализа кода предполагает, что условие, представленное выражением, имеет значение true в точке, где отображается функция, и остается истинной до тех пор, пока выражение не будет изменено, например, путем присваивания переменной.

> [!NOTE]
> `_Analysis_assume` не влияет на оптимизацию кода. Вне средства анализа кода `_Analysis_assume` определяется как отсутствие операций.

## <a name="example"></a>Пример

Следующий код использует `_Analysis_assume` для исправления предупреждения анализа кода [C6388](../code-quality/c6388.md):

```cpp
#include<windows.h>
#include<codeanalysis\sourceannotations.h>

using namespace vc_attributes;

//requires pc to be null
void f([Pre(Null=Yes)] char* pc);

// calls free and sets ch to null
void FreeAndNull(char** ch);

void test()
{
    char pc = (char)malloc(5);
    FreeAndNull(&pc);
    _Analysis_assume(pc == NULL);
    f(pc);
}
```

## <a name="see-also"></a>См. также раздел

- [__assume](/cpp/intrinsics/assume)
