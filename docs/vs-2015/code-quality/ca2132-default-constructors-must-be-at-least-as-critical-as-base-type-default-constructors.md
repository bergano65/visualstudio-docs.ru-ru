---
title: 'CA2132: Конструкторы по умолчанию должны быть по крайней мере настолько критичными, как конструкторы базовых типов по умолчанию | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f8452ac1c8d75c684a0f8e7a83c8ae3436e5c2b7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49811158"
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132: конструкторы по умолчанию должны быть по крайней мере настолько критичными, как и конструкторы базовых типов по умолчанию
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DefaultConstructorsMustHaveConsistentTransparency|
|CheckId|CA2132|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

> [!NOTE]
>  Это предупреждение применяется только к коду, на котором работает CoreCLR (версия среды CLR, предназначенную для веб-приложений Silverlight).

## <a name="cause"></a>Причина
 Атрибут прозрачности конструктора по умолчанию производного класса не такой критический, как прозрачность базового класса.

## <a name="rule-description"></a>Описание правила
 Типы и члены с атрибутом <xref:System.Security.SecurityCriticalAttribute> не может использоваться кодом приложения Silverlight. Критичные в плане безопасности типы и элементы могут использоваться только надежным кодом в среде .NET Framework для библиотеки классов Silverlight. Поскольку открытая или защищенная конструкция в производном классе должна иметь ту же или большую прозрачность, чем ее базовый класс, класс в приложении не может быть производным от класса, помеченного как SecurityCritical.

 Для кода платформы CoreCLR Если базовый тип имеет открытый или защищенный непрозрачный по умолчанию конструктор затем производный тип должен подчиняться правилам наследования конструктора по умолчанию. Производный тип также должен иметь конструктор по умолчанию, и этот конструктор должен быть по крайней мере конструктор критические по умолчанию базового типа.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение, удалите тип или не являются производными от типа не прозрачный с точки зрения безопасности.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не следует отключать предупреждения из этого правила. Нарушение этого правила в коде приложения приведет к CoreCLR отказывается загрузить тип с <xref:System.TypeLoadException>.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2132.defaultconstructorsmusthaveconsistenttransparency/cs/ca2132 - defaultconstructorsmusthaveconsistenttransparency.cs#1)]

### <a name="comments"></a>Комментарии



