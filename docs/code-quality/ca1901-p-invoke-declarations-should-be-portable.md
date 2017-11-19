---
title: "CA1901: Объявления P-Invoke должны быть переносимыми | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
helpviewer_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c3c048ae73e2b15035c9be8afd6a82c860544bb5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901: объявления P/Invoke должны быть переносимыми
|||  
|-|-|  
|TypeName|PInvokeDeclarationsShouldBePortable|  
|CheckId|CA1901|  
|Категория|Microsoft.Portability|  
|Критическое изменение|Критическое, если метод P/Invoke видим за пределами сборки. Не критическое, если метод P/Invoke не отображается за пределами сборки.|  
  
## <a name="cause"></a>Причина  
 Данное правило вычисляет размер каждого параметра и возвращаемого значения вызова P/Invoke и проверяет правильность их размера, при маршалировании в неуправляемый код на 32-разрядных и 64-разрядных платформах. Наиболее распространенные нарушение этого правила является передать целое число фиксированного размера, в котором зависят от платформы, размером указателя переменной является обязательным.  
  
## <a name="rule-description"></a>Описание правила  
 Одно из следующих сценариев приводит к нарушению данного правила возникает:  
  
-   Возвращаемого значения или параметра типизируется как целое число фиксированного размера, когда он должен иметь тип `IntPtr`.  
  
-   Имеет тип возвращаемого значения или параметра `IntPtr` при должна вводиться как целое число фиксированного размера.  
  
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
  
 В этом примере `nIconIndex` параметр объявлен как `IntPtr`, которая будет 4 байта на 32-разрядной платформе и 8 байтов на 64-разрядной платформе. В неуправляемом объявлении, можно видеть, что `nIconIndex` является 4-байтовое целое число без знака, на всех платформах.  
  
```csharp  
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,   
    UINT nIconIndex);  
```  
  
## <a name="example"></a>Пример  
 Чтобы устранить нарушение, измените объявление следующим образом:  
  
```csharp  
internal class NativeMethods{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]   
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, uint nIconIndex);  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Portability Warnings](../code-quality/portability-warnings.md)