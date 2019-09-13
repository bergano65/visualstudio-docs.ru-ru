---
title: CA2310. Не используйте небезопасный десериализатор NetDataContractSerializer
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
ms.openlocfilehash: 09496fd11945ec4d419cc215569a7436f96d71ec
ms.sourcegitcommit: 673b9364fc9a96b027662dcb4cf5d61cab60ef11
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/21/2019
ms.locfileid: "69891148"
---
# <a name="ca2310-do-not-use-insecure-deserializer-netdatacontractserializer"></a>CA2310. Не используйте небезопасный десериализатор NetDataContractSerializer

|||
|-|-|
|TypeName|донотусеинсекуредесериализернетдатаконтрактсериализер|
|CheckId|CA2310|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

<xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> Был вызван метод десериализации или указана ссылка.

## <a name="rule-description"></a>Описание правила

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Это правило находит <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> вызовы метода десериализации или ссылки. Если требуется выполнить десериализацию только в <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> том случае, если свойство имеет значение ограничить типы, отключите это правило и включите правила [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) и [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) .

## <a name="how-to-fix-violations"></a>Устранение нарушений

- Если это возможно, используйте защищенный сериализатор, а **не разрешите ему указать произвольный тип для десериализации**. Ниже приведены некоторые более безопасные сериализаторы.
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType>-Никогда не <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>использовать. Если необходимо использовать сопоставитель типов, ограничьте десериализованные типы до ожидаемого списка.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET — используйте Типенамехандлинг. None. Если необходимо использовать другое значение для Типенамехандлинг, ограничьте десериализованные типы до ожидаемого списка с помощью настраиваемого Исериализатионбиндер.
  - Буферы протоколов
- Сделайте сериализованные данные несанкционированными. После сериализации криптографически подписывает сериализованные данные. Перед десериализациюм проверьте криптографическую подпись. Защитите криптографический ключ от раскрывать и разрабатывать для смены ключей.
- Ограничьте десериализованные типы. Реализуйте пользовательский <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>интерфейс. Перед десериализациюм <xref:System.Runtime.Serialization.NetDataContractSerializer>с <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> присвойте свойству экземпляр пользовательского <xref:System.Runtime.Serialization.SerializationBinder>. В переопределенном <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> методе, если тип является непредвиденным, вызовите исключение для отмены десериализации.
  - При ограничении десериализованных типов может потребоваться отключить это правило и включить правила [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) и [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md). Правила [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) и [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) помогают <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> убедиться, что свойство всегда задано перед десериализациям.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Примеры псевдо-кода

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

[CA2311: Не выполнять десериализацию без предварительного задания NetDataContractSerializer. BINDER](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md)

[CA2312: Убедитесь, что NetDataContractSerializer. BINDER задан до десериализации](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md)
