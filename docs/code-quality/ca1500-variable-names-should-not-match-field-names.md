---
title: 'CA1500: имена переменных не должны совпадать с именами полей'
ms.date: 11/04/2016
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
ms.workload:
- multiple
ms.openlocfilehash: f291b603c94292cc86536a212a4ab8286600740b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500: имена переменных не должны совпадать с именами полей
|||
|-|-|
|TypeName|VariableNamesShouldNotMatchFieldNames|
|CheckId|CA1500|
|Категория|Microsoft.Maintainability|
|Критическое изменение|При нарушении в параметре с тем же именем, что поля:<br /><br /> Не критическое, если поле и метод, который объявляет, что параметры не видны за пределами сборки, независимо от того, сделанные изменения.<br />-Критическое, если изменить имя поля и может отображаться за пределами сборки.<br />-Критическое, если изменить имя параметра и метод, который объявляет его можно будет увидеть за пределами сборки.<br /><br /> При возникновении на локальную переменную с тем же именем, что поля:<br /><br /> Не критическое, если поле не может быть видим за пределами сборки, независимо от произведенных изменений.<br />Не критическое, если изменить имя локальной переменной и не изменяйте имя поля.<br />-Критическое, если изменить имя поля, и может отображаться за пределами сборки.|

## <a name="cause"></a>Причина
 Метод экземпляра объявляет параметр или локальную переменную, имя которого совпадает с именем поля экземпляра объявляющего типа. Для перехвата локальные переменные, которые нарушают правило, тестируемой сборки должны быть построены с использованием отладочной информации и связанный PDB-файл должен быть доступен.

## <a name="rule-description"></a>Описание правила
 Если имя поля экземпляра совпадает с параметром или имя локальной переменной, поле экземпляра осуществляется с помощью `this` (`Me` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) ключевое слово, если в теле метода. При поддержке кода можно легко забыть это различие, и предполагается, что параметр или локальная переменная ссылается на поле экземпляра, который приводит к ошибкам. Это значение равно true, особенно для тела метода длительное время.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, переименуйте параметр или переменная или поле.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показано два нарушения данного правила.

 [!code-vb[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/VisualBasic/ca1500-variable-names-should-not-match-field-names_1.vb)]
 [!code-csharp[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/CSharp/ca1500-variable-names-should-not-match-field-names_1.cs)]