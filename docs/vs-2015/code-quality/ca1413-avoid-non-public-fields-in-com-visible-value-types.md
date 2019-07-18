---
title: CA1413. Избегайте не открытых полей в видимых типах значений COM | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
helpviewer_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 59ca3c5f53dee43bdd73eb706f03792458e71698
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691140"
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413. Не используйте неоткрытые поля в типах значений, видимых для COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|
|CheckId|CA1413|
|Категория|Microsoft.Interoperability|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип значения, который специально помечен как видимый для модели объектов компонента (COM) объявляет поле закрытого экземпляра.

## <a name="rule-description"></a>Описание правила
 Не являющиеся общедоступными поля экземпляров типов значений, отображаемых для модели COM, отображаются для COM-клиентов. Проверьте содержимое поля сведения, не должны предоставляться, или которые могут оказать непреднамеренное эффект проектирования и безопасности.

 По умолчанию все открытые типы значений являются видимыми для модели COM. Тем не менее чтобы сократить число ложных срабатываний, это правило требует видимость COM типа, чтобы задавать явно. Включающая сборка должны быть отмечены <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> присвоено `false` и тип должен быть помечен атрибутом <xref:System.Runtime.InteropServices.ComVisibleAttribute> присвоено `true`.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила и сохранить скрытые поля, измените тип значения ссылочного типа, или удалите <xref:System.Runtime.InteropServices.ComVisibleAttribute> атрибут из типа.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, если допустима раскрытию поля.

## <a name="example"></a>Пример
 В примере показан тип, который нарушает правило.

 [!code-csharp[FxCop.Interoperability.NonpublicField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/cs/FxCop.Interoperability.NonpublicField.cs#1)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/vb/FxCop.Interoperability.NonpublicField.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1407: Не используйте статические члены в видимых COM типах](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Пометьте сборки атрибутом ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>См. также
 [Взаимодействие с неуправляемым кодом](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [уточнение типов .NET для взаимодействия](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)
