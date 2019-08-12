---
title: CA1901. Объявления P/Invoke должны быть переносимыми
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
helpviewer_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4a45b7061ae9d183ec7ee02a3b733ee9340b3689
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921306"
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901. Объявления P/Invoke должны быть переносимыми

|||
|-|-|
|TypeName|PInvokeDeclarationsShouldBePortable|
|CheckId|CA1901|
|Категория|Microsoft. переносимость|
|Критическое изменение|Критическое — если P/Invoke видим за пределами сборки. Не критическое — если P/Invoke не виден за пределами сборки.|

## <a name="cause"></a>Причина
Это правило оценивает размер каждого параметра и возвращаемое значение P/Invoke и проверяет, что их размер при маршалировании в неуправляемый код на 32-разрядных и 64-разрядных платформах является правильным. Наиболее распространенным нарушением этого правила является передача целого числа фиксированного размера, где требуется зависящая от платформы переменная с размером указателя.

## <a name="rule-description"></a>Описание правила
В одном из следующих сценариев происходит нарушение этого правила:

- Возвращаемое значение или параметр вводится как целое число фиксированного размера, если его необходимо ввести как `IntPtr`.

- Возвращаемое значение или параметр типизировано как, `IntPtr` если его необходимо ввести как целое число с фиксированным размером.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Это нарушение можно устранить с `IntPtr` помощью или `UIntPtr` `Int32` для представления дескрипторов вместо или `UInt32`.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Не следует отключать это предупреждение.

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

В этом примере `nIconIndex` параметр объявляется `IntPtr`как, который имеет ширину 4 байта на 32-разрядной платформе и 8 байт в ширину на 64-разрядной платформе. В объявлении неуправляемого кода ниже видно, что `nIconIndex` — это 4-байтовое целое число без знака на всех платформах.

```csharp
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,
    UINT nIconIndex);
```

## <a name="example"></a>Пример
Чтобы устранить нарушение, измените объявление на следующее:

```csharp
internal class NativeMethods{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, uint nIconIndex);
}
```

## <a name="see-also"></a>См. также
[Portability Warnings](../code-quality/portability-warnings.md)