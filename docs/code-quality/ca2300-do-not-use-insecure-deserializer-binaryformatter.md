---
title: CA2300. Не используйте небезопасный десериализатор BinaryFormatter
ms.date: 04/05/2019
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2e3ad5c23d880c65a57fdd94739475537c1aebff
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59367302"
---
# <a name="ca2300-do-not-use-insecure-deserializer-binaryformatter"></a>CA2300. Не используйте небезопасный десериализатор BinaryFormatter

|||
|-|-|
|TypeName|DoNotUseInsecureDeserializerBinaryFormatter|
|CheckId|CA2300|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Объект <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> был вызван или ссылка на метод десериализации.

## <a name="rule-description"></a>Описание правила

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Это правило находит <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> десериализации вызовы методов или ссылки. Если вы хотите выполнить десериализацию только тогда, когда <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> свойство имеет значение ограничения типов, отключите это правило и включите правила [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) и [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md) вместо этого.

## <a name="how-to-fix-violations"></a>Устранение нарушений

- По возможности вместо этого используйте безопасный сериализатор и **не позволяет злоумышленнику указать произвольный тип для десериализации**. Некоторые более безопасным сериализаторах включают:
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> -Никогда не используйте <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>. Если необходимо использовать Сопоставитель типов, необходимо ограничить десериализованные типы на ожидаемый список.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - NewtonSoft Json.NET — используйте TypeNameHandling.None. Если необходимо использовать другое значение для TypeNameHandling, необходимо ограничить десериализованные типы на ожидаемый список.
  - Буферы протокола
- Сделайте незаконного сериализованные данные. После сериализации криптографически подписать сериализованные данные. Перед десериализацией, проверки криптографической подписи. Вы должны защищать криптографические ключи от огласку и вести разработку сменой ключей.
- Ограничьте десериализованные типы. Создание пользовательского <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>. Перед десериализацией с <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, задайте <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> свойство для экземпляра пользовательского <xref:System.Runtime.Serialization.SerializationBinder>. В переопределенном <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> метод, если обнаруживается неожиданный тип затем выдал исключение.
 - При ограничении десериализованные типы, вы можете отключить это правило и включите правила [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) и [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md). Включение правил [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) и [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md) поможет убедиться, что <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> всегда будет задано значение перед десериализацией.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

- Его можно безопасно подавить предупреждение из этого правила, если вы знаете, что входное значение является доверенным. Рассмотрим, что со временем может меняться потоки границ и данных доверия приложения.
- Это безопасно отключить это предупреждение, если вы являетесь одним из выше меры предосторожности.

## <a name="pseudo-code-examples"></a>Примеры псевдокода

### <a name="violation"></a>Нарушение

```csharp
using System.IO;
using System.Runtime.Serialization.Formatters.Binary;

public class ExampleClass
{
    public object MyDeserialize(byte[] bytes)
    {
        BinaryFormatter formatter = new BinaryFormatter();
        return formatter.Deserialize(new MemoryStream(bytes));
    }
}
```

```vb
Imports System.IO
Imports System.Runtime.Serialization.Formatters.Binary

Public Class ExampleClass
    Public Function MyDeserialize(bytes As Byte()) As Object
        Dim formatter As BinaryFormatter = New BinaryFormatter()
        Return formatter.Deserialize(New MemoryStream(bytes))
    End Function
End Class
```

## <a name="related-rules"></a>Связанные правила

[CA2301: Не вызывайте BinaryFormatter.Deserialize предварительно задать BinaryFormatter.Binder](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)

[CA2302: Убедитесь, что перед вызовом BinaryFormatter.Deserialize задается BinaryFormatter.Binder](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md)