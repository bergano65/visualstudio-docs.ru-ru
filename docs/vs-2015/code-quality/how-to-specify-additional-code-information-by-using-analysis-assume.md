---
title: Практическое руководство. Укажите дополнительный код сведения с помощью __analysis_assume | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- __analysis_assume
helpviewer_keywords:
- __analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: dfae7d858dbb462ec6a93de9eb63b1b3b2a711ab
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685822"
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>Практическое руководство. Добавление дополнительных сведений о коде с помощью _Analysis_assume
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Возможность создания подсказок для средства анализа кода для кода C/C++, который поможет в процессе анализа и снижают количество предупреждений. Для предоставления дополнительных сведений, используйте следующую функцию:  
  
 `__analysis_assume(`  `expr`  `)`  
  
 `expr` -любое выражение, которое предполагается, что имеют значение true.  
  
 Средство анализа кода предполагается, что условие, представленный с помощью выражения имеет значение true, если в точке, где отображается функция и сохраняет значение true, пока выражение будет изменено, например, путем присваивания переменной.  
  
> [!NOTE]
> `__analysis_assume` не влияет на оптимизации кода. За пределами средства анализа кода `__analysis_assume` определяется как холостой.  
  
## <a name="example"></a>Пример  
 В следующем коде используется `__analysis_assume` для устранения предупреждения анализа кода [C6388](../code-quality/c6388.md):  
  
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
  __analysis_assume(pc == NULL);   
  f(pc);  
}  
```  
  
## <a name="see-also"></a>См. также  
 [__assume](https://msdn.microsoft.com/library/d8565123-b132-44b1-8235-5a8c8bff85a7)
