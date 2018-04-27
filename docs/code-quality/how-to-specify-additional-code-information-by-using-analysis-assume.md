---
title: 'Как: укажите дополнительный код сведения с помощью _Analysis_assume'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: ce8102bbc790019490c4dc2a2ccbfab7d8c33981
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>Как: укажите дополнительный код сведения с помощью _Analysis_assume
Возможность создания подсказок для средства анализа кода для кода C/C++, который будет помочь в процессе анализа и снижают количество предупреждений. Для предоставления дополнительных сведений, используйте следующую функцию:

 `_Analysis_assume(`  `expr`  `)`

 `expr` -любое выражение, которое предполагается, что принимает значение true.

 Средство анализа кода предполагает, что условие, представленный с помощью выражения является значение true, если в точке, где функции и сохраняет значение true, пока не будет изменено выражение, например, путем присваивания переменной.

> [!NOTE]
>  `_Analysis_assume` не влияет на оптимизацию кода. За пределами средство анализа кода `_Analysis_assume` определяется как холостой.

## <a name="example"></a>Пример
 В следующем коде используется `_Analysis_assume` исправление предупреждения анализа кода [C6388](../code-quality/c6388.md):

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