---
title: 'CA2132: конструкторы по умолчанию должны иметь по крайней мере такие же критические, как конструкторы по умолчанию базового типа | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ae271b116b372d4ae732d97ff3f9651ff9db426
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72643298"
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132: конструкторы по умолчанию должны быть по крайней мере настолько критичными, как и конструкторы базовых типов по умолчанию
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|дефаултконструкторсмуссавеконсистенттранспаренци|
|CheckId|CA2132|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

> [!NOTE]
> Это предупреждение применяется только к коду, на котором работает CoreCLR (версия CLR, относящаяся к веб-приложениям Silverlight).

## <a name="cause"></a>Причина
 Атрибут прозрачности конструктора по умолчанию производного класса не так важен, как прозрачность базового класса.

## <a name="rule-description"></a>Описание правила
 Типы и члены, имеющие <xref:System.Security.SecurityCriticalAttribute>, не могут использоваться кодом приложения Silverlight. Критичные в плане безопасности типы и элементы могут использоваться только надежным кодом в среде .NET Framework для библиотеки классов Silverlight. Поскольку открытая или защищенная конструкция в производном классе должна иметь ту же или большую прозрачность, чем ее базовый класс, класс в приложении не может быть производным от класса, помеченного как SecurityCritical.

 Для кода платформы CoreCLR, если базовый тип имеет открытый или защищенный непрозрачный конструктор по умолчанию, производный тип должен соблюдать правила наследования конструктора по умолчанию. Производный тип также должен иметь конструктор по умолчанию, и этот конструктор должен быть по крайней мере критическим конструктором по умолчанию базового типа.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение, удалите тип или не наследовать от непрозрачного типа безопасности.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте вывод предупреждений из этого правила. Нарушения этого правила в коде приложения приведут к тому, что CoreCLR отказывается загружать тип с <xref:System.TypeLoadException>.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2132.defaultconstructorsmusthaveconsistenttransparency/cs/ca2132 - defaultconstructorsmusthaveconsistenttransparency.cs#1)]

### <a name="comments"></a>Комментарии
