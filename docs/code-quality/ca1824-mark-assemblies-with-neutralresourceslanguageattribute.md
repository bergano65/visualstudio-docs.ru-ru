---
title: CA1824. Помечайте сборки с помощью NeutralResourcesLanguageAttribute
ms.date: 03/29/2018
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
ms.openlocfilehash: df5c0db4e9e141e5833893bbbb447328eab8851e
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233347"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824. Помечайте сборки с помощью NeutralResourcesLanguageAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|Категория|Microsoft. Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Сборка содержит ресурс на основе **RESX**, но не имеет <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> примененного к нему ресурса.

## <a name="rule-description"></a>Описание правила

<xref:System.Resources.NeutralResourcesLanguageAttribute> Атрибут информирует диспетчер ресурсов о культуре приложения по умолчанию. Если ресурсы языка и региональных параметров по умолчанию внедряются в основную сборку приложения и <xref:System.Resources.ResourceManager> должны получать ресурсы, принадлежащие к тому же языку и региональным параметрам <xref:System.Resources.ResourceManager> по умолчанию, компонент автоматически использует ресурсы, расположенные в основной сборке. Вместо поиска вспомогательной сборки. Это обходит обычную проверку сборки, улучшает производительность поиска для первого загружаемого ресурса и может сократить рабочий набор.

> [!TIP]
> См. раздел [Упаковка и развертывание ресурсов](/dotnet/framework/resources/packaging-and-deploying-resources-in-desktop-apps) для процесса <xref:System.Resources.ResourceManager> , который использует для проверки файлов ресурсов.

## <a name="fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, добавьте атрибут в сборку и укажите язык ресурсов нейтрального языка и региональных параметров.

### <a name="to-specify-the-neutral-language-for-resources"></a>Указание нейтрального языка для ресурсов

1. В **Обозреватель решений**щелкните правой кнопкой мыши проект и выберите пункт **свойства**.

2. Перейдите на вкладку **приложение** и выберите **сведения о сборке**.

   > [!NOTE]
   > Если проект является .NET Standard или проектом .NET Core, выберите вкладку **пакет** .

3. Выберите язык из раскрывающегося списка **нейтральный язык** или **нейтральный язык сборки** .

4. Нажмите кнопку **ОК**.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Предупреждение можно отключить от этого правила. Однако производительность запуска может снизиться.

## <a name="see-also"></a>См. также

- <xref:System.Resources.NeutralResourcesLanguageAttribute>
- [Ресурсы в классических приложениях (.NET)](/dotnet/framework/resources/)
- [CA1703 — строки ресурсов должны быть написаны правильно](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1701-составные слова в строках ресурсов должны иметь правильный регистр](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)