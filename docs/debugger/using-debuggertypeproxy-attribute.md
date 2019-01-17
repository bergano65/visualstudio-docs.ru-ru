---
title: Использование атрибута DebuggerTypeProxy | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- attributes [C#], debugger
- DebuggerTypeProxyAttribute class
- DebuggerTypeProxy attribute
ms.assetid: 943f3bb1-993e-4800-a47e-0af78b063014
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f868041449e622ddbd5cf177a0aa22771fd48498
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227542"
---
# <a name="using-debuggertypeproxy-attribute-c-visual-basic-ccli"></a>Использование атрибута DebuggerTypeProxy (C#, Visual Basic, C + +/ CLI)

Атрибут <xref:System.Diagnostics.DebuggerTypeProxyAttribute> указывает прокси (заменяющий тип) для типа и меняет способ отображения типа в окнах отладчика. При просмотре переменной, у которой есть прокси, прокси заменяет исходный тип при **отображении**. Окно переменных отладчика отображает только открытые члены прокси-типа. Закрытые члены не отображаются.

Данный атрибут может применяться к:

- Структуры
- Классы
- Сборки

> [!NOTE]
> Для машинного кода, этот атрибут поддерживается только в C + +/ CLI кода.

Класс прокси-типа должен иметь конструктор, принимающий аргумент типа, который будет заменен прокси. Отладчик создает новый экземпляр класса прокси-типа всякий раз, когда требуется отобразить переменную конечного типа. Это может сказываться на производительности. Поэтому не следует выполнять в конструкторе больше действий, чем это действительно необходимо.

Для снижения потерь производительности вычислитель выражений не проверяет атрибуты при отображении прокси-типа до тех пор, пока тип не будет развернут щелчком по символу "+" в окне отладчика или путем применения атрибута <xref:System.Diagnostics.DebuggerBrowsableAttribute>. Таким образом, не следует применять атрибуты к самому типу отображения. Атрибуты можно и нужно применять в основной части типа отображения.

Прокси-тип рекомендуется делать закрытым вложенным классом внутри класса, к которому применяется атрибут. В этом случае он может легко получить доступ к внутренним членам.

<xref:System.Diagnostics.DebuggerTypeProxyAttribute> может быть унаследован, поэтому если тип прокси-сервер указан в базовом классе его будут применяться ко всем производным классам, если эти производные классы не заданы собственные прокси-сервера типа.

Если атрибут <xref:System.Diagnostics.DebuggerTypeProxyAttribute> используется на уровне сборки, параметр `Target` указывает тип, который заменяется прокси.

Пример использования этого атрибута вместе с <xref:System.Diagnostics.DebuggerDisplayAttribute> и <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, см. в разделе[использование атрибута DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).

## <a name="using-generics-with-debuggertypeproxy"></a>Использование универсальных типов с атрибутом DebuggerTypeProxy

Поддержка универсальных типов ограничена. Для C# атрибут `DebuggerTypeProxy` поддерживает только открытые типы. Открытый тип (также называемый "не сконструированным" типом) — это универсальный тип, экземпляр которого создается без аргументов для параметров типа. Закрытые типы (также называемые сконструированными типами) не поддерживаются.

Синтаксис для открытого типа выглядит следующим образом:

`Namespace.TypeName<,>`

Этот синтаксис необходимо использовать при использовании универсального типа в качестве целевого типа в атрибуте `DebuggerTypeProxy`. Атрибут `DebuggerTypeProxy` предположит параметры типа самостоятельно.

Дополнительные сведения об открытых и закрытых типах в C# см. в разделе [ C# спецификации языка](/dotnet/csharp/language-reference/language-specification), откройте раздел 20.5.2 и закрытые типы.

В Visual Basic синтаксис для открытых типов не поддерживается, поэтому данный способ для Visual Basic не подходит. Вместо этого необходимо использовать строковое представление имени открытого типа.

`"Namespace.TypeName'2"`

## <a name="see-also"></a>См. также раздел

- [Использование атрибута DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
- [Создание настраиваемых представлений собственных объектов](../debugger/create-custom-views-of-dot-managed-objects.md)
- [Повышение эффективности отладки с помощью атрибутов просмотра отладчика](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
