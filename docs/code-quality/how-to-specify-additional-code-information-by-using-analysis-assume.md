---
title: Как выполнить Добавление дополнительных сведений о коде с помощью _Analysis_assume
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- _Analysis_assume
helpviewer_keywords:
- _Analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 17e25ace1da6cad9fcdc129b6c6f517c39c9c103
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53845085"
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>Как выполнить Добавление дополнительных сведений о коде с помощью _Analysis_assume
Возможность создания подсказок для средства анализа кода для кода C/C++, который поможет в процессе анализа и снижают количество предупреждений. Для предоставления дополнительных сведений, используйте следующую функцию:

 `_Analysis_assume(`  `expr`  `)`

 `expr` -любое выражение, которое предполагается, что имеют значение true.

 Средство анализа кода предполагается, что условие, представленный с помощью выражения имеет значение true, если в точке, где отображается функция и сохраняет значение true, пока выражение будет изменено, например, путем присваивания переменной.

> [!NOTE]
>  `_Analysis_assume` не влияет на оптимизации кода. За пределами средства анализа кода `_Analysis_assume` определяется как холостой.

## <a name="example"></a>Пример
 В следующем коде используется `_Analysis_assume` для устранения предупреждения анализа кода [C6388](../code-quality/c6388.md):

```
#include<windows.h>
#include<codeanalysis\sourceannotations.h>

using namespace vc_attributes;

// calls free and sets ch to null
void FreeAndNull(char* ch);

//requires pc to be null
void f([Pre(Null=Yes)] char* pc);

void test( )
{
  char *pc = (char*)malloc(5);
  FreeAndNull(pc);
  _Analysis_assume(pc == NULL);
  f(pc);
}
```

## <a name="see-also"></a>См. также
 [__assume](/cpp/intrinsics/assume)