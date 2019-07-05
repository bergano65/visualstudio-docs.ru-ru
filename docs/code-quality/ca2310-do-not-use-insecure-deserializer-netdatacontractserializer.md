---
title: 'CA2310: Не используйте небезопасных десериализатор NetDataContractSerializer'
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
- CA2310
- DoNotUseInsecureDeserializerNetDataContractSerializer
ms.openlocfilehash: e4af6bbfbd7e14b99f39ffa0adb5d1117c200d9a
ms.sourcegitcommit: db30651dc0ce4d0b274479b23a6bd102a5559098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65135432"
---
# <a name="ca2310-do-not-use-insecure-deserializer-netdatacontractserializer"></a>CA2310: Не используйте небезопасных десериализатор NetDataContractSerializer

|||
|-|-|
|TypeName|DoNotUseInsecureDeserializerNetDataContractSerializer|
|CheckId|CA2310|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Объект <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> был вызван или ссылка на метод десериализации.

## <a name="rule-description"></a>Описание правила

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Это правило находит <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> десериализации вызовы методов или ссылки. Если вы хотите выполнить десериализацию только тогда, когда <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> свойство имеет значение ограничения типов, отключите это правило и включите правила [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) и [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) вместо этого.

## <a name="how-to-fix-violations"></a>Устранение нарушений

- По возможности вместо этого используйте безопасный сериализатор и **не позволяет злоумышленнику указать произвольный тип для десериализации**. Некоторые более безопасным сериализаторах включают:
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> -Никогда не используйте <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>. Если необходимо использовать Сопоставитель типов, ограничьте список ожидаемый десериализованные типы.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET — используйте TypeNameHandling.None. Если необходимо использовать другое значение для TypeNameHandling, ограничиваются ожидаемого списка с помощью пользовательских ISerializationBinder десериализованные типы.
  - Буферы протокола
- Сделайте несанкционированного сериализованные данные. После сериализации криптографически подписать сериализованные данные. Перед десериализацией проверки криптографической подписи. Защитите криптографический ключ из огласку и проектирования для смены ключей.
- Ограничьте десериализованные типы. Создание пользовательского <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>. Перед десериализацией с <xref:System.Runtime.Serialization.NetDataContractSerializer>, задайте <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> свойство для экземпляра пользовательского <xref:System.Runtime.Serialization.SerializationBinder>. В переопределенном <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> метод, если тип является неожиданным, создавать исключение.
- При ограничении десериализованные типы, вы можете отключить это правило и включите правила [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) и [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md). Правила [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) и [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) справки, чтобы убедиться, что <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> всегда будет задано значение перед десериализацией.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Примеры псевдокода

### <a name="violation"></a>Нарушение

```csharp
using System.IO;
using System.Runtime.Serialization;

public class ExampleClass
{
    public object MyDeserialize(byte[] bytes)
    {
        NetDataContractSerializer serializer = new NetDataContractSerializer();
        return serializer.Deserialize(new MemoryStream(bytes));
    }
}
```

```vb
Imports System.IO
Imports System.Runtime.Serialization

Public Class ExampleClass
    Public Function MyDeserialize(bytes As Byte()) As Object
        Dim serializer As NetDataContractSerializer = New NetDataContractSerializer()
        Return serializer.Deserialize(New MemoryStream(bytes))
    End Function
End Class
```

## <a name="related-rules"></a>Связанные правила

[CA2311: Выполняет десериализацию предварительно задать NetDataContractSerializer.Binder](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md)

[CA2312: Убедитесь, что NetDataContractSerializer.Binder устанавливается перед десериализацией](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md)
