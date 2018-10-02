---
title: 'CA1900: Поля типа значения должны быть переносимыми | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b0a636c1de245aa46adb0b0e43c6802dddf57810
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572806"
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: поля типа значения должны быть переносимыми
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Самая актуальная документация по Visual Studio 2017, см. в разделе [CA1900: поля типа значения должны быть переносимыми](https://docs.microsoft.com/visualstudio/code-quality/ca1900-value-type-fields-should-be-portable) на сайте docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|ValueTypeFieldsShouldBePortable|  
|CheckId|CA1900|  
|Категория|Microsoft.Portability|  
|Критическое изменение|Критическое, если поле может отображаться за пределами сборки.<br /><br /> Non критическое, если поле не отображается за пределами сборки.|  
  
## <a name="cause"></a>Причина  
 Это правило проверяет правильность выравнивания структур, объявленных с явной разметкой, при маршалировании в неуправляемый код на 64-разрядных операционных системах. Обращается к памяти и процесса аварийно, если не будет устранена, это нарушение запрещены IA-64.  
  
## <a name="rule-description"></a>Описание правила  
 Структуры с явной разметкой, содержащей неправильно выровненные поля могут привести к сбоям в 64-разрядных операционных системах.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Все поля, занимающие менее 8 байт, необходим смещения, которые являются кратен их размер и поля, которые включают 8 байт или больше должны иметь смещения, кратные 8. Другим решением является использование `LayoutKind.Sequential` вместо `LayoutKind.Explicit`, если разумным.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Это предупреждение должно быть отменено, только в том случае, если оно возникает в ошибке.

