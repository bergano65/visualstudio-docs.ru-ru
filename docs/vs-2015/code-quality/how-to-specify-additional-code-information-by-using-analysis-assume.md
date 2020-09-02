---
title: Инструкции. Указание дополнительных сведений о коде с помощью __analysis_assume | Документация Майкрософт
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
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: f2f18c9284ec96de7a7b8663aff485962d194282
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "77277971"
---
# <a name="how-to-specify-additional-code-information-by-using-__analysis_assume"></a>Практическое руководство. Добавление дополнительных сведений о коде с помощью __analysis_assume
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете предоставить подсказки средству анализа кода для кода C/C++, который поможет анализировать процесс анализа и сократить число предупреждений. Чтобы предоставить дополнительные сведения, используйте следующую функцию:  
  
 `__analysis_assume(`  `expr`  `)`  
  
 `expr` — любое выражение, для которого предполагается вычисление значения true.  
  
 Средство анализа кода предполагает, что условие, представленное выражением, имеет значение true в точке, где отображается функция, и остается истинной до тех пор, пока выражение не будет изменено, например, путем присваивания переменной.  
  
> [!NOTE]
> `__analysis_assume` не влияет на оптимизацию кода. Вне средства анализа кода `__analysis_assume` определяется как отсутствие операций.  
  
## <a name="example"></a>Пример  
 Следующий код используется `__analysis_assume` для исправления предупреждения анализа кода [C6388](../code-quality/c6388.md):  
  
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
  
## <a name="see-also"></a>См. также:  
 [__assume](https://msdn.microsoft.com/library/d8565123-b132-44b1-8235-5a8c8bff85a7)
