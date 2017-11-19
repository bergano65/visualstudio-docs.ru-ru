---
title: "CA1812: Не создавайте внутренние классы | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1812
- AvoidUninstantiatedInternalClasses
helpviewer_keywords:
- AvoidUninstantiatedInternalClasses
- CA1812
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6f6344b5dca6df21cba4d9a747925a24fffe1025
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: не создавайте внутренние классы без экземпляров
|||  
|-|-|  
|TypeName|AvoidUninstantiatedInternalClasses|  
|CheckId|CA1812|  
|Категория|Microsoft.Performance|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Экземпляр типа уровня сборки не создается кодом в сборке.  
  
## <a name="rule-description"></a>Описание правила  
 Это правило пытается найти вызов одного из конструкторов типа и приводит к нарушению, если запрос не найден.  
  
 Это правило не проверяет следующие типы:  
  
-   Типы значений  
  
-   Абстрактные типы  
  
-   Перечисления  
  
-   Делегаты  
  
-   Типы массивов, определяемые компилятором  
  
-   Типы, не может быть создан и определяют `static` (`Shared` в Visual Basic) методов только.  
  
 Если применить <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> для сборки, который анализируется, это правило не будет выполняться на каких-либо конструкторов, которые помечены как `internal` , так как невозможно определить, используется ли поле в другом `friend` сборки.  
  
 Несмотря на то, что нельзя обойти это ограничение в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] анализ кода, внешний автономный инструмент FxCop будет выполняться во внутренних конструкторах при каждом `friend` сборки присутствует в анализе.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, удалите тип или добавьте код, который его использует. Если тип содержит только статические методы, добавьте один из следующих к типу, чтобы запретить компилятору выдача публичного экземпляра конструктора по умолчанию:  
  
-   Закрытый конструктор для типов, предназначенных для [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] версий 1.0 и 1.1.  
  
-   `static` (`Shared` В Visual Basic) модификатор для типов, предназначенных для [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Его можно безопасно подавить предупреждение из этого правила. Рекомендуется отключить предупреждение в следующих ситуациях:  
  
-   Например создания через отражение позднего связывания методы класса <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>.  
  
-   Класс автоматически создается средой выполнения или [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Например, классы, реализующие <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> или <xref:System.Web.IHttpHandler?displayProperty=fullName>.  
  
-   Класс передается в качестве параметра универсального типа, имеющего нового ограничения. Например следующий пример вызывает это правило.  
  
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
  
 В этих случаях рекомендуется отключить предупреждение.  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1811: не используйте невызываемый закрытый код](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1801: проверьте неиспользуемые параметры](../code-quality/ca1801-review-unused-parameters.md)  
  
 [CA1804: удалите неиспользуемые локальные переменные](../code-quality/ca1804-remove-unused-locals.md)