---
title: 'CA1811: Избегайте невызванного закрытого кода | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUncalledPrivateCode
- CA1811
helpviewer_keywords:
- CA1811
- AvoidUncalledPrivateCode
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 223b2ff9aa25ddd94a3c62eb9e641127a1cace4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543823"
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811. Избегайте невызываемого частного кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|AvoidUncalledPrivateCode|
|CheckId|CA1811|
|Категория|Microsoft. Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Частный или внутренний член (уровень сборки) не имеет вызывающих объектов в сборке, не вызывается средой CLR и не вызывается делегатом. Следующие члены не проверяются с помощью этого правила:

- Явные члены интерфейса.

- Статические конструкторы.

- Конструкторы сериализации.

- Методы, помеченные как <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> или <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> .

- Элементы, которые являются переопределениями.

## <a name="rule-description"></a>Описание правила
 Это правило может сообщать ложные срабатывания при возникновении точек входа, которые в настоящее время не определяются логикой правила. Кроме того, компилятор может выдавать невызывающий код в сборку.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите невызывающий код или добавьте код, который его вызывает.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 В этом правиле можно отключить вывод предупреждений.

## <a name="related-rules"></a>Связанные правила
 [CA1812. Избегайте неиспользуемых внутренних классов](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801. Проверьте неиспользуемые параметры](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804. Удалите неиспользуемые локальные переменные](../code-quality/ca1804-remove-unused-locals.md)
