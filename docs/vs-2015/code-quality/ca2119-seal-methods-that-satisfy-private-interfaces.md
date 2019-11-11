---
title: CA2119. Запечатайте методы, которые соответствуют частным интерфейсам | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SealMethodsThatSatisfyPrivateInterfaces
- CA2119
helpviewer_keywords:
- CA2119
- SealMethodsThatSatisfyPrivateInterfaces
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: af41fc5576cbcd56589680d99c0cd5c0dfd6e6f1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664770"
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119. Запечатайте методы, соответствующие частным интерфейсам
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|
|CheckId|CA2119|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:
 Наследуемый открытый тип предоставляет реализацию переопределяемого метода для интерфейса `internal` (`Friend` в Visual Basic).

## <a name="rule-description"></a>Описание правила
 Методы интерфейса имеют открытый доступ, который нельзя изменить с помощью реализующего типа. Внутренний интерфейс создает контракт, который не предназначен для реализации вне сборки, определяющей интерфейс. Открытый тип, реализующий метод внутреннего интерфейса с помощью модификатора `virtual` (`Overridable` в Visual Basic), позволяет переопределять метод производным типом, который находится за пределами сборки. Если второй тип в определяющей сборке вызывает метод и ждет внутреннего контракта, поведение может быть скомпрометировано, если вместо этого выполняется переопределенный метод во внешней сборке. Это создает уязвимость системы безопасности.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, запретите переопределение метода вне сборки, выполнив одно из следующих действий:

- Сделайте объявляющий тип `sealed` (`NotInheritable` в Visual Basic).

- Измените уровень доступности объявляющего типа на `internal` (`Friend` в Visual Basic).

- Удалите все открытые конструкторы из объявляющего типа.

- Реализуйте метод без использования модификатора `virtual`.

- Реализуйте метод явным образом.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Предупреждение в этом правиле можно отключить, если после тщательной проверки не существует проблем безопасности, которые могут быть использованы, если метод переопределяется вне сборки.

## <a name="example"></a>Пример
 В следующем примере показан тип `BaseImplementation`, нарушающий это правило.

 [!code-cpp[FxCop.Security.SealMethods1#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cpp/FxCop.Security.SealMethods1.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cs/FxCop.Security.SealMethods1.cs#1)]
 [!code-vb[FxCop.Security.SealMethods1#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/vb/FxCop.Security.SealMethods1.vb#1)]

## <a name="example"></a>Пример
 В следующем примере применяется реализация виртуального метода из предыдущего примера.

 [!code-cpp[FxCop.Security.SealMethods2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cpp/FxCop.Security.SealMethods2.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cs/FxCop.Security.SealMethods2.cs#1)]
 [!code-vb[FxCop.Security.SealMethods2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/vb/FxCop.Security.SealMethods2.vb#1)]

## <a name="see-also"></a>См. также
 [Интерфейсы](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37) [интерфейсов](https://msdn.microsoft.com/library/61b06674-12c9-430b-be68-cc67ecee1f5b)
