---
title: 'CA1026: не следует использовать параметры по умолчанию | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a63d6e788dd1722d0c593469b225a4f1aeb4738d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548450"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026. Не следует использовать параметры по умолчанию
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|DefaultParametersShouldNotBeUsed|
|CheckId|CA1026|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип, видимый извне, содержит метод, видимый извне, который использует параметр по умолчанию.

## <a name="rule-description"></a>Описание правила
 Методы, использующие параметры по умолчанию, разрешены в спецификации CLS; Однако CLS позволяет компиляторам игнорировать значения, назначенные этим параметрам. Код, написанный для компиляторов, игнорирующих значения параметров по умолчанию, должен явно предоставлять аргументы для каждого параметра по умолчанию. Для поддержания поведения в разных языках программирования методы, использующие параметры по умолчанию, должны заменяться перегрузками методов, предоставляющими параметры по умолчанию.

 Компилятор игнорирует значения параметров по умолчанию для управляемого расширения C++ при обращении к управляемому коду. Компилятор Visual Basic поддерживает методы, имеющие параметры по умолчанию, которые используют ключевое слово [Optional](https://msdn.microsoft.com/library/4571ce88-a539-4115-b230-54eb277c6aa7) .

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, замените метод, использующий параметры по умолчанию, на перегрузки методов, которые предоставляют параметры по умолчанию.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показан метод, использующий параметры по умолчанию, и перегруженные методы, которые предоставляют эквивалентную функциональность.

 [!code-vb[FxCop.Design.DefaultParameters#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DefaultParameters/vb/FxCop.Design.DefaultParameters.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1025. Замените повторяющиеся аргументы массивом параметров](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>См. также:
 [Независимость от языка и независимые от языка компоненты](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
