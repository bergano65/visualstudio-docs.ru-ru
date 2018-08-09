---
title: 'CA3147: Обработчики команд с ValidateAntiForgeryToken пометить'
ms.date: 08/08/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 4b4369cfd310be9322d17b8bdbfe79880f2aa579
ms.sourcegitcommit: 96a6d1f16d06ca28d309d05b6e9fbd52f628cdbc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2018
ms.locfileid: "40008718"
---
# <a name="ca3147-mark-verb-handlers-with-validateantiforgerytoken"></a>CA3147: Обработчики команд с ValidateAntiForgeryToken пометить

|||
|-|-|
|TypeName|MarkVerbHandlersWithValidateAntiForgeryToken|
|CheckId|CA3147|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Метод действия контроллера ASP.NET MVC не отмечены <xref:Microsoft.AspNetCore.Mvc.ValidateAntiForgeryTokenAttribute?displayProperty=fullName>, или указания HTTP-команда, такого как атрибут <xref:Microsoft.AspNetCore.Mvc.HttpGetAttribute?displayProperty=fullName> или <xref:Microsoft.AspNetCore.Mvc.AcceptVerbsAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила

При разработке контроллера ASP.NET MVC, следует учитывать атак с подделкой межсайтовых запросов. Атак подделки межсайтовых запросов на основе может отправлять вредоносные запросы от пользователя, прошедшего проверку подлинности в контроллер ASP.NET MVC. Дополнительные сведения см. в разделе [защиты от XSRF/CSRF в ASP.NET MVC и веб-страниц](/aspnet/mvc/overview/security/xsrfcsrf-prevention-in-aspnet-mvc-and-web-pages).

Это правило проверяет этот контроллер ASP.NET MVC методам действий либо:

- У <xref:Microsoft.AspNetCore.Mvc.ValidateAntiForgeryTokenAttribute> и указать разрешенные команды HTTP, не включая HTTP GET.

- Укажите в качестве допустимого глагола HTTP GET.

## <a name="how-to-fix-violations"></a>Устранение нарушений

- Для действий контроллеров ASP.NET MVC, которые обрабатывают запросы HTTP GET и не потенциально опасными побочными эффектами, добавьте <xref:Microsoft.AspNetCore.Mvc.HttpGetAttribute> методу.

   При наличии ASP.NET MVC запрашивает действие контроллера, обрабатывающий запрос HTTP GET и имеет потенциально опасные побочные эффекты, такие как изменение конфиденциальных данных, приложение становится уязвимым для атак с подделкой межсайтовых.  Вам потребуется изменить структуру приложения, чтобы только запросы HTTP POST, PUT или DELETE выполнять важные операции.

- Для действий контроллеров ASP.NET MVC, которые обрабатывают HTTP POST, PUT или DELETE запрашивает, добавить <xref:Microsoft.AspNetCore.Mvc.ValidateAntiForgeryTokenAttribute> и атрибуты, указав допустимых HTTP-команд (<xref:Microsoft.AspNetCore.Mvc.AcceptVerbsAttribute>, <xref:Microsoft.AspNetCore.Mvc.HttpPostAttribute>, <xref:Microsoft.AspNetCore.Mvc.HttpPutAttribute>, или <xref:Microsoft.AspNetCore.Mvc.HttpDeleteAttribute>). Кроме того, необходимо вызвать <xref:Microsoft.AspNetCore.Mvc.ViewFeatures.HtmlHelper.AntiForgeryToken%2A?displayProperty=nameWithType> из представления MVC или веб-страницы Razor. Например, см. в разделе [изучение методов edit и изменять представление](/aspnet/mvc/overview/getting-started/introduction/examining-the-edit-methods-and-edit-view).

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Можно безопасно подавить предупреждение из этого правила, если:

- Действие контроллера ASP.NET MVC не имеет опасные побочных эффектов.

- Приложение проверяет маркер защиты от подделки по-разному.

## <a name="validateantiforgerytoken-attribute-example"></a>Пример атрибута ValidateAntiForgeryToken

### <a name="violation"></a>Нарушение

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        public ActionResult TransferMoney(string toAccount, string amount)
        {
            // You don't want an attacker to specify to who and how much money to transfer.

            return null;
        }
    }
}
```

### <a name="solution"></a>Решение

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        [HttpPost]
        [ValidateAntiForgeryToken]
        public ActionResult TransferMoney(string toAccount, string amount)
        {
            return null;
        }
    }
}
```

## <a name="httpget-attribute-example"></a>Пример атрибута HttpGet

### <a name="violation"></a>Нарушение

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        public ActionResult Help(int topicId)
        {
            // This Help method is an example of a read-only operation with no harmful side effects.
            return null;
        }
    }
}
```

### <a name="solution"></a>Решение

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        [HttpGet]
        public ActionResult Help(int topicId)
        {
            return null;
        }
    }
}
```
