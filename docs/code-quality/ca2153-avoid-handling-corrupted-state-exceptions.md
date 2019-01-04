---
title: CA2153. Не используйте обработку исключений поврежденного состояния
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e6b789a4580c3787a4504d730e694308341657eb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53821864"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153. Не используйте обработку исключений поврежденного состояния

|||
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

[Исключения сбоя состояния (CSE)](https://msdn.microsoft.com/magazine/dd419661.aspx) указывают на то, что в процессе имеется повреждение памяти. Если перехватывать их вместо того, чтобы позволить процессу завершиться сбоем, это может привести к уязвимостям в системе безопасности, если злоумышленнику удастся поместить эксплойт в поврежденную область памяти.

## <a name="rule-description"></a>Описание правила

Исключение CSE указывает на то, что состояние процесса было повреждено, и не перехватывается системой. В случае повреждения состояния общий обработчик перехватывает это исключение, только если вы пометили метод соответствующим атрибутом `HandleProcessCorruptedStateExceptions` . По умолчанию [среда CLR](/dotnet/standard/clr) не вызывает обработчики catch для исключений CSE.

Позволить процессу завершиться сбоем безопаснее, чем перехватывать исключения этого типа, так как даже код ведения журнала может дать злоумышленникам возможность воспользоваться ошибками, приводящими к повреждению памяти.

Это предупреждение срабатывает при перехвате исключений CSE с помощью общего обработчика, который перехватывает все исключения, такого как catch(исключение) или catch(без указания исключения).

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить это предупреждение, выполните одно из следующих действий.

- Удалите атрибут `HandleProcessCorruptedStateExceptions`. При этом восстанавливается поведение среды выполнения по умолчанию, при котором исключения CSE не передаются в обработчики catch.

- Удалите общий обработчик catch и используйте обработчики, перехватывающие исключения определенных типов. Сюда могут входить CSE при условии, что можно безопасно обрабатывать код обработчика (такие случаи редки).

- Заново создать CSE в обработчике catch, что гарантирует исключение передается вызывающему объекту и вызвать завершение выполняющегося процесса.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Для этого правила отключать вывод предупреждений не следует.

## <a name="pseudo-code-example"></a>Пример псевдокода

### <a name="violation"></a>Нарушение

В приведенном ниже псевдокоде показан шаблон, обнаруживаемый этим правилом.

```csharp
[HandleProcessCorruptedStateExceptions]
// Method to handle and log CSE exceptions.
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error.
    }
}
```

### <a name="solution-1"></a>Решение 1

Удаление атрибута HandleProcessCorruptedExceptions приводит к тому, что исключения не обрабатываются.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error.
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error.
    }
}
```

### <a name="solution-2"></a>Решение 2

Удалите общий обработчик catch и перехватывайте только исключения определенных типов.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error.
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error.
    }
}
```

### <a name="solution-3"></a>Решение 3

Заново создать исключение.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error.
        throw;
    }
}
```