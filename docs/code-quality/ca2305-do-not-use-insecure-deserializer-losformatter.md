---
title: CA2305. Не используйте небезопасный десериализатор LosFormatter
ms.date: 05/01/2019
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
f1_keywords:
- CA2305
- DoNotUseInsecureDeserializerLosFormatter
ms.openlocfilehash: 145d45d79f1dda27d5c69f0c481277572d3eeaa2
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237727"
---
# <a name="ca2305-do-not-use-insecure-deserializer-losformatter"></a>CA2305. Не используйте небезопасный десериализатор LosFormatter

|||
|-|-|
|TypeName|донотусеинсекуредесериализерлосформаттер|
|CheckId|CA2305|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

<xref:System.Web.UI.LosFormatter?displayProperty=nameWithType> Был вызван метод десериализации или указана ссылка.

## <a name="rule-description"></a>Описание правила

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Это правило находит <xref:System.Web.UI.LosFormatter?displayProperty=nameWithType> вызовы метода десериализации или ссылки.

## <a name="how-to-fix-violations"></a>Устранение нарушений

[!INCLUDE[insecure-deserializers-fixes-for-always-insecure-deserializers](includes/insecure-deserializers-fixes-for-always-insecure-deserializers-md.md)]

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Примеры псевдо-кода

### <a name="violation"></a>Нарушение

```csharp
using System.IO;
using System.Web.UI;

public class ExampleClass
{
    public object MyDeserialize(byte[] bytes)
    {
        LosFormatter formatter = new LosFormatter();
        return formatter.Deserialize(new MemoryStream(bytes));
    }
}
```

```vb
Imports System.IO
Imports System.Web.UI

Public Class ExampleClass
    Public Function MyDeserialize(bytes As Byte()) As Object
        Dim formatter As LosFormatter = New LosFormatter()
        Return formatter.Deserialize(New MemoryStream(bytes))
    End Function
End Class
```