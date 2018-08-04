---
title: 'CA5351: не используйте ослабленные алгоритмы шифрования'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 483f51b3-e186-4433-b48e-5ca24a9a9c94
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6ab1900cf9eda3fccf7606a6a645ace986bcd21d
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512833"
---
# <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351: не используйте ослабленные алгоритмы шифрования
|||
|-|-|
|TypeName|DoNotUseBrokenCryptographicAlgorithms|
|CheckId|CA5351|
|Категория|Microsoft.Cryptography|
|Критическое изменение|Не критическое|

> [!NOTE]
>  Это предупреждение последний раз обновлялось в ноябре 2015 г.

## <a name="cause"></a>Причина
 Функции хэширования, такие как <xref:System.Security.Cryptography.MD5> , и алгоритмы шифрования, такие как <xref:System.Security.Cryptography.DES> и <xref:System.Security.Cryptography.RC2> , могут представлять значительный риск и приводить к раскрытию конфиденциальных сведений методами простых атак, таких как атаки методом подбора и хэш-конфликты.

 Перечисленные ниже алгоритмы шифрования подвержены действию известных криптоаналитических атак. Криптографический хэш-алгоритм <xref:System.Security.Cryptography.MD5> подвержен действию атак хэш-конфликтов.  В зависимости от использования хэш-конфликт может повлечь за собой работу от имени другого пользователя, подделку или другие виды атак на системы, основанные на уникальном результате шифрования функции хэширования. Алгоритмы шифрования <xref:System.Security.Cryptography.DES> и <xref:System.Security.Cryptography.RC2> подвержены действию криптоаналитических атак, которые могут привести к случайному раскрытию зашифрованных данных.

## <a name="rule-description"></a>Описание правила
 Ослабленные алгоритмы шифрования не считаются безопасными, и их использование не рекомендуется. Хэш-алгоритм MD5 восприимчив к известным атакам конфликтов, хотя конкретная уязвимость будет отличаться в зависимости от контекста использования.  Особенно уязвимыми являются хэш-алгоритмы, используемые для обеспечения целостности данных (например, с помощью подписи файла или цифрового сертификата).  В этом контексте злоумышленники могут создать два отдельных комплекта данных, чтобы можно было заменить безопасные данные вредоносными без изменения хэш-значения или аннулирования связанной цифровой подписи.

 Для алгоритмов шифрования:

-   шифрование<xref:System.Security.Cryptography.DES> содержит небольшой размер ключа, который может быть принудительно применен менее чем за день;

-   шифрование<xref:System.Security.Cryptography.RC2> уязвимо к атакам, связанным с ключом, когда злоумышленник обнаруживает математические связи между всеми значениями ключа.

 Это правило срабатывает при обнаружении любой из перечисленных выше функций шифрования в исходном коде и выдает предупреждение для пользователя.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Используйте более надежные варианты шифрования.

-   Для MD5 используйте хэши в [SHA-2](/windows/desktop/SecCrypto/hash-and-signature-algorithms) семейства (например <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384>, <xref:System.Security.Cryptography.SHA256>).

-   Для DES и RC2 используйте шифрование <xref:System.Security.Cryptography.Aes> .

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение из этого правила, если это не утверждено специалистом в шифровании.

## <a name="pseudo-code-example"></a>Пример псевдокода
 Следующий пример псевдокода иллюстрирует шаблон, обнаруживаемый этим правилом, и возможные альтернативы.

### <a name="md5-hashing-violation"></a>Нарушение хэширования MD5

```
using System.Security.Cryptography;
...
var hashAlg = MD5.Create();

```

### <a name="solution"></a>Решение

```
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();

```

### <a name="rc2-encryption-violation"></a>Нарушение шифрования RC2

```
using System.Security.Cryptography;
...
RC2 encAlg = RC2.Create();

```

### <a name="solution"></a>Решение

```
using System.Security.Cryptography;
...
using (AesManaged encAlg = new AesManaged())
{
  ...
}
```

### <a name="des-br-br-encryption-violation"></a>DES <br /><br />Нарушение шифрования

```
using System.Security.Cryptography;
...
DES encAlg = DES.Create();

```

### <a name="solution"></a>Решение

```
using System.Security.Cryptography;
...
using (AesManaged encAlg = new AesManaged())
{
  ...
}
```