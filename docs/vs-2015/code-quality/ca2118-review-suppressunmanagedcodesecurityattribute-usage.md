---
title: 'CA2118: Проверка использования SuppressUnmanagedCodeSecurityAttribute | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2118
- ReviewSuppressUnmanagedCodeSecurityUsage
helpviewer_keywords:
- ReviewSuppressUnmanagedCodeSecurityUsage
- CA2118
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bc0e88265245d795697d32a9e6a95909c0415259
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538662"
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118. Проверьте использование атрибута SuppressUnmanagedCodeSecurityAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|
|CheckId|CA2118|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип или член имеет <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> атрибут.

## <a name="rule-description"></a>Описание правила
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> изменяет поведение системы безопасности по умолчанию для элементов, выполняющих неуправляемый код с помощью COM-взаимодействия или вызова платформы. Как правило, система создает [данные и выполняет моделирование](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) для разрешения неуправляемого кода. Это требование происходит во время выполнения для каждого вызова члена и проверяет наличие разрешения у всех вызывающих объектов в стеке вызовов. При наличии атрибута система устанавливает [требование ссылки](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) на разрешение: разрешения непосредственного вызывающего объекта проверяются при JIT-компиляции вызывающего объекта.

 Этот атрибут служит в основном для повышения производительности; однако, прирост производительности сопряжен со значительными рисками безопасности. Если поместить атрибут в открытые члены, вызывающие собственные методы, вызывающим объектам в стеке вызовов (кроме непосредственный вызывающей стороной) не требуется разрешение неуправляемого кода для выполнения неуправляемого кода. В зависимости от действий открытого члена и обработки входных данных это может позволить ненадежным вызывающим объектам получать доступ к функциональным возможностям, которые обычно ограничены надежным кодом.

 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]Использует проверки безопасности, чтобы предотвратить получение вызывающими объектами прямого доступа к адресному пространству текущего процесса. Поскольку этот атрибут обходит обычную безопасность, код создает серьезную угрозу, если ее можно использовать для чтения или записи в память процесса. Обратите внимание, что риск не ограничен методами, которые намеренно предоставляют доступ к памяти процесса; Он также имеется в любом сценарии, где вредоносный код может получить доступ с помощью любого средства, например, с неправильным, неправильно сформированным или недопустимым входом.

 Политика безопасности по умолчанию не предоставляет сборке разрешение на неуправляемый код для сборки, если она не выполняется с локального компьютера или является членом одной из следующих групп:

- Группа кода зоны Мой компьютер

- Группа кода строгого имени (Майкрософт)

- Группа кода строгого имени ECMA

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Внимательно проверьте код, чтобы убедиться в том, что этот атрибут является абсолютно необходимым. Если вы не знакомы с безопасностью управляемого кода или не понимаете последствия использования этого атрибута в безопасности, удалите его из кода. Если атрибут является обязательным, необходимо убедиться, что вызывающие объекты не могут использовать ваш код злонамеренно. Если код не имеет разрешения на выполнение неуправляемого кода, этот атрибут не действует и должен быть удален.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Чтобы безопасно отключить предупреждение из этого правила, необходимо убедиться в том, что код не предоставляет вызывающим объектам доступ к собственным операциям или ресурсам, которые могут быть использованы необратимым образом.

## <a name="example"></a>Пример
 В следующем примере нарушается правило.

 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypesDoNotSuppress/cs/FxCop.Security.TypesDoNotSuppress.cs#1)]

## <a name="example"></a>Пример
 В следующем примере `DoWork` метод предоставляет общедоступный путь кода к методу вызова платформы `FormatHardDisk` .

 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PInvokeAndSuppress/cs/FxCop.Security.PInvokeAndSuppress.cs#1)]

## <a name="example"></a>Пример
 В следующем примере открытый метод `DoDangerousThing` вызывает нарушение. Чтобы устранить нарушение, `DoDangerousThing` следует сделать частным, и доступ к нему должен осуществляться через открытый метод, защищенный требованием безопасности, как показано в `DoWork` методе.

 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypeInvokeAndSuppress/cs/FxCop.Security.TypeInvokeAndSuppress.cs#1)]

## <a name="see-also"></a>См. также:
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>[Рекомендации по защищенному кодированию](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [Оптимизация безопасности](https://msdn.microsoft.com/cf255069-d85d-4de3-914a-e4625215a7c0) [данные и](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) [требования к ссылкам](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) моделирования
