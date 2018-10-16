---
title: 'CA1500: имена переменных не должны совпадать с именами полей'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
helpviewer_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
ms.assetid: fa0e5029-79e9-4a33-8576-787ac3c26c39
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 74f9cfadc4bc413c3b176d5f37f1017074547435
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548286"
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500: имена переменных не должны совпадать с именами полей

|||
|-|-|
|TypeName|VariableNamesShouldNotMatchFieldNames|
|CheckId|CA1500|
|Категория|Microsoft.Maintainability|
|Критическое изменение|При возникновении на параметр, который имеет то же имя в качестве поля:<br /><br /> Не критическое, если поле и метод, который объявляет, что параметры не видны за пределами сборки, независимо от того, сделанные изменения.<br />-Критическое, если вы измените имя поля и могут быть видны за пределами сборки.<br />-Критическое, если изменить имя параметра и метод, который объявляет его видно за пределами сборки.<br /><br /> При нарушении в локальной переменной, которая имеет то же имя в качестве поля:<br /><br /> Не критическое, если поле не видны за пределами сборки, независимо от того, изменения, внесенные.<br />Не критическое, если вы измените имя локальной переменной и не изменяйте имя поля.<br />-Критическое, если изменить имя поля, и он может отображаться за пределами сборки.|

## <a name="cause"></a>Причина

Метод экземпляра объявляет параметр или локальную переменную, имя которого совпадает с именем поля экземпляра объявляющего типа. Для перехвата локальные переменные, которые нарушают правила, протестированных сборки должны быть построены с помощью отладочную информацию и связанный PDB-файл должен быть доступен.

## <a name="rule-description"></a>Описание правила

Если имя поля экземпляра совпадает с параметром или имя локальной переменной, поля экземпляра осуществляется с помощью `this` (`Me` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) ключевое слово при использовании внутри тела метода. При обслуживании кода, это просто забыть это различие, предполагается, что параметр или локальная переменная ссылается на поле экземпляра, что приводит к ошибкам. Это значение равно true, особенно для длительных метод тела выражений.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, переименуйте параметр или переменная или поле.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример

Следующий пример показывает два нарушения данного правила.

[!code-vb[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/VisualBasic/ca1500-variable-names-should-not-match-field-names_1.vb)]
[!code-csharp[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/CSharp/ca1500-variable-names-should-not-match-field-names_1.cs)]