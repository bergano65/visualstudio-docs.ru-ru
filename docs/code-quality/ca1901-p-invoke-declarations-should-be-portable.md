---
title: "CA1901: объявления P/Invoke должны быть переносимыми | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1901"
  - "PInvokeDeclarationsShouldBePortable"
helpviewer_keywords: 
  - "CA1901"
  - "PInvokeDeclarationsShouldBePortable"
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 23
---
# CA1901: объявления P/Invoke должны быть переносимыми
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PInvokeDeclarationsShouldBePortable|  
|CheckId|CA1901|  
|Категория|Microsoft.Portability|  
|Критическое изменение|Критическое — если вызов P\/Invoke доступен для кода за пределами сборки.  Не критическое — если вызов P\/Invoke недоступен для кода за пределами сборки.|  
  
## Причина  
 Данное правило вычисляет размер каждого параметра и возвращаемого значения вызова P\/Invoke и проверяет правильность их размера при маршалировании в неуправляемый код на 32\-разрядных и 64\-разрядных платформах.  Наиболее распространенным нарушением этого правила является передача целого числа фиксированного размера там, где требуется переменная, размер которой соответствует зависящему от платформы указателю.  
  
## Описание правила  
 Любой из следующих сценариев нарушает правило:  
  
-   Типом возвращаемого значения или параметра указано целое число фиксированного размера, тогда как следовало указать тип `IntPtr`.  
  
-   Для возвращаемого значения или параметра указан тип `IntPtr`, тогда как следовало указать целочисленный тип фиксированного размера.  
  
## Устранение нарушений  
 Нарушение данного правила можно устранить, если использовать для представления дескрипторов тип `IntPtr` или `UIntPtr` вместо типа `Int32` или `UInt32`.  
  
## Отключение предупреждений  
 Не следует отключать данные предупреждения.  
  
## Пример  
 В следующем примере демонстрируется нарушение данного правила.  
  
```c#  
internal class NativeMethods  
{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]  
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, IntPtr nIconIndex);  
}  
```  
  
 В этом примере параметр `nIconIndex` объявлен как `IntPtr`, который имеет размер 4 байта на 32\-х разрядной платформе и размер 8 байт на 64\-х разрядной платформе.  В неуправляемом объявлении, которое приведено далее, можно увидеть, что `nIconIndex` является целым числом без знака размером 4 байта на всех платформах.  
  
```c#  
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,   
    UINT nIconIndex);  
```  
  
## Пример  
 Чтобы устранить это нарушение, измените объявление следующим образом:  
  
```c#  
internal class NativeMethods{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]   
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, uint nIconIndex);  
}  
```  
  
## См. также  
 [Предупреждения переносимости](../code-quality/portability-warnings.md)