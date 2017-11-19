---
title: "CA1306: Указывайте языковой стандарт для типов данных | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1306
- SetLocaleForDataTypes
helpviewer_keywords:
- CA1306
- SetLocaleForDataTypes
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2a8760aa983cdd798e5ea46fa4161375f0eab7fc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306: указывайте языковой стандарт для типов данных
|||  
|-|-|  
|TypeName|SetLocaleForDataTypes|  
|CheckId|CA1306|  
|Категория|Microsoft.Globalization|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Метод или конструктор для создания одного или нескольких <xref:System.Data.DataTable?displayProperty=fullName> или <xref:System.Data.DataSet?displayProperty=fullName> экземпляров и не было явно задано свойство языка (<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> или <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>).  
  
## <a name="rule-description"></a>Описание правила  
 Языковой стандарт определяет язык и региональные параметры представление элементов данных, таких как форматирование для числовых значений, денежных единиц и порядок сортировки. При создании <xref:System.Data.DataTable> или <xref:System.Data.DataSet>, необходимо явно задать языковой стандарт. По умолчанию языковой стандарт для этих типов — текущий язык и региональные параметры. Для данных, хранящихся в базе данных или файле и доступны глобально, языковой стандарт обычно задается инвариантного языка и региональных параметров (<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>). Если данные используются совместно языков и региональных параметров, использует локаль по умолчанию может привести к содержимое <xref:System.Data.DataTable> или <xref:System.Data.DataSet> должны быть представлены или неправильной интерпретации.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, необходимо явно задать языковой стандарт для <xref:System.Data.DataTable> или <xref:System.Data.DataSet>.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Можно безопасно отключать предупреждение из этого правила, если библиотека или приложение предназначены для ограниченного круга локальных пользователей, данные не являются общими или применение параметров по умолчанию допустимо для всех поддерживаемых сценариях.  
  
## <a name="example"></a>Пример  
 В следующем примере создается два <xref:System.Data.DataTable> экземпляров.  
  
 [!code-csharp[FxCop.Globalization.DataTable#1](../code-quality/codesnippet/CSharp/ca1306-set-locale-for-data-types_1.cs)]  
  
## <a name="see-also"></a>См. также  
 <xref:System.Data.DataTable?displayProperty=fullName>   
 <xref:System.Data.DataSet?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>