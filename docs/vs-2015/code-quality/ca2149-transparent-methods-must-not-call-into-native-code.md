---
title: 'CA2149: Прозрачные методы не следует вызывать в машинном коде | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2149
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 887252eca86205858b168c7f5a4a6c33cb0cc67d
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591120"
---
# <a name="ca2149-transparent-methods-must-not-call-into-native-code"></a>CA2149: прозрачные методы не следует вызывать в машинном коде
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA2149: прозрачные методы не следует вызывать в машинном коде](https://docs.microsoft.com/visualstudio/code-quality/ca2149-transparent-methods-must-not-call-into-native-code).

|||
|-|-|
|TypeName|TransparentMethodsMustNotCallNativeCode|
|CheckId|CA2149|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Метод вызывает собственную функцию через прототип метода, например P/Invoke.

## <a name="rule-description"></a>Описание правила
 Это правило срабатывает для любого прозрачного метода, который вызывается непосредственно в машинном коде, например, с помощью вызова P/Invoke. Нарушение этого правила приводит к <xref:System.MethodAccessException> в уровне 2 модели прозрачности и полного <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> на уровне 1 модели прозрачности.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, отметьте метод, который вызывает машинный код с <xref:System.Security.SecurityCriticalAttribute> или <xref:System.Security.SecuritySafeCriticalAttribute> атрибута.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 [!code-csharp[FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2149.transparentmethodsmustnotcallnativecode/cs/ca2149 - transparentmethodsmustnotcallnativecode.cs#1)]



