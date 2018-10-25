---
title: 'CA1900: поля типа значения должны быть переносимыми'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fbf54493d4abb455649558a82126f09b7becc605
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844646"
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: поля типа значения должны быть переносимыми

|||
|-|-|
|TypeName|ValueTypeFieldsShouldBePortable|
|CheckId|CA1900|
|Категория|Microsoft.Portability|
|Критическое изменение|Критическое, если поле может отображаться за пределами сборки.<br /><br /> Non критическое, если поле не отображается за пределами сборки.|

## <a name="cause"></a>Причина
 Это правило проверяет правильность выравнивания структур, объявленных с явной разметкой, при маршалировании в неуправляемый код на 64-разрядных операционных системах. Обращается к памяти и процесса аварийно, если не будет устранена, это нарушение запрещены IA-64.

## <a name="rule-description"></a>Описание правила
 Структуры с явной разметкой, содержащей неправильно выровненные поля могут привести к сбоям в 64-разрядных операционных системах.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Все поля, занимающие менее 8 байт, необходим смещения, которые являются кратен их размер и поля, которые включают 8 байт или больше должны иметь смещения, кратные 8. Другим решением является использование `LayoutKind.Sequential` вместо `LayoutKind.Explicit`, если разумным.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Это предупреждение должно быть отменено, только в том случае, если оно возникает в ошибке.