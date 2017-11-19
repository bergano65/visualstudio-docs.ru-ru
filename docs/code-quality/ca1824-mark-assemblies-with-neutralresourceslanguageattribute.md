---
title: "Ca1824: следует Помечать сборки атрибутом NeutralResourcesLanguageAttribute | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c1d2138065946bfd14abfedbbffdd2dc5b433d89
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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
 **NeutralResourcesLanguage** атрибут сообщает **ResourceManager** языка, который был использован для отображения ресурсов нейтрального языка и региональных параметров сборки. При поиске ресурсов в язык и региональные параметры, как язык нейтральных ресурсов **ResourceManager** автоматически использует ресурсы, которые находятся в основной сборке. Это делается вместо поиска вспомогательной сборки с текущего языка и региональных параметров пользовательского интерфейса для текущего потока. При этом повышается эффективность поиска первого загружаемого ресурса и может сократиться рабочее множество.  
  
## <a name="fixing-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, добавьте атрибут к сборке и укажите язык ресурсов нейтрального языка и региональных параметров.  
  
## <a name="specifying-the-language"></a>Указание языка  
  
#### <a name="to-specify-the-language-of-the-resource-of-the-neutral-culture"></a>Чтобы указать язык ресурсов нейтрального языка и региональных параметров  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши проект и выберите команду **свойства**.  
  
2.  На левой панели навигации выберите **приложения**, а затем нажмите кнопку **сведений о сборке**.  
  
3.  В **сведений о сборке** диалогового окна выберите язык из **нейтральный язык** раскрывающегося списка.  
  
4.  Нажмите кнопку **ОК**.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Допускается использование отключайте предупреждение из этого правила. Тем не менее может снизить производительность при запуске.