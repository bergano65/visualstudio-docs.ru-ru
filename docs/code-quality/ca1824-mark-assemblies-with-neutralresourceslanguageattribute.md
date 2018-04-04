---
title: 'Ca1824: следует Помечать сборки атрибутом NeutralResourcesLanguageAttribute | Документы Microsoft'
ms.date: 03/29/2018
ms.technology: vs-ide-code-analysis
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
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: fb5b7665cedde698dd03a5e58adb4c4a72d0f461
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/03/2018
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824: следует помечать сборки атрибутом NeutralResourcesLanguageAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|Категория|Microsoft.Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Сборка содержит **ResX**-ресурса на основе, но не имеет <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> применяемый к нему.

## <a name="rule-description"></a>Описание правила

<xref:System.Resources.NeutralResourcesLanguageAttribute> Атрибут сообщает диспетчеру ресурсов языка и региональных параметров приложения по умолчанию. Если ресурсы для культуры по умолчанию встраиваются в основную сборку приложения, и <xref:System.Resources.ResourceManager> должен будет получить ресурсы, принадлежащие к языка и региональных параметров, как культуры по умолчанию <xref:System.Resources.ResourceManager> автоматически использует ресурсы, содержащиеся в основной сборке вместо поиска вспомогательной сборки. Это обходит проверки обычные сборки, повышается эффективность поиска первого ресурса загрузки и может сократиться рабочее множество.

> [!TIP]
> В разделе [упаковки и развертывания ресурсов](/dotnet/framework/resources/packaging-and-deploying-resources-in-desktop-apps) для процесса, <xref:System.Resources.ResourceManager> производит поиск файлов ресурсов.

## <a name="fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение данного правила, добавьте атрибут к сборке и укажите язык ресурсов нейтрального языка и региональных параметров.

### <a name="to-specify-the-neutral-language-for-resources"></a>Для указания нейтрального языка для ресурсов

1. В **обозревателе решений**, щелкните правой кнопкой мыши проект и выберите **свойства**.

2. Выберите **приложения** , а затем выберите **сведений о сборке**.

   > [!NOTE]
   > Если проект является проектом .NET Standard или .NET Core, выберите **пакета** вкладки.

3. Выберите язык из **нейтрального языка** или **нейтрального языка ассемблера** раскрывающегося списка.

4. Нажмите кнопку **ОК**.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Допускается использование отключайте предупреждение из этого правила. Тем не менее могут снизить производительность при запуске.

## <a name="see-also"></a>См. также

- <xref:System.Resources.NeutralResourcesLanguageAttribute>
- [Ресурсы в приложениях для настольных систем (.NET)](/dotnet/framework/resources/)
- [CA1703 - строки ресурсов должны иметь правильное правописание](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1701 - строки ресурса, который сложных слов следует использовать правильный регистр](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)