---
title: "CA5122. Объявления P/Invoke не могут быть надежными с точки зрения безопасности | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f2581a6d-2a0e-40c1-b600-f5dc70909200
caps.latest.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 4
---
# CA5122. Объявления P/Invoke не могут быть надежными с точки зрения безопасности
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PInvokesShouldNotBeSafeCriticalFxCopRule|  
|CheckId|CA5122|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое|  
  
## Причина  
 Объявление P\/Invoke отмечено атрибутом <xref:System.Security.SecuritySafeCriticalAttribute>.  
  
```c#  
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
  
## Описание правила  
 Методы отмечаются как SecuritySafeCritical, если они выполняют критически важные для безопасности операции и являются безопасными для использования в прозрачном коде.  Одно из основных правил модели прозрачности безопасности заключается в том, что прозрачный код не может напрямую вызывать машинный код с помощью P\/Invoke.  Поэтому, если метод P\/Invoke отметить как надежный с точки зрения безопасности, это не приведет к тому, что прозрачный код будет вызывать его, и может ввести в заблуждение при анализе безопасности.  
  
## Устранение нарушений  
 Чтобы сделать P\/Invoke доступным для прозрачного кода, предоставьте для него надежный с точки зрения безопасности метод\-оболочку.  
  
```c#  
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
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.