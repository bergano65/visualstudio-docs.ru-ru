---
title: 'CA2144: прозрачный код не должен загружать сборки из массивов байтов'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2144
ms.assetid: 777b1310-6e16-4413-b4ee-5f3136304f82
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 79c2ebb4b088a0712773ce8d5c208ba0f921df75
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays"></a>CA2144: прозрачный код не должен загружать сборки из массивов байтов
|||
|-|-|
|TypeName|TransparentMethodsShouldNotLoadAssembliesFromByteArrays|
|CheckId|CA2144|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Прозрачный метод загружает сборку из массива байтов с помощью одного из следующих методов:

-   <xref:System.Reflection.Assembly.Load%2A>

-   <xref:System.Reflection.Assembly.Load%2A>

-   <xref:System.Reflection.Assembly.Load%2A>

## <a name="rule-description"></a>Описание правила
 Проверка безопасности для прозрачного кода не так тщательна, как проверка безопасности для критического кода, поскольку прозрачный код не может выполнять действия, требующие особых мер безопасности. Сборки, загруженные из массива байтов, могут остаться незамеченными в прозрачном коде, и этот массив байтов может содержать критичный или, что более важно, критичный в плане безопасности код, который подлежит аудиту. Таким образом прозрачный код не должен загружать сборки из массива байтов.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, пометьте метод, который загружает сборку с образом <xref:System.Security.SecurityCriticalAttribute> или <xref:System.Security.SecuritySafeCriticalAttribute> атрибута.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 Это правило срабатывает на следующий код, поскольку прозрачный метод загружает сборку из массива байтов.

 [!code-csharp[FxCop.Security.CA2144.TransparentMethodsShouldNotLoadAssembliesFromByteArrays#1](../code-quality/codesnippet/CSharp/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays_1.cs)]