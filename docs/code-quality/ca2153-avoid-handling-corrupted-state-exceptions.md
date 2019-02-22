---
title: CA2153 правила анализа кода для поврежденного состояния
ms.date: 02/19/2019
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b75e45b8a199265eaefe3a2b3c37ed62039e0eb
ms.sourcegitcommit: 845442e2b515c3ca1e4e47b46cc1cef4df4f08d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/20/2019
ms.locfileid: "56450273"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153. Избежать обработки поврежденного состояния

|||
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

[Исключений поврежденного состояния (CSE)](https://msdn.microsoft.com/magazine/dd419661.aspx) указать, что память в процессе имеется повреждение. Если перехватывать их вместо того, чтобы позволить процессу завершиться сбоем, это может привести к уязвимостям в системе безопасности, если злоумышленнику удастся поместить эксплойт в поврежденную область памяти.

## <a name="rule-description"></a>Описание правила

Исключение CSE указывает на то, что состояние процесса было повреждено, и не перехватывается системой. В случае повреждения состояния общий обработчик только перехватывает исключение, если вы пометили метод <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=fullName> атрибута. По умолчанию [Common Language Runtime (CLR)](/dotnet/standard/clr) не вызывает обработчики catch для исключений CSE.

Самое надежное — в том, чтобы разрешить процессу завершиться сбоем без перехвата таких исключений. Даже код ведения журнала может дать злоумышленникам возможность воспользоваться ошибки повреждения памяти.

Это предупреждение срабатывает при перехвате исключений CSE с помощью общего обработчика, который перехватывает все исключения, например, `catch (System.Exception e)` или `catch` без параметра исключения.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить это предупреждение, выполните одно из следующих действий.

- Удалите атрибут <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>. При этом восстанавливается поведение среды выполнения по умолчанию, при котором исключения CSE не передаются в обработчики catch.

- Удалите общий обработчик catch и используйте обработчики, перехватывающие исключения определенных типов. Сюда могут входить CSE, при условии, что можно безопасно обрабатывать код обработчика (такие случаи редки).

- Заново создать CSE в обработчике catch, который передает исключение вызывающему объекту и следует вызвать завершение выполняющегося процесса.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Для этого правила отключать вывод предупреждений не следует.

## <a name="pseudo-code-example"></a>Пример псевдокода

### <a name="violation"></a>Нарушение

В приведенном ниже псевдокоде показан шаблон, обнаруживаемый этим правилом.

```csharp
[HandleProcessCorruptedStateExceptions]
// Method that handles CSE exceptions.
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle exception.
    }
}
```

### <a name="solution-1---remove-the-attribute"></a>Решение 1 - удалите атрибут

Удаление <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> атрибут гарантирует, что поврежденного состояния данного метода не обрабатываются.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle exception.
    }
}
```

### <a name="solution-2---catch-specific-exceptions"></a>Решение 2 — перехватывать определенные исключения

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
        // Handle IOException.
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle UnauthorizedAccessException.
    }
}
```

### <a name="solution-3---rethrow"></a>Решение 3 — rethrow

Заново создать исключение.

```csharp
[HandleProcessCorruptedStateExceptions]
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Rethrow the exception.
        throw;
    }
}
```