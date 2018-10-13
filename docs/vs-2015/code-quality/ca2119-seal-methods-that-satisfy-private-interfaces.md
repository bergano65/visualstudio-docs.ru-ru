---
title: 'CA2119: Запечатайте методы, соответствующие частным интерфейсам | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SealMethodsThatSatisfyPrivateInterfaces
- CA2119
helpviewer_keywords:
- CA2119
- SealMethodsThatSatisfyPrivateInterfaces
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bdb4ea909534ccdb10b2df2acd0d3c0945146ec7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49287590"
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119: запечатайте методы, соответствующие частным интерфейсам
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
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

-   Сделайте объявляющий тип `sealed` (`NotInheritable` в Visual Basic).

-   Изменить доступность объявляющий тип для `internal` (`Friend` в Visual Basic).

-   Удалите все открытые конструкторы из объявляющего типа.

-   Реализуйте метод без использования `virtual` модификатор.

-   Реализуйте метод явным образом.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, если после тщательной проверки безопасности проблемы отсутствуют, могли бы быть использованы в том случае, если переопределен метод за пределы данной сборки.

## <a name="example"></a>Пример
 В следующем примере показано типом, `BaseImplementation`, который нарушает это правило.

 [!code-cpp[FxCop.Security.SealMethods1#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cpp/FxCop.Security.SealMethods1.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cs/FxCop.Security.SealMethods1.cs#1)]
 [!code-vb[FxCop.Security.SealMethods1#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/vb/FxCop.Security.SealMethods1.vb#1)]

## <a name="example"></a>Пример
 В следующем примере используется реализация виртуального метода в предыдущем примере.

 [!code-cpp[FxCop.Security.SealMethods2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cpp/FxCop.Security.SealMethods2.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cs/FxCop.Security.SealMethods2.cs#1)]
 [!code-vb[FxCop.Security.SealMethods2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/vb/FxCop.Security.SealMethods2.vb#1)]

## <a name="see-also"></a>См. также
 [Интерфейсы](http://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37) [интерфейсы](http://msdn.microsoft.com/library/61b06674-12c9-430b-be68-cc67ecee1f5b)



