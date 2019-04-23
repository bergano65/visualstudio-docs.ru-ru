---
title: CA1901. Объявления P / Invoke должны быть переносимыми | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
helpviewer_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ccbbc3178a9f65c15d11a27dee1a625cca729240
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60053953"
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901. Объявления P/Invoke должны быть переносимыми
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PInvokeDeclarationsShouldBePortable|
|CheckId|CA1901|
|Категория|Microsoft.Portability|
|Критическое изменение|Критическое, если метод P/Invoke видимо за пределами сборки. Не критическое, если метод P/Invoke не отображается за пределами сборки.|

## <a name="cause"></a>Причина
 Это правило вычисляет размер каждого параметра и возвращаемого значения вызова P/Invoke и проверяет правильность их размера, при маршалировании в неуправляемый код на 32-разрядных и 64-разрядных платформах. Наиболее распространенных нарушение этого правила является передача является целым числом, фиксированного размера, где требуется зависят от платформы, размера указателя переменной.

## <a name="rule-description"></a>Описание правила
 Одно из следующих сценариев это правило не происходит:

- Возвращаемого значения или параметра типизируется как целое число фиксированного размера он должен быть типизированы как `IntPtr`.

- Имеет тип возвращаемого значения или параметра `IntPtr` при их следует вводить как целое число фиксированного размера.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Это нарушение можно подготовить с помощью `IntPtr` или `UIntPtr` для представления дескрипторов вместо `Int32` или `UInt32`.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не следует подавлять это предупреждение.

## <a name="example"></a>Пример
 В следующем примере показано нарушение этого правила.

```csharp
internal class NativeMethods
{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, IntPtr nIconIndex);
}
```

 В этом примере `nIconIndex` параметр, объявленный как `IntPtr`, который является 4 байта на 32-разрядной платформе и 8 байтов на 64-разрядной платформе. В неуправляемом объявлении, можно увидеть, что `nIconIndex` является 4-байтовое целое число без знака, на всех платформах.

```csharp
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,
    UINT nIconIndex);
```

## <a name="example"></a>Пример
 Чтобы устранить нарушение, измените объявление следующим:

```csharp
internal class NativeMethods{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)] 
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, uint nIconIndex);
}
```

## <a name="see-also"></a>См. также
 [Portability Warnings](../code-quality/portability-warnings.md)
