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
ms.openlocfilehash: a01c8ca81ab469d578d58e6195171c2e3b07704b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62788678"
---
# <a name="ca1060-move-pinvokes-to-nativemethods-class"></a>CA1060. Переместите методы P/Invoke в класс NativeMethods

|||
|-|-|
|TypeName|MovePInvokesToNativeMethodsClass|
|CheckId|CA1060|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Метод использует службы вызова платформы для доступа к неуправляемому коду и не является членом одного из **NativeMethods** классы.

## <a name="rule-description"></a>Описание правила

Методы вызова платформы, например те, которые помечены с помощью <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> атрибута или методы, определенные с помощью `Declare` ключевое слово в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], доступ к неуправляемому коду. Эти методы должны находиться в одном из следующих классов:

- **NativeMethods** -этот класс не подавляет стека на разрешение неуправляемого кода. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> не должны быть применены к этому классу.) Этот класс предназначен для методов, которые могут использоваться в любом месте, так как выполняется анализ стека.

- **SafeNativeMethods** — этот класс подавляет стека на разрешение неуправляемого кода. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> применяется к этому классу.) Этот класс предназначен для методов, которые являются безопасными для тех, кто для вызова. Вызывающие объекты из этих методов не требуются для выполнения полной проверки безопасности следует убедиться, что использование является безопасным, поскольку они являются безопасными для любой вызывающий объект.

- **UnsafeNativeMethods** — этот класс подавляет стека на разрешение неуправляемого кода. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> применяется к этому классу.) Этот класс предназначен для методов, которые могут представлять опасность. Любой вызывающий объект из этих методов необходимо выполнить полную проверку безопасности чтобы убедиться в том, что использование является безопасным, поскольку выполняется анализ стека не потребуется.

Эти классы объявляются как `internal` (`Friend`, в Visual Basic) и объявить закрытый конструктор для предотвращения создания новых экземпляров. Методы в эти классы должны быть `static` и `internal` (`Shared` и `Friend` в Visual Basic).

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, перемещение метода к соответствующему **NativeMethods** класса. Для большинства приложений перемещение P/Invoke в новый класс с именем **NativeMethods** достаточно.

 Тем не менее, если вы разрабатываете библиотеки для использования в других приложениях, следует определить два других классов, которые называются **SafeNativeMethods** и **UnsafeNativeMethods**. Эти классы напоминают **NativeMethods** класса; Однако они отмечены с помощью специального атрибута вызывается **SuppressUnmanagedCodeSecurityAttribute**. Если этот атрибут применяется, среда выполнения не выполняет полную проверку стека, чтобы убедиться в том, что все вызывающие объекты имеют **UnmanagedCode** разрешение. Среда выполнения проверяет обычно за этим разрешением во время запуска. Поскольку проверка не выполняется, он может значительно повысить производительность для вызовов неуправляемых методов, также в нем код, который имеет ограниченные разрешения для вызова этих методов.

 Тем не менее этот атрибут следует использовать с большой осторожностью. Он может иметь серьезные последствия для безопасности, если оно неправильно реализовано...

 Сведения о том, как реализовать методы, см. в разделе **NativeMethods** примере **SafeNativeMethods** примере и **UnsafeNativeMethods** пример.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере объявляется метод, который нарушает это правило. Чтобы устранить нарушение, **RemoveDirectory** P/Invoke должны быть перемещены в соответствующий класс, который предназначен для хранения только P/Invoke.

 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_1.vb)]
 [!code-csharp[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_1.cs)]

## <a name="nativemethods-example"></a>Пример NativeMethods

### <a name="description"></a>Описание
 Так как **NativeMethods** класс не должен быть помечен с помощью **SuppressUnmanagedCodeSecurityAttribute**, потребует P/Invoke, помещаются в ней **UnmanagedCode** разрешение. Так как большинство приложений выполняются с локального компьютера и работать с полным доверием, обычно это не проблема. Тем не менее, если при разработке повторно используемых библиотек, следует определить **SafeNativeMethods** или **UnsafeNativeMethods** класса.

 В следующем примере показан **Interaction.Beep** метод, который создает оболочку для **MessageBeep** функции из user32.dll. **MessageBeep** P/Invoke помещается в **NativeMethods** класса.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_2.cs)]
 [!code-vb[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_2.vb)]

## <a name="safenativemethods-example"></a>Пример SafeNativeMethods

### <a name="description"></a>Описание
 Методы P/Invoke, можно безопасно предоставить любое приложение, и, не имеющие никаких побочных эффектов, которые должны быть помещены в класс, который называется **SafeNativeMethods**. У вас нет разрешения запросу, и вам не нужно платить за меньше внимания, когда они вызываются из.

 В следующем примере показан **Environment.TickCount** свойство, которое создает оболочку **GetTickCount** функции из kernel32.dll.

### <a name="code"></a>Код
 [!code-vb[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_3.vb)]
 [!code-csharp[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_3.cs)]

## <a name="unsafenativemethods-example"></a>Пример UnsafeNativeMethods

### <a name="description"></a>Описание
 Методы P/Invoke не может вызываться безопасно и может привести к побочным эффектам, которые должны быть помещены в класс, который называется **UnsafeNativeMethods**. Эти методы должны быть тщательно проверены, чтобы убедиться в том, что они не доступны пользователь непреднамеренно. Правило [CA2118: Проверьте использование SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) могут помочь в этом. Кроме того, методы должны иметь другое разрешение, требуемое вместо **UnmanagedCode** при их использовании.

 В следующем примере показан **Cursor.Hide** метод, который создает оболочку для **функция ShowCursor** функции из user32.dll.

### <a name="code"></a>Код
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_4.vb)]
 [!code-csharp[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_4.cs)]

## <a name="see-also"></a>См. также

- [Предупреждения конструктора](../code-quality/design-warnings.md)