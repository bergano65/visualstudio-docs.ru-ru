---
title: 'CA1812: Избегайте использования внутренних классов без экземпляров | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1812
- AvoidUninstantiatedInternalClasses
helpviewer_keywords:
- AvoidUninstantiatedInternalClasses
- CA1812
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f5a36ee8cffc221d15243ff72e2e71558e867319
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645411"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: не создавайте внутренние классы без экземпляров
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|Категория|Microsoft. Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Экземпляр типа уровня сборки не создается кодом в сборке.

## <a name="rule-description"></a>Описание правила
 Это правило пытается найти вызов одного из конструкторов типа и сообщает о нарушении, если вызов не найден.

 Это правило не проверяет следующие типы:

- Типы значений

- Абстрактные типы

- Перечисления

- Делегаты

- Типы массивов, созданные компилятором

- Типы, которые не могут быть созданы и которые определяют только методы `static` (`Shared` в Visual Basic).

  При применении <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> к анализируемой сборке это правило не будет выполняться ни для каких конструкторов, помеченных как `internal`, поскольку невозможно определить, используется ли поле другой сборкой `friend`.

  Несмотря на то, что это ограничение нельзя обойти в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ном анализе кода, внешний автономный FxCop будет выполняться во внутренних конструкторах, если в анализе имеется каждая `friend` сборка.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите тип или добавьте код, который его использует. Если тип содержит только статические методы, добавьте в тип один из следующих элементов, чтобы компилятор не выдать конструктор открытого экземпляра по умолчанию:

- Закрытый конструктор для типов, предназначенных для [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] версий 1,0 и 1,1.

- Модификатор `static` (`Shared` в Visual Basic) для типов, предназначенных для [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)].

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 В этом правиле можно отключить вывод предупреждений. Рекомендуется подавлять это предупреждение в следующих ситуациях:

- Класс создается с помощью методов отражения с поздним связыванием, таких как <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>.

- Класс создается автоматически средой выполнения или [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Например, классы, реализующие <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> или <xref:System.Web.IHttpHandler?displayProperty=fullName>.

- Класс передается как параметр универсального типа с новым ограничением. Например, в следующем примере это правило будет вырождено.

  ```csharp
  internal class MyClass
  {
      public DoSomething()
      {
      }
  }
  public class MyGeneric<T> where T : new()
  {
      public T Create()
      {
          return new T();
      }
  }
  // [...]
  MyGeneric<MyClass> mc = new MyGeneric<MyClass>();
  mc.Create();
  ```

  В таких ситуациях рекомендуется подавлять это предупреждение.

## <a name="related-rules"></a>Связанные правила
 [CA1811: не используйте невызываемый закрытый код](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1801: проверьте неиспользуемые параметры](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: удалите неиспользуемые локальные переменные](../code-quality/ca1804-remove-unused-locals.md)
