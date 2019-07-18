---
title: CA1824. Помечать сборки атрибутом NeutralResourcesLanguageAttribute | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 795d48b96392057a3f96cf3a67f3c49de8aee9b9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203086"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824. Помечайте сборки с помощью NeutralResourcesLanguageAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|Категория|Microsoft.Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Сборка содержит **ResX**-ресурса на основе, но не имеет <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> примененных к нему.

## <a name="rule-description"></a>Описание правила
 **NeutralResourcesLanguage** атрибут сообщает **ResourceManager** языка, который использовался для отображения для сборки ресурсов нейтрального языка и региональных параметров. При поиске ресурсов языка и региональных параметров, как нейтральный язык ресурсов, **ResourceManager** автоматически использует ресурсы, которые находятся в основную сборку. Это делается вместо поиска для вспомогательной сборке, которая содержит текущий язык интерфейса пользователя для текущего потока. При этом повышается эффективность поиска первого загружаемого ресурса и может сократиться рабочее множество.

## <a name="fixing-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте атрибут к сборке и указывает язык, ресурсы нейтрального языка и региональных параметров.

## <a name="specifying-the-language"></a>Выбор языка

#### <a name="to-specify-the-language-of-the-resource-of-the-neutral-culture"></a>Чтобы задать язык ресурсов нейтрального языка и региональных параметров

1. В **обозревателе решений**, щелкните правой кнопкой мыши проект и нажмите кнопку **свойства**.

2. На панели навигации слева выберите **приложения**, а затем нажмите кнопку **сведения о сборке**.

3. В **сведения о сборке** диалоговом окне выберите язык из **нейтральный язык** стрелку раскрывающегося списка.

4. Нажмите кнопку **ОК**.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Допускается, чтобы подавить предупреждение из этого правила. Тем не менее может снизить производительность при запуске.
