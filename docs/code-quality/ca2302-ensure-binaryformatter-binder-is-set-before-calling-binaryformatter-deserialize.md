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
f1_keywords:
- CA2302
- EnsureBinaryFormatterBinderIsSetBeforeCallingBinaryFormatterDeserialize
ms.openlocfilehash: 1d7c87921a226b8918bfaa79fda6de85d710baa4
ms.sourcegitcommit: 673b9364fc9a96b027662dcb4cf5d61cab60ef11
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/21/2019
ms.locfileid: "69891206"
---
# <a name="ca2302-ensure-binaryformatterbinder-is-set-before-calling-binaryformatterdeserialize"></a>CA2302. Убедитесь, что BinaryFormatter.Binder задан перед вызовом BinaryFormatter.Deserialize

|||
|-|-|
|TypeName|енсуребинариформаттербиндериссетбефорекаллингбинариформаттердесериализе|
|CheckId|CA2302|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Метод десериализации был вызван или указан <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> , и свойство может иметь значение null. <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType>

## <a name="rule-description"></a>Описание правила

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Это правило находит <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> вызовы метода десериализации или ссылки, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> если может иметь значение null. Если <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> вы хотите запретить десериализацию независимо <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> от свойства, отключите это правило и [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)и включите правило [CA2300](ca2300-do-not-use-insecure-deserializer-binaryformatter.md).

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
  - Убедитесь, что для <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> всех ветвей кода задано свойство.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Примеры псевдо-кода

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

[CA2300: Не используйте небезопасный десериализатор BinaryFormatter](ca2300-do-not-use-insecure-deserializer-binaryformatter.md)

[CA2301: Не вызывайте BinaryFormatter. десериализацию без предварительного задания BinaryFormatter. BINDER](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)
