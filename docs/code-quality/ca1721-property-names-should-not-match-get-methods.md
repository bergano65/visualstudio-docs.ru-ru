---
title: CA1721. Имена свойств не должны совпадать с именами методов get
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: bf16a9edf25132aa8b58702f01563b8d7ccf109a
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841496"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721. Имена свойств не должны совпадать с именами методов get

|||
|-|-|
|TypeName|PropertyNamesShouldNotMatchGetMethods|
|CheckId|CA1721|
|Категория|Microsoft.Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Имя элемента начинается с «Get» и в противном случае соответствует имени свойства. Например тип, содержащий метод, который называется «GetColor» и свойство с именем «Цвет» вызвать нарушение правила.

По умолчанию это правило считывает только Внешне видимые элементы и свойства, но это [можно настроить](#configurability).

## <a name="rule-description"></a>Описание правила

Методы Get и свойства должны иметь имена, позволяющие четко различать их функции.

Соглашения об именовании обеспечивают единообразие библиотек, предназначенных среда CLR. Эта согласованность, сокращает время, необходимое для изучать новую библиотеку программного обеспечения и повышает уверенность клиента в том, что библиотека была разработана тому, кто имеет опыт в разработке управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Измените имя, чтобы он не соответствует имени метода, который добавляется префикс «Get».

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Для этого правила отключать вывод предупреждений не следует.

> [!NOTE]
> Это предупреждение можно не указывать, если метод «Get» вызвана реализация IExtenderProvider-интерфейс.

## <a name="configurability"></a>Возможность настройки

Если у вас это правило из [анализаторы FxCop](install-fxcop-analyzers.md) (а не с помощью функций анализа статического кода), можно настроить, какие части вашей базы кода, чтобы применить это правило, в зависимости от их доступности. Например чтобы указать, что правило должно выполняться только для рабочей области не являющийся открытым API, добавьте следующую пару "ключ значение" файла editorconfig в проект:

```ini
dotnet_code_quality.ca1721.api_surface = private, internal
```

Этот параметр для только что это правило, для всех правил или для всех правил можно настроить в этой категории (именования). Дополнительные сведения см. в разделе [анализаторы FxCop, Настройка](configure-fxcop-analyzers.md).

## <a name="example"></a>Пример

В следующем примере содержится метод и свойство, которое нарушает это правило.

[!code-csharp[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/CSharp/ca1721-property-names-should-not-match-get-methods_1.cs)]
[!code-vb[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/VisualBasic/ca1721-property-names-should-not-match-get-methods_1.vb)]

## <a name="related-rules"></a>Связанные правила

- [CA1024: Используйте свойства, если это уместно](../code-quality/ca1024-use-properties-where-appropriate.md)