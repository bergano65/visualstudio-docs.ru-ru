---
title: 'CA2153: запрет на обработку исключений поврежденного состояния'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 035c68feddafffbb7e1502a07db47ab80eac61c5
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153: запрет на обработку исключений поврежденного состояния

|||
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

[Исключения сбоя состояния (CSE)](https://msdn.microsoft.com/magazine/dd419661.aspx) указать, что память в процессе имеется повреждение. Если перехватывать их вместо того, чтобы позволить процессу завершиться сбоем, это может привести к уязвимостям в системе безопасности, если злоумышленнику удастся поместить эксплойт в поврежденную область памяти.

## <a name="rule-description"></a>Описание правила
 Исключение CSE указывает на то, что состояние процесса было повреждено, и не перехватывается системой. В случае повреждения состояния общий обработчик перехватывает это исключение, только если вы пометили метод соответствующим атрибутом `HandleProcessCorruptedStateExceptions` . По умолчанию [Common Language Runtime (CLR)](/dotnet/standard/clr) не вызывает обработчики catch для исключений CSE.

 Позволить процессу завершиться сбоем безопаснее, чем перехватывать исключения этого типа, так как даже код ведения журнала может дать злоумышленникам возможность воспользоваться ошибками, приводящими к повреждению памяти.

 Это предупреждение срабатывает при перехвате исключений CSE с помощью общего обработчика, который перехватывает все исключения, такого как catch(исключение) или catch(без указания исключения).

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить это предупреждение, выполните одно из указанных ниже действий.

 1. Удалить `HandleProcessCorruptedStateExceptions` атрибута. При этом восстанавливается поведение среды выполнения по умолчанию, при котором исключения CSE не передаются в обработчики catch.

 2. Удалите общий обработчик catch и используйте обработчики, перехватывающие исключения определенных типов.  Это могут быть и исключения CSE при условии, что они могут быть обработаны безопасным образом (что бывает очень редко).

 3. Повторно создайте исключение CSE в обработчике catch, чтобы передать его вызывающему объекту и вызвать завершение выполняющегося процесса.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="pseudo-code-example"></a>Пример псевдокода

### <a name="violation"></a>Нарушение
 В приведенном ниже псевдокоде показан шаблон, обнаруживаемый этим правилом.

```
[HandleProcessCorruptedStateExceptions]
//method to handle and log CSE exceptions
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error
    }
}
```

### <a name="solution-1"></a>Решение 1
 Удаление атрибута HandleProcessCorruptedExceptions приводит к тому, что исключения не обрабатываются.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error
    }
}
```

### <a name="solution-2"></a>Решение 2
 Удалите общий обработчик catch и перехватывайте только исключения определенных типов.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error
    }
}
```

### <a name="solution-3"></a>Решение 3
 Повторно создайте исключение.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error
        throw;
    }
}
```