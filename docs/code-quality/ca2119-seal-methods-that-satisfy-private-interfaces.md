---
title: CA2119. Запечатайте методы, соответствующие частным интерфейсам
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SealMethodsThatSatisfyPrivateInterfaces
- CA2119
helpviewer_keywords:
- CA2119
- SealMethodsThatSatisfyPrivateInterfaces
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4c019e98e7f1311b6521dff563cb8e7bb0a2356e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55952051"
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119. Запечатайте методы, соответствующие частным интерфейсам

|||
|-|-|
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|
|CheckId|CA2119|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Наследуемый открытый тип предоставляет реализацию переопределяемого метода `internal` (`Friend` в Visual Basic) интерфейса.

## <a name="rule-description"></a>Описание правила
 Методы интерфейса иметь доступность уровня public, не может быть изменена путем реализации типа. Внутренний интерфейс создает контракт, который не предназначен для реализации за пределами сборки, определяющий интерфейс. Открытый тип, реализующий метод внутреннего интерфейса с помощью `virtual` (`Overridable` в Visual Basic) модификатор позволяет вызвать метод для переопределения с помощью производного типа, которое находится за пределами сборки. Если второй тип в определяющей сборке вызывает метод и ожидает, что только для внутреннего контракт, поведение может быть нарушено, если вместо этого выполняется переопределенный метод во внешней сборке. Это создает угрозу безопасности.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, предотвратить метода переопределение за пределы данной сборки с помощью одного из следующих:

- Сделайте объявляющий тип `sealed` (`NotInheritable` в Visual Basic).

- Изменить доступность объявляющий тип для `internal` (`Friend` в Visual Basic).

- Удалите все открытые конструкторы из объявляющего типа.

- Реализуйте метод без использования `virtual` модификатор.

- Реализуйте метод явным образом.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, если после тщательной проверки безопасности проблемы отсутствуют, могли бы быть использованы в том случае, если переопределен метод за пределы данной сборки.

## <a name="example-1"></a>Пример 1
 В следующем примере показано типом, `BaseImplementation`, который нарушает это правило.

 [!code-cpp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_1.cpp)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_1.cs)]
 [!code-vb[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_1.vb)]

## <a name="example-2"></a>Пример 2
 В следующем примере используется реализация виртуального метода в предыдущем примере.

 [!code-cpp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_2.cpp)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_2.cs)]
 [!code-vb[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_2.vb)]

## <a name="see-also"></a>См. также

- [Интерфейсы](/dotnet/csharp/programming-guide/interfaces/index)
- [Интерфейсы](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)