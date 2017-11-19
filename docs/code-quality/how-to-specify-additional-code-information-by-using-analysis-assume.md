---
title: "Как: укажите дополнительный код сведения с помощью __analysis_assume | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __analysis_assume
helpviewer_keywords: __analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 72892328e9e0cd2f85176cfc4a514d64f853d209
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2017
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>Практическое руководство. Добавление дополнительных сведений о коде с помощью __analysis_assume
Возможность создания подсказок для средства анализа кода для кода C/C++, который будет помочь в процессе анализа и снижают количество предупреждений. Для предоставления дополнительных сведений, используйте следующую функцию:  
  
 `__analysis_assume(`  `expr`  `)`  
  
 `expr`-любое выражение, которое предполагается, что принимает значение true.  
  
 Средство анализа кода предполагает, что условие, представленный с помощью выражения является значение true, если в точке, где функции и сохраняет значение true, пока не будет изменено выражение, например, путем присваивания переменной.  
  
> [!NOTE]
>  `__analysis_assume`не влияет на оптимизацию кода. За пределами средство анализа кода `__analysis_assume` определяется как холостой.  
  
## <a name="example"></a>Пример  
 В следующем коде используется `__analysis_assume` исправление предупреждения анализа кода [C6388](../code-quality/c6388.md):  
  
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
 [__assume](/cpp/intrinsics/assume)