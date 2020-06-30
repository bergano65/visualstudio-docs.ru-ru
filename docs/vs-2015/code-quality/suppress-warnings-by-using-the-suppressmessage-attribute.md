---
title: Отключение предупреждений с помощью атрибута SuppressMessage | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- VC.Project.VCFxCopTool.InputAssemblyFileName
- VC.Project.VCFxCopTool.FxCopModuleSuppressionsFile
- VC.Project.VCFxCopTool.FxCopUseTypeNameInSuppression
- VC.Project.VCFxCopTool.OutputFile
helpviewer_keywords:
- code analysis, source suppression
- source suppression
- SuppressMessage attribute
- code analysis, SuppressMessage attribute
ms.assetid: a38c57a2-d29d-43c0-84ff-3308b2484ce6
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a5d64a27759cf844550297beb19b026bbeaa0e40
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546826"
---
# <a name="suppress-warnings-by-using-the-suppressmessage-attribute"></a>Подавление предупреждений при помощи атрибута SuppressMessage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Часто бывает полезно указать, что предупреждение неприменимо, чтобы члены команды могли понять, что код был проверен, и было определено, что предупреждение должно быть подавлено. Подавление исходного кода (ISS) позволяет разработчику разместить атрибут, который подавляет предупреждение ближе к расположению, вызвавшему предупреждение. Вы можете добавить атрибут ISS непосредственно в исходный файл или использовать контекстное меню в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] интегрированной среде разработки.

## <a name="in-this-section"></a>В этом разделе

|Заголовок|Описание|
|-|-|
|[Общие сведения о подавлении в исходном коде](../code-quality/in-source-suppression-overview.md)|Узнайте о ISS и о том, как использовать его в коде.|
|[Практическое руководство. Отключение предупреждений при помощи пункта меню](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)|Сведения о подавлении предупреждений в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] интегрированной среде разработки с помощью контекстного меню.|

## <a name="related-sections"></a>Связанные разделы
 [Анализ качества управляемого кода](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
