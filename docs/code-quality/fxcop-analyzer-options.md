---
title: Параметры конфигурации анализатора FxCop
ms.date: 09/23/2019
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 26435db42e3214bb19438226faba0db0e5ac0f4f
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188833"
---
# <a name="rule-scope-options-for-fxcop-analyzers"></a>Параметры области действия правила для средств FxCop Analyzer

Некоторые правила FxCop Analyzer позволяют уточнить, к каким частям базы кода они должны применяться. На этой странице перечислены доступные параметры конфигурации области, их допустимые значения и правила, к которым они могут применяться. Чтобы использовать эти параметры, укажите их в [файле EditorConfig](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

Эти параметры конфигурации доступны начиная с версии 2.6.3 пакета NuGet [Microsoft. CodeAnalysis. фкскопанализерс](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) .

> [!TIP]
> Чтобы просмотреть полный список параметров, доступных для данной версии пакета Фкскопанализерс, просмотрите файл *анализатора Configuration.md* в папке *документации* для пакета. Файл находится в папке *% UserProfile%\\. нужет\паккажес\микрософт.кодеаналисис.фкскопанализерс\\\<версии\>\документатион\анализер Configuration.md*. Этот файл документации по конфигурации включен в каждую версию пакета, начиная с версии 2.6.5. Ниже приведен пример того, как можно задокументировать параметр в файле *анализатора Configuration.md* :
>
> Имя параметра: `sufficient_IterationCount_for_weak_KDF_algorithm`\
> Значения параметров: целочисленные значения \
> Значение по умолчанию: для каждого настраиваемого правила (по умолчанию — "100000" для большинства правил) \
> Пример: `dotnet_code_quality.CA5387.sufficient_IterationCount_for_weak_KDF_algorithm = 100000`

## <a name="api_surface"></a>api_surface

| Описание | Допустимые значения | Значение по умолчанию | Настраиваемые правила |
| - | - | - | - |
| Какая часть области API для анализа | `public`<br/>`internal` или `friend`<br/>`private`<br/>`all`<br/><br/>Несколько значений следует разделять запятой (,) | `public` | [CA1000](ca1000-do-not-declare-static-members-on-generic-types.md)<br/>[CA1003](ca1003-use-generic-event-handler-instances.md)<br/>[CA1008](ca1008-enums-should-have-zero-value.md)<br/>[CA1010](ca1010-collections-should-implement-generic-interface.md)<br/>[CA1012](ca1012-abstract-types-should-not-have-constructors.md)<br/>[CA1024](ca1024-use-properties-where-appropriate.md)<br/>[CA1027](ca1027-mark-enums-with-flagsattribute.md)<br/>[CA1028](ca1028-enum-storage-should-be-int32.md)<br/>[CA1030](ca1030-use-events-where-appropriate.md)<br/>[CA1036](ca1036-override-methods-on-comparable-types.md)<br/>[CA1040](ca1040-avoid-empty-interfaces.md)<br/>[CA1041](ca1041-provide-obsoleteattribute-message.md)<br/>[CA1043](ca1043-use-integral-or-string-argument-for-indexers.md)<br/>[CA1044](ca1044-properties-should-not-be-write-only.md)<br/>[CA1051](ca1051-do-not-declare-visible-instance-fields.md)<br/>[CA1052](ca1052-static-holder-types-should-be-sealed.md)<br/>[CA1054](ca1054-uri-parameters-should-not-be-strings.md)<br/>[CA1055](ca1055-uri-return-values-should-not-be-strings.md)<br/>[CA1056](ca1056-uri-properties-should-not-be-strings.md)<br/>[CA1058](ca1058-types-should-not-extend-certain-base-types.md)<br/>[CA1063](ca1063-implement-idisposable-correctly.md)<br/>[CA1708](ca1708-identifiers-should-differ-by-more-than-case.md)<br/>[CA1710](ca1710-identifiers-should-have-correct-suffix.md)<br/>[CA1711](ca1711-identifiers-should-not-have-incorrect-suffix.md)<br/>[CA1714](ca1714-flags-enums-should-have-plural-names.md)<br/>[CA1715](ca1715-identifiers-should-have-correct-prefix.md)<br/>[CA1716](ca1716-identifiers-should-not-match-keywords.md)<br/>[CA1717](ca1717-only-flagsattribute-enums-should-have-plural-names.md)<br/>[CA1720](ca1720-identifiers-should-not-contain-type-names.md)<br/>[CA1721](ca1721-property-names-should-not-match-get-methods.md)<br/>[CA1725](ca1725-parameter-names-should-match-base-declaration.md)<br/>[CA1802](ca1802.md)<br/>[CA1815](ca1815.md)<br/>[CA1819](ca1819.md)<br/>[CA2217](ca2217.md)<br/>[CA2225](ca2225.md)<br/>[CA2226](ca2226.md)<br/>[CA2231](ca2231.md)<br/>[CA2234](ca2234.md) |

## <a name="exclude_async_void_methods"></a>exclude_async_void_methods

| Описание | Допустимые значения | Значение по умолчанию | Настраиваемые правила |
| - | - | - | - |
| Следует ли игнорировать асинхронные методы, которые не возвращают значение | `true`<br/>`false` | `false` | [CA2007](ca2007.md) |

> [!NOTE]
> В версии 2.6.3 и более ранних версий пакета анализатора этот параметр был назван `skip_async_void_methods`.

## <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| Описание | Допустимые значения | Значение по умолчанию | Настраиваемые правила |
| - | - | - | - |
| Следует ли исключить из правила [Параметры типа](/dotnet/csharp/programming-guide/generics/generic-type-parameters) из одного символа, например `S` в `Collection<S>` | `true`<br/>`false` | `false` | [CA1715](ca1715-identifiers-should-have-correct-prefix.md) |

> [!NOTE]
> В версии 2.6.3 и более ранних версий пакета анализатора этот параметр был назван `allow_single_letter_type_parameters`.

## <a name="output_kind"></a>output_kind

| Описание | Допустимые значения | Значение по умолчанию | Настраиваемые правила |
| - | - | - | - |
| Указывает, что код в проекте, который создает сборку этого типа, должен быть проанализирован | Одно или несколько полей перечисления <xref:Microsoft.CodeAnalysis.OutputKind><br/><br/>Несколько значений следует разделять запятой (,) | Все типы выходных данных | [CA2007](ca2007.md) |
