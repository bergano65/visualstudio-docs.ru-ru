---
title: CA1824. Помечайте сборки с помощью NeutralResourcesLanguageAttribute
ms.date: 03/29/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 57845ae2e163aa8d2045204daa4beda948a50e59
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54957706"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824. Помечайте сборки с помощью NeutralResourcesLanguageAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|Категория|Microsoft.Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Сборка содержит **ResX**-ресурса на основе, но не имеет <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> примененных к нему.

## <a name="rule-description"></a>Описание правила

<xref:System.Resources.NeutralResourcesLanguageAttribute> Атрибут сообщает диспетчеру ресурсов языка и региональных параметров приложения по умолчанию. Если ресурсы для культуры по умолчанию внедряются в основную сборку приложения, и <xref:System.Resources.ResourceManager> имеет для извлечения ресурсов, принадлежащих языку и региональным параметрам, как по умолчанию язык и региональные параметры, <xref:System.Resources.ResourceManager> автоматически использует ресурсы, находящиеся в основной сборке вместо поиска для вспомогательной сборки. Это обходит проверки обычные сборки, повышается эффективность поиска первого загружаемого ресурса и может сократиться рабочее множество.

> [!TIP]
> См. в разделе [упаковки и развертывания ресурсов](/dotnet/framework/resources/packaging-and-deploying-resources-in-desktop-apps) для процесса, <xref:System.Resources.ResourceManager> производит поиск файлов ресурсов.

## <a name="fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, добавьте атрибут к сборке и указывает язык, ресурсы нейтрального языка и региональных параметров.

### <a name="to-specify-the-neutral-language-for-resources"></a>Чтобы указать для ресурсов нейтрального языка

1. В **обозревателе решений**, щелкните правой кнопкой мыши проект и выберите **свойства**.

2. Выберите **приложения** , а затем выберите **сведения о сборке**.

   > [!NOTE]
   > Если проект является проектом .NET Standard или .NET Core, выберите **пакета** вкладки.

3. Выберите язык из **нейтрального языка** или **нейтрального языка ассемблера** стрелку раскрывающегося списка.

4. Нажмите кнопку **ОК**.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Допускается, чтобы подавить предупреждение из этого правила. Тем не менее могут снизить производительность при запуске.

## <a name="see-also"></a>См. также

- <xref:System.Resources.NeutralResourcesLanguageAttribute>
- [Ресурсы в классических приложениях (.NET)](/dotnet/framework/resources/)
- [CA1703 - строки ресурсов должны иметь правильное правописание](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1701 — строка ресурса, составные слова должны иметь правильный регистр](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)