---
title: 'CA1026: Не удается использовать параметры по умолчанию | Документация Майкрософт'
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
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2fab184cba9084dbcfa38ebb60aec53077900144
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47592337"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026: не следует использовать параметры по умолчанию
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1026: не следует использовать параметры по умолчанию](https://docs.microsoft.com/visualstudio/code-quality/ca1026-default-parameters-should-not-be-used).

|||
|-|-|
|TypeName|DefaultParametersShouldNotBeUsed|
|CheckId|CA1026|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Видимый извне тип содержит видимое извне метод, использующий параметр по умолчанию.

## <a name="rule-description"></a>Описание правила
 Методы, использующие параметры по умолчанию разрешены в общеязыковой спецификацией (CLS); Однако CLS разрешает компиляторам не учитывать значения, присвоенные этим параметрам. Код, написанный для компиляторов, которые не учитывают значения параметров по умолчанию необходимо явно предоставить аргументы для каждого параметра по умолчанию. Для однородной работы с различными языками программирования, следует заменять методы, использующие параметры по умолчанию перегрузки методов, предоставляющие параметры по умолчанию.

 Компилятор игнорирует значения параметров по умолчанию для управляемых расширений для C++, при доступе к управляемым кодом. Компилятор Visual Basic поддерживает методы с параметрами по умолчанию, использующих [необязательно](http://msdn.microsoft.com/library/4571ce88-a539-4115-b230-54eb277c6aa7) ключевое слово.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, замените метод, который использует параметры по умолчанию с перегрузкой методов, предоставляющих параметры по умолчанию.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В примере показан метод, который использует параметры по умолчанию и перегруженные методы, обеспечивающие аналогичную функциональность.

 [!code-vb[FxCop.Design.DefaultParameters#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DefaultParameters/vb/FxCop.Design.DefaultParameters.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1025: замените повторяющиеся аргументы массивом параметров](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>См. также
 [Независимость от языка и независимые от языка компоненты](http://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)



