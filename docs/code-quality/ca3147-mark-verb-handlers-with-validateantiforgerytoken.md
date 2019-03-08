---
title: CA3147. Присвоение метки ValidateAntiForgeryToken обработчикам команд
ms.date: 08/08/2018
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 4c8c43ceb19aa6b4407fd4639f952ced859390b1
ms.sourcegitcommit: b7f25ae08e45fcaa84a84276b588cf6799cc7620
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/07/2019
ms.locfileid: "57567332"
---
# <a name="ca3147-mark-verb-handlers-with-validateantiforgerytoken"></a>CA3147. Присвоение метки ValidateAntiForgeryToken обработчикам команд

|||
|-|-|
|TypeName|MarkVerbHandlersWithValidateAntiForgeryToken|
|CheckId|CA3147|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Метод действия контроллера ASP.NET MVC не отмечены [ValidateAntiForgeryTokenAttribute](/previous-versions/aspnet/dd492108(v=vs.118)), или указания HTTP-команда, такого как атрибут [HttpGetAttribute](/previous-versions/aspnet/ee470993(v%3dvs.118)) или [ AcceptVerbsAttribute](/previous-versions/aspnet/dd470553%28v%3dvs.118%29).

## <a name="rule-description"></a>Описание правила

При разработке контроллера ASP.NET MVC, следует учитывать атак с подделкой межсайтовых запросов. Атак подделки межсайтовых запросов на основе может отправлять вредоносные запросы от пользователя, прошедшего проверку подлинности в контроллер ASP.NET MVC. Дополнительные сведения см. в разделе [защиты от XSRF/CSRF в ASP.NET MVC и веб-страниц](/aspnet/mvc/overview/security/xsrfcsrf-prevention-in-aspnet-mvc-and-web-pages).

Это правило проверяет этот контроллер ASP.NET MVC методам действий либо:

- У [ValidateAntiforgeryTokenAttribute](/previous-versions/aspnet/dd492108%28v%3dvs.118%29) и указать разрешенные команды HTTP, не включая HTTP GET.

- Укажите в качестве допустимого глагола HTTP GET.

## <a name="how-to-fix-violations"></a>Устранение нарушений

- Для действий контроллеров ASP.NET MVC, которые обрабатывают запросы HTTP GET и не потенциально опасными побочными эффектами, добавить [HttpGetAttribute](/previous-versions/aspnet/ee470993%28v%3dvs.118%29) методу.

   При наличии ASP.NET MVC запрашивает действие контроллера, обрабатывающий запрос HTTP GET и имеет потенциально опасные побочные эффекты, такие как изменение конфиденциальных данных, приложение становится уязвимым для атак с подделкой межсайтовых.  Вам потребуется изменить структуру приложения, чтобы только запросы HTTP POST, PUT или DELETE выполнять важные операции.

- Для действий контроллеров ASP.NET MVC, которые обрабатывают HTTP POST, PUT или DELETE запрашивает, добавить [ValidateAntiForgeryTokenAttribute](/previous-versions/aspnet/dd492108(v=vs.118)) и атрибуты, указав допустимых HTTP-команд ([AcceptVerbsAttribute](/previous-versions/aspnet/dd470553%28v%3dvs.118%29) [HttpPostAttribute](/previous-versions/aspnet/ee264023%28v%3dvs.118%29), [HttpPutAttribute](/previous-versions/aspnet/ee470909%28v%3dvs.118%29), или [HttpDeleteAttribute](/previous-versions/aspnet/ee470917%28v%3dvs.118%29)). Кроме того, необходимо вызвать [HtmlHelper.AntiForgeryToken()](/previous-versions/aspnet/web-frameworks/dd504812%28v%3dvs.118%29) метода из представления MVC или веб-страницы Razor. Например, см. в разделе [изучение методов edit и изменять представление](/aspnet/mvc/overview/getting-started/introduction/examining-the-edit-methods-and-edit-view).

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
