---
title: CA5122. Объявления P-Invoke не могут быть надежными с точки зрения безопасности
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f2581a6d-2a0e-40c1-b600-f5dc70909200
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9abe71337b5eb09d44ec6a244dc17e656768847a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541055"
---
# <a name="ca5122-pinvoke-declarations-should-not-be-safe-critical"></a>CA5122. Объявления P/Invoke не могут быть надежными с точки зрения безопасности

|||
|-|-|
|TypeName|PInvokesShouldNotBeSafeCriticalFxCopRule|
|CheckId|CA5122|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Объявление P/Invoke отмечено атрибутом <xref:System.Security.SecuritySafeCriticalAttribute>.

```csharp
[assembly: AllowPartiallyTrustedCallers]

// ...
public class C
{
    [SecuritySafeCritical]
    [DllImport("kernel32.dll")]
    public static extern bool Beep(int frequency, int duration); // CA5122 - safe critical p/invoke
   }
```

 В этом примере `C.Beep(...)` отмечен как надежный с точки зрения безопасности метод.

## <a name="rule-description"></a>Описание правила
 Методы отмечаются как SecuritySafeCritical, если они выполняют критически важные для безопасности операции и являются безопасными для использования в прозрачном коде. Одно из основных правил модели прозрачности безопасности заключается в том, что прозрачный код не может напрямую вызывать машинный код с помощью P/Invoke. Поэтому, если метод P/Invoke отметить как надежный с точки зрения безопасности, это не приведет к тому, что прозрачный код будет вызывать его, и может ввести в заблуждение при анализе безопасности.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы сделать P/Invoke доступным для прозрачного кода, предоставьте для него надежный с точки зрения безопасности метод-оболочку.

```csharp
[assembly: AllowPartiallyTrustedCallers

class C
{
   [SecurityCritical]
   [DllImport("kernel32.dll", EntryPoint="Beep")]
   private static extern bool BeepPinvoke(int frequency, int duration); // Security Critical P/Invoke

   [SecuritySafeCritical]
   public static bool Beep(int frequency, int duration)
   {
      return BeepPInvoke(frequency, duration);
   }
}
```

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.