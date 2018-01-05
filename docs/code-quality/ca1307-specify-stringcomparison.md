---
title: "CA1307: Укажите StringComparison | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7087cfe23f7911ec33891a70cd88cf47ee9e4a7b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: укажите StringComparison
|||  
|-|-|  
|TypeName|SpecifyStringComparison|  
|CheckId|CA1307|  
|Категория|Microsoft.Globalization|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Операции сравнения строк используется перегрузка метода, которая не задает <xref:System.StringComparison> параметра.  
  
## <a name="rule-description"></a>Описание правила  
 Многие строковые операции, наиболее важные <xref:System.String.Compare%2A> и <xref:System.String.Equals%2A> обеспечивают перегрузку, которая принимает <xref:System.StringComparison> значение перечисления в качестве параметра.  
  
 Каждый раз, когда существует перегрузка, принимающую <xref:System.StringComparison> параметра, его следует использовать вместо перегрузку, которая не принимает этот параметр. Явно задать этот параметр, код часто становится более ясным и проще.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, измените методы сравнения строк на перегрузки, принимающие <xref:System.StringComparison> перечисление как параметр. Например: измените `String.Compare(str1, str2)` для `String.Compare(str1, str2, StringComparison.Ordinal)`.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Можно безопасно отключать предупреждение из этого правила, если библиотека или приложение предназначено для ограниченного круга локальных пользователей и поэтому не будет локализовано.  
  
## <a name="see-also"></a>См. также  
 [Предупреждения глобализации](../code-quality/globalization-warnings.md)   
 [CA1309: используйте порядковый параметр StringComparison](../code-quality/ca1309-use-ordinal-stringcomparison.md)