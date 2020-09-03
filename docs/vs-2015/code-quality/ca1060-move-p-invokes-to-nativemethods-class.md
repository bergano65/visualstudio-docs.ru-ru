---
title: 'CA1060: Move P — Invoked to NativeMethods Class | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
helpviewer_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e01ad9fc4fc57917c123404d8863d04240585793
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533436"
---
# <a name="ca1060-move-pinvokes-to-nativemethods-class"></a>CA1060: переместите P/Invokes в класс NativeMethods
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|MovePInvokesToNativeMethodsClass|
|CheckId|CA1060|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Метод использует службы вызова платформы для доступа к неуправляемому коду и не является членом одного из классов **NativeMethods** .

## <a name="rule-description"></a>Описание правила
 Методы вызова платформы, например те, которые помечены с помощью <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> атрибута или методы, определенные с помощью `Declare` ключевого слова в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] , обращаются к неуправляемому коду. Эти методы должны находиться в одном из следующих классов:

- **NativeMethods** — этот класс не подавляет обход стека для разрешения неуправляемого кода. ( <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> не следует применять к этому классу.) Этот класс предназначен для методов, которые можно использовать в любом месте, так как будет выполнен анализ стека.

- **SafeNativeMethods** — этот класс подавляет обход стека для разрешения неуправляемого кода. ( <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> применяется к этому классу.) Этот класс предназначен для методов, которые являются надежными для любого вызова. Вызывающим объектам этих методов не требуется выполнять полную проверку безопасности, чтобы обеспечить безопасность использования, так как методы являются безопасными для любого вызывающего объекта.

- **UnsafeNativeMethods** — этот класс подавляет обход стека для разрешения неуправляемого кода. ( <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> применяется к этому классу.) Этот класс предназначен для методов, которые потенциально опасны. Любой вызывающий объект этих методов должен выполнить полную проверку безопасности, чтобы обеспечить безопасность использования, так как проверка стека не будет выполнена.

  Эти классы объявляются как `internal` ( `Friend` , в Visual Basic) и объявляют закрытый конструктор, чтобы предотвратить создание новых экземпляров. Методы в этих классах должны быть `static` и `internal` ( `Shared` и `Friend` в Visual Basic).

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, переместите метод в соответствующий класс **NativeMethods** . Для большинства приложений перемещение P/Invoke в новый класс с именем **NativeMethods** достаточно.

 Однако при разработке библиотек для использования в других приложениях следует рассмотреть возможность определения двух других классов, которые называются **SafeNativeMethods** и **UnsafeNativeMethods**. Эти классы похожи на класс **NativeMethods** . Однако они помечаются с помощью специального атрибута с именем **SuppressUnmanagedCodeSecurityAttribute**. При применении этого атрибута среда выполнения не выполняет полный анализ стека, чтобы убедиться, что все вызывающие объекты имеют разрешение **UnmanagedCode** . Среда выполнения обычно проверяет наличие этого разрешения при запуске. Поскольку проверка не выполняется, она может значительно повысить производительность вызовов этих неуправляемых методов, а также позволяет коду, имеющему ограниченные разрешения на вызов этих методов.

 Однако этот атрибут следует использовать с большой осторожностью. При неправильной реализации она может иметь серьезные последствия для безопасности.

 Сведения о том, как реализовать методы, см. в примере **NativeMethods** , примере **SafeNativeMethods** и **UnsafeNativeMethods** .

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере объявляется метод, нарушающий это правило. Чтобы устранить нарушение, **ремоведиректори** p/invoke следует переместить в соответствующий класс, предназначенный для хранения только P/Invokes.

 [!code-csharp[FxCop.Design.DllImportNativeMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.DllImportNativeMethods/cs/FxCop.Design.DllImportNativeMethods.cs#1)]
 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DllImportNativeMethods/vb/FxCop.Design.DllImportNativeMethods.vb#1)]

## <a name="nativemethods-example"></a>Пример NativeMethods

### <a name="description"></a>Описание
 Так как класс **NativeMethods** не должен быть помечен с помощью атрибута **SuppressUnmanagedCodeSecurityAttribute**, P/Invoke, которые помещаются в него, потребует разрешения **UnmanagedCode** . Поскольку большинство приложений выполняются с локального компьютера и работают совместно с полным доверием, обычно это не проблема. Однако при разработке многократно используемых библиотек следует рассмотреть возможность определения класса **SafeNativeMethods** или **UnsafeNativeMethods** .

 В следующем примере показан метод **взаимодействия. beep** , который создает оболочку для функции **мессажебип** из user32.dll. **Мессажебип** P/Invoke помещается в класс **NativeMethods** .

### <a name="code"></a>Код
 [!code-csharp[FxCop.Design.NativeMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethods/cs/FxCop.Design.NativeMethods.cs#1)]
 [!code-vb[FxCop.Design.NativeMethods#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethods/vb/FxCop.Design.NativeMethods.vb#1)]

## <a name="safenativemethods-example"></a>Пример SafeNativeMethods

### <a name="description"></a>Описание
 Методы P/Invoke, которые могут быть безопасно доступны для любого приложения и не имеют побочных эффектов, должны быть размещены в классе с именем **SafeNativeMethods**. Вам не нужно запрашивать разрешения, и вам не нужно уделять особое внимание тому, откуда они вызываются.

 В следующем примере показано свойство **Environment. TickCount** , которое служит оболочкой для функции **жеттикккаунт** из kernel32.dll.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Design.NativeMethodsSafe#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe/cs/FxCop.Design.NativeMethodsSafe.cs#1)]
 [!code-vb[FxCop.Design.NativeMethodsSafe#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe/vb/FxCop.Design.NativeMethodsSafe.vb#1)]

## <a name="unsafenativemethods-example"></a>Пример UnsafeNativeMethods

### <a name="description"></a>Описание
 Методы P/Invoke, которые не могут быть безопасно вызваны и могут вызвать побочные эффекты, должны быть размещены в классе с именем **UnsafeNativeMethods**. Эти методы должны быть тщательно проверены, чтобы обеспечить непреднамеренное предоставление пользователю доступа. Правило [CA2118: Проверка использования SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) может помочь в этом. Кроме того, методы должны иметь еще одно разрешение, которое будет требоваться вместо **UnmanagedCode** при их использовании.

 В следующем примере показан метод **cursor. Hide** , который заключает в оболочку функцию **шовкурсор** из user32.dll.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Design.NativeMethodsUnsafe#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsUnsafe/cs/FxCop.Design.NativeMethodsUnsafe.cs#1)]
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsUnsafe/vb/FxCop.Design.NativeMethodsUnsafe.vb#1)]

## <a name="see-also"></a>См. также:
 [Предупреждения конструктора](../code-quality/design-warnings.md)
