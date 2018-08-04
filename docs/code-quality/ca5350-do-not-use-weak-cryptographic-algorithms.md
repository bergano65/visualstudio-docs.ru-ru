---
title: 'CA5350: не используйте ненадежные алгоритмы шифрования'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 4c51bb8a-fcfa-46aa-ab61-634be84c4a7a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f97de4818e6be66b4ee23d97d8995dfa30533985
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510508"
---
# <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350: не используйте ненадежные алгоритмы шифрования
|||
|-|-|
|TypeName|DoNotUseWeakCryptographicAlgorithms|
|CheckId|CA5350|
|Категория|Microsoft.Cryptography|
|Критическое изменение|Не критическое|

> [!NOTE]
>  Это предупреждение последний раз обновлялось в ноябре 2015 г.

## <a name="cause"></a>Причина
 Алгоритмы шифрования, такие как <xref:System.Security.Cryptography.TripleDES> , и алгоритмы хэширования, такие как <xref:System.Security.Cryptography.SHA1> и <xref:System.Security.Cryptography.RIPEMD160> , считаются ненадежными.

 Эти алгоритмы шифрования не обеспечивают безопасность в той же степени, что более современные аналоги. Криптографические алгоритмы хэширования <xref:System.Security.Cryptography.SHA1> и <xref:System.Security.Cryptography.RIPEMD160> обеспечивают меньшую устойчивость к конфликтам, чем более современные алгоритмы хэширования. Алгоритм шифрования <xref:System.Security.Cryptography.TripleDES> предоставляет меньшее число битов защиты, чем более современные алгоритмы шифрования.

## <a name="rule-description"></a>Описание правила
 Ненадежные алгоритмы шифрования и функции хэширования еще используются сегодня по ряду причин, но они не должны использоваться для обеспечения конфиденциальности данных, которые они защищают.

 Правило срабатывает при обнаружении алгоритмов 3DES, SHA1 или RIPEMD160 в коде и выдает предупреждение для пользователя.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Используйте более криптографически надежные варианты.

-   Для шифрования TripleDES используйте шифрование <xref:System.Security.Cryptography.Aes> .

-   Для функций хэширования SHA1 или RIPEMD160 используйте функции в [SHA-2](/windows/desktop/SecCrypto/hash-and-signature-algorithms) семейства (например <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384>, <xref:System.Security.Cryptography.SHA256>).

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Отключайте предупреждение из этого правила, когда для необходимого уровня защиты данных не требуется гарантия безопасности.

## <a name="pseudo-code-example"></a>Пример псевдокода
 На момент написания этой статьи следующий пример псевдокода иллюстрирует шаблон, обнаруживаемый этим правилом.

### <a name="sha-1-hashing-violation"></a>Нарушение хэширования SHA-1

```
using System.Security.Cryptography;
...
var hashAlg = SHA1.Create();

```

### <a name="solution"></a>Решение

```
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();

```

### <a name="ripemd160-br-br-hashing-violation"></a>RIPEMD160 <br /><br />Нарушение хэширования

```
using System.Security.Cryptography;
...
var hashAlg = RIPEMD160Managed.Create();

```

### <a name="solution"></a>Решение

```
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();

```

### <a name="tripledes-encryption-violation"></a>Нарушение шифрования TripleDES

```
using System.Security.Cryptography;
...
using (TripleDES encAlg = TripleDES.Create())
{
  ...
}
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