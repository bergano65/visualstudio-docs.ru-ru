---
title: "CA1060: переместите P/Invokes в класс NativeMethods | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MovePInvokesToNativeMethodsClass"
  - "CA1060"
helpviewer_keywords: 
  - "CA1060"
  - "MovePInvokesToNativeMethodsClass"
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# CA1060: переместите P/Invokes в класс NativeMethods
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MovePInvokesToNativeMethodsClass|  
|CheckId|CA1060|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Метод использует службы PInvoke для доступа к неуправляемому коду и не является членом одного из классов **NativeMethods**.  
  
## Описание правила  
 Методы PInvoke, помеченные атрибутом <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> \(или методы, определенные с помощью ключевого слова `Declare` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\), имеют доступ к неуправляемому коду.  Методы должны находиться в одном из следующих классов.  
  
-   **NativeMethods** — этот класс не подавляет проверку стека на разрешение неуправляемого кода. \(к классу не должен быть применен <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>.\) Этот класс предназначен для методов, которые могут быть использованы где угодно, поскольку выполняется проверка стека.  
  
-   **SafeNativeMethods** — этот класс подавляет проверку стека на разрешение неуправляемого кода. \(к классу применен <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>.\) Класс предназначен для методов, которые являются безопасными для всех, кто их вызывает.  Для вызывающих их методов нет необходимости в выполнении полной проверки безопасности использования, поскольку они являются безопасными для любого вызывающего их метода.  
  
-   **UnsafeNativeMethods** — этот класс подавляет проверку стека на разрешение неуправляемого кода. \(к классу применен <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>.\) Класс предназначен для методов, которые являются потенциально опасными.  Все вызывающие их методы должны пройти полную проверку безопасности использования, поскольку проверка стека не выполняется.  
  
 Эти классы объявлены как `internal` \(`Friend` в Visual Basic\) и объявляют закрытый конструктор для предотвращения создания новых экземпляров.  Методы в этих классах должны быть `static` и `internal` \(`Shared` и `Friend` в Visual Basic\).  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, переместите метод в соответствующий класс **NativeMethods**.  Для большинства приложений достаточно переместить P\/Invokes в новый класс с именем **NativeMethods**.  
  
 Однако при разработке библиотек для использования в других приложениях нужно определить два дополнительных класса с именами **SafeNativeMethods** и **UnsafeNativeMethods**.  Эти классы похожи на класс **NativeMethods**, но они помечены специальным атрибутом **SuppressUnmanagedCodeSecurityAttribute**.  При применении этого атрибута среда выполнения не осуществляет полную проверку стека на наличие у всех вызывающих методов разрешения **UnmanagedCode**.  Обычно такая проверка производится средой выполнения во время запуска.  Поскольку проверка не выполняется, производительность для вызовов неуправляемых методов может значительно улучшиться и, кроме того, код с ограниченными разрешениями может вызывать эти методы.  
  
 Тем не менее этот атрибут следует использовать с большой осторожностью.  Он может иметь последствия для безопасности, если реализуется неправильно.  
  
 Сведения о способах реализации методов см. в примерах **NativeMethods**, **SafeNativeMethods** и **UnsafeNativeMethods**.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример  
 В следующем примере объявляется метод, нарушающий это правило.  Чтобы устранить нарушение, P\/Invoke **RemoveDirectory** следует переместить в соответствующий класс, разработанный исключительно для размещения P\/Invoke.  
  
 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_1.vb)]
 [!code-cs[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_1.cs)]  
  
## Пример NativeMethods  
  
### Описание  
 Поскольку класс **NativeMethods** не должен быть помечен атрибутом **SuppressUnmanagedCodeSecurityAttribute**, P\/Invoke, размещенному в нем, требуется разрешение **UnmanagedCode**.  Так как большинство приложений выполняется на локальном компьютере с полным доверием, обычно это не является проблемой.  Однако при разработке многократно используемых библиотек нужно определить класс **SafeNativeMethods** или **UnsafeNativeMethods**.  
  
 В следующем примере показан метод **Interaction.Beep**, создающий оболочку для функции **MessageBeep** из библиотеки user32.dll.  P\/Invoke **MessageBeep** находится внутри класса **NativeMethods**.  
  
### Код  
 [!code-cs[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_2.cs)]
 [!code-vb[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_2.vb)]  
  
## Пример SafeNativeMethods  
  
### Описание  
 Методы P\/Invoke, которые могут быть безопасными при открытии любым приложением и не имеют каких\-либо побочных эффектов, следует поместить в класс с именем **SafeNativeMethods**.  При их вызове не нужно требовать разрешений и уделять им слишком много внимания.  
  
 В следующем примере показано свойство **Environment.TickCount**, создающее оболочку для функции **GetTickCount** из библиотеки kernel32.dll.  
  
### Код  
 [!CODE [FxCop.Design.NativeMethodsSafe#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe#1)]  
  
## Пример UnsafeNativeMethods  
  
### Описание  
 Методы P\/Invoke, которые не являются безопасными при вызове и могут иметь побочные эффекты, следует поместить в класс с именем **UnsafeNativeMethods**.  Эти методы должны быть тщательно проверены, чтобы исключить возможность случайного открытия пользователем.  В этом случае целесообразно использовать правило [CA2118: обзор использования SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md).  В качестве альтернативы методы должны иметь другое разрешение, требуемое вместо **UnmanagedCode** при их использовании.  
  
 В следующем примере показан метод **Cursor.Hide**, создающий оболочку для функции **ShowCursor** из библиотеки user32.dll.  
  
### Код  
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_3.vb)]
 [!code-cs[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_3.cs)]  
  
## См. также  
 [Предупреждения конструктора](../code-quality/design-warnings.md)