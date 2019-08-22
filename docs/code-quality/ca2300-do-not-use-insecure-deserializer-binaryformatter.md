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
f1_keywords:
- CA2300
- DoNotUseInsecureDeserializerBinaryFormatter
ms.openlocfilehash: 8a2bc2929b53843749d939f16057a11c0e944e33
ms.sourcegitcommit: 673b9364fc9a96b027662dcb4cf5d61cab60ef11
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/21/2019
ms.locfileid: "69891210"
---
# <a name="ca2300-do-not-use-insecure-deserializer-binaryformatter"></a>CA2300. Не используйте небезопасный десериализатор BinaryFormatter

|||
|-|-|
|TypeName|донотусеинсекуредесериализербинариформаттер|
|CheckId|CA2300|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> Был вызван метод десериализации или указана ссылка.

## <a name="rule-description"></a>Описание правила

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Это правило находит <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> вызовы метода десериализации или ссылки. Если требуется выполнить десериализацию только в <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> том случае, если свойство имеет значение ограничить типы, отключите это правило и включите правила [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) и [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md) .

## <a name="how-to-fix-violations"></a>Устранение нарушений

- Если это возможно, используйте защищенный сериализатор, а **не разрешите ему указать произвольный тип для десериализации**. Ниже приведены некоторые более безопасные сериализаторы.
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType>-Никогда не <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>использовать. Если необходимо использовать сопоставитель типов, ограничьте десериализованные типы до ожидаемого списка.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET — используйте Типенамехандлинг. None. Если необходимо использовать другое значение для Типенамехандлинг, ограничьте десериализованные типы до ожидаемого списка с помощью настраиваемого Исериализатионбиндер.
  - Буферы протоколов
- Сделайте сериализованные данные несанкционированными. После сериализации криптографически подписывает сериализованные данные. Перед десериализациюм проверьте криптографическую подпись. Защитите криптографический ключ от раскрывать и разрабатывать для смены ключей.
- Ограничьте десериализованные типы. Реализуйте пользовательский <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>интерфейс. Перед десериализациюм <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>с <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> присвойте свойству экземпляр пользовательского <xref:System.Runtime.Serialization.SerializationBinder>. В переопределенном <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> методе, если тип является непредвиденным, вызовите исключение для отмены десериализации.
  - При ограничении десериализованных типов может потребоваться отключить это правило и включить правила [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) и [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md). Правила [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) и [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md) помогают <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> убедиться, что свойство всегда задано перед десериализациям.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Примеры псевдо-кода

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

[CA2301: Не вызывайте BinaryFormatter. десериализацию без предварительного задания BinaryFormatter. BINDER](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)

[CA2302: Убедитесь, что BinaryFormatter. BINDER задан перед вызовом BinaryFormatter. десериализация](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md)