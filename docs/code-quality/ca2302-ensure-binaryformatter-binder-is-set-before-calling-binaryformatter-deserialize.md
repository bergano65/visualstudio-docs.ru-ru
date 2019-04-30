---
title: CA2302. Убедитесь, что BinaryFormatter.Binder задан перед вызовом BinaryFormatter.Deserialize
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
ms.openlocfilehash: f8f2e98edd0cb1094422576b484be34f4f7ba8de
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545284"
---
# <a name="ca2302-ensure-binaryformatterbinder-is-set-before-calling-binaryformatterdeserialize"></a>CA2302. Убедитесь, что BinaryFormatter.Binder задан перед вызовом BinaryFormatter.Deserialize

|||
|-|-|
|TypeName|EnsureBinaryFormatterBinderIsSetBeforeCallingBinaryFormatterDeserialize|
|CheckId|CA2302|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Объект <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> был вызван или ссылка на метод десериализации и <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> свойство может иметь значение null.

## <a name="rule-description"></a>Описание правила

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Это правило находит <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> метод десериализации вызывает или ссылается на, когда <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> может иметь значение null. Если вы хотите запретить какой-либо десериализации с <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> вне зависимости от <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> свойство, отключите это правило и [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)и включить правило [CA2300](ca2300-do-not-use-insecure-deserializer-binaryformatter.md).

## <a name="how-to-fix-violations"></a>Устранение нарушений

- По возможности вместо этого используйте безопасный сериализатор и **не позволяет злоумышленнику указать произвольный тип для десериализации**. Некоторые более безопасным сериализаторах включают:
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> -Никогда не используйте <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>. Если необходимо использовать Сопоставитель типов, ограничьте список ожидаемый десериализованные типы.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - NewtonSoft Json.NET — используйте TypeNameHandling.None. Если необходимо использовать другое значение для TypeNameHandling, ограничиваются ожидаемого списка с помощью пользовательских ISerializationBinder десериализованные типы.
  - Буферы протокола
- Сделайте несанкционированного сериализованные данные. После сериализации криптографически подписать сериализованные данные. Перед десериализацией проверки криптографической подписи. Предотвратить раскрытие криптографический ключ и создать для смены ключей.
- Ограничьте десериализованные типы. Создание пользовательского <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>. Перед десериализацией с <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, задайте <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> свойство для экземпляра пользовательского <xref:System.Runtime.Serialization.SerializationBinder>. В переопределенном <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> метод, если обнаруживается неожиданный тип затем выдал исключение.
  - Убедитесь, что все ветви кода <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> набор свойств.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Примеры псевдокода

### <a name="violation"></a>Нарушение

```csharp
using System;
using System.IO;
using System.Runtime.Serialization.Formatters.Binary;

[Serializable]
public class BookRecord
{
    public string Title { get; set; }
    public string Author { get; set; }
    public int PageCount { get; set; }
    public AisleLocation Location { get; set; }
}

[Serializable]
public class AisleLocation
{
    public char Aisle { get; set; }
    public byte Shelf { get; set; }
}

public class ExampleClass
{
    public BinaryFormatter Formatter { get; set; }

    public BookRecord DeserializeBookRecord(byte[] bytes)
    {
        using (MemoryStream ms = new MemoryStream(bytes))
        {
            return (BookRecord) this.Formatter.Deserialize(ms);
        }
    }
}
```

```vb
Imports System
Imports System.IO
Imports System.Runtime.Serialization.Formatters.Binary

<Serializable()>
Public Class BookRecord
    Public Property Title As String
    Public Property Author As String
    Public Property Location As AisleLocation
End Class

<Serializable()>
Public Class AisleLocation
    Public Property Aisle As Char
    Public Property Shelf As Byte
End Class

Public Class ExampleClass
    Public Property Formatter As BinaryFormatter

    Public Function DeserializeBookRecord(bytes As Byte()) As BookRecord
        Using ms As MemoryStream = New MemoryStream(bytes)
            Return CType(Me.Formatter.Deserialize(ms), BookRecord)
        End Using
    End Function
End Class
```

### <a name="solution"></a>Решение

```csharp
using System;
using System.IO;
using System.Runtime.Serialization;
using System.Runtime.Serialization.Formatters.Binary;

public class BookRecordSerializationBinder : SerializationBinder
{
    public override Type BindToType(string assemblyName, string typeName)
    {
        // One way to discover expected types is through testing deserialization
        // of **valid** data and logging the types used.

        ////Console.WriteLine($"BindToType('{assemblyName}', '{typeName}')");

        if (typeName == "BookRecord" || typeName == "AisleLocation")
        {
            return null;
        }
        else
        {
            throw new ArgumentException("Unexpected type", nameof(typeName));
        }
    }
}

[Serializable]
public class BookRecord
{
    public string Title { get; set; }
    public string Author { get; set; }
    public int PageCount { get; set; }
    public AisleLocation Location { get; set; }
}

[Serializable]
public class AisleLocation
{
    public char Aisle { get; set; }
    public byte Shelf { get; set; }
}

public class ExampleClass
{
    public BookRecord DeserializeBookRecord(byte[] bytes)
    {
        BinaryFormatter formatter = new BinaryFormatter();
        formatter.Binder = new BookRecordSerializationBinder();
        using (MemoryStream ms = new MemoryStream(bytes))
        {
            return (BookRecord) formatter.Deserialize(ms);
        }
    }
}
```

```vb
Imports System
Imports System.IO
Imports System.Runtime.Serialization
Imports System.Runtime.Serialization.Formatters.Binary

Public Class BookRecordSerializationBinder
    Inherits SerializationBinder

    Public Overrides Function BindToType(assemblyName As String, typeName As String) As Type
        ' One way to discover expected types is through testing deserialization
        ' of **valid** data and logging the types used.

        'Console.WriteLine($"BindToType('{assemblyName}', '{typeName}')")

        If typeName = "BinaryFormatterVB.BookRecord" Or typeName = "BinaryFormatterVB.AisleLocation" Then
            Return Nothing
        Else
            Throw New ArgumentException("Unexpected type", NameOf(typeName))
        End If
    End Function
End Class

<Serializable()>
Public Class BookRecord
    Public Property Title As String
    Public Property Author As String
    Public Property Location As AisleLocation
End Class

<Serializable()>
Public Class AisleLocation
    Public Property Aisle As Char
    Public Property Shelf As Byte
End Class

Public Class ExampleClass
    Public Function DeserializeBookRecord(bytes As Byte()) As BookRecord
        Dim formatter As BinaryFormatter = New BinaryFormatter()
        formatter.Binder = New BookRecordSerializationBinder()
        Using ms As MemoryStream = New MemoryStream(bytes)
            Return CType(formatter.Deserialize(ms), BookRecord)
        End Using
    End Function
End Class
```

## <a name="related-rules"></a>Связанные правила

[CA2300: Не используйте небезопасных десериализатор BinaryFormatter](ca2300-do-not-use-insecure-deserializer-binaryformatter.md)

[CA2301: Не вызывайте BinaryFormatter.Deserialize предварительно задать BinaryFormatter.Binder](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)
