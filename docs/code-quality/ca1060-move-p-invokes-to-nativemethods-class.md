---
title: CA1060. Переместите методы P/Invoke в класс NativeMethods
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
helpviewer_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: cfa705654a5cc4122e5ee554fe050722d7883970
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235482"
---
# <a name="ca1060-move-pinvokes-to-nativemethods-class"></a>CA1060. Переместите методы P/Invoke в класс NativeMethods

|||
|-|-|
|TypeName|MovePInvokesToNativeMethodsClass|
|CheckId|CA1060|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:

Метод использует службы вызова платформы для доступа к неуправляемому коду и не является членом одного из классов **NativeMethods** .

## <a name="rule-description"></a>Описание правила

Методы вызова платформы, например те, которые помечены с помощью <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> атрибута или методы, определенные с `Declare` помощью ключевого слова в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], обращаются к неуправляемому коду. Эти методы должны находиться в одном из следующих классов:

- **NativeMethods** — этот класс не подавляет обход стека для разрешения неуправляемого кода. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> не следует применять к этому классу.) Этот класс предназначен для методов, которые можно использовать в любом месте, так как будет выполнен анализ стека.

- **SafeNativeMethods** — этот класс подавляет обход стека для разрешения неуправляемого кода. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> применяется к этому классу.) Этот класс предназначен для методов, которые являются надежными для любого вызова. Вызывающим объектам этих методов не требуется выполнять полную проверку безопасности, чтобы обеспечить безопасность использования, так как методы являются безопасными для любого вызывающего объекта.

- **UnsafeNativeMethods** — этот класс подавляет обход стека для разрешения неуправляемого кода. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> применяется к этому классу.) Этот класс предназначен для методов, которые потенциально опасны. Любой вызывающий объект этих методов должен выполнить полную проверку безопасности, чтобы обеспечить безопасность использования, так как проверка стека не будет выполнена.

Эти классы объявляются как `internal` (`Friend`, в Visual Basic) и объявляют закрытый конструктор, чтобы предотвратить создание новых экземпляров. Методы в этих классах должны быть `static` и `internal` (`Shared` и `Friend` в Visual Basic).

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, переместите метод в соответствующий класс **NativeMethods** . Для большинства приложений перемещение P/Invoke в новый класс с именем **NativeMethods** достаточно.

Однако при разработке библиотек для использования в других приложениях следует рассмотреть возможность определения двух других классов, которые называются **SafeNativeMethods** и **UnsafeNativeMethods**. Эти классы похожи на класс **NativeMethods** . Однако они помечаются с помощью специального атрибута с именем **SuppressUnmanagedCodeSecurityAttribute**. При применении этого атрибута среда выполнения не выполняет полный анализ стека, чтобы убедиться, что все вызывающие объекты имеют разрешение **UnmanagedCode** . Среда выполнения обычно проверяет наличие этого разрешения при запуске. Поскольку проверка не выполняется, она может значительно повысить производительность вызовов этих неуправляемых методов, а также позволяет коду, имеющему ограниченные разрешения на вызов этих методов.

Однако этот атрибут следует использовать с большой осторожностью. При неправильной реализации она может иметь серьезные последствия для безопасности.

Сведения о том, как реализовать методы, см. в примере **NativeMethods** , примере **SafeNativeMethods** и **UnsafeNativeMethods** .

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
В следующем примере объявляется метод, нарушающий это правило. Чтобы устранить нарушение, **ремоведиректори** p/invoke следует переместить в соответствующий класс, предназначенный для хранения только P/Invokes.

[!code-vb[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_1.vb)]
[!code-csharp[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_1.cs)]

## <a name="nativemethods-example"></a>Пример NativeMethods

### <a name="description"></a>Описание
Так как класс **NativeMethods** не должен быть помечен с помощью атрибута **SuppressUnmanagedCodeSecurityAttribute**, P/Invoke, которые помещаются в него, потребует разрешения **UnmanagedCode** . Поскольку большинство приложений выполняются с локального компьютера и работают совместно с полным доверием, обычно это не проблема. Однако при разработке многократно используемых библиотек следует рассмотреть возможность определения класса **SafeNativeMethods** или **UnsafeNativeMethods** .

В следующем примере показан метод **взаимодействия. beep** , который создает оболочку для функции **мессажебип** из User32. dll. **Мессажебип** P/Invoke помещается в класс **NativeMethods** .

### <a name="code"></a>Код
[!code-csharp[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_2.cs)]
[!code-vb[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_2.vb)]

## <a name="safenativemethods-example"></a>Пример SafeNativeMethods

### <a name="description"></a>Описание
Методы P/Invoke, которые могут быть безопасно доступны для любого приложения и не имеют побочных эффектов, должны быть размещены в классе с именем **SafeNativeMethods**. Вам не нужно запрашивать разрешения, и вам не нужно уделять особое внимание тому, откуда они вызываются.

В следующем примере показано свойство **Environment. TickCount** , которое служит оболочкой для функции **жеттикккаунт** из Kernel32. dll.

### <a name="code"></a>Код
[!code-vb[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_3.vb)]
[!code-csharp[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_3.cs)]

## <a name="unsafenativemethods-example"></a>Пример UnsafeNativeMethods

### <a name="description"></a>Описание
Методы P/Invoke, которые не могут быть безопасно вызваны и могут вызвать побочные эффекты, должны быть размещены в классе с именем **UnsafeNativeMethods**. Эти методы должны быть тщательно проверены, чтобы обеспечить непреднамеренное предоставление пользователю доступа. CA2118 правила [: Для этого может](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) помочь Проверка использования атрибута SuppressUnmanagedCodeSecurityAttribute. Кроме того, методы должны иметь еще одно разрешение, которое будет требоваться вместо **UnmanagedCode** при их использовании.

В следующем примере показан метод **cursor. Hide** , который заключает в оболочку функцию **шовкурсор** из User32. dll.

### <a name="code"></a>Код
[!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_4.vb)]
[!code-csharp[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_4.cs)]

## <a name="see-also"></a>См. также

- [Предупреждения конструктора](../code-quality/design-warnings.md)