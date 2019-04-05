---
title: Объявления P / Invoke CA5122 должен быть небезопасным критических | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: f2581a6d-2a0e-40c1-b600-f5dc70909200
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: eff316ac6f5d73e157e3dbef5126195bd0d62878
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58992223"
---
# <a name="ca5122-pinvoke-declarations-should-not-be-safe-critical"></a>CA5122. Объявления P/Invoke не могут быть надежными с точки зрения безопасности
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
    public static extern bool Beep(int frequency, int duration); // CA5122 – safe critical p/invoke
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
   [DllImport(“kernel32.dll”, EntryPoint=”Beep”)]
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
