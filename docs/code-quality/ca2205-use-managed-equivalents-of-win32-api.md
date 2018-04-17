---
title: 'CA2205: Используйте управляемые эквиваленты Win32 API | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 54c21ea55b1679e05c46c9cb0105c0418133a3cc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: используйте управляемые эквиваленты API Win32
|||  
|-|-|  
|TypeName|UseManagedEquivalentsOfWin32Api|  
|CheckId|CA2205|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Неуправляемого определен метод, и существует метод с эквивалентной функциональностью [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] библиотеки классов.  
  
## <a name="rule-description"></a>Описание правила  
 Неуправляемого метода используется для вызова неуправляемой функции DLL и определяются с помощью <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> атрибут, или `Declare` ключевого слова в Visual Basic. Неправильно определенный метод вызова платформы может привести к ошибкам из-за проблем, таких как неверно именованные функции, неправильное сопоставление типов данных параметров и возвращаемых значений, а также неверная спецификация полей, таких как соглашение о вызовах и символ набор. Если он доступен, обычно является более простым и надежным подвержен ошибкам, для вызова эквивалентный управляемый метод вместо определения и напрямую вызывать неуправляемый метод. Вызов платформы вызовите метод также может привести к дополнительным проблемам с безопасностью, необходимо устранить.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, замените вызов в его эквивалент в управляемом вызова неуправляемой функции.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Отключайте предупреждение из этого правила, если метод в качестве замены не предоставляет необходимую функциональность.  
  
## <a name="example"></a>Пример  
 В следующем примере показан платформы вызвать определения метода, который нарушает правила. Кроме того вызовы платформы вызова метода, показываются эквивалентный управляемый метод.  
  
 [!code-csharp[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/CSharp/ca2205-use-managed-equivalents-of-win32-api_1.cs)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/VisualBasic/ca2205-use-managed-equivalents-of-win32-api_1.vb)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1404: Вызывайте GetLastError сразу после P/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)  
  
 [CA1060: Переместите P/Invokes в класс NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)  
  
 [: CA1400 точек входа P/Invoke](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)  
  
 [CA1401: методы P/Invoke не должны быть видимыми](../code-quality/ca1401-p-invokes-should-not-be-visible.md)  
  
 [CA2101: Укажите тип маршалинга для строковых аргументов P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)